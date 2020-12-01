---
title: SetConsoleMode fonction)
description: Définit le mode d’entrée de la mémoire tampon d’entrée d’une console ou le mode de sortie d’une mémoire tampon d’écran de la console.
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
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420298"
---
# <a name="setconsolemode-function"></a><span data-ttu-id="550d4-104">SetConsoleMode fonction)</span><span class="sxs-lookup"><span data-stu-id="550d4-104">SetConsoleMode function</span></span>

<span data-ttu-id="550d4-105">Définit le mode d’entrée de la mémoire tampon d’entrée d’une console ou le mode de sortie d’une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="550d4-105">Sets the input mode of a console's input buffer or the output mode of a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="550d4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="550d4-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

## <a name="parameters"></a><span data-ttu-id="550d4-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="550d4-107">Parameters</span></span>

<span data-ttu-id="550d4-108">*hConsoleHandle* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="550d4-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="550d4-109">Handle vers la mémoire tampon d’entrée de la console ou une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="550d4-109">A handle to the console input buffer or a console screen buffer.</span></span> <span data-ttu-id="550d4-110">Le handle doit avoir le droit d’accès **\_ en lecture générique** .</span><span class="sxs-lookup"><span data-stu-id="550d4-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="550d4-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="550d4-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="550d4-112">*dwMode* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="550d4-112">*dwMode* \[in\]</span></span>  
<span data-ttu-id="550d4-113">Mode d’entrée ou de sortie à définir.</span><span class="sxs-lookup"><span data-stu-id="550d4-113">The input or output mode to be set.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a><span data-ttu-id="550d4-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="550d4-114">Return value</span></span>

<span data-ttu-id="550d4-115">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="550d4-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="550d4-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="550d4-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="550d4-117">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="550d4-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="550d4-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="550d4-118">Remarks</span></span>

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

<span data-ttu-id="550d4-119">Pour déterminer le mode actuel d’une mémoire tampon d’entrée de console ou d’une mémoire tampon d’écran, utilisez la fonction [**GetConsoleMode**](getconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="550d4-119">To determine the current mode of a console input buffer or a screen buffer, use the [**GetConsoleMode**](getconsolemode.md) function.</span></span>

## <a name="examples"></a><span data-ttu-id="550d4-120">Exemples</span><span class="sxs-lookup"><span data-stu-id="550d4-120">Examples</span></span>

<span data-ttu-id="550d4-121">Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="550d4-121">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="550d4-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="550d4-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="550d4-123">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="550d4-123">Minimum supported client</span></span> | <span data-ttu-id="550d4-124">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="550d4-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="550d4-125">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="550d4-125">Minimum supported server</span></span> | <span data-ttu-id="550d4-126">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="550d4-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="550d4-127">En-tête</span><span class="sxs-lookup"><span data-stu-id="550d4-127">Header</span></span> | <span data-ttu-id="550d4-128">ConsoleApi. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="550d4-128">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="550d4-129">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="550d4-129">Library</span></span> | <span data-ttu-id="550d4-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="550d4-130">Kernel32.lib</span></span> |
| <span data-ttu-id="550d4-131">DLL</span><span class="sxs-lookup"><span data-stu-id="550d4-131">DLL</span></span> | <span data-ttu-id="550d4-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="550d4-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="550d4-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="550d4-133">See also</span></span>

[<span data-ttu-id="550d4-134">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="550d4-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="550d4-135">Modes de la console</span><span class="sxs-lookup"><span data-stu-id="550d4-135">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="550d4-136">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="550d4-136">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="550d4-137">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="550d4-137">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="550d4-138">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="550d4-138">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="550d4-139">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="550d4-139">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="550d4-140">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="550d4-140">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="550d4-141">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="550d4-141">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="550d4-142">**Appel**</span><span class="sxs-lookup"><span data-stu-id="550d4-142">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
