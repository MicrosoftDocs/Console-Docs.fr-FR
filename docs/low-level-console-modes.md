---
title: Modes de la console Low-Level
description: Les types d’événements d’entrée signalés dans le tampon d’entrée d’une console dépendent des modes de saisie de la souris et de la fenêtre de la console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_low\_level\_console\_modes'
- base.low\_level\_console\_modes
- consoles.low\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 41bfdc51-27cb-4d5e-898c-507ffc8789b9
ms.openlocfilehash: acd68e9679f209349f3e0db6989ca905815525a9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039537"
---
# <a name="low-level-console-modes"></a>Modes de la console Low-Level

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Les types d’événements d’entrée signalés dans le tampon d’entrée d’une console dépendent des modes de saisie de la souris et de la fenêtre de la console. Le mode d’entrée traité de la console détermine la façon dont le système gère la combinaison de touches CTRL + C. Pour définir ou récupérer l’état des modes d’entrée d’une console, une application peut spécifier un handle de mémoire tampon d’entrée de la console dans un appel à la fonction [**SetConsoleMode**](setconsolemode.md) ou [**GetConsoleMode**](getconsolemode.md) . Les modes suivants sont utilisés avec les descripteurs d’entrée de la console.

| Mode | Description |
|-|-|
| **ACTIVER l' \_ entrée de la souris \_**     | Contrôle si les événements de souris sont signalés dans la mémoire tampon d’entrée. Par défaut, l’entrée de la souris est activée et l’entrée de fenêtre est désactivée. La modification de l’un de ces modes affecte uniquement l’entrée qui se produit après la définition du mode. les événements de souris ou de fenêtre en attente dans la mémoire tampon d’entrée ne sont pas vidés. Le pointeur de la souris s’affiche quel que soit le mode de la souris.                                                |
| **ACTIVER l’entrée de la \_ fenêtre \_**    | Contrôle si les événements de redimensionnement de mémoire tampon sont signalés dans la mémoire tampon d’entrée. Par défaut, l’entrée de la souris est activée et l’entrée de fenêtre est désactivée. La modification de l’un de ces modes affecte uniquement l’entrée qui se produit après la définition du mode. les événements de souris ou de fenêtre en attente dans la mémoire tampon d’entrée ne sont pas vidés. Le pointeur de la souris s’affiche quel que soit le mode de la souris.                                      |
| **ACTIVER \_ l' \_ entrée traitée** | Contrôle le traitement des entrées pour les applications à l’aide des fonctions d’e/s de console de haut niveau. Toutefois, si le mode d’entrée traité est activé, la combinaison de touches CTRL + C n’est pas signalée dans la mémoire tampon d’entrée de la console. Au lieu de cela, elle est passée à la fonction de gestionnaire de contrôle appropriée. Pour plus d’informations sur les gestionnaires de contrôles, consultez [gestionnaires de contrôle de console](console-control-handlers.md). |

Les modes de sortie d’une mémoire tampon d’écran n’affectent pas le comportement des fonctions de sortie de bas niveau.
