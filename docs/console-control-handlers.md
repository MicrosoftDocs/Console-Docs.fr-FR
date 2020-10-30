---
title: Gestionnaires de contrôle d’une console
description: Chaque processus de console possède sa propre liste de fonctions de gestionnaire de contrôle qui sont appelées par le système lorsque le processus reçoit un signal CTRL + C, CTRL + ATTN ou CTRL + fermer.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_console\_control\_handlers'
- base.console\_control\_handlers
- consoles.console\_control\_handlers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6480e8ee-d228-4c07-99df-de1e0c3ca250
ms.openlocfilehash: 41a1326b5b27531bf74ac571d6881a0f67c2b073
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038427"
---
# <a name="console-control-handlers"></a>Gestionnaires de contrôle d’une console

Chaque processus de console possède sa propre liste de fonctions de gestionnaire de contrôle qui sont appelées par le système lorsque le processus reçoit un signal [Ctrl + C](ctrl-c-and-ctrl-break-signals.md), [CTRL + ATTN](ctrl-c-and-ctrl-break-signals.md)ou [CTRL + fermer](ctrl-close-signal.md) . Initialement, la liste des gestionnaires de contrôles pour chaque processus contient uniquement une fonction de gestionnaire par défaut qui appelle la fonction [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) . Un processus de console peut ajouter ou supprimer des fonctions [**HandlerRoutine**](handlerroutine.md) supplémentaires en appelant la fonction [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) . Cette fonction n’affecte pas les listes de gestionnaires de contrôles pour d’autres processus. Lorsqu’un processus de console reçoit l’un des signaux de contrôle, il appelle les fonctions de gestionnaire sur une base de dernier enregistrement, première appel, jusqu’à ce que l’un des gestionnaires retourne la **valeur true** . Si aucun des gestionnaires ne retourne la **valeur true** , le gestionnaire par défaut est appelé.

Le paramètre *dwCtrlType* de la fonction identifie le signal de contrôle qui a été reçu, et la valeur de retour indique si le signal a été géré.

Un nouveau thread est démarré dans le processus client de ligne de commande pour exécuter les routines du gestionnaire. Vous trouverez plus d’informations sur les valeurs de délai d’attente et l’action de ce thread dans la documentation relative à la fonction [**HandlerRoutine**](handlerroutine.md#remarks) .

Pour obtenir un exemple de fonction de gestionnaire de contrôles, consultez [inscription d’une fonction de gestionnaire de contrôle](registering-a-control-handler-function.md).
