---
title: SetCurrentConsoleFontEx fonction)
description: Consultez les informations de référence sur la fonction SetCurrentConsoleFontEx, qui définit des informations étendues sur la police de la console actuelle.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/SetCurrentConsoleFontEx
- wincon/SetCurrentConsoleFontEx
- SetCurrentConsoleFontEx
MS-HAID:
- base.setcurrentconsolefontex
- consoles.setcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: fbc31e2a-31df-4e9e-9f61-35a4ff812f8f
topic_type:
- apiref
api_name:
- SetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 9d97383f40c38489ac3ea5e7c75386163b9d5d2d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059277"
---
# <a name="setcurrentconsolefontex-function"></a><span data-ttu-id="05456-104">SetCurrentConsoleFontEx fonction)</span><span class="sxs-lookup"><span data-stu-id="05456-104">SetCurrentConsoleFontEx function</span></span>


<span data-ttu-id="05456-105">Définit des informations étendues sur la police de la console actuelle.</span><span class="sxs-lookup"><span data-stu-id="05456-105">Sets extended information about the current console font.</span></span>

<a name="syntax"></a><span data-ttu-id="05456-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05456-106">Syntax</span></span>
------

```C
BOOL WINAPI SetCurrentConsoleFontEx(
  _In_ HANDLE               hConsoleOutput,
  _In_ BOOL                 bMaximumWindow,
  _In_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

<a name="parameters"></a><span data-ttu-id="05456-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="05456-107">Parameters</span></span>
----------

<span data-ttu-id="05456-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="05456-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="05456-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="05456-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="05456-110">Le descripteur doit avoir le droit d’accès en \*\* \_ écriture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="05456-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="05456-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="05456-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="05456-112">*bMaximumWindow* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="05456-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="05456-113">Si ce paramètre a la **valeur true**, les informations sur la police sont définies pour la taille maximale de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="05456-113">If this parameter is **TRUE**, font information is set for the maximum window size.</span></span> <span data-ttu-id="05456-114">Si ce paramètre a la **valeur false**, les informations sur la police sont définies pour la taille de fenêtre actuelle.</span><span class="sxs-lookup"><span data-stu-id="05456-114">If this parameter is **FALSE**, font information is set for the current window size.</span></span>

<span data-ttu-id="05456-115">*lpConsoleCurrentFontEx* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="05456-115">*lpConsoleCurrentFontEx* \[in\]</span></span>  
<span data-ttu-id="05456-116">Pointeur vers une structure [**de \_ police \_ de console INFOEX**](console-font-infoex.md) qui contient les informations sur la police.</span><span class="sxs-lookup"><span data-stu-id="05456-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that contains the font information.</span></span>

<a name="return-value"></a><span data-ttu-id="05456-117">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="05456-117">Return value</span></span>
------------

<span data-ttu-id="05456-118">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="05456-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="05456-119">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="05456-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="05456-120">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="05456-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="05456-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="05456-121">Remarks</span></span>
-------

<span data-ttu-id="05456-122">Pour compiler une application qui utilise cette fonction, définissez \*\* \_ Win32 \_ winnt\*\* comme 0x0500 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="05456-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="05456-123">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="05456-123">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="05456-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="05456-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="05456-125">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="05456-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="05456-126">Windows Vista [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="05456-126">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="05456-127">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="05456-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="05456-128">Windows Server 2008 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="05456-128">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="05456-129">En-tête</span><span class="sxs-lookup"><span data-stu-id="05456-129">Header</span></span></p></td>
<td><span data-ttu-id="05456-130">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="05456-130">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="05456-131">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="05456-131">Library</span></span></p></td>
<td><span data-ttu-id="05456-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="05456-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="05456-133">DLL</span><span class="sxs-lookup"><span data-stu-id="05456-133">DLL</span></span></p></td>
<td><span data-ttu-id="05456-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="05456-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="05456-135"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05456-135"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="05456-136">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="05456-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="05456-137">**police de la CONSOLE \_ \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="05456-137">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)

 

 




