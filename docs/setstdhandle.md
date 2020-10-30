---
title: SetStdHandle fonction)
description: Définit le descripteur pour l’appareil standard spécifié (entrée standard, sortie standard ou erreur standard).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 36531872df90239e2b909c80fb75ad3011280c78
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039297"
---
# <a name="setstdhandle-function"></a><span data-ttu-id="bf4dc-104">SetStdHandle fonction)</span><span class="sxs-lookup"><span data-stu-id="bf4dc-104">SetStdHandle function</span></span>

<span data-ttu-id="bf4dc-105">Définit le descripteur pour l’appareil standard spécifié (entrée standard, sortie standard ou erreur standard).</span><span class="sxs-lookup"><span data-stu-id="bf4dc-105">Sets the handle for the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="bf4dc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf4dc-106">Syntax</span></span>

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

## <a name="parameters"></a><span data-ttu-id="bf4dc-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bf4dc-107">Parameters</span></span>

<span data-ttu-id="bf4dc-108">*nStdHandle* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="bf4dc-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="bf4dc-109">Appareil standard pour lequel le descripteur doit être défini.</span><span class="sxs-lookup"><span data-stu-id="bf4dc-109">The standard device for which the handle is to be set.</span></span> <span data-ttu-id="bf4dc-110">Ce paramètre peut prendre l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="bf4dc-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="bf4dc-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="bf4dc-111">Value</span></span> | <span data-ttu-id="bf4dc-112">Signification</span><span class="sxs-lookup"><span data-stu-id="bf4dc-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="bf4dc-113">**STD_INPUT_HANDLE** (DWORD)-10</span><span class="sxs-lookup"><span data-stu-id="bf4dc-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="bf4dc-114">Périphérique d’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="bf4dc-114">The standard input device.</span></span> <span data-ttu-id="bf4dc-115">Initialement, il s’agit de la mémoire tampon d’entrée de la console, `CONIN$` .</span><span class="sxs-lookup"><span data-stu-id="bf4dc-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="bf4dc-116">**STD_OUTPUT_HANDLE** (DWORD)-11</span><span class="sxs-lookup"><span data-stu-id="bf4dc-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="bf4dc-117">Périphérique de sortie standard.</span><span class="sxs-lookup"><span data-stu-id="bf4dc-117">The standard output device.</span></span> <span data-ttu-id="bf4dc-118">Initialement, il s’agit de la mémoire tampon d’écran active de la console, `CONOUT$` .</span><span class="sxs-lookup"><span data-stu-id="bf4dc-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="bf4dc-119">**STD_ERROR_HANDLE** (DWORD)-12</span><span class="sxs-lookup"><span data-stu-id="bf4dc-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="bf4dc-120">Périphérique d’erreur standard.</span><span class="sxs-lookup"><span data-stu-id="bf4dc-120">The standard error device.</span></span> <span data-ttu-id="bf4dc-121">Initialement, il s’agit de la mémoire tampon d’écran active de la console, `CONOUT$` .</span><span class="sxs-lookup"><span data-stu-id="bf4dc-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

<span data-ttu-id="bf4dc-122">*hHandle* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="bf4dc-122">*hHandle* \[in\]</span></span>  
<span data-ttu-id="bf4dc-123">Handle pour l’appareil standard.</span><span class="sxs-lookup"><span data-stu-id="bf4dc-123">The handle for the standard device.</span></span>

## <a name="return-value"></a><span data-ttu-id="bf4dc-124">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="bf4dc-124">Return value</span></span>

<span data-ttu-id="bf4dc-125">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="bf4dc-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="bf4dc-126">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="bf4dc-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="bf4dc-127">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="bf4dc-127">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="bf4dc-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="bf4dc-128">Remarks</span></span>

<span data-ttu-id="bf4dc-129">Les handles standard d’un processus peuvent avoir été redirigés par un appel à **SetStdHandle** , auquel cas [**GetStdHandle**](getstdhandle.md) retourne le handle Redirigé.</span><span class="sxs-lookup"><span data-stu-id="bf4dc-129">The standard handles of a process may have been redirected by a call to **SetStdHandle** , in which case [**GetStdHandle**](getstdhandle.md) will return the redirected handle.</span></span> <span data-ttu-id="bf4dc-130">Si les handles standard ont été redirigés, vous pouvez spécifier la valeur CONIN $ dans un appel à la fonction [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) pour obtenir un handle vers la mémoire tampon d’entrée d’une console.</span><span class="sxs-lookup"><span data-stu-id="bf4dc-130">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="bf4dc-131">De même, vous pouvez spécifier la valeur CONOUT $ pour obtenir un descripteur de la mémoire tampon d’écran active de la console.</span><span class="sxs-lookup"><span data-stu-id="bf4dc-131">Similarly, you can specify the CONOUT$ value to get a handle to the console's active screen buffer.</span></span>

## <a name="examples"></a><span data-ttu-id="bf4dc-132">Exemples</span><span class="sxs-lookup"><span data-stu-id="bf4dc-132">Examples</span></span>

<span data-ttu-id="bf4dc-133">Pour obtenir un exemple, consultez [création d’un processus enfant avec une entrée et une sortie redirigées](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span><span class="sxs-lookup"><span data-stu-id="bf4dc-133">For an example, see [Creating a Child Process with Redirected Input and Output](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span></span>

## <a name="requirements"></a><span data-ttu-id="bf4dc-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bf4dc-134">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="bf4dc-135">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="bf4dc-135">Minimum supported client</span></span> | <span data-ttu-id="bf4dc-136">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="bf4dc-136">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="bf4dc-137">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="bf4dc-137">Minimum supported server</span></span> | <span data-ttu-id="bf4dc-138">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="bf4dc-138">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="bf4dc-139">En-tête</span><span class="sxs-lookup"><span data-stu-id="bf4dc-139">Header</span></span> | <span data-ttu-id="bf4dc-140">ProcessEnv. h (via Winbase. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="bf4dc-140">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="bf4dc-141">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="bf4dc-141">Library</span></span> | <span data-ttu-id="bf4dc-142">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="bf4dc-142">Kernel32.lib</span></span> |
| <span data-ttu-id="bf4dc-143">DLL</span><span class="sxs-lookup"><span data-stu-id="bf4dc-143">DLL</span></span> | <span data-ttu-id="bf4dc-144">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="bf4dc-144">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="bf4dc-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf4dc-145">See also</span></span>

[<span data-ttu-id="bf4dc-146">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="bf4dc-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="bf4dc-147">Handles de console</span><span class="sxs-lookup"><span data-stu-id="bf4dc-147">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="bf4dc-148">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="bf4dc-148">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="bf4dc-149">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="bf4dc-149">**GetStdHandle**</span></span>](getstdhandle.md)
