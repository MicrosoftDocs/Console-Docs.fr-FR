---
title: Structure CONSOLE_SELECTION_INFO
description: Consultez les informations de référence sur la structure CONSOLE_SELECTION_INFO, qui contient des informations pour une sélection de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/CONSOLE_SELECTION_INFO
- wincon/CONSOLE_SELECTION_INFO
- CONSOLE_SELECTION_INFO
- consoleapi3/PCONSOLE_SELECTION_INFO
- wincon/PCONSOLE_SELECTION_INFO
- PCONSOLE_SELECTION_INFO
MS-HAID:
- '\_win32\_console\_selection\_info\_str'
- base.console\_selection\_info\_str
- consoles.console\_selection\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9530b249-8db4-4516-9cc8-2b452c6751f9
topic_type:
- apiref
api_name:
- CONSOLE_SELECTION_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: a16fe43e7b7cc4b5890284921823aee7b79217b2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059269"
---
# <a name="console_selection_info-structure"></a><span data-ttu-id="b8e51-104">Structure des informations de \_ sélection de la console \_</span><span class="sxs-lookup"><span data-stu-id="b8e51-104">CONSOLE\_SELECTION\_INFO structure</span></span>


<span data-ttu-id="b8e51-105">Contient des informations pour une sélection de la console.</span><span class="sxs-lookup"><span data-stu-id="b8e51-105">Contains information for a console selection.</span></span>

<a name="syntax"></a><span data-ttu-id="b8e51-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8e51-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

<a name="members"></a><span data-ttu-id="b8e51-107">Membres</span><span class="sxs-lookup"><span data-stu-id="b8e51-107">Members</span></span>
-------

<span data-ttu-id="b8e51-108">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="b8e51-108">**dwFlags**</span></span>  
<span data-ttu-id="b8e51-109">Indicateur de sélection.</span><span class="sxs-lookup"><span data-stu-id="b8e51-109">The selection indicator.</span></span> <span data-ttu-id="b8e51-110">Ce membre peut être une ou plusieurs des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="b8e51-110">This member can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="b8e51-111">Value</span><span class="sxs-lookup"><span data-stu-id="b8e51-111">Value</span></span></th>
<th><span data-ttu-id="b8e51-112">Signification</span><span class="sxs-lookup"><span data-stu-id="b8e51-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="b8e51-113"><span id="CONSOLE_MOUSE_DOWN"></span><span id="console_mouse_down"></span>
<strong>CONSOLE_MOUSE_DOWN</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="b8e51-113"><span id="CONSOLE_MOUSE_DOWN"></span><span id="console_mouse_down"></span>
<strong>CONSOLE_MOUSE_DOWN</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="b8e51-114">La souris est inactive</span><span class="sxs-lookup"><span data-stu-id="b8e51-114">Mouse is down</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="b8e51-115"><span id="CONSOLE_MOUSE_SELECTION"></span><span id="console_mouse_selection"></span>
<strong>CONSOLE_MOUSE_SELECTION</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="b8e51-115"><span id="CONSOLE_MOUSE_SELECTION"></span><span id="console_mouse_selection"></span>
<strong>CONSOLE_MOUSE_SELECTION</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="b8e51-116">Sélection à l’aide de la souris</span><span class="sxs-lookup"><span data-stu-id="b8e51-116">Selecting with the mouse</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="b8e51-117"><span id="CONSOLE_NO_SELECTION"></span><span id="console_no_selection"></span>
<strong>CONSOLE_NO_SELECTION</strong> 0x0000</span><span class="sxs-lookup"><span data-stu-id="b8e51-117"><span id="CONSOLE_NO_SELECTION"></span><span id="console_no_selection"></span>
<strong>CONSOLE_NO_SELECTION</strong> 0x0000</span></span></td>
<td><p><span data-ttu-id="b8e51-118">Aucune sélection</span><span class="sxs-lookup"><span data-stu-id="b8e51-118">No selection</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="b8e51-119"><span id="CONSOLE_SELECTION_IN_PROGRESS"></span><span id="console_selection_in_progress"></span>
<strong>CONSOLE_SELECTION_IN_PROGRESS</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="b8e51-119"><span id="CONSOLE_SELECTION_IN_PROGRESS"></span><span id="console_selection_in_progress"></span>
<strong>CONSOLE_SELECTION_IN_PROGRESS</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="b8e51-120">La sélection a commencé</span><span class="sxs-lookup"><span data-stu-id="b8e51-120">Selection has begun</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="b8e51-121"><span id="CONSOLE_SELECTION_NOT_EMPTY"></span><span id="console_selection_not_empty"></span>
<strong>CONSOLE_SELECTION_NOT_EMPTY</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="b8e51-121"><span id="CONSOLE_SELECTION_NOT_EMPTY"></span><span id="console_selection_not_empty"></span>
<strong>CONSOLE_SELECTION_NOT_EMPTY</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="b8e51-122">Le rectangle de sélection n’est pas vide</span><span class="sxs-lookup"><span data-stu-id="b8e51-122">Selection rectangle is not empty</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="b8e51-123">**dwSelectionAnchor**</span><span class="sxs-lookup"><span data-stu-id="b8e51-123">**dwSelectionAnchor**</span></span>  
<span data-ttu-id="b8e51-124">Structure de [**repère**](coord-str.md) qui spécifie l’ancre de sélection, en caractères.</span><span class="sxs-lookup"><span data-stu-id="b8e51-124">A [**COORD**](coord-str.md) structure that specifies the selection anchor, in characters.</span></span>

<span data-ttu-id="b8e51-125">**srSelection**</span><span class="sxs-lookup"><span data-stu-id="b8e51-125">**srSelection**</span></span>  
<span data-ttu-id="b8e51-126">[**Petite structure \_ Rect**](small-rect-str.md) qui spécifie le rectangle de sélection.</span><span class="sxs-lookup"><span data-stu-id="b8e51-126">A [**SMALL\_RECT**](small-rect-str.md) structure that specifies the selection rectangle.</span></span>

<a name="requirements"></a><span data-ttu-id="b8e51-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b8e51-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b8e51-128">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="b8e51-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="b8e51-129">Windows XP [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="b8e51-129">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b8e51-130">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="b8e51-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="b8e51-131">Windows Server 2003 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="b8e51-131">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b8e51-132">En-tête</span><span class="sxs-lookup"><span data-stu-id="b8e51-132">Header</span></span></p></td>
<td><span data-ttu-id="b8e51-133">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b8e51-133">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="b8e51-134"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8e51-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="b8e51-135">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="b8e51-135">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="b8e51-136">**GetConsoleSelectionInfo**</span><span class="sxs-lookup"><span data-stu-id="b8e51-136">**GetConsoleSelectionInfo**</span></span>](getconsoleselectioninfo.md)

[<span data-ttu-id="b8e51-137">**PETIT \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="b8e51-137">**SMALL\_RECT**</span></span>](small-rect-str.md)

 

 




