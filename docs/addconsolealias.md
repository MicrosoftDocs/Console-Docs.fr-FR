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
ms.openlocfilehash: 9ff901615fa2a17ee9902bd028a2f63ee6b7a4b4
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357869"
---
# <a name="addconsolealias-function"></a><span data-ttu-id="f7cfc-104">AddConsoleAlias fonction)</span><span class="sxs-lookup"><span data-stu-id="f7cfc-104">AddConsoleAlias function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="f7cfc-105">Définit un alias de console pour l’exécutable spécifié.</span><span class="sxs-lookup"><span data-stu-id="f7cfc-105">Defines a console alias for the specified executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="f7cfc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7cfc-106">Syntax</span></span>

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

## <a name="parameters"></a><span data-ttu-id="f7cfc-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7cfc-107">Parameters</span></span>

<span data-ttu-id="f7cfc-108">*Source* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="f7cfc-108">*Source* \[in\]</span></span>  
<span data-ttu-id="f7cfc-109">Alias de la console à mapper au texte spécifié par la *cible*.</span><span class="sxs-lookup"><span data-stu-id="f7cfc-109">The console alias to be mapped to the text specified by *Target*.</span></span>

<span data-ttu-id="f7cfc-110">*Cible* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="f7cfc-110">*Target* \[in\]</span></span>  
<span data-ttu-id="f7cfc-111">Texte à substituer à la *source*.</span><span class="sxs-lookup"><span data-stu-id="f7cfc-111">The text to be substituted for *Source*.</span></span> <span data-ttu-id="f7cfc-112">Si ce paramètre a la **valeur null**, l’alias de la console est supprimé.</span><span class="sxs-lookup"><span data-stu-id="f7cfc-112">If this parameter is **NULL**, then the console alias is removed.</span></span>

<span data-ttu-id="f7cfc-113">*ExeName* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="f7cfc-113">*ExeName* \[in\]</span></span>  
<span data-ttu-id="f7cfc-114">Nom du fichier exécutable pour lequel l’alias de console doit être défini.</span><span class="sxs-lookup"><span data-stu-id="f7cfc-114">The name of the executable file for which the console alias is to be defined.</span></span>

## <a name="return-value"></a><span data-ttu-id="f7cfc-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f7cfc-115">Return value</span></span>

<span data-ttu-id="f7cfc-116">Si la fonction est réussie, la valeur de retour est **true**.</span><span class="sxs-lookup"><span data-stu-id="f7cfc-116">If the function succeeds, the return value is **TRUE**.</span></span>

<span data-ttu-id="f7cfc-117">Si la fonction échoue, la valeur de retour est **false**.</span><span class="sxs-lookup"><span data-stu-id="f7cfc-117">If the function fails, the return value is **FALSE**.</span></span> <span data-ttu-id="f7cfc-118">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="f7cfc-118">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="f7cfc-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="f7cfc-119">Remarks</span></span>

<span data-ttu-id="f7cfc-120">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="f7cfc-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="f7cfc-121">Pour plus d’informations, consultez [utilisation des en-têtes Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="f7cfc-121">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="examples"></a><span data-ttu-id="f7cfc-122">Exemples</span><span class="sxs-lookup"><span data-stu-id="f7cfc-122">Examples</span></span>

<span data-ttu-id="f7cfc-123">Pour obtenir un exemple, consultez [alias de console](console-aliases.md).</span><span class="sxs-lookup"><span data-stu-id="f7cfc-123">For an example, see [Console Aliases](console-aliases.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="f7cfc-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f7cfc-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="f7cfc-125">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="f7cfc-125">Minimum supported client</span></span> | <span data-ttu-id="f7cfc-126">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="f7cfc-126">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="f7cfc-127">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="f7cfc-127">Minimum supported server</span></span> | <span data-ttu-id="f7cfc-128">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="f7cfc-128">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="f7cfc-129">En-tête</span><span class="sxs-lookup"><span data-stu-id="f7cfc-129">Header</span></span> | <span data-ttu-id="f7cfc-130">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f7cfc-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="f7cfc-131">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="f7cfc-131">Library</span></span> | <span data-ttu-id="f7cfc-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="f7cfc-132">Kernel32.lib</span></span> |
| <span data-ttu-id="f7cfc-133">DLL</span><span class="sxs-lookup"><span data-stu-id="f7cfc-133">DLL</span></span> | <span data-ttu-id="f7cfc-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f7cfc-134">Kernel32.dll</span></span> |
| <span data-ttu-id="f7cfc-135">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="f7cfc-135">Unicode and ANSI names</span></span> | <span data-ttu-id="f7cfc-136">**AddConsoleAliasW** (Unicode) et **AddConsoleAliasA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="f7cfc-136">**AddConsoleAliasW** (Unicode) and **AddConsoleAliasA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="f7cfc-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7cfc-137">See also</span></span>

[<span data-ttu-id="f7cfc-138">Alias d’une console</span><span class="sxs-lookup"><span data-stu-id="f7cfc-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="f7cfc-139">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="f7cfc-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f7cfc-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="f7cfc-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="f7cfc-141">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="f7cfc-141">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="f7cfc-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="f7cfc-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)