---
title: ReadConsoleInput fonction)
description: Lit les données à partir d’une mémoire tampon d’entrée de la console et les supprime de la mémoire tampon.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi/ReadConsoleInput
- wincon/ReadConsoleInput
- ReadConsoleInput
- consoleapi/ReadConsoleInputA
- wincon/ReadConsoleInputA
- ReadConsoleInputA
- consoleapi/ReadConsoleInputW
- wincon/ReadConsoleInputW
- ReadConsoleInputW
MS-HAID:
- '\_win32\_readconsoleinput'
- base.readconsoleinput
- consoles.readconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5a9f7b18-cdea-4041-a377-5532d30e0105
topic_type:
- apiref
api_name:
- ReadConsoleInput
- ReadConsoleInputA
- ReadConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 38a5ee0d1572d6e40ab103cfc402d616a99d2ca5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059469"
---
# <a name="readconsoleinput-function"></a><span data-ttu-id="dfcf8-104">ReadConsoleInput fonction)</span><span class="sxs-lookup"><span data-stu-id="dfcf8-104">ReadConsoleInput function</span></span>


<span data-ttu-id="dfcf8-105">Lit les données à partir d’une mémoire tampon d’entrée de la console et les supprime de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="dfcf8-105">Reads data from a console input buffer and removes it from the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="dfcf8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfcf8-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

<a name="parameters"></a><span data-ttu-id="dfcf8-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dfcf8-107">Parameters</span></span>
----------

<span data-ttu-id="dfcf8-108">*hConsoleInput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="dfcf8-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="dfcf8-109">Handle vers la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="dfcf8-109">A handle to the console input buffer.</span></span> <span data-ttu-id="dfcf8-110">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="dfcf8-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="dfcf8-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="dfcf8-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="dfcf8-112">*lpBuffer* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="dfcf8-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="dfcf8-113">Pointeur vers un tableau de structures [**d' \_ enregistrements d’entrée**](input-record-str.md) qui reçoit les données de la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="dfcf8-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="dfcf8-114">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="dfcf8-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="dfcf8-115">Taille du tableau vers lequel pointe le paramètre *lpBuffer* , dans les éléments de tableau.</span><span class="sxs-lookup"><span data-stu-id="dfcf8-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="dfcf8-116">*lpNumberOfEventsRead* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="dfcf8-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="dfcf8-117">Pointeur vers une variable qui reçoit le nombre d’enregistrements d’entrée lus.</span><span class="sxs-lookup"><span data-stu-id="dfcf8-117">A pointer to a variable that receives the number of input records read.</span></span>

<a name="return-value"></a><span data-ttu-id="dfcf8-118">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="dfcf8-118">Return value</span></span>
------------

<span data-ttu-id="dfcf8-119">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="dfcf8-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="dfcf8-120">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="dfcf8-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="dfcf8-121">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="dfcf8-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="dfcf8-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="dfcf8-122">Remarks</span></span>
-------

<span data-ttu-id="dfcf8-123">Si le nombre d’enregistrements demandés dans le paramètre *nLength* dépasse le nombre d’enregistrements disponibles dans la mémoire tampon, le nombre disponible est Read.</span><span class="sxs-lookup"><span data-stu-id="dfcf8-123">If the number of records requested in the *nLength* parameter exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="dfcf8-124">La fonction ne retourne pas de données tant qu’au moins un enregistrement d’entrée n’a pas été lu.</span><span class="sxs-lookup"><span data-stu-id="dfcf8-124">The function does not return until at least one input record has been read.</span></span>

<span data-ttu-id="dfcf8-125">Un processus peut spécifier un handle de mémoire tampon d’entrée de la console dans l’une des [fonctions Wait](https://msdn.microsoft.com/library/windows/desktop/ms687069) pour déterminer le moment où une entrée de console n’est pas lue.</span><span class="sxs-lookup"><span data-stu-id="dfcf8-125">A process can specify a console input buffer handle in one of the [wait functions](https://msdn.microsoft.com/library/windows/desktop/ms687069) to determine when there is unread console input.</span></span> <span data-ttu-id="dfcf8-126">Lorsque la mémoire tampon d’entrée n’est pas vide, l’état d’un handle de mémoire tampon d’entrée de la console est signalé.</span><span class="sxs-lookup"><span data-stu-id="dfcf8-126">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="dfcf8-127">Pour déterminer le nombre d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée d’une console, utilisez la fonction [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) .</span><span class="sxs-lookup"><span data-stu-id="dfcf8-127">To determine the number of unread input records in a console's input buffer, use the [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) function.</span></span> <span data-ttu-id="dfcf8-128">Pour lire les enregistrements d’entrée d’une mémoire tampon d’entrée de la console sans affecter le nombre d’enregistrements non lus, utilisez la fonction [**PeekConsoleInput**](peekconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="dfcf8-128">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="dfcf8-129">Pour ignorer tous les enregistrements non lus dans le tampon d’entrée d’une console, utilisez la fonction [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="dfcf8-129">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

<span data-ttu-id="dfcf8-130">Cette fonction utilise des caractères Unicode ou 8 bits à partir de la page de codes actuelle de la console.</span><span class="sxs-lookup"><span data-stu-id="dfcf8-130">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="dfcf8-131">La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système.</span><span class="sxs-lookup"><span data-stu-id="dfcf8-131">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="dfcf8-132">Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="dfcf8-132">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="dfcf8-133">Exemples</span><span class="sxs-lookup"><span data-stu-id="dfcf8-133">Examples</span></span>
--------

<span data-ttu-id="dfcf8-134">Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="dfcf8-134">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="dfcf8-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dfcf8-135">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="dfcf8-136">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="dfcf8-136">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="dfcf8-137">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="dfcf8-137">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="dfcf8-138">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="dfcf8-138">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="dfcf8-139">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="dfcf8-139">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="dfcf8-140">En-tête</span><span class="sxs-lookup"><span data-stu-id="dfcf8-140">Header</span></span></p></td>
<td><span data-ttu-id="dfcf8-141">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="dfcf8-141">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="dfcf8-142">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="dfcf8-142">Library</span></span></p></td>
<td><span data-ttu-id="dfcf8-143">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="dfcf8-143">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="dfcf8-144">DLL</span><span class="sxs-lookup"><span data-stu-id="dfcf8-144">DLL</span></span></p></td>
<td><span data-ttu-id="dfcf8-145">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="dfcf8-145">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="dfcf8-146">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="dfcf8-146">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="dfcf8-147"><strong>ReadConsoleInputW</strong> (Unicode) et <strong>ReadConsoleInputA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="dfcf8-147"><strong>ReadConsoleInputW</strong> (Unicode) and <strong>ReadConsoleInputA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="dfcf8-148"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfcf8-148"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="dfcf8-149">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="dfcf8-149">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="dfcf8-150">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="dfcf8-150">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="dfcf8-151">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="dfcf8-151">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="dfcf8-152">**enregistrement d’entrée \_**</span><span class="sxs-lookup"><span data-stu-id="dfcf8-152">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="dfcf8-153">Fonctions d’entrée de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="dfcf8-153">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="dfcf8-154">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="dfcf8-154">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="dfcf8-155">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="dfcf8-155">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="dfcf8-156">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="dfcf8-156">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="dfcf8-157">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="dfcf8-157">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="dfcf8-158">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="dfcf8-158">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="dfcf8-159">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="dfcf8-159">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 




