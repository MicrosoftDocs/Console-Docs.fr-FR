---
title: SetConsoleActiveScreenBuffer fonction)
description: Définit la mémoire tampon d’écran spécifiée comme étant la mémoire tampon d’écran de la console actuellement affichée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/SetConsoleActiveScreenBuffer
- wincon/SetConsoleActiveScreenBuffer
- SetConsoleActiveScreenBuffer
MS-HAID:
- '\_win32\_setconsoleactivescreenbuffer'
- base.setconsoleactivescreenbuffer
- consoles.setconsoleactivescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c026cb94-c8ec-44ee-b432-3870ae3006c2
topic_type:
- apiref
api_name:
- SetConsoleActiveScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: f3fa9d79705c95fc0737597886b5562ce1045c45
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059420"
---
# <a name="setconsoleactivescreenbuffer-function"></a><span data-ttu-id="282b4-104">SetConsoleActiveScreenBuffer fonction)</span><span class="sxs-lookup"><span data-stu-id="282b4-104">SetConsoleActiveScreenBuffer function</span></span>


<span data-ttu-id="282b4-105">Définit la mémoire tampon d’écran spécifiée comme étant la mémoire tampon d’écran de la console actuellement affichée.</span><span class="sxs-lookup"><span data-stu-id="282b4-105">Sets the specified screen buffer to be the currently displayed console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="282b4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="282b4-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleActiveScreenBuffer(
  _In_ HANDLE hConsoleOutput
);
```

<a name="parameters"></a><span data-ttu-id="282b4-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="282b4-107">Parameters</span></span>
----------

<span data-ttu-id="282b4-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="282b4-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="282b4-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="282b4-109">A handle to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="282b4-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="282b4-110">Return value</span></span>
------------

<span data-ttu-id="282b4-111">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="282b4-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="282b4-112">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="282b4-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="282b4-113">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="282b4-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="282b4-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="282b4-114">Remarks</span></span>
-------

<span data-ttu-id="282b4-115">Une console peut avoir plusieurs mémoires tampons d’écran.</span><span class="sxs-lookup"><span data-stu-id="282b4-115">A console can have multiple screen buffers.</span></span> <span data-ttu-id="282b4-116">**SetConsoleActiveScreenBuffer** détermine celui qui est affiché.</span><span class="sxs-lookup"><span data-stu-id="282b4-116">**SetConsoleActiveScreenBuffer** determines which one is displayed.</span></span> <span data-ttu-id="282b4-117">Vous pouvez écrire dans une mémoire tampon d’écran inactive, puis utiliser **SetConsoleActiveScreenBuffer** pour afficher le contenu de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="282b4-117">You can write to an inactive screen buffer and then use **SetConsoleActiveScreenBuffer** to display the buffer's contents.</span></span>

<a name="examples"></a><span data-ttu-id="282b4-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="282b4-118">Examples</span></span>
--------

<span data-ttu-id="282b4-119">Pour obtenir un exemple, consultez [lecture et écriture de blocs de caractères et d’attributs](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="282b4-119">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

<a name="requirements"></a><span data-ttu-id="282b4-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="282b4-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="282b4-121">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="282b4-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="282b4-122">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="282b4-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="282b4-123">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="282b4-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="282b4-124">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="282b4-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="282b4-125">En-tête</span><span class="sxs-lookup"><span data-stu-id="282b4-125">Header</span></span></p></td>
<td><span data-ttu-id="282b4-126">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="282b4-126">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="282b4-127">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="282b4-127">Library</span></span></p></td>
<td><span data-ttu-id="282b4-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="282b4-128">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="282b4-129">DLL</span><span class="sxs-lookup"><span data-stu-id="282b4-129">DLL</span></span></p></td>
<td><span data-ttu-id="282b4-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="282b4-130">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="282b4-131"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="282b4-131"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="282b4-132">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="282b4-132">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="282b4-133">Mémoires tampons d’écran de la console</span><span class="sxs-lookup"><span data-stu-id="282b4-133">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="282b4-134">**CreateConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="282b4-134">**CreateConsoleScreenBuffer**</span></span>](createconsolescreenbuffer.md)

 

 




