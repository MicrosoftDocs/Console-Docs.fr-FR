---
title: SetConsoleHistoryInfo fonction)
description: Définit les paramètres de l’historique pour la console Windows du processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/SetConsoleHistoryInfo
- wincon/SetConsoleHistoryInfo
- SetConsoleHistoryInfo
MS-HAID:
- base.setconsolehistoryinfo
- consoles.setconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: db180f53-aa3c-4a91-bc3e-9f3f0bb7ab01
topic_type:
- apiref
api_name:
- SetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 618661b8c59506e2ba5e1f2b2b283ccf823b831a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039377"
---
# <a name="setconsolehistoryinfo-function"></a><span data-ttu-id="ae01a-104">SetConsoleHistoryInfo fonction)</span><span class="sxs-lookup"><span data-stu-id="ae01a-104">SetConsoleHistoryInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="ae01a-105">Définit les paramètres de l’historique pour la console du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="ae01a-105">Sets the history settings for the calling process's console.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae01a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae01a-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleHistoryInfo(
  _In_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a><span data-ttu-id="ae01a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ae01a-107">Parameters</span></span>

<span data-ttu-id="ae01a-108">*lpConsoleHistoryInfo* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="ae01a-108">*lpConsoleHistoryInfo* \[in\]</span></span>  
<span data-ttu-id="ae01a-109">Pointeur vers une structure [**d' \_ \_ informations d’historique**](console-history-info.md) de la console qui contient les paramètres d’historique de la console du processus.</span><span class="sxs-lookup"><span data-stu-id="ae01a-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that contains the history settings for the process's console.</span></span>

## <a name="return-value"></a><span data-ttu-id="ae01a-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="ae01a-110">Return value</span></span>

<span data-ttu-id="ae01a-111">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="ae01a-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ae01a-112">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="ae01a-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ae01a-113">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="ae01a-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="ae01a-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="ae01a-114">Remarks</span></span>

<span data-ttu-id="ae01a-115">Si le processus appelant n’est pas un processus de console, la fonction échoue et définit le dernier code d’erreur sur **erreur \_ accès \_ refusé** .</span><span class="sxs-lookup"><span data-stu-id="ae01a-115">If the calling process is not a console process, the function fails and sets the last error code to **ERROR\_ACCESS\_DENIED** .</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="ae01a-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ae01a-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ae01a-117">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ae01a-117">Minimum supported client</span></span> | <span data-ttu-id="ae01a-118">Applications de \[ Bureau Windows Vista uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ae01a-118">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="ae01a-119">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ae01a-119">Minimum supported server</span></span> | <span data-ttu-id="ae01a-120">Applications de bureau Windows Server 2008 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ae01a-120">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="ae01a-121">En-tête</span><span class="sxs-lookup"><span data-stu-id="ae01a-121">Header</span></span> | <span data-ttu-id="ae01a-122">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ae01a-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ae01a-123">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="ae01a-123">Library</span></span> | <span data-ttu-id="ae01a-124">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ae01a-124">Kernel32.lib</span></span> |
| <span data-ttu-id="ae01a-125">DLL</span><span class="sxs-lookup"><span data-stu-id="ae01a-125">DLL</span></span> | <span data-ttu-id="ae01a-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ae01a-126">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="ae01a-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae01a-127">See also</span></span>

[<span data-ttu-id="ae01a-128">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="ae01a-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ae01a-129">**\_informations sur l’historique de la console \_**</span><span class="sxs-lookup"><span data-stu-id="ae01a-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="ae01a-130">**GetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="ae01a-130">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)
