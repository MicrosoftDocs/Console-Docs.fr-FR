---
title: GetConsoleAliases fonction)
description: Récupère tous les alias de console définis pour l’exécutable spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/GetConsoleAliases
- wincon/GetConsoleAliases
- GetConsoleAliases
- consoleapi3/GetConsoleAliasesA
- wincon/GetConsoleAliasesA
- GetConsoleAliasesA
- consoleapi3/GetConsoleAliasesW
- wincon/GetConsoleAliasesW
- GetConsoleAliasesW
MS-HAID:
- base.getconsolealiases
- consoles.getconsolealiases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 92eefa4e-ffde-4886-afde-5aecf450b425
topic_type:
- apiref
api_name:
- GetConsoleAliases
- GetConsoleAliasesA
- GetConsoleAliasesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: a84579ce7bf27787e986ded2e1f21520f8d442b9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038117"
---
# <a name="getconsolealiases-function"></a><span data-ttu-id="3fe89-104">GetConsoleAliases fonction)</span><span class="sxs-lookup"><span data-stu-id="3fe89-104">GetConsoleAliases function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="3fe89-105">Récupère tous les alias de console définis pour l’exécutable spécifié.</span><span class="sxs-lookup"><span data-stu-id="3fe89-105">Retrieves all defined console aliases for the specified executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="3fe89-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fe89-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliases(
  _Out_ LPTSTR lpAliasBuffer,
  _In_  DWORD  AliasBufferLength,
  _In_  LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="3fe89-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3fe89-107">Parameters</span></span>

<span data-ttu-id="3fe89-108">*lpAliasBuffer* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="3fe89-108">*lpAliasBuffer* \[out\]</span></span>  
<span data-ttu-id="3fe89-109">Pointeur vers une mémoire tampon qui reçoit les alias.</span><span class="sxs-lookup"><span data-stu-id="3fe89-109">A pointer to a buffer that receives the aliases.</span></span>

<span data-ttu-id="3fe89-110">Le format des données est le suivant : *Source1* = *target1* \\ 0 *source2* = *TARGET2* \\ 0... *SourceN* = *Ciblen* \\ 0, où *N* est le nombre d’alias de console définis.</span><span class="sxs-lookup"><span data-stu-id="3fe89-110">The format of the data is as follows: *Source1*=*Target1*\\0 *Source2*=*Target2*\\0... *SourceN*=*TargetN*\\0, where *N* is the number of console aliases defined.</span></span>

<span data-ttu-id="3fe89-111">*AliasBufferLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="3fe89-111">*AliasBufferLength* \[in\]</span></span>  
<span data-ttu-id="3fe89-112">Taille de la mémoire tampon vers laquelle pointe *lpAliasBuffer* , en octets.</span><span class="sxs-lookup"><span data-stu-id="3fe89-112">The size of the buffer pointed to by *lpAliasBuffer* , in bytes.</span></span>

<span data-ttu-id="3fe89-113">*lpExeName* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="3fe89-113">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="3fe89-114">Fichier exécutable dont les alias doivent être récupérés.</span><span class="sxs-lookup"><span data-stu-id="3fe89-114">The executable file whose aliases are to be retrieved.</span></span>

## <a name="return-value"></a><span data-ttu-id="3fe89-115">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="3fe89-115">Return value</span></span>

<span data-ttu-id="3fe89-116">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="3fe89-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="3fe89-117">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="3fe89-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="3fe89-118">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="3fe89-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="3fe89-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="3fe89-119">Remarks</span></span>

<span data-ttu-id="3fe89-120">Pour déterminer la taille requise pour la mémoire tampon *lpExeName* , utilisez la fonction [**GetConsoleAliasesLength**](getconsolealiaseslength.md) .</span><span class="sxs-lookup"><span data-stu-id="3fe89-120">To determine the required size for the *lpExeName* buffer, use the [**GetConsoleAliasesLength**](getconsolealiaseslength.md) function.</span></span>

<span data-ttu-id="3fe89-121">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="3fe89-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="3fe89-122">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="3fe89-122">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="3fe89-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3fe89-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="3fe89-124">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="3fe89-124">Minimum supported client</span></span> | <span data-ttu-id="3fe89-125">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="3fe89-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="3fe89-126">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="3fe89-126">Minimum supported server</span></span> | <span data-ttu-id="3fe89-127">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="3fe89-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="3fe89-128">En-tête</span><span class="sxs-lookup"><span data-stu-id="3fe89-128">Header</span></span> | <span data-ttu-id="3fe89-129">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="3fe89-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="3fe89-130">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="3fe89-130">Library</span></span> | <span data-ttu-id="3fe89-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="3fe89-131">Kernel32.lib</span></span> |
| <span data-ttu-id="3fe89-132">DLL</span><span class="sxs-lookup"><span data-stu-id="3fe89-132">DLL</span></span> | <span data-ttu-id="3fe89-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3fe89-133">Kernel32.dll</span></span> |
| <span data-ttu-id="3fe89-134">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="3fe89-134">Unicode and ANSI names</span></span> | <span data-ttu-id="3fe89-135">**GetConsoleAliasesW** (Unicode) et **GetConsoleAliasesA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="3fe89-135">**GetConsoleAliasesW** (Unicode) and **GetConsoleAliasesA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="3fe89-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fe89-136">See also</span></span>

[<span data-ttu-id="3fe89-137">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="3fe89-137">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="3fe89-138">Alias d’une console</span><span class="sxs-lookup"><span data-stu-id="3fe89-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="3fe89-139">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="3fe89-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3fe89-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="3fe89-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="3fe89-141">**GetConsoleAliasesLength**</span><span class="sxs-lookup"><span data-stu-id="3fe89-141">**GetConsoleAliasesLength**</span></span>](getconsolealiaseslength.md)

[<span data-ttu-id="3fe89-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="3fe89-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
