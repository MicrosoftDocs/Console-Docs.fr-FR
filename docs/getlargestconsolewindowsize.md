---
title: GetLargestConsoleWindowSize fonction)
description: Récupère la taille de la plus grande fenêtre de console possible, en fonction de la police actuelle et de la taille de l’affichage.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/GetLargestConsoleWindowSize
- wincon/GetLargestConsoleWindowSize
- GetLargestConsoleWindowSize
MS-HAID:
- '\_win32\_getlargestconsolewindowsize'
- base.getlargestconsolewindowsize
- consoles.getlargestconsolewindowsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3e5897f3-4987-4a82-ab19-06c0b231ba67
topic_type:
- apiref
api_name:
- GetLargestConsoleWindowSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: ddaa4716886fccaaa87e86362719020eb2408765
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037837"
---
# <a name="getlargestconsolewindowsize-function"></a><span data-ttu-id="20edb-104">GetLargestConsoleWindowSize fonction)</span><span class="sxs-lookup"><span data-stu-id="20edb-104">GetLargestConsoleWindowSize function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="20edb-105">Récupère la taille de la plus grande fenêtre de console possible, en fonction de la police actuelle et de la taille de l’affichage.</span><span class="sxs-lookup"><span data-stu-id="20edb-105">Retrieves the size of the largest possible console window, based on the current font and the size of the display.</span></span>

## <a name="syntax"></a><span data-ttu-id="20edb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20edb-106">Syntax</span></span>

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a><span data-ttu-id="20edb-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="20edb-107">Parameters</span></span>

<span data-ttu-id="20edb-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="20edb-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="20edb-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="20edb-109">A handle to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="20edb-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="20edb-110">Return value</span></span>

<span data-ttu-id="20edb-111">Si la fonction est réussie, la valeur de retour est une structure de [**repère**](coord-str.md) qui spécifie le nombre de colonnes de cellule de caractères (membre **X** ) et de lignes (membre **Y** ) dans la plus grande fenêtre de console possible.</span><span class="sxs-lookup"><span data-stu-id="20edb-111">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that specifies the number of character cell columns ( **X** member) and rows ( **Y** member) in the largest possible console window.</span></span> <span data-ttu-id="20edb-112">Sinon, les membres de la structure sont nuls.</span><span class="sxs-lookup"><span data-stu-id="20edb-112">Otherwise, the members of the structure are zero.</span></span>

<span data-ttu-id="20edb-113">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="20edb-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="20edb-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="20edb-114">Remarks</span></span>

<span data-ttu-id="20edb-115">La fonction ne prend pas en compte la taille de la mémoire tampon d’écran de la console, ce qui signifie que la taille de fenêtre retournée peut être supérieure à la taille de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="20edb-115">The function does not take into consideration the size of the console screen buffer, which means that the window size returned may be larger than the size of the console screen buffer.</span></span> <span data-ttu-id="20edb-116">La fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) peut être utilisée pour déterminer la taille maximale de la fenêtre de console, en fonction de la taille actuelle de la mémoire tampon de l’écran, de la police actuelle et de la taille d’affichage.</span><span class="sxs-lookup"><span data-stu-id="20edb-116">The [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function can be used to determine the maximum size of the console window, given the current screen buffer size, the current font, and the display size.</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="20edb-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="20edb-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="20edb-118">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="20edb-118">Minimum supported client</span></span> | <span data-ttu-id="20edb-119">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="20edb-119">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="20edb-120">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="20edb-120">Minimum supported server</span></span> | <span data-ttu-id="20edb-121">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="20edb-121">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="20edb-122">En-tête</span><span class="sxs-lookup"><span data-stu-id="20edb-122">Header</span></span> | <span data-ttu-id="20edb-123">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="20edb-123">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="20edb-124">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="20edb-124">Library</span></span> | <span data-ttu-id="20edb-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="20edb-125">Kernel32.lib</span></span> |
| <span data-ttu-id="20edb-126">DLL</span><span class="sxs-lookup"><span data-stu-id="20edb-126">DLL</span></span> | <span data-ttu-id="20edb-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="20edb-127">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="20edb-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20edb-128">See also</span></span>

[<span data-ttu-id="20edb-129">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="20edb-129">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="20edb-130">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="20edb-130">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="20edb-131">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="20edb-131">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="20edb-132">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="20edb-132">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="20edb-133">Taille de la mémoire tampon de la fenêtre et de l’écran</span><span class="sxs-lookup"><span data-stu-id="20edb-133">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)
