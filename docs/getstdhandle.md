---
title: GetStdHandle fonction)
description: Récupère un handle vers l’appareil standard spécifié (entrée standard, sortie standard ou erreur standard).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- processenv/GetStdHandle
- winbase/GetStdHandle
- GetStdHandle
MS-HAID:
- '\_win32\_getstdhandle'
- base.getstdhandle
- consoles.getstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 23cd76e9-671a-48d0-9b82-2beda8917348
topic_type:
- apiref
api_name:
- GetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 613aacf4052e8e3b38c0a3e254ac4dd2b55ced5d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059081"
---
# <a name="getstdhandle-function"></a><span data-ttu-id="47718-104">GetStdHandle fonction)</span><span class="sxs-lookup"><span data-stu-id="47718-104">GetStdHandle function</span></span>


<span data-ttu-id="47718-105">Récupère un handle vers l’appareil standard spécifié (entrée standard, sortie standard ou erreur standard).</span><span class="sxs-lookup"><span data-stu-id="47718-105">Retrieves a handle to the specified standard device (standard input, standard output, or standard error).</span></span>

<a name="syntax"></a><span data-ttu-id="47718-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47718-106">Syntax</span></span>
------

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

<a name="parameters"></a><span data-ttu-id="47718-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="47718-107">Parameters</span></span>
----------

<span data-ttu-id="47718-108">*nStdHandle* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="47718-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="47718-109">Appareil standard.</span><span class="sxs-lookup"><span data-stu-id="47718-109">The standard device.</span></span> <span data-ttu-id="47718-110">Ce paramètre peut prendre l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="47718-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="47718-111">Value</span><span class="sxs-lookup"><span data-stu-id="47718-111">Value</span></span></th>
<th><span data-ttu-id="47718-112">Signification</span><span class="sxs-lookup"><span data-stu-id="47718-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="47718-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</span><span class="sxs-lookup"><span data-stu-id="47718-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD) -10</span></span></td>
<td><p><span data-ttu-id="47718-114">Périphérique d’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="47718-114">The standard input device.</span></span> <span data-ttu-id="47718-115">Au départ, il s’agit de la mémoire tampon d’entrée de la console, CONIN $.</span><span class="sxs-lookup"><span data-stu-id="47718-115">Initially, this is the console input buffer, CONIN$.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="47718-116"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</span><span class="sxs-lookup"><span data-stu-id="47718-116"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD) -11</span></span></td>
<td><p><span data-ttu-id="47718-117">Périphérique de sortie standard.</span><span class="sxs-lookup"><span data-stu-id="47718-117">The standard output device.</span></span> <span data-ttu-id="47718-118">Initialement, il s’agit de la mémoire tampon d’écran active de la console, CONOUT $.</span><span class="sxs-lookup"><span data-stu-id="47718-118">Initially, this is the active console screen buffer, CONOUT$.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="47718-119"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</span><span class="sxs-lookup"><span data-stu-id="47718-119"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD) -12</span></span></td>
<td><p><span data-ttu-id="47718-120">Périphérique d’erreur standard.</span><span class="sxs-lookup"><span data-stu-id="47718-120">The standard error device.</span></span> <span data-ttu-id="47718-121">Initialement, il s’agit de la mémoire tampon d’écran active de la console, CONOUT $.</span><span class="sxs-lookup"><span data-stu-id="47718-121">Initially, this is the active console screen buffer, CONOUT$.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="47718-122">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="47718-122">Return value</span></span>
------------

<span data-ttu-id="47718-123">Si la fonction s’exécute correctement, la valeur de retour est un handle vers l’appareil spécifié, ou un handle Redirigé défini par un appel précédent à [**SetStdHandle**](setstdhandle.md).</span><span class="sxs-lookup"><span data-stu-id="47718-123">If the function succeeds, the return value is a handle to the specified device, or a redirected handle set by a previous call to [**SetStdHandle**](setstdhandle.md).</span></span> <span data-ttu-id="47718-124">Le descripteur dispose de droits d’accès en \*\* \_ écriture\*\* génériques \*\* \_ en lecture\*\* et génériques, sauf si l’application a utilisé **SetStdHandle** pour définir un descripteur standard avec un accès plus faible.</span><span class="sxs-lookup"><span data-stu-id="47718-124">The handle has **GENERIC\_READ** and **GENERIC\_WRITE** access rights, unless the application has used **SetStdHandle** to set a standard handle with lesser access.</span></span>

<span data-ttu-id="47718-125">Si la fonction échoue, la valeur de retour est une \*\* \_ \_ valeur de handle non valide\*\*.</span><span class="sxs-lookup"><span data-stu-id="47718-125">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="47718-126">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="47718-126">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="47718-127">Si une application n’a pas de descripteurs standard associés, comme un service s’exécutant sur un bureau interactif, et n’a pas été redirigée, la valeur de retour est **null**.</span><span class="sxs-lookup"><span data-stu-id="47718-127">If an application does not have associated standard handles, such as a service running on an interactive desktop, and has not redirected them, the return value is **NULL**.</span></span>

<a name="remarks"></a><span data-ttu-id="47718-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="47718-128">Remarks</span></span>
-------

<span data-ttu-id="47718-129">Les handles retournés par **GetStdHandle** peuvent être utilisés par les applications qui doivent lire ou écrire dans la console.</span><span class="sxs-lookup"><span data-stu-id="47718-129">Handles returned by **GetStdHandle** can be used by applications that need to read from or write to the console.</span></span> <span data-ttu-id="47718-130">Quand une console est créée, le descripteur d’entrée standard est un handle de la mémoire tampon d’entrée de la console, et la sortie standard et les descripteurs d’erreur standard sont des handles de la mémoire tampon d’écran active de la console.</span><span class="sxs-lookup"><span data-stu-id="47718-130">When a console is created, the standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles of the console's active screen buffer.</span></span> <span data-ttu-id="47718-131">Ces handles peuvent être utilisés par les fonctions [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) , ou par n’importe quelle fonction de console qui accède à la mémoire tampon d’entrée de la console ou à une mémoire tampon d’écran (par exemple, les fonctions [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md)ou [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) ).</span><span class="sxs-lookup"><span data-stu-id="47718-131">These handles can be used by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) functions, or by any of the console functions that access the console input buffer or a screen buffer (for example, the [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md), or [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) functions).</span></span>

<span data-ttu-id="47718-132">Les handles standard d’un processus peuvent être redirigés par un appel à [**SetStdHandle**](setstdhandle.md), auquel cas **GetStdHandle** retourne le handle Redirigé.</span><span class="sxs-lookup"><span data-stu-id="47718-132">The standard handles of a process may be redirected by a call to [**SetStdHandle**](setstdhandle.md), in which case **GetStdHandle** returns the redirected handle.</span></span> <span data-ttu-id="47718-133">Si les handles standard ont été redirigés, vous pouvez spécifier la valeur CONIN $ dans un appel à la fonction [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) pour obtenir un handle vers la mémoire tampon d’entrée d’une console.</span><span class="sxs-lookup"><span data-stu-id="47718-133">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="47718-134">De même, vous pouvez spécifier la valeur CONOUT $ pour obtenir un handle vers la mémoire tampon d’écran active d’une console.</span><span class="sxs-lookup"><span data-stu-id="47718-134">Similarly, you can specify the CONOUT$ value to get a handle to a console's active screen buffer.</span></span>

### <a name="span-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanattachdetach-behavior"></a><span data-ttu-id="47718-135"><span id="Attach_detach_behavior"></span><span id="attach_detach_behavior"></span><span id="ATTACH_DETACH_BEHAVIOR"></span>Comportement d’attachement/détachement</span><span class="sxs-lookup"><span data-stu-id="47718-135"><span id="Attach_detach_behavior"></span><span id="attach_detach_behavior"></span><span id="ATTACH_DETACH_BEHAVIOR"></span>Attach/detach behavior</span></span>

<span data-ttu-id="47718-136">Lors de l’attachement à une nouvelle console, les handles standard sont toujours remplacés par des handles de console, sauf si **STARTF \_ USESTDHANDLES** a été spécifié lors de la création du processus.</span><span class="sxs-lookup"><span data-stu-id="47718-136">When attaching to a new console, standard handles are always replaced with console handles unless **STARTF\_USESTDHANDLES** was specified during process creation.</span></span>

<span data-ttu-id="47718-137">Si la valeur existante du handle standard est **null**, ou si la valeur existante du handle standard ressemble à un pseudohandle de console, le handle est remplacé par un handle de console.</span><span class="sxs-lookup"><span data-stu-id="47718-137">If the existing value of the standard handle is **NULL**, or the existing value of the standard handle looks like a console pseudohandle, the handle is replaced with a console handle.</span></span>

<span data-ttu-id="47718-138">Lorsqu’un parent utilise à la fois **Create \_ New \_ console** et **STARTF \_ USESTDHANDLES** pour créer un processus de console, les handles standard ne sont pas remplacés, sauf si la valeur existante du handle standard est null ou un pseudohandle de console.</span><span class="sxs-lookup"><span data-stu-id="47718-138">When a parent uses both **CREATE\_NEW\_CONSOLE** and **STARTF\_USESTDHANDLES** to create a console process, standard handles will not be replaced unless the existing value of the standard handle is NULL or a console pseudohandle.</span></span>

<a name="examples"></a><span data-ttu-id="47718-139">Exemples</span><span class="sxs-lookup"><span data-stu-id="47718-139">Examples</span></span>
--------

<span data-ttu-id="47718-140">Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="47718-140">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="47718-141">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="47718-141">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="47718-142">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="47718-142">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="47718-143">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="47718-143">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="47718-144">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="47718-144">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="47718-145">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="47718-145">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="47718-146">En-tête</span><span class="sxs-lookup"><span data-stu-id="47718-146">Header</span></span></p></td>
<td><span data-ttu-id="47718-147">ProcessEnv. h (via Winbase. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="47718-147">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="47718-148">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="47718-148">Library</span></span></p></td>
<td><span data-ttu-id="47718-149">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="47718-149">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="47718-150">DLL</span><span class="sxs-lookup"><span data-stu-id="47718-150">DLL</span></span></p></td>
<td><span data-ttu-id="47718-151">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="47718-151">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="47718-152"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47718-152"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="47718-153">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="47718-153">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="47718-154">Handles de la console</span><span class="sxs-lookup"><span data-stu-id="47718-154">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="47718-155">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="47718-155">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="47718-156">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="47718-156">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="47718-157">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="47718-157">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="47718-158">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="47718-158">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="47718-159">**SetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="47718-159">**SetStdHandle**</span></span>](setstdhandle.md)

[<span data-ttu-id="47718-160">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="47718-160">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="47718-161">**Appel**</span><span class="sxs-lookup"><span data-stu-id="47718-161">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




