---
title: Touches CTRL + C et CTRL + ATTN
description: Les combinaisons de touches CTRL + C et CTRL + ATTN reçoivent un traitement spécial par les processus de la console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_ctrl\_c\_and\_ctrl\_break\_signals'
- base.ctrl\_c\_and\_ctrl\_break\_signals
- consoles.ctrl\_c\_and\_ctrl\_break\_signals
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5357ed99-920b-47a0-a922-d5faed7bf23e
ms.openlocfilehash: 12a4541d51cb18109caa6d1c15c25479c9e91a7a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039097"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a>Touches CTRL + C et CTRL + ATTN

Les combinaisons de touches <kbd>CTRL</kbd> + <kbd>C</kbd> et <kbd>CTRL +</kbd> + <kbd>Attn</kbd> reçoivent un traitement spécial par les processus de la console. Par défaut, lorsqu’une fenêtre de console a le focus clavier, la <kbd>touche Ctrl</kbd> + <kbd>C</kbd> ou <kbd>CTRL</kbd> + <kbd>BREAK</kbd> est traitée comme un signal (SIGINT ou SIGBREAK) et non pas comme une entrée au clavier. Par défaut, ces signaux sont passés à tous les processus de console qui sont attachés à la console. (Les processus détachés ne sont pas affectés. Consultez [**création d’une console**](creation-of-a-console.md).) Le système crée un nouveau thread dans chaque processus client pour gérer l’événement. Le thread lève une exception si le processus est en cours de débogage. Le débogueur peut gérer l’exception ou continuer avec l’exception non gérée.

<kbd>CTRL</kbd> + La fonction <kbd>break</kbd> est toujours traitée comme un signal, mais une application peut modifier le comportement par défaut de la <kbd>touche Ctrl</kbd> + <kbd>C</kbd> de deux manières qui empêchent l’appel des fonctions du gestionnaire :

- La fonction [**SetConsoleMode**](setconsolemode.md) peut désactiver l’activation du mode d’entrée **\_ traité \_** pour la mémoire tampon d’entrée d’une console. par conséquent, Ctrl + C est signalé comme entrée au clavier plutôt que comme signal.
- Quand [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) est appelé avec des valeurs **null** et **true** pour ses paramètres, le processus appelant ignore les signaux Ctrl + C. Le traitement normal CTRL + C est restauré en appelant **SetConsoleCtrlHandler** avec des valeurs **null** et **false** . Cet attribut qui ignore ou ignore les signaux CTRL + C est hérité par les processus enfants, mais il peut être activé ou désactivé par n’importe quel processus sans affecter les processus existants.

Pour plus d’informations sur le traitement de ces signaux, y compris les délais d’attente, consultez la documentation sur le rappel de [**routine du gestionnaire**](handlerroutine.md) .
