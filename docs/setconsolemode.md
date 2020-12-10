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
ms.openlocfilehash: 2af598f465be6e1a33f5a8f9a2c9abe98d6ed0d2
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420298"
---
# <a name="setconsolemode-function"></a><span data-ttu-id="960b2-104">Fonction SetConsoleMode</span><span class="sxs-lookup"><span data-stu-id="960b2-104">SetConsoleMode function</span></span>

<span data-ttu-id="960b2-105">Définit le mode d’entrée d’une mémoire tampon d’entrée de console ou le mode de sortie d’une mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="960b2-105">Sets the input mode of a console's input buffer or the output mode of a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="960b2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="960b2-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

## <a name="parameters"></a><span data-ttu-id="960b2-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="960b2-107">Parameters</span></span>

<span data-ttu-id="960b2-108">*hConsoleHandle* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="960b2-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="960b2-109">Handle vers la mémoire tampon d’entrée de console ou mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="960b2-109">A handle to the console input buffer or a console screen buffer.</span></span> <span data-ttu-id="960b2-110">Le handle doit avoir le droit d’accès **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="960b2-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="960b2-111">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="960b2-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="960b2-112">*dwMode* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="960b2-112">*dwMode* \[in\]</span></span>  
<span data-ttu-id="960b2-113">Mode d’entrée ou de sortie à définir.</span><span class="sxs-lookup"><span data-stu-id="960b2-113">The input or output mode to be set.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a><span data-ttu-id="960b2-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="960b2-114">Return value</span></span>

<span data-ttu-id="960b2-115">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="960b2-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="960b2-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="960b2-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="960b2-117">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="960b2-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="960b2-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="960b2-118">Remarks</span></span>

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

<span data-ttu-id="960b2-119">Pour déterminer le mode actuel d’une mémoire tampon d’entrée de console ou d’une mémoire tampon d’écran, utilisez la fonction [**GetConsoleMode**](getconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="960b2-119">To determine the current mode of a console input buffer or a screen buffer, use the [**GetConsoleMode**](getconsolemode.md) function.</span></span>

## <a name="examples"></a><span data-ttu-id="960b2-120">Exemples</span><span class="sxs-lookup"><span data-stu-id="960b2-120">Examples</span></span>

<span data-ttu-id="960b2-121">Pour obtenir un exemple, consultez [Lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="960b2-121">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="960b2-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="960b2-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="960b2-123">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="960b2-123">Minimum supported client</span></span> | <span data-ttu-id="960b2-124">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="960b2-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="960b2-125">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="960b2-125">Minimum supported server</span></span> | <span data-ttu-id="960b2-126">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="960b2-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="960b2-127">En-tête</span><span class="sxs-lookup"><span data-stu-id="960b2-127">Header</span></span> | <span data-ttu-id="960b2-128">ConsoleApi.h (via WinCon.h, inclure Windows.h)</span><span class="sxs-lookup"><span data-stu-id="960b2-128">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="960b2-129">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="960b2-129">Library</span></span> | <span data-ttu-id="960b2-130">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="960b2-130">Kernel32.lib</span></span> |
| <span data-ttu-id="960b2-131">DLL</span><span class="sxs-lookup"><span data-stu-id="960b2-131">DLL</span></span> | <span data-ttu-id="960b2-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="960b2-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="960b2-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="960b2-133">See also</span></span>

[<span data-ttu-id="960b2-134">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="960b2-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="960b2-135">Modes de la console</span><span class="sxs-lookup"><span data-stu-id="960b2-135">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="960b2-136">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="960b2-136">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="960b2-137">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="960b2-137">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="960b2-138">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="960b2-138">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="960b2-139">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="960b2-139">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="960b2-140">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="960b2-140">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="960b2-141">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="960b2-141">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="960b2-142">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="960b2-142">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
