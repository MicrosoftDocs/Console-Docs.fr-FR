---
title: GetConsoleMode fonction)
description: Récupère le mode de saisie actuel de la mémoire tampon d’entrée d’une console ou le mode de sortie actuel d’une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/GetConsoleMode
- wincon/GetConsoleMode
- GetConsoleMode
MS-HAID:
- '\_win32\_getconsolemode'
- base.getconsolemode
- consoles.getconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 49adf618-196d-4490-93ca-cd177807f58e
topic_type:
- apiref
api_name:
- GetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 54667d92509687111cb562f517d488c8adbc2181
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038870"
---
# <a name="getconsolemode-function"></a><span data-ttu-id="ca29b-104">GetConsoleMode fonction)</span><span class="sxs-lookup"><span data-stu-id="ca29b-104">GetConsoleMode function</span></span>

<span data-ttu-id="ca29b-105">Récupère le mode de saisie actuel de la mémoire tampon d’entrée d’une console ou le mode de sortie actuel d’une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="ca29b-105">Retrieves the current input mode of a console's input buffer or the current output mode of a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="ca29b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca29b-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleMode(
  _In_  HANDLE  hConsoleHandle,
  _Out_ LPDWORD lpMode
);
```

## <a name="parameters"></a><span data-ttu-id="ca29b-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca29b-107">Parameters</span></span>

<span data-ttu-id="ca29b-108">*hConsoleHandle* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="ca29b-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="ca29b-109">Handle vers la mémoire tampon d’entrée de la console ou la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="ca29b-109">A handle to the console input buffer or the console screen buffer.</span></span> <span data-ttu-id="ca29b-110">Le handle doit avoir le droit d’accès **\_ en lecture générique** .</span><span class="sxs-lookup"><span data-stu-id="ca29b-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="ca29b-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="ca29b-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="ca29b-112">*lpMode* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="ca29b-112">*lpMode* \[out\]</span></span>  
<span data-ttu-id="ca29b-113">Pointeur vers une variable qui reçoit le mode actuel de la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ca29b-113">A pointer to a variable that receives the current mode of the specified buffer.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a><span data-ttu-id="ca29b-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="ca29b-114">Return value</span></span>

<span data-ttu-id="ca29b-115">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="ca29b-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ca29b-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="ca29b-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ca29b-117">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="ca29b-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="ca29b-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="ca29b-118">Remarks</span></span>

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

<span data-ttu-id="ca29b-119">Pour modifier les modes d’e/s d’une console, appelez la fonction [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="ca29b-119">To change a console's I/O modes, call [**SetConsoleMode**](setconsolemode.md) function.</span></span>

## <a name="examples"></a><span data-ttu-id="ca29b-120">Exemples</span><span class="sxs-lookup"><span data-stu-id="ca29b-120">Examples</span></span>

<span data-ttu-id="ca29b-121">Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="ca29b-121">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="ca29b-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ca29b-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ca29b-123">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ca29b-123">Minimum supported client</span></span> | <span data-ttu-id="ca29b-124">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ca29b-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="ca29b-125">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ca29b-125">Minimum supported server</span></span> | <span data-ttu-id="ca29b-126">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ca29b-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="ca29b-127">En-tête</span><span class="sxs-lookup"><span data-stu-id="ca29b-127">Header</span></span> | <span data-ttu-id="ca29b-128">ConsoleApi. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ca29b-128">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ca29b-129">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="ca29b-129">Library</span></span> | <span data-ttu-id="ca29b-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ca29b-130">Kernel32.lib</span></span> |
| <span data-ttu-id="ca29b-131">DLL</span><span class="sxs-lookup"><span data-stu-id="ca29b-131">DLL</span></span> | <span data-ttu-id="ca29b-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ca29b-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="ca29b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca29b-133">See also</span></span>

[<span data-ttu-id="ca29b-134">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="ca29b-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ca29b-135">Modes de la console</span><span class="sxs-lookup"><span data-stu-id="ca29b-135">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="ca29b-136">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="ca29b-136">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="ca29b-137">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="ca29b-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="ca29b-138">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="ca29b-138">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="ca29b-139">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="ca29b-139">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="ca29b-140">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="ca29b-140">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="ca29b-141">**Appel**</span><span class="sxs-lookup"><span data-stu-id="ca29b-141">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
