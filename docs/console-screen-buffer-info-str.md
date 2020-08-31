---
title: Structure CONSOLE_SCREEN_BUFFER_INFO
description: Consultez les informations de référence sur la structure CONSOLE_SCREEN_BUFFER_INFO, qui contient des informations sur une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFO
- wincon/CONSOLE_SCREEN_BUFFER_INFO
- CONSOLE_SCREEN_BUFFER_INFO
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFO
- wincon/PCONSOLE_SCREEN_BUFFER_INFO
- PCONSOLE_SCREEN_BUFFER_INFO
MS-HAID:
- '\_win32\_console\_screen\_buffer\_info\_str'
- base.console\_screen\_buffer\_info\_str
- consoles.console\_screen\_buffer\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 586b3e0f-2f6b-4a03-b8e4-602a892be56d
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4089541ddac93f5be61b7a21d5aa88a88061b261
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059296"
---
# <a name="console_screen_buffer_info-structure"></a><span data-ttu-id="0762a-104">\_Structure des \_ informations de mémoire tampon de l’écran de la console \_</span><span class="sxs-lookup"><span data-stu-id="0762a-104">CONSOLE\_SCREEN\_BUFFER\_INFO structure</span></span>


<span data-ttu-id="0762a-105">Contient des informations sur une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="0762a-105">Contains information about a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="0762a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0762a-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFO {
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
} CONSOLE_SCREEN_BUFFER_INFO;
```

<a name="members"></a><span data-ttu-id="0762a-107">Membres</span><span class="sxs-lookup"><span data-stu-id="0762a-107">Members</span></span>
-------

<span data-ttu-id="0762a-108">**dwSize nul**</span><span class="sxs-lookup"><span data-stu-id="0762a-108">**dwSize**</span></span>  
<span data-ttu-id="0762a-109">Structure de [**repère**](coord-str.md) qui contient la taille de la mémoire tampon d’écran de la console, dans les colonnes de caractères et les lignes.</span><span class="sxs-lookup"><span data-stu-id="0762a-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="0762a-110">**dwCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="0762a-110">**dwCursorPosition**</span></span>  
<span data-ttu-id="0762a-111">Structure de [**repère**](coord-str.md) qui contient les coordonnées de colonne et de ligne du curseur dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="0762a-111">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="0762a-112">**wAttributes**</span><span class="sxs-lookup"><span data-stu-id="0762a-112">**wAttributes**</span></span>  
<span data-ttu-id="0762a-113">Attributs des caractères écrits dans une mémoire tampon d’écran par les fonctions [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) et [**WriteConsole**](writeconsole.md) , ou répercutés dans une mémoire tampon d’écran par les fonctions [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="0762a-113">The attributes of the characters written to a screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="0762a-114">Pour plus d’informations, consultez [attributs de caractères](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="0762a-114">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="0762a-115">**srWindow**</span><span class="sxs-lookup"><span data-stu-id="0762a-115">**srWindow**</span></span>  
<span data-ttu-id="0762a-116">[**Petite structure \_ Rect**](small-rect-str.md) qui contient les coordonnées de la mémoire tampon d’écran de la console des angles supérieur gauche et inférieur droit de la fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="0762a-116">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="0762a-117">**dwMaximumWindowSize**</span><span class="sxs-lookup"><span data-stu-id="0762a-117">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="0762a-118">Structure de [**repère**](coord-str.md) qui contient la taille maximale de la fenêtre de console, en colonnes de caractères et en lignes, en fonction de la taille et de la police de la mémoire tampon d’écran actuelle et de la taille de l’écran.</span><span class="sxs-lookup"><span data-stu-id="0762a-118">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

<a name="examples"></a><span data-ttu-id="0762a-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="0762a-119">Examples</span></span>
--------

<span data-ttu-id="0762a-120">Pour obtenir un exemple, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="0762a-120">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="0762a-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0762a-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="0762a-122">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="0762a-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="0762a-123">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="0762a-123">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0762a-124">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="0762a-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="0762a-125">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="0762a-125">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0762a-126">En-tête</span><span class="sxs-lookup"><span data-stu-id="0762a-126">Header</span></span></p></td>
<td><span data-ttu-id="0762a-127">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0762a-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="0762a-128"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0762a-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="0762a-129">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="0762a-129">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="0762a-130">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="0762a-130">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="0762a-131">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="0762a-131">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="0762a-132">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="0762a-132">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="0762a-133">**PETIT \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="0762a-133">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="0762a-134">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="0762a-134">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="0762a-135">**Appel**</span><span class="sxs-lookup"><span data-stu-id="0762a-135">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




