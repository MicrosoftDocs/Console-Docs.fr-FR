---
title: COORD, structure
description: Définit les coordonnées d’une cellule de caractère dans une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: c29594cbddd69ae8ca6d3f958acd0eeb3cb60e9b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059240"
---
# <a name="coord-structure"></a><span data-ttu-id="48f62-104">COORD, structure</span><span class="sxs-lookup"><span data-stu-id="48f62-104">COORD structure</span></span>


<span data-ttu-id="48f62-105">Définit les coordonnées d’une cellule de caractère dans une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="48f62-105">Defines the coordinates of a character cell in a console screen buffer.</span></span> <span data-ttu-id="48f62-106">L’origine du système de coordonnées (0,0) se trouve dans la cellule supérieure gauche de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="48f62-106">The origin of the coordinate system (0,0) is at the top, left cell of the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="48f62-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48f62-107">Syntax</span></span>
------

```C
typedef struct _COORD {
  SHORT X;
  SHORT Y;
} COORD, *PCOORD;
```

<a name="members"></a><span data-ttu-id="48f62-108">Membres</span><span class="sxs-lookup"><span data-stu-id="48f62-108">Members</span></span>
-------

<span data-ttu-id="48f62-109">**X**</span><span class="sxs-lookup"><span data-stu-id="48f62-109">**X**</span></span>  
<span data-ttu-id="48f62-110">Valeur de la coordonnée ou de la colonne horizontale.</span><span class="sxs-lookup"><span data-stu-id="48f62-110">The horizontal coordinate or column value.</span></span> <span data-ttu-id="48f62-111">Les unités dépendent de l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="48f62-111">The units depend on the function call.</span></span>

<span data-ttu-id="48f62-112">**O**</span><span class="sxs-lookup"><span data-stu-id="48f62-112">**Y**</span></span>  
<span data-ttu-id="48f62-113">Valeur de la coordonnée ou de la ligne verticale.</span><span class="sxs-lookup"><span data-stu-id="48f62-113">The vertical coordinate or row value.</span></span> <span data-ttu-id="48f62-114">Les unités dépendent de l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="48f62-114">The units depend on the function call.</span></span>

<a name="examples"></a><span data-ttu-id="48f62-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="48f62-115">Examples</span></span>
--------

<span data-ttu-id="48f62-116">Pour obtenir un exemple, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="48f62-116">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="48f62-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="48f62-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="48f62-118">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="48f62-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="48f62-119">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="48f62-119">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="48f62-120">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="48f62-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="48f62-121">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="48f62-121">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="48f62-122">En-tête</span><span class="sxs-lookup"><span data-stu-id="48f62-122">Header</span></span></p></td>
<td><span data-ttu-id="48f62-123">WinConTypes. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="48f62-123">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="48f62-124"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48f62-124"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="48f62-125">**\_informations sur la police de la console \_**</span><span class="sxs-lookup"><span data-stu-id="48f62-125">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="48f62-126">**\_ \_ informations sur la mémoire tampon d’écran de la console \_**</span><span class="sxs-lookup"><span data-stu-id="48f62-126">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="48f62-127">**\_informations sur la sélection de la console \_**</span><span class="sxs-lookup"><span data-stu-id="48f62-127">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)

[<span data-ttu-id="48f62-128">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="48f62-128">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="48f62-129">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="48f62-129">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="48f62-130">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="48f62-130">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)

[<span data-ttu-id="48f62-131">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="48f62-131">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="48f62-132">**\_enregistrement d’événement de souris \_**</span><span class="sxs-lookup"><span data-stu-id="48f62-132">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="48f62-133">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="48f62-133">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="48f62-134">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="48f62-134">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="48f62-135">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="48f62-135">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="48f62-136">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="48f62-136">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="48f62-137">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="48f62-137">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="48f62-138">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="48f62-138">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)

[<span data-ttu-id="48f62-139">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="48f62-139">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="48f62-140">**enregistrement de la taille de la \_ mémoire tampon Windows \_ \_**</span><span class="sxs-lookup"><span data-stu-id="48f62-140">**WINDOW\_BUFFER\_SIZE\_RECORD**</span></span>](window-buffer-size-record-str.md)

[<span data-ttu-id="48f62-141">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="48f62-141">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="48f62-142">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="48f62-142">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="48f62-143">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="48f62-143">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




