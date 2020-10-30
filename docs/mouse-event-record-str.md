---
title: MOUSE_EVENT_RECORD, structure
description: Consultez les informations de référence sur la structure MOUSE_EVENT_RECORD, qui décrit un événement d’entrée de souris dans une structure de INPUT_RECORD de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- wincontypes/MOUSE_EVENT_RECORD
- wincon/MOUSE_EVENT_RECORD
- MOUSE_EVENT_RECORD
- wincontypes/PMOUSE_EVENT_RECORD
- wincon/PMOUSE_EVENT_RECORD
- PMOUSE_EVENT_RECORD
MS-HAID:
- '\_win32\_mouse\_event\_record\_str'
- base.mouse\_event\_record\_str
- consoles.mouse\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ea54c6-8872-4111-8d72-1377409b9247
topic_type:
- apiref
api_name:
- MOUSE_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: c10047d1386f3bce1546ee21bacdc81b8fb7bb55
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038517"
---
# <a name="mouse_event_record-structure"></a><span data-ttu-id="00cf9-104">Structure d’enregistrement d' \_ événement de souris \_</span><span class="sxs-lookup"><span data-stu-id="00cf9-104">MOUSE\_EVENT\_RECORD structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="00cf9-105">Décrit un événement d’entrée de souris dans une structure [**d' \_ enregistrement d’entrée**](input-record-str.md) de console.</span><span class="sxs-lookup"><span data-stu-id="00cf9-105">Describes a mouse input event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="00cf9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00cf9-106">Syntax</span></span>

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

## <a name="members"></a><span data-ttu-id="00cf9-107">Membres</span><span class="sxs-lookup"><span data-stu-id="00cf9-107">Members</span></span>

<span data-ttu-id="00cf9-108">**dwMousePosition**</span><span class="sxs-lookup"><span data-stu-id="00cf9-108">**dwMousePosition**</span></span>  
<span data-ttu-id="00cf9-109">Structure de [**repère**](coord-str.md) qui contient l’emplacement du curseur, en termes de coordonnées des cellules de caractères de la mémoire tampon de l’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="00cf9-109">A [**COORD**](coord-str.md) structure that contains the location of the cursor, in terms of the console screen buffer's character-cell coordinates.</span></span>

<span data-ttu-id="00cf9-110">**dwButtonState**</span><span class="sxs-lookup"><span data-stu-id="00cf9-110">**dwButtonState**</span></span>  
<span data-ttu-id="00cf9-111">État des boutons de la souris.</span><span class="sxs-lookup"><span data-stu-id="00cf9-111">The status of the mouse buttons.</span></span> <span data-ttu-id="00cf9-112">Le bit le moins significatif correspond au bouton le plus à gauche de la souris.</span><span class="sxs-lookup"><span data-stu-id="00cf9-112">The least significant bit corresponds to the leftmost mouse button.</span></span> <span data-ttu-id="00cf9-113">Le bit le moins significatif suivant correspond au bouton le plus à droite de la souris.</span><span class="sxs-lookup"><span data-stu-id="00cf9-113">The next least significant bit corresponds to the rightmost mouse button.</span></span> <span data-ttu-id="00cf9-114">Le bit suivant indique le bouton de la souris situé à l’extrême gauche.</span><span class="sxs-lookup"><span data-stu-id="00cf9-114">The next bit indicates the next-to-leftmost mouse button.</span></span> <span data-ttu-id="00cf9-115">Les bits correspondent ensuite de gauche à droite aux boutons de la souris.</span><span class="sxs-lookup"><span data-stu-id="00cf9-115">The bits then correspond left to right to the mouse buttons.</span></span> <span data-ttu-id="00cf9-116">Un bit est 1 si le bouton a été enfoncé.</span><span class="sxs-lookup"><span data-stu-id="00cf9-116">A bit is 1 if the button was pressed.</span></span>

<span data-ttu-id="00cf9-117">Les constantes suivantes sont définies pour les cinq premiers boutons de la souris.</span><span class="sxs-lookup"><span data-stu-id="00cf9-117">The following constants are defined for the first five mouse buttons.</span></span>

| <span data-ttu-id="00cf9-118">Valeur</span><span class="sxs-lookup"><span data-stu-id="00cf9-118">Value</span></span> | <span data-ttu-id="00cf9-119">Signification</span><span class="sxs-lookup"><span data-stu-id="00cf9-119">Meaning</span></span> |
|-|-|
| <span data-ttu-id="00cf9-120">**FROM_LEFT_1ST_BUTTON_PRESSED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="00cf9-120">**FROM_LEFT_1ST_BUTTON_PRESSED** 0x0001</span></span> | <span data-ttu-id="00cf9-121">Le bouton gauche de la souris.</span><span class="sxs-lookup"><span data-stu-id="00cf9-121">The leftmost mouse button.</span></span> |
| <span data-ttu-id="00cf9-122">**FROM_LEFT_2ND_BUTTON_PRESSED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="00cf9-122">**FROM_LEFT_2ND_BUTTON_PRESSED** 0x0004</span></span> | <span data-ttu-id="00cf9-123">Le deuxième bouton de la gauche.</span><span class="sxs-lookup"><span data-stu-id="00cf9-123">The second button fom the left.</span></span> |
| <span data-ttu-id="00cf9-124">**FROM_LEFT_3RD_BUTTON_PRESSED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="00cf9-124">**FROM_LEFT_3RD_BUTTON_PRESSED** 0x0008</span></span> | <span data-ttu-id="00cf9-125">Troisième bouton à partir de la gauche.</span><span class="sxs-lookup"><span data-stu-id="00cf9-125">The third button from the left.</span></span> |
| <span data-ttu-id="00cf9-126">**FROM_LEFT_4TH_BUTTON_PRESSED** 0x0010</span><span class="sxs-lookup"><span data-stu-id="00cf9-126">**FROM_LEFT_4TH_BUTTON_PRESSED** 0x0010</span></span> | <span data-ttu-id="00cf9-127">Quatrième bouton à partir de la gauche.</span><span class="sxs-lookup"><span data-stu-id="00cf9-127">The fourth button from the left.</span></span> |
| <span data-ttu-id="00cf9-128">**RIGHTMOST_BUTTON_PRESSED** 0x0002</span><span class="sxs-lookup"><span data-stu-id="00cf9-128">**RIGHTMOST_BUTTON_PRESSED** 0x0002</span></span> | <span data-ttu-id="00cf9-129">Bouton de la souris le plus à droite.</span><span class="sxs-lookup"><span data-stu-id="00cf9-129">The rightmost mouse button.</span></span> |

<span data-ttu-id="00cf9-130">**dwControlKeyState**</span><span class="sxs-lookup"><span data-stu-id="00cf9-130">**dwControlKeyState**</span></span>  
<span data-ttu-id="00cf9-131">État des touches de contrôle.</span><span class="sxs-lookup"><span data-stu-id="00cf9-131">The state of the control keys.</span></span> <span data-ttu-id="00cf9-132">Ce membre peut être une ou plusieurs des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="00cf9-132">This member can be one or more of the following values.</span></span>

| <span data-ttu-id="00cf9-133">Valeur</span><span class="sxs-lookup"><span data-stu-id="00cf9-133">Value</span></span> | <span data-ttu-id="00cf9-134">Signification</span><span class="sxs-lookup"><span data-stu-id="00cf9-134">Meaning</span></span> |
|-|-|
| <span data-ttu-id="00cf9-135">**CAPSLOCK_ON** 0x0080</span><span class="sxs-lookup"><span data-stu-id="00cf9-135">**CAPSLOCK_ON** 0x0080</span></span> | <span data-ttu-id="00cf9-136">Le voyant Verr. MAJ est activé.</span><span class="sxs-lookup"><span data-stu-id="00cf9-136">The CAPS LOCK light is on.</span></span> |
| <span data-ttu-id="00cf9-137">**ENHANCED_KEY** 0x0100</span><span class="sxs-lookup"><span data-stu-id="00cf9-137">**ENHANCED_KEY** 0x0100</span></span> | <span data-ttu-id="00cf9-138">La clé est améliorée.</span><span class="sxs-lookup"><span data-stu-id="00cf9-138">The key is enhanced.</span></span> <span data-ttu-id="00cf9-139">Consultez la [section Notes](key-event-record-str.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="00cf9-139">See [remarks](key-event-record-str.md#remarks).</span></span> |
| <span data-ttu-id="00cf9-140">**LEFT_ALT_PRESSED** 0x0002</span><span class="sxs-lookup"><span data-stu-id="00cf9-140">**LEFT_ALT_PRESSED** 0x0002</span></span> | <span data-ttu-id="00cf9-141">La touche ALT de gauche est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="00cf9-141">The left ALT key is pressed.</span></span> |
| <span data-ttu-id="00cf9-142">**LEFT_CTRL_PRESSED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="00cf9-142">**LEFT_CTRL_PRESSED** 0x0008</span></span> | <span data-ttu-id="00cf9-143">La touche CTRL de gauche est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="00cf9-143">The left CTRL key is pressed.</span></span> |
| <span data-ttu-id="00cf9-144">**NUMLOCK_ON** 0x0020</span><span class="sxs-lookup"><span data-stu-id="00cf9-144">**NUMLOCK_ON** 0x0020</span></span> | <span data-ttu-id="00cf9-145">La diode Verr. NUM est activée.</span><span class="sxs-lookup"><span data-stu-id="00cf9-145">The NUM LOCK light is on.</span></span> |
| <span data-ttu-id="00cf9-146">**RIGHT_ALT_PRESSED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="00cf9-146">**RIGHT_ALT_PRESSED** 0x0001</span></span> | <span data-ttu-id="00cf9-147">La touche ALT de droite est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="00cf9-147">The right ALT key is pressed.</span></span> |
| <span data-ttu-id="00cf9-148">**RIGHT_CTRL_PRESSED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="00cf9-148">**RIGHT_CTRL_PRESSED** 0x0004</span></span> | <span data-ttu-id="00cf9-149">La touche CTRL de droite est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="00cf9-149">The right CTRL key is pressed.</span></span> |
| <span data-ttu-id="00cf9-150">**SCROLLLOCK_ON** 0x0040</span><span class="sxs-lookup"><span data-stu-id="00cf9-150">**SCROLLLOCK_ON** 0x0040</span></span> | <span data-ttu-id="00cf9-151">Le voyant du verrou de défilement est activé.</span><span class="sxs-lookup"><span data-stu-id="00cf9-151">The SCROLL LOCK light is on.</span></span> |
| <span data-ttu-id="00cf9-152">**SHIFT_PRESSED** 0x0010</span><span class="sxs-lookup"><span data-stu-id="00cf9-152">**SHIFT_PRESSED** 0x0010</span></span> | <span data-ttu-id="00cf9-153">La touche Maj est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="00cf9-153">The SHIFT key is pressed.</span></span> |

<span data-ttu-id="00cf9-154">**dwEventFlags**</span><span class="sxs-lookup"><span data-stu-id="00cf9-154">**dwEventFlags**</span></span>  
<span data-ttu-id="00cf9-155">Type d’événement de souris.</span><span class="sxs-lookup"><span data-stu-id="00cf9-155">The type of mouse event.</span></span> <span data-ttu-id="00cf9-156">Si cette valeur est égale à zéro, elle indique qu’un bouton de la souris est enfoncé ou relâché.</span><span class="sxs-lookup"><span data-stu-id="00cf9-156">If this value is zero, it indicates a mouse button being pressed or released.</span></span> <span data-ttu-id="00cf9-157">Dans le cas contraire, ce membre est l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="00cf9-157">Otherwise, this member is one of the following values.</span></span>

| <span data-ttu-id="00cf9-158">Valeur</span><span class="sxs-lookup"><span data-stu-id="00cf9-158">Value</span></span> | <span data-ttu-id="00cf9-159">Signification</span><span class="sxs-lookup"><span data-stu-id="00cf9-159">Meaning</span></span> |
|-|-|
| <span data-ttu-id="00cf9-160">**DOUBLE_CLICK** 0x0002</span><span class="sxs-lookup"><span data-stu-id="00cf9-160">**DOUBLE_CLICK** 0x0002</span></span> | <span data-ttu-id="00cf9-161">Le deuxième clic (appuyez sur le bouton) d’un double-clic s’est produit.</span><span class="sxs-lookup"><span data-stu-id="00cf9-161">The second click (button press) of a double-click occurred.</span></span> <span data-ttu-id="00cf9-162">Le premier clic est retourné en tant qu’événement de bouton-pression standard.</span><span class="sxs-lookup"><span data-stu-id="00cf9-162">The first click is returned as a regular button-press event.</span></span> |
| <span data-ttu-id="00cf9-163">**MOUSE_HWHEELED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="00cf9-163">**MOUSE_HWHEELED** 0x0008</span></span> | <span data-ttu-id="00cf9-164">La roulette horizontale de la souris a été déplacée.</span><span class="sxs-lookup"><span data-stu-id="00cf9-164">The horizontal mouse wheel was moved.</span></span><br /><br /><span data-ttu-id="00cf9-165">Si le mot de poids fort du membre **dwButtonState** contient une valeur positive, la roulette a été pivotée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="00cf9-165">If the high word of the **dwButtonState** member contains a positive value, the wheel was rotated to the right.</span></span> <span data-ttu-id="00cf9-166">Dans le cas contraire, la roulette a été pivotée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="00cf9-166">Otherwise, the wheel was rotated to the left.</span></span> |
| <span data-ttu-id="00cf9-167">**MOUSE_MOVED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="00cf9-167">**MOUSE_MOVED** 0x0001</span></span> | <span data-ttu-id="00cf9-168">Une modification de la position de la souris s’est produite.</span><span class="sxs-lookup"><span data-stu-id="00cf9-168">A change in mouse position occurred.</span></span> |
| <span data-ttu-id="00cf9-169">**MOUSE_WHEELED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="00cf9-169">**MOUSE_WHEELED** 0x0004</span></span> | <span data-ttu-id="00cf9-170">La roulette verticale de la souris a été déplacée.</span><span class="sxs-lookup"><span data-stu-id="00cf9-170">The vertical mouse wheel was moved.</span></span><br /><br /><span data-ttu-id="00cf9-171">Si le mot de poids fort du membre **dwButtonState** contient une valeur positive, la roulette a été pivotée vers l’avant, en dehors de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="00cf9-171">If the high word of the **dwButtonState** member contains a positive value, the wheel was rotated forward, away from the user.</span></span> <span data-ttu-id="00cf9-172">Dans le cas contraire, la roulette a été tournée vers l’arrière de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="00cf9-172">Otherwise, the wheel was rotated backward, toward the user.</span></span> |

## <a name="remarks"></a><span data-ttu-id="00cf9-173">Remarques</span><span class="sxs-lookup"><span data-stu-id="00cf9-173">Remarks</span></span>

<span data-ttu-id="00cf9-174">Les événements de souris sont placés dans la mémoire tampon d’entrée lorsque la console est en mode souris ( **activer l' \_ \_ entrée de la souris** ).</span><span class="sxs-lookup"><span data-stu-id="00cf9-174">Mouse events are placed in the input buffer when the console is in mouse mode ( **ENABLE\_MOUSE\_INPUT** ).</span></span>

<span data-ttu-id="00cf9-175">Les événements de souris sont générés chaque fois que l’utilisateur déplace la souris, ou appuie sur ou relâche l’un des boutons de la souris.</span><span class="sxs-lookup"><span data-stu-id="00cf9-175">Mouse events are generated whenever the user moves the mouse, or presses or releases one of the mouse buttons.</span></span> <span data-ttu-id="00cf9-176">Les événements de souris sont placés dans la mémoire tampon d’entrée d’une console uniquement lorsque le groupe de la console a le focus clavier et que le curseur se trouve dans les limites de la fenêtre de la console.</span><span class="sxs-lookup"><span data-stu-id="00cf9-176">Mouse events are placed in a console's input buffer only when the console group has the keyboard focus and the cursor is within the borders of the console's window.</span></span>

## <a name="examples"></a><span data-ttu-id="00cf9-177">Exemples</span><span class="sxs-lookup"><span data-stu-id="00cf9-177">Examples</span></span>

<span data-ttu-id="00cf9-178">Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="00cf9-178">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="00cf9-179">Spécifications</span><span class="sxs-lookup"><span data-stu-id="00cf9-179">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="00cf9-180">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="00cf9-180">Minimum supported client</span></span> | <span data-ttu-id="00cf9-181">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="00cf9-181">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="00cf9-182">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="00cf9-182">Minimum supported server</span></span> | <span data-ttu-id="00cf9-183">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="00cf9-183">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="00cf9-184">En-tête</span><span class="sxs-lookup"><span data-stu-id="00cf9-184">Header</span></span> | <span data-ttu-id="00cf9-185">WinConTypes. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="00cf9-185">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="00cf9-186">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00cf9-186">See also</span></span>

[<span data-ttu-id="00cf9-187">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="00cf9-187">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="00cf9-188">**enregistrement d’entrée \_**</span><span class="sxs-lookup"><span data-stu-id="00cf9-188">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="00cf9-189">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="00cf9-189">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="00cf9-190">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="00cf9-190">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="00cf9-191">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="00cf9-191">**WriteConsoleInput**</span></span>](writeconsoleinput.md)
