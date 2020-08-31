---
title: AttachConsole fonction)
description: Consultez les informations de référence sur la fonction AttachConsole, qui attache le processus appelant à la console du processus spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- base.attachconsole
- consoles.attachconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c4048a2fb4c93d9f286ffc1ef7f38923836f37bf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059385"
---
# <a name="attachconsole-function"></a><span data-ttu-id="103d9-104">AttachConsole fonction)</span><span class="sxs-lookup"><span data-stu-id="103d9-104">AttachConsole function</span></span>


<span data-ttu-id="103d9-105">Joint le processus appelant à la console du processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="103d9-105">Attaches the calling process to the console of the specified process.</span></span>

<a name="syntax"></a><span data-ttu-id="103d9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="103d9-106">Syntax</span></span>
------

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

<a name="parameters"></a><span data-ttu-id="103d9-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="103d9-107">Parameters</span></span>
----------

<span data-ttu-id="103d9-108">*dwProcessId* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="103d9-108">*dwProcessId* \[in\]</span></span>  
<span data-ttu-id="103d9-109">Identificateur du processus dont la console doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="103d9-109">The identifier of the process whose console is to be used.</span></span> <span data-ttu-id="103d9-110">Ce paramètre peut prendre l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="103d9-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="103d9-111">Value</span><span class="sxs-lookup"><span data-stu-id="103d9-111">Value</span></span></th>
<th><span data-ttu-id="103d9-112">Signification</span><span class="sxs-lookup"><span data-stu-id="103d9-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="103d9-113"><em>ELECTRIQUE</em></span><span class="sxs-lookup"><span data-stu-id="103d9-113"><em>pid</em></span></span></td>
<td><p><span data-ttu-id="103d9-114">Utilisez la console du processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="103d9-114">Use the console of the specified process.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="103d9-115"><span id="ATTACH_PARENT_PROCESS"></span><span id="attach_parent_process"></span>
<strong>ATTACH_PARENT_PROCESS</strong> (DWORD)-1</span><span class="sxs-lookup"><span data-stu-id="103d9-115"><span id="ATTACH_PARENT_PROCESS"></span><span id="attach_parent_process"></span>
<strong>ATTACH_PARENT_PROCESS</strong> (DWORD)-1</span></span></td>
<td><p><span data-ttu-id="103d9-116">Utilisez la console du parent du processus en cours.</span><span class="sxs-lookup"><span data-stu-id="103d9-116">Use the console of the parent of the current process.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="103d9-117">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="103d9-117">Return value</span></span>
------------

<span data-ttu-id="103d9-118">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="103d9-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="103d9-119">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="103d9-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="103d9-120">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="103d9-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="103d9-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="103d9-121">Remarks</span></span>
-------

<span data-ttu-id="103d9-122">Un processus peut être attaché à au plus une console.</span><span class="sxs-lookup"><span data-stu-id="103d9-122">A process can be attached to at most one console.</span></span> <span data-ttu-id="103d9-123">Si le processus appelant est déjà attaché à une console, le code d’erreur retourné est **erreur \_ accès \_ refusé** (5).</span><span class="sxs-lookup"><span data-stu-id="103d9-123">If the calling process is already attached to a console, the error code returned is **ERROR\_ACCESS\_DENIED** (5).</span></span> <span data-ttu-id="103d9-124">Si le processus spécifié n’a pas de console, le code d’erreur retourné **est \_ erreur \_ handle non valide** (6).</span><span class="sxs-lookup"><span data-stu-id="103d9-124">If the specified process does not have a console, the error code returned is **ERROR\_INVALID\_HANDLE** (6).</span></span> <span data-ttu-id="103d9-125">Si le processus spécifié n’existe pas, le code d’erreur retourné est un \*\*paramètre d’erreur \_ non valide \_ \*\* (87).</span><span class="sxs-lookup"><span data-stu-id="103d9-125">If the specified process does not exist, the error code returned is **ERROR\_INVALID\_PARAMETER** (87).</span></span>

<span data-ttu-id="103d9-126">Un processus peut utiliser la fonction [**FreeConsole**](freeconsole.md) pour se détacher de sa console.</span><span class="sxs-lookup"><span data-stu-id="103d9-126">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console.</span></span> <span data-ttu-id="103d9-127">Si d’autres processus partagent la console, la console n’est pas détruite, mais le processus qui a appelé **FreeConsole** ne peut pas y faire référence.</span><span class="sxs-lookup"><span data-stu-id="103d9-127">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="103d9-128">Une console est fermée lorsque le dernier processus qui lui est associé se termine ou appelle **FreeConsole**.</span><span class="sxs-lookup"><span data-stu-id="103d9-128">A console is closed when the last process attached to it terminates or calls **FreeConsole**.</span></span> <span data-ttu-id="103d9-129">Une fois qu’un processus a appelé **FreeConsole**, il peut appeler la fonction [**AllocConsole**](allocconsole.md) pour créer une nouvelle console ou **AttachConsole** à attacher à une autre console.</span><span class="sxs-lookup"><span data-stu-id="103d9-129">After a process calls **FreeConsole**, it can call the [**AllocConsole**](allocconsole.md) function to create a new console or **AttachConsole** to attach to another console.</span></span>

<span data-ttu-id="103d9-130">Pour compiler une application qui utilise cette fonction, définissez \*\* \_ Win32 \_ winnt\*\* comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="103d9-130">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="103d9-131">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="103d9-131">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="103d9-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="103d9-132">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="103d9-133">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="103d9-133">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="103d9-134">Windows XP [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="103d9-134">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="103d9-135">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="103d9-135">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="103d9-136">Windows Server 2003 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="103d9-136">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="103d9-137">En-tête</span><span class="sxs-lookup"><span data-stu-id="103d9-137">Header</span></span></p></td>
<td><span data-ttu-id="103d9-138">ConsoleApi. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="103d9-138">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="103d9-139">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="103d9-139">Library</span></span></p></td>
<td><span data-ttu-id="103d9-140">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="103d9-140">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="103d9-141">DLL</span><span class="sxs-lookup"><span data-stu-id="103d9-141">DLL</span></span></p></td>
<td><span data-ttu-id="103d9-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="103d9-142">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="103d9-143"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="103d9-143"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="103d9-144">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="103d9-144">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="103d9-145">Consoles</span><span class="sxs-lookup"><span data-stu-id="103d9-145">Consoles</span></span>](consoles.md)

[<span data-ttu-id="103d9-146">**AllocConsole**</span><span class="sxs-lookup"><span data-stu-id="103d9-146">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="103d9-147">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="103d9-147">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="103d9-148">**GetConsoleProcessList**</span><span class="sxs-lookup"><span data-stu-id="103d9-148">**GetConsoleProcessList**</span></span>](getconsoleprocesslist.md)

 

 




