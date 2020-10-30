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
ms.openlocfilehash: 52d7e50d7ced5615cb296c0590876e4604057e42
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039387"
---
# <a name="setconsoledisplaymode-function"></a><span data-ttu-id="bfa65-104">SetConsoleDisplayMode fonction)</span><span class="sxs-lookup"><span data-stu-id="bfa65-104">SetConsoleDisplayMode function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="bfa65-105">Définit le mode d’affichage de la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bfa65-105">Sets the display mode of the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="bfa65-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfa65-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

## <a name="parameters"></a><span data-ttu-id="bfa65-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bfa65-107">Parameters</span></span>

<span data-ttu-id="bfa65-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="bfa65-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="bfa65-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="bfa65-109">A handle to the console screen buffer.</span></span>

<span data-ttu-id="bfa65-110">*dwFlags* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="bfa65-110">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="bfa65-111">Mode d’affichage de la console.</span><span class="sxs-lookup"><span data-stu-id="bfa65-111">The display mode of the console.</span></span> <span data-ttu-id="bfa65-112">Ce paramètre peut être une ou plusieurs des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="bfa65-112">This parameter can be one or more of the following values.</span></span>

| <span data-ttu-id="bfa65-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="bfa65-113">Value</span></span> | <span data-ttu-id="bfa65-114">Signification</span><span class="sxs-lookup"><span data-stu-id="bfa65-114">Meaning</span></span> |
|-|-|
| <span data-ttu-id="bfa65-115">**CONSOLE_FULLSCREEN_MODE** 1</span><span class="sxs-lookup"><span data-stu-id="bfa65-115">**CONSOLE_FULLSCREEN_MODE** 1</span></span> | <span data-ttu-id="bfa65-116">Le texte est affiché en mode plein écran.</span><span class="sxs-lookup"><span data-stu-id="bfa65-116">Text is displayed in full-screen mode.</span></span> |
| <span data-ttu-id="bfa65-117">**CONSOLE_WINDOWED_MODE** 2</span><span class="sxs-lookup"><span data-stu-id="bfa65-117">**CONSOLE_WINDOWED_MODE** 2</span></span> | <span data-ttu-id="bfa65-118">Le texte est affiché dans une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="bfa65-118">Text is displayed in a console window.</span></span> |

<span data-ttu-id="bfa65-119">*lpNewScreenBufferDimensions* \[ out, facultatif\]</span><span class="sxs-lookup"><span data-stu-id="bfa65-119">*lpNewScreenBufferDimensions* \[out, optional\]</span></span>  
<span data-ttu-id="bfa65-120">Pointeur vers une structure de [**repère**](coord-str.md) qui reçoit les nouvelles dimensions de la mémoire tampon d’écran, en caractères.</span><span class="sxs-lookup"><span data-stu-id="bfa65-120">A pointer to a [**COORD**](coord-str.md) structure that receives the new dimensions of the screen buffer, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="bfa65-121">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="bfa65-121">Return value</span></span>

<span data-ttu-id="bfa65-122">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="bfa65-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="bfa65-123">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="bfa65-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="bfa65-124">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="bfa65-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="bfa65-125">Notes</span><span class="sxs-lookup"><span data-stu-id="bfa65-125">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="bfa65-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bfa65-126">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="bfa65-127">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="bfa65-127">Minimum supported client</span></span> | <span data-ttu-id="bfa65-128">Applications de \[ Bureau Windows XP uniquement\]</span><span class="sxs-lookup"><span data-stu-id="bfa65-128">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="bfa65-129">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="bfa65-129">Minimum supported server</span></span> | <span data-ttu-id="bfa65-130">Applications de bureau Windows Server 2003 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="bfa65-130">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="bfa65-131">En-tête</span><span class="sxs-lookup"><span data-stu-id="bfa65-131">Header</span></span> | <span data-ttu-id="bfa65-132">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="bfa65-132">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="bfa65-133">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="bfa65-133">Library</span></span> | <span data-ttu-id="bfa65-134">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="bfa65-134">Kernel32.lib</span></span> |
| <span data-ttu-id="bfa65-135">DLL</span><span class="sxs-lookup"><span data-stu-id="bfa65-135">DLL</span></span> | <span data-ttu-id="bfa65-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="bfa65-136">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="bfa65-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfa65-137">See also</span></span>

[<span data-ttu-id="bfa65-138">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="bfa65-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="bfa65-139">Modes de la console</span><span class="sxs-lookup"><span data-stu-id="bfa65-139">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="bfa65-140">**GetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="bfa65-140">**GetConsoleDisplayMode**</span></span>](getconsoledisplaymode.md)
