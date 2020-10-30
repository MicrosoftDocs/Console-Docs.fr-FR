---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- wincontypes/SMALL_RECT
- wincon/SMALL_RECT
- SMALL_RECT
title: SMALL_RECT, structure
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 93121864c8754b281b92051a5e4a174b2d5956a3
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037097"
---
# <a name="small_rect-structure"></a>PETITE \_ structure Rect

Définit les coordonnées des angles supérieur gauche et inférieur droit d’un rectangle.

## <a name="syntax"></a>Syntaxe

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

## <a name="members"></a>Membres

**Left**  
Coordonnée x de l’angle supérieur gauche du rectangle.

**Top**  
Coordonnée y de l’angle supérieur gauche du rectangle.

**Right**  
Coordonnée x du coin inférieur droit du rectangle.

**Bas**  
Coordonnée y du coin inférieur droit du rectangle.

## <a name="remarks"></a>Remarques

Cette structure est utilisée par les fonctions de la console pour spécifier les zones rectangulaires des mémoires tampons d’écran de la console, où les coordonnées spécifient les lignes et les colonnes des cellules de caractères de la mémoire tampon d’écran.

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | WinConTypes. h (via WinCon. h, incluez Windows. h) |

## <a name="see-also"></a>Voir aussi

[**RECTANGULAIRE**](https://msdn.microsoft.com/library/windows/desktop/dd162897)

[**RECTo**](https://msdn.microsoft.com/library/windows/desktop/dd162907)
