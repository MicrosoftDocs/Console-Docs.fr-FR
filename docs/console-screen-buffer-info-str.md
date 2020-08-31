---
title: Structure CONSOLE_SCREEN_BUFFER_INFO
description: Consultez les informations de référence sur la structure CONSOLE_SCREEN_BUFFER_INFO, qui contient des informations sur une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFO
- wincon/CONSOLE_SCREEN_BUFFER_INFO
- CONSOLE_SCREEN_BUFFER_INFO
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFO
- wincon/PCONSOLE_SCREEN_BUFFER_INFO
- PCONSOLE_SCREEN_BUFFER_INFO
MS-HAID:
- '\_win32\_console\_screen\_buffer\_info\_str'
- base.console\_screen\_buffer\_info\_str
- consoles.console\_screen\_buffer\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 586b3e0f-2f6b-4a03-b8e4-602a892be56d
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4089541ddac93f5be61b7a21d5aa88a88061b261
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059296"
---
# <a name="console_screen_buffer_info-structure"></a>\_Structure des \_ informations de mémoire tampon de l’écran de la console \_


Contient des informations sur une mémoire tampon d’écran de la console.

<a name="syntax"></a>Syntaxe
------

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFO {
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
} CONSOLE_SCREEN_BUFFER_INFO;
```

<a name="members"></a>Membres
-------

**dwSize nul**  
Structure de [**repère**](coord-str.md) qui contient la taille de la mémoire tampon d’écran de la console, dans les colonnes de caractères et les lignes.

**dwCursorPosition**  
Structure de [**repère**](coord-str.md) qui contient les coordonnées de colonne et de ligne du curseur dans la mémoire tampon d’écran de la console.

**wAttributes**  
Attributs des caractères écrits dans une mémoire tampon d’écran par les fonctions [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) et [**WriteConsole**](writeconsole.md) , ou répercutés dans une mémoire tampon d’écran par les fonctions [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**ReadConsole**](readconsole.md) . Pour plus d’informations, consultez [attributs de caractères](console-screen-buffers.md#_win32_font_attributes).

**srWindow**  
[**Petite structure \_ Rect**](small-rect-str.md) qui contient les coordonnées de la mémoire tampon d’écran de la console des angles supérieur gauche et inférieur droit de la fenêtre d’affichage.

**dwMaximumWindowSize**  
Structure de [**repère**](coord-str.md) qui contient la taille maximale de la fenêtre de console, en colonnes de caractères et en lignes, en fonction de la taille et de la police de la mémoire tampon d’écran actuelle et de la taille de l’écran.

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
<td>ConsoleApi2. h (via wincon. h, incluez Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Voir aussi


[**COORDONNÉES**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**PETIT \_ Rect**](small-rect-str.md)

[**WriteConsole**](writeconsole.md)

[**Appel**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




