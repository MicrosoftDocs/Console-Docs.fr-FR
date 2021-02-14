---
title: SetConsoleActiveScreenBuffer fonction)
description: Définit la mémoire tampon d’écran spécifiée comme étant la mémoire tampon d’écran de la console actuellement affichée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/SetConsoleActiveScreenBuffer
- wincon/SetConsoleActiveScreenBuffer
- SetConsoleActiveScreenBuffer
MS-HAID:
- '\_win32\_setconsoleactivescreenbuffer'
- base.setconsoleactivescreenbuffer
- consoles.setconsoleactivescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c026cb94-c8ec-44ee-b432-3870ae3006c2
topic_type:
- apiref
api_name:
- SetConsoleActiveScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 72545409bfff6485a4e454d9a004f7f9fa0161e3
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357749"
---
# <a name="setconsoleactivescreenbuffer-function"></a><span data-ttu-id="679c5-104">SetConsoleActiveScreenBuffer fonction)</span><span class="sxs-lookup"><span data-stu-id="679c5-104">SetConsoleActiveScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="679c5-105">Définit la mémoire tampon d’écran spécifiée comme étant la mémoire tampon d’écran de la console actuellement affichée.</span><span class="sxs-lookup"><span data-stu-id="679c5-105">Sets the specified screen buffer to be the currently displayed console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="679c5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="679c5-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleActiveScreenBuffer(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a><span data-ttu-id="679c5-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="679c5-107">Parameters</span></span>

<span data-ttu-id="679c5-108">*hConsoleOutput* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="679c5-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="679c5-109">Handle vers la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="679c5-109">A handle to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="679c5-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="679c5-110">Return value</span></span>

<span data-ttu-id="679c5-111">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="679c5-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="679c5-112">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="679c5-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="679c5-113">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="679c5-113">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="679c5-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="679c5-114">Remarks</span></span>

<span data-ttu-id="679c5-115">Une console peut avoir plusieurs mémoires tampons d’écran.</span><span class="sxs-lookup"><span data-stu-id="679c5-115">A console can have multiple screen buffers.</span></span> <span data-ttu-id="679c5-116">**SetConsoleActiveScreenBuffer** détermine celui qui est affiché.</span><span class="sxs-lookup"><span data-stu-id="679c5-116">**SetConsoleActiveScreenBuffer** determines which one is displayed.</span></span> <span data-ttu-id="679c5-117">Vous pouvez écrire dans une mémoire tampon d’écran inactive, puis utiliser **SetConsoleActiveScreenBuffer** pour afficher le contenu de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="679c5-117">You can write to an inactive screen buffer and then use **SetConsoleActiveScreenBuffer** to display the buffer's contents.</span></span>

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a><span data-ttu-id="679c5-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="679c5-118">Examples</span></span>

<span data-ttu-id="679c5-119">Pour obtenir un exemple, consultez [lecture et écriture de blocs de caractères et d’attributs](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="679c5-119">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="679c5-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="679c5-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="679c5-121">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="679c5-121">Minimum supported client</span></span> | <span data-ttu-id="679c5-122">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="679c5-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="679c5-123">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="679c5-123">Minimum supported server</span></span> | <span data-ttu-id="679c5-124">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="679c5-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="679c5-125">En-tête</span><span class="sxs-lookup"><span data-stu-id="679c5-125">Header</span></span> | <span data-ttu-id="679c5-126">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="679c5-126">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="679c5-127">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="679c5-127">Library</span></span> | <span data-ttu-id="679c5-128">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="679c5-128">Kernel32.lib</span></span> |
| <span data-ttu-id="679c5-129">DLL</span><span class="sxs-lookup"><span data-stu-id="679c5-129">DLL</span></span> | <span data-ttu-id="679c5-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="679c5-130">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="679c5-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="679c5-131">See also</span></span>

[<span data-ttu-id="679c5-132">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="679c5-132">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="679c5-133">Mémoires tampons d’écran d’une console</span><span class="sxs-lookup"><span data-stu-id="679c5-133">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="679c5-134">**CreateConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="679c5-134">**CreateConsoleScreenBuffer**</span></span>](createconsolescreenbuffer.md)