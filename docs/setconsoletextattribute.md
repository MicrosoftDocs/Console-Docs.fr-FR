---
title: SetConsoleTextAttribute fonction)
description: Définit les attributs des caractères écrits dans la mémoire tampon d’écran de la console par la fonction WriteFile ou WriteConsole, ou en écho par la fonction ReadFile ou ReadConsole.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/SetConsoleTextAttribute
- wincon/SetConsoleTextAttribute
- SetConsoleTextAttribute
MS-HAID:
- '\_win32\_setconsoletextattribute'
- base.setconsoletextattribute
- consoles.setconsoletextattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9fba5bb5-b999-4abd-ab39-7a63d58b8074
topic_type:
- apiref
api_name:
- SetConsoleTextAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 2242466e4255b0d92c9bb1d1eac5431b59346e7b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059529"
---
# <a name="setconsoletextattribute-function"></a><span data-ttu-id="4f62d-104">SetConsoleTextAttribute fonction)</span><span class="sxs-lookup"><span data-stu-id="4f62d-104">SetConsoleTextAttribute function</span></span>


<span data-ttu-id="4f62d-105">Définit les attributs des caractères écrits dans la mémoire tampon d’écran de la console par la fonction [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ou [**WriteConsole**](writeconsole.md) , ou en écho par la fonction [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ou [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="4f62d-105">Sets the attributes of characters written to the console screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="4f62d-106">Cette fonction affecte le texte écrit après l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="4f62d-106">This function affects text written after the function call.</span></span>

<a name="syntax"></a><span data-ttu-id="4f62d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f62d-107">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleTextAttribute(
  _In_ HANDLE hConsoleOutput,
  _In_ WORD   wAttributes
);
```

<a name="parameters"></a><span data-ttu-id="4f62d-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4f62d-108">Parameters</span></span>
----------

<span data-ttu-id="4f62d-109">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="4f62d-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="4f62d-110">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="4f62d-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="4f62d-111">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="4f62d-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="4f62d-112">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="4f62d-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="4f62d-113">*wAttributes* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="4f62d-113">*wAttributes* \[in\]</span></span>  
<span data-ttu-id="4f62d-114">[Attributs de caractère](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="4f62d-114">The [character attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<a name="return-value"></a><span data-ttu-id="4f62d-115">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="4f62d-115">Return value</span></span>
------------

<span data-ttu-id="4f62d-116">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="4f62d-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4f62d-117">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="4f62d-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4f62d-118">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4f62d-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="4f62d-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="4f62d-119">Remarks</span></span>
-------

<span data-ttu-id="4f62d-120">Pour déterminer les attributs de couleur actuels d’une mémoire tampon d’écran, appelez la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="4f62d-120">To determine the current color attributes of a screen buffer, call the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<a name="examples"></a><span data-ttu-id="4f62d-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="4f62d-121">Examples</span></span>
--------

<span data-ttu-id="4f62d-122">Pour obtenir un exemple, consultez [utilisation des fonctions d’entrée et de sortie de haut niveau](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4f62d-122">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

<a name="requirements"></a><span data-ttu-id="4f62d-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4f62d-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="4f62d-124">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="4f62d-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="4f62d-125">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="4f62d-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4f62d-126">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="4f62d-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="4f62d-127">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="4f62d-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4f62d-128">En-tête</span><span class="sxs-lookup"><span data-stu-id="4f62d-128">Header</span></span></p></td>
<td><span data-ttu-id="4f62d-129">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4f62d-129">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4f62d-130">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="4f62d-130">Library</span></span></p></td>
<td><span data-ttu-id="4f62d-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4f62d-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4f62d-132">DLL</span><span class="sxs-lookup"><span data-stu-id="4f62d-132">DLL</span></span></p></td>
<td><span data-ttu-id="4f62d-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4f62d-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="4f62d-134"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f62d-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="4f62d-135">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="4f62d-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4f62d-136">Mémoires tampons d’écran de la console</span><span class="sxs-lookup"><span data-stu-id="4f62d-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="4f62d-137">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="4f62d-137">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="4f62d-138">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="4f62d-138">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="4f62d-139">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="4f62d-139">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="4f62d-140">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="4f62d-140">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="4f62d-141">**Appel**</span><span class="sxs-lookup"><span data-stu-id="4f62d-141">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




