---
title: CONSOLE_SCREEN_BUFFER_INFOEX, structure
description: Consultez les informations de référence sur la structure CONSOLE_SCREEN_BUFFER_INFOEX, qui contient des informations étendues sur une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: baf6eeb51cbae5ce410c190852c22ae237e6a367
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038347"
---
# <a name="console_screen_buffer_infoex-structure"></a><span data-ttu-id="dc269-104">\_Structure INFOEX de la \_ mémoire tampon d’écran de la console \_</span><span class="sxs-lookup"><span data-stu-id="dc269-104">CONSOLE\_SCREEN\_BUFFER\_INFOEX structure</span></span>

<span data-ttu-id="dc269-105">Contient des informations étendues sur une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="dc269-105">Contains extended information about a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="dc269-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc269-106">Syntax</span></span>

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

## <a name="members"></a><span data-ttu-id="dc269-107">Membres</span><span class="sxs-lookup"><span data-stu-id="dc269-107">Members</span></span>

<span data-ttu-id="dc269-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="dc269-108">**cbSize**</span></span>  
<span data-ttu-id="dc269-109">Taille de cette structure, en octets.</span><span class="sxs-lookup"><span data-stu-id="dc269-109">The size of this structure, in bytes.</span></span>

<span data-ttu-id="dc269-110">**dwSize nul**</span><span class="sxs-lookup"><span data-stu-id="dc269-110">**dwSize**</span></span>  
<span data-ttu-id="dc269-111">Structure de [**repère**](coord-str.md) qui contient la taille de la mémoire tampon d’écran de la console, dans les colonnes de caractères et les lignes.</span><span class="sxs-lookup"><span data-stu-id="dc269-111">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="dc269-112">**dwCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="dc269-112">**dwCursorPosition**</span></span>  
<span data-ttu-id="dc269-113">Structure de [**repère**](coord-str.md) qui contient les coordonnées de colonne et de ligne du curseur dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="dc269-113">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="dc269-114">**wAttributes**</span><span class="sxs-lookup"><span data-stu-id="dc269-114">**wAttributes**</span></span>  
<span data-ttu-id="dc269-115">Attributs des caractères écrits dans une mémoire tampon d’écran par les fonctions [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) et [**WriteConsole**](writeconsole.md) , ou répercutés dans une mémoire tampon d’écran par les fonctions [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="dc269-115">The attributes of the characters written to a screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="dc269-116">Pour plus d’informations, consultez [attributs de caractères](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="dc269-116">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="dc269-117">**srWindow**</span><span class="sxs-lookup"><span data-stu-id="dc269-117">**srWindow**</span></span>  
<span data-ttu-id="dc269-118">[**Petite structure \_ Rect**](small-rect-str.md) qui contient les coordonnées de la mémoire tampon d’écran de la console des angles supérieur gauche et inférieur droit de la fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="dc269-118">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="dc269-119">**dwMaximumWindowSize**</span><span class="sxs-lookup"><span data-stu-id="dc269-119">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="dc269-120">Structure de [**repère**](coord-str.md) qui contient la taille maximale de la fenêtre de console, en colonnes de caractères et en lignes, en fonction de la taille et de la police de la mémoire tampon d’écran actuelle et de la taille de l’écran.</span><span class="sxs-lookup"><span data-stu-id="dc269-120">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

<span data-ttu-id="dc269-121">**wPopupAttributes**</span><span class="sxs-lookup"><span data-stu-id="dc269-121">**wPopupAttributes**</span></span>  
<span data-ttu-id="dc269-122">Attribut de remplissage des fenêtres contextuelles de la console.</span><span class="sxs-lookup"><span data-stu-id="dc269-122">The fill attribute for console pop-ups.</span></span>

<span data-ttu-id="dc269-123">**bFullscreenSupported**</span><span class="sxs-lookup"><span data-stu-id="dc269-123">**bFullscreenSupported**</span></span>  
<span data-ttu-id="dc269-124">Si ce membre est `TRUE` , le mode plein écran est pris en charge ; sinon, il ne l’est pas.</span><span class="sxs-lookup"><span data-stu-id="dc269-124">If this member is `TRUE`, full-screen mode is supported; otherwise, it is not.</span></span> <span data-ttu-id="dc269-125">Ce sera toujours `FALSE` le cas pour les systèmes après Windows Vista avec le [modèle de pilote WDDM](https://docs.microsoft.com/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) , car l’accès direct VGA à l’analyse n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="dc269-125">This will always be `FALSE` for systems after Windows Vista with the [WDDM driver model](https://docs.microsoft.com/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) as true direct VGA access to the monitor is no longer available.</span></span>

<span data-ttu-id="dc269-126">**ColorTable**</span><span class="sxs-lookup"><span data-stu-id="dc269-126">**ColorTable**</span></span>  
<span data-ttu-id="dc269-127">Tableau de valeurs [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) qui décrivent les paramètres de couleur de la console.</span><span class="sxs-lookup"><span data-stu-id="dc269-127">An array of [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) values that describe the console's color settings.</span></span>

## <a name="requirements"></a><span data-ttu-id="dc269-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dc269-128">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="dc269-129">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="dc269-129">Minimum supported client</span></span> | <span data-ttu-id="dc269-130">Applications de \[ Bureau Windows Vista uniquement\]</span><span class="sxs-lookup"><span data-stu-id="dc269-130">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="dc269-131">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="dc269-131">Minimum supported server</span></span> | <span data-ttu-id="dc269-132">Applications de bureau Windows Server 2008 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="dc269-132">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="dc269-133">En-tête</span><span class="sxs-lookup"><span data-stu-id="dc269-133">Header</span></span> | <span data-ttu-id="dc269-134">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="dc269-134">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="dc269-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc269-135">See also</span></span>

[<span data-ttu-id="dc269-136">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="dc269-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="dc269-137">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="dc269-137">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)

[<span data-ttu-id="dc269-138">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="dc269-138">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)

[<span data-ttu-id="dc269-139">**PETIT \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="dc269-139">**SMALL\_RECT**</span></span>](small-rect-str.md)
