---
title: MENU_EVENT_RECORD, structure
description: Décrit un événement de menu dans une structure d’enregistrement d’entrée de console \_ . Ces événements sont utilisés en interne et doivent être ignorés.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- wincontypes/MENU_EVENT_RECORD
- wincon/MENU_EVENT_RECORD
- MENU_EVENT_RECORD
- wincontypes/PMENU_EVENT_RECORD
- wincon/PMENU_EVENT_RECORD
- PMENU_EVENT_RECORD
MS-HAID:
- '\_win32\_menu\_event\_record\_str'
- base.menu\_event\_record\_str
- consoles.menu\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 7efef0e0-01ba-44ba-a972-25c6b3aed2bd
topic_type:
- apiref
api_name:
- MENU_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: dfca825c03dbf0e63041e68adc5e43f2ca0ef669
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039517"
---
# <a name="menu_event_record-structure"></a><span data-ttu-id="f0131-105">Structure d’enregistrement d' \_ événement de menu \_</span><span class="sxs-lookup"><span data-stu-id="f0131-105">MENU\_EVENT\_RECORD structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="f0131-106">Décrit un événement de menu dans une structure [**d' \_ enregistrement d’entrée**](input-record-str.md) de console.</span><span class="sxs-lookup"><span data-stu-id="f0131-106">Describes a menu event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="f0131-107">Ces événements sont utilisés en interne et doivent être ignorés.</span><span class="sxs-lookup"><span data-stu-id="f0131-107">These events are used internally and should be ignored.</span></span>

## <a name="syntax"></a><span data-ttu-id="f0131-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0131-108">Syntax</span></span>

```C
typedef struct _MENU_EVENT_RECORD {
  UINT dwCommandId;
} MENU_EVENT_RECORD, *PMENU_EVENT_RECORD;
```

## <a name="members"></a><span data-ttu-id="f0131-109">Membres</span><span class="sxs-lookup"><span data-stu-id="f0131-109">Members</span></span>

<span data-ttu-id="f0131-110">**dwCommandId**</span><span class="sxs-lookup"><span data-stu-id="f0131-110">**dwCommandId**</span></span>  
<span data-ttu-id="f0131-111">Réservé.</span><span class="sxs-lookup"><span data-stu-id="f0131-111">Reserved.</span></span>

## <a name="requirements"></a><span data-ttu-id="f0131-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f0131-112">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="f0131-113">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="f0131-113">Minimum supported client</span></span> | <span data-ttu-id="f0131-114">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="f0131-114">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="f0131-115">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="f0131-115">Minimum supported server</span></span> | <span data-ttu-id="f0131-116">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="f0131-116">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="f0131-117">En-tête</span><span class="sxs-lookup"><span data-stu-id="f0131-117">Header</span></span> | <span data-ttu-id="f0131-118">WinConTypes. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f0131-118">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="f0131-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0131-119">See also</span></span>

[<span data-ttu-id="f0131-120">**enregistrement d’entrée \_**</span><span class="sxs-lookup"><span data-stu-id="f0131-120">**INPUT\_RECORD**</span></span>](input-record-str.md)
