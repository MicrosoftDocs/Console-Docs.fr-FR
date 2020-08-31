---
title: GetConsoleAliasesLength fonction)
description: Récupère la taille requise pour la mémoire tampon utilisée par la fonction GetConsoleAliases.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetConsoleAliasesLength
- wincon/GetConsoleAliasesLength
- GetConsoleAliasesLength
- consoleapi3/GetConsoleAliasesLengthA
- wincon/GetConsoleAliasesLengthA
- GetConsoleAliasesLengthA
- consoleapi3/GetConsoleAliasesLengthW
- wincon/GetConsoleAliasesLengthW
- GetConsoleAliasesLengthW
MS-HAID:
- base.getconsolealiaseslength
- consoles.getconsolealiaseslength
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 29e49eba-0864-4ed7-af82-1ba639261c40
topic_type:
- apiref
api_name:
- GetConsoleAliasesLength
- GetConsoleAliasesLengthA
- GetConsoleAliasesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 23d820574aab837c89f2598e9934536b91715426
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059173"
---
# <a name="getconsolealiaseslength-function"></a><span data-ttu-id="bdc94-104">GetConsoleAliasesLength fonction)</span><span class="sxs-lookup"><span data-stu-id="bdc94-104">GetConsoleAliasesLength function</span></span>


<span data-ttu-id="bdc94-105">Récupère la taille requise pour la mémoire tampon utilisée par la fonction [**GetConsoleAliases**](getconsolealiases.md) .</span><span class="sxs-lookup"><span data-stu-id="bdc94-105">Retrieves the required size for the buffer used by the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span>

<a name="syntax"></a><span data-ttu-id="bdc94-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdc94-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

<a name="parameters"></a><span data-ttu-id="bdc94-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bdc94-107">Parameters</span></span>
----------

<span data-ttu-id="bdc94-108">*lpExeName* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="bdc94-108">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="bdc94-109">Nom du fichier exécutable dont les alias de console doivent être récupérés.</span><span class="sxs-lookup"><span data-stu-id="bdc94-109">The name of the executable file whose console aliases are to be retrieved.</span></span>

<a name="return-value"></a><span data-ttu-id="bdc94-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="bdc94-110">Return value</span></span>
------------

<span data-ttu-id="bdc94-111">Taille de la mémoire tampon requise pour stocker tous les alias de console définis pour ce fichier exécutable, en octets.</span><span class="sxs-lookup"><span data-stu-id="bdc94-111">The size of the buffer required to store all console aliases defined for this executable file, in bytes.</span></span>

<a name="remarks"></a><span data-ttu-id="bdc94-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="bdc94-112">Remarks</span></span>
-------

<span data-ttu-id="bdc94-113">Pour compiler une application qui utilise cette fonction, définissez \*\* \_ Win32 \_ winnt\*\* comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="bdc94-113">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="bdc94-114">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="bdc94-114">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="bdc94-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bdc94-115">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="bdc94-116">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="bdc94-116">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="bdc94-117">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="bdc94-117">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bdc94-118">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="bdc94-118">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="bdc94-119">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="bdc94-119">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bdc94-120">En-tête</span><span class="sxs-lookup"><span data-stu-id="bdc94-120">Header</span></span></p></td>
<td><span data-ttu-id="bdc94-121">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="bdc94-121">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bdc94-122">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="bdc94-122">Library</span></span></p></td>
<td><span data-ttu-id="bdc94-123">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="bdc94-123">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bdc94-124">DLL</span><span class="sxs-lookup"><span data-stu-id="bdc94-124">DLL</span></span></p></td>
<td><span data-ttu-id="bdc94-125">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="bdc94-125">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bdc94-126">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="bdc94-126">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="bdc94-127"><strong>GetConsoleAliasesLengthW</strong> (Unicode) et <strong>GetConsoleAliasesLengthA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="bdc94-127"><strong>GetConsoleAliasesLengthW</strong> (Unicode) and <strong>GetConsoleAliasesLengthA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="bdc94-128"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdc94-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="bdc94-129">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="bdc94-129">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="bdc94-130">Alias de console</span><span class="sxs-lookup"><span data-stu-id="bdc94-130">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="bdc94-131">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="bdc94-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="bdc94-132">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="bdc94-132">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="bdc94-133">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="bdc94-133">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="bdc94-134">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="bdc94-134">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




