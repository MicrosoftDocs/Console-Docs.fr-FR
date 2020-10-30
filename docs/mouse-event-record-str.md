---
title: MOUSE_EVENT_RECORD, structure
description: Consultez les informations de référence sur la structure MOUSE_EVENT_RECORD, qui décrit un événement d’entrée de souris dans une structure de INPUT_RECORD de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- wincontypes/MOUSE_EVENT_RECORD
- wincon/MOUSE_EVENT_RECORD
- MOUSE_EVENT_RECORD
- wincontypes/PMOUSE_EVENT_RECORD
- wincon/PMOUSE_EVENT_RECORD
- PMOUSE_EVENT_RECORD
MS-HAID:
- '\_win32\_mouse\_event\_record\_str'
- base.mouse\_event\_record\_str
- consoles.mouse\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ea54c6-8872-4111-8d72-1377409b9247
topic_type:
- apiref
api_name:
- MOUSE_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: c10047d1386f3bce1546ee21bacdc81b8fb7bb55
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038517"
---
# <a name="mouse_event_record-structure"></a>Structure d’enregistrement d' \_ événement de souris \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Décrit un événement d’entrée de souris dans une structure [**d' \_ enregistrement d’entrée**](input-record-str.md) de console.

## <a name="syntax"></a>Syntaxe

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

## <a name="members"></a>Membres

**dwMousePosition**  
Structure de [**repère**](coord-str.md) qui contient l’emplacement du curseur, en termes de coordonnées des cellules de caractères de la mémoire tampon de l’écran de la console.

**dwButtonState**  
État des boutons de la souris. Le bit le moins significatif correspond au bouton le plus à gauche de la souris. Le bit le moins significatif suivant correspond au bouton le plus à droite de la souris. Le bit suivant indique le bouton de la souris situé à l’extrême gauche. Les bits correspondent ensuite de gauche à droite aux boutons de la souris. Un bit est 1 si le bouton a été enfoncé.

Les constantes suivantes sont définies pour les cinq premiers boutons de la souris.

| Valeur | Signification |
|-|-|
| **FROM_LEFT_1ST_BUTTON_PRESSED** 0x0001 | Le bouton gauche de la souris. |
| **FROM_LEFT_2ND_BUTTON_PRESSED** 0x0004 | Le deuxième bouton de la gauche. |
| **FROM_LEFT_3RD_BUTTON_PRESSED** 0x0008 | Troisième bouton à partir de la gauche. |
| **FROM_LEFT_4TH_BUTTON_PRESSED** 0x0010 | Quatrième bouton à partir de la gauche. |
| **RIGHTMOST_BUTTON_PRESSED** 0x0002 | Bouton de la souris le plus à droite. |

**dwControlKeyState**  
État des touches de contrôle. Ce membre peut être une ou plusieurs des valeurs suivantes.

| Valeur | Signification |
|-|-|
| **CAPSLOCK_ON** 0x0080 | Le voyant Verr. MAJ est activé. |
| **ENHANCED_KEY** 0x0100 | La clé est améliorée. Consultez la [section Notes](key-event-record-str.md#remarks). |
| **LEFT_ALT_PRESSED** 0x0002 | La touche ALT de gauche est enfoncée. |
| **LEFT_CTRL_PRESSED** 0x0008 | La touche CTRL de gauche est enfoncée. |
| **NUMLOCK_ON** 0x0020 | La diode Verr. NUM est activée. |
| **RIGHT_ALT_PRESSED** 0x0001 | La touche ALT de droite est enfoncée. |
| **RIGHT_CTRL_PRESSED** 0x0004 | La touche CTRL de droite est enfoncée. |
| **SCROLLLOCK_ON** 0x0040 | Le voyant du verrou de défilement est activé. |
| **SHIFT_PRESSED** 0x0010 | La touche Maj est enfoncée. |

**dwEventFlags**  
Type d’événement de souris. Si cette valeur est égale à zéro, elle indique qu’un bouton de la souris est enfoncé ou relâché. Dans le cas contraire, ce membre est l’une des valeurs suivantes.

| Valeur | Signification |
|-|-|
| **DOUBLE_CLICK** 0x0002 | Le deuxième clic (appuyez sur le bouton) d’un double-clic s’est produit. Le premier clic est retourné en tant qu’événement de bouton-pression standard. |
| **MOUSE_HWHEELED** 0x0008 | La roulette horizontale de la souris a été déplacée.<br /><br />Si le mot de poids fort du membre **dwButtonState** contient une valeur positive, la roulette a été pivotée vers la droite. Dans le cas contraire, la roulette a été pivotée vers la gauche. |
| **MOUSE_MOVED** 0x0001 | Une modification de la position de la souris s’est produite. |
| **MOUSE_WHEELED** 0x0004 | La roulette verticale de la souris a été déplacée.<br /><br />Si le mot de poids fort du membre **dwButtonState** contient une valeur positive, la roulette a été pivotée vers l’avant, en dehors de l’utilisateur. Dans le cas contraire, la roulette a été tournée vers l’arrière de l’utilisateur. |

## <a name="remarks"></a>Remarques

Les événements de souris sont placés dans la mémoire tampon d’entrée lorsque la console est en mode souris ( **activer l' \_ \_ entrée de la souris** ).

Les événements de souris sont générés chaque fois que l’utilisateur déplace la souris, ou appuie sur ou relâche l’un des boutons de la souris. Les événements de souris sont placés dans la mémoire tampon d’entrée d’une console uniquement lorsque le groupe de la console a le focus clavier et que le curseur se trouve dans les limites de la fenêtre de la console.

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

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)
