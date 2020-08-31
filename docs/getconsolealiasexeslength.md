---
title: GetConsoleAliasExesLength fonction)
description: Récupère la taille requise pour la mémoire tampon utilisée par la fonction GetConsoleAliasExes.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapie/GetConsoleAliasExesLength
- wincon/GetConsoleAliasExesLength
- GetConsoleAliasExesLength
- consoleapie/GetConsoleAliasExesLengthA
- wincon/GetConsoleAliasExesLengthA
- GetConsoleAliasExesLengthA
- consoleapie/GetConsoleAliasExesLengthW
- wincon/GetConsoleAliasExesLengthW
- GetConsoleAliasExesLengthW
MS-HAID:
- base.getconsolealiasexeslength
- consoles.getconsolealiasexeslength
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 4f23bbb1-3e43-47a9-b91a-e91529b07fb5
topic_type:
- apiref
api_name:
- GetConsoleAliasExesLength
- GetConsoleAliasExesLengthA
- GetConsoleAliasExesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0f4459254e9382a0c784ceb2c214af056087ab1b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059169"
---
# <a name="getconsolealiasexeslength-function"></a><span data-ttu-id="51eb9-104">GetConsoleAliasExesLength fonction)</span><span class="sxs-lookup"><span data-stu-id="51eb9-104">GetConsoleAliasExesLength function</span></span>


<span data-ttu-id="51eb9-105">Récupère la taille requise pour la mémoire tampon utilisée par la fonction [**GetConsoleAliasExes**](getconsolealiasexes.md) .</span><span class="sxs-lookup"><span data-stu-id="51eb9-105">Retrieves the required size for the buffer used by the [**GetConsoleAliasExes**](getconsolealiasexes.md) function.</span></span>

<a name="syntax"></a><span data-ttu-id="51eb9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51eb9-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliasExesLength(void);
```

<a name="parameters"></a><span data-ttu-id="51eb9-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="51eb9-107">Parameters</span></span>
----------

<span data-ttu-id="51eb9-108">Cette fonction n’a pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="51eb9-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="51eb9-109">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="51eb9-109">Return value</span></span>
------------

<span data-ttu-id="51eb9-110">Taille de la mémoire tampon requise pour stocker les noms de tous les fichiers exécutables qui ont des alias de console définis, en octets.</span><span class="sxs-lookup"><span data-stu-id="51eb9-110">The size of the buffer required to store the names of all executable files that have console aliases defined, in bytes.</span></span>

<a name="remarks"></a><span data-ttu-id="51eb9-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="51eb9-111">Remarks</span></span>
-------

<span data-ttu-id="51eb9-112">Pour compiler une application qui utilise cette fonction, définissez \*\* \_ Win32 \_ winnt\*\* comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="51eb9-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="51eb9-113">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="51eb9-113">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="51eb9-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="51eb9-114">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="51eb9-115">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="51eb9-115">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="51eb9-116">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="51eb9-116">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="51eb9-117">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="51eb9-117">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="51eb9-118">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="51eb9-118">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="51eb9-119">En-tête</span><span class="sxs-lookup"><span data-stu-id="51eb9-119">Header</span></span></p></td>
<td><span data-ttu-id="51eb9-120">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="51eb9-120">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="51eb9-121">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="51eb9-121">Library</span></span></p></td>
<td><span data-ttu-id="51eb9-122">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="51eb9-122">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="51eb9-123">DLL</span><span class="sxs-lookup"><span data-stu-id="51eb9-123">DLL</span></span></p></td>
<td><span data-ttu-id="51eb9-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="51eb9-124">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="51eb9-125">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="51eb9-125">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="51eb9-126"><strong>GetConsoleAliasExesLengthW</strong> (Unicode) et <strong>GetConsoleAliasExesLengthA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="51eb9-126"><strong>GetConsoleAliasExesLengthW</strong> (Unicode) and <strong>GetConsoleAliasExesLengthA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="51eb9-127"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51eb9-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="51eb9-128">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="51eb9-128">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="51eb9-129">Alias de console</span><span class="sxs-lookup"><span data-stu-id="51eb9-129">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="51eb9-130">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="51eb9-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="51eb9-131">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="51eb9-131">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="51eb9-132">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="51eb9-132">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="51eb9-133">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="51eb9-133">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




