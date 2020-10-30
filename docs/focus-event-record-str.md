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
# <a name="focus_event_record-structure"></a>Structure d’enregistrement d' \_ événement de focus \_

Décrit un événement de focus dans une structure [**d' \_ enregistrement d’entrée**](input-record-str.md) de console. Ces événements sont utilisés en interne et doivent être ignorés.

## <a name="syntax"></a>Syntaxe

```C
typedef struct _FOCUS_EVENT_RECORD {
  BOOL bSetFocus;
} FOCUS_EVENT_RECORD;
```

## <a name="members"></a>Membres

**bSetFocus**  
Réservé.

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | WinConTypes. h (via WinCon. h, incluez Windows. h) |

## <a name="see-also"></a>Voir aussi

[**enregistrement d’entrée \_**](input-record-str.md)
