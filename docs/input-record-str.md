---
title: INPUT_RECORD, structure
description: Consultez les informations de référence sur la structure INPUT_RECORD, qui décrit un événement d’entrée dans la mémoire tampon d’entrée de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- wincontypes/INPUT_RECORD
- wincon/INPUT_RECORD
- INPUT_RECORD
- wincontypes/PINPUT_RECORD
- wincon/PINPUT_RECORD
- PINPUT_RECORD
MS-HAID:
- '\_win32\_input\_record\_str'
- base.input\_record\_str
- consoles.input\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a46ba7fd-097a-455d-96ac-13aa01e11dc1
topic_type:
- apiref
api_name:
- INPUT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4ad86de170c1fef74f133a5d5c51d8de2dea497f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038537"
---
# <a name="input_record-structure"></a>Structure d’enregistrement d’entrée \_

Décrit un événement d’entrée dans la mémoire tampon d’entrée de la console. Ces enregistrements peuvent être lus à partir de la mémoire tampon d’entrée à l’aide de la fonction [**ReadConsoleInput**](readconsoleinput.md) ou [**PeekConsoleInput**](peekconsoleinput.md) , ou être écrits dans la mémoire tampon d’entrée à l’aide de la fonction [**WriteConsoleInput**](writeconsoleinput.md) .

## <a name="syntax"></a>Syntaxe

```C
typedef struct _INPUT_RECORD {
  WORD  EventType;
  union {
    KEY_EVENT_RECORD          KeyEvent;
    MOUSE_EVENT_RECORD        MouseEvent;
    WINDOW_BUFFER_SIZE_RECORD WindowBufferSizeEvent;
    MENU_EVENT_RECORD         MenuEvent;
    FOCUS_EVENT_RECORD        FocusEvent;
  } Event;
} INPUT_RECORD;
```

## <a name="members"></a>Membres

**EventType**  
Handle du type d’événement d’entrée et de l’enregistrement d’événement stocké dans le membre d' **événement** .

Ce membre peut être l’une des valeurs suivantes.

| Valeur | Signification |
|-|-|
| **FOCUS_EVENT** 0x0010 | Le membre d' **événement** contient une structure **[FOCUS_EVENT_RECORD](focus-event-record-str.md)** . Ces événements sont utilisés en interne et doivent être ignorés. |
| **KEY_EVENT** 0x0001 | Le membre d' **événement** contient une structure **[KEY_EVENT_RECORD](key-event-record-str.md)** avec des informations sur un événement de clavier. |
| **MENU_EVENT** 0x0008 | Le membre d' **événement** contient une structure **[MENU_EVENT_RECORD](menu-event-record-str.md)** . Ces événements sont utilisés en interne et doivent être ignorés. |
| **MOUSE_EVENT** 0x0002 | Le membre d' **événement** contient une structure **[MOUSE_EVENT_RECORD](mouse-event-record-str.md)** avec des informations sur un déplacement de la souris ou un événement d’enfoncement du bouton. |
| **WINDOW_BUFFER_SIZE_EVENT** 0x0004 | Le membre d' **événement** contient une structure **[WINDOW_BUFFER_SIZE_RECORD](window-buffer-size-record-str.md)** avec des informations sur la nouvelle taille de la mémoire tampon d’écran de la console. |

**Event**  
Informations d'événement. Le format de ce membre dépend du type d’événement spécifié par le membre **eventType** .

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | WinConTypes. h (via WinCon. h, incluez Windows. h) |

## <a name="see-also"></a>Voir aussi

[**FOCUS \_ , \_ enregistrement d’événement**](focus-event-record-str.md)

[**\_enregistrement d’événement clé \_**](key-event-record-str.md)

[**\_enregistrement d’événement de menu \_**](menu-event-record-str.md)

[**\_enregistrement d’événement de souris \_**](mouse-event-record-str.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)
