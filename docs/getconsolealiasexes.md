---
title: GetConsoleAliasExes fonction)
description: Récupère les noms de tous les fichiers exécutables avec les alias de console définis.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
ms.openlocfilehash: 1a97df0c22f084389e9bd6df1c4a2e8863090b45
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357492"
---
# <a name="getconsolealiasexes-function"></a><span data-ttu-id="41702-104">GetConsoleAliasExes fonction)</span><span class="sxs-lookup"><span data-stu-id="41702-104">GetConsoleAliasExes function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="41702-105">Récupère les noms de tous les fichiers exécutables avec les alias de console définis.</span><span class="sxs-lookup"><span data-stu-id="41702-105">Retrieves the names of all executable files with console aliases defined.</span></span>

## <a name="syntax"></a><span data-ttu-id="41702-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41702-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasExes(
  _Out_ LPTSTR lpExeNameBuffer,
  _In_  DWORD  ExeNameBufferLength
);
```

## <a name="parameters"></a><span data-ttu-id="41702-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="41702-107">Parameters</span></span>

<span data-ttu-id="41702-108">*lpExeNameBuffer* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="41702-108">*lpExeNameBuffer* \[out\]</span></span>  
<span data-ttu-id="41702-109">Pointeur vers une mémoire tampon qui reçoit les noms des fichiers exécutables.</span><span class="sxs-lookup"><span data-stu-id="41702-109">A pointer to a buffer that receives the names of the executable files.</span></span>

<span data-ttu-id="41702-110">*ExeNameBufferLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="41702-110">*ExeNameBufferLength* \[in\]</span></span>  
<span data-ttu-id="41702-111">Taille de la mémoire tampon vers laquelle pointe *lpExeNameBuffer*, en octets.</span><span class="sxs-lookup"><span data-stu-id="41702-111">The size of the buffer pointed to by *lpExeNameBuffer*, in bytes.</span></span>

## <a name="return-value"></a><span data-ttu-id="41702-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="41702-112">Return value</span></span>

<span data-ttu-id="41702-113">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="41702-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="41702-114">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="41702-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="41702-115">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="41702-115">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="41702-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="41702-116">Remarks</span></span>

<span data-ttu-id="41702-117">Pour déterminer la taille requise pour la mémoire tampon *lpExeNameBuffer* , utilisez la fonction [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) .</span><span class="sxs-lookup"><span data-stu-id="41702-117">To determine the required size for the *lpExeNameBuffer* buffer, use the [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) function.</span></span>

<span data-ttu-id="41702-118">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="41702-118">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="41702-119">Pour plus d’informations, consultez [utilisation des en-têtes Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="41702-119">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="41702-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="41702-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="41702-121">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="41702-121">Minimum supported client</span></span> | <span data-ttu-id="41702-122">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="41702-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="41702-123">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="41702-123">Minimum supported server</span></span> | <span data-ttu-id="41702-124">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="41702-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="41702-125">En-tête</span><span class="sxs-lookup"><span data-stu-id="41702-125">Header</span></span> | <span data-ttu-id="41702-126">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="41702-126">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="41702-127">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="41702-127">Library</span></span> | <span data-ttu-id="41702-128">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="41702-128">Kernel32.lib</span></span> |
| <span data-ttu-id="41702-129">DLL</span><span class="sxs-lookup"><span data-stu-id="41702-129">DLL</span></span> | <span data-ttu-id="41702-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="41702-130">Kernel32.dll</span></span> |
| <span data-ttu-id="41702-131">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="41702-131">Unicode and ANSI names</span></span> | <span data-ttu-id="41702-132">**GetConsoleAliasExesW** (Unicode) et **GetConsoleAliasExesA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="41702-132">**GetConsoleAliasExesW** (Unicode) and **GetConsoleAliasExesA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="41702-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41702-133">See also</span></span>

[<span data-ttu-id="41702-134">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="41702-134">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="41702-135">Alias d’une console</span><span class="sxs-lookup"><span data-stu-id="41702-135">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="41702-136">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="41702-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="41702-137">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="41702-137">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="41702-138">**GetConsoleAliasExesLength**</span><span class="sxs-lookup"><span data-stu-id="41702-138">**GetConsoleAliasExesLength**</span></span>](getconsolealiasexeslength.md)

[<span data-ttu-id="41702-139">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="41702-139">**GetConsoleAliases**</span></span>](getconsolealiases.md)