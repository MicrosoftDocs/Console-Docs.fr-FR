---
title: SetConsoleScreenBufferSize fonction)
description: Consultez les informations de référence sur la fonction SetConsoleScreenBufferSize, qui modifie la taille de la mémoire tampon d’écran de la console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/SetConsoleScreenBufferSize
- wincon/SetConsoleScreenBufferSize
- SetConsoleScreenBufferSize
MS-HAID:
- '\_win32\_setconsolescreenbuffersize'
- base.setconsolescreenbuffersize
- consoles.setconsolescreenbuffersize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 50bf1973-5604-42fe-bbeb-611ddc240bdd
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0e2f3a3ea11f291e88837885c6fc3e555fd39e09
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059532"
---
# <a name="setconsolescreenbuffersize-function"></a><span data-ttu-id="a6977-104">SetConsoleScreenBufferSize fonction)</span><span class="sxs-lookup"><span data-stu-id="a6977-104">SetConsoleScreenBufferSize function</span></span>


<span data-ttu-id="a6977-105">Modifie la taille de la mémoire tampon d’écran de la console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a6977-105">Changes the size of the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="a6977-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6977-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleScreenBufferSize(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwSize
);
```

<a name="parameters"></a><span data-ttu-id="a6977-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a6977-107">Parameters</span></span>
----------

<span data-ttu-id="a6977-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="a6977-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="a6977-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="a6977-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="a6977-110">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="a6977-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="a6977-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="a6977-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="a6977-112">*dwSize nul* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="a6977-112">*dwSize* \[in\]</span></span>  
<span data-ttu-id="a6977-113">Structure de [**repère**](coord-str.md) qui spécifie la nouvelle taille de la mémoire tampon d’écran de la console, en lignes et colonnes de caractères.</span><span class="sxs-lookup"><span data-stu-id="a6977-113">A [**COORD**](coord-str.md) structure that specifies the new size of the console screen buffer, in character rows and columns.</span></span> <span data-ttu-id="a6977-114">La largeur et la hauteur spécifiées ne peuvent pas être inférieures à la largeur et à la hauteur de la fenêtre de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="a6977-114">The specified width and height cannot be less than the width and height of the console screen buffer's window.</span></span> <span data-ttu-id="a6977-115">Les dimensions spécifiées ne peuvent pas non plus être inférieures à la taille minimale autorisée par le système.</span><span class="sxs-lookup"><span data-stu-id="a6977-115">The specified dimensions also cannot be less than the minimum size allowed by the system.</span></span> <span data-ttu-id="a6977-116">Cette valeur minimale dépend de la taille de police actuelle de la console (sélectionnée par l’utilisateur) et des valeurs de \*\* \_ CXMIN\*\* et **SM \_ CYMIN** retournées par la fonction [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) .</span><span class="sxs-lookup"><span data-stu-id="a6977-116">This minimum depends on the current font size for the console (selected by the user) and the **SM\_CXMIN** and **SM\_CYMIN** values returned by the [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) function.</span></span>

<a name="return-value"></a><span data-ttu-id="a6977-117">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="a6977-117">Return value</span></span>
------------

<span data-ttu-id="a6977-118">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="a6977-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="a6977-119">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="a6977-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="a6977-120">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="a6977-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="a6977-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a6977-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="a6977-122">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="a6977-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="a6977-123">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="a6977-123">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a6977-124">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="a6977-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="a6977-125">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="a6977-125">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a6977-126">En-tête</span><span class="sxs-lookup"><span data-stu-id="a6977-126">Header</span></span></p></td>
<td><span data-ttu-id="a6977-127">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="a6977-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a6977-128">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="a6977-128">Library</span></span></p></td>
<td><span data-ttu-id="a6977-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="a6977-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a6977-130">DLL</span><span class="sxs-lookup"><span data-stu-id="a6977-130">DLL</span></span></p></td>
<td><span data-ttu-id="a6977-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="a6977-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="a6977-132"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6977-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="a6977-133">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="a6977-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="a6977-134">Mémoire tampon d’entrée de la console</span><span class="sxs-lookup"><span data-stu-id="a6977-134">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="a6977-135">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="a6977-135">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="a6977-136">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="a6977-136">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="a6977-137">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="a6977-137">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

 

 




