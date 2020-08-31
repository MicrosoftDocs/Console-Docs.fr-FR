---
title: GetConsoleOutputCP fonction)
description: Récupère la page de codes de sortie utilisée par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi/GetConsoleOutputCP
- wincon/GetConsoleOutputCP
- GetConsoleOutputCP
MS-HAID:
- '\_win32\_getconsoleoutputcp'
- base.getconsoleoutputcp
- consoles.getconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c23706c7-ce17-4825-a494-20ca44534d45
topic_type:
- apiref
api_name:
- GetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: e80618ebd5c6b29f00e79594c55bfa15fab315ba
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059148"
---
# <a name="getconsoleoutputcp-function"></a><span data-ttu-id="854f4-104">GetConsoleOutputCP fonction)</span><span class="sxs-lookup"><span data-stu-id="854f4-104">GetConsoleOutputCP function</span></span>


<span data-ttu-id="854f4-105">Récupère la page de codes de sortie utilisée par la console associée au processus appelant.</span><span class="sxs-lookup"><span data-stu-id="854f4-105">Retrieves the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="854f4-106">Une console utilise sa page de codes de sortie pour convertir les valeurs de caractères écrites par les différentes fonctions de sortie dans les images affichées dans la fenêtre de la console.</span><span class="sxs-lookup"><span data-stu-id="854f4-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

<a name="syntax"></a><span data-ttu-id="854f4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="854f4-107">Syntax</span></span>
------

```C
UINT WINAPI GetConsoleOutputCP(void);
```

<a name="parameters"></a><span data-ttu-id="854f4-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="854f4-108">Parameters</span></span>
----------

<span data-ttu-id="854f4-109">Cette fonction n’a pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="854f4-109">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="854f4-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="854f4-110">Return value</span></span>
------------

<span data-ttu-id="854f4-111">La valeur de retour est un code qui identifie la page de codes.</span><span class="sxs-lookup"><span data-stu-id="854f4-111">The return value is a code that identifies the code page.</span></span> <span data-ttu-id="854f4-112">Pour obtenir la liste des identificateurs, consultez [identificateurs de page de codes](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span><span class="sxs-lookup"><span data-stu-id="854f4-112">For a list of identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="854f4-113">Si la valeur de retour est égale à zéro, la fonction a échoué.</span><span class="sxs-lookup"><span data-stu-id="854f4-113">If the return value is zero, the function has failed.</span></span> <span data-ttu-id="854f4-114">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="854f4-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="854f4-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="854f4-115">Remarks</span></span>
-------

<span data-ttu-id="854f4-116">Une page de codes mappe 256 codes de caractères à des caractères individuels.</span><span class="sxs-lookup"><span data-stu-id="854f4-116">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="854f4-117">Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.</span><span class="sxs-lookup"><span data-stu-id="854f4-117">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span> <span data-ttu-id="854f4-118">Pour obtenir plus d’informations sur une page de codes, y compris son nom, consultez la fonction [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .</span><span class="sxs-lookup"><span data-stu-id="854f4-118">To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span>

<span data-ttu-id="854f4-119">Pour définir la page de codes de sortie d’une console, utilisez la fonction [**SetConsoleOutputCP**](setconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="854f4-119">To set a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) function.</span></span> <span data-ttu-id="854f4-120">Pour définir et interroger la page de codes d’entrée d’une console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) et [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="854f4-120">To set and query a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

<a name="requirements"></a><span data-ttu-id="854f4-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="854f4-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="854f4-122">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="854f4-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="854f4-123">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="854f4-123">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="854f4-124">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="854f4-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="854f4-125">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="854f4-125">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="854f4-126">En-tête</span><span class="sxs-lookup"><span data-stu-id="854f4-126">Header</span></span></p></td>
<td><span data-ttu-id="854f4-127">ConsoleApi. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="854f4-127">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="854f4-128">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="854f4-128">Library</span></span></p></td>
<td><span data-ttu-id="854f4-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="854f4-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="854f4-130">DLL</span><span class="sxs-lookup"><span data-stu-id="854f4-130">DLL</span></span></p></td>
<td><span data-ttu-id="854f4-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="854f4-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="854f4-132"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="854f4-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="854f4-133">Pages de codes de la console</span><span class="sxs-lookup"><span data-stu-id="854f4-133">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="854f4-134">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="854f4-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="854f4-135">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="854f4-135">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="854f4-136">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="854f4-136">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="854f4-137">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="854f4-137">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

 

 




