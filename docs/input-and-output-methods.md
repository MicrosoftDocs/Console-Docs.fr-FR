---
title: Méthodes d’entrée et de sortie
description: Il existe deux approches différentes pour les e/s de la console, dont le choix dépend de la flexibilité et du contrôle dont une application a besoin.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_input\_and\_output\_methods'
- base.input\_and\_output\_methods
- consoles.input\_and\_output\_methods
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 55a86d5d-d0b1-4d0c-b42f-7342809289ad
ms.openlocfilehash: 8ad03cc2be8cce2c174ac4a72f700cbb31b7fd94
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039557"
---
# <a name="input-and-output-methods"></a>Méthodes d’entrée et de sortie

Il existe deux approches différentes pour les e/s de la console, dont le choix dépend de la flexibilité et du contrôle dont une application a besoin. L’approche de haut niveau permet d’effectuer des e/s de flux de caractères simples, mais elle limite l’accès aux mémoires tampons d’entrée et d’écran d’une console. L’approche de bas niveau oblige les développeurs à écrire davantage de code et à choisir parmi une plus grande gamme de fonctions, mais il offre également une plus grande flexibilité à une application.

> [!NOTE]
> L’approche de bas niveau n’est pas recommandée pour un développement nouveau et en cours. Les applications nécessitant des fonctionnalités à partir des fonctions d’e/s de la console de bas niveau sont encouragées à utiliser des **[séquences de terminaux virtuels](console-virtual-terminal-sequences.md)** et à explorer notre documentation sur les **[fonctions classiques plutôt](classic-vs-vt.md)** que sur le terminal virtuel et **[le plan d’écosystème](ecosystem-roadmap.md)** .

Une application peut utiliser les fonctions d’e/s de fichier, [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747), ainsi que les fonctions de console, [**ReadConsole**](readconsole.md) et [**WriteConsole**](writeconsole.md), pour les e/s de haut niveau qui fournissent un accès indirect aux mémoires tampons d’entrée et d’écran d’une console. Les fonctions d’entrée de haut niveau filtrent et traitent les données dans la mémoire tampon d’entrée d’une console pour retourner les entrées sous la forme d’un flux de caractères, en ignorant la souris et l’entrée de redimensionnement de mémoire tampon. De même, les fonctions de sortie de haut niveau écrivent un flux de caractères qui s’affichent à l’emplacement du curseur actuel dans une mémoire tampon d’écran. Une application contrôle la façon dont ces fonctions fonctionnent en définissant les modes d’e/s d’une console.

Les fonctions d’e/s de bas niveau fournissent un accès direct aux mémoires tampons d’entrée et d’écran d’une console, ce qui permet à une application d’accéder aux événements d’entrée et aux informations étendues pour le redimensionnement de la souris et de la mémoire tampon. Les fonctions de sortie de bas niveau permettent à une application de lire ou d’écrire dans un nombre spécifié de cellules de caractères consécutives dans une mémoire tampon d’écran, ou de lire ou d’écrire dans des blocs rectangulaires de cellules de caractères à un emplacement spécifié dans une mémoire tampon d’écran. Les modes d’entrée d’une console affectent l’entrée de bas niveau en permettant à l’application de déterminer si les événements de redimensionnement de la souris et de la mémoire tampon sont placés dans la mémoire tampon d’entrée. Les modes de sortie d’une console n’ont aucun effet sur la sortie de bas niveau.

Les méthodes d’e/s de niveau supérieur et bas ne sont pas mutuellement exclusives et une application peut utiliser n’importe quelle combinaison de ces fonctions. En règle générale, toutefois, une application utilise une approche ou l’autre exclusivement, et nous vous recommandons de vous concentrer sur un paradigme particulier pour obtenir des résultats optimaux.

> [!TIP]
> L’application idéale à l’avenir se concentrera sur les méthodes de haut niveau et augmentera les besoins supplémentaires avec les **[séquences de terminaux virtuels](console-virtual-terminal-sequences.md)** via les méthodes d’e/s de haut niveau, si nécessaire, en évitant totalement l’utilisation des fonctions d’e/s de bas niveau.

Les rubriques suivantes décrivent les modes de la console, ainsi que les fonctions d’e/s de haut niveau et de bas niveau.

- [Modes de la console](console-modes.md)
- [E/s de console de haut niveau](high-level-console-i-o.md)
- [Modes de console de haut niveau](high-level-console-modes.md)
- [Fonctions d’entrée et de sortie de la console de haut niveau](high-level-console-input-and-output-functions.md)
- [Séquences de terminal virtuel de console](console-virtual-terminal-sequences.md)
- [Fonctions classiques par rapport aux séquences de terminaux virtuels](classic-vs-vt.md)
- [Plan d’écosystème](ecosystem-roadmap.md)
- [E/s de console de bas niveau](low-level-console-i-o.md)
- [Modes de la console de bas niveau](low-level-console-modes.md)
- [Fonctions d’entrée de la console de bas niveau](low-level-console-input-functions.md)
- [Fonctions de sortie de la console de bas niveau](low-level-console-output-functions.md)
