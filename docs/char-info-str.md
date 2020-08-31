---
title: Structure CHAR_INFO
description: Spécifie un caractère Unicode ou ANSI et ses attributs. Cette structure est utilisée par les fonctions de la console pour lire et écrire dans une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- wincontypes/CHAR_INFO
- wincon/CHAR_INFO
- CHAR_INFO
- wincontypes/PCHAR_INFO
- wincon/PCHAR_INFO
- PCHAR_INFO
MS-HAID:
- '\_win32\_char\_info\_str'
- base.char\_info\_str
- consoles.char\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5574a862-b262-41af-8862-e9837c5c7b5f
topic_type:
- apiref
api_name:
- CHAR_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 6244edaa06b6dd69f8ab3962cf42cb893d08f699
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059373"
---
# <a name="char_info-structure"></a><span data-ttu-id="7806e-105">CHAR \_ info (structure)</span><span class="sxs-lookup"><span data-stu-id="7806e-105">CHAR\_INFO structure</span></span>


<span data-ttu-id="7806e-106">Spécifie un caractère Unicode ou ANSI et ses attributs.</span><span class="sxs-lookup"><span data-stu-id="7806e-106">Specifies a Unicode or ANSI character and its attributes.</span></span> <span data-ttu-id="7806e-107">Cette structure est utilisée par les fonctions de la console pour lire et écrire dans une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="7806e-107">This structure is used by console functions to read from and write to a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="7806e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7806e-108">Syntax</span></span>
------

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

<a name="members"></a><span data-ttu-id="7806e-109">Membres</span><span class="sxs-lookup"><span data-stu-id="7806e-109">Members</span></span>
-------

<span data-ttu-id="7806e-110">**Char**</span><span class="sxs-lookup"><span data-stu-id="7806e-110">**Char**</span></span>  
<span data-ttu-id="7806e-111">Union des membres suivants.</span><span class="sxs-lookup"><span data-stu-id="7806e-111">A union of the following members.</span></span>

<span data-ttu-id="7806e-112">**UnicodeChar**</span><span class="sxs-lookup"><span data-stu-id="7806e-112">**UnicodeChar**</span></span>  
<span data-ttu-id="7806e-113">Caractère Unicode d’une cellule de caractère de mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="7806e-113">Unicode character of a screen buffer character cell.</span></span>

<span data-ttu-id="7806e-114">**AsciiChar**</span><span class="sxs-lookup"><span data-stu-id="7806e-114">**AsciiChar**</span></span>  
<span data-ttu-id="7806e-115">Caractère ANSI d’une cellule de caractère de mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="7806e-115">ANSI character of a screen buffer character cell.</span></span>

<span data-ttu-id="7806e-116">**Attributs**</span><span class="sxs-lookup"><span data-stu-id="7806e-116">**Attributes**</span></span>  
<span data-ttu-id="7806e-117">Attributs de caractère.</span><span class="sxs-lookup"><span data-stu-id="7806e-117">The character attributes.</span></span> <span data-ttu-id="7806e-118">Ce membre peut être égal à zéro ou n’importe quelle combinaison des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="7806e-118">This member can be zero or any combination of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="7806e-119">Value</span><span class="sxs-lookup"><span data-stu-id="7806e-119">Value</span></span></th>
<th><span data-ttu-id="7806e-120">Signification</span><span class="sxs-lookup"><span data-stu-id="7806e-120">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="7806e-121"><span id="FOREGROUND_BLUE"></span><span id="foreground_blue"></span>
<strong>FOREGROUND_BLUE</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="7806e-121"><span id="FOREGROUND_BLUE"></span><span id="foreground_blue"></span>
<strong>FOREGROUND_BLUE</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="7806e-122">La couleur du texte contient le bleu.</span><span class="sxs-lookup"><span data-stu-id="7806e-122">Text color contains blue.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="7806e-123"><span id="FOREGROUND_GREEN"></span><span id="foreground_green"></span>
<strong>FOREGROUND_GREEN</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="7806e-123"><span id="FOREGROUND_GREEN"></span><span id="foreground_green"></span>
<strong>FOREGROUND_GREEN</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="7806e-124">La couleur du texte contient du vert.</span><span class="sxs-lookup"><span data-stu-id="7806e-124">Text color contains green.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="7806e-125"><span id="FOREGROUND_RED"></span><span id="foreground_red"></span>
<strong>FOREGROUND_RED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="7806e-125"><span id="FOREGROUND_RED"></span><span id="foreground_red"></span>
<strong>FOREGROUND_RED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="7806e-126">La couleur du texte contient le rouge.</span><span class="sxs-lookup"><span data-stu-id="7806e-126">Text color contains red.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="7806e-127"><span id="FOREGROUND_INTENSITY"></span><span id="foreground_intensity"></span>
<strong>FOREGROUND_INTENSITY</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="7806e-127"><span id="FOREGROUND_INTENSITY"></span><span id="foreground_intensity"></span>
<strong>FOREGROUND_INTENSITY</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="7806e-128">La couleur du texte est intensifiée.</span><span class="sxs-lookup"><span data-stu-id="7806e-128">Text color is intensified.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="7806e-129"><span id="BACKGROUND_BLUE"></span><span id="background_blue"></span>
<strong>BACKGROUND_BLUE</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="7806e-129"><span id="BACKGROUND_BLUE"></span><span id="background_blue"></span>
<strong>BACKGROUND_BLUE</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="7806e-130">La couleur d’arrière-plan contient le bleu.</span><span class="sxs-lookup"><span data-stu-id="7806e-130">Background color contains blue.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="7806e-131"><span id="BACKGROUND_GREEN"></span><span id="background_green"></span>
<strong>BACKGROUND_GREEN</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="7806e-131"><span id="BACKGROUND_GREEN"></span><span id="background_green"></span>
<strong>BACKGROUND_GREEN</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="7806e-132">La couleur d’arrière-plan contient du vert.</span><span class="sxs-lookup"><span data-stu-id="7806e-132">Background color contains green.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="7806e-133"><span id="BACKGROUND_RED"></span><span id="background_red"></span>
<strong>BACKGROUND_RED</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="7806e-133"><span id="BACKGROUND_RED"></span><span id="background_red"></span>
<strong>BACKGROUND_RED</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="7806e-134">La couleur d’arrière-plan contient le rouge.</span><span class="sxs-lookup"><span data-stu-id="7806e-134">Background color contains red.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="7806e-135"><span id="BACKGROUND_INTENSITY"></span><span id="background_intensity"></span>
<strong>BACKGROUND_INTENSITY</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="7806e-135"><span id="BACKGROUND_INTENSITY"></span><span id="background_intensity"></span>
<strong>BACKGROUND_INTENSITY</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="7806e-136">La couleur d’arrière-plan est intensifiée.</span><span class="sxs-lookup"><span data-stu-id="7806e-136">Background color is intensified.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="7806e-137"><span id="COMMON_LVB_LEADING_BYTE"></span><span id="common_lvb_leading_byte"></span>
<strong>COMMON_LVB_LEADING_BYTE</strong> 0x0100</span><span class="sxs-lookup"><span data-stu-id="7806e-137"><span id="COMMON_LVB_LEADING_BYTE"></span><span id="common_lvb_leading_byte"></span>
<strong>COMMON_LVB_LEADING_BYTE</strong> 0x0100</span></span></td>
<td><p><span data-ttu-id="7806e-138">Octet de début.</span><span class="sxs-lookup"><span data-stu-id="7806e-138">Leading byte.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="7806e-139"><span id="COMMON_LVB_TRAILING_BYTE"></span><span id="common_lvb_trailing_byte"></span>
<strong>COMMON_LVB_TRAILING_BYTE</strong> 0x0200</span><span class="sxs-lookup"><span data-stu-id="7806e-139"><span id="COMMON_LVB_TRAILING_BYTE"></span><span id="common_lvb_trailing_byte"></span>
<strong>COMMON_LVB_TRAILING_BYTE</strong> 0x0200</span></span></td>
<td><p><span data-ttu-id="7806e-140">Octet de fin.</span><span class="sxs-lookup"><span data-stu-id="7806e-140">Trailing byte.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="7806e-141"><span id="COMMON_LVB_GRID_HORIZONTAL"></span><span id="common_lvb_grid_horizontal"></span>
<strong>COMMON_LVB_GRID_HORIZONTAL</strong> 0x0400</span><span class="sxs-lookup"><span data-stu-id="7806e-141"><span id="COMMON_LVB_GRID_HORIZONTAL"></span><span id="common_lvb_grid_horizontal"></span>
<strong>COMMON_LVB_GRID_HORIZONTAL</strong> 0x0400</span></span></td>
<td><p><span data-ttu-id="7806e-142">Horizontal supérieur</span><span class="sxs-lookup"><span data-stu-id="7806e-142">Top horizontal</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="7806e-143"><span id="COMMON_LVB_GRID_LVERTICAL"></span><span id="common_lvb_grid_lvertical"></span>
<strong>COMMON_LVB_GRID_LVERTICAL</strong> 0x0800</span><span class="sxs-lookup"><span data-stu-id="7806e-143"><span id="COMMON_LVB_GRID_LVERTICAL"></span><span id="common_lvb_grid_lvertical"></span>
<strong>COMMON_LVB_GRID_LVERTICAL</strong> 0x0800</span></span></td>
<td><p><span data-ttu-id="7806e-144">Vertical gauche.</span><span class="sxs-lookup"><span data-stu-id="7806e-144">Left vertical.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="7806e-145"><span id="COMMON_LVB_GRID_RVERTICAL"></span><span id="common_lvb_grid_rvertical"></span>
<strong>COMMON_LVB_GRID_RVERTICAL</strong> 0x1000</span><span class="sxs-lookup"><span data-stu-id="7806e-145"><span id="COMMON_LVB_GRID_RVERTICAL"></span><span id="common_lvb_grid_rvertical"></span>
<strong>COMMON_LVB_GRID_RVERTICAL</strong> 0x1000</span></span></td>
<td><p><span data-ttu-id="7806e-146">Verticale droite.</span><span class="sxs-lookup"><span data-stu-id="7806e-146">Right vertical.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="7806e-147"><span id="COMMON_LVB_REVERSE_VIDEO"></span><span id="common_lvb_reverse_video"></span>
<strong>COMMON_LVB_REVERSE_VIDEO</strong> 0x4000</span><span class="sxs-lookup"><span data-stu-id="7806e-147"><span id="COMMON_LVB_REVERSE_VIDEO"></span><span id="common_lvb_reverse_video"></span>
<strong>COMMON_LVB_REVERSE_VIDEO</strong> 0x4000</span></span></td>
<td><p><span data-ttu-id="7806e-148">Attribut de premier plan et d’arrière-plan inversé.</span><span class="sxs-lookup"><span data-stu-id="7806e-148">Reverse foreground and background attribute.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="7806e-149"><span id="COMMON_LVB_UNDERSCORE"></span><span id="common_lvb_underscore"></span>
<strong>COMMON_LVB_UNDERSCORE</strong> 0x8000</span><span class="sxs-lookup"><span data-stu-id="7806e-149"><span id="COMMON_LVB_UNDERSCORE"></span><span id="common_lvb_underscore"></span>
<strong>COMMON_LVB_UNDERSCORE</strong> 0x8000</span></span></td>
<td><p><span data-ttu-id="7806e-150">Soulignement.</span><span class="sxs-lookup"><span data-stu-id="7806e-150">Underscore.</span></span></p></td>
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

 

<a name="examples"></a><span data-ttu-id="7806e-151">Exemples</span><span class="sxs-lookup"><span data-stu-id="7806e-151">Examples</span></span>
--------

<span data-ttu-id="7806e-152">Pour obtenir un exemple, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="7806e-152">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="7806e-153">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7806e-153">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="7806e-154">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7806e-154">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="7806e-155">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="7806e-155">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7806e-156">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7806e-156">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="7806e-157">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="7806e-157">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7806e-158">En-tête</span><span class="sxs-lookup"><span data-stu-id="7806e-158">Header</span></span></p></td>
<td><span data-ttu-id="7806e-159">Wincon. h (inclure Windows. h)</span><span class="sxs-lookup"><span data-stu-id="7806e-159">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="7806e-160"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7806e-160"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="7806e-161">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="7806e-161">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="7806e-162">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="7806e-162">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="7806e-163">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="7806e-163">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

 

 




