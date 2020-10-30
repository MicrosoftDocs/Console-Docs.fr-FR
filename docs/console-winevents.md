---
title: WinEvents de la console
description: Les constantes d’événement suivantes sont utilisées dans le paramètre Event de la fonction de rappel WinEventProc. Pour plus d’informations, consultez WinEvents.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- winuser/EVENT_CONSOLE_CARET
- winuser/EVENT_CONSOLE_END_APPLICATION
- winuser/EVENT_CONSOLE_LAYOUT
- winuser/EVENT_CONSOLE_START_APPLICATION
- winuser/EVENT_CONSOLE_UPDATE_REGION
- winuser/EVENT_CONSOLE_UPDATE_SCROLL
- winuser/EVENT_CONSOLE_UPDATE_SIMPLE
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
MS-HAID:
- '\_win32\_console\_winevents'
- base.console\_winevents
- consoles.console\_winevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b7078b2d-5508-4e42-bac2-34b70f1856e2
topic_type:
- apiref
api_name:
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
api_location:
- Winuser.h
api_type:
- HeaderDef
ms.openlocfilehash: 2c5d641140316089b38b836bf3fba7534ccd5600
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038327"
---
# <a name="console-winevents"></a><span data-ttu-id="2197a-105">WinEvents de la console</span><span class="sxs-lookup"><span data-stu-id="2197a-105">Console WinEvents</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2197a-106">Les WinEvents font partie de l’infrastructure de **[Active Accessibility Microsoft](https://docs.microsoft.com/windows/win32/winauto/microsoft-active-accessibility)** héritée.</span><span class="sxs-lookup"><span data-stu-id="2197a-106">WinEvents are part of the legacy **[Microsoft Active Accessibility](https://docs.microsoft.com/windows/win32/winauto/microsoft-active-accessibility)** framework.</span></span> <span data-ttu-id="2197a-107">Le développement à l’aide de ces événements est fortement déconseillé en faveur de l’infrastructure d' **[automatisation d’interface utilisateur de Microsoft](https://docs.microsoft.com/windows/win32/winauto/entry-uiauto-win32)** , qui fournit une suite plus robuste et plus complète d’interfaces permettant aux applications d’accessibilité et d’automatisation d’interagir avec la console.</span><span class="sxs-lookup"><span data-stu-id="2197a-107">Development using these events is strongly discouraged in favor of the **[Microsoft UI Automation](https://docs.microsoft.com/windows/win32/winauto/entry-uiauto-win32)** framework which provides a more robust and comprehensive suite of interfaces for accessibility and automation applications to interact with the console.</span></span> 

> [!WARNING]
> <span data-ttu-id="2197a-108">L’inscription à ces événements est une activité globale qui aura un impact considérable sur les performances de toutes les applications de ligne de commande exécutées sur un système en même temps, y compris les services et les utilitaires d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="2197a-108">Registering for these events is a global activity and will significantly impact performance of all command-line applications running on a system at the same time, including services and background utilities.</span></span> <span data-ttu-id="2197a-109">L’infrastructure d’automatisation de l' **interface utilisateur de Microsoft** est spécifique à la session de console et survient à cette limitation.</span><span class="sxs-lookup"><span data-stu-id="2197a-109">The **Microsoft UI Automation** framework is console session specific and overcomes this limitation.</span></span>

<span data-ttu-id="2197a-110">Les constantes d’événement suivantes sont utilisées dans le paramètre *Event* de la fonction de rappel [*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) .</span><span class="sxs-lookup"><span data-stu-id="2197a-110">The following event constants are used in the *event* parameter of the [*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) callback function.</span></span> <span data-ttu-id="2197a-111">Pour plus d’informations, consultez [winEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span><span class="sxs-lookup"><span data-stu-id="2197a-111">For more information, see [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span></span>

| <span data-ttu-id="2197a-112">Constante/valeur</span><span class="sxs-lookup"><span data-stu-id="2197a-112">Constant/value</span></span> | <span data-ttu-id="2197a-113">Description</span><span class="sxs-lookup"><span data-stu-id="2197a-113">Description</span></span> |
|-|-|
| <span data-ttu-id="2197a-114">**EVENT_CONSOLE_CARET** 0x4001</span><span class="sxs-lookup"><span data-stu-id="2197a-114">**EVENT_CONSOLE_CARET** 0x4001</span></span> | <span data-ttu-id="2197a-115">Le signe insertion de la console a été déplacé.</span><span class="sxs-lookup"><span data-stu-id="2197a-115">The console caret has moved.</span></span> <span data-ttu-id="2197a-116">Le paramètre *idObject* est une ou plusieurs des valeurs suivantes : **CONSOLE_CARET_SELECTION** ou **CONSOLE_CARET_VISIBLE** .</span><span class="sxs-lookup"><span data-stu-id="2197a-116">The *idObject* parameter is one or more of the following values: **CONSOLE_CARET_SELECTION** or **CONSOLE_CARET_VISIBLE** .</span></span> <span data-ttu-id="2197a-117">Le paramètre *idChild* est une structure de **[repère](coord-str.md)** qui spécifie la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="2197a-117">The *idChild* parameter is a **[COORD](coord-str.md)** structure that specifies the cursor's current position.</span></span> |
| <span data-ttu-id="2197a-118">**EVENT_CONSOLE_END_APPLICATION** 0x4007</span><span class="sxs-lookup"><span data-stu-id="2197a-118">**EVENT_CONSOLE_END_APPLICATION** 0x4007</span></span> | <span data-ttu-id="2197a-119">Un processus de console s’est terminé.</span><span class="sxs-lookup"><span data-stu-id="2197a-119">A console process has exited.</span></span> <span data-ttu-id="2197a-120">Le paramètre *idObject* contient l’identificateur de processus du processus terminé.</span><span class="sxs-lookup"><span data-stu-id="2197a-120">The *idObject* parameter contains the process identifier of the terminated process.</span></span> |
| <span data-ttu-id="2197a-121">**EVENT_CONSOLE_LAYOUT** 0x4005</span><span class="sxs-lookup"><span data-stu-id="2197a-121">**EVENT_CONSOLE_LAYOUT** 0x4005</span></span> | <span data-ttu-id="2197a-122">La disposition de la console a changé.</span><span class="sxs-lookup"><span data-stu-id="2197a-122">The console layout has changed.</span></span> |
| <span data-ttu-id="2197a-123">**EVENT_CONSOLE_START_APPLICATION** 0x4006</span><span class="sxs-lookup"><span data-stu-id="2197a-123">**EVENT_CONSOLE_START_APPLICATION** 0x4006</span></span> | <span data-ttu-id="2197a-124">Un nouveau processus de console a démarré.</span><span class="sxs-lookup"><span data-stu-id="2197a-124">A new console process has started.</span></span> <span data-ttu-id="2197a-125">Le paramètre *idObject* contient l’identificateur de processus du processus nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="2197a-125">The *idObject* parameter contains the process identifier of the newly created process.</span></span> <span data-ttu-id="2197a-126">Si l’application est une application 16 bits, le paramètre *idChild* est **CONSOLE_APPLICATION_16BIT** et *idObject* est l’identificateur de processus de la session NTVDM associée à la console.</span><span class="sxs-lookup"><span data-stu-id="2197a-126">If the application is a 16-bit application, the *idChild* parameter is **CONSOLE_APPLICATION_16BIT** and *idObject* is the process identifier of the NTVDM session associated with the console.</span></span> |
|<span data-ttu-id="2197a-127">**EVENT_CONSOLE_UPDATE_REGION** 0x4002</span><span class="sxs-lookup"><span data-stu-id="2197a-127">**EVENT_CONSOLE_UPDATE_REGION** 0x4002</span></span> | <span data-ttu-id="2197a-128">Plus d’un caractère a été modifié.</span><span class="sxs-lookup"><span data-stu-id="2197a-128">More than one character has changed.</span></span> <span data-ttu-id="2197a-129">Le paramètre  *idObject* est une structure de **[repère](coord-str.md)** qui spécifie le début de la région modifiée.</span><span class="sxs-lookup"><span data-stu-id="2197a-129">The  *idObject* parameter is a **[COORD](coord-str.md)** structure that specifies the start of the changed region.</span></span> <span data-ttu-id="2197a-130">Le paramètre *idChild* est une structure de **repère** qui spécifie la fin de la région modifiée.</span><span class="sxs-lookup"><span data-stu-id="2197a-130">The *idChild* parameter is a **COORD** structure that specifies the end of the changed region.</span></span> |
|<span data-ttu-id="2197a-131">**EVENT_CONSOLE_UPDATE_SCROLL** 0x4004</span><span class="sxs-lookup"><span data-stu-id="2197a-131">**EVENT_CONSOLE_UPDATE_SCROLL** 0x4004</span></span> | <span data-ttu-id="2197a-132">La console a défilé.</span><span class="sxs-lookup"><span data-stu-id="2197a-132">The console has scrolled.</span></span> <span data-ttu-id="2197a-133">Le paramètre *idObject* est la distance horizontale à laquelle la console a défilé.</span><span class="sxs-lookup"><span data-stu-id="2197a-133">The *idObject* parameter is the horizontal distance the console has scrolled.</span></span> <span data-ttu-id="2197a-134">Le paramètre *idChild* est la distance verticale à laquelle la console a défilé.</span><span class="sxs-lookup"><span data-stu-id="2197a-134">The *idChild* parameter is the vertical distance the console has scrolled.</span></span> |
|<span data-ttu-id="2197a-135">**EVENT_CONSOLE_UPDATE_SIMPLE** 0x4003</span><span class="sxs-lookup"><span data-stu-id="2197a-135">**EVENT_CONSOLE_UPDATE_SIMPLE** 0x4003</span></span> | <span data-ttu-id="2197a-136">Un caractère unique a changé.</span><span class="sxs-lookup"><span data-stu-id="2197a-136">A single character has changed.</span></span> <span data-ttu-id="2197a-137">Le paramètre *idObject* est une structure de **[repère](coord-str.md)** qui spécifie le caractère qui a changé.</span><span class="sxs-lookup"><span data-stu-id="2197a-137">The *idObject* parameter is a **[COORD](coord-str.md)** structure that specifies the character that has changed.</span></span> <span data-ttu-id="2197a-138">Le paramètre *idChild* spécifie le caractère dans le mot de poids faible et les **[attributs de caractère](console-screen-buffers.md#character-attributes)** dans le mot de poids fort.</span><span class="sxs-lookup"><span data-stu-id="2197a-138">The *idChild* parameter specifies the character in the low word and the **[character attributes](console-screen-buffers.md#character-attributes)** in the high word.</span></span> |

## <a name="requirements"></a><span data-ttu-id="2197a-139">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2197a-139">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="2197a-140">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="2197a-140">Minimum supported client</span></span> | <span data-ttu-id="2197a-141">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="2197a-141">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="2197a-142">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="2197a-142">Minimum supported server</span></span> | <span data-ttu-id="2197a-143">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="2197a-143">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="2197a-144">En-tête</span><span class="sxs-lookup"><span data-stu-id="2197a-144">Header</span></span> | <span data-ttu-id="2197a-145">Winuser. h</span><span class="sxs-lookup"><span data-stu-id="2197a-145">Winuser.h</span></span> |
