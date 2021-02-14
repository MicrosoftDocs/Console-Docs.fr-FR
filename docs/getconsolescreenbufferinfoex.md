---
title: GetConsoleScreenBufferInfoEx fonction)
description: Récupère des informations étendues sur la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfoEx
- wincon/GetConsoleScreenBufferInfoEx
- GetConsoleScreenBufferInfoEx
MS-HAID:
- base.getconsolescreenbufferinfoex
- consoles.getconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 60534226-d26f-44e2-a4cc-64811882e308
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 482aaefbeed22475f6f9301d13f480ba5a416fa9
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358899"
---
# <a name="getconsolescreenbufferinfoex-function"></a><span data-ttu-id="78b57-104">GetConsoleScreenBufferInfoEx fonction)</span><span class="sxs-lookup"><span data-stu-id="78b57-104">GetConsoleScreenBufferInfoEx function</span></span>

<span data-ttu-id="78b57-105">Récupère des informations étendues sur la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="78b57-105">Retrieves extended information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="78b57-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78b57-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleScreenBufferInfoEx(
  _In_  HANDLE                        hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a><span data-ttu-id="78b57-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="78b57-107">Parameters</span></span>

<span data-ttu-id="78b57-108">*hConsoleOutput* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="78b57-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="78b57-109">Handle vers la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="78b57-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="78b57-110">Le handle doit avoir le droit d’accès **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="78b57-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="78b57-111">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="78b57-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="78b57-112">*lpConsoleScreenBufferInfoEx* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="78b57-112">*lpConsoleScreenBufferInfoEx* \[out\]</span></span>  
<span data-ttu-id="78b57-113">Une [**structure \_ \_ \_ INFOEX de mémoire tampon d’écran**](console-screen-buffer-infoex.md) de la console qui reçoit les informations de mémoire tampon d’écran de console demandées.</span><span class="sxs-lookup"><span data-stu-id="78b57-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that receives the requested console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="78b57-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="78b57-114">Return value</span></span>

<span data-ttu-id="78b57-115">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="78b57-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="78b57-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="78b57-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="78b57-117">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="78b57-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="78b57-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="78b57-118">Remarks</span></span>

<span data-ttu-id="78b57-119">Le rectangle retourné dans le membre **srWindow** de la structure INFOEX de la [**\_ \_ mémoire tampon \_ d’écran**](console-screen-buffer-infoex.md) de la console peut être modifié, puis transmis à la fonction [**SetConsoleWindowInfo**](setconsolewindowinfo.md) pour faire défiler la mémoire tampon de l’écran de la console dans la fenêtre, pour modifier la taille de la fenêtre, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="78b57-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="78b57-120">Toutes les coordonnées retournées dans la structure INFOEX de la [**\_ \_ mémoire tampon \_ d’écran**](console-screen-buffer-infoex.md) de la console sont exprimées en coordonnées de cellule de caractères, où l’origine (0,0) se trouve dans l’angle supérieur gauche de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="78b57-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

> [!TIP]
> <span data-ttu-id="78b57-121">Cette API n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="78b57-121">This API does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="78b57-122">Son utilisation peut toujours être requise pour les applications qui tentent de dessiner des colonnes, des grilles ou de remplir l’affichage pour récupérer la taille de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="78b57-122">Its use may still be required for applications that are attempting to draw columns, grids, or fill the display to retrieve the window size.</span></span> <span data-ttu-id="78b57-123">Cet état de la fenêtre est géré par TTY/PTY/Pseudoconsole en dehors du flux de flux normal, et est généralement considéré comme un privilège utilisateur non réglable par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="78b57-123">This window state is managed by the TTY/PTY/Pseudoconsole outside of the normal stream flow and is generally considered a user privilege not adjustable by the client application.</span></span> <span data-ttu-id="78b57-124">Les mises à jour peuvent être reçues sur [**ReadConsoleInput**](readconsoleinput.md).</span><span class="sxs-lookup"><span data-stu-id="78b57-124">Updates can be received on [**ReadConsoleInput**](readconsoleinput.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="78b57-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="78b57-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="78b57-126">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="78b57-126">Minimum supported client</span></span> | <span data-ttu-id="78b57-127">Applications de \[ Bureau Windows Vista uniquement\]</span><span class="sxs-lookup"><span data-stu-id="78b57-127">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="78b57-128">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="78b57-128">Minimum supported server</span></span> | <span data-ttu-id="78b57-129">Applications de bureau Windows Server 2008 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="78b57-129">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="78b57-130">En-tête</span><span class="sxs-lookup"><span data-stu-id="78b57-130">Header</span></span> | <span data-ttu-id="78b57-131">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="78b57-131">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="78b57-132">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="78b57-132">Library</span></span> | <span data-ttu-id="78b57-133">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="78b57-133">Kernel32.lib</span></span> |
| <span data-ttu-id="78b57-134">DLL</span><span class="sxs-lookup"><span data-stu-id="78b57-134">DLL</span></span> | <span data-ttu-id="78b57-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="78b57-135">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="78b57-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78b57-136">See also</span></span>

[<span data-ttu-id="78b57-137">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="78b57-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="78b57-138">**mémoire tampon d’écran de la CONSOLE \_ \_ \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="78b57-138">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="78b57-139">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="78b57-139">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)