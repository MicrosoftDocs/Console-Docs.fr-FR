---
title: GetConsoleFontSize fonction)
description: Récupère la taille de la police utilisée par la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/GetConsoleFontSize
- wincon/GetConsoleFontSize
- GetConsoleFontSize
MS-HAID:
- '\_win32\_getconsolefontsize'
- base.getconsolefontsize
- consoles.getconsolefontsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 51b1f58d-b3fb-4e09-8398-671b3959bb01
topic_type:
- apiref
api_name:
- GetConsoleFontSize
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 39a27f2bd2c4578296ee5699503ce86487060db3
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038897"
---
# <a name="getconsolefontsize-function"></a><span data-ttu-id="ca4da-104">GetConsoleFontSize fonction)</span><span class="sxs-lookup"><span data-stu-id="ca4da-104">GetConsoleFontSize function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="ca4da-105">Récupère la taille de la police utilisée par la mémoire tampon d’écran de console spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ca4da-105">Retrieves the size of the font used by the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="ca4da-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca4da-106">Syntax</span></span>

```C
COORD WINAPI GetConsoleFontSize(
  _In_ HANDLE hConsoleOutput,
  _In_ DWORD  nFont
);
```

## <a name="parameters"></a><span data-ttu-id="ca4da-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca4da-107">Parameters</span></span>

<span data-ttu-id="ca4da-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="ca4da-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="ca4da-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="ca4da-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="ca4da-110">Le handle doit avoir le droit d’accès **\_ en lecture générique** .</span><span class="sxs-lookup"><span data-stu-id="ca4da-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="ca4da-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="ca4da-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="ca4da-112">*nFont* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="ca4da-112">*nFont* \[in\]</span></span>  
<span data-ttu-id="ca4da-113">Index de la police dont la taille doit être récupérée.</span><span class="sxs-lookup"><span data-stu-id="ca4da-113">The index of the font whose size is to be retrieved.</span></span> <span data-ttu-id="ca4da-114">Cet index est obtenu en appelant la fonction [**GetCurrentConsoleFont**](getcurrentconsolefont.md) .</span><span class="sxs-lookup"><span data-stu-id="ca4da-114">This index is obtained by calling the [**GetCurrentConsoleFont**](getcurrentconsolefont.md) function.</span></span>

## <a name="return-value"></a><span data-ttu-id="ca4da-115">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="ca4da-115">Return value</span></span>

<span data-ttu-id="ca4da-116">Si la fonction est réussie, la valeur de retour est une structure de [**repère**](coord-str.md) qui contient la largeur et la hauteur de chaque caractère de la police, en unités logiques.</span><span class="sxs-lookup"><span data-stu-id="ca4da-116">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="ca4da-117">Le membre **X** contient la largeur, tandis que le membre **Y** contient la hauteur.</span><span class="sxs-lookup"><span data-stu-id="ca4da-117">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="ca4da-118">Si la fonction échoue, la largeur et la hauteur sont égales à zéro.</span><span class="sxs-lookup"><span data-stu-id="ca4da-118">If the function fails, the width and the height are zero.</span></span> <span data-ttu-id="ca4da-119">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="ca4da-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="ca4da-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="ca4da-120">Remarks</span></span>

<span data-ttu-id="ca4da-121">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0500 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="ca4da-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="ca4da-122">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="ca4da-122">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="ca4da-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ca4da-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ca4da-124">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ca4da-124">Minimum supported client</span></span> | <span data-ttu-id="ca4da-125">Applications de \[ Bureau Windows XP uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ca4da-125">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="ca4da-126">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ca4da-126">Minimum supported server</span></span> | <span data-ttu-id="ca4da-127">Applications de bureau Windows Server 2003 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ca4da-127">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="ca4da-128">En-tête</span><span class="sxs-lookup"><span data-stu-id="ca4da-128">Header</span></span> | <span data-ttu-id="ca4da-129">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ca4da-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ca4da-130">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="ca4da-130">Library</span></span> | <span data-ttu-id="ca4da-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ca4da-131">Kernel32.lib</span></span> |
| <span data-ttu-id="ca4da-132">DLL</span><span class="sxs-lookup"><span data-stu-id="ca4da-132">DLL</span></span> | <span data-ttu-id="ca4da-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ca4da-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="ca4da-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca4da-134">See also</span></span>

[<span data-ttu-id="ca4da-135">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="ca4da-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ca4da-136">Mémoires tampons d’écran d’une console</span><span class="sxs-lookup"><span data-stu-id="ca4da-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="ca4da-137">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="ca4da-137">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="ca4da-138">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="ca4da-138">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)
