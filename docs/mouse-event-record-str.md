---
title: Structure MOUSE_EVENT_RECORD
description: Consultez les informations de référence sur la structure MOUSE_EVENT_RECORD, qui décrit un événement d’entrée de souris dans une structure de INPUT_RECORD de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- wincontypes/MOUSE_EVENT_RECORD
- wincon/MOUSE_EVENT_RECORD
- MOUSE_EVENT_RECORD
- wincontypes/PMOUSE_EVENT_RECORD
- wincon/PMOUSE_EVENT_RECORD
- PMOUSE_EVENT_RECORD
MS-HAID:
- '\_win32\_mouse\_event\_record\_str'
- base.mouse\_event\_record\_str
- consoles.mouse\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ea54c6-8872-4111-8d72-1377409b9247
topic_type:
- apiref
api_name:
- MOUSE_EVENT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: a3e95e9d35cdf2af2ec6836021dd8819323a4790
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059061"
---
# <a name="mouse_event_record-structure"></a>Structure d’enregistrement d' \_ événement de souris \_


Décrit un événement d’entrée de souris dans une structure [**d' \_ enregistrement d’entrée**](input-record-str.md) de console.

<a name="syntax"></a>Syntaxe
------

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

<a name="members"></a>Membres
-------

**dwMousePosition**  
Structure de [**repère**](coord-str.md) qui contient l’emplacement du curseur, en termes de coordonnées des cellules de caractères de la mémoire tampon de l’écran de la console.

**dwButtonState**  
État des boutons de la souris. Le bit le moins significatif correspond au bouton le plus à gauche de la souris. Le bit le moins significatif suivant correspond au bouton le plus à droite de la souris. Le bit suivant indique le bouton de la souris situé à l’extrême gauche. Les bits correspondent ensuite de gauche à droite aux boutons de la souris. Un bit est 1 si le bouton a été enfoncé.

Les constantes suivantes sont définies pour les cinq premiers boutons de la souris.

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
<td><span id="FROM_LEFT_1ST_BUTTON_PRESSED"></span><span id="from_left_1st_button_pressed"></span>
<strong>FROM_LEFT_1ST_BUTTON_PRESSED</strong> 0x0001</td>
<td><p>Le bouton gauche de la souris.</p></td>
</tr>
<tr class="even">
<td><span id="FROM_LEFT_2ND_BUTTON_PRESSED"></span><span id="from_left_2nd_button_pressed"></span>
<strong>FROM_LEFT_2ND_BUTTON_PRESSED</strong> 0x0004</td>
<td><p>Deuxième bouton à partir de la gauche.</p></td>
</tr>
<tr class="odd">
<td><span id="FROM_LEFT_3RD_BUTTON_PRESSED"></span><span id="from_left_3rd_button_pressed"></span>
<strong>FROM_LEFT_3RD_BUTTON_PRESSED</strong> 0x0008</td>
<td><p>Troisième bouton à partir de la gauche.</p></td>
</tr>
<tr class="even">
<td><span id="FROM_LEFT_4TH_BUTTON_PRESSED"></span><span id="from_left_4th_button_pressed"></span>
<strong>FROM_LEFT_4TH_BUTTON_PRESSED</strong> 0x0010</td>
<td><p>Quatrième bouton à partir de la gauche.</p></td>
</tr>
<tr class="odd">
<td><span id="RIGHTMOST_BUTTON_PRESSED"></span><span id="rightmost_button_pressed"></span>
<strong>RIGHTMOST_BUTTON_PRESSED</strong> 0x0002</td>
<td><p>Bouton de la souris le plus à droite.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

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

 

**dwEventFlags**  
Type d’événement de souris. Si cette valeur est égale à zéro, elle indique qu’un bouton de la souris est enfoncé ou relâché. Dans le cas contraire, ce membre est l’une des valeurs suivantes.

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
<td><span id="DOUBLE_CLICK"></span><span id="double_click"></span>
<strong>DOUBLE_CLICK</strong> 0x0002</td>
<td><p>Le deuxième clic (appuyez sur le bouton) d’un double-clic s’est produit. Le premier clic est retourné en tant qu’événement de bouton-pression standard.</p></td>
</tr>
<tr class="even">
<td><span id="MOUSE_HWHEELED"></span><span id="mouse_hwheeled"></span>
<strong>MOUSE_HWHEELED</strong> 0x0008</td>
<td><p>La roulette horizontale de la souris a été déplacée.</p>
<p>Si le mot de poids fort du membre <strong>dwButtonState</strong> contient une valeur positive, la roulette a été pivotée vers la droite. Dans le cas contraire, la roulette a été pivotée vers la gauche.</p></td>
</tr>
<tr class="odd">
<td><span id="MOUSE_MOVED"></span><span id="mouse_moved"></span>
<strong>MOUSE_MOVED</strong> 0x0001</td>
<td><p>Une modification de la position de la souris s’est produite.</p></td>
</tr>
<tr class="even">
<td><span id="MOUSE_WHEELED"></span><span id="mouse_wheeled"></span>
<strong>MOUSE_WHEELED</strong> 0x0004</td>
<td><p>La roulette verticale de la souris a été déplacée.</p>
<p>Si le mot de poids fort du membre <strong>dwButtonState</strong> contient une valeur positive, la roulette a été pivotée vers l’avant, en dehors de l’utilisateur. Dans le cas contraire, la roulette a été tournée vers l’arrière de l’utilisateur.</p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="remarks"></a>Remarques
-------

Les événements de souris sont placés dans la mémoire tampon d’entrée lorsque la console est en mode souris (**activer l' \_ \_ entrée de la souris**).

Les événements de souris sont générés chaque fois que l’utilisateur déplace la souris, ou appuie sur ou relâche l’un des boutons de la souris. Les événements de souris sont placés dans la mémoire tampon d’entrée d’une console uniquement lorsque le groupe de la console a le focus clavier et que le curseur se trouve dans les limites de la fenêtre de la console.

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


[**COORDONNÉES**](coord-str.md)

[**enregistrement d’entrée \_**](input-record-str.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

 

 




