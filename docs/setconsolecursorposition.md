---
title: SetConsoleCursorPosition fonction)
description: Consultez les informations de référence sur la fonction SetConsoleCursorPosition, qui définit la position du curseur dans la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/SetConsoleCursorPosition
- wincon/SetConsoleCursorPosition
- SetConsoleCursorPosition
MS-HAID:
- '\_win32\_setconsolecursorposition'
- base.setconsolecursorposition
- consoles.setconsolecursorposition
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8e9abada-a64e-429f-8286-ced1169c7104
topic_type:
- apiref
api_name:
- SetConsoleCursorPosition
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: eaa50df16248597f1054f0741113ecc9be1f3264
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059405"
---
# <a name="setconsolecursorposition-function"></a><span data-ttu-id="19e91-104">SetConsoleCursorPosition fonction)</span><span class="sxs-lookup"><span data-stu-id="19e91-104">SetConsoleCursorPosition function</span></span>


<span data-ttu-id="19e91-105">Définit la position du curseur dans la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="19e91-105">Sets the cursor position in the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="19e91-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19e91-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

<a name="parameters"></a><span data-ttu-id="19e91-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="19e91-107">Parameters</span></span>
----------

<span data-ttu-id="19e91-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="19e91-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="19e91-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="19e91-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="19e91-110">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="19e91-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="19e91-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="19e91-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="19e91-112">*dwCursorPosition* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="19e91-112">*dwCursorPosition* \[in\]</span></span>  
<span data-ttu-id="19e91-113">Structure de [**repère**](coord-str.md) qui spécifie la nouvelle position du curseur, en caractères.</span><span class="sxs-lookup"><span data-stu-id="19e91-113">A [**COORD**](coord-str.md) structure that specifies the new cursor position, in characters.</span></span> <span data-ttu-id="19e91-114">Les coordonnées sont la colonne et la ligne d’une cellule de caractère de mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="19e91-114">The coordinates are the column and row of a screen buffer character cell.</span></span> <span data-ttu-id="19e91-115">Les coordonnées doivent se trouver dans les limites de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="19e91-115">The coordinates must be within the boundaries of the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="19e91-116">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="19e91-116">Return value</span></span>
------------

<span data-ttu-id="19e91-117">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="19e91-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="19e91-118">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="19e91-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="19e91-119">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="19e91-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="19e91-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="19e91-120">Remarks</span></span>
-------

<span data-ttu-id="19e91-121">La position du curseur détermine l’emplacement d’affichage des caractères écrits par la fonction [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ou [**WriteConsole**](writeconsole.md) , ou renvoyé par la fonction [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ou [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="19e91-121">The cursor position determines where characters written by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function, are displayed.</span></span> <span data-ttu-id="19e91-122">Pour déterminer la position actuelle du curseur, utilisez la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="19e91-122">To determine the current position of the cursor, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="19e91-123">Si la nouvelle position du curseur ne se trouve pas dans les limites de la fenêtre de la mémoire tampon de l’écran de la console, l’origine de la fenêtre change pour rendre le curseur visible.</span><span class="sxs-lookup"><span data-stu-id="19e91-123">If the new cursor position is not within the boundaries of the console screen buffer's window, the window origin changes to make the cursor visible.</span></span>

<a name="examples"></a><span data-ttu-id="19e91-124">Exemples</span><span class="sxs-lookup"><span data-stu-id="19e91-124">Examples</span></span>
--------

<span data-ttu-id="19e91-125">Pour obtenir un exemple, consultez [utilisation des fonctions d’entrée et de sortie de haut niveau](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="19e91-125">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

<a name="requirements"></a><span data-ttu-id="19e91-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="19e91-126">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="19e91-127">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="19e91-127">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="19e91-128">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="19e91-128">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="19e91-129">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="19e91-129">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="19e91-130">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="19e91-130">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="19e91-131">En-tête</span><span class="sxs-lookup"><span data-stu-id="19e91-131">Header</span></span></p></td>
<td><span data-ttu-id="19e91-132">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="19e91-132">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="19e91-133">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="19e91-133">Library</span></span></p></td>
<td><span data-ttu-id="19e91-134">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="19e91-134">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="19e91-135">DLL</span><span class="sxs-lookup"><span data-stu-id="19e91-135">DLL</span></span></p></td>
<td><span data-ttu-id="19e91-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="19e91-136">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="19e91-137"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19e91-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="19e91-138">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="19e91-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="19e91-139">Mémoires tampons d’écran de la console</span><span class="sxs-lookup"><span data-stu-id="19e91-139">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="19e91-140">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="19e91-140">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="19e91-141">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="19e91-141">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="19e91-142">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="19e91-142">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="19e91-143">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="19e91-143">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="19e91-144">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="19e91-144">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

[<span data-ttu-id="19e91-145">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="19e91-145">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="19e91-146">**Appel**</span><span class="sxs-lookup"><span data-stu-id="19e91-146">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




