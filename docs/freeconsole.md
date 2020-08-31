---
title: FreeConsole fonction)
description: Consultez les informations de référence sur la fonction FreeConsole, qui détache le processus appelant à partir de sa console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi/FreeConsole
- wincon/FreeConsole
- FreeConsole
MS-HAID:
- '\_win32\_freeconsole'
- base.freeconsole
- consoles.freeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6c525325-696e-4d8b-8337-cbf9e31c900c
topic_type:
- apiref
api_name:
- FreeConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 3c8ba7b236b379bb57729538e065afebb68cc0cf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059204"
---
# <a name="freeconsole-function"></a><span data-ttu-id="d2bbd-104">FreeConsole fonction)</span><span class="sxs-lookup"><span data-stu-id="d2bbd-104">FreeConsole function</span></span>


<span data-ttu-id="d2bbd-105">Détache le processus appelant de sa console.</span><span class="sxs-lookup"><span data-stu-id="d2bbd-105">Detaches the calling process from its console.</span></span>

<a name="syntax"></a><span data-ttu-id="d2bbd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2bbd-106">Syntax</span></span>
------

```C
BOOL WINAPI FreeConsole(void);
```

<a name="parameters"></a><span data-ttu-id="d2bbd-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d2bbd-107">Parameters</span></span>
----------

<span data-ttu-id="d2bbd-108">Cette fonction n’a pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="d2bbd-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="d2bbd-109">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="d2bbd-109">Return value</span></span>
------------

<span data-ttu-id="d2bbd-110">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="d2bbd-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d2bbd-111">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="d2bbd-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d2bbd-112">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="d2bbd-112">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="d2bbd-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="d2bbd-113">Remarks</span></span>
-------

<span data-ttu-id="d2bbd-114">Un processus peut être attaché à au plus une console.</span><span class="sxs-lookup"><span data-stu-id="d2bbd-114">A process can be attached to at most one console.</span></span> <span data-ttu-id="d2bbd-115">Si le processus appelant n’est pas déjà attaché à une console, le code d’erreur retourné est **erreur : \_ \_ paramètre non valide** (87).</span><span class="sxs-lookup"><span data-stu-id="d2bbd-115">If the calling process is not already attached to a console, the error code returned is **ERROR\_INVALID\_PARAMETER** (87).</span></span>

<span data-ttu-id="d2bbd-116">Un processus peut utiliser la fonction **FreeConsole** pour se détacher de sa console.</span><span class="sxs-lookup"><span data-stu-id="d2bbd-116">A process can use the **FreeConsole** function to detach itself from its console.</span></span> <span data-ttu-id="d2bbd-117">Si d’autres processus partagent la console, la console n’est pas détruite, mais le processus qui a appelé **FreeConsole** ne peut pas y faire référence.</span><span class="sxs-lookup"><span data-stu-id="d2bbd-117">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="d2bbd-118">Une console est fermée lorsque le dernier processus qui lui est associé se termine ou appelle **FreeConsole**.</span><span class="sxs-lookup"><span data-stu-id="d2bbd-118">A console is closed when the last process attached to it terminates or calls **FreeConsole**.</span></span> <span data-ttu-id="d2bbd-119">Une fois qu’un processus a appelé **FreeConsole**, il peut appeler la fonction [**AllocConsole**](allocconsole.md) pour créer une nouvelle console ou [**AttachConsole**](attachconsole.md) à attacher à une autre console.</span><span class="sxs-lookup"><span data-stu-id="d2bbd-119">After a process calls **FreeConsole**, it can call the [**AllocConsole**](allocconsole.md) function to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<a name="requirements"></a><span data-ttu-id="d2bbd-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d2bbd-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="d2bbd-121">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="d2bbd-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="d2bbd-122">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="d2bbd-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d2bbd-123">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="d2bbd-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="d2bbd-124">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="d2bbd-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d2bbd-125">En-tête</span><span class="sxs-lookup"><span data-stu-id="d2bbd-125">Header</span></span></p></td>
<td><span data-ttu-id="d2bbd-126">ConsoleApi. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d2bbd-126">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d2bbd-127">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="d2bbd-127">Library</span></span></p></td>
<td><span data-ttu-id="d2bbd-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="d2bbd-128">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d2bbd-129">DLL</span><span class="sxs-lookup"><span data-stu-id="d2bbd-129">DLL</span></span></p></td>
<td><span data-ttu-id="d2bbd-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d2bbd-130">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="d2bbd-131"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2bbd-131"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="d2bbd-132">**AllocConsole**</span><span class="sxs-lookup"><span data-stu-id="d2bbd-132">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="d2bbd-133">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="d2bbd-133">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="d2bbd-134">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="d2bbd-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d2bbd-135">Consoles</span><span class="sxs-lookup"><span data-stu-id="d2bbd-135">Consoles</span></span>](consoles.md)

 

 




