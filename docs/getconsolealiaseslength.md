---
title: GetConsoleAliasesLength fonction)
description: Récupère la taille requise pour la mémoire tampon utilisée par la fonction GetConsoleAliases.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
ms.openlocfilehash: 78f9d718c960478e491b76a12f2a670c03529242
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357496"
---
# <a name="getconsolealiaseslength-function"></a><span data-ttu-id="1e895-104">GetConsoleAliasesLength fonction)</span><span class="sxs-lookup"><span data-stu-id="1e895-104">GetConsoleAliasesLength function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="1e895-105">Récupère la taille requise pour la mémoire tampon utilisée par la fonction [**GetConsoleAliases**](getconsolealiases.md) .</span><span class="sxs-lookup"><span data-stu-id="1e895-105">Retrieves the required size for the buffer used by the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="1e895-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e895-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="1e895-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1e895-107">Parameters</span></span>

<span data-ttu-id="1e895-108">*lpExeName* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="1e895-108">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="1e895-109">Nom du fichier exécutable dont les alias de console doivent être récupérés.</span><span class="sxs-lookup"><span data-stu-id="1e895-109">The name of the executable file whose console aliases are to be retrieved.</span></span>

## <a name="return-value"></a><span data-ttu-id="1e895-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1e895-110">Return value</span></span>

<span data-ttu-id="1e895-111">Taille de la mémoire tampon requise pour stocker tous les alias de console définis pour ce fichier exécutable, en octets.</span><span class="sxs-lookup"><span data-stu-id="1e895-111">The size of the buffer required to store all console aliases defined for this executable file, in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="1e895-112">Notes</span><span class="sxs-lookup"><span data-stu-id="1e895-112">Remarks</span></span>

<span data-ttu-id="1e895-113">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="1e895-113">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="1e895-114">Pour plus d’informations, consultez [utilisation des en-têtes Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="1e895-114">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="1e895-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1e895-115">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1e895-116">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="1e895-116">Minimum supported client</span></span> | <span data-ttu-id="1e895-117">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="1e895-117">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="1e895-118">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="1e895-118">Minimum supported server</span></span> | <span data-ttu-id="1e895-119">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="1e895-119">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="1e895-120">En-tête</span><span class="sxs-lookup"><span data-stu-id="1e895-120">Header</span></span> | <span data-ttu-id="1e895-121">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1e895-121">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="1e895-122">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="1e895-122">Library</span></span> | <span data-ttu-id="1e895-123">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="1e895-123">Kernel32.lib</span></span> |
| <span data-ttu-id="1e895-124">DLL</span><span class="sxs-lookup"><span data-stu-id="1e895-124">DLL</span></span> | <span data-ttu-id="1e895-125">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1e895-125">Kernel32.dll</span></span> |
| <span data-ttu-id="1e895-126">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="1e895-126">Unicode and ANSI names</span></span> | <span data-ttu-id="1e895-127">**GetConsoleAliasesLengthW** (Unicode) et **GetConsoleAliasesLengthA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="1e895-127">**GetConsoleAliasesLengthW** (Unicode) and **GetConsoleAliasesLengthA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="1e895-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e895-128">See also</span></span>

[<span data-ttu-id="1e895-129">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="1e895-129">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="1e895-130">Alias d’une console</span><span class="sxs-lookup"><span data-stu-id="1e895-130">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="1e895-131">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="1e895-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1e895-132">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="1e895-132">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="1e895-133">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="1e895-133">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="1e895-134">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="1e895-134">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)