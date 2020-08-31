---
title: Modes de la console
description: Un ensemble de modes d’entrée qui affecte les opérations d’entrée est associé à chaque mémoire tampon d’entrée de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_console\_modes'
- base.console\_modes
- consoles.console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f0dcc123-3b12-44c4-8f94-920203f5198e
ms.openlocfilehash: b00f53a282833b560a29c6bed4c7ef0b9e056ba5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059317"
---
# <a name="console-modes"></a>Modes de la console


Un ensemble de modes d’entrée qui affecte les opérations d’entrée est associé à chaque mémoire tampon d’entrée de console. De même, chaque mémoire tampon d’écran de console possède un ensemble de modes de sortie qui affecte les opérations de sortie. Les modes d’entrée peuvent être divisés en deux groupes : ceux qui affectent les fonctions d’entrée de haut niveau et ceux qui affectent les fonctions d’entrée de bas niveau. Les modes de sortie affectent uniquement les applications qui utilisent les fonctions de sortie de haut niveau.

La fonction [**GetConsoleMode**](getconsolemode.md) signale le mode d’entrée actuel de la mémoire tampon d’entrée d’une console ou le mode de sortie actuel d’une mémoire tampon d’écran. La fonction [**SetConsoleMode**](setconsolemode.md) définit le mode actuel d’une mémoire tampon d’entrée de la console ou d’une mémoire tampon d’écran. Si une console possède plusieurs mémoires tampons d’écran, les modes de sortie de chacun peuvent être différents. Une application peut modifier les modes d’e/s à tout moment. Pour plus d’informations sur les modes de console qui affectent les opérations d’e/s de haut niveau et de bas niveau, consultez [modes de console de haut niveau](high-level-console-modes.md) et [modes de console de bas](low-level-console-modes.md)niveau.

La fonction [**GetConsoleDisplayMode**](getconsoledisplaymode.md) indique si la console active est en mode plein écran et si elle communique directement avec le matériel.

 

 




