---
title: CONSOLE_READCONSOLE_CONTROL, structure
description: Consultez les informations de référence sur la structure CONSOLE_READCONSOLE_CONTROL, qui contient des informations relatives à une opération de lecture de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/CONSOLE_READCONSOLE_CONTROL
- wincon/CONSOLE_READCONSOLE_CONTROL
- CONSOLE_READCONSOLE_CONTROL
- consoleapi/PCONSOLE_READCONSOLE_CONTROL
- wincon/PCONSOLE_READCONSOLE_CONTROL
- PCONSOLE_READCONSOLE_CONTROL
MS-HAID:
- base.console\_readconsole\_control
- consoles.console\_readconsole\_control
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a8451a6-d692-43af-88c4-972c4dc5e07c
topic_type:
- apiref
api_name:
- CONSOLE_READCONSOLE_CONTROL
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8a703a1eaa370e16095e1b10eb146a0718f332e9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039187"
---
# <a name="console_readconsole_control-structure"></a>\_Structure de contrôle READCONSOLE de la console \_

Contient des informations relatives à une opération de lecture de console.

## <a name="syntax"></a>Syntaxe

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

## <a name="members"></a>Membres

**nLength**  
Taille de la structure. Affectez à ce membre la valeur `sizeof(CONSOLE_READCONSOLE_CONTROL)` .

**nInitialChars**  
Nombre de caractères à ignorer (et donc conserver) avant l’écriture de l’entrée récemment lue dans la mémoire tampon transmise à la fonction [**ReadConsole**](readconsole.md) . Cette valeur doit être inférieure au paramètre *nNumberOfCharsToRead* de la fonction **ReadConsole** .

**dwCtrlWakeupMask**  
Masque spécifiant quels caractères de contrôle entre `0x00` et `0x1F` doivent être utilisés pour signaler que la lecture est terminée. Chaque bit correspond à un caractère avec le bit le moins significatif correspondant à `0x00` ou `NUL` et le bit le plus significatif correspondant à `0x1F` ou à `US` . Plusieurs bits (caractères de contrôle) peuvent être spécifiés.

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

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows Vista uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2008 \[ uniquement\] |
| En-tête | ConsoleApi. h (via WinCon. h, incluez Windows. h) |

## <a name="see-also"></a>Voir aussi

[**ReadConsole**](readconsole.md)
