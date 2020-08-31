---
title: GetCurrentConsoleFontEx fonction)
description: Consultez les informations de référence sur la fonction GetCurrentConsoleFontEx, qui récupère des informations étendues sur la police de console actuellement utilisée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetCurrentConsoleFontEx
- wincon/GetCurrentConsoleFontEx
- GetCurrentConsoleFontEx
MS-HAID:
- base.getcurrentconsolefontex
- consoles.getcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 97d8e730-4110-4be5-b099-0acc1b6f8eb5
topic_type:
- apiref
api_name:
- GetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0ea8d5ad928003d4039a6c8611073ab3c38ce34f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059116"
---
# <a name="getcurrentconsolefontex-function"></a><span data-ttu-id="f5c96-104">GetCurrentConsoleFontEx fonction)</span><span class="sxs-lookup"><span data-stu-id="f5c96-104">GetCurrentConsoleFontEx function</span></span>


<span data-ttu-id="f5c96-105">Récupère des informations étendues sur la police de la console actuelle.</span><span class="sxs-lookup"><span data-stu-id="f5c96-105">Retrieves extended information about the current console font.</span></span>

<a name="syntax"></a><span data-ttu-id="f5c96-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5c96-106">Syntax</span></span>
------

```C
BOOL WINAPI GetCurrentConsoleFontEx(
  _In_  HANDLE               hConsoleOutput,
  _In_  BOOL                 bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

<a name="parameters"></a><span data-ttu-id="f5c96-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f5c96-107">Parameters</span></span>
----------

<span data-ttu-id="f5c96-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="f5c96-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="f5c96-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="f5c96-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="f5c96-110">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="f5c96-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="f5c96-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="f5c96-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="f5c96-112">*bMaximumWindow* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="f5c96-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="f5c96-113">Si ce paramètre a la **valeur true**, les informations sur la police sont récupérées pour la taille maximale de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="f5c96-113">If this parameter is **TRUE**, font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="f5c96-114">Si ce paramètre a la **valeur false**, les informations sur la police sont récupérées pour la taille de fenêtre actuelle.</span><span class="sxs-lookup"><span data-stu-id="f5c96-114">If this parameter is **FALSE**, font information is retrieved for the current window size.</span></span>

<span data-ttu-id="f5c96-115">*lpConsoleCurrentFontEx* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="f5c96-115">*lpConsoleCurrentFontEx* \[out\]</span></span>  
<span data-ttu-id="f5c96-116">Pointeur vers une structure [**de \_ police \_ de console INFOEX**](console-font-infoex.md) qui reçoit les informations de police demandées.</span><span class="sxs-lookup"><span data-stu-id="f5c96-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that receives the requested font information.</span></span>

<a name="return-value"></a><span data-ttu-id="f5c96-117">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="f5c96-117">Return value</span></span>
------------

<span data-ttu-id="f5c96-118">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="f5c96-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="f5c96-119">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="f5c96-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="f5c96-120">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="f5c96-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="f5c96-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f5c96-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f5c96-122">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="f5c96-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="f5c96-123">Windows Vista [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="f5c96-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f5c96-124">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="f5c96-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="f5c96-125">Windows Server 2008 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="f5c96-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f5c96-126">En-tête</span><span class="sxs-lookup"><span data-stu-id="f5c96-126">Header</span></span></p></td>
<td><span data-ttu-id="f5c96-127">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f5c96-127">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f5c96-128">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="f5c96-128">Library</span></span></p></td>
<td><span data-ttu-id="f5c96-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="f5c96-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f5c96-130">DLL</span><span class="sxs-lookup"><span data-stu-id="f5c96-130">DLL</span></span></p></td>
<td><span data-ttu-id="f5c96-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f5c96-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="f5c96-132"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5c96-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="f5c96-133">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="f5c96-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f5c96-134">**police de la CONSOLE \_ \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="f5c96-134">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)

 

 




