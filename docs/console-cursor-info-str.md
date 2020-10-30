---
title: Structure CONSOLE_CURSOR_INFO
description: Contient les informations relatives à la taille et à la visibilité sur le curseur de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: cdfcc00035738aa468d9795e4f6d32a54b96e1d0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037010"
---
# <a name="console_cursor_info-structure"></a>Structure des informations du \_ curseur de la console \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contient des informations sur le curseur de la console.

## <a name="syntax"></a>Syntaxe

```C
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

## <a name="members"></a>Membres

**dwSize nul**  
Pourcentage de la cellule de caractère qui est rempli par le curseur. Cette valeur est comprise entre 1 et 100. L’apparence du curseur varie, du remplissage complet de la cellule à l’affichage sous la forme d’une ligne horizontale au bas de la cellule.

> [!NOTE]
>Alors que la valeur **dwSize nul** est normalement comprise entre 1 et 100, dans certains cas, une valeur en dehors de cette plage peut être retournée. Par exemple, si **CursorSize** est défini sur 0 dans le registre, la valeur **dwSize nul** retournée est 0.

 **bVisible**  
Visibilité du curseur. Si le curseur est visible, ce membre a la **valeur true** .

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | WinCon. h (inclure Windows. h) |

## <a name="see-also"></a>Voir aussi

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**SetConsoleCursorInfo**](setconsolecursorinfo.md)
