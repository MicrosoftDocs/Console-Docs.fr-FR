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
ms.openlocfilehash: 46c412ccb41ac17a8e7cf327c80d7f8330738d65
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039327"
---
# <a name="setconsolescreenbuffersize-function"></a><span data-ttu-id="52f5e-104">SetConsoleScreenBufferSize fonction)</span><span class="sxs-lookup"><span data-stu-id="52f5e-104">SetConsoleScreenBufferSize function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="52f5e-105">Modifie la taille de la mémoire tampon d’écran de la console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="52f5e-105">Changes the size of the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="52f5e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52f5e-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleScreenBufferSize(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwSize
);
```

## <a name="parameters"></a><span data-ttu-id="52f5e-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="52f5e-107">Parameters</span></span>

<span data-ttu-id="52f5e-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="52f5e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="52f5e-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="52f5e-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="52f5e-110">Le handle doit avoir le droit d’accès **\_ en lecture générique** .</span><span class="sxs-lookup"><span data-stu-id="52f5e-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="52f5e-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="52f5e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="52f5e-112">*dwSize nul* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="52f5e-112">*dwSize* \[in\]</span></span>  
<span data-ttu-id="52f5e-113">Structure de [**repère**](coord-str.md) qui spécifie la nouvelle taille de la mémoire tampon d’écran de la console, en lignes et colonnes de caractères.</span><span class="sxs-lookup"><span data-stu-id="52f5e-113">A [**COORD**](coord-str.md) structure that specifies the new size of the console screen buffer, in character rows and columns.</span></span> <span data-ttu-id="52f5e-114">La largeur et la hauteur spécifiées ne peuvent pas être inférieures à la largeur et à la hauteur de la fenêtre de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="52f5e-114">The specified width and height cannot be less than the width and height of the console screen buffer's window.</span></span> <span data-ttu-id="52f5e-115">Les dimensions spécifiées ne peuvent pas non plus être inférieures à la taille minimale autorisée par le système.</span><span class="sxs-lookup"><span data-stu-id="52f5e-115">The specified dimensions also cannot be less than the minimum size allowed by the system.</span></span> <span data-ttu-id="52f5e-116">Cette valeur minimale dépend de la taille de police actuelle de la console (sélectionnée par l’utilisateur) et des valeurs de **\_ CXMIN** et **SM \_ CYMIN** retournées par la fonction [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) .</span><span class="sxs-lookup"><span data-stu-id="52f5e-116">This minimum depends on the current font size for the console (selected by the user) and the **SM\_CXMIN** and **SM\_CYMIN** values returned by the [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) function.</span></span>

## <a name="return-value"></a><span data-ttu-id="52f5e-117">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="52f5e-117">Return value</span></span>

<span data-ttu-id="52f5e-118">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="52f5e-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="52f5e-119">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="52f5e-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="52f5e-120">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="52f5e-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="52f5e-121">Notes</span><span class="sxs-lookup"><span data-stu-id="52f5e-121">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="52f5e-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="52f5e-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="52f5e-123">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="52f5e-123">Minimum supported client</span></span> | <span data-ttu-id="52f5e-124">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="52f5e-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="52f5e-125">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="52f5e-125">Minimum supported server</span></span> | <span data-ttu-id="52f5e-126">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="52f5e-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="52f5e-127">En-tête</span><span class="sxs-lookup"><span data-stu-id="52f5e-127">Header</span></span> | <span data-ttu-id="52f5e-128">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="52f5e-128">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="52f5e-129">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="52f5e-129">Library</span></span> | <span data-ttu-id="52f5e-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="52f5e-130">Kernel32.lib</span></span> |
| <span data-ttu-id="52f5e-131">DLL</span><span class="sxs-lookup"><span data-stu-id="52f5e-131">DLL</span></span> | <span data-ttu-id="52f5e-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="52f5e-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="52f5e-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52f5e-133">See also</span></span>

[<span data-ttu-id="52f5e-134">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="52f5e-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="52f5e-135">Mémoire tampon d’entrée d’une console</span><span class="sxs-lookup"><span data-stu-id="52f5e-135">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="52f5e-136">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="52f5e-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="52f5e-137">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="52f5e-137">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="52f5e-138">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="52f5e-138">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)
