---
title: CONSOLE_SCREEN_BUFFER_INFOEX, structure
description: Consultez les informations de référence sur la structure CONSOLE_SCREEN_BUFFER_INFOEX, qui contient des informations étendues sur une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 1e4e30601655190bc6f597bbd33dd99f14f8d488
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358080"
---
# <a name="console_screen_buffer_infoex-structure"></a>\_Structure INFOEX de la \_ mémoire tampon d’écran de la console \_

Contient des informations étendues sur une mémoire tampon d’écran de la console.

## <a name="syntax"></a>Syntaxe

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

## <a name="members"></a>Membres

**cbSize**  
Taille de cette structure, en octets.

**dwSize nul**  
Structure de [**repère**](coord-str.md) qui contient la taille de la mémoire tampon d’écran de la console, dans les colonnes de caractères et les lignes.

**dwCursorPosition**  
Structure de [**repère**](coord-str.md) qui contient les coordonnées de colonne et de ligne du curseur dans la mémoire tampon d’écran de la console.

**wAttributes**  
Attributs des caractères écrits dans une mémoire tampon d’écran par les fonctions [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) et [**WriteConsole**](writeconsole.md) , ou répercutés dans une mémoire tampon d’écran par les fonctions [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) et [**ReadConsole**](readconsole.md) . Pour plus d’informations, consultez [attributs de caractères](console-screen-buffers.md#character-attributes).

**srWindow**  
[**Petite structure \_ Rect**](small-rect-str.md) qui contient les coordonnées de la mémoire tampon d’écran de la console des angles supérieur gauche et inférieur droit de la fenêtre d’affichage.

**dwMaximumWindowSize**  
Structure de [**repère**](coord-str.md) qui contient la taille maximale de la fenêtre de console, en colonnes de caractères et en lignes, en fonction de la taille et de la police de la mémoire tampon d’écran actuelle et de la taille de l’écran.

**wPopupAttributes**  
Attribut de remplissage des fenêtres contextuelles de la console.

**bFullscreenSupported**  
Si ce membre est `TRUE` , le mode plein écran est pris en charge ; sinon, il ne l’est pas. Ce sera toujours `FALSE` le cas pour les systèmes après Windows Vista avec le [modèle de pilote WDDM](/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) , car l’accès direct VGA à l’analyse n’est plus disponible.

**ColorTable**  
Tableau de valeurs [**COLORREF**](/windows/win32/gdi/colorref) qui décrivent les paramètres de couleur de la console.

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows Vista uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2008 \[ uniquement\] |
| En-tête | ConsoleApi2. h (via WinCon. h, incluez Windows. h) |

## <a name="see-also"></a>Voir aussi

[**COORDONNÉES**](coord-str.md)

[**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md)

[**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md)

[**PETIT \_ Rect**](small-rect-str.md)