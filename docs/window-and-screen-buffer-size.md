---
title: Taille de la mémoire tampon de la fenêtre et de l’écran
description: La taille d’une mémoire tampon d’écran est exprimée en termes de grille de coordonnées basée sur les cellules de caractères.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_window\_and\_screen\_buffer\_size'
- base.window\_and\_screen\_buffer\_size
- consoles.window\_and\_screen\_buffer\_size
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 55246039-31eb-41ca-ad8e-d314cb508644
ms.openlocfilehash: 91fed765b76ebfb8b9dde318d8f76eff9a72d862
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037107"
---
# <a name="window-and-screen-buffer-size"></a>Taille de la mémoire tampon de la fenêtre et de l’écran

La taille d’une mémoire tampon d’écran est exprimée en termes de grille de coordonnées basée sur les cellules de caractères. La largeur est le nombre de cellules de caractères dans chaque ligne et la hauteur est le nombre de lignes. Une fenêtre qui détermine la taille et l’emplacement de la partie rectangulaire de la mémoire tampon d’écran de la console affichée dans la fenêtre de console est associée à chaque mémoire tampon d’écran. La fenêtre d’une mémoire tampon d’écran est définie en spécifiant les coordonnées de cellule de caractères des cellules supérieure gauche et inférieure droite du rectangle de la fenêtre.

> [!NOTE]
> Dans le monde des **[séquences de terminaux virtuels](console-virtual-terminal-sequences.md)** , la taille de la fenêtre et la taille de la mémoire tampon d’écran sont fixes à la même valeur. Le terminal gère toute région scrollback qui serait l’équivalent d’une console dont la taille de mémoire tampon d’écran est supérieure à la taille de la fenêtre. Ce contenu appartient au terminal et n’est généralement plus une partie de la zone adressable. Pour plus d’informations, consultez notre comparaison entre les **[fonctions de console classiques et les séquences de terminaux virtuels](classic-vs-vt.md)** .

Une mémoire tampon d’écran peut avoir n’importe quelle taille, limitée uniquement par la mémoire disponible. Les dimensions de la fenêtre d’une mémoire tampon d’écran ne peuvent pas dépasser les dimensions correspondantes de la mémoire tampon d’écran de la console ou de la fenêtre maximale qui peut tenir sur l’écran en fonction de la taille de police actuelle (contrôlée exclusivement par l’utilisateur).

La fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) retourne les informations suivantes sur une mémoire tampon d’écran et sa fenêtre :

- Taille actuelle de la mémoire tampon d’écran de la console
- L’emplacement actuel de la fenêtre
- Taille maximale de la fenêtre en fonction de la taille de la mémoire tampon d’écran actuelle, de la taille actuelle de la police et de la taille de l’écran

La fonction [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) retourne la taille maximale de la fenêtre d’une console en fonction de la police et de la taille d’écran actuelles. Cette taille est différente de la taille de fenêtre maximale retournée par [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) , car la taille de la mémoire tampon d’écran de la console est ignorée.

Pour modifier la taille d’une mémoire tampon d’écran, utilisez la fonction [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) . Cette fonction échoue si l’une des dimensions de la taille spécifiée est inférieure à la dimension correspondante de la fenêtre de la console.

Pour modifier la taille ou l’emplacement de la fenêtre d’une mémoire tampon d’écran, utilisez la fonction [**SetConsoleWindowInfo**](setconsolewindowinfo.md) . Cette fonction échoue si les coordonnées d’angle de fenêtre spécifiées dépassent les limites de la mémoire tampon d’écran de la console ou de l’écran. La modification de la taille de la fenêtre de la mémoire tampon active de l’écran modifie la taille de la fenêtre de console affichée à l’écran.

Un processus peut modifier le mode d’entrée de la console pour activer l’entrée de fenêtre afin que le processus puisse recevoir une entrée lorsque l’utilisateur modifie la taille de la mémoire tampon d’écran de la console. Si une application active l’entrée de fenêtre, elle peut utiliser [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) pour récupérer la taille de la mémoire tampon de la fenêtre et de l’écran au démarrage. Ces informations peuvent ensuite être utilisées pour déterminer la façon dont les données sont affichées dans la fenêtre. Si l’utilisateur modifie la taille de la mémoire tampon de l’écran de la console, l’application peut répondre en modifiant la façon dont les données sont affichées. Par exemple, une application peut ajuster la façon dont le texte est renvoyé à la ligne à la fin de la ligne si le nombre de caractères par ligne change. Si une application n’active pas l’entrée de fenêtre, elle doit soit utiliser les tailles de mémoire tampon de fenêtre et d’écran héritées, soit définir la taille souhaitée au cours du démarrage et restaurer les tailles héritées à la sortie. Pour plus d’informations sur le mode d’entrée de fenêtre, consultez [modes de console de bas niveau](low-level-console-modes.md).
