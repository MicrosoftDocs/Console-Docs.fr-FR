---
title: Structure CHAR_INFO
description: Spécifie un caractère Unicode ou ANSI et ses attributs. Cette structure est utilisée par les fonctions de la console pour lire et écrire dans une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: b07938d6ac58744533711c91a04b1a0188f7daf6
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037377"
---
# <a name="char_info-structure"></a>CHAR \_ info (structure)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Spécifie un caractère Unicode ou ANSI et ses attributs. Cette structure est utilisée par les fonctions de la console pour lire et écrire dans une mémoire tampon d’écran de la console.

## <a name="syntax"></a>Syntaxe

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

## <a name="members"></a>Membres

**Char**  
Union des membres suivants.

**UnicodeChar**  
Caractère Unicode d’une cellule de caractère de mémoire tampon d’écran.

**AsciiChar**  
Caractère ANSI d’une cellule de caractère de mémoire tampon d’écran.

**Attributs**  
Attributs de caractère. Ce membre peut être égal à zéro ou n’importe quelle combinaison des valeurs suivantes.

| Valeur | Signification |
|-|-|
| **FOREGROUND_BLUE**`0x0001` | La couleur du texte contient le bleu. |
| **FOREGROUND_GREEN**`0x0002` | La couleur du texte contient du vert. |
| **FOREGROUND_RED**`0x0004` | La couleur du texte contient le rouge. |
| **FOREGROUND_INTENSITY**`0x0008` | La couleur du texte est intensifiée. |
| **BACKGROUND_BLUE**`0x0010` | La couleur d’arrière-plan contient le bleu. |
| **BACKGROUND_GREEN**`0x0020` | La couleur d’arrière-plan contient du vert. |
| **BACKGROUND_RED**`0x0040` | La couleur d’arrière-plan contient le rouge. |
| **BACKGROUND_INTENSITY**`0x0080` | La couleur d’arrière-plan est intensifiée. |
| **COMMON_LVB_LEADING_BYTE**`0x0100` | Octet de début. |
| **COMMON_LVB_TRAILING_BYTE**`0x0200` | Octet de fin. |
| **COMMON_LVB_GRID_HORIZONTAL**`0x0400` | Horizontal supérieur. |
| **COMMON_LVB_GRID_LVERTICAL**`0x0800` | Vertical gauche. |
| **COMMON_LVB_GRID_RVERTICAL**`0x1000` | Verticale droite. |
| **COMMON_LVB_REVERSE_VIDEO**`0x4000` | Attribut de premier plan et d’arrière-plan inversé. |
| **COMMON_LVB_UNDERSCORE**`0x8000` | Soulignement. |

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | WinCon. h (inclure Windows. h) |

## <a name="see-also"></a>Voir aussi

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)
