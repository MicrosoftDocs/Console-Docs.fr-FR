---
title: Structure MOUSE_EVENT_RECORD
description: Consultez les informations de référence sur la structure MOUSE_EVENT_RECORD, qui décrit un événement d’entrée de souris dans une structure de INPUT_RECORD de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: a3e95e9d35cdf2af2ec6836021dd8819323a4790
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059061"
---
# <a name="mouse_event_record-structure"></a><span data-ttu-id="635dd-104">Structure d’enregistrement d' \_ événement de souris \_</span><span class="sxs-lookup"><span data-stu-id="635dd-104">MOUSE\_EVENT\_RECORD structure</span></span>


<span data-ttu-id="635dd-105">Décrit un événement d’entrée de souris dans une structure [**d' \_ enregistrement d’entrée**](input-record-str.md) de console.</span><span class="sxs-lookup"><span data-stu-id="635dd-105">Describes a mouse input event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span>

<a name="syntax"></a><span data-ttu-id="635dd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="635dd-106">Syntax</span></span>
------

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

<a name="members"></a><span data-ttu-id="635dd-107">Membres</span><span class="sxs-lookup"><span data-stu-id="635dd-107">Members</span></span>
-------

<span data-ttu-id="635dd-108">**dwMousePosition**</span><span class="sxs-lookup"><span data-stu-id="635dd-108">**dwMousePosition**</span></span>  
<span data-ttu-id="635dd-109">Structure de [**repère**](coord-str.md) qui contient l’emplacement du curseur, en termes de coordonnées des cellules de caractères de la mémoire tampon de l’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="635dd-109">A [**COORD**](coord-str.md) structure that contains the location of the cursor, in terms of the console screen buffer's character-cell coordinates.</span></span>

<span data-ttu-id="635dd-110">**dwButtonState**</span><span class="sxs-lookup"><span data-stu-id="635dd-110">**dwButtonState**</span></span>  
<span data-ttu-id="635dd-111">État des boutons de la souris.</span><span class="sxs-lookup"><span data-stu-id="635dd-111">The status of the mouse buttons.</span></span> <span data-ttu-id="635dd-112">Le bit le moins significatif correspond au bouton le plus à gauche de la souris.</span><span class="sxs-lookup"><span data-stu-id="635dd-112">The least significant bit corresponds to the leftmost mouse button.</span></span> <span data-ttu-id="635dd-113">Le bit le moins significatif suivant correspond au bouton le plus à droite de la souris.</span><span class="sxs-lookup"><span data-stu-id="635dd-113">The next least significant bit corresponds to the rightmost mouse button.</span></span> <span data-ttu-id="635dd-114">Le bit suivant indique le bouton de la souris situé à l’extrême gauche.</span><span class="sxs-lookup"><span data-stu-id="635dd-114">The next bit indicates the next-to-leftmost mouse button.</span></span> <span data-ttu-id="635dd-115">Les bits correspondent ensuite de gauche à droite aux boutons de la souris.</span><span class="sxs-lookup"><span data-stu-id="635dd-115">The bits then correspond left to right to the mouse buttons.</span></span> <span data-ttu-id="635dd-116">Un bit est 1 si le bouton a été enfoncé.</span><span class="sxs-lookup"><span data-stu-id="635dd-116">A bit is 1 if the button was pressed.</span></span>

<span data-ttu-id="635dd-117">Les constantes suivantes sont définies pour les cinq premiers boutons de la souris.</span><span class="sxs-lookup"><span data-stu-id="635dd-117">The following constants are defined for the first five mouse buttons.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="635dd-118">Value</span><span class="sxs-lookup"><span data-stu-id="635dd-118">Value</span></span></th>
<th><span data-ttu-id="635dd-119">Signification</span><span class="sxs-lookup"><span data-stu-id="635dd-119">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="635dd-120"><span id="FROM_LEFT_1ST_BUTTON_PRESSED"></span><span id="from_left_1st_button_pressed"></span>
<strong>FROM_LEFT_1ST_BUTTON_PRESSED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="635dd-120"><span id="FROM_LEFT_1ST_BUTTON_PRESSED"></span><span id="from_left_1st_button_pressed"></span>
<strong>FROM_LEFT_1ST_BUTTON_PRESSED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="635dd-121">Le bouton gauche de la souris.</span><span class="sxs-lookup"><span data-stu-id="635dd-121">The leftmost mouse button.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="635dd-122"><span id="FROM_LEFT_2ND_BUTTON_PRESSED"></span><span id="from_left_2nd_button_pressed"></span>
<strong>FROM_LEFT_2ND_BUTTON_PRESSED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="635dd-122"><span id="FROM_LEFT_2ND_BUTTON_PRESSED"></span><span id="from_left_2nd_button_pressed"></span>
<strong>FROM_LEFT_2ND_BUTTON_PRESSED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="635dd-123">Deuxième bouton à partir de la gauche.</span><span class="sxs-lookup"><span data-stu-id="635dd-123">The second button from the left.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="635dd-124"><span id="FROM_LEFT_3RD_BUTTON_PRESSED"></span><span id="from_left_3rd_button_pressed"></span>
<strong>FROM_LEFT_3RD_BUTTON_PRESSED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="635dd-124"><span id="FROM_LEFT_3RD_BUTTON_PRESSED"></span><span id="from_left_3rd_button_pressed"></span>
<strong>FROM_LEFT_3RD_BUTTON_PRESSED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="635dd-125">Troisième bouton à partir de la gauche.</span><span class="sxs-lookup"><span data-stu-id="635dd-125">The third button from the left.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="635dd-126"><span id="FROM_LEFT_4TH_BUTTON_PRESSED"></span><span id="from_left_4th_button_pressed"></span>
<strong>FROM_LEFT_4TH_BUTTON_PRESSED</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="635dd-126"><span id="FROM_LEFT_4TH_BUTTON_PRESSED"></span><span id="from_left_4th_button_pressed"></span>
<strong>FROM_LEFT_4TH_BUTTON_PRESSED</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="635dd-127">Quatrième bouton à partir de la gauche.</span><span class="sxs-lookup"><span data-stu-id="635dd-127">The fourth button from the left.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="635dd-128"><span id="RIGHTMOST_BUTTON_PRESSED"></span><span id="rightmost_button_pressed"></span>
<strong>RIGHTMOST_BUTTON_PRESSED</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="635dd-128"><span id="RIGHTMOST_BUTTON_PRESSED"></span><span id="rightmost_button_pressed"></span>
<strong>RIGHTMOST_BUTTON_PRESSED</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="635dd-129">Bouton de la souris le plus à droite.</span><span class="sxs-lookup"><span data-stu-id="635dd-129">The rightmost mouse button.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="635dd-130">**dwControlKeyState**</span><span class="sxs-lookup"><span data-stu-id="635dd-130">**dwControlKeyState**</span></span>  
<span data-ttu-id="635dd-131">État des touches de contrôle.</span><span class="sxs-lookup"><span data-stu-id="635dd-131">The state of the control keys.</span></span> <span data-ttu-id="635dd-132">Ce membre peut être une ou plusieurs des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="635dd-132">This member can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="635dd-133">Value</span><span class="sxs-lookup"><span data-stu-id="635dd-133">Value</span></span></th>
<th><span data-ttu-id="635dd-134">Signification</span><span class="sxs-lookup"><span data-stu-id="635dd-134">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="635dd-135"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="635dd-135"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="635dd-136">Le voyant Verr. MAJ est activé.</span><span class="sxs-lookup"><span data-stu-id="635dd-136">The CAPS LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="635dd-137"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span><span class="sxs-lookup"><span data-stu-id="635dd-137"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span></span></td>
<td><p><span data-ttu-id="635dd-138">La clé est améliorée.</span><span class="sxs-lookup"><span data-stu-id="635dd-138">The key is enhanced.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="635dd-139"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="635dd-139"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="635dd-140">La touche ALT de gauche est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="635dd-140">The left ALT key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="635dd-141"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="635dd-141"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="635dd-142">La touche CTRL de gauche est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="635dd-142">The left CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="635dd-143"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="635dd-143"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="635dd-144">La diode Verr. NUM est activée.</span><span class="sxs-lookup"><span data-stu-id="635dd-144">The NUM LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="635dd-145"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="635dd-145"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="635dd-146">La touche ALT de droite est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="635dd-146">The right ALT key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="635dd-147"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="635dd-147"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="635dd-148">La touche CTRL de droite est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="635dd-148">The right CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="635dd-149"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="635dd-149"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="635dd-150">Le voyant du verrou de défilement est activé.</span><span class="sxs-lookup"><span data-stu-id="635dd-150">The SCROLL LOCK light is on.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="635dd-151"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="635dd-151"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="635dd-152">La touche Maj est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="635dd-152">The SHIFT key is pressed.</span></span></p></td>
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
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="635dd-153">**dwEventFlags**</span><span class="sxs-lookup"><span data-stu-id="635dd-153">**dwEventFlags**</span></span>  
<span data-ttu-id="635dd-154">Type d’événement de souris.</span><span class="sxs-lookup"><span data-stu-id="635dd-154">The type of mouse event.</span></span> <span data-ttu-id="635dd-155">Si cette valeur est égale à zéro, elle indique qu’un bouton de la souris est enfoncé ou relâché.</span><span class="sxs-lookup"><span data-stu-id="635dd-155">If this value is zero, it indicates a mouse button being pressed or released.</span></span> <span data-ttu-id="635dd-156">Dans le cas contraire, ce membre est l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="635dd-156">Otherwise, this member is one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="635dd-157">Value</span><span class="sxs-lookup"><span data-stu-id="635dd-157">Value</span></span></th>
<th><span data-ttu-id="635dd-158">Signification</span><span class="sxs-lookup"><span data-stu-id="635dd-158">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="635dd-159"><span id="DOUBLE_CLICK"></span><span id="double_click"></span>
<strong>DOUBLE_CLICK</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="635dd-159"><span id="DOUBLE_CLICK"></span><span id="double_click"></span>
<strong>DOUBLE_CLICK</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="635dd-160">Le deuxième clic (appuyez sur le bouton) d’un double-clic s’est produit.</span><span class="sxs-lookup"><span data-stu-id="635dd-160">The second click (button press) of a double-click occurred.</span></span> <span data-ttu-id="635dd-161">Le premier clic est retourné en tant qu’événement de bouton-pression standard.</span><span class="sxs-lookup"><span data-stu-id="635dd-161">The first click is returned as a regular button-press event.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="635dd-162"><span id="MOUSE_HWHEELED"></span><span id="mouse_hwheeled"></span>
<strong>MOUSE_HWHEELED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="635dd-162"><span id="MOUSE_HWHEELED"></span><span id="mouse_hwheeled"></span>
<strong>MOUSE_HWHEELED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="635dd-163">La roulette horizontale de la souris a été déplacée.</span><span class="sxs-lookup"><span data-stu-id="635dd-163">The horizontal mouse wheel was moved.</span></span></p>
<p><span data-ttu-id="635dd-164">Si le mot de poids fort du membre <strong>dwButtonState</strong> contient une valeur positive, la roulette a été pivotée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="635dd-164">If the high word of the <strong>dwButtonState</strong> member contains a positive value, the wheel was rotated to the right.</span></span> <span data-ttu-id="635dd-165">Dans le cas contraire, la roulette a été pivotée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="635dd-165">Otherwise, the wheel was rotated to the left.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="635dd-166"><span id="MOUSE_MOVED"></span><span id="mouse_moved"></span>
<strong>MOUSE_MOVED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="635dd-166"><span id="MOUSE_MOVED"></span><span id="mouse_moved"></span>
<strong>MOUSE_MOVED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="635dd-167">Une modification de la position de la souris s’est produite.</span><span class="sxs-lookup"><span data-stu-id="635dd-167">A change in mouse position occurred.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="635dd-168"><span id="MOUSE_WHEELED"></span><span id="mouse_wheeled"></span>
<strong>MOUSE_WHEELED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="635dd-168"><span id="MOUSE_WHEELED"></span><span id="mouse_wheeled"></span>
<strong>MOUSE_WHEELED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="635dd-169">La roulette verticale de la souris a été déplacée.</span><span class="sxs-lookup"><span data-stu-id="635dd-169">The vertical mouse wheel was moved.</span></span></p>
<p><span data-ttu-id="635dd-170">Si le mot de poids fort du membre <strong>dwButtonState</strong> contient une valeur positive, la roulette a été pivotée vers l’avant, en dehors de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="635dd-170">If the high word of the <strong>dwButtonState</strong> member contains a positive value, the wheel was rotated forward, away from the user.</span></span> <span data-ttu-id="635dd-171">Dans le cas contraire, la roulette a été tournée vers l’arrière de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="635dd-171">Otherwise, the wheel was rotated backward, toward the user.</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="remarks"></a><span data-ttu-id="635dd-172">Remarques</span><span class="sxs-lookup"><span data-stu-id="635dd-172">Remarks</span></span>
-------

<span data-ttu-id="635dd-173">Les événements de souris sont placés dans la mémoire tampon d’entrée lorsque la console est en mode souris (**activer l' \_ \_ entrée de la souris**).</span><span class="sxs-lookup"><span data-stu-id="635dd-173">Mouse events are placed in the input buffer when the console is in mouse mode (**ENABLE\_MOUSE\_INPUT**).</span></span>

<span data-ttu-id="635dd-174">Les événements de souris sont générés chaque fois que l’utilisateur déplace la souris, ou appuie sur ou relâche l’un des boutons de la souris.</span><span class="sxs-lookup"><span data-stu-id="635dd-174">Mouse events are generated whenever the user moves the mouse, or presses or releases one of the mouse buttons.</span></span> <span data-ttu-id="635dd-175">Les événements de souris sont placés dans la mémoire tampon d’entrée d’une console uniquement lorsque le groupe de la console a le focus clavier et que le curseur se trouve dans les limites de la fenêtre de la console.</span><span class="sxs-lookup"><span data-stu-id="635dd-175">Mouse events are placed in a console's input buffer only when the console group has the keyboard focus and the cursor is within the borders of the console's window.</span></span>

<a name="examples"></a><span data-ttu-id="635dd-176">Exemples</span><span class="sxs-lookup"><span data-stu-id="635dd-176">Examples</span></span>
--------

<span data-ttu-id="635dd-177">Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="635dd-177">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="635dd-178">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="635dd-178">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="635dd-179">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="635dd-179">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="635dd-180">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="635dd-180">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="635dd-181">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="635dd-181">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="635dd-182">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="635dd-182">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="635dd-183">En-tête</span><span class="sxs-lookup"><span data-stu-id="635dd-183">Header</span></span></p></td>
<td><span data-ttu-id="635dd-184">WinConTypes. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="635dd-184">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="635dd-185"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="635dd-185"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="635dd-186">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="635dd-186">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="635dd-187">**enregistrement d’entrée \_**</span><span class="sxs-lookup"><span data-stu-id="635dd-187">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="635dd-188">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="635dd-188">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="635dd-189">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="635dd-189">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="635dd-190">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="635dd-190">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 




