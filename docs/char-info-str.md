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
ms.openlocfilehash: a16fb23d148f75480437211204a0fd7c1f161bfe
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357849"
---
# `CHAR\_INFO structure`

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
| **FOREGROUND_BLUE**`0x0001` | La couleur du texte contient du bleu. |
| **FOREGROUND_GREEN**`0x0002` | La couleur du texte contient du vert. |
| **FOREGROUND_RED**`0x0004` | La couleur du texte contient du rouge. |
| **FOREGROUND_INTENSITY**`0x0008` | La couleur du texte est intensifiée. |
| **BACKGROUND_BLUE**`0x0010` | La couleur d’arrière-plan contient du bleu. |
| **BACKGROUND_GREEN**`0x0020` | La couleur d’arrière-plan contient du vert. |
| **BACKGROUND_RED**`0x0040` | La couleur d’arrière-plan contient du rouge. |
| **BACKGROUND_INTENSITY**`0x0080` | La couleur d’arrière-plan est intensifiée. |
| **COMMON_LVB_LEADING_BYTE**`0x0100` | Octet de début. |
| **COMMON_LVB_TRAILING_BYTE**`0x0200` | Octet de fin. |
| **COMMON_LVB_GRID_HORIZONTAL**`0x0400` | Supérieur horizontal. |
| **COMMON_LVB_GRID_LVERTICAL**`0x0800` | Gauche vertical. |
| **COMMON_LVB_GRID_RVERTICAL**`0x1000` | Droite vertical. |
| **COMMON_LVB_REVERSE_VIDEO**`0x4000` | Attribut de premier plan et d’arrière-plan inversé. |
| **COMMON_LVB_UNDERSCORE**`0x8000` | Caractère de soulignement. |

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 2000 Professionnel - \[Applications de bureau uniquement\] |
| Serveur minimal pris en charge | Windows 2000 Server - \[Applications de bureau uniquement\] |
| En-tête | WinCon. h (inclure Windows. h) |

## <a name="see-also"></a>Voir aussi

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)
