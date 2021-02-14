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
ms.openlocfilehash: 317acd84289e5138e1a947251e745077ba581083
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358509"
---
# <a name="setstdhandle-function"></a><span data-ttu-id="0708a-104">SetStdHandle fonction)</span><span class="sxs-lookup"><span data-stu-id="0708a-104">SetStdHandle function</span></span>

<span data-ttu-id="0708a-105">Définit le descripteur pour l’appareil standard spécifié (entrée standard, sortie standard ou erreur standard).</span><span class="sxs-lookup"><span data-stu-id="0708a-105">Sets the handle for the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="0708a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0708a-106">Syntax</span></span>

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

## <a name="parameters"></a><span data-ttu-id="0708a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0708a-107">Parameters</span></span>

<span data-ttu-id="0708a-108">*nStdHandle* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="0708a-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="0708a-109">Appareil standard pour lequel le descripteur doit être défini.</span><span class="sxs-lookup"><span data-stu-id="0708a-109">The standard device for which the handle is to be set.</span></span> <span data-ttu-id="0708a-110">Ce paramètre peut prendre les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="0708a-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="0708a-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="0708a-111">Value</span></span> | <span data-ttu-id="0708a-112">Signification</span><span class="sxs-lookup"><span data-stu-id="0708a-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="0708a-113">**STD_INPUT_HANDLE** (DWORD) -10</span><span class="sxs-lookup"><span data-stu-id="0708a-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="0708a-114">Périphérique d’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="0708a-114">The standard input device.</span></span> <span data-ttu-id="0708a-115">À la base, il s’agit de la mémoire tampon d’entrée de la console, `CONIN$`.</span><span class="sxs-lookup"><span data-stu-id="0708a-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="0708a-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span><span class="sxs-lookup"><span data-stu-id="0708a-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="0708a-117">Périphérique de sortie standard.</span><span class="sxs-lookup"><span data-stu-id="0708a-117">The standard output device.</span></span> <span data-ttu-id="0708a-118">À la base, il s’agit de la mémoire tampon d’écran de la console active, `CONOUT$`.</span><span class="sxs-lookup"><span data-stu-id="0708a-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="0708a-119">**STD_ERROR_HANDLE** (DWORD) -12</span><span class="sxs-lookup"><span data-stu-id="0708a-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="0708a-120">Périphérique d’erreur standard.</span><span class="sxs-lookup"><span data-stu-id="0708a-120">The standard error device.</span></span> <span data-ttu-id="0708a-121">À la base, il s’agit de la mémoire tampon d’écran de la console active, `CONOUT$`.</span><span class="sxs-lookup"><span data-stu-id="0708a-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

<span data-ttu-id="0708a-122">*hHandle* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="0708a-122">*hHandle* \[in\]</span></span>  
<span data-ttu-id="0708a-123">Handle pour l’appareil standard.</span><span class="sxs-lookup"><span data-stu-id="0708a-123">The handle for the standard device.</span></span>

## <a name="return-value"></a><span data-ttu-id="0708a-124">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="0708a-124">Return value</span></span>

<span data-ttu-id="0708a-125">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="0708a-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="0708a-126">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="0708a-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0708a-127">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="0708a-127">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="0708a-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="0708a-128">Remarks</span></span>

<span data-ttu-id="0708a-129">Les handles standard d’un processus peuvent avoir été redirigés par un appel à **SetStdHandle**, auquel cas [**GetStdHandle**](getstdhandle.md) retourne le handle Redirigé.</span><span class="sxs-lookup"><span data-stu-id="0708a-129">The standard handles of a process may have been redirected by a call to **SetStdHandle**, in which case [**GetStdHandle**](getstdhandle.md) will return the redirected handle.</span></span> <span data-ttu-id="0708a-130">Si les handles standard ont été redirigés, vous pouvez spécifier la valeur CONIN $ dans un appel à la fonction [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) pour obtenir un handle vers la mémoire tampon d’entrée d’une console.</span><span class="sxs-lookup"><span data-stu-id="0708a-130">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="0708a-131">De même, vous pouvez spécifier la valeur CONOUT $ pour obtenir un descripteur de la mémoire tampon d’écran active de la console.</span><span class="sxs-lookup"><span data-stu-id="0708a-131">Similarly, you can specify the CONOUT$ value to get a handle to the console's active screen buffer.</span></span>

## <a name="examples"></a><span data-ttu-id="0708a-132">Exemples</span><span class="sxs-lookup"><span data-stu-id="0708a-132">Examples</span></span>

<span data-ttu-id="0708a-133">Pour obtenir un exemple, consultez [création d’un processus enfant avec une entrée et une sortie redirigées](/windows/win32/procthread/creating-a-child-process-with-redirected-input-and-output).</span><span class="sxs-lookup"><span data-stu-id="0708a-133">For an example, see [Creating a Child Process with Redirected Input and Output](/windows/win32/procthread/creating-a-child-process-with-redirected-input-and-output).</span></span>

## <a name="requirements"></a><span data-ttu-id="0708a-134">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0708a-134">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="0708a-135">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="0708a-135">Minimum supported client</span></span> | <span data-ttu-id="0708a-136">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="0708a-136">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="0708a-137">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="0708a-137">Minimum supported server</span></span> | <span data-ttu-id="0708a-138">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="0708a-138">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="0708a-139">En-tête</span><span class="sxs-lookup"><span data-stu-id="0708a-139">Header</span></span> | <span data-ttu-id="0708a-140">ProcessEnv.h (via Winbase.h, inclure Windows.h)</span><span class="sxs-lookup"><span data-stu-id="0708a-140">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="0708a-141">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="0708a-141">Library</span></span> | <span data-ttu-id="0708a-142">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="0708a-142">Kernel32.lib</span></span> |
| <span data-ttu-id="0708a-143">DLL</span><span class="sxs-lookup"><span data-stu-id="0708a-143">DLL</span></span> | <span data-ttu-id="0708a-144">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0708a-144">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="0708a-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0708a-145">See also</span></span>

[<span data-ttu-id="0708a-146">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="0708a-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0708a-147">Handles de console</span><span class="sxs-lookup"><span data-stu-id="0708a-147">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="0708a-148">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="0708a-148">**CreateFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-createfilea)

[<span data-ttu-id="0708a-149">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="0708a-149">**GetStdHandle**</span></span>](getstdhandle.md)