---
title: WINDOW_BUFFER_SIZE_RECORD, structure
description: Consultez les informations de référence sur la structure WINDOW_BUFFER_SIZE_RECORD, qui décrit une modification de la taille de la mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- wincontypes/WINDOW_BUFFER_SIZE_RECORD
- wincon/WINDOW_BUFFER_SIZE_RECORD
- WINDOW_BUFFER_SIZE_RECORD
- wincontypes/PWINDOW_BUFFER_SIZE_RECORD
- wincon/PWINDOW_BUFFER_SIZE_RECORD
- PWINDOW_BUFFER_SIZE_RECORD
MS-HAID:
- '\_win32\_window\_buffer\_size\_record\_str'
- base.window\_buffer\_size\_record\_str
- consoles.window\_buffer\_size\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f2875e8-aa09-455b-a923-7cc388525b98
topic_type:
- apiref
api_name:
- WINDOW_BUFFER_SIZE_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 355482dfd162e2c29944d53e5b17b0315ea15950
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039267"
---
# <a name="window_buffer_size_record-structure"></a>\_Structure d' \_ enregistrement de taille de mémoire tampon de fenêtre \_

Décrit une modification de la taille de la mémoire tampon d’écran de la console.

## <a name="syntax"></a>Syntaxe

```C
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

## <a name="members"></a>Membres

**dwSize nul**  
Structure de [**repère**](coord-str.md) qui contient la taille de la mémoire tampon de l’écran de la console, dans les colonnes et les lignes des cellules de caractères.

## <a name="remarks"></a>Remarques

Les événements de taille de mémoire tampon sont placés dans la mémoire tampon d’entrée lorsque la console est en mode compatible avec les fenêtres ( **activer l' \_ \_ entrée** de la fenêtre).

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | WinConTypes. h (via WinCon. h, incluez Windows. h) |

## <a name="see-also"></a>Voir aussi

[**COORDONNÉES**](coord-str.md)

[**enregistrement d’entrée \_**](input-record-str.md)

[**ReadConsoleInput**](readconsoleinput.md)
