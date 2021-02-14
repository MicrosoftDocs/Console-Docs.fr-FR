---
title: GetConsoleScreenBufferInfo fonction)
description: Consultez les informations de référence sur la fonction GetConsoleScreenBufferInfo, qui récupère des informations sur la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfo
- wincon/GetConsoleScreenBufferInfo
- GetConsoleScreenBufferInfo
ms.assetid: eafe819e-a99a-4ce1-8898-8860444a31af
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 2f80f77b749fc9e9dc0aebf4507b0c41f589e40c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358909"
---
# <a name="getconsolescreenbufferinfo-function"></a><span data-ttu-id="95530-104">GetConsoleScreenBufferInfo fonction)</span><span class="sxs-lookup"><span data-stu-id="95530-104">GetConsoleScreenBufferInfo function</span></span>

<span data-ttu-id="95530-105">Récupère des informations sur la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="95530-105">Retrieves information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="95530-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95530-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

## <a name="parameters"></a><span data-ttu-id="95530-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="95530-107">Parameters</span></span>

<span data-ttu-id="95530-108">*hConsoleOutput* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="95530-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="95530-109">Handle vers la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="95530-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="95530-110">Le handle doit avoir le droit d’accès **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="95530-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="95530-111">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="95530-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="95530-112">*lpConsoleScreenBufferInfo* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="95530-112">*lpConsoleScreenBufferInfo* \[out\]</span></span>  
<span data-ttu-id="95530-113">Pointeur vers une structure [**d' \_ \_ \_ informations de mémoire tampon d’écran de console**](console-screen-buffer-info-str.md) qui reçoit les informations de mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="95530-113">A pointer to a [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure that receives the console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="95530-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="95530-114">Return value</span></span>

<span data-ttu-id="95530-115">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="95530-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="95530-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="95530-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="95530-117">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="95530-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="95530-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="95530-118">Remarks</span></span>

<span data-ttu-id="95530-119">Le rectangle retourné dans le membre **srWindow** de la structure des [**\_ \_ \_ informations de mémoire tampon**](console-screen-buffer-info-str.md) de l’écran de la console peut être modifié, puis transmis à la fonction [**SetConsoleWindowInfo**](setconsolewindowinfo.md) pour faire défiler la mémoire tampon de l’écran de la console dans la fenêtre, pour modifier la taille de la fenêtre, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="95530-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="95530-120">Toutes les coordonnées retournées dans la structure des [**\_ \_ \_ informations de mémoire tampon**](console-screen-buffer-info-str.md) de l’écran de la console sont exprimées en coordonnées de cellule de caractères, où l’origine (0,0) se trouve dans l’angle supérieur gauche de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="95530-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

> [!TIP]
> <span data-ttu-id="95530-121">Cette API n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="95530-121">This API does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="95530-122">Son utilisation peut toujours être requise pour les applications qui tentent de dessiner des colonnes, des grilles ou de remplir l’affichage pour récupérer la taille de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="95530-122">Its use may still be required for applications that are attempting to draw columns, grids, or fill the display to retrieve the window size.</span></span> <span data-ttu-id="95530-123">Cet état de la fenêtre est géré par TTY/PTY/Pseudoconsole en dehors du flux de flux normal, et est généralement considéré comme un privilège utilisateur non réglable par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="95530-123">This window state is managed by the TTY/PTY/Pseudoconsole outside of the normal stream flow and is generally considered a user privilege not adjustable by the client application.</span></span> <span data-ttu-id="95530-124">Les mises à jour peuvent être reçues sur [**ReadConsoleInput**](readconsoleinput.md).</span><span class="sxs-lookup"><span data-stu-id="95530-124">Updates can be received on [**ReadConsoleInput**](readconsoleinput.md).</span></span>

## <a name="examples"></a><span data-ttu-id="95530-125">Exemples</span><span class="sxs-lookup"><span data-stu-id="95530-125">Examples</span></span>

<span data-ttu-id="95530-126">Pour obtenir un exemple, consultez [défilement de la fenêtre d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-window.md).</span><span class="sxs-lookup"><span data-stu-id="95530-126">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="95530-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="95530-127">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="95530-128">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="95530-128">Minimum supported client</span></span> | <span data-ttu-id="95530-129">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="95530-129">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="95530-130">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="95530-130">Minimum supported server</span></span> | <span data-ttu-id="95530-131">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="95530-131">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="95530-132">En-tête</span><span class="sxs-lookup"><span data-stu-id="95530-132">Header</span></span> | <span data-ttu-id="95530-133">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="95530-133">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="95530-134">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="95530-134">Library</span></span> | <span data-ttu-id="95530-135">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="95530-135">Kernel32.lib</span></span> |
| <span data-ttu-id="95530-136">DLL</span><span class="sxs-lookup"><span data-stu-id="95530-136">DLL</span></span> | <span data-ttu-id="95530-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="95530-137">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="95530-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95530-138">See also</span></span>

[<span data-ttu-id="95530-139">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="95530-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="95530-140">**\_ \_ informations sur la mémoire tampon d’écran de la console \_**</span><span class="sxs-lookup"><span data-stu-id="95530-140">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="95530-141">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="95530-141">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="95530-142">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="95530-142">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="95530-143">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="95530-143">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="95530-144">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="95530-144">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="95530-145">Taille de la mémoire tampon de la fenêtre et de l’écran</span><span class="sxs-lookup"><span data-stu-id="95530-145">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)