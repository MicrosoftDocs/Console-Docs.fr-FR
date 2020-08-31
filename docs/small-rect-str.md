---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- wincontypes/SMALL_RECT
- wincon/SMALL_RECT
- SMALL_RECT
title: Structure SMALL_RECT
description: Définit les coordonnées des angles supérieur gauche et inférieur droit d’un rectangle.
MS-HAID:
- '\_win32\_small\_rect\_str'
- base.small\_rect\_str
- consoles.small\_rect\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 62639815-c7e9-4ae2-b152-61290f78422b
topic_type:
- apiref
api_name:
- SMALL_RECT
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: b0c0bfe93c85af89c5aaefeda032795de72ed627
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060558"
---
# <a name="small_rect-structure"></a>PETITE \_ structure Rect


Définit les coordonnées des angles supérieur gauche et inférieur droit d’un rectangle.

<a name="syntax"></a>Syntaxe
------

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

<a name="members"></a>Membres
-------

**Left**  
Coordonnée x de l’angle supérieur gauche du rectangle.

**Top**  
Coordonnée y de l’angle supérieur gauche du rectangle.

**Right**  
Coordonnée x du coin inférieur droit du rectangle.

**Bas**  
Coordonnée y du coin inférieur droit du rectangle.

<a name="remarks"></a>Remarques
-------

Cette structure est utilisée par les fonctions de la console pour spécifier les zones rectangulaires des mémoires tampons d’écran de la console, où les coordonnées spécifient les lignes et les colonnes des cellules de caractères de la mémoire tampon d’écran.

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
<td>WinConTypes. h (via wincon. h, incluez Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Voir aussi


[**RECTANGULAIRE**](https://msdn.microsoft.com/library/windows/desktop/dd162897)

[**RECTo**](https://msdn.microsoft.com/library/windows/desktop/dd162907)

 

 




