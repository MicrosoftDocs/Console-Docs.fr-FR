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
ms.openlocfilehash: 317acd84289e5138e1a947251e745077ba581083
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358509"
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

*nStdHandle* \[entrée\]  
Appareil standard pour lequel le descripteur doit être défini. Ce paramètre peut prendre les valeurs suivantes.

| Valeur | Signification |
|-|-|
| **STD_INPUT_HANDLE** (DWORD) -10 | Périphérique d’entrée standard. À la base, il s’agit de la mémoire tampon d’entrée de la console, `CONIN$`. |
| **STD_OUTPUT_HANDLE** (DWORD) -11 | Périphérique de sortie standard. À la base, il s’agit de la mémoire tampon d’écran de la console active, `CONOUT$`. |
| **STD_ERROR_HANDLE** (DWORD) -12 | Périphérique d’erreur standard. À la base, il s’agit de la mémoire tampon d’écran de la console active, `CONOUT$`. |

*hHandle* \[ dans\]  
Handle pour l’appareil standard.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

Les handles standard d’un processus peuvent avoir été redirigés par un appel à **SetStdHandle**, auquel cas [**GetStdHandle**](getstdhandle.md) retourne le handle Redirigé. Si les handles standard ont été redirigés, vous pouvez spécifier la valeur CONIN $ dans un appel à la fonction [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) pour obtenir un handle vers la mémoire tampon d’entrée d’une console. De même, vous pouvez spécifier la valeur CONOUT $ pour obtenir un descripteur de la mémoire tampon d’écran active de la console.

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [création d’un processus enfant avec une entrée et une sortie redirigées](/windows/win32/procthread/creating-a-child-process-with-redirected-input-and-output).

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 2000 Professionnel - \[Applications de bureau uniquement\] |
| Serveur minimal pris en charge | Windows 2000 Server - \[Applications de bureau uniquement\] |
| En-tête | ProcessEnv.h (via Winbase.h, inclure Windows.h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de console](console-functions.md)

[Handles de console](console-handles.md)

[**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea)

[**GetStdHandle**](getstdhandle.md)