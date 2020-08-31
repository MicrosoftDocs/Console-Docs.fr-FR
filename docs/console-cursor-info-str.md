---
title: Structure CONSOLE_CURSOR_INFO
description: Contient les informations relatives à la taille et à la visibilité sur le curseur de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- wincontypes/CONSOLE_CURSOR_INFO
- wincon/CONSOLE_CURSOR_INFO
- CONSOLE_CURSOR_INFO
- wincontypes/PCONSOLE_CURSOR_INFO
- wincon/PCONSOLE_CURSOR_INFO
- PCONSOLE_CURSOR_INFO
MS-HAID:
- '\_win32\_console\_cursor\_info\_str'
- base.console\_cursor\_info\_str
- consoles.console\_cursor\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0e71ce8c-e008-4bd7-922e-c44484b425ef
topic_type:
- apiref
api_name:
- CONSOLE_CURSOR_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 0ac3eb459810f2c8ebc861759312350a487abd3c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059336"
---
# <a name="console_cursor_info-structure"></a><span data-ttu-id="e2776-104">Structure des informations du \_ curseur de la console \_</span><span class="sxs-lookup"><span data-stu-id="e2776-104">CONSOLE\_CURSOR\_INFO structure</span></span>


<span data-ttu-id="e2776-105">Contient des informations sur le curseur de la console.</span><span class="sxs-lookup"><span data-stu-id="e2776-105">Contains information about the console cursor.</span></span>

<a name="syntax"></a><span data-ttu-id="e2776-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2776-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

<a name="members"></a><span data-ttu-id="e2776-107">Membres</span><span class="sxs-lookup"><span data-stu-id="e2776-107">Members</span></span>
-------

<span data-ttu-id="e2776-108">**dwSize nul**</span><span class="sxs-lookup"><span data-stu-id="e2776-108">**dwSize**</span></span>  
<span data-ttu-id="e2776-109">Pourcentage de la cellule de caractère qui est rempli par le curseur.</span><span class="sxs-lookup"><span data-stu-id="e2776-109">The percentage of the character cell that is filled by the cursor.</span></span> <span data-ttu-id="e2776-110">Cette valeur est comprise entre 1 et 100.</span><span class="sxs-lookup"><span data-stu-id="e2776-110">This value is between 1 and 100.</span></span> <span data-ttu-id="e2776-111">L’apparence du curseur varie, du remplissage complet de la cellule à l’affichage sous la forme d’une ligne horizontale au bas de la cellule.</span><span class="sxs-lookup"><span data-stu-id="e2776-111">The cursor appearance varies, ranging from completely filling the cell to showing up as a horizontal line at the bottom of the cell.</span></span>

<span data-ttu-id="e2776-112">**Remarque**    Alors que la valeur **dwSize nul** est normalement comprise entre 1 et 100, dans certains cas, une valeur en dehors de cette plage peut être retournée.</span><span class="sxs-lookup"><span data-stu-id="e2776-112">**Note**  While the **dwSize** value is normally between 1 and 100, under some circumstances a value outside of that range might be returned.</span></span> <span data-ttu-id="e2776-113">Par exemple, si **CursorSize** est défini sur 0 dans le registre, la valeur **dwSize nul** retournée est 0.</span><span class="sxs-lookup"><span data-stu-id="e2776-113">For example, if **CursorSize** is set to 0 in the registry, the **dwSize** value returned would be 0.</span></span>

 

<span data-ttu-id="e2776-114">**bVisible**</span><span class="sxs-lookup"><span data-stu-id="e2776-114">**bVisible**</span></span>  
<span data-ttu-id="e2776-115">Visibilité du curseur.</span><span class="sxs-lookup"><span data-stu-id="e2776-115">The visibility of the cursor.</span></span> <span data-ttu-id="e2776-116">Si le curseur est visible, ce membre a la **valeur true**.</span><span class="sxs-lookup"><span data-stu-id="e2776-116">If the cursor is visible, this member is **TRUE**.</span></span>

<a name="requirements"></a><span data-ttu-id="e2776-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e2776-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e2776-118">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="e2776-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="e2776-119">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="e2776-119">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e2776-120">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="e2776-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="e2776-121">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="e2776-121">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e2776-122">En-tête</span><span class="sxs-lookup"><span data-stu-id="e2776-122">Header</span></span></p></td>
<td><span data-ttu-id="e2776-123">Wincon. h (inclure Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e2776-123">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="e2776-124"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2776-124"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="e2776-125">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="e2776-125">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="e2776-126">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="e2776-126">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

 

 




