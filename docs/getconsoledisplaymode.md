---
title: GetConsoleDisplayMode fonction)
description: Consultez les informations de référence sur la fonction GetConsoleDisplayMode, qui récupère le mode d’affichage de la console actuelle.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 5b9ec78dc6fe5d7baa1a9af64010fd577f101c47
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358349"
---
# <a name="getconsoledisplaymode-function"></a><span data-ttu-id="409a2-104">GetConsoleDisplayMode fonction)</span><span class="sxs-lookup"><span data-stu-id="409a2-104">GetConsoleDisplayMode function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="409a2-105">Récupère le mode d’affichage de la console actuelle.</span><span class="sxs-lookup"><span data-stu-id="409a2-105">Retrieves the display mode of the current console.</span></span>

## <a name="syntax"></a><span data-ttu-id="409a2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="409a2-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

## <a name="parameters"></a><span data-ttu-id="409a2-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="409a2-107">Parameters</span></span>

<span data-ttu-id="409a2-108">*lpModeFlags* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="409a2-108">*lpModeFlags* \[out\]</span></span>  
<span data-ttu-id="409a2-109">Mode d’affichage de la console.</span><span class="sxs-lookup"><span data-stu-id="409a2-109">The display mode of the console.</span></span> <span data-ttu-id="409a2-110">Ce paramètre peut être une ou plusieurs des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="409a2-110">This parameter can be one or more of the following values.</span></span>

| <span data-ttu-id="409a2-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="409a2-111">Value</span></span> | <span data-ttu-id="409a2-112">Signification</span><span class="sxs-lookup"><span data-stu-id="409a2-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="409a2-113">**CONSOLE_FULLSCREEN** 1</span><span class="sxs-lookup"><span data-stu-id="409a2-113">**CONSOLE_FULLSCREEN** 1</span></span> | <span data-ttu-id="409a2-114">Console plein écran.</span><span class="sxs-lookup"><span data-stu-id="409a2-114">Full-screen console.</span></span> <span data-ttu-id="409a2-115">La console est dans ce mode dès que la fenêtre est agrandie.</span><span class="sxs-lookup"><span data-stu-id="409a2-115">The console is in this mode as soon as the window is maximized.</span></span> <span data-ttu-id="409a2-116">À ce stade, la transition vers le mode plein écran peut encore échouer.</span><span class="sxs-lookup"><span data-stu-id="409a2-116">At this point, the transition to full-screen mode can still fail.</span></span> |
| <span data-ttu-id="409a2-117">**CONSOLE_FULLSCREEN_HARDWARE** 2</span><span class="sxs-lookup"><span data-stu-id="409a2-117">**CONSOLE_FULLSCREEN_HARDWARE** 2</span></span> | <span data-ttu-id="409a2-118">La console plein écran communique directement avec le matériel vidéo.</span><span class="sxs-lookup"><span data-stu-id="409a2-118">Full-screen console communicating directly with the video hardware.</span></span> <span data-ttu-id="409a2-119">Ce mode est défini une fois que la console est en mode **CONSOLE_FULLSCREEN** pour indiquer que la transition vers le mode plein écran est terminée.</span><span class="sxs-lookup"><span data-stu-id="409a2-119">This mode is set after the console is in **CONSOLE_FULLSCREEN** mode to indicate that the transition to full-screen mode has completed.</span></span> |

> [!NOTE]
> <span data-ttu-id="409a2-120">La transition vers un mode matériel vidéo plein écran 100% a été supprimée dans Windows Vista avec le changement de plate-forme de la pile Graphics sur [WDDM](//windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model).</span><span class="sxs-lookup"><span data-stu-id="409a2-120">The transition to a 100% full screen video hardware mode was removed in Windows Vista with the replatforming of the graphics stack to [WDDM](//windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model).</span></span> <span data-ttu-id="409a2-121">Dans les versions ultérieures de Windows, l’état maximal résultant est **CONSOLE_FULLSCREEN** représentant une fenêtre sans trame qui s’affiche en plein écran, mais qui n’est pas en contrôle exclusif du matériel.</span><span class="sxs-lookup"><span data-stu-id="409a2-121">On later versions of Windows, the maximum resulting state is **CONSOLE_FULLSCREEN** representing a frameless window that appears full screen but isn't in exclusive control of the hardware.</span></span>

## <a name="return-value"></a><span data-ttu-id="409a2-122">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="409a2-122">Return value</span></span>

<span data-ttu-id="409a2-123">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="409a2-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="409a2-124">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="409a2-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="409a2-125">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="409a2-125">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="409a2-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="409a2-126">Remarks</span></span>

<span data-ttu-id="409a2-127">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0500 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="409a2-127">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="409a2-128">Pour plus d’informations, consultez [utilisation des en-têtes Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="409a2-128">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="409a2-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="409a2-129">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="409a2-130">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="409a2-130">Minimum supported client</span></span> | <span data-ttu-id="409a2-131">Applications de \[ Bureau Windows XP uniquement\]</span><span class="sxs-lookup"><span data-stu-id="409a2-131">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="409a2-132">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="409a2-132">Minimum supported server</span></span> | <span data-ttu-id="409a2-133">Applications de bureau Windows Server 2003 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="409a2-133">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="409a2-134">En-tête</span><span class="sxs-lookup"><span data-stu-id="409a2-134">Header</span></span> | <span data-ttu-id="409a2-135">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="409a2-135">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="409a2-136">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="409a2-136">Library</span></span> | <span data-ttu-id="409a2-137">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="409a2-137">Kernel32.lib</span></span> |
| <span data-ttu-id="409a2-138">DLL</span><span class="sxs-lookup"><span data-stu-id="409a2-138">DLL</span></span> | <span data-ttu-id="409a2-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="409a2-139">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="409a2-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="409a2-140">See also</span></span>

[<span data-ttu-id="409a2-141">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="409a2-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="409a2-142">Modes de la console</span><span class="sxs-lookup"><span data-stu-id="409a2-142">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="409a2-143">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="409a2-143">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)