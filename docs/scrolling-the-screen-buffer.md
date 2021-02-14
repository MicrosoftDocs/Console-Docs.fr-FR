---
title: Défilement de la mémoire tampon d’écran
description: Décrit comment la fenêtre de console affiche une partie de la mémoire tampon d’écran active.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_scrolling\_the\_screen\_buffer'
- base.scrolling\_the\_screen\_buffer
- consoles.scrolling\_the\_screen\_buffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c8404e78-9807-4bed-bc12-25377fa96151
ms.openlocfilehash: 4c55a40f43827deeacfd1302d507732ec9bcc248
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358659"
---
# <a name="scrolling-the-screen-buffer"></a>Défilement de la mémoire tampon d’écran

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

La fenêtre de console affiche une partie de la mémoire tampon d’écran active. Chaque mémoire tampon d’écran gère son propre rectangle de fenêtre active qui spécifie les coordonnées des cellules de caractères supérieure gauche et inférieure droite à afficher dans la fenêtre de console. Pour déterminer le rectangle de la fenêtre active d’une mémoire tampon d’écran, utilisez [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md). Lorsqu’une mémoire tampon d’écran est créée, l’angle supérieur gauche de la fenêtre se trouve dans l’angle supérieur gauche de la mémoire tampon de l’écran de la console, à (0,0).

Le rectangle de la fenêtre peut être modifié pour afficher différentes parties de la mémoire tampon d’écran de la console. Le rectangle de fenêtre d’une mémoire tampon d’écran peut changer dans les cas suivants :

- Quand [**SetConsoleWindowInfo**](setconsolewindowinfo.md) est appelé pour spécifier un nouveau rectangle de fenêtre, il fait défiler la vue de la mémoire tampon d’écran de la console en modifiant la position du rectangle de la fenêtre sans modifier la taille de la fenêtre. Pour obtenir des exemples de défilement du contenu de la fenêtre, consultez défilement de la [fenêtre d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-window.md).

  ![fenêtre de mémoire tampon d’écran panoramique autour de la grande mémoire tampon du contenu](images/cscon-01.png)

- Lorsque vous utilisez la fonction [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) pour écrire dans une mémoire tampon d’écran avec l’option encapsuler au mode de sortie de fin de ligne (EOL) activé, le rectangle de la fenêtre se déplace automatiquement, de sorte que le curseur est toujours affiché.
- Lorsque la fonction [**SetConsoleCursorPosition**](setconsolecursorposition.md) spécifie une nouvelle position de curseur qui se trouve en dehors des limites du rectangle de la fenêtre active, le rectangle de la fenêtre se déplace automatiquement pour afficher le curseur.
- Lorsque l’utilisateur modifie la taille de la fenêtre de console ou utilise les barres de défilement de la fenêtre, le rectangle de la fenêtre de la mémoire tampon d’écran active peut changer. Cette modification n’est pas signalée comme un événement de redimensionnement de fenêtre dans la mémoire tampon d’entrée.

Dans chacune de ces situations, le rectangle de la fenêtre se déplace pour afficher une autre partie de la mémoire tampon d’écran de la console, mais le contenu de la mémoire tampon d’écran de la console reste à la même position. Les situations suivantes peuvent entraîner le décalage du contenu de la mémoire tampon de l’écran de la console :

- Lorsque la fonction [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) est appelée, un bloc rectangulaire est copié d’une partie d’une mémoire tampon d’écran vers une autre.
- Lors de l’utilisation de [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) pour écrire dans une mémoire tampon d’écran avec encapsuler en mode de sortie EOL activé, le contenu de la mémoire tampon de l’écran de la console défile automatiquement à la fin de la mémoire tampon d’écran de la console. Ce défilement ignore la ligne supérieure de la mémoire tampon d’écran de la console.

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) spécifie le rectangle de la mémoire tampon d’écran de la console qui est déplacé et les nouvelles coordonnées en haut à gauche auxquelles le rectangle est copié. Cette fonction peut faire défiler une partie ou la totalité du contenu de la mémoire tampon de l’écran de la console.

L’illustration montre une opération [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) qui fait défiler le contenu entier de la mémoire tampon de l’écran de la console vers le haut de plusieurs lignes. Le contenu des lignes du haut est supprimé et les lignes du bas sont remplies avec un caractère et une couleur spécifiés.

![fenêtre de mémoire tampon d’écran le contenu défilant du haut vers l’écart](images/cscon-02.png)

Les effets de [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) peuvent être limités en spécifiant un rectangle de découpage facultatif afin que le contenu de la mémoire tampon d’écran de la console en dehors du rectangle de découpage ne soit pas modifié. L’effet du découpage consiste à créer une sous-fenêtre (rectangle de découpage) dont le contenu défile sans affecter le reste de la mémoire tampon d’écran de la console. Pour obtenir un exemple qui utilise **ScrollConsoleScreenBuffer**, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).