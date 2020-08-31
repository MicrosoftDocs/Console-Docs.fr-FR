---
title: Structure INPUT_RECORD
description: Consultez les informations de référence sur la structure INPUT_RECORD, qui décrit un événement d’entrée dans la mémoire tampon d’entrée de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- wincontypes/INPUT_RECORD
- wincon/INPUT_RECORD
- INPUT_RECORD
- wincontypes/PINPUT_RECORD
- wincon/PINPUT_RECORD
- PINPUT_RECORD
MS-HAID:
- '\_win32\_input\_record\_str'
- base.input\_record\_str
- consoles.input\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a46ba7fd-097a-455d-96ac-13aa01e11dc1
topic_type:
- apiref
api_name:
- INPUT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 5d532b5a009681e650991fd083f7d6ab932a05da
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059485"
---
# <a name="input_record-structure"></a><span data-ttu-id="a2d87-104">Structure d’enregistrement d’entrée \_</span><span class="sxs-lookup"><span data-stu-id="a2d87-104">INPUT\_RECORD structure</span></span>


<span data-ttu-id="a2d87-105">Décrit un événement d’entrée dans la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="a2d87-105">Describes an input event in the console input buffer.</span></span> <span data-ttu-id="a2d87-106">Ces enregistrements peuvent être lus à partir de la mémoire tampon d’entrée à l’aide de la fonction [**ReadConsoleInput**](readconsoleinput.md) ou [**PeekConsoleInput**](peekconsoleinput.md) , ou être écrits dans la mémoire tampon d’entrée à l’aide de la fonction [**WriteConsoleInput**](writeconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="a2d87-106">These records can be read from the input buffer by using the [**ReadConsoleInput**](readconsoleinput.md) or [**PeekConsoleInput**](peekconsoleinput.md) function, or written to the input buffer by using the [**WriteConsoleInput**](writeconsoleinput.md) function.</span></span>

<a name="syntax"></a><span data-ttu-id="a2d87-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2d87-107">Syntax</span></span>
------

```C
typedef struct _INPUT_RECORD {
  WORD  EventType;
  union {
    KEY_EVENT_RECORD          KeyEvent;
    MOUSE_EVENT_RECORD        MouseEvent;
    WINDOW_BUFFER_SIZE_RECORD WindowBufferSizeEvent;
    MENU_EVENT_RECORD         MenuEvent;
    FOCUS_EVENT_RECORD        FocusEvent;
  } Event;
} INPUT_RECORD;
```

<a name="members"></a><span data-ttu-id="a2d87-108">Membres</span><span class="sxs-lookup"><span data-stu-id="a2d87-108">Members</span></span>
-------

<span data-ttu-id="a2d87-109">**EventType**</span><span class="sxs-lookup"><span data-stu-id="a2d87-109">**EventType**</span></span>  
<span data-ttu-id="a2d87-110">Handle du type d’événement d’entrée et de l’enregistrement d’événement stocké dans le membre d' **événement** .</span><span class="sxs-lookup"><span data-stu-id="a2d87-110">A handle to the type of input event and the event record stored in the **Event** member.</span></span>

<span data-ttu-id="a2d87-111">Ce membre peut être l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="a2d87-111">This member can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="a2d87-112">Value</span><span class="sxs-lookup"><span data-stu-id="a2d87-112">Value</span></span></th>
<th><span data-ttu-id="a2d87-113">Signification</span><span class="sxs-lookup"><span data-stu-id="a2d87-113">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="a2d87-114"><span id="FOCUS_EVENT"></span><span id="focus_event"></span>
<strong>FOCUS_EVENT</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="a2d87-114"><span id="FOCUS_EVENT"></span><span id="focus_event"></span>
<strong>FOCUS_EVENT</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="a2d87-115">Le membre d' <strong>événement</strong> contient une structure <a href="focus-event-record-str.md" data-raw-source="[&lt;strong&gt;FOCUS_EVENT_RECORD&lt;/strong&gt;](focus-event-record-str.md)"><strong>FOCUS_EVENT_RECORD</strong></a> .</span><span class="sxs-lookup"><span data-stu-id="a2d87-115">The <strong>Event</strong> member contains a <a href="focus-event-record-str.md" data-raw-source="[&lt;strong&gt;FOCUS_EVENT_RECORD&lt;/strong&gt;](focus-event-record-str.md)"><strong>FOCUS_EVENT_RECORD</strong></a> structure.</span></span> <span data-ttu-id="a2d87-116">Ces événements sont utilisés en interne et doivent être ignorés.</span><span class="sxs-lookup"><span data-stu-id="a2d87-116">These events are used internally and should be ignored.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="a2d87-117"><span id="KEY_EVENT"></span><span id="key_event"></span>
<strong>KEY_EVENT</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="a2d87-117"><span id="KEY_EVENT"></span><span id="key_event"></span>
<strong>KEY_EVENT</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="a2d87-118">Le membre d' <strong>événement</strong> contient une structure <a href="key-event-record-str.md" data-raw-source="[&lt;strong&gt;KEY_EVENT_RECORD&lt;/strong&gt;](key-event-record-str.md)"><strong>KEY_EVENT_RECORD</strong></a> avec des informations sur un événement de clavier.</span><span class="sxs-lookup"><span data-stu-id="a2d87-118">The <strong>Event</strong> member contains a <a href="key-event-record-str.md" data-raw-source="[&lt;strong&gt;KEY_EVENT_RECORD&lt;/strong&gt;](key-event-record-str.md)"><strong>KEY_EVENT_RECORD</strong></a> structure with information about a keyboard event.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="a2d87-119"><span id="MENU_EVENT"></span><span id="menu_event"></span>
<strong>MENU_EVENT</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="a2d87-119"><span id="MENU_EVENT"></span><span id="menu_event"></span>
<strong>MENU_EVENT</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="a2d87-120">Le membre d' <strong>événement</strong> contient une structure <a href="menu-event-record-str.md" data-raw-source="[&lt;strong&gt;MENU_EVENT_RECORD&lt;/strong&gt;](menu-event-record-str.md)"><strong>MENU_EVENT_RECORD</strong></a> .</span><span class="sxs-lookup"><span data-stu-id="a2d87-120">The <strong>Event</strong> member contains a <a href="menu-event-record-str.md" data-raw-source="[&lt;strong&gt;MENU_EVENT_RECORD&lt;/strong&gt;](menu-event-record-str.md)"><strong>MENU_EVENT_RECORD</strong></a> structure.</span></span> <span data-ttu-id="a2d87-121">Ces événements sont utilisés en interne et doivent être ignorés.</span><span class="sxs-lookup"><span data-stu-id="a2d87-121">These events are used internally and should be ignored.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="a2d87-122"><span id="MOUSE_EVENT"></span><span id="mouse_event"></span>
<strong>MOUSE_EVENT</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="a2d87-122"><span id="MOUSE_EVENT"></span><span id="mouse_event"></span>
<strong>MOUSE_EVENT</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="a2d87-123">Le membre d' <strong>événement</strong> contient une structure <a href="mouse-event-record-str.md" data-raw-source="[&lt;strong&gt;MOUSE_EVENT_RECORD&lt;/strong&gt;](mouse-event-record-str.md)"><strong>MOUSE_EVENT_RECORD</strong></a> avec des informations sur un déplacement de la souris ou un événement d’enfoncement du bouton.</span><span class="sxs-lookup"><span data-stu-id="a2d87-123">The <strong>Event</strong> member contains a <a href="mouse-event-record-str.md" data-raw-source="[&lt;strong&gt;MOUSE_EVENT_RECORD&lt;/strong&gt;](mouse-event-record-str.md)"><strong>MOUSE_EVENT_RECORD</strong></a> structure with information about a mouse movement or button press event.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="a2d87-124"><span id="WINDOW_BUFFER_SIZE_EVENT"></span><span id="window_buffer_size_event"></span>
<strong>WINDOW_BUFFER_SIZE_EVENT</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="a2d87-124"><span id="WINDOW_BUFFER_SIZE_EVENT"></span><span id="window_buffer_size_event"></span>
<strong>WINDOW_BUFFER_SIZE_EVENT</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="a2d87-125">Le membre d' <strong>événement</strong> contient une structure <a href="window-buffer-size-record-str.md" data-raw-source="[&lt;strong&gt;WINDOW_BUFFER_SIZE_RECORD&lt;/strong&gt;](window-buffer-size-record-str.md)"><strong>WINDOW_BUFFER_SIZE_RECORD</strong></a> avec des informations sur la nouvelle taille de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="a2d87-125">The <strong>Event</strong> member contains a <a href="window-buffer-size-record-str.md" data-raw-source="[&lt;strong&gt;WINDOW_BUFFER_SIZE_RECORD&lt;/strong&gt;](window-buffer-size-record-str.md)"><strong>WINDOW_BUFFER_SIZE_RECORD</strong></a> structure with information about the new size of the console screen buffer.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="a2d87-126">**Event**</span><span class="sxs-lookup"><span data-stu-id="a2d87-126">**Event**</span></span>  
<span data-ttu-id="a2d87-127">Informations d'événement.</span><span class="sxs-lookup"><span data-stu-id="a2d87-127">The event information.</span></span> <span data-ttu-id="a2d87-128">Le format de ce membre dépend du type d’événement spécifié par le membre **eventType** .</span><span class="sxs-lookup"><span data-stu-id="a2d87-128">The format of this member depends on the event type specified by the **EventType** member.</span></span>

<a name="examples"></a><span data-ttu-id="a2d87-129">Exemples</span><span class="sxs-lookup"><span data-stu-id="a2d87-129">Examples</span></span>
--------

<span data-ttu-id="a2d87-130">Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="a2d87-130">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="a2d87-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a2d87-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="a2d87-132">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="a2d87-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="a2d87-133">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="a2d87-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a2d87-134">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="a2d87-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="a2d87-135">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="a2d87-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a2d87-136">En-tête</span><span class="sxs-lookup"><span data-stu-id="a2d87-136">Header</span></span></p></td>
<td><span data-ttu-id="a2d87-137">WinConTypes. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="a2d87-137">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="a2d87-138"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2d87-138"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="a2d87-139">**FOCUS \_ , \_ enregistrement d’événement**</span><span class="sxs-lookup"><span data-stu-id="a2d87-139">**FOCUS\_EVENT\_RECORD**</span></span>](focus-event-record-str.md)

[<span data-ttu-id="a2d87-140">**\_enregistrement d’événement clé \_**</span><span class="sxs-lookup"><span data-stu-id="a2d87-140">**KEY\_EVENT\_RECORD**</span></span>](key-event-record-str.md)

[<span data-ttu-id="a2d87-141">**\_enregistrement d’événement de menu \_**</span><span class="sxs-lookup"><span data-stu-id="a2d87-141">**MENU\_EVENT\_RECORD**</span></span>](menu-event-record-str.md)

[<span data-ttu-id="a2d87-142">**\_enregistrement d’événement de souris \_**</span><span class="sxs-lookup"><span data-stu-id="a2d87-142">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="a2d87-143">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="a2d87-143">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="a2d87-144">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="a2d87-144">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="a2d87-145">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="a2d87-145">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 




