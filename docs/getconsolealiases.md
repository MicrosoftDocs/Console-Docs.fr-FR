---
title: GetConsoleAliases fonction)
description: Récupère tous les alias de console définis pour l’exécutable spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetConsoleAliases
- wincon/GetConsoleAliases
- GetConsoleAliases
- consoleapi3/GetConsoleAliasesA
- wincon/GetConsoleAliasesA
- GetConsoleAliasesA
- consoleapi3/GetConsoleAliasesW
- wincon/GetConsoleAliasesW
- GetConsoleAliasesW
MS-HAID:
- base.getconsolealiases
- consoles.getconsolealiases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 92eefa4e-ffde-4886-afde-5aecf450b425
topic_type:
- apiref
api_name:
- GetConsoleAliases
- GetConsoleAliasesA
- GetConsoleAliasesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 9e8e28323d5b696390d574a86561d7414f419bcc
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059177"
---
# <a name="getconsolealiases-function"></a><span data-ttu-id="c5ee8-104">GetConsoleAliases fonction)</span><span class="sxs-lookup"><span data-stu-id="c5ee8-104">GetConsoleAliases function</span></span>


<span data-ttu-id="c5ee8-105">Récupère tous les alias de console définis pour l’exécutable spécifié.</span><span class="sxs-lookup"><span data-stu-id="c5ee8-105">Retrieves all defined console aliases for the specified executable.</span></span>

<a name="syntax"></a><span data-ttu-id="c5ee8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5ee8-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliases(
  _Out_ LPTSTR lpAliasBuffer,
  _In_  DWORD  AliasBufferLength,
  _In_  LPTSTR lpExeName
);
```

<a name="parameters"></a><span data-ttu-id="c5ee8-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5ee8-107">Parameters</span></span>
----------

<span data-ttu-id="c5ee8-108">*lpAliasBuffer* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="c5ee8-108">*lpAliasBuffer* \[out\]</span></span>  
<span data-ttu-id="c5ee8-109">Pointeur vers une mémoire tampon qui reçoit les alias.</span><span class="sxs-lookup"><span data-stu-id="c5ee8-109">A pointer to a buffer that receives the aliases.</span></span>

<span data-ttu-id="c5ee8-110">Le format des données est le suivant : *Source1* = *target1* \\ 0*source2* = *TARGET2* \\ 0... *SourceN* = *Ciblen* \\ 0, où *N* est le nombre d’alias de console définis.</span><span class="sxs-lookup"><span data-stu-id="c5ee8-110">The format of the data is as follows: *Source1*=*Target1*\\0*Source2*=*Target2*\\0... *SourceN*=*TargetN*\\0, where *N* is the number of console aliases defined.</span></span>

<span data-ttu-id="c5ee8-111">*AliasBufferLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="c5ee8-111">*AliasBufferLength* \[in\]</span></span>  
<span data-ttu-id="c5ee8-112">Taille de la mémoire tampon vers laquelle pointe *lpAliasBuffer*, en octets.</span><span class="sxs-lookup"><span data-stu-id="c5ee8-112">The size of the buffer pointed to by *lpAliasBuffer*, in bytes.</span></span>

<span data-ttu-id="c5ee8-113">*lpExeName* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="c5ee8-113">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="c5ee8-114">Fichier exécutable dont les alias doivent être récupérés.</span><span class="sxs-lookup"><span data-stu-id="c5ee8-114">The executable file whose aliases are to be retrieved.</span></span>

<a name="return-value"></a><span data-ttu-id="c5ee8-115">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="c5ee8-115">Return value</span></span>
------------

<span data-ttu-id="c5ee8-116">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="c5ee8-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c5ee8-117">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="c5ee8-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c5ee8-118">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="c5ee8-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="c5ee8-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="c5ee8-119">Remarks</span></span>
-------

<span data-ttu-id="c5ee8-120">Pour déterminer la taille requise pour la mémoire tampon *lpExeName* , utilisez la fonction [**GetConsoleAliasesLength**](getconsolealiaseslength.md) .</span><span class="sxs-lookup"><span data-stu-id="c5ee8-120">To determine the required size for the *lpExeName* buffer, use the [**GetConsoleAliasesLength**](getconsolealiaseslength.md) function.</span></span>

<span data-ttu-id="c5ee8-121">Pour compiler une application qui utilise cette fonction, définissez \*\* \_ Win32 \_ winnt\*\* comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="c5ee8-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="c5ee8-122">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="c5ee8-122">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="c5ee8-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c5ee8-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="c5ee8-124">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="c5ee8-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="c5ee8-125">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="c5ee8-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c5ee8-126">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="c5ee8-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="c5ee8-127">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="c5ee8-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c5ee8-128">En-tête</span><span class="sxs-lookup"><span data-stu-id="c5ee8-128">Header</span></span></p></td>
<td><span data-ttu-id="c5ee8-129">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c5ee8-129">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c5ee8-130">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="c5ee8-130">Library</span></span></p></td>
<td><span data-ttu-id="c5ee8-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="c5ee8-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c5ee8-132">DLL</span><span class="sxs-lookup"><span data-stu-id="c5ee8-132">DLL</span></span></p></td>
<td><span data-ttu-id="c5ee8-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c5ee8-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c5ee8-134">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="c5ee8-134">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="c5ee8-135"><strong>GetConsoleAliasesW</strong> (Unicode) et <strong>GetConsoleAliasesA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="c5ee8-135"><strong>GetConsoleAliasesW</strong> (Unicode) and <strong>GetConsoleAliasesA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="c5ee8-136"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5ee8-136"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="c5ee8-137">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="c5ee8-137">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="c5ee8-138">Alias de console</span><span class="sxs-lookup"><span data-stu-id="c5ee8-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="c5ee8-139">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="c5ee8-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c5ee8-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="c5ee8-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="c5ee8-141">**GetConsoleAliasesLength**</span><span class="sxs-lookup"><span data-stu-id="c5ee8-141">**GetConsoleAliasesLength**</span></span>](getconsolealiaseslength.md)

[<span data-ttu-id="c5ee8-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="c5ee8-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




