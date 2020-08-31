---
title: SetStdHandle fonction)
description: Définit le descripteur pour l’appareil standard spécifié (entrée standard, sortie standard ou erreur standard).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 6ab17a2162d31c956ec64dbb33696c20ae085298
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060534"
---
# <a name="setstdhandle-function"></a><span data-ttu-id="7c7c3-104">SetStdHandle fonction)</span><span class="sxs-lookup"><span data-stu-id="7c7c3-104">SetStdHandle function</span></span>


<span data-ttu-id="7c7c3-105">Définit le descripteur pour l’appareil standard spécifié (entrée standard, sortie standard ou erreur standard).</span><span class="sxs-lookup"><span data-stu-id="7c7c3-105">Sets the handle for the specified standard device (standard input, standard output, or standard error).</span></span>

<a name="syntax"></a><span data-ttu-id="7c7c3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c7c3-106">Syntax</span></span>
------

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

<a name="parameters"></a><span data-ttu-id="7c7c3-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7c7c3-107">Parameters</span></span>
----------

<span data-ttu-id="7c7c3-108">*nStdHandle* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="7c7c3-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="7c7c3-109">Appareil standard pour lequel le descripteur doit être défini.</span><span class="sxs-lookup"><span data-stu-id="7c7c3-109">The standard device for which the handle is to be set.</span></span> <span data-ttu-id="7c7c3-110">Ce paramètre peut prendre l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="7c7c3-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="7c7c3-111">Value</span><span class="sxs-lookup"><span data-stu-id="7c7c3-111">Value</span></span></th>
<th><span data-ttu-id="7c7c3-112">Signification</span><span class="sxs-lookup"><span data-stu-id="7c7c3-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="7c7c3-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</span><span class="sxs-lookup"><span data-stu-id="7c7c3-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</span></span></td>
<td><p><span data-ttu-id="7c7c3-114">Périphérique d’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="7c7c3-114">The standard input device.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="7c7c3-115"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</span><span class="sxs-lookup"><span data-stu-id="7c7c3-115"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</span></span></td>
<td><p><span data-ttu-id="7c7c3-116">Périphérique de sortie standard.</span><span class="sxs-lookup"><span data-stu-id="7c7c3-116">The standard output device.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="7c7c3-117"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</span><span class="sxs-lookup"><span data-stu-id="7c7c3-117"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</span></span></td>
<td><p><span data-ttu-id="7c7c3-118">Périphérique d’erreur standard.</span><span class="sxs-lookup"><span data-stu-id="7c7c3-118">The standard error device.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="7c7c3-119">*hHandle* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="7c7c3-119">*hHandle* \[in\]</span></span>  
<span data-ttu-id="7c7c3-120">Handle pour l’appareil standard.</span><span class="sxs-lookup"><span data-stu-id="7c7c3-120">The handle for the standard device.</span></span>

<a name="return-value"></a><span data-ttu-id="7c7c3-121">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="7c7c3-121">Return value</span></span>
------------

<span data-ttu-id="7c7c3-122">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="7c7c3-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="7c7c3-123">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="7c7c3-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="7c7c3-124">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="7c7c3-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="7c7c3-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="7c7c3-125">Remarks</span></span>
-------

<span data-ttu-id="7c7c3-126">Les handles standard d’un processus peuvent avoir été redirigés par un appel à **SetStdHandle**, auquel cas [**GetStdHandle**](getstdhandle.md) retourne le handle Redirigé.</span><span class="sxs-lookup"><span data-stu-id="7c7c3-126">The standard handles of a process may have been redirected by a call to **SetStdHandle**, in which case [**GetStdHandle**](getstdhandle.md) will return the redirected handle.</span></span> <span data-ttu-id="7c7c3-127">Si les handles standard ont été redirigés, vous pouvez spécifier la valeur CONIN $ dans un appel à la fonction [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) pour obtenir un handle vers la mémoire tampon d’entrée d’une console.</span><span class="sxs-lookup"><span data-stu-id="7c7c3-127">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="7c7c3-128">De même, vous pouvez spécifier la valeur CONOUT $ pour obtenir un descripteur de la mémoire tampon d’écran active de la console.</span><span class="sxs-lookup"><span data-stu-id="7c7c3-128">Similarly, you can specify the CONOUT$ value to get a handle to the console's active screen buffer.</span></span>

<a name="examples"></a><span data-ttu-id="7c7c3-129">Exemples</span><span class="sxs-lookup"><span data-stu-id="7c7c3-129">Examples</span></span>
--------

<span data-ttu-id="7c7c3-130">Pour obtenir un exemple, consultez [création d’un processus enfant avec une entrée et une sortie redirigées](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span><span class="sxs-lookup"><span data-stu-id="7c7c3-130">For an example, see [Creating a Child Process with Redirected Input and Output](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span></span>

<a name="requirements"></a><span data-ttu-id="7c7c3-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7c7c3-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="7c7c3-132">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7c7c3-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="7c7c3-133">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="7c7c3-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7c7c3-134">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7c7c3-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="7c7c3-135">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="7c7c3-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7c7c3-136">En-tête</span><span class="sxs-lookup"><span data-stu-id="7c7c3-136">Header</span></span></p></td>
<td><span data-ttu-id="7c7c3-137">ProcessEnv. h (via Winbase. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="7c7c3-137">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7c7c3-138">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="7c7c3-138">Library</span></span></p></td>
<td><span data-ttu-id="7c7c3-139">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="7c7c3-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7c7c3-140">DLL</span><span class="sxs-lookup"><span data-stu-id="7c7c3-140">DLL</span></span></p></td>
<td><span data-ttu-id="7c7c3-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7c7c3-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="7c7c3-142"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c7c3-142"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="7c7c3-143">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="7c7c3-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="7c7c3-144">Handles de la console</span><span class="sxs-lookup"><span data-stu-id="7c7c3-144">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="7c7c3-145">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="7c7c3-145">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="7c7c3-146">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="7c7c3-146">**GetStdHandle**</span></span>](getstdhandle.md)

 

 




