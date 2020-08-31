---
title: GetConsoleSelectionInfo fonction)
description: Consultez les informations de référence sur la fonction GetConsoleSelectionInfo, qui récupère des informations sur la sélection de la console actuelle.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetConsoleSelectionInfo
- wincon/GetConsoleSelectionInfo
- GetConsoleSelectionInfo
MS-HAID:
- '\_win32\_getconsoleselectioninfo'
- base.getconsoleselectioninfo
- consoles.getconsoleselectioninfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 912efe9d-75dd-43bd-8dca-08671b5ed79c
topic_type:
- apiref
api_name:
- GetConsoleSelectionInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: d29a960bc6b8d96d98e0667084e31354f2aa9653
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059121"
---
# <a name="getconsoleselectioninfo-function"></a><span data-ttu-id="517ce-104">GetConsoleSelectionInfo fonction)</span><span class="sxs-lookup"><span data-stu-id="517ce-104">GetConsoleSelectionInfo function</span></span>


<span data-ttu-id="517ce-105">Récupère des informations sur la sélection de la console actuelle.</span><span class="sxs-lookup"><span data-stu-id="517ce-105">Retrieves information about the current console selection.</span></span>

<a name="syntax"></a><span data-ttu-id="517ce-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="517ce-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleSelectionInfo(
  _Out_ PCONSOLE_SELECTION_INFO lpConsoleSelectionInfo
);
```

<a name="parameters"></a><span data-ttu-id="517ce-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="517ce-107">Parameters</span></span>
----------

<span data-ttu-id="517ce-108">*lpConsoleSelectionInfo* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="517ce-108">*lpConsoleSelectionInfo* \[out\]</span></span>  
<span data-ttu-id="517ce-109">Pointeur vers une structure [**d' \_ \_ informations de sélection**](console-selection-info-str.md) de la console qui reçoit les informations de sélection.</span><span class="sxs-lookup"><span data-stu-id="517ce-109">A pointer to a [**CONSOLE\_SELECTION\_INFO**](console-selection-info-str.md) structure that receives the selection information.</span></span>

<a name="return-value"></a><span data-ttu-id="517ce-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="517ce-110">Return value</span></span>
------------

<span data-ttu-id="517ce-111">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="517ce-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="517ce-112">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="517ce-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="517ce-113">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="517ce-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="517ce-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="517ce-114">Remarks</span></span>
-------

<span data-ttu-id="517ce-115">Pour compiler une application qui utilise cette fonction, définissez \*\* \_ Win32 \_ winnt\*\* comme 0x0500 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="517ce-115">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="517ce-116">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="517ce-116">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="517ce-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="517ce-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="517ce-118">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="517ce-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="517ce-119">Windows XP [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="517ce-119">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="517ce-120">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="517ce-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="517ce-121">Windows Server 2003 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="517ce-121">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="517ce-122">En-tête</span><span class="sxs-lookup"><span data-stu-id="517ce-122">Header</span></span></p></td>
<td><span data-ttu-id="517ce-123">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="517ce-123">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="517ce-124">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="517ce-124">Library</span></span></p></td>
<td><span data-ttu-id="517ce-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="517ce-125">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="517ce-126">DLL</span><span class="sxs-lookup"><span data-stu-id="517ce-126">DLL</span></span></p></td>
<td><span data-ttu-id="517ce-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="517ce-127">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="517ce-128"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="517ce-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="517ce-129">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="517ce-129">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="517ce-130">Sélection de la console</span><span class="sxs-lookup"><span data-stu-id="517ce-130">Console Selection</span></span>](console-selection.md)

[<span data-ttu-id="517ce-131">**\_informations sur la sélection de la console \_**</span><span class="sxs-lookup"><span data-stu-id="517ce-131">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)

 

 




