---
title: FlushConsoleInputBuffer fonction)
description: Vide la mémoire tampon d’entrée de la console. Tous les enregistrements d’entrée actuellement dans la mémoire tampon d’entrée sont ignorés.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/FlushConsoleInputBuffer
- wincon/FlushConsoleInputBuffer
- FlushConsoleInputBuffer
MS-HAID:
- '\_win32\_flushconsoleinputbuffer'
- base.flushconsoleinputbuffer
- consoles.flushconsoleinputbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6f7832d6-1fb2-4ca8-bd07-43123c990851
topic_type:
- apiref
api_name:
- FlushConsoleInputBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 543552e9252c1f28701a0b316b43597cdd9cd2c9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039047"
---
# <a name="flushconsoleinputbuffer-function"></a><span data-ttu-id="2ec99-105">FlushConsoleInputBuffer fonction)</span><span class="sxs-lookup"><span data-stu-id="2ec99-105">FlushConsoleInputBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="2ec99-106">Vide la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="2ec99-106">Flushes the console input buffer.</span></span> <span data-ttu-id="2ec99-107">Tous les enregistrements d’entrée actuellement dans la mémoire tampon d’entrée sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="2ec99-107">All input records currently in the input buffer are discarded.</span></span>

## <a name="syntax"></a><span data-ttu-id="2ec99-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ec99-108">Syntax</span></span>

```C
BOOL WINAPI FlushConsoleInputBuffer(
  _In_ HANDLE hConsoleInput
);
```

## <a name="parameters"></a><span data-ttu-id="2ec99-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ec99-109">Parameters</span></span>

<span data-ttu-id="2ec99-110">*hConsoleInput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="2ec99-110">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="2ec99-111">Handle vers la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="2ec99-111">A handle to the console input buffer.</span></span> <span data-ttu-id="2ec99-112">Le descripteur doit avoir le droit d’accès en **\_ écriture générique** .</span><span class="sxs-lookup"><span data-stu-id="2ec99-112">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="2ec99-113">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="2ec99-113">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

## <a name="return-value"></a><span data-ttu-id="2ec99-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="2ec99-114">Return value</span></span>

<span data-ttu-id="2ec99-115">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="2ec99-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="2ec99-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="2ec99-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="2ec99-117">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="2ec99-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="2ec99-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="2ec99-118">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="2ec99-119">Cette API n’est pas recommandée et n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="2ec99-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="2ec99-120">Toute tentative de vider la file d’attente d’entrée peut détruire l’état de la file d’attente de façon inattendue.</span><span class="sxs-lookup"><span data-stu-id="2ec99-120">Attempting to empty the input queue all at once can destroy state in the queue in an unexpected manner.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ec99-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2ec99-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="2ec99-122">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="2ec99-122">Minimum supported client</span></span> | <span data-ttu-id="2ec99-123">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="2ec99-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="2ec99-124">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="2ec99-124">Minimum supported server</span></span> | <span data-ttu-id="2ec99-125">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="2ec99-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="2ec99-126">En-tête</span><span class="sxs-lookup"><span data-stu-id="2ec99-126">Header</span></span> | <span data-ttu-id="2ec99-127">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2ec99-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="2ec99-128">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="2ec99-128">Library</span></span> | <span data-ttu-id="2ec99-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="2ec99-129">Kernel32.lib</span></span> |
| <span data-ttu-id="2ec99-130">DLL</span><span class="sxs-lookup"><span data-stu-id="2ec99-130">DLL</span></span> | <span data-ttu-id="2ec99-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2ec99-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="2ec99-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ec99-132">See also</span></span>

[<span data-ttu-id="2ec99-133">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="2ec99-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2ec99-134">Fonctions d’entrée de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="2ec99-134">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="2ec99-135">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="2ec99-135">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="2ec99-136">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="2ec99-136">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="2ec99-137">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="2ec99-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="2ec99-138">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="2ec99-138">**WriteConsoleInput**</span></span>](writeconsoleinput.md)
