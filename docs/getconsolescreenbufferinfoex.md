---
title: GetConsoleScreenBufferInfoEx fonction)
description: Récupère des informations étendues sur la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfoEx
- wincon/GetConsoleScreenBufferInfoEx
- GetConsoleScreenBufferInfoEx
MS-HAID:
- base.getconsolescreenbufferinfoex
- consoles.getconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 60534226-d26f-44e2-a4cc-64811882e308
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 69cb3c59af1a93cf6af664bbecaf05ef00b64ce8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059144"
---
# <a name="getconsolescreenbufferinfoex-function"></a><span data-ttu-id="31e25-104">GetConsoleScreenBufferInfoEx fonction)</span><span class="sxs-lookup"><span data-stu-id="31e25-104">GetConsoleScreenBufferInfoEx function</span></span>


<span data-ttu-id="31e25-105">Récupère des informations étendues sur la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="31e25-105">Retrieves extended information about the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="31e25-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31e25-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleScreenBufferInfoEx(
  _In_  HANDLE                        hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

<a name="parameters"></a><span data-ttu-id="31e25-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="31e25-107">Parameters</span></span>
----------

<span data-ttu-id="31e25-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="31e25-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="31e25-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="31e25-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="31e25-110">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="31e25-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="31e25-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="31e25-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="31e25-112">*lpConsoleScreenBufferInfoEx* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="31e25-112">*lpConsoleScreenBufferInfoEx* \[out\]</span></span>  
<span data-ttu-id="31e25-113">Une [**structure \_ \_ \_ INFOEX de mémoire tampon d’écran**](console-screen-buffer-infoex.md) de la console qui reçoit les informations de mémoire tampon d’écran de console demandées.</span><span class="sxs-lookup"><span data-stu-id="31e25-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that receives the requested console screen buffer information.</span></span>

<a name="return-value"></a><span data-ttu-id="31e25-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="31e25-114">Return value</span></span>
------------

<span data-ttu-id="31e25-115">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="31e25-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="31e25-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="31e25-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="31e25-117">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="31e25-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="31e25-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="31e25-118">Remarks</span></span>
-------

<span data-ttu-id="31e25-119">Le rectangle retourné dans le membre **srWindow** de la structure INFOEX de la [\*\* \_ \_ mémoire tampon \_ d’écran\*\*](console-screen-buffer-infoex.md) de la console peut être modifié, puis transmis à la fonction [**SetConsoleWindowInfo**](setconsolewindowinfo.md) pour faire défiler la mémoire tampon de l’écran de la console dans la fenêtre, pour modifier la taille de la fenêtre, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="31e25-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="31e25-120">Toutes les coordonnées retournées dans la structure INFOEX de la [\*\* \_ \_ mémoire tampon \_ d’écran\*\*](console-screen-buffer-infoex.md) de la console sont exprimées en coordonnées de cellule de caractères, où l’origine (0,0) se trouve dans l’angle supérieur gauche de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="31e25-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

<a name="requirements"></a><span data-ttu-id="31e25-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="31e25-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="31e25-122">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="31e25-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="31e25-123">Windows Vista [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="31e25-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="31e25-124">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="31e25-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="31e25-125">Windows Server 2008 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="31e25-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="31e25-126">En-tête</span><span class="sxs-lookup"><span data-stu-id="31e25-126">Header</span></span></p></td>
<td><span data-ttu-id="31e25-127">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="31e25-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="31e25-128">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="31e25-128">Library</span></span></p></td>
<td><span data-ttu-id="31e25-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="31e25-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="31e25-130">DLL</span><span class="sxs-lookup"><span data-stu-id="31e25-130">DLL</span></span></p></td>
<td><span data-ttu-id="31e25-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="31e25-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="31e25-132"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31e25-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="31e25-133">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="31e25-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="31e25-134">**mémoire tampon d’écran de la CONSOLE \_ \_ \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="31e25-134">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="31e25-135">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="31e25-135">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)

 

 




