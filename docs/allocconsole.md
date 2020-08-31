---
title: AllocConsole fonction)
description: Consultez les informations de référence sur la fonction AllocConsole, qui alloue une nouvelle console pour le processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
ms.openlocfilehash: 2e06cdc82c4e58dd09b99fa08bf4917ad37b552f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059392"
---
# <a name="allocconsole-function"></a><span data-ttu-id="c7feb-104">AllocConsole fonction)</span><span class="sxs-lookup"><span data-stu-id="c7feb-104">AllocConsole function</span></span>


<span data-ttu-id="c7feb-105">Alloue une nouvelle console pour le processus appelant.</span><span class="sxs-lookup"><span data-stu-id="c7feb-105">Allocates a new console for the calling process.</span></span>

<a name="syntax"></a><span data-ttu-id="c7feb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7feb-106">Syntax</span></span>
------

```C
BOOL WINAPI AllocConsole(void);
```

<a name="parameters"></a><span data-ttu-id="c7feb-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7feb-107">Parameters</span></span>
----------

<span data-ttu-id="c7feb-108">Cette fonction n’a pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c7feb-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="c7feb-109">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="c7feb-109">Return value</span></span>
------------

<span data-ttu-id="c7feb-110">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="c7feb-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c7feb-111">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="c7feb-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c7feb-112">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="c7feb-112">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="c7feb-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="c7feb-113">Remarks</span></span>
-------

<span data-ttu-id="c7feb-114">Un processus ne peut être associé qu’à une seule console. par conséquent, la fonction **AllocConsole** échoue si le processus appelant possède déjà une console.</span><span class="sxs-lookup"><span data-stu-id="c7feb-114">A process can be associated with only one console, so the **AllocConsole** function fails if the calling process already has a console.</span></span> <span data-ttu-id="c7feb-115">Un processus peut utiliser la fonction [**FreeConsole**](freeconsole.md) pour se détacher de sa console actuelle, puis appeler **AllocConsole** pour créer une nouvelle console ou [**AttachConsole**](attachconsole.md) à attacher à une autre console.</span><span class="sxs-lookup"><span data-stu-id="c7feb-115">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its current console, then it can call **AllocConsole** to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<span data-ttu-id="c7feb-116">Si le processus appelant crée un processus enfant, l’enfant hérite de la nouvelle console.</span><span class="sxs-lookup"><span data-stu-id="c7feb-116">If the calling process creates a child process, the child inherits the new console.</span></span>

<span data-ttu-id="c7feb-117">**AllocConsole** Initialise une entrée standard, une sortie standard et des descripteurs d’erreur standard pour la nouvelle console.</span><span class="sxs-lookup"><span data-stu-id="c7feb-117">**AllocConsole** initializes standard input, standard output, and standard error handles for the new console.</span></span> <span data-ttu-id="c7feb-118">Le descripteur d’entrée standard est un handle de la mémoire tampon d’entrée de la console, et les handles de sortie standard et d’erreur standard sont des handles de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="c7feb-118">The standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles to the console's screen buffer.</span></span> <span data-ttu-id="c7feb-119">Pour récupérer ces descripteurs, utilisez la fonction [**GetStdHandle**](getstdhandle.md) .</span><span class="sxs-lookup"><span data-stu-id="c7feb-119">To retrieve these handles, use the [**GetStdHandle**](getstdhandle.md) function.</span></span>

<span data-ttu-id="c7feb-120">Cette fonction est principalement utilisée par une application d’interface graphique utilisateur (GUI) pour créer une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="c7feb-120">This function is primarily used by a graphical user interface (GUI) application to create a console window.</span></span> <span data-ttu-id="c7feb-121">Les applications GUI sont initialisées sans console.</span><span class="sxs-lookup"><span data-stu-id="c7feb-121">GUI applications are initialized without a console.</span></span> <span data-ttu-id="c7feb-122">Les applications console sont initialisées avec une console, sauf si elles sont créées en tant que processus détachés (en appelant la fonction [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) avec l’indicateur de \*\* \_ processus détaché\*\* ).</span><span class="sxs-lookup"><span data-stu-id="c7feb-122">Console applications are initialized with a console, unless they are created as detached processes (by calling the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function with the **DETACHED\_PROCESS** flag).</span></span>

<a name="requirements"></a><span data-ttu-id="c7feb-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c7feb-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="c7feb-124">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="c7feb-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="c7feb-125">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="c7feb-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c7feb-126">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="c7feb-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="c7feb-127">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="c7feb-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c7feb-128">En-tête</span><span class="sxs-lookup"><span data-stu-id="c7feb-128">Header</span></span></p></td>
<td><span data-ttu-id="c7feb-129">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c7feb-129">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c7feb-130">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="c7feb-130">Library</span></span></p></td>
<td><span data-ttu-id="c7feb-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="c7feb-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c7feb-132">DLL</span><span class="sxs-lookup"><span data-stu-id="c7feb-132">DLL</span></span></p></td>
<td><span data-ttu-id="c7feb-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c7feb-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="c7feb-134"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7feb-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="c7feb-135">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="c7feb-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c7feb-136">Consoles</span><span class="sxs-lookup"><span data-stu-id="c7feb-136">Consoles</span></span>](consoles.md)

[<span data-ttu-id="c7feb-137">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="c7feb-137">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="c7feb-138">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="c7feb-138">**CreateProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[<span data-ttu-id="c7feb-139">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="c7feb-139">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="c7feb-140">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="c7feb-140">**GetStdHandle**</span></span>](getstdhandle.md)

 

 




