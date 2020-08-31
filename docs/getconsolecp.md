---
title: GetConsoleCP fonction)
description: Récupère la page de codes d’entrée utilisée par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi/GetConsoleCP
- wincon/GetConsoleCP
- GetConsoleCP
MS-HAID:
- '\_win32\_getconsolecp'
- base.getconsolecp
- consoles.getconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9e0af6d9-0f5c-45b3-a686-22449d26de47
topic_type:
- apiref
api_name:
- GetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: ba0ebfecddf5702e8078197b834931a62658d9dc
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059172"
---
# <a name="getconsolecp-function"></a><span data-ttu-id="f5629-104">GetConsoleCP fonction)</span><span class="sxs-lookup"><span data-stu-id="f5629-104">GetConsoleCP function</span></span>


<span data-ttu-id="f5629-105">Récupère la page de codes d’entrée utilisée par la console associée au processus appelant.</span><span class="sxs-lookup"><span data-stu-id="f5629-105">Retrieves the input code page used by the console associated with the calling process.</span></span> <span data-ttu-id="f5629-106">Une console utilise sa page de codes d’entrée pour convertir l’entrée au clavier en valeur de caractère correspondante.</span><span class="sxs-lookup"><span data-stu-id="f5629-106">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span>

<a name="syntax"></a><span data-ttu-id="f5629-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5629-107">Syntax</span></span>
------

```C
UINT WINAPI GetConsoleCP(void);
```

<a name="parameters"></a><span data-ttu-id="f5629-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f5629-108">Parameters</span></span>
----------

<span data-ttu-id="f5629-109">Cette fonction n’a pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f5629-109">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="f5629-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="f5629-110">Return value</span></span>
------------

<span data-ttu-id="f5629-111">La valeur de retour est un code qui identifie la page de codes.</span><span class="sxs-lookup"><span data-stu-id="f5629-111">The return value is a code that identifies the code page.</span></span> <span data-ttu-id="f5629-112">Pour obtenir la liste des identificateurs, consultez [identificateurs de page de codes](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span><span class="sxs-lookup"><span data-stu-id="f5629-112">For a list of identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="f5629-113">Si la valeur de retour est égale à zéro, la fonction a échoué.</span><span class="sxs-lookup"><span data-stu-id="f5629-113">If the return value is zero, the function has failed.</span></span> <span data-ttu-id="f5629-114">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="f5629-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="f5629-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="f5629-115">Remarks</span></span>
-------

<span data-ttu-id="f5629-116">Une page de codes mappe 256 codes de caractères à des caractères individuels.</span><span class="sxs-lookup"><span data-stu-id="f5629-116">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="f5629-117">Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.</span><span class="sxs-lookup"><span data-stu-id="f5629-117">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span> <span data-ttu-id="f5629-118">Pour obtenir plus d’informations sur une page de codes, y compris son nom, consultez la fonction [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .</span><span class="sxs-lookup"><span data-stu-id="f5629-118">To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span>

<span data-ttu-id="f5629-119">Pour définir la page de codes d’entrée d’une console, utilisez la fonction [**SetConsoleCP**](setconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="f5629-119">To set a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) function.</span></span> <span data-ttu-id="f5629-120">Pour définir et interroger la page de codes de sortie d’une console, utilisez les fonctions [**SetConsoleOutputCP**](setconsoleoutputcp.md) et [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="f5629-120">To set and query a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions.</span></span>

<a name="requirements"></a><span data-ttu-id="f5629-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f5629-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f5629-122">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="f5629-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="f5629-123">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="f5629-123">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f5629-124">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="f5629-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="f5629-125">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="f5629-125">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f5629-126">En-tête</span><span class="sxs-lookup"><span data-stu-id="f5629-126">Header</span></span></p></td>
<td><span data-ttu-id="f5629-127">ConsoleApi. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f5629-127">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f5629-128">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="f5629-128">Library</span></span></p></td>
<td><span data-ttu-id="f5629-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="f5629-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f5629-130">DLL</span><span class="sxs-lookup"><span data-stu-id="f5629-130">DLL</span></span></p></td>
<td><span data-ttu-id="f5629-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f5629-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="f5629-132"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5629-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="f5629-133">Pages de codes de la console</span><span class="sxs-lookup"><span data-stu-id="f5629-133">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="f5629-134">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="f5629-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f5629-135">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="f5629-135">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="f5629-136">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="f5629-136">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="f5629-137">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="f5629-137">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

 

 




