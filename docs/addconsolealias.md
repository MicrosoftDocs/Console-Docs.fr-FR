---
title: AddConsoleAlias fonction)
description: Consultez les informations de référence sur la fonction AddConsoleAlias, qui définit un alias de console pour l’exécutable spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/AddConsoleAlias
- consoleapi3/AddConsoleAliasA
- consoleapi3/AddConsoleAliasW
- wincon/AddConsoleAlias
- wincon/AddConsoleAliasA
- wincon/AddConsoleAliasW
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
MS-HAID:
- base.addconsolealias
- consoles.addconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e4072c3c-cf32-4992-847e-efdb846e5784
topic_type:
- apiref
api_name:
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 2f2396122e693ab76ddf4e4e0bcdb2d38a2c042b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037550"
---
# <a name="addconsolealias-function"></a><span data-ttu-id="4c197-104">AddConsoleAlias fonction)</span><span class="sxs-lookup"><span data-stu-id="4c197-104">AddConsoleAlias function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="4c197-105">Définit un alias de console pour l’exécutable spécifié.</span><span class="sxs-lookup"><span data-stu-id="4c197-105">Defines a console alias for the specified executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="4c197-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c197-106">Syntax</span></span>

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

## <a name="parameters"></a><span data-ttu-id="4c197-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4c197-107">Parameters</span></span>

<span data-ttu-id="4c197-108">*Source* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="4c197-108">*Source* \[in\]</span></span>  
<span data-ttu-id="4c197-109">Alias de la console à mapper au texte spécifié par la *cible* .</span><span class="sxs-lookup"><span data-stu-id="4c197-109">The console alias to be mapped to the text specified by *Target* .</span></span>

<span data-ttu-id="4c197-110">*Cible* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="4c197-110">*Target* \[in\]</span></span>  
<span data-ttu-id="4c197-111">Texte à substituer à la *source* .</span><span class="sxs-lookup"><span data-stu-id="4c197-111">The text to be substituted for *Source* .</span></span> <span data-ttu-id="4c197-112">Si ce paramètre a la **valeur null** , l’alias de la console est supprimé.</span><span class="sxs-lookup"><span data-stu-id="4c197-112">If this parameter is **NULL** , then the console alias is removed.</span></span>

<span data-ttu-id="4c197-113">*ExeName* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="4c197-113">*ExeName* \[in\]</span></span>  
<span data-ttu-id="4c197-114">Nom du fichier exécutable pour lequel l’alias de console doit être défini.</span><span class="sxs-lookup"><span data-stu-id="4c197-114">The name of the executable file for which the console alias is to be defined.</span></span>

## <a name="return-value"></a><span data-ttu-id="4c197-115">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="4c197-115">Return value</span></span>

<span data-ttu-id="4c197-116">Si la fonction est réussie, la valeur de retour est **true** .</span><span class="sxs-lookup"><span data-stu-id="4c197-116">If the function succeeds, the return value is **TRUE** .</span></span>

<span data-ttu-id="4c197-117">Si la fonction échoue, la valeur de retour est **false** .</span><span class="sxs-lookup"><span data-stu-id="4c197-117">If the function fails, the return value is **FALSE** .</span></span> <span data-ttu-id="4c197-118">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4c197-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="4c197-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="4c197-119">Remarks</span></span>

<span data-ttu-id="4c197-120">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="4c197-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="4c197-121">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="4c197-121">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="examples"></a><span data-ttu-id="4c197-122">Exemples</span><span class="sxs-lookup"><span data-stu-id="4c197-122">Examples</span></span>

<span data-ttu-id="4c197-123">Pour obtenir un exemple, consultez [alias de console](console-aliases.md).</span><span class="sxs-lookup"><span data-stu-id="4c197-123">For an example, see [Console Aliases](console-aliases.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="4c197-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4c197-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4c197-125">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="4c197-125">Minimum supported client</span></span> | <span data-ttu-id="4c197-126">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="4c197-126">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="4c197-127">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="4c197-127">Minimum supported server</span></span> | <span data-ttu-id="4c197-128">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="4c197-128">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="4c197-129">En-tête</span><span class="sxs-lookup"><span data-stu-id="4c197-129">Header</span></span> | <span data-ttu-id="4c197-130">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4c197-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="4c197-131">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="4c197-131">Library</span></span> | <span data-ttu-id="4c197-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4c197-132">Kernel32.lib</span></span> |
| <span data-ttu-id="4c197-133">DLL</span><span class="sxs-lookup"><span data-stu-id="4c197-133">DLL</span></span> | <span data-ttu-id="4c197-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4c197-134">Kernel32.dll</span></span> |
| <span data-ttu-id="4c197-135">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="4c197-135">Unicode and ANSI names</span></span> | <span data-ttu-id="4c197-136">**AddConsoleAliasW** (Unicode) et **AddConsoleAliasA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="4c197-136">**AddConsoleAliasW** (Unicode) and **AddConsoleAliasA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="4c197-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c197-137">See also</span></span>

[<span data-ttu-id="4c197-138">Alias d’une console</span><span class="sxs-lookup"><span data-stu-id="4c197-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="4c197-139">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="4c197-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4c197-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="4c197-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="4c197-141">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="4c197-141">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="4c197-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="4c197-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
