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
# <a name="ctrlc-and-ctrlbreak-signals"></a><span data-ttu-id="2d7f3-104">Touches CTRL + C et CTRL + ATTN</span><span class="sxs-lookup"><span data-stu-id="2d7f3-104">CTRL+C and CTRL+BREAK Signals</span></span>

<span data-ttu-id="2d7f3-105">Les combinaisons de touches <kbd>CTRL</kbd> + <kbd>C</kbd> et <kbd>CTRL +</kbd> + <kbd>Attn</kbd> reçoivent un traitement spécial par les processus de la console.</span><span class="sxs-lookup"><span data-stu-id="2d7f3-105">The <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations receive special handling by console processes.</span></span> <span data-ttu-id="2d7f3-106">Par défaut, lorsqu’une fenêtre de console a le focus clavier, la <kbd>touche Ctrl</kbd> + <kbd>C</kbd> ou <kbd>CTRL</kbd> + <kbd>BREAK</kbd> est traitée comme un signal (SIGINT ou SIGBREAK) et non pas comme une entrée au clavier.</span><span class="sxs-lookup"><span data-stu-id="2d7f3-106">By default, when a console window has the keyboard focus, <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> is treated as a signal (SIGINT or SIGBREAK) and not as keyboard input.</span></span> <span data-ttu-id="2d7f3-107">Par défaut, ces signaux sont passés à tous les processus de console qui sont attachés à la console.</span><span class="sxs-lookup"><span data-stu-id="2d7f3-107">By default, these signals are passed to all console processes that are attached to the console.</span></span> <span data-ttu-id="2d7f3-108">(Les processus détachés ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="2d7f3-108">(Detached processes are not affected.</span></span> <span data-ttu-id="2d7f3-109">Consultez [**création d’une console**](creation-of-a-console.md).) Le système crée un nouveau thread dans chaque processus client pour gérer l’événement.</span><span class="sxs-lookup"><span data-stu-id="2d7f3-109">See [**Creation of a Console**](creation-of-a-console.md).) The system creates a new thread in each client process to handle the event.</span></span> <span data-ttu-id="2d7f3-110">Le thread lève une exception si le processus est en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="2d7f3-110">The thread raises an exception if the process is being debugged.</span></span> <span data-ttu-id="2d7f3-111">Le débogueur peut gérer l’exception ou continuer avec l’exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="2d7f3-111">The debugger can handle the exception or continue with the exception unhandled.</span></span>

<span data-ttu-id="2d7f3-112"><kbd>CTRL</kbd> + La fonction <kbd>break</kbd> est toujours traitée comme un signal, mais une application peut modifier le comportement par défaut de la <kbd>touche Ctrl</kbd> + <kbd>C</kbd> de deux manières qui empêchent l’appel des fonctions du gestionnaire :</span><span class="sxs-lookup"><span data-stu-id="2d7f3-112"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but an application can change the default <kbd>CTRL</kbd>+<kbd>C</kbd> behavior in two ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="2d7f3-113">La fonction [**SetConsoleMode**](setconsolemode.md) peut désactiver l’activation du mode d’entrée **\_ traité \_** pour la mémoire tampon d’entrée d’une console. par conséquent, Ctrl + C est signalé comme entrée au clavier plutôt que comme signal.</span><span class="sxs-lookup"><span data-stu-id="2d7f3-113">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** input mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="2d7f3-114">Quand [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) est appelé avec des valeurs **null** et **true** pour ses paramètres, le processus appelant ignore les signaux Ctrl + C.</span><span class="sxs-lookup"><span data-stu-id="2d7f3-114">When [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) is called with **NULL** and **TRUE** values for its parameters, the calling process ignores CTRL+C signals.</span></span> <span data-ttu-id="2d7f3-115">Le traitement normal CTRL + C est restauré en appelant **SetConsoleCtrlHandler** avec des valeurs **null** et **false** .</span><span class="sxs-lookup"><span data-stu-id="2d7f3-115">Normal CTRL+C processing is restored by calling **SetConsoleCtrlHandler** with **NULL** and **FALSE** values.</span></span> <span data-ttu-id="2d7f3-116">Cet attribut qui ignore ou ignore les signaux CTRL + C est hérité par les processus enfants, mais il peut être activé ou désactivé par n’importe quel processus sans affecter les processus existants.</span><span class="sxs-lookup"><span data-stu-id="2d7f3-116">This attribute of ignoring or not ignoring CTRL+C signals is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>

<span data-ttu-id="2d7f3-117">Pour plus d’informations sur le traitement de ces signaux, y compris les délais d’attente, consultez la documentation sur le rappel de [**routine du gestionnaire**](handlerroutine.md) .</span><span class="sxs-lookup"><span data-stu-id="2d7f3-117">For more information on how these signals are processed, including timeouts, please see the [**Handler Routine**](handlerroutine.md) callback documentation.</span></span>
