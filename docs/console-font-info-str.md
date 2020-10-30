---
title: Structure CONSOLE_FONT_INFO
description: Consultez les informations de référence sur la structure CONSOLE_FONT_INFO, qui contient l’index et la taille d’une police de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- wincontypes/CONSOLE_FONT_INFO
- wincon/CONSOLE_FONT_INFO
- CONSOLE_FONT_INFO
- wincontypes/PCONSOLE_FONT_INFO
- wincon/PCONSOLE_FONT_INFO
- PCONSOLE_FONT_INFO
MS-HAID:
- '\_win32\_console\_font\_info\_str'
- base.console\_font\_info\_str
- consoles.console\_font\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 380b8183-1964-46f2-a511-01f39f21f5c5
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 6c437e626ed6d207da4672a3a5ea60c2ea0ee008
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037137"
---
# <a name="console_font_info-structure"></a>Structure des informations de \_ police de la console \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contient des informations pour une police de console.

## <a name="syntax"></a>Syntaxe

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

## <a name="members"></a>Membres

**nFont**  
Index de la police dans la table des polices de la console du système.

**dwFontSize**  
Structure de [**repère**](coord-str.md) qui contient la largeur et la hauteur de chaque caractère de la police, en unités logiques. Le membre **X** contient la largeur, tandis que le membre **Y** contient la hauteur.

## <a name="remarks"></a>Remarques

Pour obtenir la taille de la police, transmettez l’index de la police à la fonction [**GetConsoleFontSize**](getconsolefontsize.md) .

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows XP uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2003 \[ uniquement\] |
| En-tête | WinCon. h (inclure Windows. h) |

## <a name="see-also"></a>Voir aussi

[**COORDONNÉES**](coord-str.md)

[**GetCurrentConsoleFont**](getcurrentconsolefont.md)
