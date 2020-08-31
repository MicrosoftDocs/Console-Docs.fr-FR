---
title: FlushConsoleInputBuffer fonction)
description: Vide la mémoire tampon d’entrée de la console. Tous les enregistrements d’entrée actuellement dans la mémoire tampon d’entrée sont ignorés.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/FlushConsoleInputBuffer
- wincon/FlushConsoleInputBuffer
- FlushConsoleInputBuffer
MS-HAID:
- '\_win32\_flushconsoleinputbuffer'
- base.flushconsoleinputbuffer
- consoles.flushconsoleinputbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6f7832d6-1fb2-4ca8-bd07-43123c990851
topic_type:
- apiref
api_name:
- FlushConsoleInputBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: dd184e1fc1f788912be00e9270ccb239c20b8ce8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059208"
---
# <a name="flushconsoleinputbuffer-function"></a><span data-ttu-id="89b9a-105">FlushConsoleInputBuffer fonction)</span><span class="sxs-lookup"><span data-stu-id="89b9a-105">FlushConsoleInputBuffer function</span></span>


<span data-ttu-id="89b9a-106">Vide la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="89b9a-106">Flushes the console input buffer.</span></span> <span data-ttu-id="89b9a-107">Tous les enregistrements d’entrée actuellement dans la mémoire tampon d’entrée sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="89b9a-107">All input records currently in the input buffer are discarded.</span></span>

<a name="syntax"></a><span data-ttu-id="89b9a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89b9a-108">Syntax</span></span>
------

```C
BOOL WINAPI FlushConsoleInputBuffer(
  _In_ HANDLE hConsoleInput
);
```

<a name="parameters"></a><span data-ttu-id="89b9a-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="89b9a-109">Parameters</span></span>
----------

<span data-ttu-id="89b9a-110">*hConsoleInput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="89b9a-110">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="89b9a-111">Handle vers la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="89b9a-111">A handle to the console input buffer.</span></span> <span data-ttu-id="89b9a-112">Le descripteur doit avoir le droit d’accès en \*\* \_ écriture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="89b9a-112">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="89b9a-113">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="89b9a-113">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<a name="return-value"></a><span data-ttu-id="89b9a-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="89b9a-114">Return value</span></span>
------------

<span data-ttu-id="89b9a-115">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="89b9a-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="89b9a-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="89b9a-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="89b9a-117">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="89b9a-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="89b9a-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="89b9a-118">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="89b9a-119">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="89b9a-119">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="89b9a-120">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="89b9a-120">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="89b9a-121">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="89b9a-121">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="89b9a-122">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="89b9a-122">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="89b9a-123">En-tête</span><span class="sxs-lookup"><span data-stu-id="89b9a-123">Header</span></span></p></td>
<td><span data-ttu-id="89b9a-124">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="89b9a-124">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="89b9a-125">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="89b9a-125">Library</span></span></p></td>
<td><span data-ttu-id="89b9a-126">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="89b9a-126">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="89b9a-127">DLL</span><span class="sxs-lookup"><span data-stu-id="89b9a-127">DLL</span></span></p></td>
<td><span data-ttu-id="89b9a-128">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="89b9a-128">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="89b9a-129"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89b9a-129"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="89b9a-130">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="89b9a-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="89b9a-131">Fonctions d’entrée de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="89b9a-131">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="89b9a-132">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="89b9a-132">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="89b9a-133">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="89b9a-133">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="89b9a-134">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="89b9a-134">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="89b9a-135">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="89b9a-135">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 




