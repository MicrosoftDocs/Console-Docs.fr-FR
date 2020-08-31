---
title: Structure CONSOLE_CURSOR_INFO
description: Contient les informations relatives à la taille et à la visibilité sur le curseur de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- wincontypes/CONSOLE_CURSOR_INFO
- wincon/CONSOLE_CURSOR_INFO
- CONSOLE_CURSOR_INFO
- wincontypes/PCONSOLE_CURSOR_INFO
- wincon/PCONSOLE_CURSOR_INFO
- PCONSOLE_CURSOR_INFO
MS-HAID:
- '\_win32\_console\_cursor\_info\_str'
- base.console\_cursor\_info\_str
- consoles.console\_cursor\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0e71ce8c-e008-4bd7-922e-c44484b425ef
topic_type:
- apiref
api_name:
- CONSOLE_CURSOR_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 0ac3eb459810f2c8ebc861759312350a487abd3c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059336"
---
# <a name="console_cursor_info-structure"></a>Structure des informations du \_ curseur de la console \_


Contient des informations sur le curseur de la console.

<a name="syntax"></a>Syntaxe
------

```C
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

<a name="members"></a>Membres
-------

**dwSize nul**  
Pourcentage de la cellule de caractère qui est rempli par le curseur. Cette valeur est comprise entre 1 et 100. L’apparence du curseur varie, du remplissage complet de la cellule à l’affichage sous la forme d’une ligne horizontale au bas de la cellule.

**Remarque**    Alors que la valeur **dwSize nul** est normalement comprise entre 1 et 100, dans certains cas, une valeur en dehors de cette plage peut être retournée. Par exemple, si **CursorSize** est défini sur 0 dans le registre, la valeur **dwSize nul** retournée est 0.

 

**bVisible**  
Visibilité du curseur. Si le curseur est visible, ce membre a la **valeur true**.

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


[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**SetConsoleCursorInfo**](setconsolecursorinfo.md)

 

 




