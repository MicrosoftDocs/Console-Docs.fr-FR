---
title: GetCurrentConsoleFont fonction)
description: Récupère des informations sur la police de console actuelle pour une mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/GetCurrentConsoleFont
- wincon/GetCurrentConsoleFont
- GetCurrentConsoleFont
MS-HAID:
- '\_win32\_getcurrentconsolefont'
- base.getcurrentconsolefont
- consoles.getcurrentconsolefont
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 347508ea-5c15-4568-b99f-1e7f5cdac8c1
topic_type:
- apiref
api_name:
- GetCurrentConsoleFont
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 93f22e1b1d1fa6d60e5d97b7650809d19e01f03c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357259"
---
# <a name="getcurrentconsolefont-function"></a><span data-ttu-id="9d4d7-104">GetCurrentConsoleFont fonction)</span><span class="sxs-lookup"><span data-stu-id="9d4d7-104">GetCurrentConsoleFont function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="9d4d7-105">Récupère des informations sur la police de la console actuelle.</span><span class="sxs-lookup"><span data-stu-id="9d4d7-105">Retrieves information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="9d4d7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d4d7-106">Syntax</span></span>

```C
BOOL WINAPI GetCurrentConsoleFont(
  _In_  HANDLE             hConsoleOutput,
  _In_  BOOL               bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFO lpConsoleCurrentFont
);
```

## <a name="parameters"></a><span data-ttu-id="9d4d7-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d4d7-107">Parameters</span></span>

<span data-ttu-id="9d4d7-108">*hConsoleOutput* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="9d4d7-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="9d4d7-109">Handle vers la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="9d4d7-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="9d4d7-110">Le handle doit avoir le droit d’accès **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="9d4d7-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="9d4d7-111">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="9d4d7-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="9d4d7-112">*bMaximumWindow* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="9d4d7-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="9d4d7-113">Si ce paramètre a la **valeur true**, les informations sur la police sont récupérées pour la taille maximale de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="9d4d7-113">If this parameter is **TRUE**, font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="9d4d7-114">Si ce paramètre a la **valeur false**, les informations sur la police sont récupérées pour la taille de fenêtre actuelle.</span><span class="sxs-lookup"><span data-stu-id="9d4d7-114">If this parameter is **FALSE**, font information is retrieved for the current window size.</span></span>

<span data-ttu-id="9d4d7-115">*lpConsoleCurrentFont* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="9d4d7-115">*lpConsoleCurrentFont* \[out\]</span></span>  
<span data-ttu-id="9d4d7-116">Pointeur vers une structure [**d' \_ \_ informations de police de console**](console-font-info-str.md) qui reçoit les informations de police demandées.</span><span class="sxs-lookup"><span data-stu-id="9d4d7-116">A pointer to a [**CONSOLE\_FONT\_INFO**](console-font-info-str.md) structure that receives the requested font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="9d4d7-117">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="9d4d7-117">Return value</span></span>

<span data-ttu-id="9d4d7-118">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="9d4d7-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="9d4d7-119">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="9d4d7-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="9d4d7-120">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="9d4d7-120">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="9d4d7-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="9d4d7-121">Remarks</span></span>

<span data-ttu-id="9d4d7-122">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0500 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="9d4d7-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="9d4d7-123">Pour plus d’informations, consultez [utilisation des en-têtes Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="9d4d7-123">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="9d4d7-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9d4d7-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="9d4d7-125">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="9d4d7-125">Minimum supported client</span></span> | <span data-ttu-id="9d4d7-126">Applications de \[ Bureau Windows XP uniquement\]</span><span class="sxs-lookup"><span data-stu-id="9d4d7-126">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="9d4d7-127">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="9d4d7-127">Minimum supported server</span></span> | <span data-ttu-id="9d4d7-128">Applications de bureau Windows Server 2003 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="9d4d7-128">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="9d4d7-129">En-tête</span><span class="sxs-lookup"><span data-stu-id="9d4d7-129">Header</span></span> | <span data-ttu-id="9d4d7-130">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9d4d7-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="9d4d7-131">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="9d4d7-131">Library</span></span> | <span data-ttu-id="9d4d7-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="9d4d7-132">Kernel32.lib</span></span> |
| <span data-ttu-id="9d4d7-133">DLL</span><span class="sxs-lookup"><span data-stu-id="9d4d7-133">DLL</span></span> | <span data-ttu-id="9d4d7-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9d4d7-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="9d4d7-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d4d7-135">See also</span></span>

[<span data-ttu-id="9d4d7-136">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="9d4d7-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="9d4d7-137">Mémoires tampons d’écran d’une console</span><span class="sxs-lookup"><span data-stu-id="9d4d7-137">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="9d4d7-138">**\_informations sur la police de la console \_**</span><span class="sxs-lookup"><span data-stu-id="9d4d7-138">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="9d4d7-139">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="9d4d7-139">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)