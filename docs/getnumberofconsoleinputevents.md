---
title: GetNumberOfConsoleInputEvents fonction)
description: Récupère le nombre d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/GetNumberOfConsoleInputEvents
- wincon/GetNumberOfConsoleInputEvents
- GetNumberOfConsoleInputEvents
MS-HAID:
- '\_win32\_getnumberofconsoleinputevents'
- base.getnumberofconsoleinputevents
- consoles.getnumberofconsoleinputevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1083b4f1-8fa6-4054-a516-3b447c3b0130
topic_type:
- apiref
api_name:
- GetNumberOfConsoleInputEvents
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: b4cad78d35114c509f4e810a858e6ae3b8bfb644
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038687"
---
# <a name="getnumberofconsoleinputevents-function"></a><span data-ttu-id="56cb6-104">GetNumberOfConsoleInputEvents fonction)</span><span class="sxs-lookup"><span data-stu-id="56cb6-104">GetNumberOfConsoleInputEvents function</span></span>

<span data-ttu-id="56cb6-105">Récupère le nombre d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="56cb6-105">Retrieves the number of unread input records in the console's input buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="56cb6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56cb6-106">Syntax</span></span>

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

## <a name="parameters"></a><span data-ttu-id="56cb6-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="56cb6-107">Parameters</span></span>

<span data-ttu-id="56cb6-108">*hConsoleInput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="56cb6-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="56cb6-109">Handle vers la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="56cb6-109">A handle to the console input buffer.</span></span> <span data-ttu-id="56cb6-110">Le handle doit avoir le droit d’accès **\_ en lecture générique** .</span><span class="sxs-lookup"><span data-stu-id="56cb6-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="56cb6-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="56cb6-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="56cb6-112">*lpcNumberOfEvents* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="56cb6-112">*lpcNumberOfEvents* \[out\]</span></span>  
<span data-ttu-id="56cb6-113">Pointeur vers une variable qui reçoit le nombre d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="56cb6-113">A pointer to a variable that receives the number of unread input records in the console's input buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="56cb6-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="56cb6-114">Return value</span></span>

<span data-ttu-id="56cb6-115">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="56cb6-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="56cb6-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="56cb6-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="56cb6-117">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="56cb6-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="56cb6-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="56cb6-118">Remarks</span></span>

<span data-ttu-id="56cb6-119">La fonction **GetNumberOfConsoleInputEvents** signale le nombre total d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée, y compris les enregistrements d’entrée de clavier, de souris et de redimensionnement de fenêtre.</span><span class="sxs-lookup"><span data-stu-id="56cb6-119">The **GetNumberOfConsoleInputEvents** function reports the total number of unread input records in the input buffer, including keyboard, mouse, and window-resizing input records.</span></span> <span data-ttu-id="56cb6-120">Les processus utilisant la fonction [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ou [**ReadConsole**](readconsole.md) peuvent uniquement lire les entrées au clavier.</span><span class="sxs-lookup"><span data-stu-id="56cb6-120">Processes using the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function can only read keyboard input.</span></span> <span data-ttu-id="56cb6-121">Les processus qui utilisent la fonction [**ReadConsoleInput**](readconsoleinput.md) peuvent lire tous les types d’enregistrements d’entrée.</span><span class="sxs-lookup"><span data-stu-id="56cb6-121">Processes using the [**ReadConsoleInput**](readconsoleinput.md) function can read all types of input records.</span></span>

<span data-ttu-id="56cb6-122">Un processus peut spécifier un handle de mémoire tampon d’entrée de la console dans l’une des [fonctions Wait](https://msdn.microsoft.com/library/windows/desktop/ms687069) pour déterminer le moment où une entrée de console n’est pas lue.</span><span class="sxs-lookup"><span data-stu-id="56cb6-122">A process can specify a console input buffer handle in one of the [wait functions](https://msdn.microsoft.com/library/windows/desktop/ms687069) to determine when there is unread console input.</span></span> <span data-ttu-id="56cb6-123">Lorsque la mémoire tampon d’entrée n’est pas vide, l’état d’un handle de mémoire tampon d’entrée de la console est signalé.</span><span class="sxs-lookup"><span data-stu-id="56cb6-123">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="56cb6-124">Pour lire les enregistrements d’entrée d’une mémoire tampon d’entrée de la console sans affecter le nombre d’enregistrements non lus, utilisez la fonction [**PeekConsoleInput**](peekconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="56cb6-124">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="56cb6-125">Pour ignorer tous les enregistrements non lus dans le tampon d’entrée d’une console, utilisez la fonction [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="56cb6-125">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="56cb6-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="56cb6-126">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="56cb6-127">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="56cb6-127">Minimum supported client</span></span> | <span data-ttu-id="56cb6-128">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="56cb6-128">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="56cb6-129">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="56cb6-129">Minimum supported server</span></span> | <span data-ttu-id="56cb6-130">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="56cb6-130">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="56cb6-131">En-tête</span><span class="sxs-lookup"><span data-stu-id="56cb6-131">Header</span></span> | <span data-ttu-id="56cb6-132">ConsoleApi. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="56cb6-132">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="56cb6-133">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="56cb6-133">Library</span></span> | <span data-ttu-id="56cb6-134">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="56cb6-134">Kernel32.lib</span></span> |
| <span data-ttu-id="56cb6-135">DLL</span><span class="sxs-lookup"><span data-stu-id="56cb6-135">DLL</span></span> | <span data-ttu-id="56cb6-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="56cb6-136">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="56cb6-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56cb6-137">See also</span></span>

[<span data-ttu-id="56cb6-138">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="56cb6-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="56cb6-139">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="56cb6-139">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="56cb6-140">Fonctions d’entrée de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="56cb6-140">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="56cb6-141">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="56cb6-141">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="56cb6-142">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="56cb6-142">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="56cb6-143">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="56cb6-143">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="56cb6-144">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="56cb6-144">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)
