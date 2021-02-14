---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- wincontypes/SMALL_RECT
- wincon/SMALL_RECT
- SMALL_RECT
title: SMALL_RECT, structure
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: f9cbe94fff616a93d835f47b618a28bb9f521891
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358489"
---
# <a name="small_rect-structure"></a><span data-ttu-id="7cfc7-104">PETITE \_ structure Rect</span><span class="sxs-lookup"><span data-stu-id="7cfc7-104">SMALL\_RECT structure</span></span>

<span data-ttu-id="7cfc7-105">Définit les coordonnées des angles supérieur gauche et inférieur droit d’un rectangle.</span><span class="sxs-lookup"><span data-stu-id="7cfc7-105">Defines the coordinates of the upper left and lower right corners of a rectangle.</span></span>

## <a name="syntax"></a><span data-ttu-id="7cfc7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cfc7-106">Syntax</span></span>

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

## <a name="members"></a><span data-ttu-id="7cfc7-107">Membres</span><span class="sxs-lookup"><span data-stu-id="7cfc7-107">Members</span></span>

<span data-ttu-id="7cfc7-108">**Left**</span><span class="sxs-lookup"><span data-stu-id="7cfc7-108">**Left**</span></span>  
<span data-ttu-id="7cfc7-109">Coordonnée x de l’angle supérieur gauche du rectangle.</span><span class="sxs-lookup"><span data-stu-id="7cfc7-109">The x-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="7cfc7-110">**Top**</span><span class="sxs-lookup"><span data-stu-id="7cfc7-110">**Top**</span></span>  
<span data-ttu-id="7cfc7-111">Coordonnée y de l’angle supérieur gauche du rectangle.</span><span class="sxs-lookup"><span data-stu-id="7cfc7-111">The y-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="7cfc7-112">**Right**</span><span class="sxs-lookup"><span data-stu-id="7cfc7-112">**Right**</span></span>  
<span data-ttu-id="7cfc7-113">Coordonnée x du coin inférieur droit du rectangle.</span><span class="sxs-lookup"><span data-stu-id="7cfc7-113">The x-coordinate of the lower right corner of the rectangle.</span></span>

<span data-ttu-id="7cfc7-114">**Bas**</span><span class="sxs-lookup"><span data-stu-id="7cfc7-114">**Bottom**</span></span>  
<span data-ttu-id="7cfc7-115">Coordonnée y du coin inférieur droit du rectangle.</span><span class="sxs-lookup"><span data-stu-id="7cfc7-115">The y-coordinate of the lower right corner of the rectangle.</span></span>

## <a name="remarks"></a><span data-ttu-id="7cfc7-116">Notes</span><span class="sxs-lookup"><span data-stu-id="7cfc7-116">Remarks</span></span>

<span data-ttu-id="7cfc7-117">Cette structure est utilisée par les fonctions de la console pour spécifier les zones rectangulaires des mémoires tampons d’écran de la console, où les coordonnées spécifient les lignes et les colonnes des cellules de caractères de la mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="7cfc7-117">This structure is used by console functions to specify rectangular areas of console screen buffers, where the coordinates specify the rows and columns of screen-buffer character cells.</span></span>

## <a name="examples"></a><span data-ttu-id="7cfc7-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="7cfc7-118">Examples</span></span>

<span data-ttu-id="7cfc7-119">Pour obtenir un exemple, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="7cfc7-119">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="7cfc7-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7cfc7-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="7cfc7-121">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7cfc7-121">Minimum supported client</span></span> | <span data-ttu-id="7cfc7-122">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="7cfc7-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="7cfc7-123">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7cfc7-123">Minimum supported server</span></span> | <span data-ttu-id="7cfc7-124">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="7cfc7-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="7cfc7-125">En-tête</span><span class="sxs-lookup"><span data-stu-id="7cfc7-125">Header</span></span> | <span data-ttu-id="7cfc7-126">WinConTypes. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="7cfc7-126">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="7cfc7-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cfc7-127">See also</span></span>

<span data-ttu-id="7cfc7-128">[**RECTANGULAIRE**](/previous-versions//dd162897(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="7cfc7-128">[**RECT**](/previous-versions//dd162897(v=vs.85))</span></span>

<span data-ttu-id="7cfc7-129">[**RECTo**](/previous-versions//dd162907(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="7cfc7-129">[**RECTL**](/previous-versions//dd162907(v=vs.85))</span></span>