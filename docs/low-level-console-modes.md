---
title: Modes de la console de bas niveau
description: Les types d’événements d’entrée signalés dans le tampon d’entrée d’une console dépendent des modes de saisie de la souris et de la fenêtre de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_low\_level\_console\_modes'
- base.low\_level\_console\_modes
- consoles.low\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 41bfdc51-27cb-4d5e-898c-507ffc8789b9
ms.openlocfilehash: 375b3b6eaef499324bdbde24ec973d91c50dda5b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059284"
---
# <a name="low-level-console-modes"></a>Modes de la console de bas niveau


Les types d’événements d’entrée signalés dans le tampon d’entrée d’une console dépendent des modes de saisie de la souris et de la fenêtre de la console. Le mode d’entrée traité de la console détermine la façon dont le système gère la combinaison de touches CTRL + C. Pour définir ou récupérer l’état des modes d’entrée d’une console, une application peut spécifier un handle de mémoire tampon d’entrée de la console dans un appel à la fonction [**SetConsoleMode**](setconsolemode.md) ou [**GetConsoleMode**](getconsolemode.md) . Les modes suivants sont utilisés avec les descripteurs d’entrée de la console.


| Mode                         | Description                                                                                                                                                                                                                                                                                                                                                                                           |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **ACTIVER l' \_ entrée de la souris \_**     | Contrôle si les événements de souris sont signalés dans la mémoire tampon d’entrée. Par défaut, l’entrée de la souris est activée et l’entrée de fenêtre est désactivée. La modification de l’un de ces modes affecte uniquement l’entrée qui se produit après la définition du mode. les événements de souris ou de fenêtre en attente dans la mémoire tampon d’entrée ne sont pas vidés. Le pointeur de la souris s’affiche quel que soit le mode de la souris.                                                |
| **ACTIVER l’entrée de la \_ fenêtre \_**    | Contrôle si les événements de redimensionnement de mémoire tampon sont signalés dans la mémoire tampon d’entrée. Par défaut, l’entrée de la souris est activée et l’entrée de fenêtre est désactivée. La modification de l’un de ces modes affecte uniquement l’entrée qui se produit après la définition du mode. les événements de souris ou de fenêtre en attente dans la mémoire tampon d’entrée ne sont pas vidés. Le pointeur de la souris s’affiche quel que soit le mode de la souris.                                      |
| **ACTIVER \_ l' \_ entrée traitée** | Contrôle le traitement des entrées pour les applications à l’aide des fonctions d’e/s de console de haut niveau. Toutefois, si le mode d’entrée traité est activé, la combinaison de touches CTRL + C n’est pas signalée dans la mémoire tampon d’entrée de la console. Au lieu de cela, elle est passée à la fonction de gestionnaire de contrôle appropriée. Pour plus d’informations sur les gestionnaires de contrôles, consultez [gestionnaires de contrôle de console](console-control-handlers.md). |



Les modes de sortie d’une mémoire tampon d’écran n’affectent pas le comportement des fonctions de sortie de bas niveau.








