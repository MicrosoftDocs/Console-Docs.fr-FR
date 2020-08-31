---
title: Structure KEY_EVENT_RECORD
description: Décrit un événement d’entrée au clavier dans une structure d’enregistrement d’entrée de console \_ .
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: fd7386d5796442d34cdaa29fcf52831bc6aa1d78
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059480"
---
# <a name="key_event_record-structure"></a>Structure d’enregistrement d' \_ événement clé \_


Décrit un événement d’entrée au clavier dans une structure [**d' \_ enregistrement d’entrée**](input-record-str.md) de console.

<a name="syntax"></a>Syntaxe
------

```C
typedef struct _KEY_EVENT_RECORD {
  BOOL  bKeyDown;
  WORD  wRepeatCount;
  WORD  wVirtualKeyCode;
  WORD  wVirtualScanCode;
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } uChar;
  DWORD dwControlKeyState;
} KEY_EVENT_RECORD;
```

<a name="members"></a>Membres
-------

**bKeyDown**  
Si la touche est enfoncée, ce membre a la **valeur true**. Dans le cas contraire, ce membre a la **valeur false** (la touche est relâchée).

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
<td><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</td>
<td><p>Le voyant Verr. MAJ est activé.</p></td>
</tr>
<tr class="even">
<td><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</td>
<td><p>La clé est améliorée.</p></td>
</tr>
<tr class="odd">
<td><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</td>
<td><p>La touche ALT de gauche est enfoncée.</p></td>
</tr>
<tr class="even">
<td><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</td>
<td><p>La touche CTRL de gauche est enfoncée.</p></td>
</tr>
<tr class="odd">
<td><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</td>
<td><p>La diode Verr. NUM est activée.</p></td>
</tr>
<tr class="even">
<td><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</td>
<td><p>La touche ALT de droite est enfoncée.</p></td>
</tr>
<tr class="odd">
<td><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</td>
<td><p>La touche CTRL de droite est enfoncée.</p></td>
</tr>
<tr class="even">
<td><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</td>
<td><p>Le voyant du verrou de défilement est activé.</p></td>
</tr>
<tr class="odd">
<td><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</td>
<td><p>La touche Maj est enfoncée.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="remarks"></a>Remarques
-------

Les clés améliorées pour les claviers IBM® 101 et 102 sont les touches Inser, DEL, début, fin, PAGE précédente, PAGE suivante et direction dans les clusters à gauche du pavé numérique. et les touches de division (/) et de saisie dans le clavier.

Les événements d’entrée au clavier sont générés lorsqu’une touche, y compris des touches de contrôle, est enfoncée ou libérée. Toutefois, la touche ALT enfoncée et libérée sans combiner avec un autre caractère a une signification particulière pour le système et n’est pas transmise à l’application. En outre, la combinaison de touches CTRL + C n’est pas transmise si le handle d’entrée est en mode traité (**activer l' \_ \_ entrée traitée**).

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


[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

[**enregistrement d’entrée \_**](input-record-str.md)

 

 




