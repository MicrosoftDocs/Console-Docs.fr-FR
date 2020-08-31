---
title: GetConsoleWindow fonction)
description: Récupère le handle de fenêtre utilisé par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetConsoleWindow
- wincon/GetConsoleWindow
- GetConsoleWindow
MS-HAID:
- '\_win32\_getconsolewindow'
- base.getconsolewindow
- consoles.getconsolewindow
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a5ab0b37-45ac-4413-b6ff-73876556ad38
topic_type:
- apiref
api_name:
- GetConsoleWindow
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: dd356bab4674da0cc090e42911829dee994fa8b1
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059108"
---
# <a name="getconsolewindow-function"></a><span data-ttu-id="c7a96-104">GetConsoleWindow fonction)</span><span class="sxs-lookup"><span data-stu-id="c7a96-104">GetConsoleWindow function</span></span>


<span data-ttu-id="c7a96-105">Récupère le handle de fenêtre utilisé par la console associée au processus appelant.</span><span class="sxs-lookup"><span data-stu-id="c7a96-105">Retrieves the window handle used by the console associated with the calling process.</span></span>

<a name="syntax"></a><span data-ttu-id="c7a96-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7a96-106">Syntax</span></span>
------

```C
HWND WINAPI GetConsoleWindow(void);
```

<a name="parameters"></a><span data-ttu-id="c7a96-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7a96-107">Parameters</span></span>
----------

<span data-ttu-id="c7a96-108">Cette fonction n’a pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c7a96-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="c7a96-109">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="c7a96-109">Return value</span></span>
------------

<span data-ttu-id="c7a96-110">La valeur de retour est un handle de la fenêtre utilisée par la console associée au processus appelant ou **null** s’il n’existe aucune console associée.</span><span class="sxs-lookup"><span data-stu-id="c7a96-110">The return value is a handle to the window used by the console associated with the calling process or **NULL** if there is no such associated console.</span></span>

<a name="remarks"></a><span data-ttu-id="c7a96-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="c7a96-111">Remarks</span></span>
-------

<span data-ttu-id="c7a96-112">Pour compiler une application qui utilise cette fonction, définissez \*\* \_ Win32 \_ winnt\*\* comme 0x0500 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="c7a96-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="c7a96-113">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="c7a96-113">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="c7a96-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c7a96-114">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="c7a96-115">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="c7a96-115">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="c7a96-116">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="c7a96-116">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c7a96-117">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="c7a96-117">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="c7a96-118">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="c7a96-118">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c7a96-119">En-tête</span><span class="sxs-lookup"><span data-stu-id="c7a96-119">Header</span></span></p></td>
<td><span data-ttu-id="c7a96-120">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c7a96-120">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c7a96-121">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="c7a96-121">Library</span></span></p></td>
<td><span data-ttu-id="c7a96-122">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="c7a96-122">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c7a96-123">DLL</span><span class="sxs-lookup"><span data-stu-id="c7a96-123">DLL</span></span></p></td>
<td><span data-ttu-id="c7a96-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c7a96-124">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="c7a96-125"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7a96-125"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="c7a96-126">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="c7a96-126">Console Functions</span></span>](console-functions.md)

 

 




