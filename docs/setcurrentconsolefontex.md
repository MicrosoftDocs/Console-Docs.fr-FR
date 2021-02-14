---
title: SetCurrentConsoleFontEx fonction)
description: Consultez les informations de référence sur la fonction SetCurrentConsoleFontEx, qui définit des informations étendues sur la police de la console actuelle.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/SetCurrentConsoleFontEx
- wincon/SetCurrentConsoleFontEx
- SetCurrentConsoleFontEx
MS-HAID:
- base.setcurrentconsolefontex
- consoles.setcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: fbc31e2a-31df-4e9e-9f61-35a4ff812f8f
topic_type:
- apiref
api_name:
- SetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 87bd942c0d739932ccb51e0af3e47e6fdb29f4da
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358519"
---
# <a name="setcurrentconsolefontex-function"></a><span data-ttu-id="3babe-104">SetCurrentConsoleFontEx fonction)</span><span class="sxs-lookup"><span data-stu-id="3babe-104">SetCurrentConsoleFontEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="3babe-105">Définit des informations étendues sur la police de la console actuelle.</span><span class="sxs-lookup"><span data-stu-id="3babe-105">Sets extended information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="3babe-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3babe-106">Syntax</span></span>

```C
BOOL WINAPI SetCurrentConsoleFontEx(
  _In_ HANDLE               hConsoleOutput,
  _In_ BOOL                 bMaximumWindow,
  _In_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

## <a name="parameters"></a><span data-ttu-id="3babe-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3babe-107">Parameters</span></span>

<span data-ttu-id="3babe-108">*hConsoleOutput* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="3babe-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="3babe-109">Handle vers la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="3babe-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="3babe-110">Le handle doit avoir le droit d’accès **GENERIC\_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="3babe-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="3babe-111">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="3babe-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="3babe-112">*bMaximumWindow* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="3babe-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="3babe-113">Si ce paramètre a la **valeur true**, les informations sur la police sont définies pour la taille maximale de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="3babe-113">If this parameter is **TRUE**, font information is set for the maximum window size.</span></span> <span data-ttu-id="3babe-114">Si ce paramètre a la **valeur false**, les informations sur la police sont définies pour la taille de fenêtre actuelle.</span><span class="sxs-lookup"><span data-stu-id="3babe-114">If this parameter is **FALSE**, font information is set for the current window size.</span></span>

<span data-ttu-id="3babe-115">*lpConsoleCurrentFontEx* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="3babe-115">*lpConsoleCurrentFontEx* \[in\]</span></span>  
<span data-ttu-id="3babe-116">Pointeur vers une structure [**de \_ police \_ de console INFOEX**](console-font-infoex.md) qui contient les informations sur la police.</span><span class="sxs-lookup"><span data-stu-id="3babe-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that contains the font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="3babe-117">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="3babe-117">Return value</span></span>

<span data-ttu-id="3babe-118">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="3babe-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="3babe-119">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="3babe-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="3babe-120">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="3babe-120">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="3babe-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="3babe-121">Remarks</span></span>

<span data-ttu-id="3babe-122">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0500 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="3babe-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="3babe-123">Pour plus d’informations, consultez [utilisation des en-têtes Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="3babe-123">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="3babe-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3babe-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="3babe-125">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="3babe-125">Minimum supported client</span></span> | <span data-ttu-id="3babe-126">Applications de \[ Bureau Windows Vista uniquement\]</span><span class="sxs-lookup"><span data-stu-id="3babe-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="3babe-127">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="3babe-127">Minimum supported server</span></span> | <span data-ttu-id="3babe-128">Applications de bureau Windows Server 2008 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="3babe-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="3babe-129">En-tête</span><span class="sxs-lookup"><span data-stu-id="3babe-129">Header</span></span> | <span data-ttu-id="3babe-130">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="3babe-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="3babe-131">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="3babe-131">Library</span></span> | <span data-ttu-id="3babe-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="3babe-132">Kernel32.lib</span></span> |
| <span data-ttu-id="3babe-133">DLL</span><span class="sxs-lookup"><span data-stu-id="3babe-133">DLL</span></span> | <span data-ttu-id="3babe-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3babe-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="3babe-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3babe-135">See also</span></span>

[<span data-ttu-id="3babe-136">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="3babe-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3babe-137">**police de la CONSOLE \_ \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="3babe-137">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)