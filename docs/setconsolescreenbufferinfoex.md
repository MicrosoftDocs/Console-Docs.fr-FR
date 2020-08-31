---
title: SetConsoleScreenBufferInfoEx fonction)
description: Définit les informations étendues relatives à la mémoire tampon d’écran de console spécifiée dans la mémoire tampon spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/SetConsoleScreenBufferInfoEx
- wincon/SetConsoleScreenBufferInfoEx
- SetConsoleScreenBufferInfoEx
MS-HAID:
- base.setconsolescreenbufferinfoex
- consoles.setconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ff851144-eee9-4410-8fd1-28aa24fc25f1
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 403ce6c3625aacdcc8b2eb498e7df1715d1e6b94
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059521"
---
# <a name="setconsolescreenbufferinfoex-function"></a><span data-ttu-id="d4fe1-104">SetConsoleScreenBufferInfoEx fonction)</span><span class="sxs-lookup"><span data-stu-id="d4fe1-104">SetConsoleScreenBufferInfoEx function</span></span>


<span data-ttu-id="d4fe1-105">Définit des informations étendues sur la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d4fe1-105">Sets extended information about the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="d4fe1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4fe1-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleScreenBufferInfoEx(
  _In_ HANDLE                        hConsoleOutput,
  _In_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

<a name="parameters"></a><span data-ttu-id="d4fe1-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d4fe1-107">Parameters</span></span>
----------

<span data-ttu-id="d4fe1-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="d4fe1-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="d4fe1-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="d4fe1-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="d4fe1-110">Le descripteur doit avoir le droit d’accès en \*\* \_ écriture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="d4fe1-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="d4fe1-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="d4fe1-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="d4fe1-112">*lpConsoleScreenBufferInfoEx* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="d4fe1-112">*lpConsoleScreenBufferInfoEx* \[in\]</span></span>  
<span data-ttu-id="d4fe1-113">Une [**structure \_ \_ \_ INFOEX de mémoire tampon d’écran**](console-screen-buffer-infoex.md) de la console qui contient les informations de mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="d4fe1-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that contains the console screen buffer information.</span></span>

<a name="return-value"></a><span data-ttu-id="d4fe1-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="d4fe1-114">Return value</span></span>
------------

<span data-ttu-id="d4fe1-115">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="d4fe1-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d4fe1-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="d4fe1-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d4fe1-117">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="d4fe1-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="d4fe1-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d4fe1-118">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="d4fe1-119">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="d4fe1-119">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="d4fe1-120">Windows Vista [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="d4fe1-120">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d4fe1-121">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="d4fe1-121">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="d4fe1-122">Windows Server 2008 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="d4fe1-122">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d4fe1-123">En-tête</span><span class="sxs-lookup"><span data-stu-id="d4fe1-123">Header</span></span></p></td>
<td><span data-ttu-id="d4fe1-124">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d4fe1-124">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d4fe1-125">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="d4fe1-125">Library</span></span></p></td>
<td><span data-ttu-id="d4fe1-126">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="d4fe1-126">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d4fe1-127">DLL</span><span class="sxs-lookup"><span data-stu-id="d4fe1-127">DLL</span></span></p></td>
<td><span data-ttu-id="d4fe1-128">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d4fe1-128">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="d4fe1-129"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4fe1-129"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="d4fe1-130">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="d4fe1-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d4fe1-131">**mémoire tampon d’écran de la CONSOLE \_ \_ \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="d4fe1-131">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="d4fe1-132">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="d4fe1-132">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)

 

 




