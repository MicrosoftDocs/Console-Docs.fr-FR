---
title: Structure CONSOLE_READCONSOLE_CONTROL
description: Consultez les informations de référence sur la structure CONSOLE_READCONSOLE_CONTROL, qui contient des informations relatives à une opération de lecture de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi/CONSOLE_READCONSOLE_CONTROL
- wincon/CONSOLE_READCONSOLE_CONTROL
- CONSOLE_READCONSOLE_CONTROL
- consoleapi/PCONSOLE_READCONSOLE_CONTROL
- wincon/PCONSOLE_READCONSOLE_CONTROL
- PCONSOLE_READCONSOLE_CONTROL
MS-HAID:
- base.console\_readconsole\_control
- consoles.console\_readconsole\_control
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a8451a6-d692-43af-88c4-972c4dc5e07c
topic_type:
- apiref
api_name:
- CONSOLE_READCONSOLE_CONTROL
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4fc6af26cd540a7af207af252963c21ba216cdee
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059308"
---
# <a name="console_readconsole_control-structure"></a><span data-ttu-id="29f11-104">\_Structure de contrôle READCONSOLE de la console \_</span><span class="sxs-lookup"><span data-stu-id="29f11-104">CONSOLE\_READCONSOLE\_CONTROL structure</span></span>


<span data-ttu-id="29f11-105">Contient des informations relatives à une opération de lecture de console.</span><span class="sxs-lookup"><span data-stu-id="29f11-105">Contains information for a console read operation.</span></span>

<a name="syntax"></a><span data-ttu-id="29f11-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29f11-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

<a name="members"></a><span data-ttu-id="29f11-107">Membres</span><span class="sxs-lookup"><span data-stu-id="29f11-107">Members</span></span>
-------

<span data-ttu-id="29f11-108">**nLength**</span><span class="sxs-lookup"><span data-stu-id="29f11-108">**nLength**</span></span>  
<span data-ttu-id="29f11-109">Taille de la structure.</span><span class="sxs-lookup"><span data-stu-id="29f11-109">The size of the structure.</span></span> <span data-ttu-id="29f11-110">Affectez à ce membre la valeur `sizeof(CONSOLE_READCONSOLE_CONTROL)` .</span><span class="sxs-lookup"><span data-stu-id="29f11-110">Set this member to `sizeof(CONSOLE_READCONSOLE_CONTROL)`.</span></span>

<span data-ttu-id="29f11-111">**nInitialChars**</span><span class="sxs-lookup"><span data-stu-id="29f11-111">**nInitialChars**</span></span>  
<span data-ttu-id="29f11-112">Nombre de caractères à ignorer (et donc conserver) avant l’écriture de l’entrée récemment lue dans la mémoire tampon transmise à la fonction [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="29f11-112">The number of characters to skip (and thus preserve) before writing newly read input in the buffer passed to the [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="29f11-113">Cette valeur doit être inférieure au paramètre *nNumberOfCharsToRead* de la fonction **ReadConsole** .</span><span class="sxs-lookup"><span data-stu-id="29f11-113">This value must be less than the *nNumberOfCharsToRead* parameter of the **ReadConsole** function.</span></span>

<span data-ttu-id="29f11-114">**dwCtrlWakeupMask**</span><span class="sxs-lookup"><span data-stu-id="29f11-114">**dwCtrlWakeupMask**</span></span>  
<span data-ttu-id="29f11-115">Caractère de contrôle défini par l’utilisateur utilisé pour signaler que la lecture est terminée.</span><span class="sxs-lookup"><span data-stu-id="29f11-115">A user-defined control character used to signal that the read is complete.</span></span>

<span data-ttu-id="29f11-116">**dwControlKeyState**</span><span class="sxs-lookup"><span data-stu-id="29f11-116">**dwControlKeyState**</span></span>  
<span data-ttu-id="29f11-117">État des touches de contrôle.</span><span class="sxs-lookup"><span data-stu-id="29f11-117">The state of the control keys.</span></span> <span data-ttu-id="29f11-118">Ce membre peut être une ou plusieurs des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="29f11-118">This member can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="29f11-119">Value</span><span class="sxs-lookup"><span data-stu-id="29f11-119">Value</span></span></th>
<th><span data-ttu-id="29f11-120">Signification</span><span class="sxs-lookup"><span data-stu-id="29f11-120">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="29f11-121"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="29f11-121"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="29f11-122">Le voyant Verr. MAJ est activé.</span><span class="sxs-lookup"><span data-stu-id="29f11-122">The CAPS LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="29f11-123"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span><span class="sxs-lookup"><span data-stu-id="29f11-123"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span></span></td>
<td><p><span data-ttu-id="29f11-124">La clé est améliorée.</span><span class="sxs-lookup"><span data-stu-id="29f11-124">The key is enhanced.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="29f11-125"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="29f11-125"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="29f11-126">La touche ALT de gauche est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="29f11-126">The left ALT key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="29f11-127"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="29f11-127"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="29f11-128">La touche CTRL de gauche est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="29f11-128">The left CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="29f11-129"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="29f11-129"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="29f11-130">La diode Verr. NUM est activée.</span><span class="sxs-lookup"><span data-stu-id="29f11-130">The NUM LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="29f11-131"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="29f11-131"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="29f11-132">La touche ALT de droite est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="29f11-132">The right ALT key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="29f11-133"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="29f11-133"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="29f11-134">La touche CTRL de droite est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="29f11-134">The right CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="29f11-135"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="29f11-135"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="29f11-136">Le voyant du verrou de défilement est activé.</span><span class="sxs-lookup"><span data-stu-id="29f11-136">The SCROLL LOCK light is on.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="29f11-137"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="29f11-137"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="29f11-138">La touche Maj est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="29f11-138">The SHIFT key is pressed.</span></span></p></td>
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

 

<a name="requirements"></a><span data-ttu-id="29f11-139">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="29f11-139">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="29f11-140">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="29f11-140">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="29f11-141">Windows Vista [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="29f11-141">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="29f11-142">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="29f11-142">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="29f11-143">Windows Server 2008 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="29f11-143">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="29f11-144">En-tête</span><span class="sxs-lookup"><span data-stu-id="29f11-144">Header</span></span></p></td>
<td><span data-ttu-id="29f11-145">ConsoleApi. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="29f11-145">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="29f11-146"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29f11-146"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="29f11-147">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="29f11-147">**ReadConsole**</span></span>](readconsole.md)

 

 




