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
ms.openlocfilehash: 395acba39600fe1a98a80ed06ea23646b0b9f174
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038957"
---
# <a name="getconsolealiaseslength-function"></a><span data-ttu-id="1ec1f-104">GetConsoleAliasesLength fonction)</span><span class="sxs-lookup"><span data-stu-id="1ec1f-104">GetConsoleAliasesLength function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="1ec1f-105">Récupère la taille requise pour la mémoire tampon utilisée par la fonction [**GetConsoleAliases**](getconsolealiases.md) .</span><span class="sxs-lookup"><span data-stu-id="1ec1f-105">Retrieves the required size for the buffer used by the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ec1f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ec1f-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="1ec1f-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1ec1f-107">Parameters</span></span>

<span data-ttu-id="1ec1f-108">*lpExeName* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="1ec1f-108">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="1ec1f-109">Nom du fichier exécutable dont les alias de console doivent être récupérés.</span><span class="sxs-lookup"><span data-stu-id="1ec1f-109">The name of the executable file whose console aliases are to be retrieved.</span></span>

## <a name="return-value"></a><span data-ttu-id="1ec1f-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="1ec1f-110">Return value</span></span>

<span data-ttu-id="1ec1f-111">Taille de la mémoire tampon requise pour stocker tous les alias de console définis pour ce fichier exécutable, en octets.</span><span class="sxs-lookup"><span data-stu-id="1ec1f-111">The size of the buffer required to store all console aliases defined for this executable file, in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ec1f-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="1ec1f-112">Remarks</span></span>

<span data-ttu-id="1ec1f-113">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="1ec1f-113">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="1ec1f-114">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="1ec1f-114">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="1ec1f-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1ec1f-115">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1ec1f-116">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="1ec1f-116">Minimum supported client</span></span> | <span data-ttu-id="1ec1f-117">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="1ec1f-117">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="1ec1f-118">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="1ec1f-118">Minimum supported server</span></span> | <span data-ttu-id="1ec1f-119">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="1ec1f-119">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="1ec1f-120">En-tête</span><span class="sxs-lookup"><span data-stu-id="1ec1f-120">Header</span></span> | <span data-ttu-id="1ec1f-121">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1ec1f-121">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="1ec1f-122">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="1ec1f-122">Library</span></span> | <span data-ttu-id="1ec1f-123">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="1ec1f-123">Kernel32.lib</span></span> |
| <span data-ttu-id="1ec1f-124">DLL</span><span class="sxs-lookup"><span data-stu-id="1ec1f-124">DLL</span></span> | <span data-ttu-id="1ec1f-125">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1ec1f-125">Kernel32.dll</span></span> |
| <span data-ttu-id="1ec1f-126">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="1ec1f-126">Unicode and ANSI names</span></span> | <span data-ttu-id="1ec1f-127">**GetConsoleAliasesLengthW** (Unicode) et **GetConsoleAliasesLengthA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="1ec1f-127">**GetConsoleAliasesLengthW** (Unicode) and **GetConsoleAliasesLengthA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="1ec1f-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ec1f-128">See also</span></span>

[<span data-ttu-id="1ec1f-129">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="1ec1f-129">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="1ec1f-130">Alias d’une console</span><span class="sxs-lookup"><span data-stu-id="1ec1f-130">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="1ec1f-131">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="1ec1f-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1ec1f-132">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="1ec1f-132">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="1ec1f-133">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="1ec1f-133">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="1ec1f-134">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="1ec1f-134">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
