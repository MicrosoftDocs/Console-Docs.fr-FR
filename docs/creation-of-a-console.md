---
title: Création d’une console
description: Le système crée une console quand il démarre un processus de console, qui est un processus en mode caractère dont le point d’entrée est la fonction main.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_creation\_of\_a\_console'
- base.creation\_of\_a\_console
- consoles.creation\_of\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ec2559-cade-447e-8594-5b824d3d3e81
ms.localizationpriority: high
ms.openlocfilehash: bf7993874c4f7c7031dbbcc9ce53a0610157eb75
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357919"
---
# <a name="creation-of-a-console"></a>Création d’une console

Le système crée une console quand il démarre un *processus de console*, qui est un processus en mode caractère dont le point d’entrée est la fonction **main**. Par exemple, le système crée une console quand il démarre le processeur de commande `cmd.exe`. Quand le processeur de commande démarre un nouveau processus de console, l’utilisateur peut spécifier si le système crée une console pour le nouveau processus ou s’il hérite de la console du processeur de commandes.

Un processus peut créer une console en utilisant une des méthodes suivantes :

- Une interface graphique utilisateur (GUI) ou un processus de console peut utiliser la fonction [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) avec **CREATE\_NEW\_CONSOLE** pour créer un processus de console avec une nouvelle console. (Par défaut, un processus de console hérite de la console de son parent, et il n’y a pas de garantie que l’entrée est reçue par le processus auquel elle était destinée.)
- Une interface graphique utilisateur ou un processus de console qui n’est pas actuellement attaché à une console peut utiliser la fonction [**AllocConsole**](allocconsole.md) pour créer une console. (Les processus GUI ne sont pas attachés à une console quand ils sont créés. Les processus de console ne sont pas attachés à une console s’ils sont créés en utilisant [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) avec **DETACHED\_PROCESS**.)

En règle générale, un processus utilise [**AllocConsole**](allocconsole.md) pour créer une console quand une erreur se produit et demande une interaction avec l’utilisateur. Par exemple, un processus GUI peut créer une console quand une erreur se produit qui l’empêche d’utiliser son interface graphique normale, ou un processus de console qui n’interagit normalement pas avec l’utilisateur peut créer une console pour afficher une erreur.

Un processus peut aussi créer une console en spécifiant l’indicateur **CREATE\_NEW** CONSOLE\_dans un appel à [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa). Cette méthode crée une console qui est accessible au processus enfant, mais pas au processus parent. Des consoles distinctes permettent aux processus parents et enfants d’interagir sans conflit avec l’utilisateur. Si cet indicateur n’est pas spécifié lors de la création d’un processus de console, les deux processus sont attachés à la même console, et il n’y a pas de garantie que le processus correct recevra l’entrée qui lui est destinée. Les applications peuvent éviter les confusions en créant des processus enfants qui n’héritent pas des handles de la mémoire tampon d’entrée, ou en n’autorisant qu’un seul processus enfant à la fois pour hériter d’un handle de mémoire tampon d’entrée tout en empêchant le processus parent de lire l’entrée de la console jusqu’à ce que l’enfant ait terminé.

La création d’une console entraîne la création d’une fenêtre de console ainsi que de mémoires tampons d’écran d’E/S distinctes. Le processus associé à la nouvelle console utilise la fonction [**GetStdHandle**](getstdhandle.md) pour récupérer les handles des mémoires tampons d’entrée et d’écran de la nouvelle console. Ces handles permettent au processus d’accéder à la console.

Quand un processus utilise [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa), il peut spécifier une structure [**STARTUPINFO**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa), dont les membres contrôlent les caractéristiques de la première nouvelle console (le cas échéant) créée pour le processus enfant. La structure **STARTUPINFO** spécifiée dans l’appel à **CreateProcess** affecte une console créée si l’indicateur **CREATE\_NEW\_CONSOLE** est spécifié. Elle affecte également une console créée si le processus enfant utilise par la suite [**AllocConsole**](allocconsole.md). Les caractéristiques suivantes de la console peuvent être spécifiées :

- Taille de la nouvelle fenêtre de console, en cellules de caractères
- Emplacement de la nouvelle fenêtre de console, en coordonnées de pixels d’écran
- Taille de la mémoire tampon d’écran de la nouvelle console, en cellules de caractères
- Attributs de couleur de texte et d’arrière-plan de la mémoire tampon d’écran de la nouvelle console
- Nom d’affichage de la barre de titre de la fenêtre de la nouvelle console

Le système utilise les valeurs par défaut si les valeurs de [**STARTUPINFO**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa) ne sont pas spécifiées. Un processus enfant peut utiliser la fonction [**GetStartupInfo**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getstartupinfow) pour déterminer les valeurs dans sa structure **STARTUPINFO**.

Un processus ne peut pas changer l’emplacement de sa fenêtre de console sur l’écran, mais les fonctions de console suivantes sont disponibles pour définir ou récupérer les autres propriétés spécifiées dans la structure [**STARTUPINFO**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).

| Fonction | Description |
|-|-|
| [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) | Récupère la taille de la fenêtre, la taille de la mémoire tampon d’écran et les attributs de couleur. |
| [**SetConsoleWindowInfo**](setconsolewindowinfo.md)  | Change la taille de la fenêtre de console.  |
| [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) | Change la taille de la mémoire tampon d’écran de console. |
| [**SetConsoleTextAttribute**](setconsoletextattribute.md) | Définit les attributs de couleur.  |
| [**SetConsoleTitle**](setconsoletitle.md)  | Définit le titre de la fenêtre de console. |
| [**GetConsoleTitle**](getconsoletitle.md)  | Récupère le titre de la fenêtre de console.  |

Un processus peut utiliser la fonction [**FreeConsole**](freeconsole.md) pour se détacher d’une console héritée ou d’une console créée par [**AllocConsole**](allocconsole.md).

Un processus peut utiliser la fonction [**AttachConsole**](attachconsole.md) pour s’attacher à une autre session de console existante après avoir utilisé [**FreeConsole**](freeconsole.md) pour se détacher de sa propre session (ou s’il n’y a aucune autre session attachée).