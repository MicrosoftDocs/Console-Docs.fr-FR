---
title: SetConsoleDisplayMode fonction)
description: Consultez les informations de référence sur la fonction SetConsoleDisplayMode, qui définit le mode d’affichage de la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- base.setconsoledisplaymode
- consoles.setconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744
topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: af61d897269311ccfa9db336083e898f6d75da80
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357699"
---
# <a name="setconsoledisplaymode-function"></a><span data-ttu-id="ec799-104">SetConsoleDisplayMode fonction)</span><span class="sxs-lookup"><span data-stu-id="ec799-104">SetConsoleDisplayMode function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="ec799-105">Définit le mode d’affichage de la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ec799-105">Sets the display mode of the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="ec799-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec799-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

## <a name="parameters"></a><span data-ttu-id="ec799-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ec799-107">Parameters</span></span>

<span data-ttu-id="ec799-108">*hConsoleOutput* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="ec799-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="ec799-109">Handle vers la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="ec799-109">A handle to the console screen buffer.</span></span>

<span data-ttu-id="ec799-110">*dwFlags* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="ec799-110">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="ec799-111">Mode d’affichage de la console.</span><span class="sxs-lookup"><span data-stu-id="ec799-111">The display mode of the console.</span></span> <span data-ttu-id="ec799-112">Ce paramètre peut être une ou plusieurs des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="ec799-112">This parameter can be one or more of the following values.</span></span>

| <span data-ttu-id="ec799-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="ec799-113">Value</span></span> | <span data-ttu-id="ec799-114">Signification</span><span class="sxs-lookup"><span data-stu-id="ec799-114">Meaning</span></span> |
|-|-|
| <span data-ttu-id="ec799-115">**CONSOLE_FULLSCREEN_MODE** 1</span><span class="sxs-lookup"><span data-stu-id="ec799-115">**CONSOLE_FULLSCREEN_MODE** 1</span></span> | <span data-ttu-id="ec799-116">Le texte est affiché en mode plein écran.</span><span class="sxs-lookup"><span data-stu-id="ec799-116">Text is displayed in full-screen mode.</span></span> |
| <span data-ttu-id="ec799-117">**CONSOLE_WINDOWED_MODE** 2</span><span class="sxs-lookup"><span data-stu-id="ec799-117">**CONSOLE_WINDOWED_MODE** 2</span></span> | <span data-ttu-id="ec799-118">Le texte est affiché dans une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="ec799-118">Text is displayed in a console window.</span></span> |

<span data-ttu-id="ec799-119">*lpNewScreenBufferDimensions* \[ out, facultatif\]</span><span class="sxs-lookup"><span data-stu-id="ec799-119">*lpNewScreenBufferDimensions* \[out, optional\]</span></span>  
<span data-ttu-id="ec799-120">Pointeur vers une structure de [**repère**](coord-str.md) qui reçoit les nouvelles dimensions de la mémoire tampon d’écran, en caractères.</span><span class="sxs-lookup"><span data-stu-id="ec799-120">A pointer to a [**COORD**](coord-str.md) structure that receives the new dimensions of the screen buffer, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="ec799-121">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="ec799-121">Return value</span></span>

<span data-ttu-id="ec799-122">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="ec799-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ec799-123">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="ec799-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ec799-124">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="ec799-124">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="ec799-125">Notes</span><span class="sxs-lookup"><span data-stu-id="ec799-125">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="ec799-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ec799-126">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ec799-127">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ec799-127">Minimum supported client</span></span> | <span data-ttu-id="ec799-128">Applications de \[ Bureau Windows XP uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ec799-128">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="ec799-129">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ec799-129">Minimum supported server</span></span> | <span data-ttu-id="ec799-130">Applications de bureau Windows Server 2003 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ec799-130">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="ec799-131">En-tête</span><span class="sxs-lookup"><span data-stu-id="ec799-131">Header</span></span> | <span data-ttu-id="ec799-132">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ec799-132">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ec799-133">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="ec799-133">Library</span></span> | <span data-ttu-id="ec799-134">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="ec799-134">Kernel32.lib</span></span> |
| <span data-ttu-id="ec799-135">DLL</span><span class="sxs-lookup"><span data-stu-id="ec799-135">DLL</span></span> | <span data-ttu-id="ec799-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ec799-136">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="ec799-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec799-137">See also</span></span>

[<span data-ttu-id="ec799-138">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="ec799-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ec799-139">Modes de la console</span><span class="sxs-lookup"><span data-stu-id="ec799-139">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="ec799-140">**GetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="ec799-140">**GetConsoleDisplayMode**</span></span>](getconsoledisplaymode.md)