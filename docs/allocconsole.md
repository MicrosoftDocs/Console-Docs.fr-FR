---
title: Fonction AllocConsole
description: Consultez les informations de référence sur la fonction AllocConsole, qui alloue une nouvelle console pour le processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/AllocConsole
- wincon/AllocConsole
- AllocConsole
MS-HAID:
- '\_win32\_allocconsole'
- base.allocconsole
- consoles.allocconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bdf3bf2f-8eb8-4ba6-bf3a-a67b29dffda2
topic_type:
- apiref
api_name:
- AllocConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 3b48570424a4c60a56094f5c41934f9946f67203
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357859"
---
# <a name="allocconsole-function"></a><span data-ttu-id="304be-104">Fonction AllocConsole</span><span class="sxs-lookup"><span data-stu-id="304be-104">AllocConsole function</span></span>

<span data-ttu-id="304be-105">Alloue une nouvelle console pour le processus appelant.</span><span class="sxs-lookup"><span data-stu-id="304be-105">Allocates a new console for the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="304be-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="304be-106">Syntax</span></span>

```C
BOOL WINAPI AllocConsole(void);
```

## <a name="parameters"></a><span data-ttu-id="304be-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="304be-107">Parameters</span></span>

<span data-ttu-id="304be-108">Cette fonction n’a pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="304be-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="304be-109">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="304be-109">Return value</span></span>

<span data-ttu-id="304be-110">Si la fonction aboutit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="304be-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="304be-111">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="304be-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="304be-112">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="304be-112">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="304be-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="304be-113">Remarks</span></span>

<span data-ttu-id="304be-114">Un processus peut être associé à une seule console. Par conséquent, la fonction **AllocConsole** échoue si le processus appelant dispose déjà d’une console.</span><span class="sxs-lookup"><span data-stu-id="304be-114">A process can be associated with only one console, so the **AllocConsole** function fails if the calling process already has a console.</span></span> <span data-ttu-id="304be-115">Un processus peut utiliser la fonction [**FreeConsole**](freeconsole.md) pour se détacher de sa console actuelle, puis appeler **AllocConsole** pour créer une nouvelle console ou [**AttachConsole**](attachconsole.md) pour effectuer l’attachement à une autre console.</span><span class="sxs-lookup"><span data-stu-id="304be-115">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its current console, then it can call **AllocConsole** to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<span data-ttu-id="304be-116">Si le processus appelant crée un processus enfant, l’enfant hérite de la nouvelle console.</span><span class="sxs-lookup"><span data-stu-id="304be-116">If the calling process creates a child process, the child inherits the new console.</span></span>

<span data-ttu-id="304be-117">**AllocConsole** Initialise une entrée standard, une sortie standard et des handles d’erreur standard pour la nouvelle console.</span><span class="sxs-lookup"><span data-stu-id="304be-117">**AllocConsole** initializes standard input, standard output, and standard error handles for the new console.</span></span> <span data-ttu-id="304be-118">Le handle d’entrée standard est un handle vers la mémoire tampon d’entrée de la console, et les handles de sortie standard et d’erreur standard sont des handles vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="304be-118">The standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles to the console's screen buffer.</span></span> <span data-ttu-id="304be-119">Pour récupérer ces handles, utilisez la fonction [**GetStdHandle**](getstdhandle.md).</span><span class="sxs-lookup"><span data-stu-id="304be-119">To retrieve these handles, use the [**GetStdHandle**](getstdhandle.md) function.</span></span>

<span data-ttu-id="304be-120">Cette fonction est principalement utilisée par une application d’interface graphique utilisateur (GUI) pour créer une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="304be-120">This function is primarily used by a graphical user interface (GUI) application to create a console window.</span></span> <span data-ttu-id="304be-121">Les applications GUI sont initialisées sans console.</span><span class="sxs-lookup"><span data-stu-id="304be-121">GUI applications are initialized without a console.</span></span> <span data-ttu-id="304be-122">Les applications console sont initialisées à l’aide d’une console, sauf si elles sont créées en tant que processus détachés (en appelant la fonction [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) avec l’indicateur **DETACHED\_PROCESS**).</span><span class="sxs-lookup"><span data-stu-id="304be-122">Console applications are initialized with a console, unless they are created as detached processes (by calling the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) function with the **DETACHED\_PROCESS** flag).</span></span>

## <a name="requirements"></a><span data-ttu-id="304be-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="304be-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="304be-124">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="304be-124">Minimum supported client</span></span> | <span data-ttu-id="304be-125">Windows 2000 Professionnel \[applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="304be-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="304be-126">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="304be-126">Minimum supported server</span></span> | <span data-ttu-id="304be-127">Windows 2000 Server \[applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="304be-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="304be-128">En-tête</span><span class="sxs-lookup"><span data-stu-id="304be-128">Header</span></span> | <span data-ttu-id="304be-129">ConsoleApi.h (via WinCon.h, include Windows.h)</span><span class="sxs-lookup"><span data-stu-id="304be-129">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="304be-130">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="304be-130">Library</span></span> | <span data-ttu-id="304be-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="304be-131">Kernel32.lib</span></span> |
| <span data-ttu-id="304be-132">DLL</span><span class="sxs-lookup"><span data-stu-id="304be-132">DLL</span></span> | <span data-ttu-id="304be-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="304be-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="304be-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="304be-134">See also</span></span>

[<span data-ttu-id="304be-135">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="304be-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="304be-136">Consoles</span><span class="sxs-lookup"><span data-stu-id="304be-136">Consoles</span></span>](consoles.md)

[<span data-ttu-id="304be-137">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="304be-137">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="304be-138">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="304be-138">**CreateProcess**</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)

[<span data-ttu-id="304be-139">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="304be-139">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="304be-140">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="304be-140">**GetStdHandle**</span></span>](getstdhandle.md)