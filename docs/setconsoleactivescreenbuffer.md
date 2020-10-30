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
ms.openlocfilehash: 7eb27a383a0bdbfc985188eb477ab9a878f33274
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039437"
---
# <a name="setconsoleactivescreenbuffer-function"></a><span data-ttu-id="3d422-104">SetConsoleActiveScreenBuffer fonction)</span><span class="sxs-lookup"><span data-stu-id="3d422-104">SetConsoleActiveScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="3d422-105">Définit la mémoire tampon d’écran spécifiée comme étant la mémoire tampon d’écran de la console actuellement affichée.</span><span class="sxs-lookup"><span data-stu-id="3d422-105">Sets the specified screen buffer to be the currently displayed console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="3d422-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d422-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleActiveScreenBuffer(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a><span data-ttu-id="3d422-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3d422-107">Parameters</span></span>

<span data-ttu-id="3d422-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="3d422-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="3d422-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="3d422-109">A handle to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="3d422-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="3d422-110">Return value</span></span>

<span data-ttu-id="3d422-111">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="3d422-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="3d422-112">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="3d422-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="3d422-113">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="3d422-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="3d422-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="3d422-114">Remarks</span></span>

<span data-ttu-id="3d422-115">Une console peut avoir plusieurs mémoires tampons d’écran.</span><span class="sxs-lookup"><span data-stu-id="3d422-115">A console can have multiple screen buffers.</span></span> <span data-ttu-id="3d422-116">**SetConsoleActiveScreenBuffer** détermine celui qui est affiché.</span><span class="sxs-lookup"><span data-stu-id="3d422-116">**SetConsoleActiveScreenBuffer** determines which one is displayed.</span></span> <span data-ttu-id="3d422-117">Vous pouvez écrire dans une mémoire tampon d’écran inactive, puis utiliser **SetConsoleActiveScreenBuffer** pour afficher le contenu de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="3d422-117">You can write to an inactive screen buffer and then use **SetConsoleActiveScreenBuffer** to display the buffer's contents.</span></span>

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a><span data-ttu-id="3d422-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="3d422-118">Examples</span></span>

<span data-ttu-id="3d422-119">Pour obtenir un exemple, consultez [lecture et écriture de blocs de caractères et d’attributs](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="3d422-119">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="3d422-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3d422-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="3d422-121">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="3d422-121">Minimum supported client</span></span> | <span data-ttu-id="3d422-122">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="3d422-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="3d422-123">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="3d422-123">Minimum supported server</span></span> | <span data-ttu-id="3d422-124">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="3d422-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="3d422-125">En-tête</span><span class="sxs-lookup"><span data-stu-id="3d422-125">Header</span></span> | <span data-ttu-id="3d422-126">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="3d422-126">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="3d422-127">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="3d422-127">Library</span></span> | <span data-ttu-id="3d422-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="3d422-128">Kernel32.lib</span></span> |
| <span data-ttu-id="3d422-129">DLL</span><span class="sxs-lookup"><span data-stu-id="3d422-129">DLL</span></span> | <span data-ttu-id="3d422-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3d422-130">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="3d422-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d422-131">See also</span></span>

[<span data-ttu-id="3d422-132">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="3d422-132">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3d422-133">Mémoires tampons d’écran d’une console</span><span class="sxs-lookup"><span data-stu-id="3d422-133">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="3d422-134">**CreateConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="3d422-134">**CreateConsoleScreenBuffer**</span></span>](createconsolescreenbuffer.md)
