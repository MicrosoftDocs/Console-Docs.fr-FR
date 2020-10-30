---
title: API de console classiques et séquences de terminaux virtuels
description: Décrit le contraste entre la surface de l’API de la console Win32 classique et le concept des séquences de terminaux virtuels, parfois également appelées séquences d’échappement, pour écrire des applications en ligne de commande.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, terminal, terminal virtuel, séquences d’échappement, VT, VT100, API de console
ms.prod: console
ms.openlocfilehash: 0fdd39cab5b8f6ca5cc1602c8e68ec7f2a2303ad
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039579"
---
# <a name="classic-console-apis-versus-virtual-terminal-sequences"></a>API de console classiques et séquences de terminaux virtuels

Nous vous recommandons de remplacer l' **API de console Windows** classique par des **séquences de terminaux virtuels** . Cet article présente la différence entre les deux et évoque les raisons de notre recommandation.

## <a name="definitions"></a>Définitions

La surface de l’API de la **[console Windows](console-functions.md)** classique est définie comme la série d’interfaces fonctionnelles du langage C sur `kernel32.dll` avec « console » dans le nom.

Les **[séquences de terminaux virtuels](console-virtual-terminal-sequences.md)** sont définies comme un langage de commandes incorporées dans les flux de sortie standard et d’entrée. Les séquences de terminaux virtuels utilisent des caractères d’échappement non imprimables pour les commandes de signalisation entrelacées avec du texte imprimable normal.

## <a name="history"></a>Historique

La **console Windows** fournit une surface d’API étendue pour les applications de ligne de commande client pour manipuler à la fois le tampon d’affichage de sortie et la mémoire tampon d’entrée utilisateur. Toutefois, d’autres plateformes non-Windows n’ont jamais permis cette approche pilotée par les API spécifique à leurs environnements de ligne de commande, en choisissant plutôt d’utiliser des séquences de terminaux virtuels incorporées dans les flux de sortie standard d’entrée et standard. *(Pendant une période, Microsoft a également pris en charge ce comportement dans les premières éditions de DOS et Windows par le biais d’un pilote appelé ANSI.SYS.)*

En revanche, les **séquences de terminaux virtuels** (dans divers dialectes) pilotent les opérations de l’environnement de ligne de commande pour toutes les autres plateformes. Ces séquences sont enracinées dans une [norme](https://www.ecma-international.org/publications/standards/Ecma-048.htm) et une série d’extensions ECMA par de nombreux fournisseurs qui effectuent le suivi des terminaux Digital Equipment Corporation et Tektronix, par le biais de terminaux logiciels plus modernes et courants, tels que [xterm](https://invisible-island.net/xterm/). De nombreuses extensions existent au sein du domaine de séquence de terminaux virtuels et certaines séquences sont plus largement prises en charge que d’autres, mais il est possible de dire que le monde s’est standardisé en tant que langage de commande pour les expériences de ligne de commande avec un sous-ensemble connu pris en charge par pratiquement toutes les applications clientes terminal et de ligne de commande.

## <a name="cross-platform-support"></a>Prise en charge multiplateforme

Les **séquences de terminaux virtuels** sont prises en charge de façon native sur les plateformes, ce qui rend les applications terminal et les utilitaires de ligne de commande facilement transférables entre les versions et les variantes de systèmes d’exploitation, à l’exception de Windows.

En revanche, les **API de console Windows** sont uniquement prises en charge sur Windows. Un adaptateur étendu ou une bibliothèque de traduction doit être écrit entre Windows et le terminal virtuel, ou vice versa, lors de la tentative de portage des utilitaires de ligne de commande d’une plateforme ou d’une autre.

### <a name="remote-access"></a>Accès à distance

Les **séquences de terminaux virtuels** possèdent un avantage majeur pour l’accès à distance. Ils ne nécessitent aucun travail supplémentaire pour le transport ou effectuent des appels de procédure distante, sur ce qui est requis pour configurer une connexion de ligne de commande à distance standard. Il suffit de connecter un canal de transport sortant et un canal de transport entrant (ou un canal bidirectionnel unique) sur un canal, un socket, un fichier, un port série ou tout autre appareil pour fournir complètement toutes les informations requises pour qu’une application contienne ces séquences sur un hôte distant.

En revanche, les **API de console Windows** sont uniquement accessibles sur l’ordinateur local et tous les efforts à distance nécessitent la création d’une couche d’appel et de transport à distance complète au-delà d’un simple canal.

### <a name="separation-of-concerns"></a>Séparation des responsabilités

Certaines **API de console Windows** fournissent un accès de bas niveau aux mémoires tampons d’entrée et de sortie ou aux fonctions pratiques pour les lignes de commande interactives. Cela peut inclure les alias et l’historique des commandes programmés dans le sous-système de la console et l’environnement hôte, plutôt que dans l’application cliente de ligne de commande elle-même.

En revanche, d' **autres plateformes** rendent la mémoire de l’état actuel de l’application et les fonctionnalités pratiques de la responsabilité de l’utilitaire de ligne de commande ou de l’interpréteur de commandes lui-même.

La **console Windows** de gestion de cette responsabilité dans l’hôte de la console et l’API permet d’écrire plus rapidement et plus facilement une application en ligne de commande avec ces fonctionnalités, en supprimant la responsabilité de mémoriser l’état du dessin ou de gérer les fonctionnalités de l’édition. Toutefois, il est presque impossible de connecter ces activités à distance sur des plateformes, des versions ou des scénarios en raison des variations des implémentations et de la disponibilité. Cette façon de gérer la responsabilité rend également l’expérience interactive finale de ces applications en ligne de commande Windows entièrement dépendante de l’implémentation, des priorités et du cycle de publication de l’hôte de console.

Par exemple, les fonctionnalités avancées de modification de ligne, comme la mise en surbrillance de la syntaxe et la sélection complexe, ne sont possibles que si une application en ligne de commande gère elle-même les problèmes. La console ne pouvait jamais avoir suffisamment de contexte pour bien comprendre ces scénarios de manière générale, comme dans le cas de l’application cliente.

En revanche, d’autres plateformes utilisent des **séquences de terminaux virtuels** pour gérer ces activités et la communication de terminal virtuel lui-même par le biais de bibliothèques côté client réutilisables, telles que [ReadLine](https://tiswww.case.edu/php/chet/readline/rltop.html) et [ncurses](https://invisible-island.net/ncurses/ncurses.html). Le terminal final est uniquement responsable de l’affichage des informations et de la réception des entrées via ce canal de communication bidirectionnel.

### <a name="wrong-way-verbs"></a>Verbes de Wrong-Way

Avec la **console Windows** , certaines actions peuvent être effectuées dans la direction opposée au naturel sur les flux d’entrée et de sortie. Cela permet aux applications en ligne de commande Windows d’éviter la préoccupation de gérer leurs propres tampons. Il permet également aux applications de ligne de commande Windows d’effectuer des opérations avancées, telles que la simulation/l’injection d’entrée pour le compte d’un utilisateur, ou la lecture d’un historique de ce qui a été écrit.

Bien que cela offre une alimentation supplémentaire aux applications Windows opérant dans un contexte utilisateur spécifique sur un ordinateur unique, elle fournit également un vecteur pour franchir la sécurité et les niveaux de privilège ou les domaines lorsqu’ils sont utilisés dans certains scénarios. Ces scénarios incluent l’utilisation de contextes sur le même ordinateur, ou dans des contextes sur un autre ordinateur ou environnement.

D’autres plateformes, qui utilisent des **séquences de terminaux virtuels** , n’autorisent pas cette activité. L’objectif de notre recommandation de passer de la console Windows classique aux séquences de terminaux virtuels est de converger avec cette stratégie pour des raisons d’interopérabilité et de sécurité.

### <a name="direct-window-access"></a>Accès direct à la fenêtre

La surface de l’API de la **console Windows** fournit le handle de fenêtre exact à la fenêtre d’hébergement. Cela permet à un utilitaire de ligne de commande d’effectuer des opérations de fenêtre avancées en atteignant la large gamme d’API Win32 autorisées sur un handle de fenêtre. Ces API Win32 peuvent manipuler l’état de la fenêtre, le frame, l’icône ou d’autres propriétés de la fenêtre.

En revanche, sur d’autres plateformes avec des **séquences de terminaux virtuels** , il existe un ensemble étroit de commandes pouvant être exécutées sur la fenêtre. Ces commandes peuvent effectuer des opérations telles que la modification de la taille de la fenêtre ou du titre affiché, mais elles doivent être effectuées dans la même bande et sous le même contrôle que le reste du flux.

À mesure que Windows a évolué, les contrôles de sécurité et les restrictions sur les handles de fenêtre ont augmenté. En outre, la nature et l’existence d’un descripteur de fenêtre adressable par l’application sur n’importe quel élément d’interface utilisateur spécifique a évolué, en particulier avec la prise en charge accrue des facteurs de forme de périphérique et des plateformes. Cela permet d’accéder directement aux applications en ligne de commande fragiles à mesure que la plateforme et les expériences évoluent.

### <a name="unicode"></a>Unicode

UTF-8 est l’encodage accepté pour les données Unicode sur presque toutes les plateformes modernes, car il a un juste équilibre entre la portabilité, la taille de stockage et le temps de traitement. Toutefois, Windows a choisi l’encodage UTF-16 comme principal codage pour les données Unicode. La prise en charge d’UTF-8 s’améliore dans Windows et l’utilisation de ces formats Unicode n’exclut pas l’utilisation d’autres encodages.

La plateforme de la **console Windows** est prise en charge et continuera à prendre en charge l’ensemble des pages de codes et des encodages existants. Utilisez UTF-16 pour une compatibilité maximale entre les différentes versions de Windows et effectuez une traduction algorithmique avec UTF-8, si nécessaire. L’augmentation de la prise en charge d’UTF-8 est en cours pour le système de la console.

La prise en charge d’UTF-16 dans la console peut être utilisée sans aucune configuration supplémentaire via la variante _W_ de toutes les API de console. il s’agit d’un choix plus probable pour les applications qui sont déjà bien au format UTF-16 par le biais de la communication avec la `wchar_t` variante et _W_ des autres fonctions et produits de la plate-forme Microsoft et Windows.

La prise en charge d’UTF-8 dans la console peut être utilisée par le biais d' _une_ variante d’API de console sur des handles de console après avoir défini la page de codes sur `65001` ou `CP_UTF8` avec les méthodes [**SetConsoleOutputCP**](setconsoleoutputcp.md) et [**SetConsoleCP**](setconsolecp.md) , selon le cas. La définition des pages de codes à l’avance n’est nécessaire que si la machine n’a pas choisi « utiliser Unicode UTF-8 pour la prise en charge des langues mondiales » dans la section paramètres pour les applications non-Unicode dans la zone région du panneau de configuration.

>[!NOTE]
> À l’heure actuelle, UTF-8 est entièrement pris en charge sur le flux de sortie standard avec les méthodes [**WriteConsole**](writeconsole.md) et [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) . La prise en charge du flux d’entrée varie selon le mode d’entrée et continue à s’améliorer au fil du temps. En particulier, les modes **[« cuits »](high-level-console-modes.md)** par défaut en entrée ne prennent pas encore en charge UTF-8. L’état actuel de ce travail est disponible à l’adresse suivante : [**Microsoft/Terminal # °**](https://github.com/microsoft/terminal/issues/7777) github. La solution de contournement consiste à utiliser l’UTF-16 convertible algorithmiquement pour lire les entrées via [**ReadConsoleW**](readconsole.md) ou [**ReadConsoleInputW**](readconsoleinput.md) jusqu’à ce que les problèmes en suspens soient résolus.

## <a name="recommendations"></a>Recommandations

Pour tous les développements nouveaux et en continu sur Windows, les **séquences de terminaux virtuels sont recommandées** comme méthode d’interaction avec le terminal. Cela convergera les applications clientes de ligne de commande Windows avec le style de programmation d’application sur toutes les autres plateformes.

### <a name="exceptions-for-using-windows-console-apis"></a>Exceptions pour l’utilisation des API de console Windows

Un **sous-ensemble limité d’API de console Windows est toujours nécessaire** pour établir l’environnement initial. La plate-forme Windows diffère encore des autres dans le processus, les signaux, les périphériques et la gestion de l’encodage :

- Les handles standard d’un processus sont toujours contrôlés avec **[GetStdHandle](getstdhandle.md)** et **[SetStdHandle](setstdhandle.md)** .

- La configuration des modes de console sur un handle pour s’abonner à une séquence de terminaux virtuels est gérée avec **[GetConsoleMode](getconsolemode.md)** et **[SetConsoleMode](setconsolemode.md)** .

- La déclaration de la page de codes ou la prise en charge UTF-8 est effectuée avec les méthodes [**SetConsoleOutputCP**](setconsoleoutputcp.md) et [**SetConsoleCP**](setconsolecp.md) .

- Un certain niveau de gestion globale des processus peut être nécessaire avec [**AllocConsole**](allocconsole.md), [**AttachConsole**](attachconsole.md) et [**FreeConsole**](freeconsole.md) pour rejoindre ou abandonner une session de périphérique de la console.

- Les signaux et la gestion des signaux continueront d’être effectués avec [**SetConsoleCtrlHandler**](setconsolectrlhandler.md), [**HandlerRoutine**](handlerroutine.md)et [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md).

- La communication avec les descripteurs de l’appareil de la console peut être effectuée avec [**WriteConsole**](writeconsole.md) et [**ReadConsole**](readconsole.md). Elles peuvent également être exploitées par le biais de runtimes de langage de programmation dans les formulaires de :-C Runtime (CRT) : [e/s de flux](https://docs.microsoft.com/cpp/c-runtime-library/stream-i-o) comme **printf** , **scanf** , **putc** , **GETC** ou [d’autres niveaux de fonctions d’e/s](https://docs.microsoft.com/cpp/c-runtime-library/input-and-output).
        -Bibliothèque standard C++ (STL) : [iostream](https://docs.microsoft.com/cpp/standard-library/iostream) comme **cout** et **CIN** .
        -Runtime .NET : [System. console](https://docs.microsoft.com/dotnet/api/system.console) , comme **console. WriteLine** .

- Les applications qui doivent être conscientes des modifications de taille de fenêtre devront toujours utiliser [**ReadConsoleInput**](readconsoleinput.md) pour les recevoir avec des événements clés, car **ReadConsole** seul les ignore.

- La recherche de la taille de la fenêtre doit toujours être effectuée avec [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) pour les applications tentant de dessiner des colonnes, des grilles ou de remplir l’affichage. La taille de la fenêtre et de la mémoire tampon correspond à celle d’une session [pseudoconsole](pseudoconsoles.md) .

## <a name="future-planning-and-pseudoconsole"></a>Planification et pseudoconsole à venir

Il n’est pas prévu de supprimer les API de console Windows de la plateforme.

En revanche, l’hôte de console Windows a fourni la technologie **[pseudoconsole](pseudoconsoles.md)** pour traduire les appels d’application en ligne de commande Windows existants en séquences de terminaux virtuels et les transférer vers un autre environnement d’hébergement à distance ou sur plusieurs plateformes.

Cette traduction n’est pas parfaite. Elle nécessite que la fenêtre hôte de la console maintienne un environnement simulé de ce que Windows aurait affiché à l’utilisateur. Il projette ensuite un réplica de cet environnement simulé sur l’hôte **pseudoconsole** . Tous les appels d’API de console Windows sont exécutés dans l’environnement simulé pour répondre aux besoins de l’application cliente de ligne de commande héritée. Seuls les effets sont propagés sur l’hôte final.

Une application en ligne de commande désire la compatibilité complète entre les plateformes et la prise en charge complète de tous les nouveaux scénarios et fonctionnalités sur Windows et ailleurs est donc recommandée pour passer aux séquences de terminaux virtuels et ajuster l’architecture des applications en ligne de commande pour les aligner sur toutes les plateformes.

Pour plus d’informations sur cette transition Windows pour les applications en ligne de commande, consultez notre feuille de route pour l' [écosystème](ecosystem-roadmap.md).
