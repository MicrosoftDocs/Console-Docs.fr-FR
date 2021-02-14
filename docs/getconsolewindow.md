---
title: GetConsoleWindow fonction)
description: Récupère le handle de fenêtre utilisé par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/GetConsoleWindow
- wincon/GetConsoleWindow
- GetConsoleWindow
MS-HAID:
- '\_win32\_getconsolewindow'
- base.getconsolewindow
- consoles.getconsolewindow
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a5ab0b37-45ac-4413-b6ff-73876556ad38
topic_type:
- apiref
api_name:
- GetConsoleWindow
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: ead8c4216fd0d1beb2a5fa6a6acfe3f4ce20df6f
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358889"
---
# <a name="getconsolewindow-function"></a><span data-ttu-id="c654c-104">GetConsoleWindow fonction)</span><span class="sxs-lookup"><span data-stu-id="c654c-104">GetConsoleWindow function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="c654c-105">Récupère le handle de fenêtre utilisé par la console associée au processus appelant.</span><span class="sxs-lookup"><span data-stu-id="c654c-105">Retrieves the window handle used by the console associated with the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="c654c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c654c-106">Syntax</span></span>

```C
HWND WINAPI GetConsoleWindow(void);
```

## <a name="parameters"></a><span data-ttu-id="c654c-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c654c-107">Parameters</span></span>

<span data-ttu-id="c654c-108">Cette fonction n’a pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c654c-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="c654c-109">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="c654c-109">Return value</span></span>

<span data-ttu-id="c654c-110">La valeur de retour est un handle de la fenêtre utilisée par la console associée au processus appelant ou **null** s’il n’existe aucune console associée.</span><span class="sxs-lookup"><span data-stu-id="c654c-110">The return value is a handle to the window used by the console associated with the calling process or **NULL** if there is no such associated console.</span></span>

## <a name="remarks"></a><span data-ttu-id="c654c-111">Notes</span><span class="sxs-lookup"><span data-stu-id="c654c-111">Remarks</span></span>

<span data-ttu-id="c654c-112">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0500 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="c654c-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="c654c-113">Pour plus d’informations, consultez [utilisation des en-têtes Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="c654c-113">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>


[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

<span data-ttu-id="c654c-114">Pour une application hébergée dans une session [**pseudoconsole**](pseudoconsoles.md) , cette fonction retourne un handle de fenêtre pour la file d’attente des messages uniquement.</span><span class="sxs-lookup"><span data-stu-id="c654c-114">For an application that is hosted inside a [**pseudoconsole**](pseudoconsoles.md) session, this function returns a window handle for message queue purposes only.</span></span> <span data-ttu-id="c654c-115">La fenêtre associée n’est pas affichée localement, car _pseudoconsole_ sérialise toutes les actions dans un flux de présentation dans une autre fenêtre de terminal à un autre endroit.</span><span class="sxs-lookup"><span data-stu-id="c654c-115">The associated window is not displayed locally as the _pseudoconsole_ is serializing all actions to a stream for presentation on another terminal window elsewhere.</span></span>

## <a name="requirements"></a><span data-ttu-id="c654c-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c654c-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c654c-117">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="c654c-117">Minimum supported client</span></span> | <span data-ttu-id="c654c-118">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="c654c-118">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="c654c-119">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="c654c-119">Minimum supported server</span></span> | <span data-ttu-id="c654c-120">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="c654c-120">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="c654c-121">En-tête</span><span class="sxs-lookup"><span data-stu-id="c654c-121">Header</span></span> | <span data-ttu-id="c654c-122">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c654c-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c654c-123">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="c654c-123">Library</span></span> | <span data-ttu-id="c654c-124">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="c654c-124">Kernel32.lib</span></span> |
| <span data-ttu-id="c654c-125">DLL</span><span class="sxs-lookup"><span data-stu-id="c654c-125">DLL</span></span> | <span data-ttu-id="c654c-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c654c-126">Kernel32.dll</span></span> |

</table>

## <a name="see-also"></a><span data-ttu-id="c654c-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c654c-127">See also</span></span>

[<span data-ttu-id="c654c-128">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="c654c-128">Console Functions</span></span>](console-functions.md)