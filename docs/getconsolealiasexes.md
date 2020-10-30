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
ms.openlocfilehash: 0e818c8ecee8ac777f7cc3cf2394d8846bebd034
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038077"
---
# <a name="getconsolealiasexes-function"></a><span data-ttu-id="e8c20-104">GetConsoleAliasExes fonction)</span><span class="sxs-lookup"><span data-stu-id="e8c20-104">GetConsoleAliasExes function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="e8c20-105">Récupère les noms de tous les fichiers exécutables avec les alias de console définis.</span><span class="sxs-lookup"><span data-stu-id="e8c20-105">Retrieves the names of all executable files with console aliases defined.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8c20-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8c20-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasExes(
  _Out_ LPTSTR lpExeNameBuffer,
  _In_  DWORD  ExeNameBufferLength
);
```

## <a name="parameters"></a><span data-ttu-id="e8c20-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8c20-107">Parameters</span></span>

<span data-ttu-id="e8c20-108">*lpExeNameBuffer* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="e8c20-108">*lpExeNameBuffer* \[out\]</span></span>  
<span data-ttu-id="e8c20-109">Pointeur vers une mémoire tampon qui reçoit les noms des fichiers exécutables.</span><span class="sxs-lookup"><span data-stu-id="e8c20-109">A pointer to a buffer that receives the names of the executable files.</span></span>

<span data-ttu-id="e8c20-110">*ExeNameBufferLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="e8c20-110">*ExeNameBufferLength* \[in\]</span></span>  
<span data-ttu-id="e8c20-111">Taille de la mémoire tampon vers laquelle pointe *lpExeNameBuffer* , en octets.</span><span class="sxs-lookup"><span data-stu-id="e8c20-111">The size of the buffer pointed to by *lpExeNameBuffer* , in bytes.</span></span>

## <a name="return-value"></a><span data-ttu-id="e8c20-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="e8c20-112">Return value</span></span>

<span data-ttu-id="e8c20-113">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="e8c20-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e8c20-114">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="e8c20-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e8c20-115">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="e8c20-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="e8c20-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="e8c20-116">Remarks</span></span>

<span data-ttu-id="e8c20-117">Pour déterminer la taille requise pour la mémoire tampon *lpExeNameBuffer* , utilisez la fonction [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) .</span><span class="sxs-lookup"><span data-stu-id="e8c20-117">To determine the required size for the *lpExeNameBuffer* buffer, use the [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) function.</span></span>

<span data-ttu-id="e8c20-118">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="e8c20-118">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="e8c20-119">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="e8c20-119">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="e8c20-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e8c20-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e8c20-121">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="e8c20-121">Minimum supported client</span></span> | <span data-ttu-id="e8c20-122">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="e8c20-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="e8c20-123">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="e8c20-123">Minimum supported server</span></span> | <span data-ttu-id="e8c20-124">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="e8c20-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="e8c20-125">En-tête</span><span class="sxs-lookup"><span data-stu-id="e8c20-125">Header</span></span> | <span data-ttu-id="e8c20-126">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e8c20-126">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="e8c20-127">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="e8c20-127">Library</span></span> | <span data-ttu-id="e8c20-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="e8c20-128">Kernel32.lib</span></span> |
| <span data-ttu-id="e8c20-129">DLL</span><span class="sxs-lookup"><span data-stu-id="e8c20-129">DLL</span></span> | <span data-ttu-id="e8c20-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e8c20-130">Kernel32.dll</span></span> |
| <span data-ttu-id="e8c20-131">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="e8c20-131">Unicode and ANSI names</span></span> | <span data-ttu-id="e8c20-132">**GetConsoleAliasExesW** (Unicode) et **GetConsoleAliasExesA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="e8c20-132">**GetConsoleAliasExesW** (Unicode) and **GetConsoleAliasExesA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="e8c20-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8c20-133">See also</span></span>

[<span data-ttu-id="e8c20-134">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="e8c20-134">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="e8c20-135">Alias d’une console</span><span class="sxs-lookup"><span data-stu-id="e8c20-135">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="e8c20-136">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="e8c20-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e8c20-137">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="e8c20-137">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="e8c20-138">**GetConsoleAliasExesLength**</span><span class="sxs-lookup"><span data-stu-id="e8c20-138">**GetConsoleAliasExesLength**</span></span>](getconsolealiasexeslength.md)

[<span data-ttu-id="e8c20-139">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="e8c20-139">**GetConsoleAliases**</span></span>](getconsolealiases.md)
