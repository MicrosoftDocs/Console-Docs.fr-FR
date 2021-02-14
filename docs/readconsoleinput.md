---
title: ReadConsoleInput fonction)
description: Lit les données à partir d’une mémoire tampon d’entrée de la console et les supprime de la mémoire tampon.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/ReadConsoleInput
- wincon/ReadConsoleInput
- ReadConsoleInput
- consoleapi/ReadConsoleInputA
- wincon/ReadConsoleInputA
- ReadConsoleInputA
- consoleapi/ReadConsoleInputW
- wincon/ReadConsoleInputW
- ReadConsoleInputW
MS-HAID:
- '\_win32\_readconsoleinput'
- base.readconsoleinput
- consoles.readconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5a9f7b18-cdea-4041-a377-5532d30e0105
topic_type:
- apiref
api_name:
- ReadConsoleInput
- ReadConsoleInputA
- ReadConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 06e784ebaebde2ed68ed17f75f4e54932aa463f5
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358719"
---
# <a name="readconsoleinput-function"></a><span data-ttu-id="5caa6-104">ReadConsoleInput fonction)</span><span class="sxs-lookup"><span data-stu-id="5caa6-104">ReadConsoleInput function</span></span>

<span data-ttu-id="5caa6-105">Lit les données à partir d’une mémoire tampon d’entrée de la console et les supprime de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="5caa6-105">Reads data from a console input buffer and removes it from the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="5caa6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5caa6-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

## <a name="parameters"></a><span data-ttu-id="5caa6-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5caa6-107">Parameters</span></span>

<span data-ttu-id="5caa6-108">*hConsoleInput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="5caa6-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="5caa6-109">Handle vers la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="5caa6-109">A handle to the console input buffer.</span></span> <span data-ttu-id="5caa6-110">Le handle doit avoir le droit d’accès **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="5caa6-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="5caa6-111">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="5caa6-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="5caa6-112">*lpBuffer* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="5caa6-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="5caa6-113">Pointeur vers un tableau de structures [**d' \_ enregistrements d’entrée**](input-record-str.md) qui reçoit les données de la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5caa6-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="5caa6-114">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="5caa6-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="5caa6-115">Taille du tableau vers lequel pointe le paramètre *lpBuffer* , dans les éléments de tableau.</span><span class="sxs-lookup"><span data-stu-id="5caa6-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="5caa6-116">*lpNumberOfEventsRead* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="5caa6-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="5caa6-117">Pointeur vers une variable qui reçoit le nombre d’enregistrements d’entrée lus.</span><span class="sxs-lookup"><span data-stu-id="5caa6-117">A pointer to a variable that receives the number of input records read.</span></span>

## <a name="return-value"></a><span data-ttu-id="5caa6-118">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="5caa6-118">Return value</span></span>

<span data-ttu-id="5caa6-119">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="5caa6-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="5caa6-120">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="5caa6-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="5caa6-121">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="5caa6-121">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="5caa6-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="5caa6-122">Remarks</span></span>

<span data-ttu-id="5caa6-123">Si le nombre d’enregistrements demandés dans le paramètre *nLength* dépasse le nombre d’enregistrements disponibles dans la mémoire tampon, le nombre disponible est Read.</span><span class="sxs-lookup"><span data-stu-id="5caa6-123">If the number of records requested in the *nLength* parameter exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="5caa6-124">La fonction ne retourne pas de données tant qu’au moins un enregistrement d’entrée n’a pas été lu.</span><span class="sxs-lookup"><span data-stu-id="5caa6-124">The function does not return until at least one input record has been read.</span></span>

<span data-ttu-id="5caa6-125">Un processus peut spécifier un handle de mémoire tampon d’entrée de la console dans l’une des [fonctions Wait](/windows/win32/sync/wait-functions) pour déterminer le moment où une entrée de console n’est pas lue.</span><span class="sxs-lookup"><span data-stu-id="5caa6-125">A process can specify a console input buffer handle in one of the [wait functions](/windows/win32/sync/wait-functions) to determine when there is unread console input.</span></span> <span data-ttu-id="5caa6-126">Lorsque la mémoire tampon d’entrée n’est pas vide, l’état d’un handle de mémoire tampon d’entrée de la console est signalé.</span><span class="sxs-lookup"><span data-stu-id="5caa6-126">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="5caa6-127">Pour déterminer le nombre d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée d’une console, utilisez la fonction [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) .</span><span class="sxs-lookup"><span data-stu-id="5caa6-127">To determine the number of unread input records in a console's input buffer, use the [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) function.</span></span> <span data-ttu-id="5caa6-128">Pour lire les enregistrements d’entrée d’une mémoire tampon d’entrée de la console sans affecter le nombre d’enregistrements non lus, utilisez la fonction [**PeekConsoleInput**](peekconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="5caa6-128">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="5caa6-129">Pour ignorer tous les enregistrements non lus dans le tampon d’entrée d’une console, utilisez la fonction [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="5caa6-129">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## <a name="examples"></a><span data-ttu-id="5caa6-130">Exemples</span><span class="sxs-lookup"><span data-stu-id="5caa6-130">Examples</span></span>

<span data-ttu-id="5caa6-131">Pour obtenir un exemple, consultez [Lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="5caa6-131">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="5caa6-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5caa6-132">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="5caa6-133">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="5caa6-133">Minimum supported client</span></span> | <span data-ttu-id="5caa6-134">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="5caa6-134">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="5caa6-135">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="5caa6-135">Minimum supported server</span></span> | <span data-ttu-id="5caa6-136">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="5caa6-136">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="5caa6-137">En-tête</span><span class="sxs-lookup"><span data-stu-id="5caa6-137">Header</span></span> | <span data-ttu-id="5caa6-138">ConsoleApi.h (via WinCon.h, inclure Windows.h)</span><span class="sxs-lookup"><span data-stu-id="5caa6-138">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="5caa6-139">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="5caa6-139">Library</span></span> | <span data-ttu-id="5caa6-140">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="5caa6-140">Kernel32.lib</span></span> |
| <span data-ttu-id="5caa6-141">DLL</span><span class="sxs-lookup"><span data-stu-id="5caa6-141">DLL</span></span> | <span data-ttu-id="5caa6-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="5caa6-142">Kernel32.dll</span></span> |
| <span data-ttu-id="5caa6-143">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="5caa6-143">Unicode and ANSI names</span></span> | <span data-ttu-id="5caa6-144">**ReadConsoleInputW** (Unicode) et **ReadConsoleInputA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="5caa6-144">**ReadConsoleInputW** (Unicode) and **ReadConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="5caa6-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5caa6-145">See also</span></span>

[<span data-ttu-id="5caa6-146">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="5caa6-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="5caa6-147">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="5caa6-147">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="5caa6-148">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="5caa6-148">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="5caa6-149">**enregistrement d’entrée \_**</span><span class="sxs-lookup"><span data-stu-id="5caa6-149">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="5caa6-150">Fonctions d’entrée de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="5caa6-150">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="5caa6-151">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="5caa6-151">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="5caa6-152">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="5caa6-152">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="5caa6-153">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="5caa6-153">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="5caa6-154">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="5caa6-154">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="5caa6-155">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="5caa6-155">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="5caa6-156">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="5caa6-156">**WriteConsoleInput**</span></span>](writeconsoleinput.md)