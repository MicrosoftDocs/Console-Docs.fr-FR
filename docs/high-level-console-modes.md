---
title: Modes de la console High-Level
description: Le comportement des fonctions de console de haut niveau est affecté par les modes d’entrée et de sortie de la console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_high\_level\_console\_modes'
- base.high\_level\_console\_modes
- consoles.high\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3ec915eb-333d-484d-a14d-46377b503ecc
ms.openlocfilehash: 418983a788957578e97fee70624fd80c1b09bc04
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038640"
---
# <a name="high-level-console-modes"></a><span data-ttu-id="6ff39-104">Modes de la console High-Level</span><span class="sxs-lookup"><span data-stu-id="6ff39-104">High-Level Console Modes</span></span>

<span data-ttu-id="6ff39-105">Le comportement des fonctions de console de haut niveau est affecté par les modes d’entrée et de sortie de la console.</span><span class="sxs-lookup"><span data-stu-id="6ff39-105">The behavior of the high-level console functions is affected by the console input and output modes.</span></span> <span data-ttu-id="6ff39-106">Tous les modes d’entrée de la console suivants sont activés pour la mémoire tampon d’entrée d’une console lors de la création d’une console :</span><span class="sxs-lookup"><span data-stu-id="6ff39-106">All of the following console input modes are enabled for a console's input buffer when a console is created:</span></span>

- <span data-ttu-id="6ff39-107">Mode de saisie de ligne</span><span class="sxs-lookup"><span data-stu-id="6ff39-107">Line input mode</span></span>
- <span data-ttu-id="6ff39-108">Mode de saisie traité</span><span class="sxs-lookup"><span data-stu-id="6ff39-108">Processed input mode</span></span>
- <span data-ttu-id="6ff39-109">Mode de saisie d’écho</span><span class="sxs-lookup"><span data-stu-id="6ff39-109">Echo input mode</span></span>

<span data-ttu-id="6ff39-110">Les deux modes de sortie de console suivants sont activés pour une mémoire tampon d’écran de console lors de sa création :</span><span class="sxs-lookup"><span data-stu-id="6ff39-110">Both of the following console output modes are enabled for a console screen buffer when it is created:</span></span>

- <span data-ttu-id="6ff39-111">Mode de sortie traité</span><span class="sxs-lookup"><span data-stu-id="6ff39-111">Processed output mode</span></span>
- <span data-ttu-id="6ff39-112">Retour en mode de sortie de EOL</span><span class="sxs-lookup"><span data-stu-id="6ff39-112">Wrapping at EOL output mode</span></span>

<span data-ttu-id="6ff39-113">Les trois modes d’entrée, ainsi que le mode de sortie traité, sont conçus pour fonctionner ensemble.</span><span class="sxs-lookup"><span data-stu-id="6ff39-113">All three input modes, along with processed output mode, are designed to work together.</span></span> <span data-ttu-id="6ff39-114">Il est préférable d’activer ou de désactiver tous ces modes en tant que groupe.</span><span class="sxs-lookup"><span data-stu-id="6ff39-114">It is best to either enable or disable all of these modes as a group.</span></span> <span data-ttu-id="6ff39-115">Lorsque toutes les sont activées, l’application est dite en mode « cuit », ce qui signifie que la majeure partie du traitement est gérée pour l’application.</span><span class="sxs-lookup"><span data-stu-id="6ff39-115">When all are enabled, the application is said to be in "cooked" mode, which means that most of the processing is handled for the application.</span></span> <span data-ttu-id="6ff39-116">Lorsque tous les sont désactivés, l’application est en mode « brut », ce qui signifie que l’entrée n’est pas filtrée et que le traitement est laissé à l’application.</span><span class="sxs-lookup"><span data-stu-id="6ff39-116">When all are disabled, the application is in "raw" mode, which means that input is unfiltered and any processing is left to the application.</span></span>

<span data-ttu-id="6ff39-117">Une application peut utiliser la fonction [**GetConsoleMode**](getconsolemode.md) pour déterminer le mode actuel de la mémoire tampon d’entrée ou de mémoire tampon d’entrée d’une console.</span><span class="sxs-lookup"><span data-stu-id="6ff39-117">An application can use the [**GetConsoleMode**](getconsolemode.md) function to determine the current mode of a console's input buffer or screen buffer.</span></span> <span data-ttu-id="6ff39-118">Vous pouvez activer ou désactiver l’un de ces modes en utilisant les valeurs suivantes dans la fonction [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="6ff39-118">You can enable or disable any of these modes by using the following values in the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="6ff39-119">Notez que la définition du mode de sortie d’une mémoire tampon d’écran n’affecte pas le mode de sortie des autres mémoires tampons d’écran.</span><span class="sxs-lookup"><span data-stu-id="6ff39-119">Note that setting the output mode of one screen buffer does not affect the output mode of other screen buffers.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]
