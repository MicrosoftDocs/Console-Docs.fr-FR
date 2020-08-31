---
title: Touches CTRL + C et CTRL + ATTN
description: Les combinaisons de touches CTRL + C et CTRL + ATTN reçoivent un traitement spécial par les processus de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_ctrl\_c\_and\_ctrl\_break\_signals'
- base.ctrl\_c\_and\_ctrl\_break\_signals
- consoles.ctrl\_c\_and\_ctrl\_break\_signals
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5357ed99-920b-47a0-a922-d5faed7bf23e
ms.openlocfilehash: 95e28c9d390e9edb0be7dcac5aa4600224ab118c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059216"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a>Touches CTRL + C et CTRL + ATTN


Les combinaisons de touches CTRL + C et CTRL + ATTN reçoivent un traitement spécial par les processus de la console. Par défaut, lorsqu’une fenêtre de console a le focus clavier, CTRL + C ou CTRL + Pause est traité comme un signal (SIGINT ou SIGBREAK) et non comme une entrée au clavier. Par défaut, ces signaux sont passés à tous les processus de console qui sont attachés à la console. (Les processus détachés ne sont pas affectés.) Le système crée un nouveau thread dans chaque processus client pour gérer l’événement. Le thread lève une exception si le processus est en cours de débogage. Le débogueur peut gérer l’exception ou continuer avec l’exception non gérée.

CTRL + ATTN est toujours traité comme un signal, mais une application peut modifier le comportement par défaut de CTRL + C de deux manières qui empêchent l’appel des fonctions du gestionnaire :

- La fonction [**SetConsoleMode**](setconsolemode.md) peut désactiver l’activation du mode d’entrée ** \_ traité \_ ** pour la mémoire tampon d’entrée d’une console. par conséquent, Ctrl + C est signalé comme entrée au clavier plutôt que comme signal.
- Quand [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) est appelé avec des valeurs **null** et **true** pour ses paramètres, le processus appelant ignore les signaux Ctrl + C. Le traitement normal CTRL + C est restauré en appelant **SetConsoleCtrlHandler** avec des valeurs **null** et **false** . Cet attribut qui ignore ou ignore les signaux CTRL + C est hérité par les processus enfants, mais il peut être activé ou désactivé par n’importe quel processus sans affecter les processus existants.

 

 




