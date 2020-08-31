---
title: Structure MENU_EVENT_RECORD
description: Décrit un événement de menu dans une structure d’enregistrement d’entrée de console \_ . Ces événements sont utilisés en interne et doivent être ignorés.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8bbfbf6ad8bd885d69ce08e94dfced93b0bd3257
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059077"
---
# <a name="menu_event_record-structure"></a><span data-ttu-id="7edd7-105">Structure d’enregistrement d' \_ événement de menu \_</span><span class="sxs-lookup"><span data-stu-id="7edd7-105">MENU\_EVENT\_RECORD structure</span></span>


<span data-ttu-id="7edd7-106">Décrit un événement de menu dans une structure [**d' \_ enregistrement d’entrée**](input-record-str.md) de console.</span><span class="sxs-lookup"><span data-stu-id="7edd7-106">Describes a menu event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="7edd7-107">Ces événements sont utilisés en interne et doivent être ignorés.</span><span class="sxs-lookup"><span data-stu-id="7edd7-107">These events are used internally and should be ignored.</span></span>

<a name="syntax"></a><span data-ttu-id="7edd7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7edd7-108">Syntax</span></span>
------

```C
typedef struct _MENU_EVENT_RECORD {
  UINT dwCommandId;
} MENU_EVENT_RECORD, *PMENU_EVENT_RECORD;
```

<a name="members"></a><span data-ttu-id="7edd7-109">Membres</span><span class="sxs-lookup"><span data-stu-id="7edd7-109">Members</span></span>
-------

<span data-ttu-id="7edd7-110">**dwCommandId**</span><span class="sxs-lookup"><span data-stu-id="7edd7-110">**dwCommandId**</span></span>  
<span data-ttu-id="7edd7-111">Réservé.</span><span class="sxs-lookup"><span data-stu-id="7edd7-111">Reserved.</span></span>

<a name="requirements"></a><span data-ttu-id="7edd7-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7edd7-112">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="7edd7-113">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7edd7-113">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="7edd7-114">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="7edd7-114">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7edd7-115">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7edd7-115">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="7edd7-116">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="7edd7-116">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7edd7-117">En-tête</span><span class="sxs-lookup"><span data-stu-id="7edd7-117">Header</span></span></p></td>
<td><span data-ttu-id="7edd7-118">WinConTypes. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="7edd7-118">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="7edd7-119"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7edd7-119"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="7edd7-120">**enregistrement d’entrée \_**</span><span class="sxs-lookup"><span data-stu-id="7edd7-120">**INPUT\_RECORD**</span></span>](input-record-str.md)

 

 




