---
title: Structure WINDOW_BUFFER_SIZE_RECORD
description: Consultez les informations de référence sur la structure WINDOW_BUFFER_SIZE_RECORD, qui décrit une modification de la taille de la mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- wincontypes/WINDOW_BUFFER_SIZE_RECORD
- wincon/WINDOW_BUFFER_SIZE_RECORD
- WINDOW_BUFFER_SIZE_RECORD
- wincontypes/PWINDOW_BUFFER_SIZE_RECORD
- wincon/PWINDOW_BUFFER_SIZE_RECORD
- PWINDOW_BUFFER_SIZE_RECORD
MS-HAID:
- '\_win32\_window\_buffer\_size\_record\_str'
- base.window\_buffer\_size\_record\_str
- consoles.window\_buffer\_size\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f2875e8-aa09-455b-a923-7cc388525b98
topic_type:
- apiref
api_name:
- WINDOW_BUFFER_SIZE_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 0041c4390fe331302df458965faec0ace2d1888f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060543"
---
# <a name="window_buffer_size_record-structure"></a>\_Structure d' \_ enregistrement de taille de mémoire tampon de fenêtre \_


Décrit une modification de la taille de la mémoire tampon d’écran de la console.

<a name="syntax"></a>Syntaxe
------

```C
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

<a name="members"></a>Membres
-------

**dwSize nul**  
Structure de [**repère**](coord-str.md) qui contient la taille de la mémoire tampon de l’écran de la console, dans les colonnes et les lignes des cellules de caractères.

<a name="remarks"></a>Remarques
-------

Les événements de taille de mémoire tampon sont placés dans la mémoire tampon d’entrée lorsque la console est en mode compatible avec les fenêtres (**activer l' \_ \_ entrée**de la fenêtre).

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

[**ReadConsoleInput**](readconsoleinput.md)

 

 




