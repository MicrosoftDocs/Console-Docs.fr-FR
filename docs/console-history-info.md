---
title: CONSOLE_HISTORY_INFO, structure
description: Consultez les informations de référence sur la structure CONSOLE_HISTORY_INFO, qui contient des informations sur l’historique de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/CONSOLE_HISTORY_INFO
- wincon/CONSOLE_HISTORY_INFO
- CONSOLE_HISTORY_INFO
- consoleapi3/PCONSOLE_HISTORY_INFO
- wincon/PCONSOLE_HISTORY_INFO
- PCONSOLE_HISTORY_INFO
MS-HAID:
- base.console\_history\_info
- consoles.console\_history\_info
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: df7d2f12-5299-47ed-b1f6-2db903dba81b
topic_type:
- apiref
api_name:
- CONSOLE_HISTORY_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 24d41dca61146cc3e835f405889400ae0d168e7f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039217"
---
# <a name="console_history_info-structure"></a><span data-ttu-id="62a0c-104">\_Structure des informations de l’historique de la console \_</span><span class="sxs-lookup"><span data-stu-id="62a0c-104">CONSOLE\_HISTORY\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="62a0c-105">Contient des informations sur l’historique de la console.</span><span class="sxs-lookup"><span data-stu-id="62a0c-105">Contains information about the console history.</span></span>

## <a name="syntax"></a><span data-ttu-id="62a0c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62a0c-106">Syntax</span></span>

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

## <a name="members"></a><span data-ttu-id="62a0c-107">Membres</span><span class="sxs-lookup"><span data-stu-id="62a0c-107">Members</span></span>

<span data-ttu-id="62a0c-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="62a0c-108">**cbSize**</span></span>  
<span data-ttu-id="62a0c-109">Taille de la structure en octets.</span><span class="sxs-lookup"><span data-stu-id="62a0c-109">The size of the structure, in bytes.</span></span> <span data-ttu-id="62a0c-110">Affectez à ce membre la valeur `sizeof(CONSOLE_HISTORY_INFO)` .</span><span class="sxs-lookup"><span data-stu-id="62a0c-110">Set this member to `sizeof(CONSOLE_HISTORY_INFO)`.</span></span>

<span data-ttu-id="62a0c-111">**HistoryBufferSize**</span><span class="sxs-lookup"><span data-stu-id="62a0c-111">**HistoryBufferSize**</span></span>  
<span data-ttu-id="62a0c-112">Nombre de commandes conservées dans chaque mémoire tampon de l’historique.</span><span class="sxs-lookup"><span data-stu-id="62a0c-112">The number of commands kept in each history buffer.</span></span>

<span data-ttu-id="62a0c-113">**NumberOfHistoryBuffers**</span><span class="sxs-lookup"><span data-stu-id="62a0c-113">**NumberOfHistoryBuffers**</span></span>  
<span data-ttu-id="62a0c-114">Nombre de mémoires tampons d’historique conservées pour ce processus de console.</span><span class="sxs-lookup"><span data-stu-id="62a0c-114">The number of history buffers kept for this console process.</span></span>

<span data-ttu-id="62a0c-115">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="62a0c-115">**dwFlags**</span></span>  
<span data-ttu-id="62a0c-116">Ce paramètre peut être égal à zéro ou à la valeur suivante.</span><span class="sxs-lookup"><span data-stu-id="62a0c-116">This parameter can be zero or the following value.</span></span>

| <span data-ttu-id="62a0c-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="62a0c-117">Value</span></span> | <span data-ttu-id="62a0c-118">Signification</span><span class="sxs-lookup"><span data-stu-id="62a0c-118">Meaning</span></span> |
|-|-|
| <span data-ttu-id="62a0c-119">**HISTORY_NO_DUP_FLAG** 0x1</span><span class="sxs-lookup"><span data-stu-id="62a0c-119">**HISTORY_NO_DUP_FLAG** 0x1</span></span> | <span data-ttu-id="62a0c-120">Les entrées en double ne sont pas stockées dans la mémoire tampon de l’historique.</span><span class="sxs-lookup"><span data-stu-id="62a0c-120">Duplicate entries will not be stored in the history buffer.</span></span>

## <a name="requirements"></a><span data-ttu-id="62a0c-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="62a0c-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="62a0c-122">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="62a0c-122">Minimum supported client</span></span> | <span data-ttu-id="62a0c-123">Applications de \[ Bureau Windows Vista uniquement\]</span><span class="sxs-lookup"><span data-stu-id="62a0c-123">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="62a0c-124">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="62a0c-124">Minimum supported server</span></span> | <span data-ttu-id="62a0c-125">Applications de bureau Windows Server 2008 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="62a0c-125">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="62a0c-126">En-tête</span><span class="sxs-lookup"><span data-stu-id="62a0c-126">Header</span></span> | <span data-ttu-id="62a0c-127">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="62a0c-127">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="62a0c-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62a0c-128">See also</span></span>

[<span data-ttu-id="62a0c-129">**GetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="62a0c-129">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)

[<span data-ttu-id="62a0c-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="62a0c-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)
