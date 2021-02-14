---
title: Feuille de route de l’écosystème de la console et du terminal Windows
description: Fournit une vue d’ensemble des interactions et des plans pour l’hôte de console Windows, les API de console, le sous-système de console et le produit Terminal.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, terminal, terminal virtuel, hôte de console, ligne de commande, sous-système, feuille de route, écosystème
ms.prod: console
ms.localizationpriority: high
ms.openlocfilehash: 3db266b761d4a8ee1fd8ec24d640bb277ab76edb
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357899"
---
# <a name="windows-console-and-terminal-ecosystem-roadmap"></a>Feuille de route de l’écosystème de la console et du terminal Windows

Ce document est une feuille de route générale de la console Windows et des produits Terminal Windows. Il couvre les sujets suivants :


- Intégration de la console Windows et de Terminal Windows à l’écosystème des applications en ligne de commande sur Windows et d’autres systèmes d’exploitation

- Historique et feuille de route des produits, fonctionnalités et stratégies qui font partie du développement de la plateforme

Dans l’ère actuelle de la console/du terminal, l’objectif de Microsoft est d’offrir une expérience de premier ordre directement aux développeurs sur la plateforme Windows, et de [supprimer progressivement](classic-vs-vt.md) les API de console Windows classiques, en les remplaçant par des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) utilisant une [pseudoconsole](pseudoconsoles.md). **[Terminal Windows](/terminal/get-started)** illustre cette transition vers une expérience de premier ordre, en invitant la communauté des développeurs à une [collaboration open source](https://github.com/microsoft/terminal), en prenant en charge un éventail complet de combinaisons d’applications clientes en ligne de commande et d’applications d’hébergement de terminal, et en unifiant l’écosystème Windows avec toutes les autres plateformes.

## <a name="definitions"></a>Définitions

Avant de continuer, nous vous recommandons de vous familiariser avec les [définitions](definitions.md) de la terminologie courante utilisée dans cet espace. La terminologie courante comprend des termes tels que : [applications en ligne de commande (ou de console)](definitions.md#command-line-applications), [handles standard (`STDIN`, `STDOUT`, `STDERR`)](definitions.md#standard-handles), [appareils TTY et PTY](definitions.md#ttypty), [clients et serveurs](definitions.md#clients-and-servers), [sous-système de console](definitions.md#console-subsystem), [hôte de la console](definitions.md#console-host), [pseudoconsole](definitions.md#pseudoconsole)et [terminal](definitions.md#terminal).

## <a name="architecture"></a>Architecture

L’architecture générale du système comporte quatre parties : client, appareil, serveur et terminal.

![Organigramme de communication de la ligne de commande - De la source vers la destination : client à appareil vers serveur à terminal](images/command-line-communication.png)

### <a name="client"></a>Client

Le client est une application en ligne de commande qui utilise une interface textuelle pour permettre à l’utilisateur d’entrer des commandes (plutôt qu’une interface utilisateur basée sur la souris) et qui retourne une représentation textuelle du résultat. Sur Windows, l’API de console fournit une couche de communication entre le client et l’appareil. (Il peut également s’agir d’un handle de console standard avec des API de contrôle d’appareil.)

### <a name="device"></a>Appareil

L’appareil est une couche intermédiaire de communications de gestion des messages entre deux processus, le client et le serveur. Sur Windows, il s’agit du pilote de la console. Sur d’autres plateformes, il s’agit de l’appareil TTY ou PTY. D’autres appareils, tels que des fichiers, canaux et sockets, peuvent être utilisés comme canal de communication si la transaction entière est en texte brut ou si elle contient des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md), mais pas avec l’[API de console Windows](console-functions.md).

### <a name="server"></a>Serveur

Le serveur interprète les messages ou appels d’API demandés en provenance du client. Sur Windows en mode de fonctionnement classique, le serveur crée également une interface utilisateur pour présenter la sortie à l’écran. Le serveur collecte par ailleurs une entrée à renvoyer au client dans les messages de réponse, par le biais du pilote, comme un terminal groupé dans le même module. En mode [pseudoconsole](pseudoconsoles.md), il ne s’agit que d’un traducteur permettant de présenter ces informations dans des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) à un terminal attaché.

### <a name="terminal"></a>Terminal

Le terminal est la couche finale fournissant l’affichage graphique et les services d’interactivité avec l’utilisateur. Il est chargé de capturer les entrées et de les encoder en tant que [séquences de terminaux virtuels](console-virtual-terminal-sequences.md), qui finissent par atteindre le `STDIN` du client. Il reçoit et décode également les *séquences de terminaux virtuels* qu’il reçoit en provenance du `STDOUT` du client à des fins de présentation à l’écran.

#### <a name="further-connections"></a>Autres connexions

D’autres connexions peuvent également être établies en effectuant un chaînage des applications qui assument plusieurs rôles dans l’un des points de terminaison. Par exemple, une session SSH a deux rôles : il s’agit d’un **terminal** pour l’application en ligne de commande exécutée sur un appareil, mais elle transfère toutes les informations reçues sur un rôle **client** sur un autre appareil. Ce chaînage peut se produire indéfiniment entre les appareils et les contextes, offrant ainsi une grande flexibilité de scénario.

Sur les plateformes non-Windows, les rôles **serveur** et **terminal** constituent une même unité, car aucune couche de compatibilité de traduction n’est nécessaire entre un ensemble d’API et des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md).

## <a name="microsoft-products"></a>Produits Microsoft

Tous les produits en ligne de commande Microsoft Windows sont maintenant disponibles sur GitHub dans un dépôt open source, [microsoft/terminal](https://github.com/microsoft/terminal).

### <a name="windows-console-host"></a>Hôte de console Windows

Il s’agit de l’interface utilisateur Windows traditionnelle pour les applications en ligne de commande. Elle gère l’ensemble des opérations d’API de console appelées à partir de n’importe quelle application en ligne de commande attachée. La console Windows gère également la représentation de l’interface graphique utilisateur (GUI) pour le compte de toutes ces applications. Elle se trouve dans le répertoire système sous le nom `conhost.exe`, ou `openconsole.exe` dans sa forme open source. Elle est fournie avec le système d’exploitation Windows. Elle figure également dans d’autres produits Microsoft générés à partir du dépôt open source pour une implémentation plus à jour de l’infrastructure de [pseudoconsole](pseudoconsoles.md). Selon les définitions ci-dessus, elle opère soit dans un rôle traditionnel serveur-terminal combiné, soit dans un rôle serveur-uniquement par le biais de l’infrastructure de _pseudoconsole_ préférée.

### <a name="windows-terminal"></a>Terminal Windows

Il s’agit de la nouvelle interface Windows pour les applications en ligne de commande. Terminal Windows constitue un exemple d’utilisation par première partie de la [pseudoconsole](pseudoconsoles.md) afin de séparer les préoccupations entre la maintenance des API et l’interfaçage des applications textuelles, à l’instar de toutes les plateformes non-Windows.


Terminal Windows est l’interface utilisateur phare en mode texte pour Windows. Elle illustre les fonctionnalités de l’écosystème et pilote le développement Windows vers l’unification avec d’autres plateformes. Terminal Windows illustre également comment créer une application moderne, robuste et complexe qui couvre l’historique et la gamme des API et frameworks Windows. Selon les définitions ci-dessus, ce produit opère dans un rôle de terminal.

## <a name="major-historical-milestones"></a>Principaux jalons historiques

Cette section sur les principaux jalons du sous-système de console décrit l’implémentation avant 2014, puis fournit une vue d’ensemble du travail effectué depuis 2014, date à laquelle le focus a été replacé sur la ligne de commande à l’ère Windows 10.

### <a name="initial-implementation"></a>Implémentation initiale

**\[1989-Années 1990]** Le système hôte de console initial a été implémenté en tant qu’émulation de l’environnement DOS au sein du système d’exploitation Windows. Son code est enchevêtré et coopératif avec l’[invite de commandes](/windows-server/administration/windows-commands/cmd), `cmd.exe`, qui est une représentation de cet environnement DOS. Le code du système hôte de console partage les responsabilités et les privilèges avec l’interpréteur de commandes. Il fournit également un niveau de base de services pour d’autres utilitaires en ligne de commande, afin d’exécuter des services d’une manière semblable à CMD.

### <a name="dbcs-for-cjk"></a>DBCS pour CJK

**\[1997-1999\]** À cette époque, la prise en charge de [DBCS](/windows/win32/intl/double-byte-character-sets) (Double-Byte Character Set, ou « jeu de caractères codés sur deux octets ») est introduite pour prendre en charge les marchés CJK (chinois, japonais et coréen). Cet effort se traduit par une bifurcation de nombreuses méthodes d’écriture et de lecture à l’intérieur de la console en vue de fournir à la fois des versions « occidentales », pour gérer les caractères codés sur un octet, et une représentation alternative pour les versions « orientales », où deux octets sont nécessaires pour représenter la vaste gamme de caractères. Cette bifurcation comprenait la représentation agrandie d’une cellule dans l’environnement de la console afin qu’elle occupe une ou deux cellules de large, où une cellule est étroite (plus haute que large) et deux cellules est large, pleine largeur ou un carré dans lequel les idéogrammes chinois, japonais et coréens typiques peuvent être inscrits.

### <a name="securityisolation"></a>Sécurité/isolation

**\[2005-2009\]** Avec l’expérience du sous-système de console s’exécutant au sein du processus système critique, `csrss.exe`, la connexion de diverses applications clientes, à différents niveaux d’accès, à un processus ultra critique et privilégié unique a été jugée comme particulièrement dangereuse. Durant cette ère, le sous-système de console était divisé en applications clientes, pilotes et serveurs. Chaque application pouvait s’exécuter dans son propre contexte, réduisant ainsi les responsabilités et les privilèges dans chacune d’elles. Cette isolation augmentait la robustesse générale du système, car toute défaillance dans le sous-système de la console n’avait plus d’incidence sur la fonctionnalité des autres processus critiques.

### <a name="user-experience-improvements"></a>Améliorations apportées à l’expérience utilisateur

**\[2014-2016\]** Après une longue période durant laquelle la maintenance du sous-système de console a été assurée par diverses équipes au sein de l’organisation, une nouvelle équipe axée sur le développement a été formée afin d’assumer la propriété et la direction des améliorations apportées à la console. Durant cette période, les améliorations ont porté sur les aspects suivants : sélection de lignes, fluidité du redimensionnement de fenêtre, nouveau flux du texte, copier-coller, prise en charge des résolutions élevées, et accent sur Unicode, notamment la convergence de la séparation entre les algorithmes de stockage et de manipulation de flux « Ouest » et « Est ».

### <a name="virtual-terminal-client"></a>Client Terminal virtuel

**\[2015-2017\]** Avec l’arrivée du [Sous-système Windows pour Linux](/windows/wsl/), les efforts de Microsoft en vue d’améliorer l’expérience de [Docker sur Windows](/dotnet/architecture/microservices/container-docker-introduction/docker-defined) et l’adoption d’[OpenSSH](/windows-server/administration/openssh/openssh_overview) en tant que principale technologie d’exécution à distance de la ligne de commande, les implémentations initiales de [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) ont été introduites dans l’hôte de console. Cela a permis à la console existante d’assumer la fonction de terminal, attaché directement à ces applications Linux natives dans leurs environnements respectifs, avec rendu des attributs graphiques et textuels à l’écran et retour de l’entrée utilisateur dans le dialecte approprié.

### <a name="virtual-terminal-server"></a>Serveur Terminal virtuel

**\[2018\]** Au cours des vingt dernières années, des alternatives tierces pour l’hôte de console de la boîte de réception ont été créées afin d’accroître la productivité du développeur, principalement centrées sur des personnalisations enrichies et des interfaces avec onglets. Ces applications avaient toujours besoin d’exécuter et de masquer la fenêtre hôte de console. Elles étaient attachées en tant qu’application « cliente » secondaire pour récupérer les informations de mémoire tampon dans des boucles d’interrogation durant l’exécution de l’application cliente en ligne de commande principale. Leur objectif était d’être des terminaux, comme sur d’autres plateformes, mais dans l’univers de Windows où les terminaux n’étaient pas remplaçables.

C’est durant cette période que l’infrastructure de [pseudoconsole](pseudoconsoles.md) a été introduite. La pseudoconsole permet à n’importe quelle application de lancer l’hôte de console en mode non interactif et de devenir l’interface terminal finale pour l’utilisateur. Dans le cadre de cet effort, la principale limitation a porté sur la promesse de compatibilité continue de Windows concernant la maintenance de toutes les [API de console Windows](console-functions.md) publiées à l’avenir, tout en fournissant une interface d’hébergement de serveur de remplacement qui correspondait à ce qui est attendu sur toutes les autres plateformes : des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md). Cet effort a par conséquent donné naissance à un reflet de la phase cliente : la _pseudoconsole_ projette ce qui serait affiché à l’écran en tant que _séquences de terminaux virtuels_ pour un hôte délégué, et interprète les réponses en séquences d’entrée au format Windows en vue de leur consommation par les applications clientes.

## <a name="roadmap-for-the-future"></a>Feuille de route pour l’avenir

### <a name="terminal-applications"></a>Applications de terminal

**\[2019-\]Présent** Il s’agit de l’ère open source pour le sous-système de console, axée sur le nouveau Terminal Windows. Annoncé durant la conférence Microsoft Build en mai 2019, Terminal Windows est entièrement disponible sur GitHub dans [microsoft/terminal](https://github.com/microsoft/terminal). La création de l’application Terminal Windows par-dessus la plateforme affinée pour [pseudoconsole](pseudoconsoles.md) sera l’objectif de cette ère, le but étant de fournir une expérience de terminal de première classe directement aux développeurs sur la plateforme Windows.

**[Terminal Windows](/terminal/get-started)** vise non seulement à mettre les fonctionnalités de la plateforme en avant, notamment la technologie d’interface [WinUI](/apps/winui/), le modèle d’empaquetage [MSIX](/msix/) et l’architecture de composant [C++/WinRT](/uwp/cpp-and-winrt-apis/), mais également à constituer une validation de la plateforme proprement dite. Terminal Windows est un facteur de motivation pour l’organisation Windows dans l’ouverture et l’évolution de la plateforme d’application en fonction des besoins en vue de continuer à accroître la productivité des développeurs. Le jeu unique d’exigences des utilisateurs avec pouvoir et des développeurs de Terminal Windows constitue un facteur de motivation dans l’identification des critères que la plateforme Windows moderne doit satisfaire pour répondre aux besoins de ces marchés.

À l’intérieur du système d’exploitation Windows, cela comprend [la mise hors service de l’interface utilisateur de l’hôte de console classique](./classic-vs-vt.md) en faveur de [Terminal Windows](/terminal/get-started), de [ConPTY](https://devblogs.microsoft.com/commandline/windows-command-line-introducing-the-windows-pseudo-console-conpty/) et des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md).

Pour finir, cette ère envisage d’offrir un choix complet en guise d’alternative à l’expérience par défaut, qu’il s’agisse du produit Terminal Windows ou de tout autre terminal.

### <a name="client-support-library"></a>Bibliothèque de prise en charge de client

**\[L’avenir\]** Avec la prise en charge et la documentation des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) côté client, nous encourageons vivement les développeurs d’utilitaires en ligne de commande Windows à utiliser des séquences de terminaux virtuels plutôt que les API Windows classiques, afin de tirer parti d’un écosystème unifié avec toutes les plateformes. Toutefois, l’une des pièces manquantes du puzzle est que les autres plateformes proposent un grand nombre de bibliothèques d’assistance côté client pour gérer les entrées comme [ReadLine](https://tiswww.case.edu/php/chet/readline/rltop.html) et l’affichage graphique comme [ncurses](https://invisible-island.net/ncurses/ncurses.html). Cet élément particulier de la feuille de route représente l’exploration de ce qu’offre l’écosystème et comment nous pouvons accélérer l’adoption des séquences de terminaux virtuels dans les applications en ligne de commande Windows en remplacement de l’API de console classique.

### <a name="sequence-passthrough"></a>Adoption des séquences

**\[L’avenir\]** La combinaison des implémentations de serveur et de client de terminal virtuel autorise une combinaison complète d’applications clientes en ligne de commande et d’applications d’hébergement de terminal. Cette combinaison peut communiquer avec les [API de console Windows](console-functions.md) classiques ou les [séquences de terminaux virtuels](console-virtual-terminal-sequences.md). Toutefois, il existe un coût de surcharge pour la conversion en méthode Windows compatible classique, puis la reconversion en méthode de terminal virtuel plus universelle.

Une fois que le marché aura suffisamment adopté les _séquences de terminaux virtuels_ et UTF-8 sur Windows, la tâche de conversion/interprétation de l’hôte de console pourra éventuellement être désactivée. L’hôte de console deviendra alors un service d’appel d’API simple, et relaiera les appels d’appareil vers l’application d’hébergement par le biais de la [pseudoconsole](pseudoconsoles.md). Ce changement augmentera les performances et optimisera le dialecte des séquences pouvant être parlé entre l’application cliente et le terminal. Grâce à ce changement, des scénarios d’interactivité supplémentaires seront possibles, et le monde de Windows sera *(enfin)* aligné avec la famille de toutes les autres plateformes dans l’espace d’applications en ligne de commande.