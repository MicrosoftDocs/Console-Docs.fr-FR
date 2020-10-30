---
title: SetConsoleCursorPosition fonction)
description: Consultez les informations de référence sur la fonction SetConsoleCursorPosition, qui définit la position du curseur dans la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/SetConsoleCursorPosition
- wincon/SetConsoleCursorPosition
- SetConsoleCursorPosition
MS-HAID:
- '\_win32\_setconsolecursorposition'
- base.setconsolecursorposition
- consoles.setconsolecursorposition
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8e9abada-a64e-429f-8286-ced1169c7104
topic_type:
- apiref
api_name:
- SetConsoleCursorPosition
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c93fbf4b619b522a95af2b03a49d60ff6f880e7d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039367"
---
# <a name="setconsolecursorposition-function"></a><span data-ttu-id="cab86-104">SetConsoleCursorPosition fonction)</span><span class="sxs-lookup"><span data-stu-id="cab86-104">SetConsoleCursorPosition function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="cab86-105">Définit la position du curseur dans la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="cab86-105">Sets the cursor position in the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="cab86-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cab86-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

## <a name="parameters"></a><span data-ttu-id="cab86-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cab86-107">Parameters</span></span>

<span data-ttu-id="cab86-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="cab86-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="cab86-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="cab86-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="cab86-110">Le handle doit avoir le droit d’accès **\_ en lecture générique** .</span><span class="sxs-lookup"><span data-stu-id="cab86-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="cab86-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="cab86-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="cab86-112">*dwCursorPosition* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="cab86-112">*dwCursorPosition* \[in\]</span></span>  
<span data-ttu-id="cab86-113">Structure de [**repère**](coord-str.md) qui spécifie la nouvelle position du curseur, en caractères.</span><span class="sxs-lookup"><span data-stu-id="cab86-113">A [**COORD**](coord-str.md) structure that specifies the new cursor position, in characters.</span></span> <span data-ttu-id="cab86-114">Les coordonnées sont la colonne et la ligne d’une cellule de caractère de mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="cab86-114">The coordinates are the column and row of a screen buffer character cell.</span></span> <span data-ttu-id="cab86-115">Les coordonnées doivent se trouver dans les limites de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="cab86-115">The coordinates must be within the boundaries of the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="cab86-116">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="cab86-116">Return value</span></span>

<span data-ttu-id="cab86-117">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="cab86-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="cab86-118">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="cab86-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="cab86-119">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="cab86-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="cab86-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="cab86-120">Remarks</span></span>

<span data-ttu-id="cab86-121">La position du curseur détermine l’emplacement d’affichage des caractères écrits par la fonction [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ou [**WriteConsole**](writeconsole.md) , ou renvoyé par la fonction [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ou [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="cab86-121">The cursor position determines where characters written by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function, are displayed.</span></span> <span data-ttu-id="cab86-122">Pour déterminer la position actuelle du curseur, utilisez la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="cab86-122">To determine the current position of the cursor, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="cab86-123">Si la nouvelle position du curseur ne se trouve pas dans les limites de la fenêtre de la mémoire tampon de l’écran de la console, l’origine de la fenêtre change pour rendre le curseur visible.</span><span class="sxs-lookup"><span data-stu-id="cab86-123">If the new cursor position is not within the boundaries of the console screen buffer's window, the window origin changes to make the cursor visible.</span></span>

> [!TIP]
> <span data-ttu-id="cab86-124">Cette API possède un **[terminal virtuel](console-virtual-terminal-sequences.md)** équivalent dans les sections de positionnement de curseur et **[de positionnement de](console-virtual-terminal-sequences.md#cursor-positioning)** curseur **[simples](console-virtual-terminal-sequences.md#simple-cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="cab86-124">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[simple cursor positioning](console-virtual-terminal-sequences.md#simple-cursor-positioning)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sections.</span></span> <span data-ttu-id="cab86-125">L’utilisation des séquences de saut de ligne, de retour chariot, de retour arrière et de contrôle Tab peut également faciliter le positionnement du curseur.</span><span class="sxs-lookup"><span data-stu-id="cab86-125">Use of the newline, carriage return, backspace, and tab control sequences can also assist with cursor positioning.</span></span>

## <a name="examples"></a><span data-ttu-id="cab86-126">Exemples</span><span class="sxs-lookup"><span data-stu-id="cab86-126">Examples</span></span>

<span data-ttu-id="cab86-127">Pour obtenir un exemple, consultez [utilisation des fonctions d’entrée et de sortie High-Level](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="cab86-127">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="cab86-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cab86-128">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="cab86-129">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="cab86-129">Minimum supported client</span></span> | <span data-ttu-id="cab86-130">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="cab86-130">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="cab86-131">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="cab86-131">Minimum supported server</span></span> | <span data-ttu-id="cab86-132">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="cab86-132">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="cab86-133">En-tête</span><span class="sxs-lookup"><span data-stu-id="cab86-133">Header</span></span> | <span data-ttu-id="cab86-134">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="cab86-134">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="cab86-135">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="cab86-135">Library</span></span> | <span data-ttu-id="cab86-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="cab86-136">Kernel32.lib</span></span> |
| <span data-ttu-id="cab86-137">DLL</span><span class="sxs-lookup"><span data-stu-id="cab86-137">DLL</span></span> | <span data-ttu-id="cab86-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="cab86-138">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="cab86-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cab86-139">See also</span></span>

[<span data-ttu-id="cab86-140">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="cab86-140">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="cab86-141">Mémoires tampons d’écran d’une console</span><span class="sxs-lookup"><span data-stu-id="cab86-141">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="cab86-142">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="cab86-142">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="cab86-143">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="cab86-143">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="cab86-144">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="cab86-144">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="cab86-145">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="cab86-145">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="cab86-146">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="cab86-146">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

[<span data-ttu-id="cab86-147">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="cab86-147">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="cab86-148">**Appel**</span><span class="sxs-lookup"><span data-stu-id="cab86-148">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
