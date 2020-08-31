---
title: Gestionnaires de contrôle de console
description: Chaque processus de console possède sa propre liste de fonctions de gestionnaire de contrôle qui sont appelées par le système lorsque le processus reçoit un signal CTRL + C, CTRL + ATTN ou CTRL + fermer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_console\_control\_handlers'
- base.console\_control\_handlers
- consoles.console\_control\_handlers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6480e8ee-d228-4c07-99df-de1e0c3ca250
ms.openlocfilehash: b3fa6f3e842d1757b90ff03c30a343ad12964882
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059337"
---
# <a name="console-control-handlers"></a>Gestionnaires de contrôle de console


Chaque processus de console possède sa propre liste de fonctions de gestionnaire de contrôle qui sont appelées par le système lorsque le processus reçoit un signal [Ctrl + C](ctrl-c-and-ctrl-break-signals.md), [CTRL + ATTN](ctrl-c-and-ctrl-break-signals.md)ou [CTRL + fermer](ctrl-close-signal.md) . Initialement, la liste des gestionnaires de contrôles pour chaque processus contient uniquement une fonction de gestionnaire par défaut qui appelle la fonction [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) . Un processus de console peut ajouter ou supprimer des fonctions [**HandlerRoutine**](handlerroutine.md) supplémentaires en appelant la fonction [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) . Cette fonction n’affecte pas les listes de gestionnaires de contrôles pour d’autres processus. Lorsqu’un processus de console reçoit l’un des signaux de contrôle, il appelle les fonctions de gestionnaire sur une base de dernier enregistrement, première appel, jusqu’à ce que l’un des gestionnaires retourne la **valeur true**. Si aucun des gestionnaires ne retourne la **valeur true**, le gestionnaire par défaut est appelé.

Le paramètre *dwCtrlType* de la fonction identifie le signal de contrôle qui a été reçu, et la valeur de retour indique si le signal a été géré.

Pour obtenir un exemple de fonction de gestionnaire de contrôles, consultez [inscription d’une fonction de gestionnaire de contrôle](registering-a-control-handler-function.md).

 

 




