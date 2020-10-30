---
title: Création d’une console
description: Le système crée une nouvelle console lorsqu’il démarre un processus de console, un processus en mode caractère dont le point d’entrée est la fonction principale.
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
ms.openlocfilehash: 78a77044452fe2287a7cea0bfe5a6542eceef337
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038237"
---
# <a name="creation-of-a-console"></a>Création d’une console

Le système crée une nouvelle console lorsqu’il démarre un *processus de console* , un processus en mode caractère dont le point d’entrée est la fonction **principale** . Par exemple, le système crée une nouvelle console lorsqu’il démarre le processeur de commandes `cmd.exe` . Lorsque le processeur de commande démarre un nouveau processus de console, l’utilisateur peut spécifier si le système crée une nouvelle console pour le nouveau processus ou s’il hérite de la console du processeur de commandes.

Un processus peut créer une console à l’aide de l’une des méthodes suivantes :

- Une interface utilisateur graphique (GUI) ou un processus de console peut utiliser la fonction [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) avec **Create \_ New \_ console** pour créer un processus de console avec une nouvelle console. (Par défaut, un processus de console hérite de la console de son parent, et il n’y a aucune garantie que l’entrée est reçue par le processus auquel elle était destinée.)
- Une interface utilisateur graphique ou un processus de console qui n’est pas actuellement attaché à une console peut utiliser la fonction [**AllocConsole**](allocconsole.md) pour créer une nouvelle console. (Les processus GUI ne sont pas attachés à une console lorsqu’ils sont créés. Les processus de console ne sont pas attachés à une console s’ils sont créés à l’aide de [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) avec un **\_ processus détaché** .)

En règle générale, un processus utilise [**AllocConsole**](allocconsole.md) pour créer une console lorsqu’une erreur se produit et nécessite une interaction avec l’utilisateur. Par exemple, un processus d’interface graphique utilisateur peut créer une console lorsqu’une erreur se produit, l’empêchant d’utiliser son interface graphique normale, ou un processus de console qui n’interagit normalement pas avec l’utilisateur peut créer une console pour afficher une erreur.

Un processus peut également créer une console en spécifiant l’indicateur **Create \_ New \_ console** dans un appel à [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425). Cette méthode crée une nouvelle console qui est accessible au processus enfant, mais pas au processus parent. Des consoles distinctes permettent aux processus parents et enfants d’interagir sans conflit avec l’utilisateur. Si cet indicateur n’est pas spécifié lors de la création d’un processus de console, les deux processus sont attachés à la même console, et il n’y a aucune garantie que le processus correct recevra l’entrée qui lui est destinée. Les applications peuvent éviter toute confusion en créant des processus enfants qui n’héritent pas de handles de la mémoire tampon d’entrée, ou en n’autorisant qu’un seul processus enfant à la fois pour hériter d’un handle de mémoire tampon d’entrée tout en empêchant le processus parent de lire l’entrée de la console jusqu’à la fin de l’enfant.

La création d’une nouvelle console entraîne une nouvelle fenêtre de console, ainsi que des mémoires tampons d’écran d’e/s distinctes. Le processus associé à la nouvelle console utilise la fonction [**GetStdHandle**](getstdhandle.md) pour récupérer les descripteurs des mémoires tampons d’entrée et d’écran de la nouvelle console. Ces handles permettent au processus d’accéder à la console.

Lorsqu’un processus utilise [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425), il peut spécifier une structure [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) , dont les membres contrôlent les caractéristiques de la première nouvelle console (le cas échéant) créée pour le processus enfant. La structure **STARTUPINFO** spécifiée dans l’appel à **CreateProcess** affecte une console créée si l’indicateur **Create \_ New \_ console** est spécifié. Cela affecte également une console créée si le processus enfant utilise ensuite [**AllocConsole**](allocconsole.md). Les caractéristiques de console suivantes peuvent être spécifiées :

- Taille de la nouvelle fenêtre de console, dans les cellules de caractères
- Emplacement de la nouvelle fenêtre de console, en coordonnées en pixels d’écran
- Taille de la mémoire tampon d’écran de la nouvelle console, dans les cellules de caractères
- Attributs de couleur de texte et d’arrière-plan de la mémoire tampon d’écran de la nouvelle console
- Nom complet de la barre de titre de la fenêtre de la nouvelle console

Le système utilise les valeurs par défaut si les valeurs [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) ne sont pas spécifiées. Un processus enfant peut utiliser la fonction [**GetStartupInfo**](https://msdn.microsoft.com/library/windows/desktop/ms683230) pour déterminer les valeurs dans sa structure **STARTUPINFO** .

Un processus ne peut pas modifier l’emplacement de sa fenêtre de console à l’écran, mais les fonctions de console suivantes sont disponibles pour définir ou récupérer les autres propriétés spécifiées dans la structure [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) .

| Fonction | Description |
|-|-|
| [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) | Récupère la taille de la fenêtre, la taille de la mémoire tampon d’écran et les attributs de couleur. |
| [**SetConsoleWindowInfo**](setconsolewindowinfo.md)  | Modifie la taille de la fenêtre de console.  |
| [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) | Modifie la taille de la mémoire tampon d’écran de la console. |
| [**SetConsoleTextAttribute**](setconsoletextattribute.md) | Définit les attributs de couleur.  |
| [**SetConsoleTitle**](setconsoletitle.md)  | Définit le titre de la fenêtre de console. |
| [**GetConsoleTitle**](getconsoletitle.md)  | Récupère le titre de la fenêtre de console.  |

Un processus peut utiliser la fonction [**FreeConsole**](freeconsole.md) pour se détacher d’une console héritée ou d’une console créée par [**AllocConsole**](allocconsole.md).

Un processus peut utiliser la fonction [**AttachConsole**](attachconsole.md) pour s’attacher à une autre session de console existante après l’utilisation de [**FreeConsole**](freeconsole.md) pour se détacher de sa propre session (ou s’il n’y a aucune session jointe).
