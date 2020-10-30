---
title: CONSOLE_SCREEN_BUFFER_INFO, structure
description: Consultez les informations de référence sur la structure CONSOLE_SCREEN_BUFFER_INFO, qui contient des informations sur une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8b3a739a9f66e25687b60a3450c9381822c16e53
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039177"
---
# <a name="console_screen_buffer_info-structure"></a><span data-ttu-id="9665f-104">\_Structure des \_ informations de mémoire tampon de l’écran de la console \_</span><span class="sxs-lookup"><span data-stu-id="9665f-104">CONSOLE\_SCREEN\_BUFFER\_INFO structure</span></span>

<span data-ttu-id="9665f-105">Contient des informations sur une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="9665f-105">Contains information about a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="9665f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9665f-106">Syntax</span></span>

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFO {
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
} CONSOLE_SCREEN_BUFFER_INFO;
```

## <a name="members"></a><span data-ttu-id="9665f-107">Membres</span><span class="sxs-lookup"><span data-stu-id="9665f-107">Members</span></span>

<span data-ttu-id="9665f-108">**dwSize nul**</span><span class="sxs-lookup"><span data-stu-id="9665f-108">**dwSize**</span></span>  
<span data-ttu-id="9665f-109">Structure de [**repère**](coord-str.md) qui contient la taille de la mémoire tampon d’écran de la console, dans les colonnes de caractères et les lignes.</span><span class="sxs-lookup"><span data-stu-id="9665f-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="9665f-110">**dwCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="9665f-110">**dwCursorPosition**</span></span>  
<span data-ttu-id="9665f-111">Structure de [**repère**](coord-str.md) qui contient les coordonnées de colonne et de ligne du curseur dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="9665f-111">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="9665f-112">**wAttributes**</span><span class="sxs-lookup"><span data-stu-id="9665f-112">**wAttributes**</span></span>  
<span data-ttu-id="9665f-113">Attributs des caractères écrits dans une mémoire tampon d’écran par les fonctions [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) et [**WriteConsole**](writeconsole.md) , ou répercutés dans une mémoire tampon d’écran par les fonctions [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="9665f-113">The attributes of the characters written to a screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="9665f-114">Pour plus d’informations, consultez [attributs de caractères](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="9665f-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="9665f-115">**srWindow**</span><span class="sxs-lookup"><span data-stu-id="9665f-115">**srWindow**</span></span>  
<span data-ttu-id="9665f-116">[**Petite structure \_ Rect**](small-rect-str.md) qui contient les coordonnées de la mémoire tampon d’écran de la console des angles supérieur gauche et inférieur droit de la fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="9665f-116">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="9665f-117">**dwMaximumWindowSize**</span><span class="sxs-lookup"><span data-stu-id="9665f-117">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="9665f-118">Structure de [**repère**](coord-str.md) qui contient la taille maximale de la fenêtre de console, en colonnes de caractères et en lignes, en fonction de la taille et de la police de la mémoire tampon d’écran actuelle et de la taille de l’écran.</span><span class="sxs-lookup"><span data-stu-id="9665f-118">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

## <a name="examples"></a><span data-ttu-id="9665f-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="9665f-119">Examples</span></span>

<span data-ttu-id="9665f-120">Pour obtenir un exemple, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="9665f-120">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="9665f-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9665f-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="9665f-122">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="9665f-122">Minimum supported client</span></span> | <span data-ttu-id="9665f-123">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="9665f-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="9665f-124">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="9665f-124">Minimum supported server</span></span> | <span data-ttu-id="9665f-125">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="9665f-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="9665f-126">En-tête</span><span class="sxs-lookup"><span data-stu-id="9665f-126">Header</span></span> | <span data-ttu-id="9665f-127">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9665f-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="9665f-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9665f-128">See also</span></span>

[<span data-ttu-id="9665f-129">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="9665f-129">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="9665f-130">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="9665f-130">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="9665f-131">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="9665f-131">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="9665f-132">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="9665f-132">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="9665f-133">**PETIT \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="9665f-133">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="9665f-134">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="9665f-134">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="9665f-135">**Appel**</span><span class="sxs-lookup"><span data-stu-id="9665f-135">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
