---
title: COORD, structure
description: Définit les coordonnées d’une cellule de caractère dans une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- wincontypes/COORD
- wincon/COORD
- COORD
- wincontypes/PCOORD
- wincon/PCOORD
- PCOORD
MS-HAID:
- '\_win32\_coord\_str'
- base.coord\_str
- consoles.coord\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d730c46e-ea17-475e-b956-8ee5f4f5c04e
topic_type:
- apiref
api_name:
- COORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: c8e6f87c3a2730a8af21b9bc064c71900fb82f5b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038307"
---
# <a name="coord-structure"></a><span data-ttu-id="35a04-104">COORD, structure</span><span class="sxs-lookup"><span data-stu-id="35a04-104">COORD structure</span></span>

<span data-ttu-id="35a04-105">Définit les coordonnées d’une cellule de caractère dans une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="35a04-105">Defines the coordinates of a character cell in a console screen buffer.</span></span> <span data-ttu-id="35a04-106">L’origine du système de coordonnées (0,0) se trouve dans la cellule supérieure gauche de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="35a04-106">The origin of the coordinate system (0,0) is at the top, left cell of the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="35a04-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35a04-107">Syntax</span></span>

```C
typedef struct _COORD {
  SHORT X;
  SHORT Y;
} COORD, *PCOORD;
```

## <a name="members"></a><span data-ttu-id="35a04-108">Membres</span><span class="sxs-lookup"><span data-stu-id="35a04-108">Members</span></span>

<span data-ttu-id="35a04-109">**X**</span><span class="sxs-lookup"><span data-stu-id="35a04-109">**X**</span></span>  
<span data-ttu-id="35a04-110">Valeur de la coordonnée ou de la colonne horizontale.</span><span class="sxs-lookup"><span data-stu-id="35a04-110">The horizontal coordinate or column value.</span></span> <span data-ttu-id="35a04-111">Les unités dépendent de l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="35a04-111">The units depend on the function call.</span></span>

<span data-ttu-id="35a04-112">**O**</span><span class="sxs-lookup"><span data-stu-id="35a04-112">**Y**</span></span>  
<span data-ttu-id="35a04-113">Valeur de la coordonnée ou de la ligne verticale.</span><span class="sxs-lookup"><span data-stu-id="35a04-113">The vertical coordinate or row value.</span></span> <span data-ttu-id="35a04-114">Les unités dépendent de l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="35a04-114">The units depend on the function call.</span></span>

## <a name="examples"></a><span data-ttu-id="35a04-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="35a04-115">Examples</span></span>

<span data-ttu-id="35a04-116">Pour obtenir un exemple, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="35a04-116">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="35a04-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="35a04-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="35a04-118">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="35a04-118">Minimum supported client</span></span> | <span data-ttu-id="35a04-119">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="35a04-119">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="35a04-120">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="35a04-120">Minimum supported server</span></span> | <span data-ttu-id="35a04-121">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="35a04-121">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="35a04-122">En-tête</span><span class="sxs-lookup"><span data-stu-id="35a04-122">Header</span></span> | <span data-ttu-id="35a04-123">WinConTypes. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="35a04-123">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="35a04-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35a04-124">See also</span></span>

[<span data-ttu-id="35a04-125">**\_informations sur la police de la console \_**</span><span class="sxs-lookup"><span data-stu-id="35a04-125">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="35a04-126">**\_ \_ informations sur la mémoire tampon d’écran de la console \_**</span><span class="sxs-lookup"><span data-stu-id="35a04-126">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="35a04-127">**\_informations sur la sélection de la console \_**</span><span class="sxs-lookup"><span data-stu-id="35a04-127">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)

[<span data-ttu-id="35a04-128">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="35a04-128">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="35a04-129">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="35a04-129">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="35a04-130">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="35a04-130">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)

[<span data-ttu-id="35a04-131">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="35a04-131">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="35a04-132">**\_enregistrement d’événement de souris \_**</span><span class="sxs-lookup"><span data-stu-id="35a04-132">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="35a04-133">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="35a04-133">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="35a04-134">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="35a04-134">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="35a04-135">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="35a04-135">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="35a04-136">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="35a04-136">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="35a04-137">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="35a04-137">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="35a04-138">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="35a04-138">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)

[<span data-ttu-id="35a04-139">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="35a04-139">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="35a04-140">**enregistrement de la taille de la \_ mémoire tampon Windows \_ \_**</span><span class="sxs-lookup"><span data-stu-id="35a04-140">**WINDOW\_BUFFER\_SIZE\_RECORD**</span></span>](window-buffer-size-record-str.md)

[<span data-ttu-id="35a04-141">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="35a04-141">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="35a04-142">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="35a04-142">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="35a04-143">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="35a04-143">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
