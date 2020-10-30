---
title: Modes de la console
description: Un ensemble de modes d’entrée qui affecte les opérations d’entrée est associé à chaque mémoire tampon d’entrée de console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_console\_modes'
- base.console\_modes
- consoles.console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f0dcc123-3b12-44c4-8f94-920203f5198e
ms.openlocfilehash: 0bd048101546d20735745656677702f9f07115fd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039197"
---
# <a name="console-modes"></a>Modes de la console

Un ensemble de modes d’entrée qui affecte les opérations d’entrée est associé à chaque mémoire tampon d’entrée de console. De même, chaque mémoire tampon d’écran de console possède un ensemble de modes de sortie qui affecte les opérations de sortie. Les modes d’entrée peuvent être divisés en deux groupes : ceux qui affectent les fonctions d’entrée de haut niveau et ceux qui affectent les fonctions d’entrée de bas niveau. Les modes de sortie affectent uniquement les applications qui utilisent les fonctions de sortie de haut niveau.

La fonction [**GetConsoleMode**](getconsolemode.md) signale le mode d’entrée actuel de la mémoire tampon d’entrée d’une console ou le mode de sortie actuel d’une mémoire tampon d’écran. La fonction [**SetConsoleMode**](setconsolemode.md) définit le mode actuel d’une mémoire tampon d’entrée de la console ou d’une mémoire tampon d’écran. Si une console possède plusieurs mémoires tampons d’écran, les modes de sortie de chacun peuvent être différents. Une application peut modifier les modes d’e/s à tout moment. Pour plus d’informations sur les modes de console qui affectent les opérations d’e/s de haut niveau et de bas niveau, consultez [modes de console de haut niveau](high-level-console-modes.md) et [modes de console de bas](low-level-console-modes.md)niveau.

Une application en ligne de commande doit s’attendre à ce que d’autres applications de ligne de commande puissent modifier le mode de console à tout moment et ne pas restaurer son formulaire d’origine avant que le contrôle soit retourné. En outre, nous recommandons que toutes les applications de ligne de commande capturent le mode de console initial au démarrage et essaient de la restaurer au moment de la fermeture pour garantir un impact minimal sur les autres applications de ligne de commande attachées à la même console.

La fonction [**GetConsoleDisplayMode**](getconsoledisplaymode.md) indique si la console active est en mode plein écran.
