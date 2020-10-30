---
title: KEY_EVENT_RECORD, structure
description: Décrit un événement d’entrée au clavier dans une structure d’enregistrement d’entrée de console \_ .
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- wincontypes/KEY_EVENT_RECORD
- wincon/KEY_EVENT_RECORD
- KEY_EVENT_RECORD
- wincontypes/PKEY_EVENT_RECORD
- wincon/PKEY_EVENT_RECORD
- PKEY_EVENT_RECORD
MS-HAID:
- '\_win32\_key\_event\_record\_str'
- base.key\_event\_record\_str
- consoles.key\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b3fed86b-84ef-48e4-97e1-cb3d65f714a7
topic_type:
- apiref
api_name:
- KEY_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 0a2ba8ecf8b07a83db54642c2399bb93d99b7aa2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039527"
---
# <a name="key_event_record-structure"></a>Structure d’enregistrement d' \_ événement clé \_

Décrit un événement d’entrée au clavier dans une structure [**d' \_ enregistrement d’entrée**](input-record-str.md) de console.

## <a name="syntax"></a>Syntaxe

```C
typedef struct _KEY_EVENT_RECORD {
  BOOL  bKeyDown;
  WORD  wRepeatCount;
  WORD  wVirtualKeyCode;
  WORD  wVirtualScanCode;
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } uChar;
  DWORD dwControlKeyState;
} KEY_EVENT_RECORD;
```

## <a name="members"></a>Membres

**bKeyDown**  
Si la touche est enfoncée, ce membre a la **valeur true** . Dans le cas contraire, ce membre a la **valeur false** (la touche est relâchée).

**wRepeatCount**  
Nombre de répétitions, qui indique qu’une touche est maintenue enfoncée. Par exemple, lorsqu’une touche est maintenue enfoncée, vous pouvez obtenir cinq événements avec ce membre égal à 1, un événement avec ce membre égal à 5 ou plusieurs événements avec ce membre supérieur ou égal à 1.

**wVirtualKeyCode**  
[Code de clé virtuelle](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) qui identifie la clé donnée de façon indépendante du périphérique.

**wVirtualScanCode**  
Code d’analyse virtuelle de la clé donnée qui représente la valeur dépendante de l’appareil générée par le matériel clavier.

**uChar**  
Union des membres suivants.

**UnicodeChar**  
Caractère Unicode traduit.

**AsciiChar**  
Caractère ASCII traduit.

**dwControlKeyState**  
État des touches de contrôle. Ce membre peut être une ou plusieurs des valeurs suivantes.

| Valeur | Signification |
|-|-|
| **CAPSLOCK_ON** 0x0080 | Le voyant Verr. MAJ est activé. |
| **ENHANCED_KEY** 0x0100 | La clé est améliorée. Consultez la [section Notes](key-event-record-str.md#remarks). |
| **LEFT_ALT_PRESSED** 0x0002 | La touche ALT de gauche est enfoncée. |
| **LEFT_CTRL_PRESSED** 0x0008 | La touche CTRL de gauche est enfoncée. |
| **NUMLOCK_ON** 0x0020 | La diode Verr. NUM est activée. |
| **RIGHT_ALT_PRESSED** 0x0001 | La touche ALT de droite est enfoncée. |
| **RIGHT_CTRL_PRESSED** 0x0004 | La touche CTRL de droite est enfoncée. |
| **SCROLLLOCK_ON** 0x0040 | Le voyant du verrou de défilement est activé. |
| **SHIFT_PRESSED** 0x0010 | La touche Maj est enfoncée. |

## <a name="remarks"></a>Remarques

Les clés améliorées pour les claviers IBM® 101 et 102 sont les touches Inser, DEL, début, fin, PAGE précédente, PAGE suivante et direction dans les clusters à gauche du pavé numérique. et les touches de division (/) et de saisie dans le clavier.

Les événements d’entrée au clavier sont générés lorsqu’une touche, y compris des touches de contrôle, est enfoncée ou libérée. Toutefois, la touche ALT enfoncée et libérée sans combiner avec un autre caractère a une signification particulière pour le système et n’est pas transmise à l’application. En outre, la combinaison de touches CTRL + C n’est pas transmise si le handle d’entrée est en mode traité ( **activer l' \_ \_ entrée traitée** ).

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | WinConTypes. h (via WinCon. h, incluez Windows. h) |

## <a name="see-also"></a>Voir aussi

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

[**enregistrement d’entrée \_**](input-record-str.md)
