---
title: E/s de console de haut niveau
description: Les fonctions d’e/s de haut niveau offrent un moyen simple de lire un flux de caractères à partir de l’entrée de la console ou d’écrire un flux de caractères dans la sortie de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_high\_level\_console\_i\_o'
- base.high\_level\_console\_i\_o
- consoles.high\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6d191fee-87bb-4659-8056-910149e591f7
ms.openlocfilehash: 2209259f604bb8653bca6ab38ca763b63f65713f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059076"
---
# <a name="high-level-console-io"></a>E/s de console de haut niveau


Les fonctions d’e/s de haut niveau offrent un moyen simple de lire un flux de caractères à partir de l’entrée de la console ou d’écrire un flux de caractères dans la sortie de la console. Une opération de lecture de haut niveau obtient des caractères d’entrée à partir de la mémoire tampon d’entrée d’une console et les stocke dans une mémoire tampon spécifiée. Une opération d’écriture de haut niveau prend les caractères d’une mémoire tampon spécifiée et les écrit dans une mémoire tampon d’écran à l’emplacement actuel du curseur, en avançant le curseur à mesure que chaque caractère est écrit.

Les e/s de haut niveau vous permettent de choisir entre les fonctions [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) et les fonctions [**ReadConsole**](readconsole.md) et [**WriteConsole**](writeconsole.md) . Ils sont identiques, à l’exception de deux différences importantes. Les fonctions de console prennent en charge l’utilisation de caractères Unicode ou du jeu de caractères ANSI. les fonctions d’e/s de fichier ne prennent pas en charge Unicode. En outre, les fonctions d’e/s de fichier peuvent être utilisées pour accéder aux fichiers, aux canaux et aux périphériques de communication série. les fonctions de console peuvent uniquement être utilisées avec des handles de console. Cette distinction est importante si une application s’appuie sur des handles standard qui ont peut-être été redirigés.

Lors de l’utilisation d’un ensemble de fonctions de haut niveau, une application peut contrôler les couleurs de texte et d’arrière-plan utilisées pour afficher les caractères écrits par la suite dans une mémoire tampon d’écran. Une application peut également utiliser les modes de console qui affectent les e/s de console de haut niveau pour activer ou désactiver les propriétés suivantes :

- Écho de l’entrée au clavier vers la mémoire tampon d’écran active
- Entrée de ligne, dans laquelle une opération de lecture n’est pas retournée tant que la touche entrée n’est pas enfoncée
- Traitement automatique de l’entrée au clavier pour gérer les retours chariot, CTRL + C et d’autres détails d’entrée
- Traitement automatique de la sortie pour gérer le retour à la ligne, les retours chariot, les retours à la ligne et d’autres détails de sortie

Pour plus d'informations, voir les rubriques suivantes :

- [Modes de la console](console-modes.md)
- [Modes de console de haut niveau](high-level-console-modes.md)
- [Fonctions d’entrée et de sortie de la console de haut niveau](high-level-console-input-and-output-functions.md)

 

 




