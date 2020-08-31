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
# <a name="ctrlc-and-ctrlbreak-signals"></a><span data-ttu-id="5fecc-104">Touches CTRL + C et CTRL + ATTN</span><span class="sxs-lookup"><span data-stu-id="5fecc-104">CTRL+C and CTRL+BREAK Signals</span></span>


<span data-ttu-id="5fecc-105">Les combinaisons de touches CTRL + C et CTRL + ATTN reçoivent un traitement spécial par les processus de la console.</span><span class="sxs-lookup"><span data-stu-id="5fecc-105">The CTRL+C and CTRL+BREAK key combinations receive special handling by console processes.</span></span> <span data-ttu-id="5fecc-106">Par défaut, lorsqu’une fenêtre de console a le focus clavier, CTRL + C ou CTRL + Pause est traité comme un signal (SIGINT ou SIGBREAK) et non comme une entrée au clavier.</span><span class="sxs-lookup"><span data-stu-id="5fecc-106">By default, when a console window has the keyboard focus, CTRL+C or CTRL+BREAK is treated as a signal (SIGINT or SIGBREAK) and not as keyboard input.</span></span> <span data-ttu-id="5fecc-107">Par défaut, ces signaux sont passés à tous les processus de console qui sont attachés à la console.</span><span class="sxs-lookup"><span data-stu-id="5fecc-107">By default, these signals are passed to all console processes that are attached to the console.</span></span> <span data-ttu-id="5fecc-108">(Les processus détachés ne sont pas affectés.) Le système crée un nouveau thread dans chaque processus client pour gérer l’événement.</span><span class="sxs-lookup"><span data-stu-id="5fecc-108">(Detached processes are not affected.) The system creates a new thread in each client process to handle the event.</span></span> <span data-ttu-id="5fecc-109">Le thread lève une exception si le processus est en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="5fecc-109">The thread raises an exception if the process is being debugged.</span></span> <span data-ttu-id="5fecc-110">Le débogueur peut gérer l’exception ou continuer avec l’exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="5fecc-110">The debugger can handle the exception or continue with the exception unhandled.</span></span>

<span data-ttu-id="5fecc-111">CTRL + ATTN est toujours traité comme un signal, mais une application peut modifier le comportement par défaut de CTRL + C de deux manières qui empêchent l’appel des fonctions du gestionnaire :</span><span class="sxs-lookup"><span data-stu-id="5fecc-111">CTRL+BREAK is always treated as a signal, but an application can change the default CTRL+C behavior in two ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="5fecc-112">La fonction [**SetConsoleMode**](setconsolemode.md) peut désactiver l’activation du mode d’entrée \*\* \_ traité \_ \*\* pour la mémoire tampon d’entrée d’une console. par conséquent, Ctrl + C est signalé comme entrée au clavier plutôt que comme signal.</span><span class="sxs-lookup"><span data-stu-id="5fecc-112">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** input mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="5fecc-113">Quand [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) est appelé avec des valeurs **null** et **true** pour ses paramètres, le processus appelant ignore les signaux Ctrl + C.</span><span class="sxs-lookup"><span data-stu-id="5fecc-113">When [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) is called with **NULL** and **TRUE** values for its parameters, the calling process ignores CTRL+C signals.</span></span> <span data-ttu-id="5fecc-114">Le traitement normal CTRL + C est restauré en appelant **SetConsoleCtrlHandler** avec des valeurs **null** et **false** .</span><span class="sxs-lookup"><span data-stu-id="5fecc-114">Normal CTRL+C processing is restored by calling **SetConsoleCtrlHandler** with **NULL** and **FALSE** values.</span></span> <span data-ttu-id="5fecc-115">Cet attribut qui ignore ou ignore les signaux CTRL + C est hérité par les processus enfants, mais il peut être activé ou désactivé par n’importe quel processus sans affecter les processus existants.</span><span class="sxs-lookup"><span data-stu-id="5fecc-115">This attribute of ignoring or not ignoring CTRL+C signals is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>

 

 




