---
title: GetConsoleScreenBufferInfo fonction)
description: Consultez les informations de référence sur la fonction GetConsoleScreenBufferInfo, qui récupère des informations sur la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfo
- wincon/GetConsoleScreenBufferInfo
- GetConsoleScreenBufferInfo
ms.assetid: eafe819e-a99a-4ce1-8898-8860444a31af
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 8ced380982705647b7944cee0f72c723c38776c3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059128"
---
# <a name="getconsolescreenbufferinfo-function"></a><span data-ttu-id="aa8a5-104">GetConsoleScreenBufferInfo fonction)</span><span class="sxs-lookup"><span data-stu-id="aa8a5-104">GetConsoleScreenBufferInfo function</span></span>


<span data-ttu-id="aa8a5-105">Récupère des informations sur la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="aa8a5-105">Retrieves information about the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="aa8a5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa8a5-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

<a name="parameters"></a><span data-ttu-id="aa8a5-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aa8a5-107">Parameters</span></span>
----------

<span data-ttu-id="aa8a5-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="aa8a5-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="aa8a5-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="aa8a5-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="aa8a5-110">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="aa8a5-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="aa8a5-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="aa8a5-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="aa8a5-112">*lpConsoleScreenBufferInfo* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="aa8a5-112">*lpConsoleScreenBufferInfo* \[out\]</span></span>  
<span data-ttu-id="aa8a5-113">Pointeur vers une structure [**d' \_ \_ \_ informations de mémoire tampon d’écran de console**](console-screen-buffer-info-str.md) qui reçoit les informations de mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="aa8a5-113">A pointer to a [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure that receives the console screen buffer information.</span></span>

<a name="return-value"></a><span data-ttu-id="aa8a5-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="aa8a5-114">Return value</span></span>
------------

<span data-ttu-id="aa8a5-115">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="aa8a5-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="aa8a5-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="aa8a5-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="aa8a5-117">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="aa8a5-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="aa8a5-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="aa8a5-118">Remarks</span></span>
-------

<span data-ttu-id="aa8a5-119">Le rectangle retourné dans le membre **srWindow** de la structure des [\*\* \_ \_ \_ informations de mémoire tampon\*\*](console-screen-buffer-info-str.md) de l’écran de la console peut être modifié, puis transmis à la fonction [**SetConsoleWindowInfo**](setconsolewindowinfo.md) pour faire défiler la mémoire tampon de l’écran de la console dans la fenêtre, pour modifier la taille de la fenêtre, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="aa8a5-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="aa8a5-120">Toutes les coordonnées retournées dans la structure des [\*\* \_ \_ \_ informations de mémoire tampon\*\*](console-screen-buffer-info-str.md) de l’écran de la console sont exprimées en coordonnées de cellule de caractères, où l’origine (0,0) se trouve dans l’angle supérieur gauche de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="aa8a5-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

<a name="examples"></a><span data-ttu-id="aa8a5-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="aa8a5-121">Examples</span></span>
--------

<span data-ttu-id="aa8a5-122">Pour obtenir un exemple, consultez [défilement de la fenêtre d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-window.md).</span><span class="sxs-lookup"><span data-stu-id="aa8a5-122">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

<a name="requirements"></a><span data-ttu-id="aa8a5-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="aa8a5-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="aa8a5-124">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="aa8a5-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="aa8a5-125">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="aa8a5-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="aa8a5-126">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="aa8a5-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="aa8a5-127">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="aa8a5-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="aa8a5-128">En-tête</span><span class="sxs-lookup"><span data-stu-id="aa8a5-128">Header</span></span></p></td>
<td><span data-ttu-id="aa8a5-129">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="aa8a5-129">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="aa8a5-130">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="aa8a5-130">Library</span></span></p></td>
<td><span data-ttu-id="aa8a5-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="aa8a5-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="aa8a5-132">DLL</span><span class="sxs-lookup"><span data-stu-id="aa8a5-132">DLL</span></span></p></td>
<td><span data-ttu-id="aa8a5-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="aa8a5-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="aa8a5-134"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa8a5-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="aa8a5-135">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="aa8a5-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="aa8a5-136">**\_ \_ informations sur la mémoire tampon d’écran de la console \_**</span><span class="sxs-lookup"><span data-stu-id="aa8a5-136">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="aa8a5-137">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="aa8a5-137">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="aa8a5-138">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="aa8a5-138">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="aa8a5-139">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="aa8a5-139">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="aa8a5-140">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="aa8a5-140">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="aa8a5-141">Taille de la mémoire tampon de la fenêtre et de l’écran</span><span class="sxs-lookup"><span data-stu-id="aa8a5-141">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)

 

 




