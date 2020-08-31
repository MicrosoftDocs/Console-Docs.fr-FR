---
title: Structure FOCUS_EVENT_RECORD
description: Décrit un événement de focus dans une structure d’enregistrement d’entrée de console \_ . Ces événements sont utilisés en interne et doivent être ignorés.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- wincontypes/FOCUS_EVENT_RECORD
- wincon/FOCUS_EVENT_RECORD
- FOCUS_EVENT_RECORD
- wincontypes/PFOCUS_EVENT_RECORD
- wincon/PFOCUS_EVENT_RECORD
- PFOCUS_EVENT_RECORD
MS-HAID:
- '\_win32\_focus\_event\_record\_str'
- base.focus\_event\_record\_str
- consoles.focus\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 4db0ae89-8446-4f0a-98e2-ba0b11ef7efe
topic_type:
- apiref
api_name:
- FOCUS_EVENT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 61f37e3645a66ca9f755f66f0baa03a2238983ad
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059205"
---
# <a name="focus_event_record-structure"></a><span data-ttu-id="84706-105">Structure d’enregistrement d' \_ événement de focus \_</span><span class="sxs-lookup"><span data-stu-id="84706-105">FOCUS\_EVENT\_RECORD structure</span></span>


<span data-ttu-id="84706-106">Décrit un événement de focus dans une structure [**d' \_ enregistrement d’entrée**](input-record-str.md) de console.</span><span class="sxs-lookup"><span data-stu-id="84706-106">Describes a focus event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="84706-107">Ces événements sont utilisés en interne et doivent être ignorés.</span><span class="sxs-lookup"><span data-stu-id="84706-107">These events are used internally and should be ignored.</span></span>

<a name="syntax"></a><span data-ttu-id="84706-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84706-108">Syntax</span></span>
------

```C
typedef struct _FOCUS_EVENT_RECORD {
  BOOL bSetFocus;
} FOCUS_EVENT_RECORD;
```

<a name="members"></a><span data-ttu-id="84706-109">Membres</span><span class="sxs-lookup"><span data-stu-id="84706-109">Members</span></span>
-------

<span data-ttu-id="84706-110">**bSetFocus**</span><span class="sxs-lookup"><span data-stu-id="84706-110">**bSetFocus**</span></span>  
<span data-ttu-id="84706-111">Réservé.</span><span class="sxs-lookup"><span data-stu-id="84706-111">Reserved.</span></span>

<a name="requirements"></a><span data-ttu-id="84706-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="84706-112">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="84706-113">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="84706-113">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="84706-114">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="84706-114">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="84706-115">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="84706-115">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="84706-116">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="84706-116">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="84706-117">En-tête</span><span class="sxs-lookup"><span data-stu-id="84706-117">Header</span></span></p></td>
<td><span data-ttu-id="84706-118">WinConTypes. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="84706-118">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="84706-119"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84706-119"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="84706-120">**enregistrement d’entrée \_**</span><span class="sxs-lookup"><span data-stu-id="84706-120">**INPUT\_RECORD**</span></span>](input-record-str.md)

 

 




