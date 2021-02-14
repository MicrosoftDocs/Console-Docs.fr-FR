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
ms.openlocfilehash: c920e5dd279a23b07702fa12b80da4245561548f
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358449"
---
# <a name="getconsolecursorinfo-function"></a><span data-ttu-id="c1713-104">GetConsoleCursorInfo fonction)</span><span class="sxs-lookup"><span data-stu-id="c1713-104">GetConsoleCursorInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="c1713-105">Récupère des informations sur la taille et la visibilité du curseur pour la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c1713-105">Retrieves information about the size and visibility of the cursor for the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="c1713-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1713-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleCursorInfo(
  _In_  HANDLE               hConsoleOutput,
  _Out_ PCONSOLE_CURSOR_INFO lpConsoleCursorInfo
);
```

## <a name="parameters"></a><span data-ttu-id="c1713-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c1713-107">Parameters</span></span>

<span data-ttu-id="c1713-108">*hConsoleOutput* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="c1713-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="c1713-109">Handle vers la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="c1713-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="c1713-110">Le handle doit avoir le droit d’accès **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="c1713-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="c1713-111">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="c1713-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="c1713-112">*lpConsoleCursorInfo* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="c1713-112">*lpConsoleCursorInfo* \[out\]</span></span>  
<span data-ttu-id="c1713-113">Pointeur vers une structure [**d' \_ \_ informations de curseur de console**](console-cursor-info-str.md) qui reçoit des informations sur le curseur de la console.</span><span class="sxs-lookup"><span data-stu-id="c1713-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that receives information about the console's cursor.</span></span>

## <a name="return-value"></a><span data-ttu-id="c1713-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="c1713-114">Return value</span></span>

<span data-ttu-id="c1713-115">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="c1713-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c1713-116">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="c1713-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c1713-117">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="c1713-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="c1713-118">Notes</span><span class="sxs-lookup"><span data-stu-id="c1713-118">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="c1713-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c1713-119">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c1713-120">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="c1713-120">Minimum supported client</span></span> | <span data-ttu-id="c1713-121">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="c1713-121">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="c1713-122">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="c1713-122">Minimum supported server</span></span> | <span data-ttu-id="c1713-123">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="c1713-123">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="c1713-124">En-tête</span><span class="sxs-lookup"><span data-stu-id="c1713-124">Header</span></span> | <span data-ttu-id="c1713-125">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c1713-125">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c1713-126">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="c1713-126">Library</span></span> | <span data-ttu-id="c1713-127">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="c1713-127">Kernel32.lib</span></span> |
| <span data-ttu-id="c1713-128">DLL</span><span class="sxs-lookup"><span data-stu-id="c1713-128">DLL</span></span> | <span data-ttu-id="c1713-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c1713-129">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="c1713-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1713-130">See also</span></span>

[<span data-ttu-id="c1713-131">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="c1713-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c1713-132">Mémoires tampons d’écran d’une console</span><span class="sxs-lookup"><span data-stu-id="c1713-132">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="c1713-133">**\_informations sur le curseur de la console \_**</span><span class="sxs-lookup"><span data-stu-id="c1713-133">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="c1713-134">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="c1713-134">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)