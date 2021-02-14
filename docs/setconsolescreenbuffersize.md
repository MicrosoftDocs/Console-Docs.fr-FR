---
title: SetConsoleScreenBufferSize fonction)
description: Consultez les informations de référence sur la fonction SetConsoleScreenBufferSize, qui modifie la taille de la mémoire tampon d’écran de la console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/SetConsoleScreenBufferSize
- wincon/SetConsoleScreenBufferSize
- SetConsoleScreenBufferSize
MS-HAID:
- '\_win32\_setconsolescreenbuffersize'
- base.setconsolescreenbuffersize
- consoles.setconsolescreenbuffersize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 50bf1973-5604-42fe-bbeb-611ddc240bdd
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 66c8eee2b3c4cd50e74ac17404dd30c571e47f96
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357579"
---
# <a name="setconsolescreenbuffersize-function"></a><span data-ttu-id="51ffe-104">SetConsoleScreenBufferSize fonction)</span><span class="sxs-lookup"><span data-stu-id="51ffe-104">SetConsoleScreenBufferSize function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="51ffe-105">Modifie la taille de la mémoire tampon d’écran de la console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="51ffe-105">Changes the size of the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="51ffe-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51ffe-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleScreenBufferSize(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwSize
);
```

## <a name="parameters"></a><span data-ttu-id="51ffe-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="51ffe-107">Parameters</span></span>

<span data-ttu-id="51ffe-108">*hConsoleOutput* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="51ffe-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="51ffe-109">Handle vers la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="51ffe-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="51ffe-110">Le handle doit avoir le droit d’accès **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="51ffe-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="51ffe-111">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="51ffe-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="51ffe-112">*dwSize nul* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="51ffe-112">*dwSize* \[in\]</span></span>  
<span data-ttu-id="51ffe-113">Structure de [**repère**](coord-str.md) qui spécifie la nouvelle taille de la mémoire tampon d’écran de la console, en lignes et colonnes de caractères.</span><span class="sxs-lookup"><span data-stu-id="51ffe-113">A [**COORD**](coord-str.md) structure that specifies the new size of the console screen buffer, in character rows and columns.</span></span> <span data-ttu-id="51ffe-114">La largeur et la hauteur spécifiées ne peuvent pas être inférieures à la largeur et à la hauteur de la fenêtre de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="51ffe-114">The specified width and height cannot be less than the width and height of the console screen buffer's window.</span></span> <span data-ttu-id="51ffe-115">Les dimensions spécifiées ne peuvent pas non plus être inférieures à la taille minimale autorisée par le système.</span><span class="sxs-lookup"><span data-stu-id="51ffe-115">The specified dimensions also cannot be less than the minimum size allowed by the system.</span></span> <span data-ttu-id="51ffe-116">Cette valeur minimale dépend de la taille de police actuelle de la console (sélectionnée par l’utilisateur) et des valeurs de **\_ CXMIN** et **SM \_ CYMIN** retournées par la fonction [**GetSystemMetrics**](/windows/win32/api/winuser/nf-winuser-getsystemmetrics) .</span><span class="sxs-lookup"><span data-stu-id="51ffe-116">This minimum depends on the current font size for the console (selected by the user) and the **SM\_CXMIN** and **SM\_CYMIN** values returned by the [**GetSystemMetrics**](/windows/win32/api/winuser/nf-winuser-getsystemmetrics) function.</span></span>

## <a name="return-value"></a><span data-ttu-id="51ffe-117">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="51ffe-117">Return value</span></span>

<span data-ttu-id="51ffe-118">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="51ffe-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="51ffe-119">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="51ffe-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="51ffe-120">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="51ffe-120">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="51ffe-121">Notes</span><span class="sxs-lookup"><span data-stu-id="51ffe-121">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="51ffe-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="51ffe-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="51ffe-123">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="51ffe-123">Minimum supported client</span></span> | <span data-ttu-id="51ffe-124">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="51ffe-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="51ffe-125">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="51ffe-125">Minimum supported server</span></span> | <span data-ttu-id="51ffe-126">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="51ffe-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="51ffe-127">En-tête</span><span class="sxs-lookup"><span data-stu-id="51ffe-127">Header</span></span> | <span data-ttu-id="51ffe-128">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="51ffe-128">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="51ffe-129">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="51ffe-129">Library</span></span> | <span data-ttu-id="51ffe-130">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="51ffe-130">Kernel32.lib</span></span> |
| <span data-ttu-id="51ffe-131">DLL</span><span class="sxs-lookup"><span data-stu-id="51ffe-131">DLL</span></span> | <span data-ttu-id="51ffe-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="51ffe-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="51ffe-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51ffe-133">See also</span></span>

[<span data-ttu-id="51ffe-134">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="51ffe-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="51ffe-135">Mémoire tampon d’entrée d’une console</span><span class="sxs-lookup"><span data-stu-id="51ffe-135">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="51ffe-136">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="51ffe-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="51ffe-137">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="51ffe-137">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="51ffe-138">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="51ffe-138">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)