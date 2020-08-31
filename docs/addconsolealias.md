---
title: AddConsoleAlias fonction)
description: Consultez les informations de référence sur la fonction AddConsoleAlias, qui définit un alias de console pour l’exécutable spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/AddConsoleAlias
- consoleapi3/AddConsoleAliasA
- consoleapi3/AddConsoleAliasW
- wincon/AddConsoleAlias
- wincon/AddConsoleAliasA
- wincon/AddConsoleAliasW
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
MS-HAID:
- base.addconsolealias
- consoles.addconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e4072c3c-cf32-4992-847e-efdb846e5784
topic_type:
- apiref
api_name:
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 108a77b3178e7695e7477ea198df616fa8bcb199
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059389"
---
# <a name="addconsolealias-function"></a><span data-ttu-id="190a0-104">AddConsoleAlias fonction)</span><span class="sxs-lookup"><span data-stu-id="190a0-104">AddConsoleAlias function</span></span>


<span data-ttu-id="190a0-105">Définit un alias de console pour l’exécutable spécifié.</span><span class="sxs-lookup"><span data-stu-id="190a0-105">Defines a console alias for the specified executable.</span></span>

<a name="syntax"></a><span data-ttu-id="190a0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="190a0-106">Syntax</span></span>
------

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

<a name="parameters"></a><span data-ttu-id="190a0-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="190a0-107">Parameters</span></span>
----------

<span data-ttu-id="190a0-108">*Source* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="190a0-108">*Source* \[in\]</span></span>  
<span data-ttu-id="190a0-109">Alias de la console à mapper au texte spécifié par la *cible*.</span><span class="sxs-lookup"><span data-stu-id="190a0-109">The console alias to be mapped to the text specified by *Target*.</span></span>

<span data-ttu-id="190a0-110">*Cible* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="190a0-110">*Target* \[in\]</span></span>  
<span data-ttu-id="190a0-111">Texte à substituer à la *source*.</span><span class="sxs-lookup"><span data-stu-id="190a0-111">The text to be substituted for *Source*.</span></span> <span data-ttu-id="190a0-112">Si ce paramètre a la **valeur null**, l’alias de la console est supprimé.</span><span class="sxs-lookup"><span data-stu-id="190a0-112">If this parameter is **NULL**, then the console alias is removed.</span></span>

<span data-ttu-id="190a0-113">*ExeName* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="190a0-113">*ExeName* \[in\]</span></span>  
<span data-ttu-id="190a0-114">Nom du fichier exécutable pour lequel l’alias de console doit être défini.</span><span class="sxs-lookup"><span data-stu-id="190a0-114">The name of the executable file for which the console alias is to be defined.</span></span>

<a name="return-value"></a><span data-ttu-id="190a0-115">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="190a0-115">Return value</span></span>
------------

<span data-ttu-id="190a0-116">Si la fonction est réussie, la valeur de retour est **true**.</span><span class="sxs-lookup"><span data-stu-id="190a0-116">If the function succeeds, the return value is **TRUE**.</span></span>

<span data-ttu-id="190a0-117">Si la fonction échoue, la valeur de retour est **false**.</span><span class="sxs-lookup"><span data-stu-id="190a0-117">If the function fails, the return value is **FALSE**.</span></span> <span data-ttu-id="190a0-118">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="190a0-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="190a0-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="190a0-119">Remarks</span></span>
-------

<span data-ttu-id="190a0-120">Pour compiler une application qui utilise cette fonction, définissez \*\* \_ Win32 \_ winnt\*\* comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="190a0-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="190a0-121">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="190a0-121">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="examples"></a><span data-ttu-id="190a0-122">Exemples</span><span class="sxs-lookup"><span data-stu-id="190a0-122">Examples</span></span>
--------

<span data-ttu-id="190a0-123">Pour obtenir un exemple, consultez [alias de console](console-aliases.md).</span><span class="sxs-lookup"><span data-stu-id="190a0-123">For an example, see [Console Aliases](console-aliases.md).</span></span>

<a name="requirements"></a><span data-ttu-id="190a0-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="190a0-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="190a0-125">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="190a0-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="190a0-126">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="190a0-126">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="190a0-127">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="190a0-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="190a0-128">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="190a0-128">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="190a0-129">En-tête</span><span class="sxs-lookup"><span data-stu-id="190a0-129">Header</span></span></p></td>
<td><span data-ttu-id="190a0-130">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="190a0-130">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="190a0-131">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="190a0-131">Library</span></span></p></td>
<td><span data-ttu-id="190a0-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="190a0-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="190a0-133">DLL</span><span class="sxs-lookup"><span data-stu-id="190a0-133">DLL</span></span></p></td>
<td><span data-ttu-id="190a0-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="190a0-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="190a0-135">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="190a0-135">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="190a0-136"><strong>AddConsoleAliasW</strong> (Unicode) et <strong>AddConsoleAliasA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="190a0-136"><strong>AddConsoleAliasW</strong> (Unicode) and <strong>AddConsoleAliasA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="190a0-137"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="190a0-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="190a0-138">Alias de console</span><span class="sxs-lookup"><span data-stu-id="190a0-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="190a0-139">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="190a0-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="190a0-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="190a0-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="190a0-141">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="190a0-141">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="190a0-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="190a0-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




