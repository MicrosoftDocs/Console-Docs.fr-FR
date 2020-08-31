---
title: Fonctions de sortie de la console de bas niveau
description: Les fonctions de sortie de la console de bas niveau fournissent un accès direct aux cellules de caractères d’une mémoire tampon d’écran.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_low\_level\_console\_output\_functions'
- base.low\_level\_console\_output\_functions
- consoles.low\_level\_console\_output\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 94185428-e8c7-4926-93ec-867b8c97b4ca
ms.openlocfilehash: 16441e318e7c0eed2de1125a2f7613cb4a105d44
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059080"
---
# <a name="low-level-console-output-functions"></a>Fonctions de sortie de la console de bas niveau


Les fonctions de sortie de la console de bas niveau fournissent un accès direct aux cellules de caractères d’une mémoire tampon d’écran. Un ensemble de fonctions lit ou écrit dans des cellules consécutives en commençant à n’importe quel emplacement dans la mémoire tampon d’écran de la console. Un autre jeu de fonctions lit ou écrit dans des blocs rectangulaires de cellules.

Les fonctions suivantes lisent ou écrivent dans un nombre spécifié de cellules de caractères consécutives dans une mémoire tampon d’écran, en commençant par une cellule spécifiée.


| Fonction                                                           | Description                                                                                                             |
|--------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| [**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)   | Copie une chaîne de caractères Unicode ou ANSI à partir d’une mémoire tampon d’écran.                                                     |
| [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md) | Écrit une chaîne de caractères Unicode ou ANSI dans une mémoire tampon d’écran.                                                       |
| [**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)   | Copie une chaîne de texte et des attributs de couleur d’arrière-plan à partir d’une mémoire tampon d’écran.                                           |
| [**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md) | Écrit une chaîne de texte et des attributs de couleur d’arrière-plan dans une mémoire tampon d’écran.                                             |
| [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)   | Écrit un caractère Unicode ou ANSI unique dans un nombre spécifié de cellules consécutives dans une mémoire tampon d’écran.                |
| [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)   | Écrit une combinaison d’attributs de couleur d’arrière-plan et de texte dans un nombre spécifié de cellules consécutives dans une mémoire tampon d’écran. |


Pour toutes ces fonctions, lorsque la dernière cellule d’une ligne est rencontrée, la lecture ou l’écriture s’ajuste à la première cellule de la ligne suivante. Lorsque la fin de la dernière ligne de la mémoire tampon de l’écran de la console est atteinte, les fonctions d’écriture ignorent tous les caractères ou attributs non écrits, et les fonctions de lecture indiquent le nombre de caractères ou d’attributs réellement écrits.

Les fonctions suivantes lisent ou écrivent dans des blocs rectangulaires de cellules de caractères à un emplacement spécifié dans une mémoire tampon d’écran.


| Fonction                                         | Description                                                                                                               |
|--------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| [**ReadConsoleOutput**](readconsoleoutput.md)   | Copie les données de caractère et de couleur à partir d’un bloc spécifié de cellules de mémoire tampon d’écran dans un bloc donné d’une mémoire tampon de destination. |
| [**WriteConsoleOutput**](writeconsoleoutput.md) | Écrit des données de caractère et de couleur dans un bloc spécifié de cellules de mémoire tampon d’écran à partir d’un bloc donné dans une mémoire tampon source.        |



Ces fonctions traitent les mémoires tampons d’écran et les mémoires tampons sources ou de destination en tant que tableaux à deux dimensions de structures d' [** \_ informations de type char**](char-info-str.md) (contenant les données d’attribut character et Color pour chaque cellule). Les fonctions spécifient la largeur et la hauteur, dans les cellules de caractères, de la mémoire tampon source ou de destination, et le pointeur vers la mémoire tampon est traité comme un pointeur vers la cellule d’origine (0,0) du tableau à deux dimensions. Les fonctions utilisent une [**petite structure \_ Rect**](small-rect-str.md) pour spécifier le rectangle auquel accéder dans la mémoire tampon de l’écran de la console, et les coordonnées de la cellule supérieure gauche dans la mémoire tampon source ou de destination déterminent l’emplacement du rectangle correspondant dans cette mémoire tampon.

Ces fonctions découpent automatiquement le rectangle de mémoire tampon d’écran spécifié pour l’ajuster aux limites de la mémoire tampon d’écran de la console. Par exemple, si le rectangle spécifie des coordonnées inférieures droites (colonne 100, ligne 50) et que la mémoire tampon de l’écran de la console n’a que 80 colonnes de largeur, les coordonnées sont découpées afin d’être (colonne 79, ligne 50). De même, ce rectangle ajusté est de nouveau coupé pour tenir dans les limites de la mémoire tampon source ou de destination. Les coordonnées de la mémoire tampon d’écran du rectangle réel qui a été lu ou écrit dans sont spécifiées. Pour obtenir un exemple qui utilise ces fonctions, consultez [lecture et écriture de blocs de caractères et d’attributs](reading-and-writing-blocks-of-characters-and-attributes.md).

L’illustration montre une opération [**ReadConsoleOutput**](readconsoleoutput.md) où le découpage se produit lorsque le bloc est lu à partir de la mémoire tampon d’écran de la console, et à nouveau lorsque le bloc est copié dans la mémoire tampon de destination. La fonction signale le rectangle de mémoire tampon d’écran réel à partir duquel elle a été copiée.

![fenêtre de mémoire tampon d’écran avec mémoire tampon de destination](images/cscon-03.png)








