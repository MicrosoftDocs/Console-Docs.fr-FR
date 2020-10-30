---
title: Applications en mode caractère
description: Les consoles gèrent les entrées et sorties (e/s) des applications en mode caractère (les applications qui ne fournissent pas leur propre interface utilisateur graphique).
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_character\_mode\_applications'
- base.character\_mode\_applications
- consoles.character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ea3ea214-892c-4953-bc22-7905efbc173f
ms.openlocfilehash: 5e1b0b2b5162360122580f3ea7a100750b96272e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037347"
---
# <a name="character-mode-applications"></a>Applications en mode caractère

Les consoles gèrent les entrées et sorties (e/s) des applications en mode caractère (les applications qui ne fournissent pas leur propre interface utilisateur graphique).

Les fonctions de console permettent différents niveaux d’accès à une console. Les fonctions d’e/s de console de haut niveau permettent à une application de lire à partir d’une entrée standard pour récupérer l’entrée au clavier stockée dans la mémoire tampon d’entrée d’une console. Les fonctions permettent également à une application d’écrire dans une sortie standard ou une erreur standard d’afficher du texte dans la mémoire tampon d’écran de la console. Les fonctions de haut niveau prennent également en charge la redirection des handles standard et le contrôle des modes de console pour différentes fonctionnalités d’e/s. Les fonctions d’e/s de la console de bas niveau permettent aux applications de recevoir des informations détaillées sur les événements de clavier et de souris, ainsi que des événements impliquant des interactions de l’utilisateur avec la fenêtre de la console. Les fonctions de bas niveau permettent également un meilleur contrôle de la sortie à l’écran.

Cette vue d’ensemble décrit la prise en charge des applications en mode caractère.

- [À propos des consoles](about-character-mode-applications.md)
- [Utilisation de la console](using-the-console.md)
- [Informations de référence sur la console](console-reference.md)
