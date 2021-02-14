---
title: Fonction SetConsoleMode
description: Définit le mode d’entrée d’une mémoire tampon d’entrée de console ou le mode de sortie d’une mémoire tampon d’écran de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/SetConsoleMode
- wincon/SetConsoleMode
- SetConsoleMode
MS-HAID:
- '\_win32\_setconsolemode'
- base.setconsolemode
- consoles.setconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 77508d58-8a7a-4c47-9ec5-dc61e5c4beac
topic_type:
- apiref
api_name:
- SetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: b4e165610288a04af653f052a2f1071d7e45937d
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357659"
---
# <a name="setconsolemode-function"></a><span data-ttu-id="40ab3-104">Fonction SetConsoleMode</span><span class="sxs-lookup"><span data-stu-id="40ab3-104">SetConsoleMode function</span></span>

<span data-ttu-id="40ab3-105">Définit le mode d’entrée d’une mémoire tampon d’entrée de console ou le mode de sortie d’une mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="40ab3-105">Sets the input mode of a console's input buffer or the output mode of a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="40ab3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40ab3-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

## <a name="parameters"></a><span data-ttu-id="40ab3-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="40ab3-107">Parameters</span></span>

<span data-ttu-id="40ab3-108">*hConsoleHandle* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="40ab3-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="40ab3-109">Handle vers la mémoire tampon d’entrée de console ou mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="40ab3-109">A handle to the console input buffer or a console screen buffer.</span></span> <span data-ttu-id="40ab3-110">Le handle doit avoir le droit d’accès **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="40ab3-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="40ab3-111">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="40ab3-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="40ab3-112">*dwMode* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="40ab3-112">*dwMode* \[in\]</span></span>  
<span data-ttu-id="40ab3-113">Mode d’entrée ou de sortie à définir.</span><span class="sxs-lookup"><span data-stu-id="40ab3-113">The input or output mode to be set.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a><span data-ttu-id="40ab3-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="40ab3-114">Return value</span></span>

<span data-ttu-id="40ab3-115">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="40ab3-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="40ab3-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="40ab3-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="40ab3-117">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="40ab3-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="40ab3-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="40ab3-118">Remarks</span></span>

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

<span data-ttu-id="40ab3-119">Pour déterminer le mode actuel d’une mémoire tampon d’entrée de console ou d’une mémoire tampon d’écran, utilisez la fonction [**GetConsoleMode**](getconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="40ab3-119">To determine the current mode of a console input buffer or a screen buffer, use the [**GetConsoleMode**](getconsolemode.md) function.</span></span>

## <a name="examples"></a><span data-ttu-id="40ab3-120">Exemples</span><span class="sxs-lookup"><span data-stu-id="40ab3-120">Examples</span></span>

<span data-ttu-id="40ab3-121">Pour obtenir un exemple, consultez [Lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="40ab3-121">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="40ab3-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="40ab3-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="40ab3-123">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="40ab3-123">Minimum supported client</span></span> | <span data-ttu-id="40ab3-124">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="40ab3-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="40ab3-125">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="40ab3-125">Minimum supported server</span></span> | <span data-ttu-id="40ab3-126">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="40ab3-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="40ab3-127">En-tête</span><span class="sxs-lookup"><span data-stu-id="40ab3-127">Header</span></span> | <span data-ttu-id="40ab3-128">ConsoleApi.h (via WinCon.h, inclure Windows.h)</span><span class="sxs-lookup"><span data-stu-id="40ab3-128">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="40ab3-129">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="40ab3-129">Library</span></span> | <span data-ttu-id="40ab3-130">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="40ab3-130">Kernel32.lib</span></span> |
| <span data-ttu-id="40ab3-131">DLL</span><span class="sxs-lookup"><span data-stu-id="40ab3-131">DLL</span></span> | <span data-ttu-id="40ab3-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="40ab3-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="40ab3-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40ab3-133">See also</span></span>

[<span data-ttu-id="40ab3-134">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="40ab3-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="40ab3-135">Modes de la console</span><span class="sxs-lookup"><span data-stu-id="40ab3-135">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="40ab3-136">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="40ab3-136">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="40ab3-137">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="40ab3-137">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="40ab3-138">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="40ab3-138">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="40ab3-139">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="40ab3-139">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="40ab3-140">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="40ab3-140">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="40ab3-141">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="40ab3-141">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="40ab3-142">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="40ab3-142">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)