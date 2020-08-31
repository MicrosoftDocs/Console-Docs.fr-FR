---
title: Structure CONSOLE_SELECTION_INFO
description: Consultez les informations de référence sur la structure CONSOLE_SELECTION_INFO, qui contient des informations pour une sélection de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/CONSOLE_SELECTION_INFO
- wincon/CONSOLE_SELECTION_INFO
- CONSOLE_SELECTION_INFO
- consoleapi3/PCONSOLE_SELECTION_INFO
- wincon/PCONSOLE_SELECTION_INFO
- PCONSOLE_SELECTION_INFO
MS-HAID:
- '\_win32\_console\_selection\_info\_str'
- base.console\_selection\_info\_str
- consoles.console\_selection\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9530b249-8db4-4516-9cc8-2b452c6751f9
topic_type:
- apiref
api_name:
- CONSOLE_SELECTION_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: a16fe43e7b7cc4b5890284921823aee7b79217b2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059269"
---
# <a name="console_selection_info-structure"></a>Structure des informations de \_ sélection de la console \_


Contient des informations pour une sélection de la console.

<a name="syntax"></a>Syntaxe
------

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

<a name="members"></a>Membres
-------

**dwFlags**  
Indicateur de sélection. Ce membre peut être une ou plusieurs des valeurs suivantes.

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
<td><span id="CONSOLE_MOUSE_DOWN"></span><span id="console_mouse_down"></span>
<strong>CONSOLE_MOUSE_DOWN</strong> 0x0008</td>
<td><p>La souris est inactive</p></td>
</tr>
<tr class="even">
<td><span id="CONSOLE_MOUSE_SELECTION"></span><span id="console_mouse_selection"></span>
<strong>CONSOLE_MOUSE_SELECTION</strong> 0x0004</td>
<td><p>Sélection à l’aide de la souris</p></td>
</tr>
<tr class="odd">
<td><span id="CONSOLE_NO_SELECTION"></span><span id="console_no_selection"></span>
<strong>CONSOLE_NO_SELECTION</strong> 0x0000</td>
<td><p>Aucune sélection</p></td>
</tr>
<tr class="even">
<td><span id="CONSOLE_SELECTION_IN_PROGRESS"></span><span id="console_selection_in_progress"></span>
<strong>CONSOLE_SELECTION_IN_PROGRESS</strong> 0x0001</td>
<td><p>La sélection a commencé</p></td>
</tr>
<tr class="odd">
<td><span id="CONSOLE_SELECTION_NOT_EMPTY"></span><span id="console_selection_not_empty"></span>
<strong>CONSOLE_SELECTION_NOT_EMPTY</strong> 0x0002</td>
<td><p>Le rectangle de sélection n’est pas vide</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

**dwSelectionAnchor**  
Structure de [**repère**](coord-str.md) qui spécifie l’ancre de sélection, en caractères.

**srSelection**  
[**Petite structure \_ Rect**](small-rect-str.md) qui spécifie le rectangle de sélection.

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
<td><p>Windows XP [applications de bureau uniquement]</p></td>
</tr>
<tr class="even">
<td><p>Serveur minimal pris en charge</p></td>
<td><p>Windows Server 2003 [applications de bureau uniquement]</p></td>
</tr>
<tr class="odd">
<td><p>En-tête</p></td>
<td>ConsoleApi3. h (via wincon. h, incluez Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Voir aussi


[**COORDONNÉES**](coord-str.md)

[**GetConsoleSelectionInfo**](getconsoleselectioninfo.md)

[**PETIT \_ Rect**](small-rect-str.md)

 

 




