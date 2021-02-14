---
title: AttachConsole fonction)
description: Consultez les informations de référence sur la fonction AttachConsole, qui attache le processus appelant à la console du processus spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- base.attachconsole
- consoles.attachconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: a1be050dccc0c77b6ad448cc45e87906a115d82c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357839"
---
# <a name="attachconsole-function"></a><span data-ttu-id="b2d61-104">AttachConsole fonction)</span><span class="sxs-lookup"><span data-stu-id="b2d61-104">AttachConsole function</span></span>

<span data-ttu-id="b2d61-105">Joint le processus appelant à la console du processus spécifié en tant qu’application cliente.</span><span class="sxs-lookup"><span data-stu-id="b2d61-105">Attaches the calling process to the console of the specified process as a client application.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2d61-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2d61-106">Syntax</span></span>

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

## <a name="parameters"></a><span data-ttu-id="b2d61-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b2d61-107">Parameters</span></span>

<span data-ttu-id="b2d61-108">*dwProcessId* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="b2d61-108">*dwProcessId* \[in\]</span></span>  
<span data-ttu-id="b2d61-109">Identificateur du processus dont la console doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="b2d61-109">The identifier of the process whose console is to be used.</span></span> <span data-ttu-id="b2d61-110">Ce paramètre peut prendre les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="b2d61-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="b2d61-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="b2d61-111">Value</span></span> | <span data-ttu-id="b2d61-112">Signification</span><span class="sxs-lookup"><span data-stu-id="b2d61-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="b2d61-113">*pid*</span><span class="sxs-lookup"><span data-stu-id="b2d61-113">*pid*</span></span> | <span data-ttu-id="b2d61-114">Utilisez la console du processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="b2d61-114">Use the console of the specified process.</span></span> |
| <span data-ttu-id="b2d61-115">**Attacher \_ \_processus parent**`(DWORD)-1`</span><span class="sxs-lookup"><span data-stu-id="b2d61-115">**ATTACH\_PARENT\_PROCESS** `(DWORD)-1`</span></span> | <span data-ttu-id="b2d61-116">Utilisez la console du parent du processus en cours.</span><span class="sxs-lookup"><span data-stu-id="b2d61-116">Use the console of the parent of the current process.</span></span> |

## <a name="return-value"></a><span data-ttu-id="b2d61-117">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="b2d61-117">Return value</span></span>

<span data-ttu-id="b2d61-118">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="b2d61-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b2d61-119">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="b2d61-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b2d61-120">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="b2d61-120">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="b2d61-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="b2d61-121">Remarks</span></span>

<span data-ttu-id="b2d61-122">Un processus peut être attaché à au plus une console.</span><span class="sxs-lookup"><span data-stu-id="b2d61-122">A process can be attached to at most one console.</span></span> <span data-ttu-id="b2d61-123">Si le processus appelant est déjà attaché à une console, le code d’erreur retourné est **erreur \_ accès \_ refusé** ( `5` ).</span><span class="sxs-lookup"><span data-stu-id="b2d61-123">If the calling process is already attached to a console, the error code returned is **ERROR\_ACCESS\_DENIED** (`5`).</span></span> <span data-ttu-id="b2d61-124">Si le processus spécifié n’a pas de console, le code d’erreur retourné **est \_ erreur \_ handle non valide** ( `6` ).</span><span class="sxs-lookup"><span data-stu-id="b2d61-124">If the specified process does not have a console, the error code returned is **ERROR\_INVALID\_HANDLE** (`6`).</span></span> <span data-ttu-id="b2d61-125">Si le processus spécifié n’existe pas, le code d’erreur retourné est **erreur : \_ \_ paramètre non valide** ( `87` ).</span><span class="sxs-lookup"><span data-stu-id="b2d61-125">If the specified process does not exist, the error code returned is **ERROR\_INVALID\_PARAMETER** (`87`).</span></span>

<span data-ttu-id="b2d61-126">Un processus peut utiliser la fonction [**FreeConsole**](freeconsole.md) pour se détacher de sa console.</span><span class="sxs-lookup"><span data-stu-id="b2d61-126">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console.</span></span> <span data-ttu-id="b2d61-127">Si d’autres processus partagent la console, la console n’est pas détruite, mais le processus qui a appelé **FreeConsole** ne peut pas y faire référence.</span><span class="sxs-lookup"><span data-stu-id="b2d61-127">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="b2d61-128">Une console est fermée lorsque le dernier processus qui lui est associé se termine ou appelle **FreeConsole**.</span><span class="sxs-lookup"><span data-stu-id="b2d61-128">A console is closed when the last process attached to it terminates or calls **FreeConsole**.</span></span> <span data-ttu-id="b2d61-129">Une fois qu’un processus a appelé **FreeConsole**, il peut appeler la fonction [**AllocConsole**](allocconsole.md) pour créer une nouvelle console ou **AttachConsole** à attacher à une autre console.</span><span class="sxs-lookup"><span data-stu-id="b2d61-129">After a process calls **FreeConsole**, it can call the [**AllocConsole**](allocconsole.md) function to create a new console or **AttachConsole** to attach to another console.</span></span>

<span data-ttu-id="b2d61-130">Cette fonction est surtout utile pour les applications qui ont été liées avec [**/SUBSYSTEM : Windows**](/cpp/build/reference/subsystem-specify-subsystem), ce qui implique au système d’exploitation qu’une console n’est pas nécessaire avant d’entrer dans la méthode main du programme.</span><span class="sxs-lookup"><span data-stu-id="b2d61-130">This function is primarily useful to applications that were linked with [**/SUBSYSTEM:WINDOWS**](/cpp/build/reference/subsystem-specify-subsystem), which implies to the operating system that a console is not needed before entering the program's main method.</span></span> <span data-ttu-id="b2d61-131">Dans cette instance, les handles standard récupérés avec [**GetStdHandle**](getstdhandle.md) seront probablement non valides au démarrage tant que **AttachConsole** n’est pas appelé.</span><span class="sxs-lookup"><span data-stu-id="b2d61-131">In that instance, the standard handles retrieved with [**GetStdHandle**](getstdhandle.md) will likely be invalid on startup until **AttachConsole** is called.</span></span> <span data-ttu-id="b2d61-132">L’exception est si l’application est lancée avec l’héritage de handle par son processus parent.</span><span class="sxs-lookup"><span data-stu-id="b2d61-132">The exception to this is if the application is launched with handle inheritance by its parent process.</span></span>

<span data-ttu-id="b2d61-133">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme `0x0501` ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="b2d61-133">To compile an application that uses this function, define **\_WIN32\_WINNT** as `0x0501` or later.</span></span> <span data-ttu-id="b2d61-134">Pour plus d’informations, consultez [utilisation des en-têtes Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="b2d61-134">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

## <a name="requirements"></a><span data-ttu-id="b2d61-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b2d61-135">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b2d61-136">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="b2d61-136">Minimum supported client</span></span> | <span data-ttu-id="b2d61-137">Applications de \[ Bureau Windows XP uniquement\]</span><span class="sxs-lookup"><span data-stu-id="b2d61-137">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="b2d61-138">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="b2d61-138">Minimum supported server</span></span> | <span data-ttu-id="b2d61-139">Applications de bureau Windows Server 2003 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="b2d61-139">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="b2d61-140">En-tête</span><span class="sxs-lookup"><span data-stu-id="b2d61-140">Header</span></span> | <span data-ttu-id="b2d61-141">ConsoleApi.h (via WinCon.h, inclure Windows.h)</span><span class="sxs-lookup"><span data-stu-id="b2d61-141">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="b2d61-142">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="b2d61-142">Library</span></span> | <span data-ttu-id="b2d61-143">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="b2d61-143">Kernel32.lib</span></span> |
| <span data-ttu-id="b2d61-144">DLL</span><span class="sxs-lookup"><span data-stu-id="b2d61-144">DLL</span></span> | <span data-ttu-id="b2d61-145">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b2d61-145">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="b2d61-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2d61-146">See also</span></span>

[<span data-ttu-id="b2d61-147">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="b2d61-147">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b2d61-148">Consoles</span><span class="sxs-lookup"><span data-stu-id="b2d61-148">Consoles</span></span>](consoles.md)

[<span data-ttu-id="b2d61-149">**AllocConsole**</span><span class="sxs-lookup"><span data-stu-id="b2d61-149">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="b2d61-150">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="b2d61-150">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="b2d61-151">**GetConsoleProcessList**</span><span class="sxs-lookup"><span data-stu-id="b2d61-151">**GetConsoleProcessList**</span></span>](getconsoleprocesslist.md)