---
title: GetConsoleFontSize fonction)
description: Récupère la taille de la police utilisée par la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetConsoleFontSize
- wincon/GetConsoleFontSize
- GetConsoleFontSize
MS-HAID:
- '\_win32\_getconsolefontsize'
- base.getconsolefontsize
- consoles.getconsolefontsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 51b1f58d-b3fb-4e09-8398-671b3959bb01
topic_type:
- apiref
api_name:
- GetConsoleFontSize
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: b992ddaab35cb5af25479426dca83ef6381e73dd
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059168"
---
# <a name="getconsolefontsize-function"></a><span data-ttu-id="6b301-104">GetConsoleFontSize fonction)</span><span class="sxs-lookup"><span data-stu-id="6b301-104">GetConsoleFontSize function</span></span>


<span data-ttu-id="6b301-105">Récupère la taille de la police utilisée par la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6b301-105">Retrieves the size of the font used by the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="6b301-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b301-106">Syntax</span></span>
------

```C
COORD WINAPI GetConsoleFontSize(
  _In_ HANDLE hConsoleOutput,
  _In_ DWORD  nFont
);
```

<a name="parameters"></a><span data-ttu-id="6b301-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6b301-107">Parameters</span></span>
----------

<span data-ttu-id="6b301-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="6b301-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="6b301-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="6b301-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="6b301-110">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="6b301-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="6b301-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="6b301-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="6b301-112">*nFont* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="6b301-112">*nFont* \[in\]</span></span>  
<span data-ttu-id="6b301-113">Index de la police dont la taille doit être récupérée.</span><span class="sxs-lookup"><span data-stu-id="6b301-113">The index of the font whose size is to be retrieved.</span></span> <span data-ttu-id="6b301-114">Cet index est obtenu en appelant la fonction [**GetCurrentConsoleFont**](getcurrentconsolefont.md) .</span><span class="sxs-lookup"><span data-stu-id="6b301-114">This index is obtained by calling the [**GetCurrentConsoleFont**](getcurrentconsolefont.md) function.</span></span>

<a name="return-value"></a><span data-ttu-id="6b301-115">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="6b301-115">Return value</span></span>
------------

<span data-ttu-id="6b301-116">Si la fonction est réussie, la valeur de retour est une structure de [**repère**](coord-str.md) qui contient la largeur et la hauteur de chaque caractère de la police, en unités logiques.</span><span class="sxs-lookup"><span data-stu-id="6b301-116">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="6b301-117">Le membre **X** contient la largeur, tandis que le membre **Y** contient la hauteur.</span><span class="sxs-lookup"><span data-stu-id="6b301-117">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="6b301-118">Si la fonction échoue, la largeur et la hauteur sont égales à zéro.</span><span class="sxs-lookup"><span data-stu-id="6b301-118">If the function fails, the width and the height are zero.</span></span> <span data-ttu-id="6b301-119">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="6b301-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="6b301-120">Pour compiler une application qui utilise cette fonction, définissez \*\* \_ Win32 \_ winnt\*\* comme 0x0500 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="6b301-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="6b301-121">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="6b301-121">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="6b301-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6b301-122">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="6b301-123">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="6b301-123">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="6b301-124">Windows XP [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="6b301-124">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6b301-125">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="6b301-125">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="6b301-126">Windows Server 2003 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="6b301-126">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6b301-127">En-tête</span><span class="sxs-lookup"><span data-stu-id="6b301-127">Header</span></span></p></td>
<td><span data-ttu-id="6b301-128">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6b301-128">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6b301-129">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="6b301-129">Library</span></span></p></td>
<td><span data-ttu-id="6b301-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="6b301-130">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6b301-131">DLL</span><span class="sxs-lookup"><span data-stu-id="6b301-131">DLL</span></span></p></td>
<td><span data-ttu-id="6b301-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6b301-132">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="6b301-133"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b301-133"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="6b301-134">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="6b301-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="6b301-135">Mémoires tampons d’écran de la console</span><span class="sxs-lookup"><span data-stu-id="6b301-135">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="6b301-136">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="6b301-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="6b301-137">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="6b301-137">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)

 

 




