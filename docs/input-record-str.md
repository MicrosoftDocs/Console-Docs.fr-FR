---
title: Structure INPUT_RECORD
description: Consultez les informations de référence sur la structure INPUT_RECORD, qui décrit un événement d’entrée dans la mémoire tampon d’entrée de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 5d532b5a009681e650991fd083f7d6ab932a05da
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059485"
---
# <a name="input_record-structure"></a>Structure d’enregistrement d’entrée \_


Décrit un événement d’entrée dans la mémoire tampon d’entrée de la console. Ces enregistrements peuvent être lus à partir de la mémoire tampon d’entrée à l’aide de la fonction [**ReadConsoleInput**](readconsoleinput.md) ou [**PeekConsoleInput**](peekconsoleinput.md) , ou être écrits dans la mémoire tampon d’entrée à l’aide de la fonction [**WriteConsoleInput**](writeconsoleinput.md) .

<a name="syntax"></a>Syntaxe
------

```C
typedef struct _INPUT_RECORD {
  WORD  EventType;
  union {
    KEY_EVENT_RECORD          KeyEvent;
    MOUSE_EVENT_RECORD        MouseEvent;
    WINDOW_BUFFER_SIZE_RECORD WindowBufferSizeEvent;
    MENU_EVENT_RECORD         MenuEvent;
    FOCUS_EVENT_RECORD        FocusEvent;
  } Event;
} INPUT_RECORD;
```

<a name="members"></a>Membres
-------

**EventType**  
Handle du type d’événement d’entrée et de l’enregistrement d’événement stocké dans le membre d' **événement** .

Ce membre peut être l’une des valeurs suivantes.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Value</th>
<th>Signification</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="FOCUS_EVENT"></span><span id="focus_event"></span>
<strong>FOCUS_EVENT</strong> 0x0010</td>
<td><p>Le membre d' <strong>événement</strong> contient une structure <a href="focus-event-record-str.md" data-raw-source="[&lt;strong&gt;FOCUS_EVENT_RECORD&lt;/strong&gt;](focus-event-record-str.md)"><strong>FOCUS_EVENT_RECORD</strong></a> . Ces événements sont utilisés en interne et doivent être ignorés.</p></td>
</tr>
<tr class="even">
<td><span id="KEY_EVENT"></span><span id="key_event"></span>
<strong>KEY_EVENT</strong> 0x0001</td>
<td><p>Le membre d' <strong>événement</strong> contient une structure <a href="key-event-record-str.md" data-raw-source="[&lt;strong&gt;KEY_EVENT_RECORD&lt;/strong&gt;](key-event-record-str.md)"><strong>KEY_EVENT_RECORD</strong></a> avec des informations sur un événement de clavier.</p></td>
</tr>
<tr class="odd">
<td><span id="MENU_EVENT"></span><span id="menu_event"></span>
<strong>MENU_EVENT</strong> 0x0008</td>
<td><p>Le membre d' <strong>événement</strong> contient une structure <a href="menu-event-record-str.md" data-raw-source="[&lt;strong&gt;MENU_EVENT_RECORD&lt;/strong&gt;](menu-event-record-str.md)"><strong>MENU_EVENT_RECORD</strong></a> . Ces événements sont utilisés en interne et doivent être ignorés.</p></td>
</tr>
<tr class="even">
<td><span id="MOUSE_EVENT"></span><span id="mouse_event"></span>
<strong>MOUSE_EVENT</strong> 0x0002</td>
<td><p>Le membre d' <strong>événement</strong> contient une structure <a href="mouse-event-record-str.md" data-raw-source="[&lt;strong&gt;MOUSE_EVENT_RECORD&lt;/strong&gt;](mouse-event-record-str.md)"><strong>MOUSE_EVENT_RECORD</strong></a> avec des informations sur un déplacement de la souris ou un événement d’enfoncement du bouton.</p></td>
</tr>
<tr class="odd">
<td><span id="WINDOW_BUFFER_SIZE_EVENT"></span><span id="window_buffer_size_event"></span>
<strong>WINDOW_BUFFER_SIZE_EVENT</strong> 0x0004</td>
<td><p>Le membre d' <strong>événement</strong> contient une structure <a href="window-buffer-size-record-str.md" data-raw-source="[&lt;strong&gt;WINDOW_BUFFER_SIZE_RECORD&lt;/strong&gt;](window-buffer-size-record-str.md)"><strong>WINDOW_BUFFER_SIZE_RECORD</strong></a> avec des informations sur la nouvelle taille de la mémoire tampon d’écran de la console.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

**Event**  
Informations d'événement. Le format de ce membre dépend du type d’événement spécifié par le membre **eventType** .

<a name="examples"></a>Exemples
--------

Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).

<a name="requirements"></a>Configuration requise
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Client minimal pris en charge</p></td>
<td><p>Windows 2000 professionnel [applications de bureau uniquement]</p></td>
</tr>
<tr class="even">
<td><p>Serveur minimal pris en charge</p></td>
<td><p>Serveur Windows 2000 [applications de bureau uniquement]</p></td>
</tr>
<tr class="odd">
<td><p>En-tête</p></td>
<td>WinConTypes. h (via wincon. h, incluez Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Voir aussi


[**FOCUS \_ , \_ enregistrement d’événement**](focus-event-record-str.md)

[**\_enregistrement d’événement clé \_**](key-event-record-str.md)

[**\_enregistrement d’événement de menu \_**](menu-event-record-str.md)

[**\_enregistrement d’événement de souris \_**](mouse-event-record-str.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

 

 




