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
ms.openlocfilehash: 251fc71ef58840a962e5c1e09e88474959de27ae
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038767"
---
# <a name="getconsolescreenbufferinfo-function"></a><span data-ttu-id="d104a-104">GetConsoleScreenBufferInfo fonction)</span><span class="sxs-lookup"><span data-stu-id="d104a-104">GetConsoleScreenBufferInfo function</span></span>

<span data-ttu-id="d104a-105">Récupère des informations sur la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d104a-105">Retrieves information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="d104a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d104a-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

## <a name="parameters"></a><span data-ttu-id="d104a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d104a-107">Parameters</span></span>

<span data-ttu-id="d104a-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="d104a-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="d104a-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="d104a-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="d104a-110">Le handle doit avoir le droit d’accès **\_ en lecture générique** .</span><span class="sxs-lookup"><span data-stu-id="d104a-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="d104a-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="d104a-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="d104a-112">*lpConsoleScreenBufferInfo* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="d104a-112">*lpConsoleScreenBufferInfo* \[out\]</span></span>  
<span data-ttu-id="d104a-113">Pointeur vers une structure [**d' \_ \_ \_ informations de mémoire tampon d’écran de console**](console-screen-buffer-info-str.md) qui reçoit les informations de mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="d104a-113">A pointer to a [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure that receives the console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="d104a-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="d104a-114">Return value</span></span>

<span data-ttu-id="d104a-115">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="d104a-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d104a-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="d104a-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d104a-117">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="d104a-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="d104a-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="d104a-118">Remarks</span></span>

<span data-ttu-id="d104a-119">Le rectangle retourné dans le membre **srWindow** de la structure des [**\_ \_ \_ informations de mémoire tampon**](console-screen-buffer-info-str.md) de l’écran de la console peut être modifié, puis transmis à la fonction [**SetConsoleWindowInfo**](setconsolewindowinfo.md) pour faire défiler la mémoire tampon de l’écran de la console dans la fenêtre, pour modifier la taille de la fenêtre, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="d104a-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="d104a-120">Toutes les coordonnées retournées dans la structure des [**\_ \_ \_ informations de mémoire tampon**](console-screen-buffer-info-str.md) de l’écran de la console sont exprimées en coordonnées de cellule de caractères, où l’origine (0,0) se trouve dans l’angle supérieur gauche de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="d104a-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

> [!TIP]
> <span data-ttu-id="d104a-121">Cette API n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="d104a-121">This API does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="d104a-122">Son utilisation peut toujours être requise pour les applications qui tentent de dessiner des colonnes, des grilles ou de remplir l’affichage pour récupérer la taille de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="d104a-122">Its use may still be required for applications that are attempting to draw columns, grids, or fill the display to retrieve the window size.</span></span> <span data-ttu-id="d104a-123">Cet état de la fenêtre est géré par TTY/PTY/Pseudoconsole en dehors du flux de flux normal, et est généralement considéré comme un privilège utilisateur non réglable par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="d104a-123">This window state is managed by the TTY/PTY/Pseudoconsole outside of the normal stream flow and is generally considered a user privilege not adjustable by the client application.</span></span> <span data-ttu-id="d104a-124">Les mises à jour peuvent être reçues sur [**ReadConsoleInput**](readconsoleinput.md).</span><span class="sxs-lookup"><span data-stu-id="d104a-124">Updates can be received on [**ReadConsoleInput**](readconsoleinput.md).</span></span>

## <a name="examples"></a><span data-ttu-id="d104a-125">Exemples</span><span class="sxs-lookup"><span data-stu-id="d104a-125">Examples</span></span>

<span data-ttu-id="d104a-126">Pour obtenir un exemple, consultez [défilement de la fenêtre d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-window.md).</span><span class="sxs-lookup"><span data-stu-id="d104a-126">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="d104a-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d104a-127">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="d104a-128">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="d104a-128">Minimum supported client</span></span> | <span data-ttu-id="d104a-129">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="d104a-129">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="d104a-130">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="d104a-130">Minimum supported server</span></span> | <span data-ttu-id="d104a-131">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="d104a-131">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="d104a-132">En-tête</span><span class="sxs-lookup"><span data-stu-id="d104a-132">Header</span></span> | <span data-ttu-id="d104a-133">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d104a-133">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="d104a-134">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="d104a-134">Library</span></span> | <span data-ttu-id="d104a-135">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="d104a-135">Kernel32.lib</span></span> |
| <span data-ttu-id="d104a-136">DLL</span><span class="sxs-lookup"><span data-stu-id="d104a-136">DLL</span></span> | <span data-ttu-id="d104a-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d104a-137">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="d104a-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d104a-138">See also</span></span>

[<span data-ttu-id="d104a-139">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="d104a-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d104a-140">**\_ \_ informations sur la mémoire tampon d’écran de la console \_**</span><span class="sxs-lookup"><span data-stu-id="d104a-140">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="d104a-141">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="d104a-141">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="d104a-142">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="d104a-142">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="d104a-143">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="d104a-143">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="d104a-144">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="d104a-144">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="d104a-145">Taille de la mémoire tampon de la fenêtre et de l’écran</span><span class="sxs-lookup"><span data-stu-id="d104a-145">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)
