---
title: Mémoires tampons d’écran d’une console
description: Une mémoire tampon d’écran est un tableau à deux dimensions qui comprend des données sur les caractères et les couleurs utilisés pour la sortie de la fenêtre de console.
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
ms.localizationpriority: high
ms.openlocfilehash: 4c5740be3b60d54f9e7b586b41e962a4102222a0
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420198"
---
# <a name="console-screen-buffers"></a>Mémoires tampons d’écran d’une console

Une *mémoire tampon d’écran* est un tableau à deux dimensions qui comprend des données sur les caractères et les couleurs utilisés pour la sortie de la fenêtre de console. Une console peut avoir plusieurs mémoires tampons d’écran. La *mémoire tampon active* est celle qui est affichée à l’écran.

Le système crée une mémoire tampon d’écran chaque fois qu’il crée une nouvelle console. Pour ouvrir le handle vers la mémoire tampon d’écran active de la console, spécifiez la valeur **CONOUT$** dans un appel à la fonction [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858). Un processus peut utiliser la fonction [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) afin de créer des mémoires tampons d’écran supplémentaires pour sa console. Une nouvelle mémoire tampon d’écran n’est pas active tant que son handle n’est pas spécifié dans un appel à la fonction [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md). Toutefois, les mémoires tampons d’écran sont accessibles en lecture et en écriture, qu’elles soient actives ou inactives.

Chaque mémoire tampon d’écran a son propre tableau à deux dimensions contenant des informations sur les caractères. Les données concernant chaque caractère sont stockées dans une structure [**CHAR\_INFO**](char-info-str.md) qui spécifie le caractère Unicode ou ANSI, ainsi que les couleurs de premier plan et d’arrière-plan dans lesquelles ce caractère est affiché.

Pour chaque mémoire tampon d’écran, vous pouvez définir indépendamment un certain nombre de propriétés. Cela signifie que le changement de la mémoire tampon d’écran active peut avoir un impact important sur l’apparence de la fenêtre de la console. Les propriétés associées à une mémoire tampon d’écran sont les suivantes :

- Taille de la mémoire tampon d’écran, en nombre de lignes et de colonnes de caractères.
- Attributs du texte (couleurs de premier plan et d’arrière-plan pour l’affichage du texte qui doit être écrit par la fonction [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ou [**WriteConsole**](writeconsole.md)).
- Taille et emplacement de la fenêtre (zone rectangulaire de la mémoire tampon d’écran qui s’affiche dans la fenêtre de la console).
- Position, apparence et visibilité du curseur.
- Modes de sortie (**ENABLE\_PROCESSED\_OUTPUT** et **ENABLE\_WRAP\_AT\_EOL\_OUTPUT**). Pour plus d’informations sur les modes de sortie de la console, consultez [Modes de haut niveau de la console](high-level-console-modes.md).

Lorsque vous créez une mémoire tampon d’écran, celle-ci contient des espaces à chaque position. Son curseur est visible et positionné à l’origine de la mémoire tampon (0,0). La fenêtre est positionnée de sorte que son coin supérieur gauche est situé à l’origine de la mémoire tampon. La taille de la mémoire tampon d’écran de la console, la taille de la fenêtre, les attributs du texte et l’apparence du curseur sont déterminés par l’utilisateur ou par les valeurs par défaut du système. Pour récupérer les valeurs actuelles des différentes propriétés associées à la mémoire tampon d’écran de la console, utilisez les fonctions [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md), [**GetConsoleCursorInfo**](getconsolecursorinfo.md) et [**GetConsoleMode**](getconsolemode.md).

Les applications qui changent les propriétés de la mémoire tampon d’écran de la console doivent créer leur propre mémoire tampon d’écran, ou enregistrer l’état de la mémoire tampon d’écran héritée lors du démarrage et la restaurer au moment de la fermeture. Ce comportement coopératif est nécessaire pour faire en sorte que les autres applications qui partagent la même session de console ne soient pas impactées par les modifications.

> [!TIP]
> Au lieu de créer une deuxième mémoire tampon d’écran à cet effet, nous vous recommandons d’utiliser le [**mode de mémoire tampon alternatif**](console-virtual-terminal-sequences.md#alternate-screen-buffer), si cela vous est possible. Le **mode de mémoire tampon alternatif** offre une meilleure compatibilité sur les appareils distants et sur les autres plateformes. Pour plus d’informations, consultez [**Comparaison entre les API de console classiques et les séquences de terminal virtuel**](classic-vs-vt.md).

## <a name="cursor-appearance-and-position"></a>Apparence et position du curseur

Le curseur d’une mémoire tampon d’écran peut être visible ou masqué. Lorsqu’il est visible, son apparence peut varier, allant du remplissage intégral d’une cellule de caractère à l’affichage d’une ligne horizontale au bas de la cellule. Pour récupérer des informations sur l’apparence et la visibilité du curseur, utilisez la fonction [**GetConsoleCursorInfo**](getconsolecursorinfo.md). Cette fonction indique si le curseur est visible et décrit l’apparence de celui-ci en indiquant l’espace qu’il remplit dans une cellule de caractère (en pourcentage). Pour définir l’apparence et la visibilité du curseur, utilisez la fonction [**SetConsoleCursorInfo**](setconsolecursorinfo.md).

Les caractères écrits par les [fonctions d’E/S de console de haut niveau](high-level-console-i-o.md) le sont à l’emplacement actuel du curseur, et font avancer le curseur à l’emplacement suivant. Pour déterminer la position actuelle du curseur dans le système de coordonnées d’une mémoire tampon d’écran, utilisez [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md). Vous pouvez utiliser [**SetConsoleCursorPosition**](setconsolecursorposition.md) pour définir la position du curseur et, donc, contrôler le positionnement du texte qui est écrit ou répercuté par les fonctions d’E/S de haut niveau. Si vous déplacez le curseur, le texte situé au nouvel emplacement du curseur sera remplacé.

> [!NOTE]
> Il est déconseillé d’utiliser les fonctions de bas niveau pour trouver la position du curseur. Nous vous recommandons plutôt d’utiliser les [séquences de terminal virtuel](console-virtual-terminal-sequences.md) pour interroger cette position, si des dispositions avancées le demandent. Pour savoir pourquoi la préférence est donnée aux séquences de terminal virtuel, consultez le document **[Comparaison entre les API de console classiques et les séquences de terminal virtuel](classic-vs-vt.md)** .

La position, l’apparence et la visibilité du curseur sont définies de manière indépendante pour chaque mémoire tampon d’écran.

## <a name="character-attributes"></a>Attributs de caractères

Les attributs de caractères se divisent en deux classes : Color et DBCS. Les attributs suivants sont définis dans le fichier d’en-tête `WinCon.h`.

| Attribut | Signification |
|-|-|
| **FOREGROUND\_BLUE** | La couleur du texte contient du bleu. |
| **FOREGROUND\_GREEN** | La couleur du texte contient du vert. |
| **FOREGROUND\_RED** | La couleur du texte contient du rouge. |
| **FOREGROUND\_INTENSITY** | La couleur du texte est intensifiée. |
| **BACKGROUND\_BLUE** | La couleur d’arrière-plan contient du bleu. |
| **BACKGROUND\_GREEN** | La couleur d’arrière-plan contient du vert. |
| **BACKGROUND\_RED** | La couleur d’arrière-plan contient du rouge. |
| **BACKGROUND\_INTENSITY** | La couleur d’arrière-plan est intensifiée. |
| **COMMON\_LVB\_LEADING\_BYTE** | Octet de début. |
| **COMMON\_LVB\_TRAILING\_BYTE** | Octet de fin. |
| **COMMON\_LVB\_GRID\_HORIZONTAL** | Supérieur horizontal. |
| **COMMON\_LVB\_GRID\_LVERTICAL** | Gauche vertical. |
| **COMMON\_LVB\_GRID\_RVERTICAL** | Droite vertical. |
| **COMMON\_LVB\_REVERSE\_VIDEO** | Inverse les attributs du premier plan et de l’arrière-plan. |
| **COMMON\_LVB\_UNDERSCORE** | Caractère de soulignement. |

Les attributs du premier plan spécifient la couleur du texte. Les attributs de l’arrière-plan spécifient la couleur qui est utilisée pour remplir l’arrière-plan de la cellule. Les autres attributs sont utilisés avec [DBCS](https://msdn.microsoft.com/library/windows/desktop/dd317794).

Une application peut combiner les constantes du premier plan et de l’arrière-plan pour obtenir des couleurs différentes. Par exemple, la combinaison suivante produit un texte cyan clair sur un arrière-plan bleu.

`FOREGROUND_BLUE | FOREGROUND_GREEN | FOREGROUND_INTENSITY | BACKGROUND_BLUE`

Si aucune constante d’arrière-plan n’est spécifiée, l’arrière-plan est noir, et si aucune constante de premier plan n’est spécifiée, le texte est noir. Par exemple, la combinaison suivante produit du texte noir sur un arrière-plan blanc.

`BACKGROUND_BLUE | BACKGROUND_GREEN | BACKGROUND_RED`

Chaque cellule de caractère de la mémoire tampon d’écran stocke les attributs des couleurs qui sont utilisées pour dessiner le premier plan (texte) et l’arrière-plan de cette cellule. Une application peut définir les données de couleur pour chaque cellule de caractère individuellement, en stockant les données dans le membre **Attributes** de la structure [**CHAR\_INFO**](char-info-str.md) pour chaque cellule. Les attributs de texte actuels de chaque mémoire tampon d’écran seront utilisés pour les caractères qui seront écrits ou répercutés par la suite par les fonctions de haut niveau.

Une application peut utiliser [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) pour déterminer les attributs de texte actuels d’une mémoire tampon d’écran, et la fonction [**SetConsoleTextAttribute**](setconsoletextattribute.md) pour définir les attributs de caractères. La modification des attributs d’une mémoire tampon d’écran n’affecte pas l’affichage des caractères précédemment écrits. Ces attributs de texte n’affectent pas les caractères écrits par les fonctions d’E/S de console de bas niveau (comme la fonction [**WriteConsoleOutput**](writeconsoleoutput.md) ou [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)), qui spécifient explicitement les attributs de chaque cellule écrite ou qui laissent les attributs inchangés.

> [!NOTE]
> Il est déconseillé d’utiliser des fonctions de bas niveau pour manipuler des attributs de texte par défaut ou spécifiés. Nous vous recommandons plutôt d’utiliser les [séquences de terminal virtuel](console-virtual-terminal-sequences.md) pour définir des attributs de texte. Pour savoir pourquoi la préférence est donnée aux séquences de terminal virtuel, consultez le document **[Comparaison entre les API de console classiques et les séquences de terminal virtuel](classic-vs-vt.md)** .

## <a name="font-attributes"></a>Attributs de police

La fonction [**GetCurrentConsoleFont**](getcurrentconsolefont.md) récupère des informations sur la police actuelle de la console. Les informations stockées dans la structure [**CONSOLE\_FONT\_INFO**](console-font-info-str.md) comprend la largeur et la hauteur de chaque caractère dans la police en question.

La fonction [**GetConsoleFontSize**](getconsolefontsize.md) récupère la taille de la police utilisée par la mémoire tampon d’écran de console spécifiée.

> [!NOTE]
> Il est déconseillé d’utiliser des fonctions pour rechercher et manipuler des informations de police. Nous vous recommandons plutôt d’utiliser des applications en ligne de commande sans police pour garantir la compatibilité entre les plateformes, ainsi que la compatibilité avec les environnements hôtes qui permettent à l’utilisateur de personnaliser la police. Pour plus d’informations sur les préférences utilisateur et les environnements hôtes, y compris les terminaux, consultez la **[Feuille de route de l’écosystème](ecosystem-roadmap.md)** .
