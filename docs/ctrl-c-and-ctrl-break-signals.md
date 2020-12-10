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
# <a name="ctrlc-and-ctrlbreak-signals"></a><span data-ttu-id="0c794-104">Signaux CTRL+C et CTRL+ATTN</span><span class="sxs-lookup"><span data-stu-id="0c794-104">CTRL+C and CTRL+BREAK Signals</span></span>

<span data-ttu-id="0c794-105">Les combinaisons de touches <kbd>CTRL</kbd>+<kbd>C</kbd> et <kbd>CTRL</kbd>+<kbd>ATTN</kbd> reçoivent un traitement spécial par les processus de console.</span><span class="sxs-lookup"><span data-stu-id="0c794-105">The <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations receive special handling by console processes.</span></span> <span data-ttu-id="0c794-106">Par défaut, quand une fenêtre de console a le focus clavier, la combinaison de touches <kbd>CTRL</kbd>+<kbd>C</kbd> ou <kbd>CTRL</kbd>+<kbd>ATTN</kbd> est traitée comme un signal (SIGINT ou SIGBREAK) et non comme une entrée de clavier.</span><span class="sxs-lookup"><span data-stu-id="0c794-106">By default, when a console window has the keyboard focus, <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> is treated as a signal (SIGINT or SIGBREAK) and not as keyboard input.</span></span> <span data-ttu-id="0c794-107">Par défaut, ces signaux sont passés à tous les processus de console qui sont attachés à la console.</span><span class="sxs-lookup"><span data-stu-id="0c794-107">By default, these signals are passed to all console processes that are attached to the console.</span></span> <span data-ttu-id="0c794-108">(Les processus détachés ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="0c794-108">(Detached processes are not affected.</span></span> <span data-ttu-id="0c794-109">Consultez [**Création d’une console**](creation-of-a-console.md).) Le système crée un thread dans chaque processus client pour gérer l’événement.</span><span class="sxs-lookup"><span data-stu-id="0c794-109">See [**Creation of a Console**](creation-of-a-console.md).) The system creates a new thread in each client process to handle the event.</span></span> <span data-ttu-id="0c794-110">Le thread lève une exception si le processus est en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="0c794-110">The thread raises an exception if the process is being debugged.</span></span> <span data-ttu-id="0c794-111">Le débogueur peut gérer l’exception ou continuer avec l’exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="0c794-111">The debugger can handle the exception or continue with the exception unhandled.</span></span>

<span data-ttu-id="0c794-112">La combinaison de touches <kbd>CTRL</kbd>+<kbd>ATTN</kbd> est toujours traitée comme un signal, mais une application peut changer le comportement par défaut de <kbd>CTRL</kbd>+<kbd>C</kbd> de deux manières qui empêchent l’appel des fonctions du gestionnaire :</span><span class="sxs-lookup"><span data-stu-id="0c794-112"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but an application can change the default <kbd>CTRL</kbd>+<kbd>C</kbd> behavior in two ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="0c794-113">La fonction [**SetConsoleMode**](setconsolemode.md) peut désactiver le mode d’entrée **ENABLE\_PROCESSED\_INPUT** pour la mémoire tampon d’entrée d’une console. Par conséquent, CTRL+C est signalé comme étant une entrée du clavier plutôt que comme un signal.</span><span class="sxs-lookup"><span data-stu-id="0c794-113">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** input mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="0c794-114">Quand [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) est appelé avec les valeurs **NULL** et **TRUE** pour ses paramètres, le processus appelant ignore les signaux CTRL+C.</span><span class="sxs-lookup"><span data-stu-id="0c794-114">When [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) is called with **NULL** and **TRUE** values for its parameters, the calling process ignores CTRL+C signals.</span></span> <span data-ttu-id="0c794-115">Le traitement normal de CTRL+C est restauré en appelant **SetConsoleCtrlHandler** avec les valeurs **NULL** et **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="0c794-115">Normal CTRL+C processing is restored by calling **SetConsoleCtrlHandler** with **NULL** and **FALSE** values.</span></span> <span data-ttu-id="0c794-116">Cet attribut permettant d’ignorer ou de ne pas ignorer les signaux CTRL+C est hérité par les processus enfants, mais il peut être activé ou désactivé par n’importe quel processus sans affecter les processus existants.</span><span class="sxs-lookup"><span data-stu-id="0c794-116">This attribute of ignoring or not ignoring CTRL+C signals is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>

<span data-ttu-id="0c794-117">Pour plus d’informations sur la façon dont ces signaux sont traités, notamment les délais d’attente, consultez la documentation de rappel sur la [**routine des gestionnaires**](handlerroutine.md).</span><span class="sxs-lookup"><span data-stu-id="0c794-117">For more information on how these signals are processed, including timeouts, please see the [**Handler Routine**](handlerroutine.md) callback documentation.</span></span>
