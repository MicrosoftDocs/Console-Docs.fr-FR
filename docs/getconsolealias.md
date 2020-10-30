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
ms.openlocfilehash: 37c441c48c2bb71fc8e590d4f8a80032561f833e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039027"
---
# <a name="getconsolealias-function"></a><span data-ttu-id="71453-104">GetConsoleAlias fonction)</span><span class="sxs-lookup"><span data-stu-id="71453-104">GetConsoleAlias function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="71453-105">Récupère le texte pour l’alias et l’exécutable de la console spécifiés.</span><span class="sxs-lookup"><span data-stu-id="71453-105">Retrieves the text for the specified console alias and executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="71453-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71453-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAlias(
  _In_  LPTSTR lpSource,
  _Out_ LPTSTR lpTargetBuffer,
  _In_  DWORD  TargetBufferLength,
  _In_  LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="71453-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="71453-107">Parameters</span></span>

<span data-ttu-id="71453-108">*lpSource* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="71453-108">*lpSource* \[in\]</span></span>  
<span data-ttu-id="71453-109">Alias de la console dont le texte doit être récupéré.</span><span class="sxs-lookup"><span data-stu-id="71453-109">The console alias whose text is to be retrieved.</span></span>

<span data-ttu-id="71453-110">*lpTargetBuffer* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="71453-110">*lpTargetBuffer* \[out\]</span></span>  
<span data-ttu-id="71453-111">Pointeur vers une mémoire tampon qui reçoit le texte associé à l’alias de la console.</span><span class="sxs-lookup"><span data-stu-id="71453-111">A pointer to a buffer that receives the text associated with the console alias.</span></span>

<span data-ttu-id="71453-112">*TargetBufferLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="71453-112">*TargetBufferLength* \[in\]</span></span>  
<span data-ttu-id="71453-113">Taille de la mémoire tampon vers laquelle pointe *lpTargetBuffer* , en octets.</span><span class="sxs-lookup"><span data-stu-id="71453-113">The size of the buffer pointed to by *lpTargetBuffer* , in bytes.</span></span>

<span data-ttu-id="71453-114">*lpExeName* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="71453-114">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="71453-115">Nom du fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="71453-115">The name of the executable file.</span></span>

## <a name="return-value"></a><span data-ttu-id="71453-116">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="71453-116">Return value</span></span>

<span data-ttu-id="71453-117">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="71453-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="71453-118">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="71453-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="71453-119">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="71453-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="71453-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="71453-120">Remarks</span></span>

<span data-ttu-id="71453-121">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="71453-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="71453-122">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="71453-122">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="71453-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="71453-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="71453-124">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="71453-124">Minimum supported client</span></span> | <span data-ttu-id="71453-125">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="71453-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="71453-126">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="71453-126">Minimum supported server</span></span> | <span data-ttu-id="71453-127">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="71453-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="71453-128">En-tête</span><span class="sxs-lookup"><span data-stu-id="71453-128">Header</span></span> | <span data-ttu-id="71453-129">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="71453-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="71453-130">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="71453-130">Library</span></span> | <span data-ttu-id="71453-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="71453-131">Kernel32.lib</span></span> |
| <span data-ttu-id="71453-132">DLL</span><span class="sxs-lookup"><span data-stu-id="71453-132">DLL</span></span> | <span data-ttu-id="71453-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="71453-133">Kernel32.dll</span></span> |
| <span data-ttu-id="71453-134">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="71453-134">Unicode and ANSI names</span></span> | <span data-ttu-id="71453-135">**GetConsoleAliasW** (Unicode) et **GetConsoleAliasA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="71453-135">**GetConsoleAliasW** (Unicode) and **GetConsoleAliasA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="71453-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71453-136">See also</span></span>

[<span data-ttu-id="71453-137">Alias d’une console</span><span class="sxs-lookup"><span data-stu-id="71453-137">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="71453-138">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="71453-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="71453-139">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="71453-139">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="71453-140">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="71453-140">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="71453-141">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="71453-141">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
