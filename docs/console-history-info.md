---
title: Structure CONSOLE_HISTORY_INFO
description: Consultez les informations de référence sur la structure CONSOLE_HISTORY_INFO, qui contient des informations sur l’historique de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: ee0161f0c4aac5a280fd18260ebbb1f7ca57d54a
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059500"
---
# <a name="console_history_info-structure"></a><span data-ttu-id="5c2aa-104">\_Structure des informations de l’historique de la console \_</span><span class="sxs-lookup"><span data-stu-id="5c2aa-104">CONSOLE\_HISTORY\_INFO structure</span></span>


<span data-ttu-id="5c2aa-105">Contient des informations sur l’historique de la console.</span><span class="sxs-lookup"><span data-stu-id="5c2aa-105">Contains information about the console history.</span></span>

<a name="syntax"></a><span data-ttu-id="5c2aa-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c2aa-106">Syntax</span></span>
------

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

<a name="members"></a><span data-ttu-id="5c2aa-107">Membres</span><span class="sxs-lookup"><span data-stu-id="5c2aa-107">Members</span></span>
-------

<span data-ttu-id="5c2aa-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="5c2aa-108">**cbSize**</span></span>  
<span data-ttu-id="5c2aa-109">Taille de la structure en octets.</span><span class="sxs-lookup"><span data-stu-id="5c2aa-109">The size of the structure, in bytes.</span></span> <span data-ttu-id="5c2aa-110">Affectez à ce membre la valeur `sizeof(CONSOLE_HISTORY_INFO)` .</span><span class="sxs-lookup"><span data-stu-id="5c2aa-110">Set this member to `sizeof(CONSOLE_HISTORY_INFO)`.</span></span>

<span data-ttu-id="5c2aa-111">**HistoryBufferSize**</span><span class="sxs-lookup"><span data-stu-id="5c2aa-111">**HistoryBufferSize**</span></span>  
<span data-ttu-id="5c2aa-112">Nombre de commandes conservées dans chaque mémoire tampon de l’historique.</span><span class="sxs-lookup"><span data-stu-id="5c2aa-112">The number of commands kept in each history buffer.</span></span>

<span data-ttu-id="5c2aa-113">**NumberOfHistoryBuffers**</span><span class="sxs-lookup"><span data-stu-id="5c2aa-113">**NumberOfHistoryBuffers**</span></span>  
<span data-ttu-id="5c2aa-114">Nombre de mémoires tampons d’historique conservées pour ce processus de console.</span><span class="sxs-lookup"><span data-stu-id="5c2aa-114">The number of history buffers kept for this console process.</span></span>

<span data-ttu-id="5c2aa-115">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="5c2aa-115">**dwFlags**</span></span>  
<span data-ttu-id="5c2aa-116">Ce paramètre peut être égal à zéro ou à la valeur suivante.</span><span class="sxs-lookup"><span data-stu-id="5c2aa-116">This parameter can be zero or the following value.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="5c2aa-117">Value</span><span class="sxs-lookup"><span data-stu-id="5c2aa-117">Value</span></span></th>
<th><span data-ttu-id="5c2aa-118">Signification</span><span class="sxs-lookup"><span data-stu-id="5c2aa-118">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="5c2aa-119"><span id="HISTORY_NO_DUP_FLAG"></span><span id="history_no_dup_flag"></span>
<strong>HISTORY_NO_DUP_FLAG</strong> 0x1</span><span class="sxs-lookup"><span data-stu-id="5c2aa-119"><span id="HISTORY_NO_DUP_FLAG"></span><span id="history_no_dup_flag"></span>
<strong>HISTORY_NO_DUP_FLAG</strong> 0x1</span></span></td>
<td><p><span data-ttu-id="5c2aa-120">Les entrées en double ne sont pas stockées dans la mémoire tampon de l’historique.</span><span class="sxs-lookup"><span data-stu-id="5c2aa-120">Duplicate entries will not be stored in the history buffer.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="requirements"></a><span data-ttu-id="5c2aa-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5c2aa-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="5c2aa-122">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="5c2aa-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="5c2aa-123">Windows Vista [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="5c2aa-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5c2aa-124">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="5c2aa-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="5c2aa-125">Windows Server 2008 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="5c2aa-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5c2aa-126">En-tête</span><span class="sxs-lookup"><span data-stu-id="5c2aa-126">Header</span></span></p></td>
<td><span data-ttu-id="5c2aa-127">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5c2aa-127">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="5c2aa-128"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c2aa-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="5c2aa-129">**GetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="5c2aa-129">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)

[<span data-ttu-id="5c2aa-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="5c2aa-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)

 

 




