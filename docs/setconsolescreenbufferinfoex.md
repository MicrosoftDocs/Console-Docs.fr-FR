---
title: SetConsoleScreenBufferInfoEx fonction)
description: Définit les informations étendues relatives à la mémoire tampon d’écran de console spécifiée dans la mémoire tampon spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/SetConsoleScreenBufferInfoEx
- wincon/SetConsoleScreenBufferInfoEx
- SetConsoleScreenBufferInfoEx
MS-HAID:
- base.setconsolescreenbufferinfoex
- consoles.setconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ff851144-eee9-4410-8fd1-28aa24fc25f1
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4a83c91a60a26d8e962efdf10b127e97beb70a7f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039347"
---
# <a name="setconsolescreenbufferinfoex-function"></a><span data-ttu-id="63b03-104">SetConsoleScreenBufferInfoEx fonction)</span><span class="sxs-lookup"><span data-stu-id="63b03-104">SetConsoleScreenBufferInfoEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="63b03-105">Définit des informations étendues sur la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="63b03-105">Sets extended information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="63b03-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63b03-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleScreenBufferInfoEx(
  _In_ HANDLE                        hConsoleOutput,
  _In_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a><span data-ttu-id="63b03-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="63b03-107">Parameters</span></span>

<span data-ttu-id="63b03-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="63b03-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="63b03-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="63b03-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="63b03-110">Le descripteur doit avoir le droit d’accès en **\_ écriture générique** .</span><span class="sxs-lookup"><span data-stu-id="63b03-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="63b03-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="63b03-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="63b03-112">*lpConsoleScreenBufferInfoEx* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="63b03-112">*lpConsoleScreenBufferInfoEx* \[in\]</span></span>  
<span data-ttu-id="63b03-113">Une [**structure \_ \_ \_ INFOEX de mémoire tampon d’écran**](console-screen-buffer-infoex.md) de la console qui contient les informations de mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="63b03-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that contains the console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="63b03-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="63b03-114">Return value</span></span>

<span data-ttu-id="63b03-115">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="63b03-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="63b03-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="63b03-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="63b03-117">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="63b03-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="63b03-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="63b03-118">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="63b03-119">Cette API a un équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** partiel.</span><span class="sxs-lookup"><span data-stu-id="63b03-119">This API has a partial **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="63b03-120">La **[mémoire tampon de positionnement des curseurs](console-virtual-terminal-sequences.md#cursor-positioning)** et les **[attributs de texte](console-virtual-terminal-sequences.md#text-formatting)** ont des équivalents de séquence spécifiques.</span><span class="sxs-lookup"><span data-stu-id="63b03-120">**[Cursor positioning buffer](console-virtual-terminal-sequences.md#cursor-positioning)** and **[text attributes](console-virtual-terminal-sequences.md#text-formatting)** have specific sequence equivalents.</span></span> <span data-ttu-id="63b03-121">La table des couleurs n’est pas configurable, mais les **[couleurs étendues](console-virtual-terminal-sequences.md#extended-colors)** sont disponibles au-delà de ce qui est normalement disponible via les fonctions de la **[console](console-functions.md)** .</span><span class="sxs-lookup"><span data-stu-id="63b03-121">The color table is not configurable, but **[extended colors](console-virtual-terminal-sequences.md#extended-colors)** are available beyond what is normally available through **[console functions](console-functions.md)** .</span></span> <span data-ttu-id="63b03-122">Les attributs Popup ne sont pas équivalents à ceux des menus contextuels qui sont la responsabilité de l’application cliente de ligne de commande dans le monde des **terminaux virtuels** .</span><span class="sxs-lookup"><span data-stu-id="63b03-122">Popup attributes have no equivalent as popup menus are the responsibility of the command-line client application in the **virtual terminal** world.</span></span> <span data-ttu-id="63b03-123">Enfin, la taille de la fenêtre et l’État plein écran sont considérés comme des privilèges détenus par l’utilisateur dans le monde des **terminaux virtuels** et n’ont pas de séquence équivalente.</span><span class="sxs-lookup"><span data-stu-id="63b03-123">Finally, the size of the window and the full screen status are considered privileges owned by the user in the **virtual terminal** world and have no equivalent sequence.</span></span>

## <a name="requirements"></a><span data-ttu-id="63b03-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="63b03-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="63b03-125">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="63b03-125">Minimum supported client</span></span> | <span data-ttu-id="63b03-126">Applications de \[ Bureau Windows Vista uniquement\]</span><span class="sxs-lookup"><span data-stu-id="63b03-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="63b03-127">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="63b03-127">Minimum supported server</span></span> | <span data-ttu-id="63b03-128">Applications de bureau Windows Server 2008 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="63b03-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="63b03-129">En-tête</span><span class="sxs-lookup"><span data-stu-id="63b03-129">Header</span></span> | <span data-ttu-id="63b03-130">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="63b03-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="63b03-131">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="63b03-131">Library</span></span> | <span data-ttu-id="63b03-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="63b03-132">Kernel32.lib</span></span> |
| <span data-ttu-id="63b03-133">DLL</span><span class="sxs-lookup"><span data-stu-id="63b03-133">DLL</span></span> | <span data-ttu-id="63b03-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="63b03-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="63b03-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63b03-135">See also</span></span>

[<span data-ttu-id="63b03-136">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="63b03-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="63b03-137">**mémoire tampon d’écran de la CONSOLE \_ \_ \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="63b03-137">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="63b03-138">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="63b03-138">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)
