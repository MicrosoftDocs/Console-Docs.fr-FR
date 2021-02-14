---
title: E/s de la console High-Level
description: Les fonctions d’e/s de haut niveau offrent un moyen simple de lire un flux de caractères à partir de l’entrée de la console ou d’écrire un flux de caractères dans la sortie de la console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_high\_level\_console\_i\_o'
- base.high\_level\_console\_i\_o
- consoles.high\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6d191fee-87bb-4659-8056-910149e591f7
ms.openlocfilehash: d240a261ea555e0bfa506c96c1aaea9d6a933697
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358692"
---
# <a name="high-level-console-io"></a>E/s de la console High-Level

Les fonctions d’e/s de haut niveau offrent un moyen simple de lire un flux de caractères à partir de l’entrée de la console ou d’écrire un flux de caractères dans la sortie de la console. Une opération de lecture de haut niveau obtient des caractères d’entrée à partir de la mémoire tampon d’entrée d’une console et les stocke dans une mémoire tampon spécifiée. Une opération d’écriture de haut niveau prend les caractères d’une mémoire tampon spécifiée et les écrit dans une mémoire tampon d’écran à l’emplacement actuel du curseur, en avançant le curseur à mesure que chaque caractère est écrit.

Les e/s de haut niveau vous permettent de choisir entre les fonctions [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) et [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) et les fonctions [**ReadConsole**](readconsole.md) et [**WriteConsole**](writeconsole.md) . Ils sont identiques, à l’exception de deux différences importantes. Les fonctions de console prennent en charge l’utilisation de caractères Unicode ou du jeu de caractères ANSI par le biais des variantes A et W de chaque fonction. les fonctions d’e/s de fichier ne prennent pas en charge Unicode, à l’exception de UTF-8 définis avec la `CP_UTF8` constante sur les fonctions **[SetConsoleCP](setconsolecp.md)** et **[SetConsoleOutputCP](setconsoleoutputcp.md)** antérieures à l’utilisation. En outre, les fonctions d’e/s de fichier peuvent être utilisées pour accéder aux fichiers, aux canaux et aux périphériques de communication série. les fonctions de console peuvent uniquement être utilisées avec des handles de console. Cette distinction est importante si une application s’appuie sur des handles standard qui ont peut-être été redirigés.

Lors de l’utilisation d’un ensemble de fonctions de haut niveau, une application peut contrôler les couleurs de texte et d’arrière-plan utilisées pour afficher les caractères écrits par la suite dans une mémoire tampon d’écran avec le mécanisme préféré par le biais de **[séquences de terminaux virtuels](console-virtual-terminal-sequences.md)**. Une application peut également utiliser les modes de console qui affectent les e/s de console de haut niveau pour activer ou désactiver les propriétés suivantes :

- Écho de l’entrée au clavier vers la mémoire tampon d’écran active
- Entrée de ligne, dans laquelle une opération de lecture n’est pas retournée tant que la touche entrée n’est pas enfoncée
- Traitement automatique de l’entrée au clavier pour gérer les retours chariot, CTRL + C et d’autres détails d’entrée
- Traitement automatique de la sortie pour gérer le retour à la ligne, les retours chariot, les retours à la ligne et d’autres détails de sortie

Pour plus d'informations, voir les rubriques suivantes :

- [Modes de la console](console-modes.md)
- [Modes de console de haut niveau](high-level-console-modes.md)
- [Fonctions d’entrée et de sortie de la console de haut niveau](high-level-console-input-and-output-functions.md)
- [API classiques et séquences de terminaux virtuels](classic-vs-vt.md)