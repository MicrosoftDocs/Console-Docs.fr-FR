---
title: GetConsoleSelectionInfo fonction)
description: Consultez les informations de référence sur la fonction GetConsoleSelectionInfo, qui récupère des informations sur la sélection de la console actuelle.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/GetConsoleSelectionInfo
- wincon/GetConsoleSelectionInfo
- GetConsoleSelectionInfo
MS-HAID:
- '\_win32\_getconsoleselectioninfo'
- base.getconsoleselectioninfo
- consoles.getconsoleselectioninfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 912efe9d-75dd-43bd-8dca-08671b5ed79c
topic_type:
- apiref
api_name:
- GetConsoleSelectionInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 2f1052940b468455121cc363317c2b7cfa8246b3
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038847"
---
# <a name="getconsoleselectioninfo-function"></a><span data-ttu-id="a07d0-104">GetConsoleSelectionInfo fonction)</span><span class="sxs-lookup"><span data-stu-id="a07d0-104">GetConsoleSelectionInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="a07d0-105">Récupère des informations sur la sélection de la console actuelle.</span><span class="sxs-lookup"><span data-stu-id="a07d0-105">Retrieves information about the current console selection.</span></span>

## <a name="syntax"></a><span data-ttu-id="a07d0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a07d0-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleSelectionInfo(
  _Out_ PCONSOLE_SELECTION_INFO lpConsoleSelectionInfo
);
```

## <a name="parameters"></a><span data-ttu-id="a07d0-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a07d0-107">Parameters</span></span>

<span data-ttu-id="a07d0-108">*lpConsoleSelectionInfo* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="a07d0-108">*lpConsoleSelectionInfo* \[out\]</span></span>  
<span data-ttu-id="a07d0-109">Pointeur vers une structure [**d' \_ \_ informations de sélection**](console-selection-info-str.md) de la console qui reçoit les informations de sélection.</span><span class="sxs-lookup"><span data-stu-id="a07d0-109">A pointer to a [**CONSOLE\_SELECTION\_INFO**](console-selection-info-str.md) structure that receives the selection information.</span></span>

## <a name="return-value"></a><span data-ttu-id="a07d0-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="a07d0-110">Return value</span></span>

<span data-ttu-id="a07d0-111">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="a07d0-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="a07d0-112">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="a07d0-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="a07d0-113">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="a07d0-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="a07d0-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="a07d0-114">Remarks</span></span>

<span data-ttu-id="a07d0-115">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0500 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="a07d0-115">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="a07d0-116">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="a07d0-116">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="a07d0-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a07d0-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="a07d0-118">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="a07d0-118">Minimum supported client</span></span> | <span data-ttu-id="a07d0-119">Applications de \[ Bureau Windows XP uniquement\]</span><span class="sxs-lookup"><span data-stu-id="a07d0-119">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="a07d0-120">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="a07d0-120">Minimum supported server</span></span> | <span data-ttu-id="a07d0-121">Applications de bureau Windows Server 2003 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="a07d0-121">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="a07d0-122">En-tête</span><span class="sxs-lookup"><span data-stu-id="a07d0-122">Header</span></span> | <span data-ttu-id="a07d0-123">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="a07d0-123">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="a07d0-124">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="a07d0-124">Library</span></span> | <span data-ttu-id="a07d0-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="a07d0-125">Kernel32.lib</span></span> |
| <span data-ttu-id="a07d0-126">DLL</span><span class="sxs-lookup"><span data-stu-id="a07d0-126">DLL</span></span> | <span data-ttu-id="a07d0-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="a07d0-127">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="a07d0-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a07d0-128">See also</span></span>

[<span data-ttu-id="a07d0-129">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="a07d0-129">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="a07d0-130">Sélection de consoles</span><span class="sxs-lookup"><span data-stu-id="a07d0-130">Console Selection</span></span>](console-selection.md)

[<span data-ttu-id="a07d0-131">**\_informations sur la sélection de la console \_**</span><span class="sxs-lookup"><span data-stu-id="a07d0-131">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)
