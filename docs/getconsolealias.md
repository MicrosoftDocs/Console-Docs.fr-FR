---
title: GetConsoleAlias fonction)
description: Récupère le texte de l’alias de console spécifié et le nom de l’exécutable.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetConsoleAlias
- wincon/GetConsoleAlias
- GetConsoleAlias
- consoleapi3/GetConsoleAliasA
- wincon/GetConsoleAliasA
- GetConsoleAliasA
- consoleapi3/GetConsoleAliasW
- wincon/GetConsoleAliasW
- GetConsoleAliasW
MS-HAID:
- base.getconsolealias
- consoles.getconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e8514f24-8121-4fad-94bb-c9eedf7a700d
topic_type:
- apiref
api_name:
- GetConsoleAlias
- GetConsoleAliasA
- GetConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 3a7797db4b559e66c1ec30f72e148ff00e79e7aa
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059181"
---
# <a name="getconsolealias-function"></a><span data-ttu-id="498c6-104">GetConsoleAlias fonction)</span><span class="sxs-lookup"><span data-stu-id="498c6-104">GetConsoleAlias function</span></span>


<span data-ttu-id="498c6-105">Récupère le texte pour l’alias et l’exécutable de la console spécifiés.</span><span class="sxs-lookup"><span data-stu-id="498c6-105">Retrieves the text for the specified console alias and executable.</span></span>

<a name="syntax"></a><span data-ttu-id="498c6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="498c6-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAlias(
  _In_  LPTSTR lpSource,
  _Out_ LPTSTR lpTargetBuffer,
  _In_  DWORD  TargetBufferLength,
  _In_  LPTSTR lpExeName
);
```

<a name="parameters"></a><span data-ttu-id="498c6-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="498c6-107">Parameters</span></span>
----------

<span data-ttu-id="498c6-108">*lpSource* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="498c6-108">*lpSource* \[in\]</span></span>  
<span data-ttu-id="498c6-109">Alias de la console dont le texte doit être récupéré.</span><span class="sxs-lookup"><span data-stu-id="498c6-109">The console alias whose text is to be retrieved.</span></span>

<span data-ttu-id="498c6-110">*lpTargetBuffer* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="498c6-110">*lpTargetBuffer* \[out\]</span></span>  
<span data-ttu-id="498c6-111">Pointeur vers une mémoire tampon qui reçoit le texte associé à l’alias de la console.</span><span class="sxs-lookup"><span data-stu-id="498c6-111">A pointer to a buffer that receives the text associated with the console alias.</span></span>

<span data-ttu-id="498c6-112">*TargetBufferLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="498c6-112">*TargetBufferLength* \[in\]</span></span>  
<span data-ttu-id="498c6-113">Taille de la mémoire tampon vers laquelle pointe *lpTargetBuffer*, en octets.</span><span class="sxs-lookup"><span data-stu-id="498c6-113">The size of the buffer pointed to by *lpTargetBuffer*, in bytes.</span></span>

<span data-ttu-id="498c6-114">*lpExeName* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="498c6-114">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="498c6-115">Nom du fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="498c6-115">The name of the executable file.</span></span>

<a name="return-value"></a><span data-ttu-id="498c6-116">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="498c6-116">Return value</span></span>
------------

<span data-ttu-id="498c6-117">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="498c6-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="498c6-118">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="498c6-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="498c6-119">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="498c6-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="498c6-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="498c6-120">Remarks</span></span>
-------

<span data-ttu-id="498c6-121">Pour compiler une application qui utilise cette fonction, définissez \*\* \_ Win32 \_ winnt\*\* comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="498c6-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="498c6-122">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="498c6-122">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="498c6-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="498c6-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="498c6-124">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="498c6-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="498c6-125">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="498c6-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="498c6-126">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="498c6-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="498c6-127">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="498c6-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="498c6-128">En-tête</span><span class="sxs-lookup"><span data-stu-id="498c6-128">Header</span></span></p></td>
<td><span data-ttu-id="498c6-129">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="498c6-129">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="498c6-130">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="498c6-130">Library</span></span></p></td>
<td><span data-ttu-id="498c6-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="498c6-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="498c6-132">DLL</span><span class="sxs-lookup"><span data-stu-id="498c6-132">DLL</span></span></p></td>
<td><span data-ttu-id="498c6-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="498c6-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="498c6-134">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="498c6-134">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="498c6-135"><strong>GetConsoleAliasW</strong> (Unicode) et <strong>GetConsoleAliasA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="498c6-135"><strong>GetConsoleAliasW</strong> (Unicode) and <strong>GetConsoleAliasA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="498c6-136"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="498c6-136"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="498c6-137">Alias de console</span><span class="sxs-lookup"><span data-stu-id="498c6-137">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="498c6-138">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="498c6-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="498c6-139">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="498c6-139">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="498c6-140">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="498c6-140">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="498c6-141">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="498c6-141">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




