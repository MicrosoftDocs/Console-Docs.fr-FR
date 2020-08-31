---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- wincontypes/SMALL_RECT
- wincon/SMALL_RECT
- SMALL_RECT
title: Structure SMALL_RECT
description: Définit les coordonnées des angles supérieur gauche et inférieur droit d’un rectangle.
MS-HAID:
- '\_win32\_small\_rect\_str'
- base.small\_rect\_str
- consoles.small\_rect\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 62639815-c7e9-4ae2-b152-61290f78422b
topic_type:
- apiref
api_name:
- SMALL_RECT
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: b0c0bfe93c85af89c5aaefeda032795de72ed627
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060558"
---
# <a name="small_rect-structure"></a><span data-ttu-id="7b038-104">PETITE \_ structure Rect</span><span class="sxs-lookup"><span data-stu-id="7b038-104">SMALL\_RECT structure</span></span>


<span data-ttu-id="7b038-105">Définit les coordonnées des angles supérieur gauche et inférieur droit d’un rectangle.</span><span class="sxs-lookup"><span data-stu-id="7b038-105">Defines the coordinates of the upper left and lower right corners of a rectangle.</span></span>

<a name="syntax"></a><span data-ttu-id="7b038-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b038-106">Syntax</span></span>
------

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

<a name="members"></a><span data-ttu-id="7b038-107">Membres</span><span class="sxs-lookup"><span data-stu-id="7b038-107">Members</span></span>
-------

<span data-ttu-id="7b038-108">**Left**</span><span class="sxs-lookup"><span data-stu-id="7b038-108">**Left**</span></span>  
<span data-ttu-id="7b038-109">Coordonnée x de l’angle supérieur gauche du rectangle.</span><span class="sxs-lookup"><span data-stu-id="7b038-109">The x-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="7b038-110">**Top**</span><span class="sxs-lookup"><span data-stu-id="7b038-110">**Top**</span></span>  
<span data-ttu-id="7b038-111">Coordonnée y de l’angle supérieur gauche du rectangle.</span><span class="sxs-lookup"><span data-stu-id="7b038-111">The y-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="7b038-112">**Right**</span><span class="sxs-lookup"><span data-stu-id="7b038-112">**Right**</span></span>  
<span data-ttu-id="7b038-113">Coordonnée x du coin inférieur droit du rectangle.</span><span class="sxs-lookup"><span data-stu-id="7b038-113">The x-coordinate of the lower right corner of the rectangle.</span></span>

<span data-ttu-id="7b038-114">**Bas**</span><span class="sxs-lookup"><span data-stu-id="7b038-114">**Bottom**</span></span>  
<span data-ttu-id="7b038-115">Coordonnée y du coin inférieur droit du rectangle.</span><span class="sxs-lookup"><span data-stu-id="7b038-115">The y-coordinate of the lower right corner of the rectangle.</span></span>

<a name="remarks"></a><span data-ttu-id="7b038-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="7b038-116">Remarks</span></span>
-------

<span data-ttu-id="7b038-117">Cette structure est utilisée par les fonctions de la console pour spécifier les zones rectangulaires des mémoires tampons d’écran de la console, où les coordonnées spécifient les lignes et les colonnes des cellules de caractères de la mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="7b038-117">This structure is used by console functions to specify rectangular areas of console screen buffers, where the coordinates specify the rows and columns of screen-buffer character cells.</span></span>

<a name="examples"></a><span data-ttu-id="7b038-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="7b038-118">Examples</span></span>
--------

<span data-ttu-id="7b038-119">Pour obtenir un exemple, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="7b038-119">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="7b038-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7b038-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="7b038-121">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7b038-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="7b038-122">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="7b038-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7b038-123">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7b038-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="7b038-124">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="7b038-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7b038-125">En-tête</span><span class="sxs-lookup"><span data-stu-id="7b038-125">Header</span></span></p></td>
<td><span data-ttu-id="7b038-126">WinConTypes. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="7b038-126">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="7b038-127"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b038-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="7b038-128">**RECTANGULAIRE**</span><span class="sxs-lookup"><span data-stu-id="7b038-128">**RECT**</span></span>](https://msdn.microsoft.com/library/windows/desktop/dd162897)

[<span data-ttu-id="7b038-129">**RECTo**</span><span class="sxs-lookup"><span data-stu-id="7b038-129">**RECTL**</span></span>](https://msdn.microsoft.com/library/windows/desktop/dd162907)

 

 




