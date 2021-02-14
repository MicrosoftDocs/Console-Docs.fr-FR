---
title: SetConsoleCursorInfo fonction)
description: Définit la taille et la visibilité du curseur pour la mémoire tampon d’écran de la console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/SetConsoleCursorInfo
- wincon/SetConsoleCursorInfo
- SetConsoleCursorInfo
MS-HAID:
- '\_win32\_setconsolecursorinfo'
- base.setconsolecursorinfo
- consoles.setconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c98cbffb-18de-41e8-bba7-5fb46a0c5d25
topic_type:
- apiref
api_name:
- SetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 565ed3bda8bd864fb52aac0106f01cee96eb78ba
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357689"
---
# <a name="setconsolecursorinfo-function"></a><span data-ttu-id="756be-104">SetConsoleCursorInfo fonction)</span><span class="sxs-lookup"><span data-stu-id="756be-104">SetConsoleCursorInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="756be-105">Définit la taille et la visibilité du curseur pour la mémoire tampon d’écran de la console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="756be-105">Sets the size and visibility of the cursor for the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="756be-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="756be-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

## <a name="parameters"></a><span data-ttu-id="756be-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="756be-107">Parameters</span></span>

<span data-ttu-id="756be-108">*hConsoleOutput* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="756be-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="756be-109">Handle vers la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="756be-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="756be-110">Le handle doit avoir le droit d’accès **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="756be-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="756be-111">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="756be-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="756be-112">*lpConsoleCursorInfo* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="756be-112">*lpConsoleCursorInfo* \[in\]</span></span>  
<span data-ttu-id="756be-113">Pointeur vers une structure [**d' \_ \_ informations de curseur de console**](console-cursor-info-str.md) qui fournit les nouvelles spécifications pour le curseur de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="756be-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that provides the new specifications for the console screen buffer's cursor.</span></span>

## <a name="return-value"></a><span data-ttu-id="756be-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="756be-114">Return value</span></span>

<span data-ttu-id="756be-115">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="756be-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="756be-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="756be-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="756be-117">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="756be-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="756be-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="756be-118">Remarks</span></span>

<span data-ttu-id="756be-119">Lorsque le curseur d’une mémoire tampon d’écran est visible, son apparence peut varier, du remplissage complet d’une cellule de caractère à l’affichage sous forme de ligne horizontale au bas de la cellule.</span><span class="sxs-lookup"><span data-stu-id="756be-119">When a screen buffer's cursor is visible, its appearance can vary, ranging from completely filling a character cell to showing up as a horizontal line at the bottom of the cell.</span></span> <span data-ttu-id="756be-120">Le membre **dwSize nul** de la structure d' [**\_ \_ informations du curseur**](console-cursor-info-str.md) de la console spécifie le pourcentage d’une cellule de caractère qui est remplie par le curseur.</span><span class="sxs-lookup"><span data-stu-id="756be-120">The **dwSize** member of the [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure specifies the percentage of a character cell that is filled by the cursor.</span></span> <span data-ttu-id="756be-121">Si ce membre est inférieur à 1 ou supérieur à 100, **SetConsoleCursorInfo** échoue.</span><span class="sxs-lookup"><span data-stu-id="756be-121">If this member is less than 1 or greater than 100, **SetConsoleCursorInfo** fails.</span></span>

> [!TIP]
> <span data-ttu-id="756be-122">Cette API a un **[terminal virtuel](console-virtual-terminal-sequences.md)** équivalent dans la section **[visibilité du curseur](console-virtual-terminal-sequences.md#cursor-visibility)** avec les `^[[?25h` `^[[?25l` séquences et.</span><span class="sxs-lookup"><span data-stu-id="756be-122">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[cursor visibility](console-virtual-terminal-sequences.md#cursor-visibility)** section with the `^[[?25h` and `^[[?25l` sequences.</span></span> 

## <a name="requirements"></a><span data-ttu-id="756be-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="756be-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="756be-124">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="756be-124">Minimum supported client</span></span> | <span data-ttu-id="756be-125">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="756be-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="756be-126">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="756be-126">Minimum supported server</span></span> | <span data-ttu-id="756be-127">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="756be-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="756be-128">En-tête</span><span class="sxs-lookup"><span data-stu-id="756be-128">Header</span></span> | <span data-ttu-id="756be-129">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="756be-129">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="756be-130">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="756be-130">Library</span></span> | <span data-ttu-id="756be-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="756be-131">Kernel32.lib</span></span> |
| <span data-ttu-id="756be-132">DLL</span><span class="sxs-lookup"><span data-stu-id="756be-132">DLL</span></span> | <span data-ttu-id="756be-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="756be-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="756be-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="756be-134">See also</span></span>

[<span data-ttu-id="756be-135">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="756be-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="756be-136">Mémoires tampons d’écran d’une console</span><span class="sxs-lookup"><span data-stu-id="756be-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="756be-137">**\_informations sur le curseur de la console \_**</span><span class="sxs-lookup"><span data-stu-id="756be-137">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="756be-138">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="756be-138">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="756be-139">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="756be-139">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)