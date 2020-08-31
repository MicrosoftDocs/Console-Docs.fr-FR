---
title: GetConsoleDisplayMode fonction)
description: Consultez les informations de référence sur la fonction GetConsoleDisplayMode, qui récupère le mode d’affichage de la console actuelle.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 76b3354ac9b44c36ec4cfe3d12257583d10f2ee2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059176"
---
# <a name="getconsoledisplaymode-function"></a><span data-ttu-id="3e223-104">GetConsoleDisplayMode fonction)</span><span class="sxs-lookup"><span data-stu-id="3e223-104">GetConsoleDisplayMode function</span></span>


<span data-ttu-id="3e223-105">Récupère le mode d’affichage de la console actuelle.</span><span class="sxs-lookup"><span data-stu-id="3e223-105">Retrieves the display mode of the current console.</span></span>

<a name="syntax"></a><span data-ttu-id="3e223-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e223-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

<a name="parameters"></a><span data-ttu-id="3e223-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3e223-107">Parameters</span></span>
----------

<span data-ttu-id="3e223-108">*lpModeFlags* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="3e223-108">*lpModeFlags* \[out\]</span></span>  
<span data-ttu-id="3e223-109">Mode d’affichage de la console.</span><span class="sxs-lookup"><span data-stu-id="3e223-109">The display mode of the console.</span></span> <span data-ttu-id="3e223-110">Ce paramètre peut être une ou plusieurs des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="3e223-110">This parameter can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="3e223-111">Value</span><span class="sxs-lookup"><span data-stu-id="3e223-111">Value</span></span></th>
<th><span data-ttu-id="3e223-112">Signification</span><span class="sxs-lookup"><span data-stu-id="3e223-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="3e223-113"><span id="CONSOLE_FULLSCREEN"></span><span id="console_fullscreen"></span>
<strong>CONSOLE_FULLSCREEN</strong> 1</span><span class="sxs-lookup"><span data-stu-id="3e223-113"><span id="CONSOLE_FULLSCREEN"></span><span id="console_fullscreen"></span>
<strong>CONSOLE_FULLSCREEN</strong> 1</span></span></td>
<td><p><span data-ttu-id="3e223-114">Console plein écran.</span><span class="sxs-lookup"><span data-stu-id="3e223-114">Full-screen console.</span></span> <span data-ttu-id="3e223-115">La console est dans ce mode dès que la fenêtre est agrandie.</span><span class="sxs-lookup"><span data-stu-id="3e223-115">The console is in this mode as soon as the window is maximized.</span></span> <span data-ttu-id="3e223-116">À ce stade, la transition vers le mode plein écran peut encore échouer.</span><span class="sxs-lookup"><span data-stu-id="3e223-116">At this point, the transition to full-screen mode can still fail.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="3e223-117"><span id="CONSOLE_FULLSCREEN_HARDWARE"></span><span id="console_fullscreen_hardware"></span>
<strong>CONSOLE_FULLSCREEN_HARDWARE</strong> 2</span><span class="sxs-lookup"><span data-stu-id="3e223-117"><span id="CONSOLE_FULLSCREEN_HARDWARE"></span><span id="console_fullscreen_hardware"></span>
<strong>CONSOLE_FULLSCREEN_HARDWARE</strong> 2</span></span></td>
<td><p><span data-ttu-id="3e223-118">La console plein écran communique directement avec le matériel vidéo.</span><span class="sxs-lookup"><span data-stu-id="3e223-118">Full-screen console communicating directly with the video hardware.</span></span> <span data-ttu-id="3e223-119">Ce mode est défini une fois que la console est en mode <strong>CONSOLE_FULLSCREEN</strong> pour indiquer que la transition vers le mode plein écran est terminée.</span><span class="sxs-lookup"><span data-stu-id="3e223-119">This mode is set after the console is in <strong>CONSOLE_FULLSCREEN</strong> mode to indicate that the transition to full-screen mode has completed.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="3e223-120">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="3e223-120">Return value</span></span>
------------

<span data-ttu-id="3e223-121">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="3e223-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="3e223-122">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="3e223-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="3e223-123">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="3e223-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="3e223-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="3e223-124">Remarks</span></span>
-------

<span data-ttu-id="3e223-125">Pour compiler une application qui utilise cette fonction, définissez \*\* \_ Win32 \_ winnt\*\* comme 0x0500 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="3e223-125">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="3e223-126">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="3e223-126">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="3e223-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3e223-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="3e223-128">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="3e223-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="3e223-129">Windows XP [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="3e223-129">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3e223-130">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="3e223-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="3e223-131">Windows Server 2003 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="3e223-131">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3e223-132">En-tête</span><span class="sxs-lookup"><span data-stu-id="3e223-132">Header</span></span></p></td>
<td><span data-ttu-id="3e223-133">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="3e223-133">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3e223-134">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="3e223-134">Library</span></span></p></td>
<td><span data-ttu-id="3e223-135">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="3e223-135">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3e223-136">DLL</span><span class="sxs-lookup"><span data-stu-id="3e223-136">DLL</span></span></p></td>
<td><span data-ttu-id="3e223-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3e223-137">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="3e223-138"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e223-138"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="3e223-139">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="3e223-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3e223-140">Modes de la console</span><span class="sxs-lookup"><span data-stu-id="3e223-140">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="3e223-141">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="3e223-141">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)

 

 




