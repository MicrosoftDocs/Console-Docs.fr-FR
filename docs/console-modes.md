---
title: Modes de la console
description: Un ensemble de modes d’entrée qui affecte les opérations d’entrée est associé à chaque mémoire tampon d’entrée de console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_console\_modes'
- base.console\_modes
- consoles.console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f0dcc123-3b12-44c4-8f94-920203f5198e
ms.openlocfilehash: 0bd048101546d20735745656677702f9f07115fd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039197"
---
# <a name="console-modes"></a><span data-ttu-id="c5756-104">Modes de la console</span><span class="sxs-lookup"><span data-stu-id="c5756-104">Console Modes</span></span>

<span data-ttu-id="c5756-105">Un ensemble de modes d’entrée qui affecte les opérations d’entrée est associé à chaque mémoire tampon d’entrée de console.</span><span class="sxs-lookup"><span data-stu-id="c5756-105">Associated with each console input buffer is a set of input modes that affects input operations.</span></span> <span data-ttu-id="c5756-106">De même, chaque mémoire tampon d’écran de console possède un ensemble de modes de sortie qui affecte les opérations de sortie.</span><span class="sxs-lookup"><span data-stu-id="c5756-106">Similarly, each console screen buffer has a set of output modes that affects output operations.</span></span> <span data-ttu-id="c5756-107">Les modes d’entrée peuvent être divisés en deux groupes : ceux qui affectent les fonctions d’entrée de haut niveau et ceux qui affectent les fonctions d’entrée de bas niveau.</span><span class="sxs-lookup"><span data-stu-id="c5756-107">The input modes can be divided into two groups: those that affect the high-level input functions and those that affect the low-level input functions.</span></span> <span data-ttu-id="c5756-108">Les modes de sortie affectent uniquement les applications qui utilisent les fonctions de sortie de haut niveau.</span><span class="sxs-lookup"><span data-stu-id="c5756-108">The output modes only affect applications that use the high-level output functions.</span></span>

<span data-ttu-id="c5756-109">La fonction [**GetConsoleMode**](getconsolemode.md) signale le mode d’entrée actuel de la mémoire tampon d’entrée d’une console ou le mode de sortie actuel d’une mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="c5756-109">The [**GetConsoleMode**](getconsolemode.md) function reports the current input mode of a console's input buffer or the current output mode of a screen buffer.</span></span> <span data-ttu-id="c5756-110">La fonction [**SetConsoleMode**](setconsolemode.md) définit le mode actuel d’une mémoire tampon d’entrée de la console ou d’une mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="c5756-110">The [**SetConsoleMode**](setconsolemode.md) function sets the current mode of either a console input buffer or a screen buffer.</span></span> <span data-ttu-id="c5756-111">Si une console possède plusieurs mémoires tampons d’écran, les modes de sortie de chacun peuvent être différents.</span><span class="sxs-lookup"><span data-stu-id="c5756-111">If a console has multiple screen buffers, the output modes of each can be different.</span></span> <span data-ttu-id="c5756-112">Une application peut modifier les modes d’e/s à tout moment.</span><span class="sxs-lookup"><span data-stu-id="c5756-112">An application can change I/O modes at any time.</span></span> <span data-ttu-id="c5756-113">Pour plus d’informations sur les modes de console qui affectent les opérations d’e/s de haut niveau et de bas niveau, consultez [modes de console de haut niveau](high-level-console-modes.md) et [modes de console de bas](low-level-console-modes.md)niveau.</span><span class="sxs-lookup"><span data-stu-id="c5756-113">For more information about the console modes that affect high-level and low-level I/O operations, see [High-Level Console Modes](high-level-console-modes.md) and [Low-Level Console Modes](low-level-console-modes.md).</span></span>

<span data-ttu-id="c5756-114">Une application en ligne de commande doit s’attendre à ce que d’autres applications de ligne de commande puissent modifier le mode de console à tout moment et ne pas restaurer son formulaire d’origine avant que le contrôle soit retourné.</span><span class="sxs-lookup"><span data-stu-id="c5756-114">A command-line application should expect that other command-line applications may change the console mode at any time and may not restore it to its original form before control is returned.</span></span> <span data-ttu-id="c5756-115">En outre, nous recommandons que toutes les applications de ligne de commande capturent le mode de console initial au démarrage et essaient de la restaurer au moment de la fermeture pour garantir un impact minimal sur les autres applications de ligne de commande attachées à la même console.</span><span class="sxs-lookup"><span data-stu-id="c5756-115">Additionally, we recommend that all command-line applications should capture the initial console mode at startup and attempt to restore it when exiting to ensure minimal impact on other command-line applications attached to the same console.</span></span>

<span data-ttu-id="c5756-116">La fonction [**GetConsoleDisplayMode**](getconsoledisplaymode.md) indique si la console active est en mode plein écran.</span><span class="sxs-lookup"><span data-stu-id="c5756-116">The [**GetConsoleDisplayMode**](getconsoledisplaymode.md) function reports whether the current console is in full-screen mode.</span></span>
