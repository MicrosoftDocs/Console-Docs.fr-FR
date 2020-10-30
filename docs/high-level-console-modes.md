---
title: Modes de la console High-Level
description: Le comportement des fonctions de console de haut niveau est affecté par les modes d’entrée et de sortie de la console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_high\_level\_console\_modes'
- base.high\_level\_console\_modes
- consoles.high\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3ec915eb-333d-484d-a14d-46377b503ecc
ms.openlocfilehash: 418983a788957578e97fee70624fd80c1b09bc04
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038640"
---
# <a name="high-level-console-modes"></a>Modes de la console High-Level

Le comportement des fonctions de console de haut niveau est affecté par les modes d’entrée et de sortie de la console. Tous les modes d’entrée de la console suivants sont activés pour la mémoire tampon d’entrée d’une console lors de la création d’une console :

- Mode de saisie de ligne
- Mode de saisie traité
- Mode de saisie d’écho

Les deux modes de sortie de console suivants sont activés pour une mémoire tampon d’écran de console lors de sa création :

- Mode de sortie traité
- Retour en mode de sortie de EOL

Les trois modes d’entrée, ainsi que le mode de sortie traité, sont conçus pour fonctionner ensemble. Il est préférable d’activer ou de désactiver tous ces modes en tant que groupe. Lorsque toutes les sont activées, l’application est dite en mode « cuit », ce qui signifie que la majeure partie du traitement est gérée pour l’application. Lorsque tous les sont désactivés, l’application est en mode « brut », ce qui signifie que l’entrée n’est pas filtrée et que le traitement est laissé à l’application.

Une application peut utiliser la fonction [**GetConsoleMode**](getconsolemode.md) pour déterminer le mode actuel de la mémoire tampon d’entrée ou de mémoire tampon d’entrée d’une console. Vous pouvez activer ou désactiver l’un de ces modes en utilisant les valeurs suivantes dans la fonction [**SetConsoleMode**](setconsolemode.md) . Notez que la définition du mode de sortie d’une mémoire tampon d’écran n’affecte pas le mode de sortie des autres mémoires tampons d’écran.

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]
