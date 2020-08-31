---
title: GetLargestConsoleWindowSize fonction)
description: Récupère la taille de la plus grande fenêtre de console possible, en fonction de la police actuelle et de la taille de l’affichage.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
ms.openlocfilehash: 086c09b00ba15ad3e1922655fbd9b5f39d872d41
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059113"
---
# <a name="getlargestconsolewindowsize-function"></a><span data-ttu-id="2ca0a-104">GetLargestConsoleWindowSize fonction)</span><span class="sxs-lookup"><span data-stu-id="2ca0a-104">GetLargestConsoleWindowSize function</span></span>


<span data-ttu-id="2ca0a-105">Récupère la taille de la plus grande fenêtre de console possible, en fonction de la police actuelle et de la taille de l’affichage.</span><span class="sxs-lookup"><span data-stu-id="2ca0a-105">Retrieves the size of the largest possible console window, based on the current font and the size of the display.</span></span>

<a name="syntax"></a><span data-ttu-id="2ca0a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ca0a-106">Syntax</span></span>
------

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

<a name="parameters"></a><span data-ttu-id="2ca0a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca0a-107">Parameters</span></span>
----------

<span data-ttu-id="2ca0a-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="2ca0a-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="2ca0a-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="2ca0a-109">A handle to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="2ca0a-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="2ca0a-110">Return value</span></span>
------------

<span data-ttu-id="2ca0a-111">Si la fonction est réussie, la valeur de retour est une structure de [**repère**](coord-str.md) qui spécifie le nombre de colonnes de cellule de caractères (membre**X** ) et de lignes (membre**Y** ) dans la plus grande fenêtre de console possible.</span><span class="sxs-lookup"><span data-stu-id="2ca0a-111">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that specifies the number of character cell columns (**X** member) and rows (**Y** member) in the largest possible console window.</span></span> <span data-ttu-id="2ca0a-112">Sinon, les membres de la structure sont nuls.</span><span class="sxs-lookup"><span data-stu-id="2ca0a-112">Otherwise, the members of the structure are zero.</span></span>

<span data-ttu-id="2ca0a-113">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="2ca0a-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="2ca0a-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="2ca0a-114">Remarks</span></span>
-------

<span data-ttu-id="2ca0a-115">La fonction ne prend pas en compte la taille de la mémoire tampon d’écran de la console, ce qui signifie que la taille de fenêtre retournée peut être supérieure à la taille de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="2ca0a-115">The function does not take into consideration the size of the console screen buffer, which means that the window size returned may be larger than the size of the console screen buffer.</span></span> <span data-ttu-id="2ca0a-116">La fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) peut être utilisée pour déterminer la taille maximale de la fenêtre de console, en fonction de la taille actuelle de la mémoire tampon de l’écran, de la police actuelle et de la taille d’affichage.</span><span class="sxs-lookup"><span data-stu-id="2ca0a-116">The [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function can be used to determine the maximum size of the console window, given the current screen buffer size, the current font, and the display size.</span></span>

<a name="requirements"></a><span data-ttu-id="2ca0a-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2ca0a-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="2ca0a-118">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="2ca0a-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="2ca0a-119">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="2ca0a-119">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2ca0a-120">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="2ca0a-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="2ca0a-121">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="2ca0a-121">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2ca0a-122">En-tête</span><span class="sxs-lookup"><span data-stu-id="2ca0a-122">Header</span></span></p></td>
<td><span data-ttu-id="2ca0a-123">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2ca0a-123">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2ca0a-124">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="2ca0a-124">Library</span></span></p></td>
<td><span data-ttu-id="2ca0a-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="2ca0a-125">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2ca0a-126">DLL</span><span class="sxs-lookup"><span data-stu-id="2ca0a-126">DLL</span></span></p></td>
<td><span data-ttu-id="2ca0a-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2ca0a-127">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="2ca0a-128"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ca0a-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="2ca0a-129">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="2ca0a-129">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2ca0a-130">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="2ca0a-130">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="2ca0a-131">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="2ca0a-131">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="2ca0a-132">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="2ca0a-132">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="2ca0a-133">Taille de la mémoire tampon de la fenêtre et de l’écran</span><span class="sxs-lookup"><span data-stu-id="2ca0a-133">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)

 

 




