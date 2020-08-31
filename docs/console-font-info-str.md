---
title: Structure CONSOLE_FONT_INFO
description: Consultez les informations de référence sur la structure CONSOLE_FONT_INFO, qui contient l’index et la taille d’une police de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- wincontypes/CONSOLE_FONT_INFO
- wincon/CONSOLE_FONT_INFO
- CONSOLE_FONT_INFO
- wincontypes/PCONSOLE_FONT_INFO
- wincon/PCONSOLE_FONT_INFO
- PCONSOLE_FONT_INFO
MS-HAID:
- '\_win32\_console\_font\_info\_str'
- base.console\_font\_info\_str
- consoles.console\_font\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 380b8183-1964-46f2-a511-01f39f21f5c5
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: c4218c53eacd95d67f3dc9056f5a1024ac1a8ab0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059333"
---
# <a name="console_font_info-structure"></a>Structure des informations de \_ police de la console \_


Contient des informations pour une police de console.

<a name="syntax"></a>Syntaxe
------

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

<a name="members"></a>Membres
-------

**nFont**  
Index de la police dans la table des polices de la console du système.

**dwFontSize**  
Structure de [**repère**](coord-str.md) qui contient la largeur et la hauteur de chaque caractère de la police, en unités logiques. Le membre **X** contient la largeur, tandis que le membre **Y** contient la hauteur.

<a name="remarks"></a>Remarques
-------

Pour obtenir la taille de la police, transmettez l’index de la police à la fonction [**GetConsoleFontSize**](getconsolefontsize.md) .

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
<td>Wincon. h (inclure Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Voir aussi


[**COORDONNÉES**](coord-str.md)

[**GetCurrentConsoleFont**](getcurrentconsolefont.md)

 

 




