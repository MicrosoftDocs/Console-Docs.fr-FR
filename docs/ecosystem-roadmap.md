---
title: Guide de la console Windows et de l’écosystème des terminaux
description: Fournit une vue d’ensemble des interactions entre les plans et pour l’hôte de console Windows, les API de console, le sous-système de console et le produit terminal.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, terminal, terminal virtuel, hôte de console, ligne de commande, sous-système, feuille de route, écosystème
ms.prod: console
ms.openlocfilehash: e47b72a6f66e54b5f2904770f7c1a87e08d927e2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039586"
---
# <a name="windows-console-and-terminal-ecosystem-roadmap"></a>Guide de la console Windows et de l’écosystème des terminaux

Ce document est un guide de haut niveau de la console Windows et des produits Windows Terminal Server. Il couvre les sujets suivants :


- Intégration de la console Windows et du terminal Windows à l’écosystème des applications en ligne de commande sur Windows et d’autres systèmes d’exploitation.

- Un historique et un futur plan des produits, fonctionnalités et stratégies qui font partie du développement de la plateforme, ainsi que la création pour cette plateforme.

L’objectif de l’ère actuelle de la console/du terminal chez Microsoft est d’offrir une expérience de premier ordre directement aux développeurs sur la plate-forme Windows et de créer [progressivement des](classic-vs-vt.md) API de console Windows classiques, en les remplaçant par des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) utilisant [pseudoconsole](pseudoconsoles.md). **[Windows Terminal](/terminal/get-started)** présente cette transition dans une expérience de premier ordre, en invitant la [collaboration Open source](https://github.com/microsoft/terminal) de la communauté des développeurs, en prenant en charge un large éventail de combinaisons d’applications de ligne de commande client et d’hébergement de terminaux, et en unifiant l’écosystème Windows avec toutes les autres plateformes.

## <a name="definitions"></a>Définitions

Avant de continuer, il est recommandé de vous familiariser avec les [définitions](definitions.md) de la terminologie courante utilisée dans cet espace. La terminologie courante comprend : les [applications de ligne de commande (ou de console)](definitions.md#command-line-applications), les [Handles standard ( `STDIN` , `STDOUT` , `STDERR` )](definitions.md#standard-handles), les [appareils TTY et Pty](definitions.md#ttypty), [les clients et les serveurs](definitions.md#clients-and-servers), le [sous-système](definitions.md#console-subsystem)de la console, l' [hôte de console](definitions.md#console-host), [pseudoconsole](definitions.md#pseudoconsole)et [Terminal](definitions.md#terminal).

## <a name="architecture"></a>Architecture

L’architecture générale du système est en quatre parties : client, périphérique, serveur et terminal.

![Source de l’organigramme de la communication de la ligne de commande vers la destination, exécution du client vers l’appareil vers le serveur vers le terminal](images/command-line-communication.png)

### <a name="client"></a>Client

Le client est une application de ligne de commande qui utilise une interface textuelle pour permettre à l’utilisateur d’entrer des commandes (plutôt qu’une interface utilisateur basée sur la souris), en retournant une représentation textuelle du résultat. Sur Windows, l’API de console fournit une couche de communication entre le client et l’appareil. (Il peut également s’agir d’un handle de console standard avec des API de contrôle de périphérique).

### <a name="device"></a>Appareil

L’appareil est une couche intermédiaire de communications de gestion des messages entre deux processus, le client et le serveur. Sur Windows, il s’agit du pilote de la console. Sur les autres plateformes, il s’agit de l’appareil TTY ou PTY. D’autres périphériques, tels que des fichiers, des canaux et des sockets, peuvent être utilisés comme ce canal de communication si l’ensemble de la transaction est en texte brut ou contient des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md), mais pas avec les [API de console Windows](console-functions.md).

### <a name="server"></a>Serveur

Le serveur interprète les appels d’API ou les messages demandés du client. Sur Windows dans le mode de fonctionnement classique, le serveur crée également une interface utilisateur pour présenter la sortie à l’écran. Le serveur collecte également les entrées à renvoyer dans les messages de réponse au client, par le biais du pilote, comme un terminal dans le même module. À l’aide du mode [pseudoconsole](pseudoconsoles.md) , il ne s’agit que d’un traducteur pour présenter ces informations dans des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) à un terminal attaché.

### <a name="terminal"></a>Terminal

Le terminal est la couche finale fournissant l’affichage graphique et les services d’interactivité à l’utilisateur. Il est chargé de capturer les entrées et de les encoder en [séquences de terminaux virtuels](console-virtual-terminal-sequences.md), ce qui finit par atteindre le client `STDIN` . Elle va également recevoir et décoder les *séquences de terminaux virtuels* qu’elle reçoit de la présentation du client à `STDOUT` l’écran.

#### <a name="further-connections"></a>Autres connexions

En guise d’addenda, d’autres connexions peuvent être effectuées en effectuant un chaînage des applications qui traitent plusieurs rôles dans l’un des points de terminaison. Par exemple, une session SSH a deux rôles : il s’agit d’un **Terminal** pour l’application en ligne de commande qui s’exécute sur un appareil, mais il transfère toutes les informations reçues sur un rôle **client** sur un autre appareil. Ce chaînage peut se produire indéfiniment entre les appareils et les contextes offrant une grande flexibilité de scénario.

Sur les plateformes non-Windows, les rôles **serveur** et **Terminal** représentent une seule unité, car il n’est pas nécessaire de disposer d’une couche de compatibilité de traduction entre un ensemble d’API et des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md).

## <a name="microsoft-products"></a>Produits Microsoft

Tous les produits de ligne de commande Microsoft Windows sont désormais disponibles sur GitHub dans un référentiel Open source, [Microsoft/Terminal](https://github.com/microsoft/terminal).

### <a name="windows-console-host"></a>Hôte de console Windows

Il s’agit de l’interface utilisateur Windows traditionnelle pour les applications de ligne de commande. Il gère l’ensemble de la maintenance des API de console appelée à partir de n’importe quelle application de ligne de commande attachée. La console Windows gère également la représentation de l’interface graphique utilisateur (GUI) pour le compte de toutes ces applications. Il se trouve dans le répertoire système sous la forme `conhost.exe` , ou `openconsole.exe` dans son formulaire Open source. Il est fourni avec le système d’exploitation Windows. Il se trouve également dans d’autres produits Microsoft générés à partir du référentiel Open source pour une implémentation plus à jour de l’infrastructure [pseudoconsole](pseudoconsoles.md) . Selon les définitions ci-dessus, il fonctionne dans un rôle combiné serveur-et-terminal traditionnellement ou un rôle serveur uniquement par le biais de l’infrastructure _pseudoconsole_ préférée.

### <a name="windows-terminal"></a>Terminal Windows

Il s’agit de la nouvelle interface Windows pour les applications en ligne de commande. Windows Terminal est un exemple de première partie de l’utilisation de [pseudoconsole](pseudoconsoles.md) pour séparer les préoccupations entre la maintenance des API et l’interfaçage des applications textuelles, à l’instar de toutes les plateformes non-Windows.


Windows Terminal est l’interface utilisateur phare en mode texte pour Windows. Il illustre les fonctionnalités de l’écosystème et dirige le développement Windows vers l’unifier avec d’autres plateformes. Windows Terminal est également un exemple de création d’une application moderne robuste et complexe qui couvre l’historique et la gamme des API et infrastructures Windows. Selon les définitions ci-dessus, ce produit fonctionne dans un rôle de terminal.

## <a name="major-historical-milestones"></a>Principales étapes majeures historiques

Les principales étapes majeures historiques du sous-système de la console sont mises en œuvre avant le 2014, puis passent à une vue d’ensemble du travail effectué depuis 2014, lorsque le focus renouvelé sur la ligne de commande a été formé dans l’ère Windows 10.

### <a name="initial-implementation"></a>Implémentation initiale

**\[ 1989-années 1990]** le système hôte de console initial a été implémenté comme une émulation de l’environnement dos au sein du système d’exploitation Windows. Son code est enchevêtré et coopératif avec l' [invite de commandes](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd), `cmd.exe` , qui est une représentation de cet environnement dos. Le code système hôte de la console partage les responsabilités et les privilèges avec l’interpréteur de commandes/l’interpréteur de commandes. Il fournit également un niveau de base de services pour d’autres utilitaires de ligne de commande afin d’exécuter des services de la même manière qu’un type CMD.

### <a name="dbcs-for-cjk"></a>DBCS pour CJK

**\[ 1997-1999 \]** dans ce temps, la prise en charge de [DBCS](https://docs.microsoft.com/windows/win32/intl/double-byte-character-sets) (« jeu de caractères codés sur deux octets ») est introduite pour prendre en charge les marchés CJK (chinois, japonais et coréen). Cet effort se traduit par une bifurcation de nombreuses méthodes d’écriture et de lecture à l’intérieur de la console pour fournir à la fois des versions « occidentales » à des caractères codés sur un octet, ainsi qu’une représentation alternative pour les versions « est », où deux octets sont nécessaires pour représenter le vaste tableau de caractères. Cette bifurcation comprenait la représentation en expansion d’une cellule de l’environnement de la console pour qu’elle soit de 1 ou 2 cellules larges, où 1 cellule est étroite (plus haut que large) et 2 cellules est large, pleine largeur ou un carré dans lequel les idéogrammes chinois, japonais et coréens typiques peuvent être inscrits.

### <a name="securityisolation"></a>Sécurité/isolation

**\[ 2005-2009 \]** avec l’expérience du sous-système de la console s’exécutant au sein du processus système critique, la `csrss.exe` connexion des applications clientes assorties, à différents niveaux d’accès, à un seul processus Super critique et privilégié a été observée comme particulièrement dangereuse. Dans cette ère, le sous-système de la console a été divisé en applications clientes, pilotes et serveur. Chaque application peut s’exécuter dans son propre contexte, ce qui réduit les responsabilités et les privilèges dans chacun d’eux. Cette isolation a augmenté la robustesse générale du système, car toute défaillance dans le sous-système de la console n’a plus d’incidence sur les autres fonctionnalités de processus critiques.

### <a name="user-experience-improvements"></a>Améliorations de l’expérience utilisateur

**\[ 2014-2016 \]** après une maintenance en temps réel de la maintenance du sous-système de la console par des équipes assorties de l’organisation, une nouvelle équipe axée sur les développeurs a été formée pour la sienne et les améliorations apportées à la console. Améliorations pendant cette période : la sélection de lignes, le redimensionnement lisse de la fenêtre, le reflux de texte, la copie et le collage, la prise en charge des résolutions élevées et l’accent sur Unicode, y compris la convergence du fractionnement entre les algorithmes de stockage et de manipulation de flux « Ouest » et « est ».

### <a name="virtual-terminal-client"></a>Client terminal virtuel

**\[ 2015-2017 \]** avec l’arrivée du [sous-système Windows pour Linux](https://docs.microsoft.com/windows/wsl/), Microsoft s’efforce d’améliorer l’expérience de l' [arrimeur sur Windows](https://docs.microsoft.com/dotnet/architecture/microservices/container-docker-introduction/docker-defined)et l’adoption d' [OpenSSH](https://docs.microsoft.com/windows-server/administration/openssh/openssh_overview) comme technologie d’exécution à distance de ligne de commande premier, les implémentations initiales des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) ont été introduites dans l’hôte de la console. Cela permettait à la console existante d’agir en tant que terminal, attaché directement à ces applications Linux natives dans leurs environnements respectifs, en rendant les attributs graphiques et de texte à l’écran et en renvoyant les entrées utilisateur dans le dialecte approprié.

### <a name="virtual-terminal-server"></a>Serveur Terminal Server virtuel

**\[ 2018 \]** au cours des vingt dernières années, des alternatives tierces pour l’hôte de la console de la boîte de réception ont été créées pour offrir une productivité de développement supplémentaire, centrée de manière visible dans des personnalisations enrichies et des interfaces avec onglets. Ces applications ont toujours besoin d’exécuter et de masquer la fenêtre hôte de la console. Ils sont attachés en tant qu’application secondaire « cliente » pour récupérer les informations de mémoire tampon dans les boucles d’interrogation lorsque l’application cliente de ligne de commande principale fonctionne. Leur objectif était d’être un terminal, comme sur d’autres plateformes, mais dans le monde de Windows où les terminaux n’étaient pas remplaçables.

Au cours de cette période, l’infrastructure [pseudoconsole](pseudoconsoles.md) a été introduite. Pseudoconsole permet à n’importe quelle application de lancer l’hôte de console en mode non interactif et de devenir l’interface terminal finale pour l’utilisateur. La principale limitation dans le cadre de cet effort était la promesse de compatibilité continue de Windows dans la maintenance de toutes les [API de console Windows](console-functions.md) publiées pour un avenir infini, tout en fournissant une interface d’hébergement de serveur de remplacement qui correspondait à ce qui est attendu sur toutes les autres plateformes : [séquences de terminaux virtuels](console-virtual-terminal-sequences.md). Par conséquent, cet effort a mené à bien l’image miroir de la phase client : les projets _pseudoconsole_ ce qui serait affiché sur l’écran en tant que _séquences de terminaux virtuels_ pour un hôte délégué et interprète les réponses dans les séquences d’entrée de format Windows pour la consommation des applications clientes.

## <a name="roadmap-for-the-future"></a>Feuille de route pour le futur

### <a name="terminal-applications"></a>Applications Terminal Server

**\[ 2019- \]** il s’agit maintenant de l’ère Open source pour le sous-système de la console, en vous concentrant sur le nouveau terminal Windows. Annoncé au cours de la Conférence Microsoft Build en mai 2019, Windows Terminal est entièrement sur GitHub chez [Microsoft/Terminal](https://github.com/microsoft/terminal). La création de l’application Windows Terminal en plus de la plateforme affinée pour [pseudoconsole](pseudoconsoles.md) sera l’objectif de cette ère, en apportant une expérience de terminal de première classe directement aux développeurs sur la plate-forme Windows.

**[Windows Terminal](/terminal/get-started)** envisage non seulement de présenter la plate-forme, notamment la technologie d’interface [WinUI](/apps/winui/) , le modèle d’empaquetage [MSIX](/msix/) et l’architecture du composant [C++/WinRT](/uwp/cpp-and-winrt-apis/) , mais également de valider la plateforme elle-même. Windows Terminal dirige l’organisation Windows pour ouvrir et faire évoluer la plate-forme d’application en fonction des besoins afin de continuer à accroître la productivité des développeurs. Le jeu d’utilisateurs avec pouvoir et les besoins en développement uniques du terminal Windows pilotent la plate-forme Windows moderne requise pour ce que ces marchés ont réellement besoin de Windows.

Dans le système d’exploitation Windows, cela comprend la mise hors service de [l’interface utilisateur de l’hôte de la console classique](./classic-vs-vt.md) à partir de sa position par défaut au profit des [séquences](console-virtual-terminal-sequences.md)de terminaux virtuels, [ConPTY](https://devblogs.microsoft.com/commandline/windows-command-line-introducing-the-windows-pseudo-console-conpty/)et [Windows Terminal Server](/terminal/get-started).

Enfin, cette ère envisage d’offrir un choix complet sur l’expérience par défaut, qu’il s’agisse du produit Windows Terminal ou de tout autre terminal.

### <a name="client-support-library"></a>Bibliothèque de prise en charge client

À l' **\[ \] avenir** , avec la prise en charge et la documentation des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) côté client, nous encourageons vivement les développeurs de l’utilitaire en ligne de commande Windows à utiliser les séquences de terminaux virtuels d’abord sur les API Windows classiques pour tirer parti d’un écosystème unifié avec toutes les plateformes. Toutefois, les autres plateformes comportent un grand nombre de bibliothèques d’assistance côté client pour gérer les entrées comme [ReadLine](https://tiswww.case.edu/php/chet/readline/rltop.html) et affichage graphique comme [ncurses](https://invisible-island.net/ncurses/ncurses.html). Ce futur élément de carte routière représente l’exploration de ce que l’écosystème offre et comment nous pouvons accélérer l’adoption de séquences de terminaux virtuels dans les applications en ligne de commande Windows via l’API de console classique.

### <a name="sequence-passthrough"></a>Séquence passthrough

À l' **\[ avenir \]** , la combinaison des implémentations du client et du serveur de terminal virtuel permet d’obtenir un mixage et une correspondance complets des applications de ligne de commande client et d’hébergement de terminaux. Cette combinaison peut concerner les API de [console Windows](console-functions.md) classiques ou les [séquences de terminaux virtuels](console-virtual-terminal-sequences.md). Toutefois, il y a un coût de surcharge pour la conversion en méthode Windows compatible classique, puis vers la méthode de terminal virtuel plus universelle.

Une fois que le marché a suffisamment adopté les _séquences de terminaux virtuels_ et UTF-8 sur Windows, le travail de conversion/d’interprétation de l’hôte de la console peut éventuellement être désactivé. L’hôte de la console devient alors un service d’appel d’API simple et relaie les appels de l’appareil à l’application d’hébergement via le [pseudoconsole](pseudoconsoles.md). Cette modification augmente les performances et optimise le dialecte des séquences qui peuvent être parlées entre l’application cliente et le terminal. Grâce à cette modification, les scénarios d’interactivité supplémentaires seraient activés et *(enfin)* apportent l’alignement au monde de Windows avec la famille de toutes les autres plateformes dans l’espace d’application en ligne de commande.
