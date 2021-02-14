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
ms.openlocfilehash: a26dbeb2a873bd780f91c240bf2658cde11b45ec
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359019"
---
# <a name="getconsolehistoryinfo-function"></a><span data-ttu-id="0c080-104">GetConsoleHistoryInfo fonction)</span><span class="sxs-lookup"><span data-stu-id="0c080-104">GetConsoleHistoryInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="0c080-105">Récupère les paramètres d’historique pour la console du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="0c080-105">Retrieves the history settings for the calling process's console.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c080-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c080-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a><span data-ttu-id="0c080-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0c080-107">Parameters</span></span>

<span data-ttu-id="0c080-108">*lpConsoleHistoryInfo* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="0c080-108">*lpConsoleHistoryInfo* \[out\]</span></span>  
<span data-ttu-id="0c080-109">Pointeur vers une structure [**d' \_ \_ informations d’historique**](console-history-info.md) de la console qui reçoit les paramètres d’historique de la console du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="0c080-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that receives the history settings for the calling process's console.</span></span>

## <a name="return-value"></a><span data-ttu-id="0c080-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0c080-110">Return value</span></span>

<span data-ttu-id="0c080-111">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="0c080-111">If the function succeeds the return value is nonzero.</span></span>

<span data-ttu-id="0c080-112">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="0c080-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0c080-113">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="0c080-113">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="0c080-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="0c080-114">Remarks</span></span>

<span data-ttu-id="0c080-115">Si le processus appelant n’est pas un processus de console, la fonction échoue et définit la dernière erreur sur **erreur \_ accès \_ refusé**.</span><span class="sxs-lookup"><span data-stu-id="0c080-115">If the calling process is not a console process, the function fails and sets the last error to **ERROR\_ACCESS\_DENIED**.</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="0c080-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0c080-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="0c080-117">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="0c080-117">Minimum supported client</span></span> | <span data-ttu-id="0c080-118">Applications de \[ Bureau Windows Vista uniquement\]</span><span class="sxs-lookup"><span data-stu-id="0c080-118">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="0c080-119">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="0c080-119">Minimum supported server</span></span> | <span data-ttu-id="0c080-120">Applications de bureau Windows Server 2008 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="0c080-120">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="0c080-121">En-tête</span><span class="sxs-lookup"><span data-stu-id="0c080-121">Header</span></span> | <span data-ttu-id="0c080-122">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0c080-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="0c080-123">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="0c080-123">Library</span></span> | <span data-ttu-id="0c080-124">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="0c080-124">Kernel32.lib</span></span> |
| <span data-ttu-id="0c080-125">DLL</span><span class="sxs-lookup"><span data-stu-id="0c080-125">DLL</span></span> | <span data-ttu-id="0c080-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0c080-126">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="0c080-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c080-127">See also</span></span>

[<span data-ttu-id="0c080-128">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="0c080-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0c080-129">**\_informations sur l’historique de la console \_**</span><span class="sxs-lookup"><span data-stu-id="0c080-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="0c080-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="0c080-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)