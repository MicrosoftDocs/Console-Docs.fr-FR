---
title: Structure CONSOLE_SELECTION_INFO
description: Consultez les informations de référence sur la structure CONSOLE_SELECTION_INFO, qui contient des informations pour une sélection de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/CONSOLE_SELECTION_INFO
- wincon/CONSOLE_SELECTION_INFO
- CONSOLE_SELECTION_INFO
- consoleapi3/PCONSOLE_SELECTION_INFO
- wincon/PCONSOLE_SELECTION_INFO
- PCONSOLE_SELECTION_INFO
MS-HAID:
- '\_win32\_console\_selection\_info\_str'
- base.console\_selection\_info\_str
- consoles.console\_selection\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9530b249-8db4-4516-9cc8-2b452c6751f9
topic_type:
- apiref
api_name:
- CONSOLE_SELECTION_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: aaf1cfaea2a8822c142aab87f6dcf1b022b7160c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038367"
---
# <a name="console_selection_info-structure"></a>Structure des informations de \_ sélection de la console \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contient des informations pour une sélection de la console.

## <a name="syntax"></a>Syntaxe

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

## <a name="members"></a>Membres

**dwFlags**  
Indicateur de sélection. Ce membre peut être une ou plusieurs des valeurs suivantes.

| Valeur | Signification |
|-|-|
| **CONSOLE_MOUSE_DOWN** 0x0008 | Le bouton de la souris est enfoncé. L’utilisateur ajuste activement le rectangle de sélection à l’aide d’une souris. |
| **CONSOLE_MOUSE_SELECTION** 0x0004 | Sélection à l’aide de la souris. Si la valeur est OFF, l’utilisateur est `conhost.exe` sélectionné pour le mode de marquage avec le clavier. |
| **CONSOLE_NO_SELECTION** 0x0000 | Aucune sélection. |
| **CONSOLE_SELECTION_IN_PROGRESS** 0x0001 | La sélection a commencé. Si vous sélectionnez une souris, cela ne se produit généralement pas sans l' `CONSOLE_SELECTION_NOT_EMPTY` indicateur. Dans le cas d’une sélection de clavier, cela peut se produire lorsque le mode marque a été entré, mais que l’utilisateur accède toujours à la position initiale. |
| **CONSOLE_SELECTION_NOT_EMPTY** 0x0002 | Le rectangle de sélection n’est pas vide. La charge utile de *dwSelectionAnchor* et *srSelection* est valide.  |

**dwSelectionAnchor**  
Structure de [**repère**](coord-str.md) qui spécifie l’ancre de sélection, en caractères.

**srSelection**  
[**Petite structure \_ Rect**](small-rect-str.md) qui spécifie le rectangle de sélection.

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows XP uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2003 \[ uniquement\] |
| En-tête | ConsoleApi3. h (via WinCon. h, incluez Windows. h) |

## <a name="see-also"></a>Voir aussi

[**COORDONNÉES**](coord-str.md)

[**GetConsoleSelectionInfo**](getconsoleselectioninfo.md)

[**PETIT \_ Rect**](small-rect-str.md)
