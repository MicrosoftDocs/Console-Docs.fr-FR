---
title: GetConsoleCursorInfo fonction)
description: Récupère des informations sur la taille et la visibilité du curseur pour la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/GetConsoleCursorInfo
- wincon/GetConsoleCursorInfo
- GetConsoleCursorInfo
MS-HAID:
- '\_win32\_getconsolecursorinfo'
- base.getconsolecursorinfo
- consoles.getconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6200577d-8d84-46bd-9330-d0b6cbbb3e52
topic_type:
- apiref
api_name:
- GetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 2d9869c5c291addaf94a06fa67e11e3195ead686
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038917"
---
# <a name="getconsolecursorinfo-function"></a><span data-ttu-id="5c0e5-104">GetConsoleCursorInfo fonction)</span><span class="sxs-lookup"><span data-stu-id="5c0e5-104">GetConsoleCursorInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="5c0e5-105">Récupère des informations sur la taille et la visibilité du curseur pour la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5c0e5-105">Retrieves information about the size and visibility of the cursor for the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="5c0e5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c0e5-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleCursorInfo(
  _In_  HANDLE               hConsoleOutput,
  _Out_ PCONSOLE_CURSOR_INFO lpConsoleCursorInfo
);
```

## <a name="parameters"></a><span data-ttu-id="5c0e5-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5c0e5-107">Parameters</span></span>

<span data-ttu-id="5c0e5-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="5c0e5-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="5c0e5-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="5c0e5-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="5c0e5-110">Le handle doit avoir le droit d’accès **\_ en lecture générique** .</span><span class="sxs-lookup"><span data-stu-id="5c0e5-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="5c0e5-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="5c0e5-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="5c0e5-112">*lpConsoleCursorInfo* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="5c0e5-112">*lpConsoleCursorInfo* \[out\]</span></span>  
<span data-ttu-id="5c0e5-113">Pointeur vers une structure [**d' \_ \_ informations de curseur de console**](console-cursor-info-str.md) qui reçoit des informations sur le curseur de la console.</span><span class="sxs-lookup"><span data-stu-id="5c0e5-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that receives information about the console's cursor.</span></span>

## <a name="return-value"></a><span data-ttu-id="5c0e5-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="5c0e5-114">Return value</span></span>

<span data-ttu-id="5c0e5-115">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="5c0e5-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="5c0e5-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="5c0e5-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="5c0e5-117">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="5c0e5-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="5c0e5-118">Notes</span><span class="sxs-lookup"><span data-stu-id="5c0e5-118">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="5c0e5-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5c0e5-119">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="5c0e5-120">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="5c0e5-120">Minimum supported client</span></span> | <span data-ttu-id="5c0e5-121">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="5c0e5-121">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="5c0e5-122">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="5c0e5-122">Minimum supported server</span></span> | <span data-ttu-id="5c0e5-123">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="5c0e5-123">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="5c0e5-124">En-tête</span><span class="sxs-lookup"><span data-stu-id="5c0e5-124">Header</span></span> | <span data-ttu-id="5c0e5-125">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5c0e5-125">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="5c0e5-126">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="5c0e5-126">Library</span></span> | <span data-ttu-id="5c0e5-127">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="5c0e5-127">Kernel32.lib</span></span> |
| <span data-ttu-id="5c0e5-128">DLL</span><span class="sxs-lookup"><span data-stu-id="5c0e5-128">DLL</span></span> | <span data-ttu-id="5c0e5-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="5c0e5-129">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="5c0e5-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c0e5-130">See also</span></span>

[<span data-ttu-id="5c0e5-131">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="5c0e5-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="5c0e5-132">Mémoires tampons d’écran d’une console</span><span class="sxs-lookup"><span data-stu-id="5c0e5-132">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="5c0e5-133">**\_informations sur le curseur de la console \_**</span><span class="sxs-lookup"><span data-stu-id="5c0e5-133">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="5c0e5-134">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="5c0e5-134">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)
