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
ms.openlocfilehash: 4bbb14dd501d483f35fbce5e1a729eaf002b1579
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039397"
---
# <a name="setconsolecursorinfo-function"></a><span data-ttu-id="4479b-104">SetConsoleCursorInfo fonction)</span><span class="sxs-lookup"><span data-stu-id="4479b-104">SetConsoleCursorInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="4479b-105">Définit la taille et la visibilité du curseur pour la mémoire tampon d’écran de la console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4479b-105">Sets the size and visibility of the cursor for the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="4479b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4479b-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

## <a name="parameters"></a><span data-ttu-id="4479b-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4479b-107">Parameters</span></span>

<span data-ttu-id="4479b-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="4479b-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="4479b-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="4479b-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="4479b-110">Le handle doit avoir le droit d’accès **\_ en lecture générique** .</span><span class="sxs-lookup"><span data-stu-id="4479b-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="4479b-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="4479b-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="4479b-112">*lpConsoleCursorInfo* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="4479b-112">*lpConsoleCursorInfo* \[in\]</span></span>  
<span data-ttu-id="4479b-113">Pointeur vers une structure [**d' \_ \_ informations de curseur de console**](console-cursor-info-str.md) qui fournit les nouvelles spécifications pour le curseur de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="4479b-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that provides the new specifications for the console screen buffer's cursor.</span></span>

## <a name="return-value"></a><span data-ttu-id="4479b-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="4479b-114">Return value</span></span>

<span data-ttu-id="4479b-115">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="4479b-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4479b-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="4479b-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4479b-117">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4479b-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="4479b-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="4479b-118">Remarks</span></span>

<span data-ttu-id="4479b-119">Lorsque le curseur d’une mémoire tampon d’écran est visible, son apparence peut varier, du remplissage complet d’une cellule de caractère à l’affichage sous forme de ligne horizontale au bas de la cellule.</span><span class="sxs-lookup"><span data-stu-id="4479b-119">When a screen buffer's cursor is visible, its appearance can vary, ranging from completely filling a character cell to showing up as a horizontal line at the bottom of the cell.</span></span> <span data-ttu-id="4479b-120">Le membre **dwSize nul** de la structure d' [**\_ \_ informations du curseur**](console-cursor-info-str.md) de la console spécifie le pourcentage d’une cellule de caractère qui est remplie par le curseur.</span><span class="sxs-lookup"><span data-stu-id="4479b-120">The **dwSize** member of the [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure specifies the percentage of a character cell that is filled by the cursor.</span></span> <span data-ttu-id="4479b-121">Si ce membre est inférieur à 1 ou supérieur à 100, **SetConsoleCursorInfo** échoue.</span><span class="sxs-lookup"><span data-stu-id="4479b-121">If this member is less than 1 or greater than 100, **SetConsoleCursorInfo** fails.</span></span>

> [!TIP]
> <span data-ttu-id="4479b-122">Cette API a un **[terminal virtuel](console-virtual-terminal-sequences.md)** équivalent dans la section **[visibilité du curseur](console-virtual-terminal-sequences.md#cursor-visibility)** avec les `^[[?25h` `^[[?25l` séquences et.</span><span class="sxs-lookup"><span data-stu-id="4479b-122">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[cursor visibility](console-virtual-terminal-sequences.md#cursor-visibility)** section with the `^[[?25h` and `^[[?25l` sequences.</span></span> 

## <a name="requirements"></a><span data-ttu-id="4479b-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4479b-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4479b-124">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="4479b-124">Minimum supported client</span></span> | <span data-ttu-id="4479b-125">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="4479b-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="4479b-126">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="4479b-126">Minimum supported server</span></span> | <span data-ttu-id="4479b-127">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="4479b-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="4479b-128">En-tête</span><span class="sxs-lookup"><span data-stu-id="4479b-128">Header</span></span> | <span data-ttu-id="4479b-129">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4479b-129">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="4479b-130">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="4479b-130">Library</span></span> | <span data-ttu-id="4479b-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4479b-131">Kernel32.lib</span></span> |
| <span data-ttu-id="4479b-132">DLL</span><span class="sxs-lookup"><span data-stu-id="4479b-132">DLL</span></span> | <span data-ttu-id="4479b-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4479b-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="4479b-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4479b-134">See also</span></span>

[<span data-ttu-id="4479b-135">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="4479b-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4479b-136">Mémoires tampons d’écran d’une console</span><span class="sxs-lookup"><span data-stu-id="4479b-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="4479b-137">**\_informations sur le curseur de la console \_**</span><span class="sxs-lookup"><span data-stu-id="4479b-137">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="4479b-138">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="4479b-138">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="4479b-139">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="4479b-139">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)
