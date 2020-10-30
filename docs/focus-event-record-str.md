---
title: FOCUS_EVENT_RECORD, structure
description: Décrit un événement de focus dans une structure d’enregistrement d’entrée de console \_ . Ces événements sont utilisés en interne et doivent être ignorés.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: dc86c1b5b1c42a9d905673da4ea368de76a5fae9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038167"
---
# <a name="focus_event_record-structure"></a><span data-ttu-id="386a9-105">Structure d’enregistrement d' \_ événement de focus \_</span><span class="sxs-lookup"><span data-stu-id="386a9-105">FOCUS\_EVENT\_RECORD structure</span></span>

<span data-ttu-id="386a9-106">Décrit un événement de focus dans une structure [**d' \_ enregistrement d’entrée**](input-record-str.md) de console.</span><span class="sxs-lookup"><span data-stu-id="386a9-106">Describes a focus event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="386a9-107">Ces événements sont utilisés en interne et doivent être ignorés.</span><span class="sxs-lookup"><span data-stu-id="386a9-107">These events are used internally and should be ignored.</span></span>

## <a name="syntax"></a><span data-ttu-id="386a9-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="386a9-108">Syntax</span></span>

```C
typedef struct _FOCUS_EVENT_RECORD {
  BOOL bSetFocus;
} FOCUS_EVENT_RECORD;
```

## <a name="members"></a><span data-ttu-id="386a9-109">Membres</span><span class="sxs-lookup"><span data-stu-id="386a9-109">Members</span></span>

<span data-ttu-id="386a9-110">**bSetFocus**</span><span class="sxs-lookup"><span data-stu-id="386a9-110">**bSetFocus**</span></span>  
<span data-ttu-id="386a9-111">Réservé.</span><span class="sxs-lookup"><span data-stu-id="386a9-111">Reserved.</span></span>

## <a name="requirements"></a><span data-ttu-id="386a9-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="386a9-112">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="386a9-113">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="386a9-113">Minimum supported client</span></span> | <span data-ttu-id="386a9-114">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="386a9-114">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="386a9-115">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="386a9-115">Minimum supported server</span></span> | <span data-ttu-id="386a9-116">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="386a9-116">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="386a9-117">En-tête</span><span class="sxs-lookup"><span data-stu-id="386a9-117">Header</span></span> | <span data-ttu-id="386a9-118">WinConTypes. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="386a9-118">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="386a9-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="386a9-119">See also</span></span>

[<span data-ttu-id="386a9-120">**enregistrement d’entrée \_**</span><span class="sxs-lookup"><span data-stu-id="386a9-120">**INPUT\_RECORD**</span></span>](input-record-str.md)
