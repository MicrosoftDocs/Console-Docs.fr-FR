---
title: GetConsoleAliasExes fonction)
description: Récupère les noms de tous les fichiers exécutables avec les alias de console définis.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetConsoleAliasExes
- wincon/GetConsoleAliasExes
- GetConsoleAliasExes
- consoleapi3/GetConsoleAliasExesA
- wincon/GetConsoleAliasExesA
- GetConsoleAliasExesA
- consoleapi3/GetConsoleAliasExesW
- wincon/GetConsoleAliasExesW
- GetConsoleAliasExesW
MS-HAID:
- base.getconsolealiasexes
- consoles.getconsolealiasexes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c229de09-cfa6-4829-9c9a-8ff63500eaf4
topic_type:
- apiref
api_name:
- GetConsoleAliasExes
- GetConsoleAliasExesA
- GetConsoleAliasExesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: e112112fc1510ab4c3f0a99ff9b208cc364e361a
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059180"
---
# <a name="getconsolealiasexes-function"></a><span data-ttu-id="4c2e5-104">GetConsoleAliasExes fonction)</span><span class="sxs-lookup"><span data-stu-id="4c2e5-104">GetConsoleAliasExes function</span></span>


<span data-ttu-id="4c2e5-105">Récupère les noms de tous les fichiers exécutables avec les alias de console définis.</span><span class="sxs-lookup"><span data-stu-id="4c2e5-105">Retrieves the names of all executable files with console aliases defined.</span></span>

<a name="syntax"></a><span data-ttu-id="4c2e5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c2e5-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliasExes(
  _Out_ LPTSTR lpExeNameBuffer,
  _In_  DWORD  ExeNameBufferLength
);
```

<a name="parameters"></a><span data-ttu-id="4c2e5-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4c2e5-107">Parameters</span></span>
----------

<span data-ttu-id="4c2e5-108">*lpExeNameBuffer* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="4c2e5-108">*lpExeNameBuffer* \[out\]</span></span>  
<span data-ttu-id="4c2e5-109">Pointeur vers une mémoire tampon qui reçoit les noms des fichiers exécutables.</span><span class="sxs-lookup"><span data-stu-id="4c2e5-109">A pointer to a buffer that receives the names of the executable files.</span></span>

<span data-ttu-id="4c2e5-110">*ExeNameBufferLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="4c2e5-110">*ExeNameBufferLength* \[in\]</span></span>  
<span data-ttu-id="4c2e5-111">Taille de la mémoire tampon vers laquelle pointe *lpExeNameBuffer*, en octets.</span><span class="sxs-lookup"><span data-stu-id="4c2e5-111">The size of the buffer pointed to by *lpExeNameBuffer*, in bytes.</span></span>

<a name="return-value"></a><span data-ttu-id="4c2e5-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="4c2e5-112">Return value</span></span>
------------

<span data-ttu-id="4c2e5-113">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="4c2e5-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4c2e5-114">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="4c2e5-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4c2e5-115">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4c2e5-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="4c2e5-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="4c2e5-116">Remarks</span></span>
-------

<span data-ttu-id="4c2e5-117">Pour déterminer la taille requise pour la mémoire tampon *lpExeNameBuffer* , utilisez la fonction [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) .</span><span class="sxs-lookup"><span data-stu-id="4c2e5-117">To determine the required size for the *lpExeNameBuffer* buffer, use the [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) function.</span></span>

<span data-ttu-id="4c2e5-118">Pour compiler une application qui utilise cette fonction, définissez \*\* \_ Win32 \_ winnt\*\* comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="4c2e5-118">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="4c2e5-119">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="4c2e5-119">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="4c2e5-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4c2e5-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="4c2e5-121">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="4c2e5-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="4c2e5-122">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="4c2e5-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4c2e5-123">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="4c2e5-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="4c2e5-124">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="4c2e5-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4c2e5-125">En-tête</span><span class="sxs-lookup"><span data-stu-id="4c2e5-125">Header</span></span></p></td>
<td><span data-ttu-id="4c2e5-126">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4c2e5-126">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4c2e5-127">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="4c2e5-127">Library</span></span></p></td>
<td><span data-ttu-id="4c2e5-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4c2e5-128">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4c2e5-129">DLL</span><span class="sxs-lookup"><span data-stu-id="4c2e5-129">DLL</span></span></p></td>
<td><span data-ttu-id="4c2e5-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4c2e5-130">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4c2e5-131">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="4c2e5-131">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="4c2e5-132"><strong>GetConsoleAliasExesW</strong> (Unicode) et <strong>GetConsoleAliasExesA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="4c2e5-132"><strong>GetConsoleAliasExesW</strong> (Unicode) and <strong>GetConsoleAliasExesA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="4c2e5-133"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c2e5-133"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="4c2e5-134">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="4c2e5-134">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="4c2e5-135">Alias de console</span><span class="sxs-lookup"><span data-stu-id="4c2e5-135">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="4c2e5-136">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="4c2e5-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4c2e5-137">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="4c2e5-137">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="4c2e5-138">**GetConsoleAliasExesLength**</span><span class="sxs-lookup"><span data-stu-id="4c2e5-138">**GetConsoleAliasExesLength**</span></span>](getconsolealiasexeslength.md)

[<span data-ttu-id="4c2e5-139">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="4c2e5-139">**GetConsoleAliases**</span></span>](getconsolealiases.md)

 

 




