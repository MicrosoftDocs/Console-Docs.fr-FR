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
ms.openlocfilehash: b394f116a75e3c8fb7fddbdc3335e89fbca96652
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037857"
---
# <a name="getcurrentconsolefont-function"></a><span data-ttu-id="429c7-104">GetCurrentConsoleFont fonction)</span><span class="sxs-lookup"><span data-stu-id="429c7-104">GetCurrentConsoleFont function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="429c7-105">Récupère des informations sur la police de la console actuelle.</span><span class="sxs-lookup"><span data-stu-id="429c7-105">Retrieves information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="429c7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="429c7-106">Syntax</span></span>

```C
BOOL WINAPI GetCurrentConsoleFont(
  _In_  HANDLE             hConsoleOutput,
  _In_  BOOL               bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFO lpConsoleCurrentFont
);
```

## <a name="parameters"></a><span data-ttu-id="429c7-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="429c7-107">Parameters</span></span>

<span data-ttu-id="429c7-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="429c7-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="429c7-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="429c7-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="429c7-110">Le handle doit avoir le droit d’accès **\_ en lecture générique** .</span><span class="sxs-lookup"><span data-stu-id="429c7-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="429c7-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="429c7-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="429c7-112">*bMaximumWindow* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="429c7-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="429c7-113">Si ce paramètre a la **valeur true** , les informations sur la police sont récupérées pour la taille maximale de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="429c7-113">If this parameter is **TRUE** , font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="429c7-114">Si ce paramètre a la **valeur false** , les informations sur la police sont récupérées pour la taille de fenêtre actuelle.</span><span class="sxs-lookup"><span data-stu-id="429c7-114">If this parameter is **FALSE** , font information is retrieved for the current window size.</span></span>

<span data-ttu-id="429c7-115">*lpConsoleCurrentFont* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="429c7-115">*lpConsoleCurrentFont* \[out\]</span></span>  
<span data-ttu-id="429c7-116">Pointeur vers une structure [**d' \_ \_ informations de police de console**](console-font-info-str.md) qui reçoit les informations de police demandées.</span><span class="sxs-lookup"><span data-stu-id="429c7-116">A pointer to a [**CONSOLE\_FONT\_INFO**](console-font-info-str.md) structure that receives the requested font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="429c7-117">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="429c7-117">Return value</span></span>

<span data-ttu-id="429c7-118">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="429c7-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="429c7-119">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="429c7-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="429c7-120">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="429c7-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="429c7-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="429c7-121">Remarks</span></span>

<span data-ttu-id="429c7-122">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0500 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="429c7-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="429c7-123">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="429c7-123">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="429c7-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="429c7-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="429c7-125">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="429c7-125">Minimum supported client</span></span> | <span data-ttu-id="429c7-126">Applications de \[ Bureau Windows XP uniquement\]</span><span class="sxs-lookup"><span data-stu-id="429c7-126">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="429c7-127">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="429c7-127">Minimum supported server</span></span> | <span data-ttu-id="429c7-128">Applications de bureau Windows Server 2003 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="429c7-128">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="429c7-129">En-tête</span><span class="sxs-lookup"><span data-stu-id="429c7-129">Header</span></span> | <span data-ttu-id="429c7-130">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="429c7-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="429c7-131">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="429c7-131">Library</span></span> | <span data-ttu-id="429c7-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="429c7-132">Kernel32.lib</span></span> |
| <span data-ttu-id="429c7-133">DLL</span><span class="sxs-lookup"><span data-stu-id="429c7-133">DLL</span></span> | <span data-ttu-id="429c7-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="429c7-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="429c7-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="429c7-135">See also</span></span>

[<span data-ttu-id="429c7-136">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="429c7-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="429c7-137">Mémoires tampons d’écran d’une console</span><span class="sxs-lookup"><span data-stu-id="429c7-137">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="429c7-138">**\_informations sur la police de la console \_**</span><span class="sxs-lookup"><span data-stu-id="429c7-138">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="429c7-139">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="429c7-139">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)
