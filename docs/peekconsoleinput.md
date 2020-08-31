---
title: PeekConsoleInput fonction)
description: Lit les données de la mémoire tampon d’entrée de la console spécifiée sans les supprimer de la mémoire tampon.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi/PeekConsoleInput
- wincon/PeekConsoleInput
- PeekConsoleInput
- consoleapi/PeekConsoleInputA
- wincon/PeekConsoleInputA
- PeekConsoleInputA
- consoleapi/PeekConsoleInputW
- wincon/PeekConsoleInputW
- PeekConsoleInputW
MS-HAID:
- '\_win32\_peekconsoleinput'
- base.peekconsoleinput
- consoles.peekconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9982dc20-43bd-4ee3-a68d-157c9134daca
topic_type:
- apiref
api_name:
- PeekConsoleInput
- PeekConsoleInputA
- PeekConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: c74df91f3b70827cd0c5410d01b2a165694909f9
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059060"
---
# <a name="peekconsoleinput-function"></a><span data-ttu-id="1d0b8-104">PeekConsoleInput fonction)</span><span class="sxs-lookup"><span data-stu-id="1d0b8-104">PeekConsoleInput function</span></span>


<span data-ttu-id="1d0b8-105">Lit les données de la mémoire tampon d’entrée de la console spécifiée sans les supprimer de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="1d0b8-105">Reads data from the specified console input buffer without removing it from the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="1d0b8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d0b8-106">Syntax</span></span>
------

```C
BOOL WINAPI PeekConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

<a name="parameters"></a><span data-ttu-id="1d0b8-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1d0b8-107">Parameters</span></span>
----------

<span data-ttu-id="1d0b8-108">*hConsoleInput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="1d0b8-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="1d0b8-109">Handle vers la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="1d0b8-109">A handle to the console input buffer.</span></span> <span data-ttu-id="1d0b8-110">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="1d0b8-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="1d0b8-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="1d0b8-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="1d0b8-112">*lpBuffer* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="1d0b8-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="1d0b8-113">Pointeur vers un tableau de structures [**d' \_ enregistrements d’entrée**](input-record-str.md) qui reçoit les données de la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="1d0b8-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="1d0b8-114">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="1d0b8-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="1d0b8-115">Taille du tableau vers lequel pointe le paramètre *lpBuffer* , dans les éléments de tableau.</span><span class="sxs-lookup"><span data-stu-id="1d0b8-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="1d0b8-116">*lpNumberOfEventsRead* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="1d0b8-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="1d0b8-117">Pointeur vers une variable qui reçoit le nombre d’enregistrements d’entrée lus.</span><span class="sxs-lookup"><span data-stu-id="1d0b8-117">A pointer to a variable that receives the number of input records read.</span></span>

<a name="return-value"></a><span data-ttu-id="1d0b8-118">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="1d0b8-118">Return value</span></span>
------------

<span data-ttu-id="1d0b8-119">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="1d0b8-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="1d0b8-120">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="1d0b8-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="1d0b8-121">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="1d0b8-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="1d0b8-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="1d0b8-122">Remarks</span></span>
-------

<span data-ttu-id="1d0b8-123">Si le nombre d’enregistrements demandés dépasse le nombre d’enregistrements disponibles dans la mémoire tampon, le nombre disponible est lu.</span><span class="sxs-lookup"><span data-stu-id="1d0b8-123">If the number of records requested exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="1d0b8-124">Si aucune donnée n’est disponible, la fonction est retournée immédiatement.</span><span class="sxs-lookup"><span data-stu-id="1d0b8-124">If no data is available, the function returns immediately.</span></span>

<span data-ttu-id="1d0b8-125">Cette fonction utilise des caractères Unicode ou 8 bits à partir de la page de codes actuelle de la console.</span><span class="sxs-lookup"><span data-stu-id="1d0b8-125">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="1d0b8-126">La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système.</span><span class="sxs-lookup"><span data-stu-id="1d0b8-126">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="1d0b8-127">Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="1d0b8-127">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="1d0b8-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1d0b8-128">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="1d0b8-129">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="1d0b8-129">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="1d0b8-130">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="1d0b8-130">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1d0b8-131">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="1d0b8-131">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="1d0b8-132">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="1d0b8-132">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1d0b8-133">En-tête</span><span class="sxs-lookup"><span data-stu-id="1d0b8-133">Header</span></span></p></td>
<td><span data-ttu-id="1d0b8-134">ConsoleApi. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1d0b8-134">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1d0b8-135">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="1d0b8-135">Library</span></span></p></td>
<td><span data-ttu-id="1d0b8-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="1d0b8-136">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1d0b8-137">DLL</span><span class="sxs-lookup"><span data-stu-id="1d0b8-137">DLL</span></span></p></td>
<td><span data-ttu-id="1d0b8-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1d0b8-138">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1d0b8-139">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="1d0b8-139">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="1d0b8-140"><strong>PeekConsoleInputW</strong> (Unicode) et <strong>PeekConsoleInputA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="1d0b8-140"><strong>PeekConsoleInputW</strong> (Unicode) and <strong>PeekConsoleInputA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="1d0b8-141"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d0b8-141"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="1d0b8-142">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="1d0b8-142">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1d0b8-143">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="1d0b8-143">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="1d0b8-144">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="1d0b8-144">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="1d0b8-145">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="1d0b8-145">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="1d0b8-146">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="1d0b8-146">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

[<span data-ttu-id="1d0b8-147">**enregistrement d’entrée \_**</span><span class="sxs-lookup"><span data-stu-id="1d0b8-147">**INPUT\_RECORD**</span></span>](input-record-str.md)

 

 




