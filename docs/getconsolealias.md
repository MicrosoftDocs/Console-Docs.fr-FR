---
title: GetConsoleAlias fonction)
description: Récupère le texte de l’alias de console spécifié et le nom de l’exécutable.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
ms.openlocfilehash: d3706ddb86c270aeaf22f46e08e5381c79fea0bb
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357539"
---
# <a name="getconsolealias-function"></a><span data-ttu-id="ec640-104">GetConsoleAlias fonction)</span><span class="sxs-lookup"><span data-stu-id="ec640-104">GetConsoleAlias function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="ec640-105">Récupère le texte pour l’alias et l’exécutable de la console spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ec640-105">Retrieves the text for the specified console alias and executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="ec640-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec640-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAlias(
  _In_  LPTSTR lpSource,
  _Out_ LPTSTR lpTargetBuffer,
  _In_  DWORD  TargetBufferLength,
  _In_  LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="ec640-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ec640-107">Parameters</span></span>

<span data-ttu-id="ec640-108">*lpSource* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="ec640-108">*lpSource* \[in\]</span></span>  
<span data-ttu-id="ec640-109">Alias de la console dont le texte doit être récupéré.</span><span class="sxs-lookup"><span data-stu-id="ec640-109">The console alias whose text is to be retrieved.</span></span>

<span data-ttu-id="ec640-110">*lpTargetBuffer* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="ec640-110">*lpTargetBuffer* \[out\]</span></span>  
<span data-ttu-id="ec640-111">Pointeur vers une mémoire tampon qui reçoit le texte associé à l’alias de la console.</span><span class="sxs-lookup"><span data-stu-id="ec640-111">A pointer to a buffer that receives the text associated with the console alias.</span></span>

<span data-ttu-id="ec640-112">*TargetBufferLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="ec640-112">*TargetBufferLength* \[in\]</span></span>  
<span data-ttu-id="ec640-113">Taille de la mémoire tampon vers laquelle pointe *lpTargetBuffer*, en octets.</span><span class="sxs-lookup"><span data-stu-id="ec640-113">The size of the buffer pointed to by *lpTargetBuffer*, in bytes.</span></span>

<span data-ttu-id="ec640-114">*lpExeName* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="ec640-114">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="ec640-115">Nom du fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="ec640-115">The name of the executable file.</span></span>

## <a name="return-value"></a><span data-ttu-id="ec640-116">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="ec640-116">Return value</span></span>

<span data-ttu-id="ec640-117">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="ec640-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ec640-118">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="ec640-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ec640-119">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="ec640-119">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="ec640-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="ec640-120">Remarks</span></span>

<span data-ttu-id="ec640-121">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="ec640-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="ec640-122">Pour plus d’informations, consultez [utilisation des en-têtes Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="ec640-122">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="ec640-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ec640-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ec640-124">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ec640-124">Minimum supported client</span></span> | <span data-ttu-id="ec640-125">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ec640-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="ec640-126">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ec640-126">Minimum supported server</span></span> | <span data-ttu-id="ec640-127">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ec640-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="ec640-128">En-tête</span><span class="sxs-lookup"><span data-stu-id="ec640-128">Header</span></span> | <span data-ttu-id="ec640-129">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ec640-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ec640-130">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="ec640-130">Library</span></span> | <span data-ttu-id="ec640-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="ec640-131">Kernel32.lib</span></span> |
| <span data-ttu-id="ec640-132">DLL</span><span class="sxs-lookup"><span data-stu-id="ec640-132">DLL</span></span> | <span data-ttu-id="ec640-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ec640-133">Kernel32.dll</span></span> |
| <span data-ttu-id="ec640-134">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="ec640-134">Unicode and ANSI names</span></span> | <span data-ttu-id="ec640-135">**GetConsoleAliasW** (Unicode) et **GetConsoleAliasA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="ec640-135">**GetConsoleAliasW** (Unicode) and **GetConsoleAliasA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="ec640-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec640-136">See also</span></span>

[<span data-ttu-id="ec640-137">Alias d’une console</span><span class="sxs-lookup"><span data-stu-id="ec640-137">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="ec640-138">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="ec640-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ec640-139">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="ec640-139">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="ec640-140">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="ec640-140">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="ec640-141">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="ec640-141">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)