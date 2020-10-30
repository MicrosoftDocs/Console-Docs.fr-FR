---
title: GetConsoleHistoryInfo fonction)
description: Consultez les informations de référence sur la fonction GetConsoleHistoryInfo, qui récupère les paramètres d’historique de la console du processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/GetConsoleHistoryInfo
- wincon/GetConsoleHistoryInfo
- GetConsoleHistoryInfo
MS-HAID:
- base.getconsolehistoryinfo
- consoles.getconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 145008b3-8a4a-4e6a-9144-ee787ce90ef4
topic_type:
- apiref
api_name:
- GetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 8335b7e23ffec0e894221f97f2c01be5b081d31f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038027"
---
# <a name="getconsolehistoryinfo-function"></a><span data-ttu-id="57186-104">GetConsoleHistoryInfo fonction)</span><span class="sxs-lookup"><span data-stu-id="57186-104">GetConsoleHistoryInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="57186-105">Récupère les paramètres d’historique pour la console du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="57186-105">Retrieves the history settings for the calling process's console.</span></span>

## <a name="syntax"></a><span data-ttu-id="57186-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57186-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a><span data-ttu-id="57186-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="57186-107">Parameters</span></span>

<span data-ttu-id="57186-108">*lpConsoleHistoryInfo* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="57186-108">*lpConsoleHistoryInfo* \[out\]</span></span>  
<span data-ttu-id="57186-109">Pointeur vers une structure [**d' \_ \_ informations d’historique**](console-history-info.md) de la console qui reçoit les paramètres d’historique de la console du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="57186-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that receives the history settings for the calling process's console.</span></span>

## <a name="return-value"></a><span data-ttu-id="57186-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="57186-110">Return value</span></span>

<span data-ttu-id="57186-111">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="57186-111">If the function succeeds the return value is nonzero.</span></span>

<span data-ttu-id="57186-112">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="57186-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="57186-113">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="57186-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="57186-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="57186-114">Remarks</span></span>

<span data-ttu-id="57186-115">Si le processus appelant n’est pas un processus de console, la fonction échoue et définit la dernière erreur sur **erreur \_ accès \_ refusé** .</span><span class="sxs-lookup"><span data-stu-id="57186-115">If the calling process is not a console process, the function fails and sets the last error to **ERROR\_ACCESS\_DENIED** .</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="57186-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="57186-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="57186-117">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="57186-117">Minimum supported client</span></span> | <span data-ttu-id="57186-118">Applications de \[ Bureau Windows Vista uniquement\]</span><span class="sxs-lookup"><span data-stu-id="57186-118">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="57186-119">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="57186-119">Minimum supported server</span></span> | <span data-ttu-id="57186-120">Applications de bureau Windows Server 2008 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="57186-120">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="57186-121">En-tête</span><span class="sxs-lookup"><span data-stu-id="57186-121">Header</span></span> | <span data-ttu-id="57186-122">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="57186-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="57186-123">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="57186-123">Library</span></span> | <span data-ttu-id="57186-124">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="57186-124">Kernel32.lib</span></span> |
| <span data-ttu-id="57186-125">DLL</span><span class="sxs-lookup"><span data-stu-id="57186-125">DLL</span></span> | <span data-ttu-id="57186-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="57186-126">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="57186-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57186-127">See also</span></span>

[<span data-ttu-id="57186-128">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="57186-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="57186-129">**\_informations sur l’historique de la console \_**</span><span class="sxs-lookup"><span data-stu-id="57186-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="57186-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="57186-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)
