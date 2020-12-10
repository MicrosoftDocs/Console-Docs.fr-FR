---
title: Signaux CTRL+C et CTRL+ATTN
description: Les combinaisons de touches CTRL+C et CTRL+ATTN reçoivent un traitement spécial par les processus de console.
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
ms.localizationpriority: high
ms.openlocfilehash: 38cc3486a9e945635147c2e17a4d2f0d197d1d3c
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420188"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a>Signaux CTRL+C et CTRL+ATTN

Les combinaisons de touches <kbd>CTRL</kbd>+<kbd>C</kbd> et <kbd>CTRL</kbd>+<kbd>ATTN</kbd> reçoivent un traitement spécial par les processus de console. Par défaut, quand une fenêtre de console a le focus clavier, la combinaison de touches <kbd>CTRL</kbd>+<kbd>C</kbd> ou <kbd>CTRL</kbd>+<kbd>ATTN</kbd> est traitée comme un signal (SIGINT ou SIGBREAK) et non comme une entrée de clavier. Par défaut, ces signaux sont passés à tous les processus de console qui sont attachés à la console. (Les processus détachés ne sont pas affectés. Consultez [**Création d’une console**](creation-of-a-console.md).) Le système crée un thread dans chaque processus client pour gérer l’événement. Le thread lève une exception si le processus est en cours de débogage. Le débogueur peut gérer l’exception ou continuer avec l’exception non gérée.

La combinaison de touches <kbd>CTRL</kbd>+<kbd>ATTN</kbd> est toujours traitée comme un signal, mais une application peut changer le comportement par défaut de <kbd>CTRL</kbd>+<kbd>C</kbd> de deux manières qui empêchent l’appel des fonctions du gestionnaire :

- La fonction [**SetConsoleMode**](setconsolemode.md) peut désactiver le mode d’entrée **ENABLE\_PROCESSED\_INPUT** pour la mémoire tampon d’entrée d’une console. Par conséquent, CTRL+C est signalé comme étant une entrée du clavier plutôt que comme un signal.
- Quand [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) est appelé avec les valeurs **NULL** et **TRUE** pour ses paramètres, le processus appelant ignore les signaux CTRL+C. Le traitement normal de CTRL+C est restauré en appelant **SetConsoleCtrlHandler** avec les valeurs **NULL** et **FALSE**. Cet attribut permettant d’ignorer ou de ne pas ignorer les signaux CTRL+C est hérité par les processus enfants, mais il peut être activé ou désactivé par n’importe quel processus sans affecter les processus existants.

Pour plus d’informations sur la façon dont ces signaux sont traités, notamment les délais d’attente, consultez la documentation de rappel sur la [**routine des gestionnaires**](handlerroutine.md).
