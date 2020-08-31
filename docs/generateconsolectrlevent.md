---
title: GenerateConsoleCtrlEvent fonction)
description: Envoie un signal spécifié à un groupe de processus de console qui partage la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/GenerateConsoleCtrlEvent
- wincon/GenerateConsoleCtrlEvent
- GenerateConsoleCtrlEvent
MS-HAID:
- '\_win32\_generateconsolectrlevent'
- base.generateconsolectrlevent
- consoles.generateconsolectrlevent
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ed392d97-6fd0-4256-a783-bc7d27d01a10
topic_type:
- apiref
api_name:
- GenerateConsoleCtrlEvent
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 31c0330a002362542a799ab7e038d3f65497ded3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059200"
---
# <a name="generateconsolectrlevent-function"></a><span data-ttu-id="bdafe-104">GenerateConsoleCtrlEvent fonction)</span><span class="sxs-lookup"><span data-stu-id="bdafe-104">GenerateConsoleCtrlEvent function</span></span>


<span data-ttu-id="bdafe-105">Envoie un signal spécifié à un groupe de processus de console qui partage la console associée au processus appelant.</span><span class="sxs-lookup"><span data-stu-id="bdafe-105">Sends a specified signal to a console process group that shares the console associated with the calling process.</span></span>

<a name="syntax"></a><span data-ttu-id="bdafe-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdafe-106">Syntax</span></span>
------

```C
BOOL WINAPI GenerateConsoleCtrlEvent(
  _In_ DWORD dwCtrlEvent,
  _In_ DWORD dwProcessGroupId
);
```

<a name="parameters"></a><span data-ttu-id="bdafe-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bdafe-107">Parameters</span></span>
----------

<span data-ttu-id="bdafe-108">*dwCtrlEvent* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="bdafe-108">*dwCtrlEvent* \[in\]</span></span>  
<span data-ttu-id="bdafe-109">Type de signal à générer.</span><span class="sxs-lookup"><span data-stu-id="bdafe-109">The type of signal to be generated.</span></span> <span data-ttu-id="bdafe-110">Ce paramètre peut prendre l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="bdafe-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="bdafe-111">Value</span><span class="sxs-lookup"><span data-stu-id="bdafe-111">Value</span></span></th>
<th><span data-ttu-id="bdafe-112">Signification</span><span class="sxs-lookup"><span data-stu-id="bdafe-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="bdafe-113"><span id="CTRL_C_EVENT"></span><span id="ctrl_c_event"></span>
<strong>CTRL_C_EVENT</strong> 0</span><span class="sxs-lookup"><span data-stu-id="bdafe-113"><span id="CTRL_C_EVENT"></span><span id="ctrl_c_event"></span>
<strong>CTRL_C_EVENT</strong> 0</span></span></td>
<td><p><span data-ttu-id="bdafe-114">Génère un signal CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="bdafe-114">Generates a CTRL+C signal.</span></span> <span data-ttu-id="bdafe-115">Ce signal ne peut pas être généré pour les groupes de processus.</span><span class="sxs-lookup"><span data-stu-id="bdafe-115">This signal cannot be generated for process groups.</span></span> <span data-ttu-id="bdafe-116">Si <em>dwProcessGroupId</em> est différent de zéro, cette fonction est réussie, mais le signal Ctrl + C n’est pas reçu par les processus au sein du groupe de processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="bdafe-116">If <em>dwProcessGroupId</em> is nonzero, this function will succeed, but the CTRL+C signal will not be received by processes within the specified process group.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="bdafe-117"><span id="CTRL_BREAK_EVENT"></span><span id="ctrl_break_event"></span>
<strong>CTRL_BREAK_EVENT</strong> 1</span><span class="sxs-lookup"><span data-stu-id="bdafe-117"><span id="CTRL_BREAK_EVENT"></span><span id="ctrl_break_event"></span>
<strong>CTRL_BREAK_EVENT</strong> 1</span></span></td>
<td><p><span data-ttu-id="bdafe-118">Génère un signal CTRL + ATTN.</span><span class="sxs-lookup"><span data-stu-id="bdafe-118">Generates a CTRL+BREAK signal.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="bdafe-119">*dwProcessGroupId* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="bdafe-119">*dwProcessGroupId* \[in\]</span></span>  
<span data-ttu-id="bdafe-120">Identificateur du groupe de processus devant recevoir le signal.</span><span class="sxs-lookup"><span data-stu-id="bdafe-120">The identifier of the process group to receive the signal.</span></span> <span data-ttu-id="bdafe-121">Un groupe de processus est créé lorsque l’indicateur de création d’un \*\* \_ nouveau \_ \_ groupe de processus\*\* est spécifié dans un appel à la fonction [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) .</span><span class="sxs-lookup"><span data-stu-id="bdafe-121">A process group is created when the **CREATE\_NEW\_PROCESS\_GROUP** flag is specified in a call to the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function.</span></span> <span data-ttu-id="bdafe-122">L’identificateur de processus du nouveau processus est également l’identificateur de groupe de processus d’un nouveau groupe de processus.</span><span class="sxs-lookup"><span data-stu-id="bdafe-122">The process identifier of the new process is also the process group identifier of a new process group.</span></span> <span data-ttu-id="bdafe-123">Le groupe de processus comprend tous les processus qui sont des descendants du processus racine.</span><span class="sxs-lookup"><span data-stu-id="bdafe-123">The process group includes all processes that are descendants of the root process.</span></span> <span data-ttu-id="bdafe-124">Seuls les processus du groupe qui partagent la même console que le processus appelant reçoivent le signal.</span><span class="sxs-lookup"><span data-stu-id="bdafe-124">Only those processes in the group that share the same console as the calling process receive the signal.</span></span> <span data-ttu-id="bdafe-125">En d’autres termes, si un processus du groupe crée une nouvelle console, ce processus ne reçoit pas le signal, ni ses descendants.</span><span class="sxs-lookup"><span data-stu-id="bdafe-125">In other words, if a process in the group creates a new console, that process does not receive the signal, nor do its descendants.</span></span>

<span data-ttu-id="bdafe-126">Si ce paramètre est égal à zéro, le signal est généré dans tous les processus qui partagent la console du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="bdafe-126">If this parameter is zero, the signal is generated in all processes that share the console of the calling process.</span></span>

<a name="return-value"></a><span data-ttu-id="bdafe-127">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="bdafe-127">Return value</span></span>
------------

<span data-ttu-id="bdafe-128">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="bdafe-128">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="bdafe-129">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="bdafe-129">If the function fails, the return value is zero.</span></span> <span data-ttu-id="bdafe-130">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="bdafe-130">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="bdafe-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="bdafe-131">Remarks</span></span>
-------

<span data-ttu-id="bdafe-132">**GenerateConsoleCtrlEvent** entraîne l’appel des fonctions du gestionnaire de contrôle des processus dans le groupe cible.</span><span class="sxs-lookup"><span data-stu-id="bdafe-132">**GenerateConsoleCtrlEvent** causes the control handler functions of processes in the target group to be called.</span></span> <span data-ttu-id="bdafe-133">Tous les processus de console ont une fonction de gestionnaire par défaut qui appelle la fonction [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) .</span><span class="sxs-lookup"><span data-stu-id="bdafe-133">All console processes have a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function.</span></span> <span data-ttu-id="bdafe-134">Un processus de console peut utiliser la fonction [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) pour installer ou supprimer d’autres fonctions de gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="bdafe-134">A console process can use the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function to install or remove other handler functions.</span></span>

<span data-ttu-id="bdafe-135">[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) peut également activer un attribut pouvant être hérité qui amène le processus appelant à ignorer les signaux Ctrl + C.</span><span class="sxs-lookup"><span data-stu-id="bdafe-135">[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) can also enable an inheritable attribute that causes the calling process to ignore CTRL+C signals.</span></span> <span data-ttu-id="bdafe-136">Si **GenerateConsoleCtrlEvent** envoie un signal Ctrl + C à un processus pour lequel cet attribut est activé, les fonctions de gestionnaire pour ce processus ne sont pas appelées.</span><span class="sxs-lookup"><span data-stu-id="bdafe-136">If **GenerateConsoleCtrlEvent** sends a CTRL+C signal to a process for which this attribute is enabled, the handler functions for that process are not called.</span></span> <span data-ttu-id="bdafe-137">Les signaux CTRL + ATTN entraînent toujours l’appel des fonctions du gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="bdafe-137">CTRL+BREAK signals always cause the handler functions to be called.</span></span>

<a name="requirements"></a><span data-ttu-id="bdafe-138">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bdafe-138">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="bdafe-139">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="bdafe-139">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="bdafe-140">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="bdafe-140">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bdafe-141">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="bdafe-141">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="bdafe-142">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="bdafe-142">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bdafe-143">En-tête</span><span class="sxs-lookup"><span data-stu-id="bdafe-143">Header</span></span></p></td>
<td><span data-ttu-id="bdafe-144">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="bdafe-144">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bdafe-145">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="bdafe-145">Library</span></span></p></td>
<td><span data-ttu-id="bdafe-146">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="bdafe-146">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bdafe-147">DLL</span><span class="sxs-lookup"><span data-stu-id="bdafe-147">DLL</span></span></p></td>
<td><span data-ttu-id="bdafe-148">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="bdafe-148">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="bdafe-149"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdafe-149"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="bdafe-150">Gestionnaires de contrôle de console</span><span class="sxs-lookup"><span data-stu-id="bdafe-150">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="bdafe-151">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="bdafe-151">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="bdafe-152">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="bdafe-152">**CreateProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[<span data-ttu-id="bdafe-153">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="bdafe-153">**ExitProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[<span data-ttu-id="bdafe-154">**SetConsoleCtrlHandler**</span><span class="sxs-lookup"><span data-stu-id="bdafe-154">**SetConsoleCtrlHandler**</span></span>](setconsolectrlhandler.md)

 

 




