---
title: SetConsoleCursorInfo fonction)
description: Définit la taille et la visibilité du curseur pour la mémoire tampon d’écran de la console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/SetConsoleCursorInfo
- wincon/SetConsoleCursorInfo
- SetConsoleCursorInfo
MS-HAID:
- '\_win32\_setconsolecursorinfo'
- base.setconsolecursorinfo
- consoles.setconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c98cbffb-18de-41e8-bba7-5fb46a0c5d25
topic_type:
- apiref
api_name:
- SetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 81f16e8c9d9cf90008bbd2e8619c2fa105d04212
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059413"
---
# <a name="setconsolecursorinfo-function"></a><span data-ttu-id="44081-104">SetConsoleCursorInfo fonction)</span><span class="sxs-lookup"><span data-stu-id="44081-104">SetConsoleCursorInfo function</span></span>


<span data-ttu-id="44081-105">Définit la taille et la visibilité du curseur pour la mémoire tampon d’écran de la console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="44081-105">Sets the size and visibility of the cursor for the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="44081-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44081-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

<a name="parameters"></a><span data-ttu-id="44081-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="44081-107">Parameters</span></span>
----------

<span data-ttu-id="44081-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="44081-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="44081-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="44081-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="44081-110">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="44081-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="44081-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="44081-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="44081-112">*lpConsoleCursorInfo* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="44081-112">*lpConsoleCursorInfo* \[in\]</span></span>  
<span data-ttu-id="44081-113">Pointeur vers une structure [**d' \_ \_ informations de curseur de console**](console-cursor-info-str.md) qui fournit les nouvelles spécifications pour le curseur de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="44081-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that provides the new specifications for the console screen buffer's cursor.</span></span>

<a name="return-value"></a><span data-ttu-id="44081-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="44081-114">Return value</span></span>
------------

<span data-ttu-id="44081-115">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="44081-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="44081-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="44081-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="44081-117">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="44081-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="44081-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="44081-118">Remarks</span></span>
-------

<span data-ttu-id="44081-119">Lorsque le curseur d’une mémoire tampon d’écran est visible, son apparence peut varier, du remplissage complet d’une cellule de caractère à l’affichage sous forme de ligne horizontale au bas de la cellule.</span><span class="sxs-lookup"><span data-stu-id="44081-119">When a screen buffer's cursor is visible, its appearance can vary, ranging from completely filling a character cell to showing up as a horizontal line at the bottom of the cell.</span></span> <span data-ttu-id="44081-120">Le membre **dwSize nul** de la structure d' [\*\* \_ \_ informations du curseur\*\*](console-cursor-info-str.md) de la console spécifie le pourcentage d’une cellule de caractère qui est remplie par le curseur.</span><span class="sxs-lookup"><span data-stu-id="44081-120">The **dwSize** member of the [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure specifies the percentage of a character cell that is filled by the cursor.</span></span> <span data-ttu-id="44081-121">Si ce membre est inférieur à 1 ou supérieur à 100, **SetConsoleCursorInfo** échoue.</span><span class="sxs-lookup"><span data-stu-id="44081-121">If this member is less than 1 or greater than 100, **SetConsoleCursorInfo** fails.</span></span>

<a name="requirements"></a><span data-ttu-id="44081-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="44081-122">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="44081-123">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="44081-123">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="44081-124">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="44081-124">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="44081-125">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="44081-125">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="44081-126">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="44081-126">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="44081-127">En-tête</span><span class="sxs-lookup"><span data-stu-id="44081-127">Header</span></span></p></td>
<td><span data-ttu-id="44081-128">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="44081-128">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="44081-129">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="44081-129">Library</span></span></p></td>
<td><span data-ttu-id="44081-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="44081-130">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="44081-131">DLL</span><span class="sxs-lookup"><span data-stu-id="44081-131">DLL</span></span></p></td>
<td><span data-ttu-id="44081-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="44081-132">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="44081-133"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44081-133"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="44081-134">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="44081-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="44081-135">Mémoires tampons d’écran de la console</span><span class="sxs-lookup"><span data-stu-id="44081-135">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="44081-136">**\_informations sur le curseur de la console \_**</span><span class="sxs-lookup"><span data-stu-id="44081-136">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="44081-137">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="44081-137">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="44081-138">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="44081-138">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

 

 




