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
# <a name="console-control-handlers"></a><span data-ttu-id="9cce0-104">Gestionnaires de contrôle de console</span><span class="sxs-lookup"><span data-stu-id="9cce0-104">Console Control Handlers</span></span>


<span data-ttu-id="9cce0-105">Chaque processus de console possède sa propre liste de fonctions de gestionnaire de contrôle qui sont appelées par le système lorsque le processus reçoit un signal [Ctrl + C](ctrl-c-and-ctrl-break-signals.md), [CTRL + ATTN](ctrl-c-and-ctrl-break-signals.md)ou [CTRL + fermer](ctrl-close-signal.md) .</span><span class="sxs-lookup"><span data-stu-id="9cce0-105">Each console process has its own list of control handler functions that are called by the system when the process receives a [CTRL+C](ctrl-c-and-ctrl-break-signals.md), [CTRL+BREAK](ctrl-c-and-ctrl-break-signals.md), or [CTRL+CLOSE](ctrl-close-signal.md) signal.</span></span> <span data-ttu-id="9cce0-106">Initialement, la liste des gestionnaires de contrôles pour chaque processus contient uniquement une fonction de gestionnaire par défaut qui appelle la fonction [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) .</span><span class="sxs-lookup"><span data-stu-id="9cce0-106">Initially, the list of control handlers for each process contains only a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function.</span></span> <span data-ttu-id="9cce0-107">Un processus de console peut ajouter ou supprimer des fonctions [**HandlerRoutine**](handlerroutine.md) supplémentaires en appelant la fonction [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) .</span><span class="sxs-lookup"><span data-stu-id="9cce0-107">A console process can add or remove additional [**HandlerRoutine**](handlerroutine.md) functions by calling the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function.</span></span> <span data-ttu-id="9cce0-108">Cette fonction n’affecte pas les listes de gestionnaires de contrôles pour d’autres processus.</span><span class="sxs-lookup"><span data-stu-id="9cce0-108">This function does not affect the lists of control handlers for other processes.</span></span> <span data-ttu-id="9cce0-109">Lorsqu’un processus de console reçoit l’un des signaux de contrôle, il appelle les fonctions de gestionnaire sur une base de dernier enregistrement, première appel, jusqu’à ce que l’un des gestionnaires retourne la **valeur true**.</span><span class="sxs-lookup"><span data-stu-id="9cce0-109">When a console process receives any of the control signals, it calls the handler functions on a last-registered, first-called basis until one of the handlers returns **TRUE**.</span></span> <span data-ttu-id="9cce0-110">Si aucun des gestionnaires ne retourne la **valeur true**, le gestionnaire par défaut est appelé.</span><span class="sxs-lookup"><span data-stu-id="9cce0-110">If none of the handlers returns **TRUE**, the default handler is called.</span></span>

<span data-ttu-id="9cce0-111">Le paramètre *dwCtrlType* de la fonction identifie le signal de contrôle qui a été reçu, et la valeur de retour indique si le signal a été géré.</span><span class="sxs-lookup"><span data-stu-id="9cce0-111">The function's *dwCtrlType* parameter identifies which control signal was received, and the return value indicates whether the signal was handled.</span></span>

<span data-ttu-id="9cce0-112">Pour obtenir un exemple de fonction de gestionnaire de contrôles, consultez [inscription d’une fonction de gestionnaire de contrôle](registering-a-control-handler-function.md).</span><span class="sxs-lookup"><span data-stu-id="9cce0-112">For an example of a control handler function, see [Registering a Control Handler Function](registering-a-control-handler-function.md).</span></span>

 

 




