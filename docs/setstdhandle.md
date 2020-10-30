---
title: SetStdHandle fonction)
description: Définit le descripteur pour l’appareil standard spécifié (entrée standard, sortie standard ou erreur standard).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 36531872df90239e2b909c80fb75ad3011280c78
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039297"
---
# <a name="setstdhandle-function"></a>SetStdHandle fonction)

Définit le descripteur pour l’appareil standard spécifié (entrée standard, sortie standard ou erreur standard).

## <a name="syntax"></a>Syntaxe

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

## <a name="parameters"></a>Paramètres

*nStdHandle* \[ dans\]  
Appareil standard pour lequel le descripteur doit être défini. Ce paramètre peut prendre l’une des valeurs suivantes.

| Valeur | Signification |
|-|-|
| **STD_INPUT_HANDLE** (DWORD)-10 | Périphérique d’entrée standard. Initialement, il s’agit de la mémoire tampon d’entrée de la console, `CONIN$` . |
| **STD_OUTPUT_HANDLE** (DWORD)-11 | Périphérique de sortie standard. Initialement, il s’agit de la mémoire tampon d’écran active de la console, `CONOUT$` . |
| **STD_ERROR_HANDLE** (DWORD)-12 | Périphérique d’erreur standard. Initialement, il s’agit de la mémoire tampon d’écran active de la console, `CONOUT$` . |

*hHandle* \[ dans\]  
Handle pour l’appareil standard.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Les handles standard d’un processus peuvent avoir été redirigés par un appel à **SetStdHandle** , auquel cas [**GetStdHandle**](getstdhandle.md) retourne le handle Redirigé. Si les handles standard ont été redirigés, vous pouvez spécifier la valeur CONIN $ dans un appel à la fonction [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) pour obtenir un handle vers la mémoire tampon d’entrée d’une console. De même, vous pouvez spécifier la valeur CONOUT $ pour obtenir un descripteur de la mémoire tampon d’écran active de la console.

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [création d’un processus enfant avec une entrée et une sortie redirigées](https://msdn.microsoft.com/library/windows/desktop/ms682499).

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | ProcessEnv. h (via Winbase. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[Handles de console](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetStdHandle**](getstdhandle.md)
