---
title: SetConsoleCP fonction)
description: Définit la page de codes d’entrée utilisée par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/SetConsoleCP
- wincon/SetConsoleCP
- SetConsoleCP
MS-HAID:
- '\_win32\_setconsolecp'
- base.setconsolecp
- consoles.setconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a1a9ba5-c792-491d-ae51-979f462dcb53
topic_type:
- apiref
api_name:
- SetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: cf7048f9042b6c516c6d8e7a6e0544fdc2ac7533
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059417"
---
# <a name="setconsolecp-function"></a><span data-ttu-id="1bb6b-104">SetConsoleCP fonction)</span><span class="sxs-lookup"><span data-stu-id="1bb6b-104">SetConsoleCP function</span></span>


<span data-ttu-id="1bb6b-105">Définit la page de codes d’entrée utilisée par la console associée au processus appelant.</span><span class="sxs-lookup"><span data-stu-id="1bb6b-105">Sets the input code page used by the console associated with the calling process.</span></span> <span data-ttu-id="1bb6b-106">Une console utilise sa page de codes d’entrée pour convertir l’entrée au clavier en valeur de caractère correspondante.</span><span class="sxs-lookup"><span data-stu-id="1bb6b-106">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span>

<a name="syntax"></a><span data-ttu-id="1bb6b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bb6b-107">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleCP(
  _In_ UINT wCodePageID
);
```

<a name="parameters"></a><span data-ttu-id="1bb6b-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1bb6b-108">Parameters</span></span>
----------

<span data-ttu-id="1bb6b-109">*wCodePageID* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="1bb6b-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="1bb6b-110">Identificateur de la page de codes à définir.</span><span class="sxs-lookup"><span data-stu-id="1bb6b-110">The identifier of the code page to be set.</span></span> <span data-ttu-id="1bb6b-111">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="1bb6b-111">For more information, see Remarks.</span></span>

<a name="return-value"></a><span data-ttu-id="1bb6b-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="1bb6b-112">Return value</span></span>
------------

<span data-ttu-id="1bb6b-113">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="1bb6b-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="1bb6b-114">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="1bb6b-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="1bb6b-115">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="1bb6b-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="1bb6b-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="1bb6b-116">Remarks</span></span>
-------

<span data-ttu-id="1bb6b-117">Une page de codes mappe 256 codes de caractères à des caractères individuels.</span><span class="sxs-lookup"><span data-stu-id="1bb6b-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="1bb6b-118">Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.</span><span class="sxs-lookup"><span data-stu-id="1bb6b-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="1bb6b-119">Pour rechercher les pages de codes qui sont installées ou prises en charge par le système d’exploitation, utilisez la fonction [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) .</span><span class="sxs-lookup"><span data-stu-id="1bb6b-119">To find the code pages that are installed or supported by the operating system, use the [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) function.</span></span> <span data-ttu-id="1bb6b-120">Les identificateurs des pages de codes disponibles sur l’ordinateur local sont également stockés dans le Registre sous la clé suivante :</span><span class="sxs-lookup"><span data-stu-id="1bb6b-120">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

<span data-ttu-id="1bb6b-121">**HKEY \_ local \_ machine \\ System \\ CurrentControlSet \\ contrôler \\ la \\ page de codes nls**</span><span class="sxs-lookup"><span data-stu-id="1bb6b-121">**HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Nls\\CodePage**</span></span>

<span data-ttu-id="1bb6b-122">Toutefois, il est préférable d’utiliser [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) pour énumérer les pages de code, car le registre peut différer dans différentes versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="1bb6b-122">However, it is better to use [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>

<span data-ttu-id="1bb6b-123">Pour déterminer si une page de codes particulière est valide, utilisez la fonction [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) .</span><span class="sxs-lookup"><span data-stu-id="1bb6b-123">To determine whether a particular code page is valid, use the [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) function.</span></span> <span data-ttu-id="1bb6b-124">Pour obtenir plus d’informations sur une page de codes, y compris son nom, utilisez la fonction [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .</span><span class="sxs-lookup"><span data-stu-id="1bb6b-124">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span> <span data-ttu-id="1bb6b-125">Pour obtenir la liste des identificateurs de page de codes disponibles, consultez [identificateurs de page de codes](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span><span class="sxs-lookup"><span data-stu-id="1bb6b-125">For a list of available code page identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="1bb6b-126">Pour déterminer la page de codes d’entrée actuelle d’une console, utilisez la fonction [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="1bb6b-126">To determine a console's current input code page, use the [**GetConsoleCP**](getconsolecp.md) function.</span></span> <span data-ttu-id="1bb6b-127">Pour définir et récupérer la page de codes de sortie d’une console, utilisez les fonctions [**SetConsoleOutputCP**](setconsoleoutputcp.md) et [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="1bb6b-127">To set and retrieve a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions.</span></span>

<a name="requirements"></a><span data-ttu-id="1bb6b-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1bb6b-128">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="1bb6b-129">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="1bb6b-129">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="1bb6b-130">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="1bb6b-130">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1bb6b-131">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="1bb6b-131">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="1bb6b-132">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="1bb6b-132">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1bb6b-133">En-tête</span><span class="sxs-lookup"><span data-stu-id="1bb6b-133">Header</span></span></p></td>
<td><span data-ttu-id="1bb6b-134">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1bb6b-134">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1bb6b-135">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="1bb6b-135">Library</span></span></p></td>
<td><span data-ttu-id="1bb6b-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="1bb6b-136">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1bb6b-137">DLL</span><span class="sxs-lookup"><span data-stu-id="1bb6b-137">DLL</span></span></p></td>
<td><span data-ttu-id="1bb6b-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1bb6b-138">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="1bb6b-139"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bb6b-139"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="1bb6b-140">Pages de codes de la console</span><span class="sxs-lookup"><span data-stu-id="1bb6b-140">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="1bb6b-141">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="1bb6b-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1bb6b-142">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="1bb6b-142">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="1bb6b-143">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="1bb6b-143">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="1bb6b-144">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="1bb6b-144">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

 

 




