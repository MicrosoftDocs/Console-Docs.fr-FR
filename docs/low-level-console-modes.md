---
title: Modes de la console de bas niveau
description: Les types d’événements d’entrée signalés dans le tampon d’entrée d’une console dépendent des modes de saisie de la souris et de la fenêtre de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_low\_level\_console\_modes'
- base.low\_level\_console\_modes
- consoles.low\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 41bfdc51-27cb-4d5e-898c-507ffc8789b9
ms.openlocfilehash: 375b3b6eaef499324bdbde24ec973d91c50dda5b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059284"
---
# <a name="low-level-console-modes"></a><span data-ttu-id="a1847-104">Modes de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="a1847-104">Low-Level Console Modes</span></span>


<span data-ttu-id="a1847-105">Les types d’événements d’entrée signalés dans le tampon d’entrée d’une console dépendent des modes de saisie de la souris et de la fenêtre de la console.</span><span class="sxs-lookup"><span data-stu-id="a1847-105">The types of input events reported in a console's input buffer depend on the console's mouse and window input modes.</span></span> <span data-ttu-id="a1847-106">Le mode d’entrée traité de la console détermine la façon dont le système gère la combinaison de touches CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="a1847-106">The console's processed input mode determines how the system handles the CTRL+C key combination.</span></span> <span data-ttu-id="a1847-107">Pour définir ou récupérer l’état des modes d’entrée d’une console, une application peut spécifier un handle de mémoire tampon d’entrée de la console dans un appel à la fonction [**SetConsoleMode**](setconsolemode.md) ou [**GetConsoleMode**](getconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="a1847-107">To set or retrieve the state of a console's input modes, an application can specify a console input buffer handle in a call to the [**SetConsoleMode**](setconsolemode.md) or [**GetConsoleMode**](getconsolemode.md) function.</span></span> <span data-ttu-id="a1847-108">Les modes suivants sont utilisés avec les descripteurs d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="a1847-108">The following modes are used with console input handles.</span></span>


| <span data-ttu-id="a1847-109">Mode</span><span class="sxs-lookup"><span data-stu-id="a1847-109">Mode</span></span>                         | <span data-ttu-id="a1847-110">Description</span><span class="sxs-lookup"><span data-stu-id="a1847-110">Description</span></span>                                                                                                                                                                                                                                                                                                                                                                                           |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a1847-111">**ACTIVER l' \_ entrée de la souris \_**</span><span class="sxs-lookup"><span data-stu-id="a1847-111">**ENABLE\_MOUSE\_INPUT**</span></span>     | <span data-ttu-id="a1847-112">Contrôle si les événements de souris sont signalés dans la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="a1847-112">Controls whether mouse events are reported in the input buffer.</span></span> <span data-ttu-id="a1847-113">Par défaut, l’entrée de la souris est activée et l’entrée de fenêtre est désactivée.</span><span class="sxs-lookup"><span data-stu-id="a1847-113">By default, mouse input is enabled and window input is disabled.</span></span> <span data-ttu-id="a1847-114">La modification de l’un de ces modes affecte uniquement l’entrée qui se produit après la définition du mode. les événements de souris ou de fenêtre en attente dans la mémoire tampon d’entrée ne sont pas vidés.</span><span class="sxs-lookup"><span data-stu-id="a1847-114">Changing either of these modes affects only input that occurs after the mode is set; pending mouse or window events in the input buffer are not flushed.</span></span> <span data-ttu-id="a1847-115">Le pointeur de la souris s’affiche quel que soit le mode de la souris.</span><span class="sxs-lookup"><span data-stu-id="a1847-115">The mouse pointer is displayed regardless of the mouse mode.</span></span>                                                |
| <span data-ttu-id="a1847-116">**ACTIVER l’entrée de la \_ fenêtre \_**</span><span class="sxs-lookup"><span data-stu-id="a1847-116">**ENABLE\_WINDOW\_INPUT**</span></span>    | <span data-ttu-id="a1847-117">Contrôle si les événements de redimensionnement de mémoire tampon sont signalés dans la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="a1847-117">Controls whether buffer-resizing events are reported in the input buffer.</span></span> <span data-ttu-id="a1847-118">Par défaut, l’entrée de la souris est activée et l’entrée de fenêtre est désactivée.</span><span class="sxs-lookup"><span data-stu-id="a1847-118">By default, mouse input is enabled and window input is disabled.</span></span> <span data-ttu-id="a1847-119">La modification de l’un de ces modes affecte uniquement l’entrée qui se produit après la définition du mode. les événements de souris ou de fenêtre en attente dans la mémoire tampon d’entrée ne sont pas vidés.</span><span class="sxs-lookup"><span data-stu-id="a1847-119">Changing either of these modes affects only input that occurs after the mode is set; pending mouse or window events in the input buffer are not flushed.</span></span> <span data-ttu-id="a1847-120">Le pointeur de la souris s’affiche quel que soit le mode de la souris.</span><span class="sxs-lookup"><span data-stu-id="a1847-120">The mouse pointer is displayed regardless of the mouse mode.</span></span>                                      |
| <span data-ttu-id="a1847-121">**ACTIVER \_ l' \_ entrée traitée**</span><span class="sxs-lookup"><span data-stu-id="a1847-121">**ENABLE\_PROCESSED\_INPUT**</span></span> | <span data-ttu-id="a1847-122">Contrôle le traitement des entrées pour les applications à l’aide des fonctions d’e/s de console de haut niveau.</span><span class="sxs-lookup"><span data-stu-id="a1847-122">Controls the processing of input for applications using the high-level console I/O functions.</span></span> <span data-ttu-id="a1847-123">Toutefois, si le mode d’entrée traité est activé, la combinaison de touches CTRL + C n’est pas signalée dans la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="a1847-123">However, if processed input mode is enabled, the CTRL+C key combination is not reported in the console's input buffer.</span></span> <span data-ttu-id="a1847-124">Au lieu de cela, elle est passée à la fonction de gestionnaire de contrôle appropriée.</span><span class="sxs-lookup"><span data-stu-id="a1847-124">Instead, it is passed on to the appropriate control handler function.</span></span> <span data-ttu-id="a1847-125">Pour plus d’informations sur les gestionnaires de contrôles, consultez [gestionnaires de contrôle de console](console-control-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="a1847-125">For more information about control handlers, see [Console Control Handlers](console-control-handlers.md).</span></span> |



<span data-ttu-id="a1847-126">Les modes de sortie d’une mémoire tampon d’écran n’affectent pas le comportement des fonctions de sortie de bas niveau.</span><span class="sxs-lookup"><span data-stu-id="a1847-126">The output modes of a screen buffer do not affect the behavior of the low-level output functions.</span></span>








