---
title: GetConsoleAliasExesLength fonction)
description: Récupère la taille requise pour la mémoire tampon utilisée par la fonction GetConsoleAliasExes.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
ms.openlocfilehash: d204fd3effe5169b6be3e60a9e3c0d39fa418d20
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038907"
---
# <a name="getconsolealiasexeslength-function"></a><span data-ttu-id="ec913-104">GetConsoleAliasExesLength fonction)</span><span class="sxs-lookup"><span data-stu-id="ec913-104">GetConsoleAliasExesLength function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="ec913-105">Récupère la taille requise pour la mémoire tampon utilisée par la fonction [**GetConsoleAliasExes**](getconsolealiasexes.md) .</span><span class="sxs-lookup"><span data-stu-id="ec913-105">Retrieves the required size for the buffer used by the [**GetConsoleAliasExes**](getconsolealiasexes.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="ec913-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec913-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasExesLength(void);
```

## <a name="parameters"></a><span data-ttu-id="ec913-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ec913-107">Parameters</span></span>

<span data-ttu-id="ec913-108">Cette fonction n’a pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="ec913-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="ec913-109">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="ec913-109">Return value</span></span>

<span data-ttu-id="ec913-110">Taille de la mémoire tampon requise pour stocker les noms de tous les fichiers exécutables qui ont des alias de console définis, en octets.</span><span class="sxs-lookup"><span data-stu-id="ec913-110">The size of the buffer required to store the names of all executable files that have console aliases defined, in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="ec913-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="ec913-111">Remarks</span></span>

<span data-ttu-id="ec913-112">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="ec913-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="ec913-113">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="ec913-113">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="ec913-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ec913-114">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ec913-115">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ec913-115">Minimum supported client</span></span> | <span data-ttu-id="ec913-116">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ec913-116">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="ec913-117">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ec913-117">Minimum supported server</span></span> | <span data-ttu-id="ec913-118">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ec913-118">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="ec913-119">En-tête</span><span class="sxs-lookup"><span data-stu-id="ec913-119">Header</span></span> | <span data-ttu-id="ec913-120">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ec913-120">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ec913-121">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="ec913-121">Library</span></span> | <span data-ttu-id="ec913-122">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ec913-122">Kernel32.lib</span></span> |
| <span data-ttu-id="ec913-123">DLL</span><span class="sxs-lookup"><span data-stu-id="ec913-123">DLL</span></span> | <span data-ttu-id="ec913-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ec913-124">Kernel32.dll</span></span> |
| <span data-ttu-id="ec913-125">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="ec913-125">Unicode and ANSI names</span></span> | <span data-ttu-id="ec913-126">**GetConsoleAliasExesLengthW** (Unicode) et **GetConsoleAliasExesLengthA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="ec913-126">**GetConsoleAliasExesLengthW** (Unicode) and **GetConsoleAliasExesLengthA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="ec913-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec913-127">See also</span></span>

[<span data-ttu-id="ec913-128">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="ec913-128">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="ec913-129">Alias d’une console</span><span class="sxs-lookup"><span data-stu-id="ec913-129">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="ec913-130">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="ec913-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ec913-131">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="ec913-131">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="ec913-132">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="ec913-132">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="ec913-133">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="ec913-133">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
