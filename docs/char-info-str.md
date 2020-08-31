---
title: Structure CHAR_INFO
description: Spécifie un caractère Unicode ou ANSI et ses attributs. Cette structure est utilisée par les fonctions de la console pour lire et écrire dans une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- wincontypes/CHAR_INFO
- wincon/CHAR_INFO
- CHAR_INFO
- wincontypes/PCHAR_INFO
- wincon/PCHAR_INFO
- PCHAR_INFO
MS-HAID:
- '\_win32\_char\_info\_str'
- base.char\_info\_str
- consoles.char\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5574a862-b262-41af-8862-e9837c5c7b5f
topic_type:
- apiref
api_name:
- CHAR_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 6244edaa06b6dd69f8ab3962cf42cb893d08f699
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059373"
---
# <a name="char_info-structure"></a>CHAR \_ info (structure)


Spécifie un caractère Unicode ou ANSI et ses attributs. Cette structure est utilisée par les fonctions de la console pour lire et écrire dans une mémoire tampon d’écran de la console.

<a name="syntax"></a>Syntaxe
------

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

<a name="members"></a>Membres
-------

**Char**  
Union des membres suivants.

**UnicodeChar**  
Caractère Unicode d’une cellule de caractère de mémoire tampon d’écran.

**AsciiChar**  
Caractère ANSI d’une cellule de caractère de mémoire tampon d’écran.

**Attributs**  
Attributs de caractère. Ce membre peut être égal à zéro ou n’importe quelle combinaison des valeurs suivantes.

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
<td><span id="FOREGROUND_BLUE"></span><span id="foreground_blue"></span>
<strong>FOREGROUND_BLUE</strong> 0x0001</td>
<td><p>La couleur du texte contient le bleu.</p></td>
</tr>
<tr class="even">
<td><span id="FOREGROUND_GREEN"></span><span id="foreground_green"></span>
<strong>FOREGROUND_GREEN</strong> 0x0002</td>
<td><p>La couleur du texte contient du vert.</p></td>
</tr>
<tr class="odd">
<td><span id="FOREGROUND_RED"></span><span id="foreground_red"></span>
<strong>FOREGROUND_RED</strong> 0x0004</td>
<td><p>La couleur du texte contient le rouge.</p></td>
</tr>
<tr class="even">
<td><span id="FOREGROUND_INTENSITY"></span><span id="foreground_intensity"></span>
<strong>FOREGROUND_INTENSITY</strong> 0x0008</td>
<td><p>La couleur du texte est intensifiée.</p></td>
</tr>
<tr class="odd">
<td><span id="BACKGROUND_BLUE"></span><span id="background_blue"></span>
<strong>BACKGROUND_BLUE</strong> 0x0010</td>
<td><p>La couleur d’arrière-plan contient le bleu.</p></td>
</tr>
<tr class="even">
<td><span id="BACKGROUND_GREEN"></span><span id="background_green"></span>
<strong>BACKGROUND_GREEN</strong> 0x0020</td>
<td><p>La couleur d’arrière-plan contient du vert.</p></td>
</tr>
<tr class="odd">
<td><span id="BACKGROUND_RED"></span><span id="background_red"></span>
<strong>BACKGROUND_RED</strong> 0x0040</td>
<td><p>La couleur d’arrière-plan contient le rouge.</p></td>
</tr>
<tr class="even">
<td><span id="BACKGROUND_INTENSITY"></span><span id="background_intensity"></span>
<strong>BACKGROUND_INTENSITY</strong> 0x0080</td>
<td><p>La couleur d’arrière-plan est intensifiée.</p></td>
</tr>
<tr class="odd">
<td><span id="COMMON_LVB_LEADING_BYTE"></span><span id="common_lvb_leading_byte"></span>
<strong>COMMON_LVB_LEADING_BYTE</strong> 0x0100</td>
<td><p>Octet de début.</p></td>
</tr>
<tr class="even">
<td><span id="COMMON_LVB_TRAILING_BYTE"></span><span id="common_lvb_trailing_byte"></span>
<strong>COMMON_LVB_TRAILING_BYTE</strong> 0x0200</td>
<td><p>Octet de fin.</p></td>
</tr>
<tr class="odd">
<td><span id="COMMON_LVB_GRID_HORIZONTAL"></span><span id="common_lvb_grid_horizontal"></span>
<strong>COMMON_LVB_GRID_HORIZONTAL</strong> 0x0400</td>
<td><p>Horizontal supérieur</p></td>
</tr>
<tr class="even">
<td><span id="COMMON_LVB_GRID_LVERTICAL"></span><span id="common_lvb_grid_lvertical"></span>
<strong>COMMON_LVB_GRID_LVERTICAL</strong> 0x0800</td>
<td><p>Vertical gauche.</p></td>
</tr>
<tr class="odd">
<td><span id="COMMON_LVB_GRID_RVERTICAL"></span><span id="common_lvb_grid_rvertical"></span>
<strong>COMMON_LVB_GRID_RVERTICAL</strong> 0x1000</td>
<td><p>Verticale droite.</p></td>
</tr>
<tr class="even">
<td><span id="COMMON_LVB_REVERSE_VIDEO"></span><span id="common_lvb_reverse_video"></span>
<strong>COMMON_LVB_REVERSE_VIDEO</strong> 0x4000</td>
<td><p>Attribut de premier plan et d’arrière-plan inversé.</p></td>
</tr>
<tr class="odd">
<td><span id="COMMON_LVB_UNDERSCORE"></span><span id="common_lvb_underscore"></span>
<strong>COMMON_LVB_UNDERSCORE</strong> 0x8000</td>
<td><p>Soulignement.</p></td>
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

 

<a name="examples"></a>Exemples
--------

Pour obtenir un exemple, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).

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
<td>Wincon. h (inclure Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Voir aussi


[**ReadConsoleOutput**](readconsoleoutput.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

 

 




