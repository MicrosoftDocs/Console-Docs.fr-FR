---
title: GetNumberOfConsoleInputEvents fonction)
description: Récupère le nombre d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi/GetNumberOfConsoleInputEvents
- wincon/GetNumberOfConsoleInputEvents
- GetNumberOfConsoleInputEvents
MS-HAID:
- '\_win32\_getnumberofconsoleinputevents'
- base.getnumberofconsoleinputevents
- consoles.getnumberofconsoleinputevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1083b4f1-8fa6-4054-a516-3b447c3b0130
topic_type:
- apiref
api_name:
- GetNumberOfConsoleInputEvents
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: c5e3a59308239898f78796170d08f8b21ca1b667
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059117"
---
# <a name="getnumberofconsoleinputevents-function"></a><span data-ttu-id="b12f9-104">GetNumberOfConsoleInputEvents fonction)</span><span class="sxs-lookup"><span data-stu-id="b12f9-104">GetNumberOfConsoleInputEvents function</span></span>


<span data-ttu-id="b12f9-105">Récupère le nombre d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="b12f9-105">Retrieves the number of unread input records in the console's input buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="b12f9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b12f9-106">Syntax</span></span>
------

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

<a name="parameters"></a><span data-ttu-id="b12f9-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b12f9-107">Parameters</span></span>
----------

<span data-ttu-id="b12f9-108">*hConsoleInput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="b12f9-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="b12f9-109">Handle vers la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="b12f9-109">A handle to the console input buffer.</span></span> <span data-ttu-id="b12f9-110">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="b12f9-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="b12f9-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="b12f9-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="b12f9-112">*lpcNumberOfEvents* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="b12f9-112">*lpcNumberOfEvents* \[out\]</span></span>  
<span data-ttu-id="b12f9-113">Pointeur vers une variable qui reçoit le nombre d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="b12f9-113">A pointer to a variable that receives the number of unread input records in the console's input buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="b12f9-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="b12f9-114">Return value</span></span>
------------

<span data-ttu-id="b12f9-115">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="b12f9-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b12f9-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="b12f9-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b12f9-117">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="b12f9-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="b12f9-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="b12f9-118">Remarks</span></span>
-------

<span data-ttu-id="b12f9-119">La fonction **GetNumberOfConsoleInputEvents** signale le nombre total d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée, y compris les enregistrements d’entrée de clavier, de souris et de redimensionnement de fenêtre.</span><span class="sxs-lookup"><span data-stu-id="b12f9-119">The **GetNumberOfConsoleInputEvents** function reports the total number of unread input records in the input buffer, including keyboard, mouse, and window-resizing input records.</span></span> <span data-ttu-id="b12f9-120">Les processus utilisant la fonction [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ou [**ReadConsole**](readconsole.md) peuvent uniquement lire les entrées au clavier.</span><span class="sxs-lookup"><span data-stu-id="b12f9-120">Processes using the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function can only read keyboard input.</span></span> <span data-ttu-id="b12f9-121">Les processus qui utilisent la fonction [**ReadConsoleInput**](readconsoleinput.md) peuvent lire tous les types d’enregistrements d’entrée.</span><span class="sxs-lookup"><span data-stu-id="b12f9-121">Processes using the [**ReadConsoleInput**](readconsoleinput.md) function can read all types of input records.</span></span>

<span data-ttu-id="b12f9-122">Un processus peut spécifier un handle de mémoire tampon d’entrée de la console dans l’une des [fonctions Wait](https://msdn.microsoft.com/library/windows/desktop/ms687069) pour déterminer le moment où une entrée de console n’est pas lue.</span><span class="sxs-lookup"><span data-stu-id="b12f9-122">A process can specify a console input buffer handle in one of the [wait functions](https://msdn.microsoft.com/library/windows/desktop/ms687069) to determine when there is unread console input.</span></span> <span data-ttu-id="b12f9-123">Lorsque la mémoire tampon d’entrée n’est pas vide, l’état d’un handle de mémoire tampon d’entrée de la console est signalé.</span><span class="sxs-lookup"><span data-stu-id="b12f9-123">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="b12f9-124">Pour lire les enregistrements d’entrée d’une mémoire tampon d’entrée de la console sans affecter le nombre d’enregistrements non lus, utilisez la fonction [**PeekConsoleInput**](peekconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="b12f9-124">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="b12f9-125">Pour ignorer tous les enregistrements non lus dans le tampon d’entrée d’une console, utilisez la fonction [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="b12f9-125">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

<a name="requirements"></a><span data-ttu-id="b12f9-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b12f9-126">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b12f9-127">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="b12f9-127">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="b12f9-128">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="b12f9-128">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b12f9-129">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="b12f9-129">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="b12f9-130">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="b12f9-130">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b12f9-131">En-tête</span><span class="sxs-lookup"><span data-stu-id="b12f9-131">Header</span></span></p></td>
<td><span data-ttu-id="b12f9-132">ConsoleApi. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b12f9-132">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b12f9-133">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="b12f9-133">Library</span></span></p></td>
<td><span data-ttu-id="b12f9-134">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="b12f9-134">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b12f9-135">DLL</span><span class="sxs-lookup"><span data-stu-id="b12f9-135">DLL</span></span></p></td>
<td><span data-ttu-id="b12f9-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b12f9-136">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="b12f9-137"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b12f9-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="b12f9-138">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="b12f9-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b12f9-139">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="b12f9-139">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="b12f9-140">Fonctions d’entrée de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="b12f9-140">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="b12f9-141">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="b12f9-141">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="b12f9-142">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="b12f9-142">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="b12f9-143">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="b12f9-143">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="b12f9-144">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="b12f9-144">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

 

 




