---
title: INPUT_RECORD, structure
description: Consultez les informations de référence sur la structure INPUT_RECORD, qui décrit un événement d’entrée dans la mémoire tampon d’entrée de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4ad86de170c1fef74f133a5d5c51d8de2dea497f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038537"
---
# <a name="input_record-structure"></a><span data-ttu-id="77e90-104">Structure d’enregistrement d’entrée \_</span><span class="sxs-lookup"><span data-stu-id="77e90-104">INPUT\_RECORD structure</span></span>

<span data-ttu-id="77e90-105">Décrit un événement d’entrée dans la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="77e90-105">Describes an input event in the console input buffer.</span></span> <span data-ttu-id="77e90-106">Ces enregistrements peuvent être lus à partir de la mémoire tampon d’entrée à l’aide de la fonction [**ReadConsoleInput**](readconsoleinput.md) ou [**PeekConsoleInput**](peekconsoleinput.md) , ou être écrits dans la mémoire tampon d’entrée à l’aide de la fonction [**WriteConsoleInput**](writeconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="77e90-106">These records can be read from the input buffer by using the [**ReadConsoleInput**](readconsoleinput.md) or [**PeekConsoleInput**](peekconsoleinput.md) function, or written to the input buffer by using the [**WriteConsoleInput**](writeconsoleinput.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="77e90-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77e90-107">Syntax</span></span>

```C
typedef struct _INPUT_RECORD {
  WORD  EventType;
  union {
    KEY_EVENT_RECORD          KeyEvent;
    MOUSE_EVENT_RECORD        MouseEvent;
    WINDOW_BUFFER_SIZE_RECORD WindowBufferSizeEvent;
    MENU_EVENT_RECORD         MenuEvent;
    FOCUS_EVENT_RECORD        FocusEvent;
  } Event;
} INPUT_RECORD;
```

## <a name="members"></a><span data-ttu-id="77e90-108">Membres</span><span class="sxs-lookup"><span data-stu-id="77e90-108">Members</span></span>

<span data-ttu-id="77e90-109">**EventType**</span><span class="sxs-lookup"><span data-stu-id="77e90-109">**EventType**</span></span>  
<span data-ttu-id="77e90-110">Handle du type d’événement d’entrée et de l’enregistrement d’événement stocké dans le membre d' **événement** .</span><span class="sxs-lookup"><span data-stu-id="77e90-110">A handle to the type of input event and the event record stored in the **Event** member.</span></span>

<span data-ttu-id="77e90-111">Ce membre peut être l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="77e90-111">This member can be one of the following values.</span></span>

| <span data-ttu-id="77e90-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="77e90-112">Value</span></span> | <span data-ttu-id="77e90-113">Signification</span><span class="sxs-lookup"><span data-stu-id="77e90-113">Meaning</span></span> |
|-|-|
| <span data-ttu-id="77e90-114">**FOCUS_EVENT** 0x0010</span><span class="sxs-lookup"><span data-stu-id="77e90-114">**FOCUS_EVENT** 0x0010</span></span> | <span data-ttu-id="77e90-115">Le membre d' **événement** contient une structure **[FOCUS_EVENT_RECORD](focus-event-record-str.md)** .</span><span class="sxs-lookup"><span data-stu-id="77e90-115">The **Event** member contains a **[FOCUS_EVENT_RECORD](focus-event-record-str.md)** structure.</span></span> <span data-ttu-id="77e90-116">Ces événements sont utilisés en interne et doivent être ignorés.</span><span class="sxs-lookup"><span data-stu-id="77e90-116">These events are used internally and should be ignored.</span></span> |
| <span data-ttu-id="77e90-117">**KEY_EVENT** 0x0001</span><span class="sxs-lookup"><span data-stu-id="77e90-117">**KEY_EVENT** 0x0001</span></span> | <span data-ttu-id="77e90-118">Le membre d' **événement** contient une structure **[KEY_EVENT_RECORD](key-event-record-str.md)** avec des informations sur un événement de clavier.</span><span class="sxs-lookup"><span data-stu-id="77e90-118">The **Event** member contains a **[KEY_EVENT_RECORD](key-event-record-str.md)** structure with information about a keyboard event.</span></span> |
| <span data-ttu-id="77e90-119">**MENU_EVENT** 0x0008</span><span class="sxs-lookup"><span data-stu-id="77e90-119">**MENU_EVENT** 0x0008</span></span> | <span data-ttu-id="77e90-120">Le membre d' **événement** contient une structure **[MENU_EVENT_RECORD](menu-event-record-str.md)** .</span><span class="sxs-lookup"><span data-stu-id="77e90-120">The **Event** member contains a **[MENU_EVENT_RECORD](menu-event-record-str.md)** structure.</span></span> <span data-ttu-id="77e90-121">Ces événements sont utilisés en interne et doivent être ignorés.</span><span class="sxs-lookup"><span data-stu-id="77e90-121">These events are used internally and should be ignored.</span></span> |
| <span data-ttu-id="77e90-122">**MOUSE_EVENT** 0x0002</span><span class="sxs-lookup"><span data-stu-id="77e90-122">**MOUSE_EVENT** 0x0002</span></span> | <span data-ttu-id="77e90-123">Le membre d' **événement** contient une structure **[MOUSE_EVENT_RECORD](mouse-event-record-str.md)** avec des informations sur un déplacement de la souris ou un événement d’enfoncement du bouton.</span><span class="sxs-lookup"><span data-stu-id="77e90-123">The **Event** member contains a **[MOUSE_EVENT_RECORD](mouse-event-record-str.md)** structure with information about a mouse movement or button press event.</span></span> |
| <span data-ttu-id="77e90-124">**WINDOW_BUFFER_SIZE_EVENT** 0x0004</span><span class="sxs-lookup"><span data-stu-id="77e90-124">**WINDOW_BUFFER_SIZE_EVENT** 0x0004</span></span> | <span data-ttu-id="77e90-125">Le membre d' **événement** contient une structure **[WINDOW_BUFFER_SIZE_RECORD](window-buffer-size-record-str.md)** avec des informations sur la nouvelle taille de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="77e90-125">The **Event** member contains a **[WINDOW_BUFFER_SIZE_RECORD](window-buffer-size-record-str.md)** structure with information about the new size of the console screen buffer.</span></span> |

<span data-ttu-id="77e90-126">**Event**</span><span class="sxs-lookup"><span data-stu-id="77e90-126">**Event**</span></span>  
<span data-ttu-id="77e90-127">Informations d'événement.</span><span class="sxs-lookup"><span data-stu-id="77e90-127">The event information.</span></span> <span data-ttu-id="77e90-128">Le format de ce membre dépend du type d’événement spécifié par le membre **eventType** .</span><span class="sxs-lookup"><span data-stu-id="77e90-128">The format of this member depends on the event type specified by the **EventType** member.</span></span>

## <a name="examples"></a><span data-ttu-id="77e90-129">Exemples</span><span class="sxs-lookup"><span data-stu-id="77e90-129">Examples</span></span>

<span data-ttu-id="77e90-130">Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="77e90-130">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="77e90-131">Spécifications</span><span class="sxs-lookup"><span data-stu-id="77e90-131">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="77e90-132">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="77e90-132">Minimum supported client</span></span> | <span data-ttu-id="77e90-133">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="77e90-133">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="77e90-134">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="77e90-134">Minimum supported server</span></span> | <span data-ttu-id="77e90-135">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="77e90-135">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="77e90-136">En-tête</span><span class="sxs-lookup"><span data-stu-id="77e90-136">Header</span></span> | <span data-ttu-id="77e90-137">WinConTypes. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="77e90-137">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="77e90-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77e90-138">See also</span></span>

[<span data-ttu-id="77e90-139">**FOCUS \_ , \_ enregistrement d’événement**</span><span class="sxs-lookup"><span data-stu-id="77e90-139">**FOCUS\_EVENT\_RECORD**</span></span>](focus-event-record-str.md)

[<span data-ttu-id="77e90-140">**\_enregistrement d’événement clé \_**</span><span class="sxs-lookup"><span data-stu-id="77e90-140">**KEY\_EVENT\_RECORD**</span></span>](key-event-record-str.md)

[<span data-ttu-id="77e90-141">**\_enregistrement d’événement de menu \_**</span><span class="sxs-lookup"><span data-stu-id="77e90-141">**MENU\_EVENT\_RECORD**</span></span>](menu-event-record-str.md)

[<span data-ttu-id="77e90-142">**\_enregistrement d’événement de souris \_**</span><span class="sxs-lookup"><span data-stu-id="77e90-142">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="77e90-143">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="77e90-143">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="77e90-144">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="77e90-144">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="77e90-145">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="77e90-145">**WriteConsoleInput**</span></span>](writeconsoleinput.md)
