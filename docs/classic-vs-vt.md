---
title: API de console classiques et séquences de terminaux virtuels
description: Décrit la différence entre la surface de l’API de console Win32 classique et le concept des séquences de terminaux virtuels, parfois également appelées séquences d’échappement, pour écrire des applications en ligne de commande.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, terminal, terminal virtuel, séquences d’échappement, vt, vt100, api de console
ms.prod: console
ms.localizationpriority: high
ms.openlocfilehash: 2af1b2e2760df42dc60a991dad1afacf27831ec5
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357809"
---
# <a name="classic-console-apis-versus-virtual-terminal-sequences"></a>API de console classiques et séquences de terminaux virtuels

Nous vous recommandons de remplacer l'**API de console Windows** classique par des **séquences de terminaux virtuels**. Cet article présente la différence entre les deux et évoque les raisons de notre recommandation.

## <a name="definitions"></a>Définitions

La surface de l’ **[API de console Windows](console-functions.md)** classique est définie comme la série d’interfaces fonctionnelles du langage C sur `kernel32.dll` dont le nom contient « Console ».

Les **[séquences de terminaux virtuels](console-virtual-terminal-sequences.md)** sont définies comme un langage de commandes incorporé dans les flux de sortie et d’entrée standard. Les séquences de terminaux virtuels utilisent des caractères d’échappement non affichables pour signaler les commandes entrelacées avec du texte affichable normal.

## <a name="history"></a>Historique

La **console Windows** fournit une surface d’API étendue permettant aux applications clientes en ligne de commande de manipuler à la fois la mémoire tampon d’affichage de sortie et la mémoire tampon d’entrée utilisateur. Toutefois, d’autres plateformes non-Windows n’ont jamais offert cette approche spécifique pilotée par les API à leurs environnements de ligne de commande, choisissant plutôt d’utiliser des séquences de terminaux virtuels incorporées dans les flux d’entrée et de sortie standard. *(Pendant un certain temps, Microsoft a également pris en charge ce comportement dans les premières éditions de DOS et Windows par le biais d’un pilote nommé ANSI.SYS.)*

À l’inverse, les **séquences de terminaux virtuels** (dans différents dialectes) pilotent les opérations de l’environnement de ligne de commande de toutes les autres plateformes. Ces séquences prennent racine dans une [norme ECMA](https://www.ecma-international.org/publications/standards/Ecma-048.htm) et des séries d’extensions de nombreux fournisseurs qui remontent aux terminaux Digital Equipment Corporation et Tektronix, jusqu’aux terminaux logiciels plus modernes et courants tels que [xterm](https://invisible-island.net/xterm/). De nombreuses extensions existent au sein du domaine de séquences de terminaux virtuels, et certaines sont plus largement prises en charge que d’autres, mais il est généralement admis aujourd’hui que cette approche a été adoptée en guise de norme de langage de commande pour les expériences de ligne de commande, dont une partie bien connue est prise en charge par pratiquement toutes les applications clientes de terminal et en ligne de commande.

## <a name="cross-platform-support"></a>Prise en charge multiplateforme

Les **séquences de terminaux virtuels** sont prises en charge en mode natif sur les plateformes, ce qui rend les applications de terminal et les utilitaires en ligne de commande facilement transférables entre les versions et les variantes de systèmes d’exploitation, à l’exception de Windows.

À l’inverse, les **API de console Windows** sont uniquement prises en charge sur Windows. Une bibliothèque étendue de traduction ou d’adaptateurs doit être écrite entre Windows et le terminal virtuel, ou vice versa, en cas de tentative de portage des utilitaires en ligne de commande à partir d’une plateforme ou d’une autre.

### <a name="remote-access"></a>Accès à distance

Les **séquences de terminaux virtuels** offrent un avantage indéniable en matière d’accès à distance. Elles ne demandent aucun travail supplémentaire pour le transport ou l’exécution d’appels de procédure distante, par rapport à ce qui est requis pour configurer une connexion de ligne de commande à distance standard. Il suffit de connecter un canal de transport sortant et un canal de transport entrant (ou un canal bidirectionnel unique) sur un canal, un socket, un fichier, un port série ou tout autre appareil pour transporter toutes les informations requises par une application communiquant ces séquences à un hôte distant.

Les **API de console Windows**, quant à elles, sont uniquement accessibles sur l’ordinateur local, et tous les efforts visant à activer l’accès à distance nécessiteraient la création d’une couche complète d’appel et de transport à distance au-delà d’un simple canal.

### <a name="separation-of-concerns"></a>Séparation des responsabilités

Certaines **API de console Windows** fournissent un accès de bas niveau aux mémoires tampons d’entrée et de sortie ou aux fonctions pratiques pour les lignes de commande interactives. Cela peut inclure des alias et un historique des commandes programmés dans le sous-système de la console et l’environnement hôte, plutôt que dans l’application cliente en ligne de commande elle-même.

À l’inverse, les **autres plateformes** attribuent la responsabilité de la mémoire de l’état actuel de l’application et des fonctionnalités pratiques à l’utilitaire en ligne de commande ou à l’interpréteur de commandes lui-même.

La façon dont la **console Windows** gère cette responsabilité dans l’hôte de console et l’API permet d’écrire plus rapidement et plus facilement une application en ligne de commande avec ces fonctionnalités, et évite de devoir mémoriser l’état du dessin ou de gérer les modifications des fonctionnalités pratiques. Toutefois, cela rend presque impossible la connexion de ces activités à distance entre plateformes, versions ou scénarios, en raison des variations d’implémentation et de disponibilité. Cette façon de gérer la responsabilité rend également l’expérience interactive finale de ces applications en ligne de commande Windows entièrement dépendante de l’implémentation, des priorités et du cycle de mise en production de l’hôte de console.

Par exemple, des fonctionnalités avancées de modification de ligne, comme la coloration syntaxique et la sélection complexe, ne sont possibles que lorsqu’une application en ligne de commande gère elle-même les aspects liés à la modification. La console ne pourrait jamais avoir suffisamment de contexte pour comprendre entièrement ces scénarios de manière globale, comme le peut l’application cliente.

À l’inverse, les autres plateformes utilisent des **séquences de terminaux virtuels** pour gérer ces activités et la communication du terminal virtuel proprement dite par le biais de bibliothèques côté client réutilisables, comme [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) et [ncurses](https://invisible-island.net/ncurses/ncurses.html). Le terminal final est uniquement responsable de l’affichage des informations et de la réception de l’entrée par le biais de ce canal de communication bidirectionnel.

### <a name="wrong-way-verbs"></a>Verbes à direction inverse

Avec la **console Windows**, certaines actions peuvent être effectuées dans la direction opposée à la normale sur les flux d’entrée et de sortie. Cela évite aux applications en ligne de commande Windows de devoir gérer leurs propres mémoires tampons. Cela permet également aux applications en ligne de commande Windows d’effectuer des opérations avancées, telles que la simulation/l’injection d’entrée pour le compte d’un utilisateur, ou la relecture d’une partie de l’historique de ce qui a été écrit.

Même si cela donne une puissance supplémentaire aux applications Windows opérant dans un contexte utilisateur spécifique sur un ordinateur unique, cela donne également un vecteur pour outrepasser la sécurité et les niveaux de privilège ou les domaines en cas d’utilisation dans certains scénarios. Ces scénarios incluent les opérations inter-contextes sur le même ordinateur, ou entre contextes vers un autre ordinateur ou environnement.

Les autres plateformes, qui utilisent des **séquences de terminaux virtuels**, n’autorisent pas cette activité. L’objectif de notre recommandation concernant la transition de la console Windows classique aux séquences de terminaux virtuels est la convergence avec cette stratégie pour des raisons d’interopérabilité et de sécurité.

### <a name="direct-window-access"></a>Accès direct aux fenêtres

La **surface de l’API de console Windows** fournit le handle de fenêtre exact vers la fenêtre d’hébergement. Cela permet à un utilitaire en ligne de commande d’effectuer des opérations de fenêtre avancées en tirant parti de la large gamme d’API Win32 autorisées sur un handle de fenêtre. Ces API Win32 peuvent manipuler l’état de la fenêtre, le frame, l’icône ou d’autres propriétés de la fenêtre.

À l’inverse, sur les autres plateformes avec des **séquences de terminaux virtuels**, il existe un jeu étroit de commandes pouvant être exécutées sur la fenêtre. Ces commandes peuvent effectuer des opérations telles que le changement de la taille de la fenêtre ou du titre affiché, mais elles doivent être effectuées dans la même bande et sous le même contrôle que le reste du flux.

À mesure que Windows a évolué, les contrôles de sécurité et les restrictions sur les handles de fenêtre ont augmenté. De plus, la nature et l’existence d’un handle de fenêtre adressable par l’application sur n’importe quel élément d’interface utilisateur spécifique ont aussi évolué, en particulier avec la prise en charge accrue des facteurs de forme d’appareils et de plateformes. Cela rend l’accès direct aux fenêtres d’applications en ligne de commande fragile à mesure que la plateforme et les expériences évoluent.

### <a name="unicode"></a>Unicode

UTF-8 est l’encodage accepté pour les données Unicode sur presque toutes les plateformes modernes, car il offre un juste équilibre entre la portabilité, la taille de stockage et le temps de traitement. Toutefois, Windows a traditionnellement choisi l’encodage UTF-16 comme principal encodage pour les données Unicode. La prise en charge d’UTF-8 va croissante dans Windows, et l’utilisation de ces formats Unicode n’exclut pas l’usage d’autres encodages.

La plateforme de **console Windows** prend en charge et continuera à prendre en charge l’ensemble des pages de codes et encodages existants. Utilisez UTF-16 pour une compatibilité maximale entre les différentes versions de Windows, et effectuez une traduction algorithmique avec UTF-8 si nécessaire. L’extension de la prise en charge d’UTF-8 est en cours pour le système de console.

La prise en charge d’UTF-16 dans la console peut être utilisée sans aucune configuration supplémentaire par le biais de la variante _W_ de toutes les API de console, et s’avère être un choix plus probable pour les applications faisant déjà usage d’UTF-16 par le biais de la communication avec le `wchar_t` et la variante _W_ d’autres fonctions et produits de la plateforme Microsoft et Windows.

La prise en charge d’UTF-8 dans la console peut être utilisée par le biais de la variante _A_ des API de console sur les handles de console après avoir défini la page de codes sur `65001` ou `CP_UTF8` avec les méthodes [**SetConsoleOutputCP**](setconsoleoutputcp.md) et [**SetConsoleCP**](setconsolecp.md), le cas échéant. La définition préalable des pages de codes n’est nécessaire que si la machine n’a pas choisi « Utiliser Unicode UTF-8 pour la prise en charge des langues mondiales » dans les paramètres des applications non-Unicode, dans la section Région du Panneau de configuration.

>[!NOTE]
> À l’heure actuelle, UTF-8 est entièrement pris en charge sur le flux de sortie standard avec les méthodes [**WriteConsole**](writeconsole.md) et [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile). La prise en charge du flux d’entrée varie en fonction du mode d’entrée, et continuera à s’améliorer au fil du temps. En particulier, les modes **[« cooked »](high-level-console-modes.md)** par défaut sur l’entrée ne prennent pas encore complètement en charge UTF-8. L’état actuel de ce travail est accessible à [**microsoft/terminal#7777**](https://github.com/microsoft/terminal/issues/7777) sur GitHub. La solution de contournement consiste à utiliser l’UTF-16 traduisible algorithmiquement pour lire l’entrée par le biais de [**ReadConsoleW**](readconsole.md) ou [**ReadConsoleInputW**](readconsoleinput.md) jusqu’à ce que les problèmes en suspens soient résolus.

## <a name="recommendations"></a>Recommandations

Pour toutes les tâches de développement nouvelles et en cours sur Windows, **les séquences de terminaux virtuels sont les méthodes d’interaction avec le terminal recommandées**. Cela permet d’aligner les applications clientes en ligne de commande Windows avec le style de programmation d’application sur toutes les autres plateformes.

### <a name="exceptions-for-using-windows-console-apis"></a>Exceptions pour l’utilisation des API de console Windows

Un **sous-ensemble limité d’API de console Windows est toujours nécessaire** pour établir l’environnement initial. La plateforme Windows diffère encore des autres en termes de processus, de signal, d’appareil et de gestion de l’encodage :

- Les handles standard d’un processus sont toujours contrôlés avec **[GetStdHandle](getstdhandle.md)** et **[SetStdHandle](setstdhandle.md)** .

- La configuration des modes de console sur un handle afin d’adopter la prise en charge des séquences de terminaux virtuels sera gérée avec **[GetConsoleMode](getconsolemode.md)** et **[SetConsoleMode](setconsolemode.md)** .

- La déclaration de la page de codes ou de la prise en charge d’UTF-8 s’effectue avec les méthodes [**SetConsoleOutputCP**](setconsoleoutputcp.md) et [**SetConsoleCP**](setconsolecp.md).

- Un certain niveau de gestion globale des processus peut être requis avec [**AllocConsole**](allocconsole.md), [**AttachConsole**](attachconsole.md) et [**FreeConsole**](freeconsole.md) pour rejoindre ou quitter une session d’appareil de console.

- Les signaux et la gestion des signaux continueront à être menés avec [**SetConsoleCtrlHandler**](setconsolectrlhandler.md), [**HandlerRoutine**](handlerroutine.md) et [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md).

- La communication avec les handles d’appareil de console peut être menée avec [**WriteConsole**](writeconsole.md) et [**ReadConsole**](readconsole.md). Ces opérations peuvent également être optimisées par le biais de runtimes de langage de programmation sous les formes suivantes : Runtime -C (CRT) : [E/S de flux](/cpp/c-runtime-library/stream-i-o) comme **printf**, **scanf**, **putc**, **GETC** ou [autres niveaux de fonctions d’E/S](/cpp/c-runtime-library/input-and-output).
        - Bibliothèque standard C++ (STL) : [iostream](/cpp/standard-library/iostream) comme **cout** et **cin**.
        - Runtime .NET : [System.Console](/dotnet/api/system.console) comme **Console.WriteLine**.

- Les applications qui doivent avoir connaissance des changements de la taille de fenêtre doivent toujours utiliser [**ReadConsoleInput**](readconsoleinput.md) pour les recevoir entrelacées avec des événements clés, car **ReadConsole** seul les ignorera.

- La recherche de la taille de fenêtre doit toujours être effectuée avec [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) pour les applications tentant de tracer des colonnes ou des grilles ou de remplir l’affichage. La taille de la fenêtre et de la mémoire tampon correspondent dans une session de [pseudoconsole](pseudoconsoles.md).

## <a name="future-planning-and-pseudoconsole"></a>Planification future et pseudoconsole

Il n’est pas prévu de supprimer les API de console Windows de la plateforme.

Au contraire, l’hôte de console Windows a fourni la technologie de **[pseudoconsole](pseudoconsoles.md)** pour traduire les appels d’application en ligne de commande Windows existants en séquences de terminaux virtuels, et les transférer à un autre environnement d’hébergement distant ou d’une plateforme à une autre.

Cette traduction n’est pas parfaite. Elle exige que la fenêtre hôte de console conserve un environnement simulé de ce que Windows aurait affiché à l’utilisateur. Elle projette ensuite un réplica de cet environnement simulé sur l’hôte de **pseudoconsole**. Tous les appels d’API de console Windows sont exécutés dans l’environnement simulé afin de répondre aux besoins de l’application cliente en ligne de commande héritée. Seuls les effets sont propagés sur l’hôte final.

Une application en ligne de commande souhaitant bénéficier d’une compatibilité complète multiplateforme et de la prise en charge complète de tous les nouveaux scénarios et fonctionnalités sur Windows et ailleurs doit donc de préférence passer aux séquences de terminaux virtuels. L’architecture des applications en ligne de commande doit par ailleurs être ajustée pour être alignée avec toutes les plateformes.

Pour plus d’informations sur cette transition de Windows pour les applications en ligne de commande, consultez notre [feuille de route de l’écosystème](ecosystem-roadmap.md).