---
title: WinEvents de la console
description: Les constantes d’événement suivantes sont utilisées dans le paramètre Event de la fonction de rappel WinEventProc. Pour plus d’informations, consultez WinEvents.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
ms.openlocfilehash: ab58df01b3fb29e6efea3ecd0aab145fe2f298c2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059244"
---
# <a name="console-winevents"></a><span data-ttu-id="cb2e2-105">WinEvents de la console</span><span class="sxs-lookup"><span data-stu-id="cb2e2-105">Console WinEvents</span></span>


<span data-ttu-id="cb2e2-106">Les constantes d’événement suivantes sont utilisées dans le paramètre *Event* de la fonction de rappel [*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) .</span><span class="sxs-lookup"><span data-stu-id="cb2e2-106">The following event constants are used in the *event* parameter of the [*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) callback function.</span></span> <span data-ttu-id="cb2e2-107">Pour plus d’informations, consultez [winEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span><span class="sxs-lookup"><span data-stu-id="cb2e2-107">For more information, see [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="cb2e2-108">Constante/valeur</span><span class="sxs-lookup"><span data-stu-id="cb2e2-108">Constant/value</span></span></th>
<th><span data-ttu-id="cb2e2-109">Description</span><span class="sxs-lookup"><span data-stu-id="cb2e2-109">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="cb2e2-110"><span id="EVENT_CONSOLE_CARET"></span><span id="event_console_caret"></span>
<strong>EVENT_CONSOLE_CARET</strong> 0x4001</span><span class="sxs-lookup"><span data-stu-id="cb2e2-110"><span id="EVENT_CONSOLE_CARET"></span><span id="event_console_caret"></span>
<strong>EVENT_CONSOLE_CARET</strong> 0x4001</span></span></td>
<td><p><span data-ttu-id="cb2e2-111">Le signe insertion de la console a été déplacé.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-111">The console caret has moved.</span></span> <span data-ttu-id="cb2e2-112">Le paramètre <em>idObject</em> est une ou plusieurs des valeurs suivantes : <strong>CONSOLE_CARET_SELECTION</strong> ou <strong>CONSOLE_CARET_VISIBLE</strong>.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-112">The <em>idObject</em> parameter is one or more of the following values: <strong>CONSOLE_CARET_SELECTION</strong> or <strong>CONSOLE_CARET_VISIBLE</strong>.</span></span></p>
<p><span data-ttu-id="cb2e2-113">Le paramètre <em>idChild</em> est une structure de <strong><a href="https://docs.microsoft.com/windows/console/coord-str">repère</a></strong> qui spécifie la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-113">The <em>idChild</em> parameter is a <strong><a href="https://docs.microsoft.com/windows/console/coord-str">COORD</a></strong> structure that specifies the cursor's current position.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="cb2e2-114"><span id="EVENT_CONSOLE_END_APPLICATION"></span><span id="event_console_end_application"></span>
<strong>EVENT_CONSOLE_END_APPLICATION</strong> 0x4007</span><span class="sxs-lookup"><span data-stu-id="cb2e2-114"><span id="EVENT_CONSOLE_END_APPLICATION"></span><span id="event_console_end_application"></span>
<strong>EVENT_CONSOLE_END_APPLICATION</strong> 0x4007</span></span></td>
<td><p><span data-ttu-id="cb2e2-115">Un processus de console s’est terminé.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-115">A console process has exited.</span></span> <span data-ttu-id="cb2e2-116">Le paramètre <em>idObject</em> contient l’identificateur de processus du processus terminé.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-116">The <em>idObject</em> parameter contains the process identifier of the terminated process.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="cb2e2-117"><span id="EVENT_CONSOLE_LAYOUT"></span><span id="event_console_layout"></span>
<strong>EVENT_CONSOLE_LAYOUT</strong> 0x4005</span><span class="sxs-lookup"><span data-stu-id="cb2e2-117"><span id="EVENT_CONSOLE_LAYOUT"></span><span id="event_console_layout"></span>
<strong>EVENT_CONSOLE_LAYOUT</strong> 0x4005</span></span></td>
<td><p><span data-ttu-id="cb2e2-118">La disposition de la console a changé.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-118">The console layout has changed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="cb2e2-119"><span id="EVENT_CONSOLE_START_APPLICATION"></span><span id="event_console_start_application"></span>
<strong>EVENT_CONSOLE_START_APPLICATION</strong> 0x4006</span><span class="sxs-lookup"><span data-stu-id="cb2e2-119"><span id="EVENT_CONSOLE_START_APPLICATION"></span><span id="event_console_start_application"></span>
<strong>EVENT_CONSOLE_START_APPLICATION</strong> 0x4006</span></span></td>
<td><p><span data-ttu-id="cb2e2-120">Un nouveau processus de console a démarré.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-120">A new console process has started.</span></span> <span data-ttu-id="cb2e2-121">Le paramètre <em>idObject</em> contient l’identificateur de processus du processus nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-121">The <em>idObject</em> parameter contains the process identifier of the newly created process.</span></span> <span data-ttu-id="cb2e2-122">Si l’application est une application 16 bits, le paramètre <em>idChild</em> est <strong>CONSOLE_APPLICATION_16BIT</strong> et <em>idObject</em> est l’identificateur de processus de la session NTVDM associée à la console.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-122">If the application is a 16-bit application, the <em>idChild</em> parameter is <strong>CONSOLE_APPLICATION_16BIT</strong> and <em>idObject</em> is the process identifier of the NTVDM session associated with the console.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="cb2e2-123"><span id="EVENT_CONSOLE_UPDATE_REGION"></span><span id="event_console_update_region"></span>
<strong>EVENT_CONSOLE_UPDATE_REGION</strong> 0x4002</span><span class="sxs-lookup"><span data-stu-id="cb2e2-123"><span id="EVENT_CONSOLE_UPDATE_REGION"></span><span id="event_console_update_region"></span>
<strong>EVENT_CONSOLE_UPDATE_REGION</strong> 0x4002</span></span></td>
<td><p><span data-ttu-id="cb2e2-124">Plus d’un caractère a été modifié.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-124">More than one character has changed.</span></span> <span data-ttu-id="cb2e2-125">Le paramètre <em>idObject</em> est une structure de <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>repère</strong></a> qui spécifie le début de la région modifiée.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-125">The <em>idObject</em> parameter is a <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>COORD</strong></a> structure that specifies the start of the changed region.</span></span> <span data-ttu-id="cb2e2-126">Le paramètre <em>idChild</em> est une structure de <strong>repère</strong> qui spécifie la fin de la région modifiée.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-126">The <em>idChild</em> parameter is a <strong>COORD</strong> structure that specifies the end of the changed region.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="cb2e2-127"><span id="EVENT_CONSOLE_UPDATE_SCROLL"></span><span id="event_console_update_scroll"></span>
<strong>EVENT_CONSOLE_UPDATE_SCROLL</strong> 0x4004</span><span class="sxs-lookup"><span data-stu-id="cb2e2-127"><span id="EVENT_CONSOLE_UPDATE_SCROLL"></span><span id="event_console_update_scroll"></span>
<strong>EVENT_CONSOLE_UPDATE_SCROLL</strong> 0x4004</span></span></td>
<td><p><span data-ttu-id="cb2e2-128">La console a défilé.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-128">The console has scrolled.</span></span> <span data-ttu-id="cb2e2-129">Le paramètre <em>idObject</em> est la distance horizontale à laquelle la console a défilé.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-129">The <em>idObject</em> parameter is the horizontal distance the console has scrolled.</span></span> <span data-ttu-id="cb2e2-130">Le paramètre <em>idChild</em> est la distance verticale à laquelle la console a défilé.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-130">The <em>idChild</em> parameter is the vertical distance the console has scrolled.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="cb2e2-131"><span id="EVENT_CONSOLE_UPDATE_SIMPLE"></span><span id="event_console_update_simple"></span>
<strong>EVENT_CONSOLE_UPDATE_SIMPLE</strong> 0x4003</span><span class="sxs-lookup"><span data-stu-id="cb2e2-131"><span id="EVENT_CONSOLE_UPDATE_SIMPLE"></span><span id="event_console_update_simple"></span>
<strong>EVENT_CONSOLE_UPDATE_SIMPLE</strong> 0x4003</span></span></td>
<td><p><span data-ttu-id="cb2e2-132">Un caractère unique a changé.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-132">A single character has changed.</span></span> <span data-ttu-id="cb2e2-133">Le paramètre <em>idObject</em> est une structure de <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>repère</strong></a> qui spécifie le caractère qui a changé.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-133">The <em>idObject</em> parameter is a <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>COORD</strong></a> structure that specifies the character that has changed.</span></span> <span data-ttu-id="cb2e2-134">Le paramètre <em>idChild</em> spécifie le caractère dans le mot de poids faible et les <a href="console-screen-buffers.md#_win32_font_attributes" data-raw-source="[character attributes](console-screen-buffers.md#_win32_font_attributes)">attributs de caractère</a> dans le mot de poids fort.</span><span class="sxs-lookup"><span data-stu-id="cb2e2-134">The <em>idChild</em> parameter specifies the character in the low word and the <a href="console-screen-buffers.md#_win32_font_attributes" data-raw-source="[character attributes](console-screen-buffers.md#_win32_font_attributes)">character attributes</a> in the high word.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

<a name="requirements"></a><span data-ttu-id="cb2e2-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cb2e2-135">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="cb2e2-136">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="cb2e2-136">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="cb2e2-137">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="cb2e2-137">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="cb2e2-138">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="cb2e2-138">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="cb2e2-139">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="cb2e2-139">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="cb2e2-140">En-tête</span><span class="sxs-lookup"><span data-stu-id="cb2e2-140">Header</span></span></p></td>
<td><span data-ttu-id="cb2e2-141">Winuser. h</span><span class="sxs-lookup"><span data-stu-id="cb2e2-141">Winuser.h</span></span></td>
</tr>
</tbody>
</table>
