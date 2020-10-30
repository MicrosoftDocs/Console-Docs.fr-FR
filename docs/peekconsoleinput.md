---
title: PeekConsoleInput fonction)
description: Lit les données de la mémoire tampon d’entrée de la console spécifiée sans les supprimer de la mémoire tampon.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/PeekConsoleInput
- wincon/PeekConsoleInput
- PeekConsoleInput
- consoleapi/PeekConsoleInputA
- wincon/PeekConsoleInputA
- PeekConsoleInputA
- consoleapi/PeekConsoleInputW
- wincon/PeekConsoleInputW
- PeekConsoleInputW
MS-HAID:
- '\_win32\_peekconsoleinput'
- base.peekconsoleinput
- consoles.peekconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9982dc20-43bd-4ee3-a68d-157c9134daca
topic_type:
- apiref
api_name:
- PeekConsoleInput
- PeekConsoleInputA
- PeekConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 9052f15b36e16dd2ddf7fe46d3d201aa21403f91
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039497"
---
# <a name="peekconsoleinput-function"></a><span data-ttu-id="17786-104">PeekConsoleInput fonction)</span><span class="sxs-lookup"><span data-stu-id="17786-104">PeekConsoleInput function</span></span>

<span data-ttu-id="17786-105">Lit les données de la mémoire tampon d’entrée de la console spécifiée sans les supprimer de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="17786-105">Reads data from the specified console input buffer without removing it from the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="17786-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17786-106">Syntax</span></span>

```C
BOOL WINAPI PeekConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

## <a name="parameters"></a><span data-ttu-id="17786-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="17786-107">Parameters</span></span>

<span data-ttu-id="17786-108">*hConsoleInput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="17786-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="17786-109">Handle vers la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="17786-109">A handle to the console input buffer.</span></span> <span data-ttu-id="17786-110">Le handle doit avoir le droit d’accès **\_ en lecture générique** .</span><span class="sxs-lookup"><span data-stu-id="17786-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="17786-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="17786-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="17786-112">*lpBuffer* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="17786-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="17786-113">Pointeur vers un tableau de structures [**d' \_ enregistrements d’entrée**](input-record-str.md) qui reçoit les données de la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="17786-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="17786-114">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="17786-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="17786-115">Taille du tableau vers lequel pointe le paramètre *lpBuffer* , dans les éléments de tableau.</span><span class="sxs-lookup"><span data-stu-id="17786-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="17786-116">*lpNumberOfEventsRead* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="17786-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="17786-117">Pointeur vers une variable qui reçoit le nombre d’enregistrements d’entrée lus.</span><span class="sxs-lookup"><span data-stu-id="17786-117">A pointer to a variable that receives the number of input records read.</span></span>

## <a name="return-value"></a><span data-ttu-id="17786-118">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="17786-118">Return value</span></span>

<span data-ttu-id="17786-119">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="17786-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="17786-120">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="17786-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="17786-121">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="17786-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="17786-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="17786-122">Remarks</span></span>

<span data-ttu-id="17786-123">Si le nombre d’enregistrements demandés dépasse le nombre d’enregistrements disponibles dans la mémoire tampon, le nombre disponible est lu.</span><span class="sxs-lookup"><span data-stu-id="17786-123">If the number of records requested exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="17786-124">Si aucune donnée n’est disponible, la fonction est retournée immédiatement.</span><span class="sxs-lookup"><span data-stu-id="17786-124">If no data is available, the function returns immediately.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## <a name="requirements"></a><span data-ttu-id="17786-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="17786-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="17786-126">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="17786-126">Minimum supported client</span></span> | <span data-ttu-id="17786-127">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="17786-127">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="17786-128">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="17786-128">Minimum supported server</span></span> | <span data-ttu-id="17786-129">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="17786-129">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="17786-130">En-tête</span><span class="sxs-lookup"><span data-stu-id="17786-130">Header</span></span> | <span data-ttu-id="17786-131">ConsoleApi. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="17786-131">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="17786-132">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="17786-132">Library</span></span> | <span data-ttu-id="17786-133">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="17786-133">Kernel32.lib</span></span> |
| <span data-ttu-id="17786-134">DLL</span><span class="sxs-lookup"><span data-stu-id="17786-134">DLL</span></span> | <span data-ttu-id="17786-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="17786-135">Kernel32.dll</span></span> |
| <span data-ttu-id="17786-136">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="17786-136">Unicode and ANSI names</span></span> | <span data-ttu-id="17786-137">**PeekConsoleInputW** (Unicode) et **PeekConsoleInputA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="17786-137">**PeekConsoleInputW** (Unicode) and **PeekConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="17786-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17786-138">See also</span></span>

[<span data-ttu-id="17786-139">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="17786-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="17786-140">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="17786-140">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="17786-141">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="17786-141">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="17786-142">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="17786-142">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="17786-143">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="17786-143">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

[<span data-ttu-id="17786-144">**enregistrement d’entrée \_**</span><span class="sxs-lookup"><span data-stu-id="17786-144">**INPUT\_RECORD**</span></span>](input-record-str.md)
