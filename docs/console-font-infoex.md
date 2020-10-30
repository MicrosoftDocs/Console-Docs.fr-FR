---
title: Structure CONSOLE_FONT_INFOEX
description: Consultez les informations de référence sur la structure CONSOLE_FONT_INFOEX, qui contient des informations étendues pour une police de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/CONSOLE_FONT_INFOEX
- wincon/CONSOLE_FONT_INFOEX
- CONSOLE_FONT_INFOEX
- consoleapi3/PCONSOLE_FONT_INFOEX
- wincon/PCONSOLE_FONT_INFOEX
- PCONSOLE_FONT_INFOEX
MS-HAID:
- base.console\_font\_infoex
- consoles.console\_font\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e9a087e1-264d-4d48-8adb-771a0e35b511
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFOEX
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: ef89d1bf47a4153d44140d3f9f4845bb7496680e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039257"
---
# <a name="console_font_infoex-structure"></a>Structure de la police de la CONSOLE \_ \_ INFOEX

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contient des informations étendues pour une police de console.

## <a name="syntax"></a>Syntaxe

```C
typedef struct _CONSOLE_FONT_INFOEX {
  ULONG cbSize;
  DWORD nFont;
  COORD dwFontSize;
  UINT  FontFamily;
  UINT  FontWeight;
  WCHAR FaceName[LF_FACESIZE];
} CONSOLE_FONT_INFOEX, *PCONSOLE_FONT_INFOEX;
```

## <a name="members"></a>Membres

**cbSize**  
Taille de cette structure, en octets. Ce membre doit être défini sur `sizeof(CONSOLE_FONT_INFOEX)` avant d’appeler [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) , sinon il échouera.

**nFont**  
Index de la police dans la table des polices de la console du système.

**dwFontSize**  
Structure de [**repère**](coord-str.md) qui contient la largeur et la hauteur de chaque caractère de la police, en unités logiques. Le membre **X** contient la largeur, tandis que le membre **Y** contient la hauteur.

**FontFamily**  
L’espacement de la police et la famille. Pour plus d’informations sur les valeurs possibles de ce membre, consultez la description du membre **tmPitchAndFamily** de la structure [**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132) .

**FontWeight**  
Épaisseur de la police. Le poids peut être compris entre 100 et 1000, par multiples de 100. Par exemple, le poids normal est 400, tandis que 700 est gras.

**FaceName**  
Nom du type de caractères (Courier ou Arial, par exemple).

## <a name="remarks"></a>Remarques

Pour obtenir la taille de la police, transmettez l’index de la police à la fonction [**GetConsoleFontSize**](getconsolefontsize.md) .

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows Vista uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2008 \[ uniquement\] |
| En-tête | WinCon. h (inclure Windows. h) |

## <a name="see-also"></a>Voir aussi

[**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md)
