---
title: Mémoires tampons d’écran d’une console
description: Une mémoire tampon d’écran est un tableau à deux dimensions de données de caractères et de couleur pour la sortie dans une fenêtre de console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_console\_screen\_buffers'
- base.console\_screen\_buffers
- consoles.console\_screen\_buffers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f94995fc-5f5f-4fcd-969d-7e10020634c2
ms.openlocfilehash: c3121a53f654bd2fa85fa140c2efc6d6217b7796
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039167"
---
# <a name="console-screen-buffers"></a>Mémoires tampons d’écran d’une console

Une *mémoire tampon d’écran* est un tableau à deux dimensions de données de caractères et de couleur pour la sortie dans une fenêtre de console. Une console peut avoir plusieurs mémoires tampons d’écran. La *mémoire tampon d’écran active* est celle qui est affichée à l’écran.

Le système crée une mémoire tampon d’écran à chaque fois qu’elle crée une nouvelle console. Pour ouvrir un handle vers la mémoire tampon d’écran active d’une console, spécifiez la valeur **CONOUT $** dans un appel à la fonction [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) . Un processus peut utiliser la fonction [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) pour créer des mémoires tampon d’écran supplémentaires pour sa console. Une nouvelle mémoire tampon d’écran n’est pas active tant que son handle n’est pas spécifié dans un appel à la fonction [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) . Toutefois, les mémoires tampons d’écran sont accessibles pour la lecture et l’écriture, qu’elles soient actives ou inactives.

Chaque mémoire tampon d’écran possède son propre tableau à deux dimensions d’enregistrements d’informations de caractères. Les données de chaque caractère sont stockées dans une structure d' [**\_ informations char**](char-info-str.md) qui spécifie le caractère Unicode ou ANSI, ainsi que les couleurs de premier plan et d’arrière-plan dans lesquelles ce caractère est affiché.

Un certain nombre de propriétés associées à une mémoire tampon d’écran peuvent être définies indépendamment pour chaque mémoire tampon d’écran. Cela signifie que la modification de la mémoire tampon d’écran active peut avoir un effet spectaculaire sur l’apparence de la fenêtre de console. Les propriétés associées à une mémoire tampon d’écran sont les suivantes :

- Taille de la mémoire tampon d’écran, dans les lignes et les colonnes de caractères.
- Attributs de texte (couleurs de premier plan et d’arrière-plan pour l’affichage de texte à écrire par la fonction [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ou [**WriteConsole**](writeconsole.md) ).
- Taille et emplacement de la fenêtre (zone rectangulaire de la mémoire tampon d’écran de la console affichée dans la fenêtre de console).
- Position, apparence et visibilité du curseur.
- Modes de sortie ( **activer la \_ \_ sortie traitée** et **activer le \_ Retour à la ligne \_ à la \_ \_ sortie de EOL** ). Pour plus d’informations sur les modes de sortie de la console, consultez [modes de console de haut niveau](high-level-console-modes.md).

Lorsqu’une mémoire tampon d’écran est créée, elle contient des espaces à chaque position. Son curseur est visible et positionné à l’origine de la mémoire tampon (0,0), et la fenêtre est positionnée avec son coin supérieur gauche à l’origine de la mémoire tampon. La taille de la mémoire tampon d’écran de la console, la taille de la fenêtre, les attributs de texte et l’apparence du curseur sont déterminés par l’utilisateur ou par les valeurs par défaut du système. Pour récupérer les valeurs actuelles des différentes propriétés associées à la mémoire tampon d’écran de la console, utilisez les fonctions [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md), [**GetConsoleCursorInfo**](getconsolecursorinfo.md)et [**GetConsoleMode**](getconsolemode.md) .

Les applications qui modifient les propriétés de mémoire tampon d’écran de la console doivent créer leur propre mémoire tampon d’écran ou enregistrer l’état de la mémoire tampon d’écran héritée lors du démarrage et la restaurer à la sortie. Ce comportement coopératif est nécessaire pour s’assurer que les autres applications qui partagent la même session de console ne sont pas affectées par les modifications.

> [!TIP]
> Il est recommandé d’utiliser le [**mode de mémoire tampon alternatif**](console-virtual-terminal-sequences.md#alternate-screen-buffer) , si possible, au lieu de créer une deuxième mémoire tampon d’écran à cet effet. Le **mode de mémoire tampon de remplacement** offre une meilleure compatibilité sur les appareils distants et sur d’autres plateformes. Pour plus d’informations, consultez notre discussion sur les [**API de console classiques et le terminal virtuel**](classic-vs-vt.md) .

## <a name="cursor-appearance-and-position"></a>Apparence et position du curseur

Le curseur d’une mémoire tampon d’écran peut être visible ou masqué. Lorsqu’il est visible, son apparence peut varier, du remplissage complet d’une cellule de caractère à l’affichage d’une ligne horizontale au bas de la cellule. Pour extraire des informations sur l’apparence et la visibilité du curseur, utilisez la fonction [**GetConsoleCursorInfo**](getconsolecursorinfo.md) . Cette fonction indique si le curseur est visible et décrit l’apparence du curseur en tant que pourcentage d’une cellule de caractère qu’il remplit. Pour définir l’apparence et la visibilité du curseur, utilisez la fonction [**SetConsoleCursorInfo**](setconsolecursorinfo.md) .

Les caractères écrits par les [fonctions d’e/s de console de haut niveau](high-level-console-i-o.md) sont écrits à l’emplacement actuel du curseur, en avançant le curseur à l’emplacement suivant. Pour déterminer la position actuelle du curseur dans le système de coordonnées d’une mémoire tampon d’écran, utilisez [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md). Vous pouvez utiliser [**SetConsoleCursorPosition**](setconsolecursorposition.md) pour définir la position du curseur et, par conséquent, contrôler l’emplacement du texte écrit ou renvoyé par les fonctions d’e/s de niveau supérieur. Si vous déplacez le curseur, le texte du nouvel emplacement du curseur est remplacé.

> [!NOTE]
> L’utilisation des fonctions de bas niveau pour trouver la position du curseur est déconseillée. Il est recommandé d’utiliser des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) pour interroger cette position si nécessaire pour les dispositions avancées. Vous trouverez plus d’informations sur la préférence sur les séquences de terminaux virtuels dans le document **[fonctions classiques et terminal virtuel](classic-vs-vt.md)** .

La position, l’apparence et la visibilité du curseur sont définies indépendamment pour chaque mémoire tampon d’écran.

## <a name="character-attributes"></a>Attributs de caractères

Les attributs de caractères peuvent être divisés en deux classes : Color et DBCS. Les attributs suivants sont définis dans le `WinCon.h` fichier d’en-tête.

| Attribut | Signification |
|-|-|
| **bleu de premier plan \_** | La couleur du texte contient le bleu. |
| **vert de premier plan \_** | La couleur du texte contient du vert. |
| **PREMIER plan \_ rouge** | La couleur du texte contient le rouge. |
| **intensité du premier plan \_** | La couleur du texte est intensifiée. |
| **ARRIÈRE-plan \_ bleu** | La couleur d’arrière-plan contient le bleu. |
| **ARRIÈRE-plan \_ vert** | La couleur d’arrière-plan contient du vert. |
| **ARRIÈRE-plan \_ rouge** | La couleur d’arrière-plan contient le rouge. |
| **intensité de l’arrière-plan \_** | La couleur d’arrière-plan est intensifiée. |
| **\_octet de \_ début \_ lvb courant** | Octet de début. |
| **\_octet de \_ fin lvb \_ commun** | Octet de fin. |
| **\_ \_ quadrillage horizontal lvb \_ commun** | Horizontal supérieur. |
| **\_LVERTICAL de \_ grille \_ lvb commun** | Vertical gauche. |
| **\_RVERTICAL de \_ grille \_ lvb commun** | Verticale droite. |
| **\_ \_ vidéo inversée lvb courante \_** | Attributs de premier plan et d’arrière-plan inversés. |
| **trait \_ de \_ soulignement lvb commun** | Soulignement. |

Les attributs de premier plan spécifient la couleur du texte. Les attributs d’arrière-plan spécifient la couleur utilisée pour remplir l’arrière-plan de la cellule. Les autres attributs sont utilisés avec [DBCS](https://msdn.microsoft.com/library/windows/desktop/dd317794).

Une application peut combiner les constantes de premier plan et d’arrière-plan pour obtenir des couleurs différentes. Par exemple, la combinaison suivante produit un texte cyan clair sur un arrière-plan bleu.

`FOREGROUND_BLUE | FOREGROUND_GREEN | FOREGROUND_INTENSITY | BACKGROUND_BLUE`

Si aucune constante d’arrière-plan n’est spécifiée, l’arrière-plan est noir et si aucune constante de premier plan n’est spécifiée, le texte est noir. Par exemple, la combinaison suivante produit du texte noir sur un arrière-plan blanc.

`BACKGROUND_BLUE | BACKGROUND_GREEN | BACKGROUND_RED`

Chaque cellule de caractère de mémoire tampon d’écran stocke les attributs de couleur pour les couleurs utilisées pour dessiner le premier plan (texte) et l’arrière-plan de cette cellule. Une application peut définir les données de couleur pour chaque cellule de caractère individuellement, en stockant les données dans le membre **attributes** de la structure d' [**\_ informations char**](char-info-str.md) pour chaque cellule. Les attributs de texte actuels de chaque mémoire tampon d’écran sont utilisés pour les caractères écrits ou renvoyés par la suite par les fonctions de haut niveau.

Une application peut utiliser [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) pour déterminer les attributs de texte actuels d’une mémoire tampon d’écran et la fonction [**SetConsoleTextAttribute**](setconsoletextattribute.md) pour définir les attributs de caractères. La modification des attributs d’une mémoire tampon d’écran n’affecte pas l’affichage des caractères précédemment écrits. Ces attributs de texte n’affectent pas les caractères écrits par les fonctions d’e/s de la console de bas niveau (telles que la fonction [**WriteConsoleOutput**](writeconsoleoutput.md) ou [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md) ), qui spécifient explicitement les attributs de chaque cellule écrite ou laissent les attributs inchangés.

> [!NOTE]
> L’utilisation des fonctions de bas niveau pour manipuler des attributs de texte par défaut et spécifiques est déconseillée. Il est recommandé d’utiliser des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) pour définir des attributs de texte. Vous trouverez plus d’informations sur la préférence sur les séquences de terminaux virtuels dans le document **[fonctions classiques et terminal virtuel](classic-vs-vt.md)** .

## <a name="font-attributes"></a>Attributs de police

La fonction [**GetCurrentConsoleFont**](getcurrentconsolefont.md) récupère des informations sur la police de la console actuelle. Les informations stockées dans la structure des [**\_ \_ informations**](console-font-info-str.md) sur la police de la console incluent la largeur et la hauteur de chaque caractère de la police.

La fonction [**GetConsoleFontSize**](getconsolefontsize.md) récupère la taille de la police utilisée par la mémoire tampon d’écran de la console spécifiée.

> [!NOTE]
> L’utilisation de fonctions pour rechercher et manipuler les informations de police est déconseillée. Il est recommandé d’utiliser des applications en ligne de commande de manière neutre pour garantir la compatibilité entre plateformes, ainsi que la compatibilité avec les environnements d’hôte qui permettent à l’utilisateur de personnaliser la police. Plus d’informations préférences utilisateur et environnements hôtes, y compris les terminaux, consultez la feuille de route pour l' **[écosystème](ecosystem-roadmap.md)** .
