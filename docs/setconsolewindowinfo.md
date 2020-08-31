---
title: SetConsoleWindowInfo fonction)
description: Définit la taille actuelle et la position de la fenêtre d’une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/SetConsoleWindowInfo
- wincon/SetConsoleWindowInfo
- SetConsoleWindowInfo
MS-HAID:
- '\_win32\_setconsolewindowinfo'
- base.setconsolewindowinfo
- consoles.setconsolewindowinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad16a8fe-ca91-41d6-93b1-8cce6d54b1da
topic_type:
- apiref
api_name:
- SetConsoleWindowInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: ae09434a1fc67902d2160f4e66890f4392eac3f8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059280"
---
# <a name="setconsolewindowinfo-function"></a><span data-ttu-id="59da3-104">SetConsoleWindowInfo fonction)</span><span class="sxs-lookup"><span data-stu-id="59da3-104">SetConsoleWindowInfo function</span></span>


<span data-ttu-id="59da3-105">Définit la taille actuelle et la position de la fenêtre d’une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="59da3-105">Sets the current size and position of a console screen buffer's window.</span></span>

<a name="syntax"></a><span data-ttu-id="59da3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59da3-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleWindowInfo(
  _In_       HANDLE     hConsoleOutput,
  _In_       BOOL       bAbsolute,
  _In_ const SMALL_RECT *lpConsoleWindow
);
```

<a name="parameters"></a><span data-ttu-id="59da3-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="59da3-107">Parameters</span></span>
----------

<span data-ttu-id="59da3-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="59da3-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="59da3-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="59da3-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="59da3-110">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="59da3-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="59da3-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="59da3-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="59da3-112">*bAbsolute* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="59da3-112">*bAbsolute* \[in\]</span></span>  
<span data-ttu-id="59da3-113">Si ce paramètre a la **valeur true**, les coordonnées spécifient les nouveaux angles supérieur gauche et inférieur droit de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="59da3-113">If this parameter is **TRUE**, the coordinates specify the new upper-left and lower-right corners of the window.</span></span> <span data-ttu-id="59da3-114">Si la **valeur est false**, les coordonnées sont relatives aux coordonnées de l’angle de la fenêtre active.</span><span class="sxs-lookup"><span data-stu-id="59da3-114">If it is **FALSE**, the coordinates are relative to the current window-corner coordinates.</span></span>

<span data-ttu-id="59da3-115">*lpConsoleWindow* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="59da3-115">*lpConsoleWindow* \[in\]</span></span>  
<span data-ttu-id="59da3-116">Pointeur vers une [**petite structure \_ Rect**](small-rect-str.md) qui spécifie les nouveaux angles supérieur gauche et inférieur droit de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="59da3-116">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure that specifies the new upper-left and lower-right corners of the window.</span></span>

<a name="return-value"></a><span data-ttu-id="59da3-117">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="59da3-117">Return value</span></span>
------------

<span data-ttu-id="59da3-118">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="59da3-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="59da3-119">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="59da3-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="59da3-120">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="59da3-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="59da3-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="59da3-121">Remarks</span></span>
-------

<span data-ttu-id="59da3-122">La fonction échoue si le rectangle de fenêtre spécifié s’étend au-delà des limites de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="59da3-122">The function fails if the specified window rectangle extends beyond the boundaries of the console screen buffer.</span></span> <span data-ttu-id="59da3-123">Cela signifie que les membres **supérieur** et **gauche** du rectangle *lpConsoleWindow* (ou les coordonnées supérieure et gauche CALCULées, si *bAbsolute* est false) ne peuvent pas être inférieurs à zéro.</span><span class="sxs-lookup"><span data-stu-id="59da3-123">This means that the **Top** and **Left** members of the *lpConsoleWindow* rectangle (or the calculated top and left coordinates, if *bAbsolute* is FALSE) cannot be less than zero.</span></span> <span data-ttu-id="59da3-124">De même, les membres **inférieurs** et **droits** (ou les coordonnées en bas et à droite calculés) ne peuvent pas être supérieurs à (hauteur de la mémoire tampon d’écran – 1) et (largeur de la mémoire tampon de l’écran – 1), respectivement.</span><span class="sxs-lookup"><span data-stu-id="59da3-124">Similarly, the **Bottom** and **Right** members (or the calculated bottom and right coordinates) cannot be greater than (screen buffer height – 1) and (screen buffer width – 1), respectively.</span></span> <span data-ttu-id="59da3-125">La fonction échoue également si le membre de **droite** (ou la coordonnée droite calculée) est inférieur ou égal au membre de **gauche** (ou la coordonnée gauche calculée) ou si le membre **inférieur** (ou la coordonnée inférieure calculée) est inférieur ou égal au membre **supérieur** (ou coordonnée supérieure calculée).</span><span class="sxs-lookup"><span data-stu-id="59da3-125">The function also fails if the **Right** member (or calculated right coordinate) is less than or equal to the **Left** member (or calculated left coordinate) or if the **Bottom** member (or calculated bottom coordinate) is less than or equal to the **Top** member (or calculated top coordinate).</span></span>

<span data-ttu-id="59da3-126">Pour les consoles avec plus d’une mémoire tampon d’écran, la modification de l’emplacement de la fenêtre pour une mémoire tampon d’écran n’affecte pas les emplacements des fenêtres des autres mémoires tampons d’écran.</span><span class="sxs-lookup"><span data-stu-id="59da3-126">For consoles with more than one screen buffer, changing the window location for one screen buffer does not affect the window locations of the other screen buffers.</span></span>

<span data-ttu-id="59da3-127">Pour déterminer la taille actuelle et la position de la fenêtre d’une mémoire tampon d’écran, utilisez la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="59da3-127">To determine the current size and position of a screen buffer's window, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span> <span data-ttu-id="59da3-128">Cette fonction retourne également la taille maximale de la fenêtre, selon la taille de la mémoire tampon d’écran actuelle, la taille actuelle de la police et la taille de l’écran.</span><span class="sxs-lookup"><span data-stu-id="59da3-128">This function also returns the maximum size of the window, given the current screen buffer size, the current font size, and the screen size.</span></span> <span data-ttu-id="59da3-129">La fonction [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) retourne la taille maximale de la fenêtre en fonction de la taille actuelle de la police et de l’écran, mais elle ne tient pas compte de la taille de la mémoire tampon de l’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="59da3-129">The [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) function returns the maximum window size given the current font and screen sizes, but it does not consider the size of the console screen buffer.</span></span>

<span data-ttu-id="59da3-130">**SetConsoleWindowInfo** peut être utilisé pour faire défiler le contenu de la mémoire tampon de l’écran de la console en décalant la position du rectangle de la fenêtre sans modifier sa taille.</span><span class="sxs-lookup"><span data-stu-id="59da3-130">**SetConsoleWindowInfo** can be used to scroll the contents of the console screen buffer by shifting the position of the window rectangle without changing its size.</span></span>

<a name="examples"></a><span data-ttu-id="59da3-131">Exemples</span><span class="sxs-lookup"><span data-stu-id="59da3-131">Examples</span></span>
--------

<span data-ttu-id="59da3-132">Pour obtenir un exemple, consultez [défilement de la fenêtre d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-window.md).</span><span class="sxs-lookup"><span data-stu-id="59da3-132">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

<a name="requirements"></a><span data-ttu-id="59da3-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="59da3-133">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="59da3-134">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="59da3-134">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="59da3-135">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="59da3-135">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="59da3-136">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="59da3-136">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="59da3-137">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="59da3-137">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="59da3-138">En-tête</span><span class="sxs-lookup"><span data-stu-id="59da3-138">Header</span></span></p></td>
<td><span data-ttu-id="59da3-139">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="59da3-139">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="59da3-140">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="59da3-140">Library</span></span></p></td>
<td><span data-ttu-id="59da3-141">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="59da3-141">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="59da3-142">DLL</span><span class="sxs-lookup"><span data-stu-id="59da3-142">DLL</span></span></p></td>
<td><span data-ttu-id="59da3-143">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="59da3-143">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="59da3-144"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59da3-144"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="59da3-145">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="59da3-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="59da3-146">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="59da3-146">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="59da3-147">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="59da3-147">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="59da3-148">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="59da3-148">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="59da3-149">Défilement de la mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="59da3-149">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

[<span data-ttu-id="59da3-150">**PETIT \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="59da3-150">**SMALL\_RECT**</span></span>](small-rect-str.md)

 

 




