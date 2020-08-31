---
title: SetConsoleDisplayMode fonction)
description: Consultez les informations de référence sur la fonction SetConsoleDisplayMode, qui définit le mode d’affichage de la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- base.setconsoledisplaymode
- consoles.setconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744
topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0d4564b9a7562fb495c9834df98708d5faff5334
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059321"
---
# <a name="setconsoledisplaymode-function"></a><span data-ttu-id="332f2-104">SetConsoleDisplayMode fonction)</span><span class="sxs-lookup"><span data-stu-id="332f2-104">SetConsoleDisplayMode function</span></span>


<span data-ttu-id="332f2-105">Définit le mode d’affichage de la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="332f2-105">Sets the display mode of the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="332f2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="332f2-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

<a name="parameters"></a><span data-ttu-id="332f2-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="332f2-107">Parameters</span></span>
----------

<span data-ttu-id="332f2-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="332f2-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="332f2-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="332f2-109">A handle to the console screen buffer.</span></span>

<span data-ttu-id="332f2-110">*dwFlags* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="332f2-110">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="332f2-111">Mode d’affichage de la console.</span><span class="sxs-lookup"><span data-stu-id="332f2-111">The display mode of the console.</span></span> <span data-ttu-id="332f2-112">Ce paramètre peut être une ou plusieurs des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="332f2-112">This parameter can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="332f2-113">Value</span><span class="sxs-lookup"><span data-stu-id="332f2-113">Value</span></span></th>
<th><span data-ttu-id="332f2-114">Signification</span><span class="sxs-lookup"><span data-stu-id="332f2-114">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="332f2-115"><span id="CONSOLE_FULLSCREEN_MODE"></span><span id="console_fullscreen_mode"></span>
<strong>CONSOLE_FULLSCREEN_MODE</strong> 1</span><span class="sxs-lookup"><span data-stu-id="332f2-115"><span id="CONSOLE_FULLSCREEN_MODE"></span><span id="console_fullscreen_mode"></span>
<strong>CONSOLE_FULLSCREEN_MODE</strong> 1</span></span></td>
<td><p><span data-ttu-id="332f2-116">Le texte est affiché en mode plein écran.</span><span class="sxs-lookup"><span data-stu-id="332f2-116">Text is displayed in full-screen mode.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="332f2-117"><span id="CONSOLE_WINDOWED_MODE"></span><span id="console_windowed_mode"></span>
<strong>CONSOLE_WINDOWED_MODE</strong> 2</span><span class="sxs-lookup"><span data-stu-id="332f2-117"><span id="CONSOLE_WINDOWED_MODE"></span><span id="console_windowed_mode"></span>
<strong>CONSOLE_WINDOWED_MODE</strong> 2</span></span></td>
<td><p><span data-ttu-id="332f2-118">Le texte est affiché dans une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="332f2-118">Text is displayed in a console window.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="332f2-119">*lpNewScreenBufferDimensions* \[ out, facultatif\]</span><span class="sxs-lookup"><span data-stu-id="332f2-119">*lpNewScreenBufferDimensions* \[out, optional\]</span></span>  
<span data-ttu-id="332f2-120">Pointeur vers une structure de [**repère**](coord-str.md) qui reçoit les nouvelles dimensions de la mémoire tampon d’écran, en caractères.</span><span class="sxs-lookup"><span data-stu-id="332f2-120">A pointer to a [**COORD**](coord-str.md) structure that receives the new dimensions of the screen buffer, in characters.</span></span>

<a name="return-value"></a><span data-ttu-id="332f2-121">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="332f2-121">Return value</span></span>
------------

<span data-ttu-id="332f2-122">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="332f2-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="332f2-123">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="332f2-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="332f2-124">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="332f2-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="332f2-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="332f2-125">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="332f2-126">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="332f2-126">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="332f2-127">Windows XP [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="332f2-127">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="332f2-128">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="332f2-128">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="332f2-129">Windows Server 2003 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="332f2-129">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="332f2-130">En-tête</span><span class="sxs-lookup"><span data-stu-id="332f2-130">Header</span></span></p></td>
<td><span data-ttu-id="332f2-131">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="332f2-131">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="332f2-132">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="332f2-132">Library</span></span></p></td>
<td><span data-ttu-id="332f2-133">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="332f2-133">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="332f2-134">DLL</span><span class="sxs-lookup"><span data-stu-id="332f2-134">DLL</span></span></p></td>
<td><span data-ttu-id="332f2-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="332f2-135">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="332f2-136"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="332f2-136"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="332f2-137">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="332f2-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="332f2-138">Modes de la console</span><span class="sxs-lookup"><span data-stu-id="332f2-138">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="332f2-139">**GetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="332f2-139">**GetConsoleDisplayMode**</span></span>](getconsoledisplaymode.md)

 

 




