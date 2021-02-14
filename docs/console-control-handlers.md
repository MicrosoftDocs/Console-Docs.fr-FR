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
ms.openlocfilehash: 06528cfc93d074bd0cc2579d5ba50445025a04fb
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358139"
---
# <a name="console-control-handlers"></a><span data-ttu-id="56e28-104">Gestionnaires de contrôle d’une console</span><span class="sxs-lookup"><span data-stu-id="56e28-104">Console Control Handlers</span></span>

<span data-ttu-id="56e28-105">Chaque processus de console possède sa propre liste de fonctions de gestionnaire de contrôle qui sont appelées par le système lorsque le processus reçoit un signal [Ctrl + C](ctrl-c-and-ctrl-break-signals.md), [CTRL + ATTN](ctrl-c-and-ctrl-break-signals.md)ou [CTRL + fermer](ctrl-close-signal.md) .</span><span class="sxs-lookup"><span data-stu-id="56e28-105">Each console process has its own list of control handler functions that are called by the system when the process receives a [CTRL+C](ctrl-c-and-ctrl-break-signals.md), [CTRL+BREAK](ctrl-c-and-ctrl-break-signals.md), or [CTRL+CLOSE](ctrl-close-signal.md) signal.</span></span> <span data-ttu-id="56e28-106">Initialement, la liste des gestionnaires de contrôles pour chaque processus contient uniquement une fonction de gestionnaire par défaut qui appelle la fonction [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) .</span><span class="sxs-lookup"><span data-stu-id="56e28-106">Initially, the list of control handlers for each process contains only a default handler function that calls the [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) function.</span></span> <span data-ttu-id="56e28-107">Un processus de console peut ajouter ou supprimer des fonctions [**HandlerRoutine**](handlerroutine.md) supplémentaires en appelant la fonction [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) .</span><span class="sxs-lookup"><span data-stu-id="56e28-107">A console process can add or remove additional [**HandlerRoutine**](handlerroutine.md) functions by calling the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function.</span></span> <span data-ttu-id="56e28-108">Cette fonction n’affecte pas les listes de gestionnaires de contrôles pour d’autres processus.</span><span class="sxs-lookup"><span data-stu-id="56e28-108">This function does not affect the lists of control handlers for other processes.</span></span> <span data-ttu-id="56e28-109">Lorsqu’un processus de console reçoit l’un des signaux de contrôle, il appelle les fonctions de gestionnaire sur une base de dernier enregistrement, première appel, jusqu’à ce que l’un des gestionnaires retourne la **valeur true**.</span><span class="sxs-lookup"><span data-stu-id="56e28-109">When a console process receives any of the control signals, it calls the handler functions on a last-registered, first-called basis until one of the handlers returns **TRUE**.</span></span> <span data-ttu-id="56e28-110">Si aucun des gestionnaires ne retourne la **valeur true**, le gestionnaire par défaut est appelé.</span><span class="sxs-lookup"><span data-stu-id="56e28-110">If none of the handlers returns **TRUE**, the default handler is called.</span></span>

<span data-ttu-id="56e28-111">Le paramètre *dwCtrlType* de la fonction identifie le signal de contrôle qui a été reçu, et la valeur de retour indique si le signal a été géré.</span><span class="sxs-lookup"><span data-stu-id="56e28-111">The function's *dwCtrlType* parameter identifies which control signal was received, and the return value indicates whether the signal was handled.</span></span>

<span data-ttu-id="56e28-112">Un nouveau thread est démarré dans le processus client de ligne de commande pour exécuter les routines du gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="56e28-112">A new thread is started inside the command-line client process to run the handler routines.</span></span> <span data-ttu-id="56e28-113">Vous trouverez plus d’informations sur les valeurs de délai d’attente et l’action de ce thread dans la documentation relative à la fonction [**HandlerRoutine**](handlerroutine.md#remarks) .</span><span class="sxs-lookup"><span data-stu-id="56e28-113">More information on the timeout values and action of this thread can be found in the [**HandlerRoutine**](handlerroutine.md#remarks) function documentation.</span></span>

<span data-ttu-id="56e28-114">Pour obtenir un exemple de fonction de gestionnaire de contrôles, consultez [inscription d’une fonction de gestionnaire de contrôle](registering-a-control-handler-function.md).</span><span class="sxs-lookup"><span data-stu-id="56e28-114">For an example of a control handler function, see [Registering a Control Handler Function](registering-a-control-handler-function.md).</span></span>