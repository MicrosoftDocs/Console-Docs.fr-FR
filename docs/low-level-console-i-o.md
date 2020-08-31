---
title: E/s de console de bas niveau
description: Les fonctions d’e/s de la console de bas niveau étendent le contrôle d’une application sur les e/s de la console en permettant un accès direct aux mémoires tampons d’entrée et d’écran d’une console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_low\_level\_console\_i\_o'
- base.low\_level\_console\_i\_o
- consoles.low\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c874aff4-6129-4dbc-8949-24d46382d81c
ms.openlocfilehash: b548a188189b597a270faac1cfbc83a2af699fab
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059472"
---
# <a name="low-level-console-io"></a>E/s de console de bas niveau


Les fonctions d’e/s de la console de bas niveau étendent le contrôle d’une application sur les e/s de la console en permettant un accès direct aux mémoires tampons d’entrée et d’écran d’une console. Ces fonctions permettent à une application d’effectuer les tâches suivantes :

- Recevoir une entrée à propos des événements de redimensionnement de la souris et de la mémoire tampon
- Recevoir des informations étendues sur les événements d’entrée au clavier
- Écrire des enregistrements d’entrée dans la mémoire tampon d’entrée
- Lire les enregistrements d’entrée sans les supprimer de la mémoire tampon d’entrée
- Déterminer le nombre d’événements en attente dans la mémoire tampon d’entrée
- Vider la mémoire tampon d’entrée
- Lire et écrire des chaînes de caractères Unicode ou ANSI à un emplacement spécifié dans une mémoire tampon d’écran
- Lire et écrire des chaînes de texte et des attributs de couleur d’arrière-plan à l’emplacement spécifié dans la mémoire tampon d’écran
- Lire et écrire des blocs rectangulaires de données de caractère et de couleur à un emplacement de mémoire tampon d’écran spécifié
- Écrire un caractère Unicode ou ANSI unique, ou une combinaison d’attributs de couleur de texte et d’arrière-plan, à un nombre spécifié de cellules consécutives en commençant à l’emplacement de mémoire tampon d’écran spécifié

Pour plus d'informations, voir les rubriques suivantes :

- [Modes de la console](console-modes.md)
- [Modes de la console de bas niveau](low-level-console-modes.md)
- [Fonctions d’entrée de la console de bas niveau](low-level-console-input-functions.md)
- [Fonctions de sortie de la console de bas niveau](low-level-console-output-functions.md)

 

 




