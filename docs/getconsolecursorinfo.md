---
title: GetConsoleCursorInfo fonction)
description: Récupère des informations sur la taille et la visibilité du curseur pour la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/GetConsoleCursorInfo
- wincon/GetConsoleCursorInfo
- GetConsoleCursorInfo
MS-HAID:
- '\_win32\_getconsolecursorinfo'
- base.getconsolecursorinfo
- consoles.getconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6200577d-8d84-46bd-9330-d0b6cbbb3e52
topic_type:
- apiref
api_name:
- GetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d87fe0828451615e837c1c6c809a0160f15cf018
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059165"
---
# <a name="getconsolecursorinfo-function"></a><span data-ttu-id="bfabf-104">GetConsoleCursorInfo fonction)</span><span class="sxs-lookup"><span data-stu-id="bfabf-104">GetConsoleCursorInfo function</span></span>


<span data-ttu-id="bfabf-105">Récupère des informations sur la taille et la visibilité du curseur pour la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bfabf-105">Retrieves information about the size and visibility of the cursor for the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="bfabf-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfabf-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleCursorInfo(
  _In_  HANDLE               hConsoleOutput,
  _Out_ PCONSOLE_CURSOR_INFO lpConsoleCursorInfo
);
```

<a name="parameters"></a><span data-ttu-id="bfabf-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bfabf-107">Parameters</span></span>
----------

<span data-ttu-id="bfabf-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="bfabf-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="bfabf-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="bfabf-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="bfabf-110">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="bfabf-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="bfabf-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="bfabf-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="bfabf-112">*lpConsoleCursorInfo* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="bfabf-112">*lpConsoleCursorInfo* \[out\]</span></span>  
<span data-ttu-id="bfabf-113">Pointeur vers une structure [**d' \_ \_ informations de curseur de console**](console-cursor-info-str.md) qui reçoit des informations sur le curseur de la console.</span><span class="sxs-lookup"><span data-stu-id="bfabf-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that receives information about the console's cursor.</span></span>

<a name="return-value"></a><span data-ttu-id="bfabf-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="bfabf-114">Return value</span></span>
------------

<span data-ttu-id="bfabf-115">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="bfabf-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="bfabf-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="bfabf-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="bfabf-117">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="bfabf-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="bfabf-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bfabf-118">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="bfabf-119">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="bfabf-119">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="bfabf-120">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="bfabf-120">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bfabf-121">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="bfabf-121">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="bfabf-122">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="bfabf-122">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bfabf-123">En-tête</span><span class="sxs-lookup"><span data-stu-id="bfabf-123">Header</span></span></p></td>
<td><span data-ttu-id="bfabf-124">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="bfabf-124">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bfabf-125">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="bfabf-125">Library</span></span></p></td>
<td><span data-ttu-id="bfabf-126">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="bfabf-126">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bfabf-127">DLL</span><span class="sxs-lookup"><span data-stu-id="bfabf-127">DLL</span></span></p></td>
<td><span data-ttu-id="bfabf-128">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="bfabf-128">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="bfabf-129"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfabf-129"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="bfabf-130">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="bfabf-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="bfabf-131">Mémoires tampons d’écran de la console</span><span class="sxs-lookup"><span data-stu-id="bfabf-131">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="bfabf-132">**\_informations sur le curseur de la console \_**</span><span class="sxs-lookup"><span data-stu-id="bfabf-132">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="bfabf-133">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="bfabf-133">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

 

 




