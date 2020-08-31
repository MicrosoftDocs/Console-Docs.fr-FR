---
title: Structure CONSOLE_SCREEN_BUFFER_INFOEX
description: Consultez les informations de référence sur la structure CONSOLE_SCREEN_BUFFER_INFOEX, qui contient des informations étendues sur une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFOEX
- wincon/CONSOLE_SCREEN_BUFFER_INFOEX
- CONSOLE_SCREEN_BUFFER_INFOEX
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFOEX
- wincon/PCONSOLE_SCREEN_BUFFER_INFOEX
- PCONSOLE_SCREEN_BUFFER_INFOEX
MS-HAID:
- base.console\_screen\_buffer\_infoex
- consoles.console\_screen\_buffer\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6ed40df3-063d-41c9-8637-510c95104603
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFOEX
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 010120f2d925727e37bd72905bab4536db073371
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059293"
---
# <a name="console_screen_buffer_infoex-structure"></a><span data-ttu-id="3c629-104">\_Structure INFOEX de la \_ mémoire tampon d’écran de la console \_</span><span class="sxs-lookup"><span data-stu-id="3c629-104">CONSOLE\_SCREEN\_BUFFER\_INFOEX structure</span></span>


<span data-ttu-id="3c629-105">Contient des informations étendues sur une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="3c629-105">Contains extended information about a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="3c629-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c629-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

<a name="members"></a><span data-ttu-id="3c629-107">Membres</span><span class="sxs-lookup"><span data-stu-id="3c629-107">Members</span></span>
-------

<span data-ttu-id="3c629-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="3c629-108">**cbSize**</span></span>  
<span data-ttu-id="3c629-109">Taille de cette structure, en octets.</span><span class="sxs-lookup"><span data-stu-id="3c629-109">The size of this structure, in bytes.</span></span>

<span data-ttu-id="3c629-110">**dwSize nul**</span><span class="sxs-lookup"><span data-stu-id="3c629-110">**dwSize**</span></span>  
<span data-ttu-id="3c629-111">Structure de [**repère**](coord-str.md) qui contient la taille de la mémoire tampon d’écran de la console, dans les colonnes de caractères et les lignes.</span><span class="sxs-lookup"><span data-stu-id="3c629-111">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="3c629-112">**dwCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="3c629-112">**dwCursorPosition**</span></span>  
<span data-ttu-id="3c629-113">Structure de [**repère**](coord-str.md) qui contient les coordonnées de colonne et de ligne du curseur dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="3c629-113">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="3c629-114">**wAttributes**</span><span class="sxs-lookup"><span data-stu-id="3c629-114">**wAttributes**</span></span>  
<span data-ttu-id="3c629-115">Attributs des caractères écrits dans une mémoire tampon d’écran par les fonctions [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) et [**WriteConsole**](writeconsole.md) , ou répercutés dans une mémoire tampon d’écran par les fonctions [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="3c629-115">The attributes of the characters written to a screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="3c629-116">Pour plus d’informations, consultez [attributs de caractères](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="3c629-116">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="3c629-117">**srWindow**</span><span class="sxs-lookup"><span data-stu-id="3c629-117">**srWindow**</span></span>  
<span data-ttu-id="3c629-118">[**Petite structure \_ Rect**](small-rect-str.md) qui contient les coordonnées de la mémoire tampon d’écran de la console des angles supérieur gauche et inférieur droit de la fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="3c629-118">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="3c629-119">**dwMaximumWindowSize**</span><span class="sxs-lookup"><span data-stu-id="3c629-119">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="3c629-120">Structure de [**repère**](coord-str.md) qui contient la taille maximale de la fenêtre de console, en colonnes de caractères et en lignes, en fonction de la taille et de la police de la mémoire tampon d’écran actuelle et de la taille de l’écran.</span><span class="sxs-lookup"><span data-stu-id="3c629-120">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

<span data-ttu-id="3c629-121">**wPopupAttributes**</span><span class="sxs-lookup"><span data-stu-id="3c629-121">**wPopupAttributes**</span></span>  
<span data-ttu-id="3c629-122">Attribut de remplissage des fenêtres contextuelles de la console.</span><span class="sxs-lookup"><span data-stu-id="3c629-122">The fill attribute for console pop-ups.</span></span>

<span data-ttu-id="3c629-123">**bFullscreenSupported**</span><span class="sxs-lookup"><span data-stu-id="3c629-123">**bFullscreenSupported**</span></span>  
<span data-ttu-id="3c629-124">Si ce membre a la valeur TRUE, le mode plein écran est pris en charge ; Sinon, ce n’est pas le cas.</span><span class="sxs-lookup"><span data-stu-id="3c629-124">If this member is TRUE, full-screen mode is supported; otherwise, it is not.</span></span>

<span data-ttu-id="3c629-125">**ColorTable**</span><span class="sxs-lookup"><span data-stu-id="3c629-125">**ColorTable**</span></span>  
<span data-ttu-id="3c629-126">Tableau de valeurs [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) qui décrivent les paramètres de couleur de la console.</span><span class="sxs-lookup"><span data-stu-id="3c629-126">An array of [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) values that describe the console's color settings.</span></span>

<a name="requirements"></a><span data-ttu-id="3c629-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3c629-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="3c629-128">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="3c629-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="3c629-129">Windows Vista [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="3c629-129">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3c629-130">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="3c629-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="3c629-131">Windows Server 2008 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="3c629-131">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3c629-132">En-tête</span><span class="sxs-lookup"><span data-stu-id="3c629-132">Header</span></span></p></td>
<td><span data-ttu-id="3c629-133">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="3c629-133">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="3c629-134"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c629-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="3c629-135">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="3c629-135">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="3c629-136">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="3c629-136">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)

[<span data-ttu-id="3c629-137">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="3c629-137">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)

[<span data-ttu-id="3c629-138">**PETIT \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="3c629-138">**SMALL\_RECT**</span></span>](small-rect-str.md)

 

 




