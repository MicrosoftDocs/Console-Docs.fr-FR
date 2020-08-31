---
title: SetConsoleOutputCP fonction)
description: Définit la page de codes de sortie utilisée par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/SetConsoleOutputCP
- wincon/SetConsoleOutputCP
- SetConsoleOutputCP
MS-HAID:
- '\_win32\_setconsoleoutputcp'
- base.setconsoleoutputcp
- consoles.setconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0b41e66b-ca19-4d69-9f39-92da158344ef
topic_type:
- apiref
api_name:
- SetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: ae1f3970af6c8db1ebedc29e0644ed001258ecc5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059525"
---
# <a name="setconsoleoutputcp-function"></a><span data-ttu-id="55161-104">SetConsoleOutputCP fonction)</span><span class="sxs-lookup"><span data-stu-id="55161-104">SetConsoleOutputCP function</span></span>


<span data-ttu-id="55161-105">Définit la page de codes de sortie utilisée par la console associée au processus appelant.</span><span class="sxs-lookup"><span data-stu-id="55161-105">Sets the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="55161-106">Une console utilise sa page de codes de sortie pour convertir les valeurs de caractères écrites par les différentes fonctions de sortie dans les images affichées dans la fenêtre de la console.</span><span class="sxs-lookup"><span data-stu-id="55161-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

<a name="syntax"></a><span data-ttu-id="55161-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55161-107">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleOutputCP(
  _In_ UINT wCodePageID
);
```

<a name="parameters"></a><span data-ttu-id="55161-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="55161-108">Parameters</span></span>
----------

<span data-ttu-id="55161-109">*wCodePageID* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="55161-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="55161-110">Identificateur de la page de codes à définir.</span><span class="sxs-lookup"><span data-stu-id="55161-110">The identifier of the code page to set.</span></span> <span data-ttu-id="55161-111">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="55161-111">For more information, see Remarks.</span></span>

<a name="return-value"></a><span data-ttu-id="55161-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="55161-112">Return value</span></span>
------------

<span data-ttu-id="55161-113">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="55161-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="55161-114">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="55161-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="55161-115">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="55161-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="55161-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="55161-116">Remarks</span></span>
-------

<span data-ttu-id="55161-117">Une page de codes mappe 256 codes de caractères à des caractères individuels.</span><span class="sxs-lookup"><span data-stu-id="55161-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="55161-118">Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.</span><span class="sxs-lookup"><span data-stu-id="55161-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="55161-119">Si la police actuelle est une police Unicode à espacement fixe, **SetConsoleOutputCP** modifie le mappage des valeurs de caractère dans le jeu de glyphes de la police, plutôt que de charger une police distincte chaque fois qu’elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="55161-119">If the current font is a fixed-pitch Unicode font, **SetConsoleOutputCP** changes the mapping of the character values into the glyph set of the font, rather than loading a separate font each time it is called.</span></span> <span data-ttu-id="55161-120">Cela affecte la façon dont les caractères étendus (valeur ASCII supérieure à 127) sont affichés dans une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="55161-120">This affects how extended characters (ASCII value greater than 127) are displayed in a console window.</span></span> <span data-ttu-id="55161-121">Toutefois, si la police actuelle est une police raster, **SetConsoleOutputCP** n’affecte pas la manière dont les caractères étendus sont affichés.</span><span class="sxs-lookup"><span data-stu-id="55161-121">However, if the current font is a raster font, **SetConsoleOutputCP** does not affect how extended characters are displayed.</span></span>

<span data-ttu-id="55161-122">Pour rechercher les pages de codes qui sont installées ou prises en charge par le système d’exploitation, utilisez la fonction [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) .</span><span class="sxs-lookup"><span data-stu-id="55161-122">To find the code pages that are installed or supported by the operating system, use the [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) function.</span></span> <span data-ttu-id="55161-123">Les identificateurs des pages de codes disponibles sur l’ordinateur local sont également stockés dans le Registre sous la clé suivante :</span><span class="sxs-lookup"><span data-stu-id="55161-123">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

<span data-ttu-id="55161-124">**HKEY \_ local \_ machine \\ System \\ CurrentControlSet \\ contrôler \\ la \\ page de codes nls**</span><span class="sxs-lookup"><span data-stu-id="55161-124">**HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Nls\\CodePage**</span></span>

<span data-ttu-id="55161-125">Toutefois, il est préférable d’utiliser [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) pour énumérer les pages de code, car le registre peut différer dans différentes versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="55161-125">However, it is better to use [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>
<span data-ttu-id="55161-126">Pour déterminer si une page de codes particulière est valide, utilisez la fonction [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) .</span><span class="sxs-lookup"><span data-stu-id="55161-126">To determine whether a particular code page is valid, use the [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) function.</span></span> <span data-ttu-id="55161-127">Pour obtenir plus d’informations sur une page de codes, y compris son nom, utilisez la fonction [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .</span><span class="sxs-lookup"><span data-stu-id="55161-127">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span> <span data-ttu-id="55161-128">Pour obtenir la liste des identificateurs de page de codes disponibles, consultez [identificateurs de page de codes](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span><span class="sxs-lookup"><span data-stu-id="55161-128">For a list of available code page identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="55161-129">Pour déterminer la page de codes de sortie actuelle d’une console, utilisez la fonction [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="55161-129">To determine a console's current output code page, use the [**GetConsoleOutputCP**](getconsoleoutputcp.md) function.</span></span> <span data-ttu-id="55161-130">Pour définir et récupérer la page de codes d’entrée d’une console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) et [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="55161-130">To set and retrieve a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

<a name="requirements"></a><span data-ttu-id="55161-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="55161-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="55161-132">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="55161-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="55161-133">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="55161-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="55161-134">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="55161-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="55161-135">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="55161-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="55161-136">En-tête</span><span class="sxs-lookup"><span data-stu-id="55161-136">Header</span></span></p></td>
<td><span data-ttu-id="55161-137">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="55161-137">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="55161-138">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="55161-138">Library</span></span></p></td>
<td><span data-ttu-id="55161-139">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="55161-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="55161-140">DLL</span><span class="sxs-lookup"><span data-stu-id="55161-140">DLL</span></span></p></td>
<td><span data-ttu-id="55161-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="55161-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="55161-142"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55161-142"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="55161-143">Pages de codes de la console</span><span class="sxs-lookup"><span data-stu-id="55161-143">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="55161-144">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="55161-144">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="55161-145">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="55161-145">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="55161-146">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="55161-146">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="55161-147">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="55161-147">**SetConsoleCP**</span></span>](setconsolecp.md)

 

 




