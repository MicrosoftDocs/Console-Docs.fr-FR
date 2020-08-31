---
title: Structure CONSOLE_SCREEN_BUFFER_INFOEX
description: Consultez les informations de référence sur la structure CONSOLE_SCREEN_BUFFER_INFOEX, qui contient des informations étendues sur une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFOEX
- wincon/CONSOLE_SCREEN_BUFFER_INFOEX
- CONSOLE_SCREEN_BUFFER_INFOEX
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFOEX
- wincon/PCONSOLE_SCREEN_BUFFER_INFOEX
- PCONSOLE_SCREEN_BUFFER_INFOEX
MS-HAID:
- base.console\_screen\_buffer\_infoex
- consoles.console\_screen\_buffer\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6ed40df3-063d-41c9-8637-510c95104603
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFOEX
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 010120f2d925727e37bd72905bab4536db073371
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059293"
---
# <a name="console_screen_buffer_infoex-structure"></a>\_Structure INFOEX de la \_ mémoire tampon d’écran de la console \_


Contient des informations étendues sur une mémoire tampon d’écran de la console.

<a name="syntax"></a>Syntaxe
------

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

<a name="members"></a>Membres
-------

**cbSize**  
Taille de cette structure, en octets.

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

**wPopupAttributes**  
Attribut de remplissage des fenêtres contextuelles de la console.

**bFullscreenSupported**  
Si ce membre a la valeur TRUE, le mode plein écran est pris en charge ; Sinon, ce n’est pas le cas.

**ColorTable**  
Tableau de valeurs [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) qui décrivent les paramètres de couleur de la console.

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
<td><p>Windows Vista [applications de bureau uniquement]</p></td>
</tr>
<tr class="even">
<td><p>Serveur minimal pris en charge</p></td>
<td><p>Windows Server 2008 [applications de bureau uniquement]</p></td>
</tr>
<tr class="odd">
<td><p>En-tête</p></td>
<td>ConsoleApi2. h (via wincon. h, incluez Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Voir aussi


[**COORDONNÉES**](coord-str.md)

[**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md)

[**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md)

[**PETIT \_ Rect**](small-rect-str.md)

 

 




