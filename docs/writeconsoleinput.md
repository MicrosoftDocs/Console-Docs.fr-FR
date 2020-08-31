---
title: WriteConsoleInput fonction)
description: Consultez les informations de référence sur la fonction WriteConsoleInput, qui écrit les données directement dans la mémoire tampon d’entrée de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/WriteConsoleInput
- wincon/WriteConsoleInput
- WriteConsoleInput
- consoleapi2/WriteConsoleInputA
- wincon/WriteConsoleInputA
- WriteConsoleInputA
- consoleapi2/WriteConsoleInputW
- wincon/WriteConsoleInputW
- WriteConsoleInputW
MS-HAID:
- '\_win32\_writeconsoleinput'
- base.writeconsoleinput
- consoles.writeconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad06231f-5063-4aff-b14d-8df5e6e42430
topic_type:
- apiref
api_name:
- WriteConsoleInput
- WriteConsoleInputA
- WriteConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 784bed6c1a7b7f7ed9ed204b8483d30371e510a3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060566"
---
# <a name="writeconsoleinput-function"></a><span data-ttu-id="b2801-104">WriteConsoleInput fonction)</span><span class="sxs-lookup"><span data-stu-id="b2801-104">WriteConsoleInput function</span></span>


<span data-ttu-id="b2801-105">Écrit les données directement dans la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="b2801-105">Writes data directly to the console input buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="b2801-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2801-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

<a name="parameters"></a><span data-ttu-id="b2801-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b2801-107">Parameters</span></span>
----------

<span data-ttu-id="b2801-108">*hConsoleInput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="b2801-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="b2801-109">Handle vers la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="b2801-109">A handle to the console input buffer.</span></span> <span data-ttu-id="b2801-110">Le descripteur doit avoir le droit d’accès en \*\* \_ écriture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="b2801-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="b2801-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="b2801-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="b2801-112">*lpBuffer* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="b2801-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="b2801-113">Pointeur vers un tableau de structures [**d' \_ enregistrements d’entrée**](input-record-str.md) qui contiennent les données à écrire dans la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="b2801-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that contain data to be written to the input buffer.</span></span>

<span data-ttu-id="b2801-114">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="b2801-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="b2801-115">Nombre d’enregistrements d’entrée à écrire.</span><span class="sxs-lookup"><span data-stu-id="b2801-115">The number of input records to be written.</span></span>

<span data-ttu-id="b2801-116">*lpNumberOfEventsWritten* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="b2801-116">*lpNumberOfEventsWritten* \[out\]</span></span>  
<span data-ttu-id="b2801-117">Pointeur vers une variable qui reçoit le nombre d’enregistrements d’entrée réellement écrits.</span><span class="sxs-lookup"><span data-stu-id="b2801-117">A pointer to a variable that receives the number of input records actually written.</span></span>

<a name="return-value"></a><span data-ttu-id="b2801-118">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="b2801-118">Return value</span></span>
------------

<span data-ttu-id="b2801-119">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="b2801-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b2801-120">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="b2801-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b2801-121">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="b2801-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="b2801-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="b2801-122">Remarks</span></span>
-------

<span data-ttu-id="b2801-123">**WriteConsoleInput** place les enregistrements d’entrée dans la mémoire tampon d’entrée derrière les événements en attente dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="b2801-123">**WriteConsoleInput** places input records into the input buffer behind any pending events in the buffer.</span></span> <span data-ttu-id="b2801-124">Le tampon d’entrée augmente de manière dynamique, si nécessaire, pour contenir autant d’événements que ceux écrits.</span><span class="sxs-lookup"><span data-stu-id="b2801-124">The input buffer grows dynamically, if necessary, to hold as many events as are written.</span></span>

<span data-ttu-id="b2801-125">Cette fonction utilise des caractères Unicode ou 8 bits à partir de la page de codes actuelle de la console.</span><span class="sxs-lookup"><span data-stu-id="b2801-125">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="b2801-126">La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système.</span><span class="sxs-lookup"><span data-stu-id="b2801-126">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="b2801-127">Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="b2801-127">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="b2801-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b2801-128">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b2801-129">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="b2801-129">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="b2801-130">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="b2801-130">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b2801-131">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="b2801-131">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="b2801-132">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="b2801-132">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b2801-133">En-tête</span><span class="sxs-lookup"><span data-stu-id="b2801-133">Header</span></span></p></td>
<td><span data-ttu-id="b2801-134">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b2801-134">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b2801-135">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="b2801-135">Library</span></span></p></td>
<td><span data-ttu-id="b2801-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="b2801-136">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b2801-137">DLL</span><span class="sxs-lookup"><span data-stu-id="b2801-137">DLL</span></span></p></td>
<td><span data-ttu-id="b2801-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b2801-138">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b2801-139">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="b2801-139">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="b2801-140"><strong>WriteConsoleInputW</strong> (Unicode) et <strong>WriteConsoleInputA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="b2801-140"><strong>WriteConsoleInputW</strong> (Unicode) and <strong>WriteConsoleInputA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="b2801-141"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2801-141"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="b2801-142">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="b2801-142">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b2801-143">**enregistrement d’entrée \_**</span><span class="sxs-lookup"><span data-stu-id="b2801-143">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="b2801-144">Fonctions d’entrée de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="b2801-144">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="b2801-145">**MapVirtualKey**</span><span class="sxs-lookup"><span data-stu-id="b2801-145">**MapVirtualKey**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646306)

[<span data-ttu-id="b2801-146">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="b2801-146">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="b2801-147">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="b2801-147">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="b2801-148">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="b2801-148">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="b2801-149">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="b2801-149">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="b2801-150">**VkKeyScan**</span><span class="sxs-lookup"><span data-stu-id="b2801-150">**VkKeyScan**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646329)

 

 




