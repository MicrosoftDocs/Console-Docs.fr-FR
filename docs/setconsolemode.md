---
title: Fonction SetConsoleMode
description: Définit le mode d’entrée d’une mémoire tampon d’entrée de console ou le mode de sortie d’une mémoire tampon d’écran de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/SetConsoleMode
- wincon/SetConsoleMode
- SetConsoleMode
MS-HAID:
- '\_win32\_setconsolemode'
- base.setconsolemode
- consoles.setconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 77508d58-8a7a-4c47-9ec5-dc61e5c4beac
topic_type:
- apiref
api_name:
- SetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 2af598f465be6e1a33f5a8f9a2c9abe98d6ed0d2
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420298"
---
# <a name="setconsolemode-function"></a>Fonction SetConsoleMode

Définit le mode d’entrée d’une mémoire tampon d’entrée de console ou le mode de sortie d’une mémoire tampon d’écran de console.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

## <a name="parameters"></a>Paramètres

*hConsoleHandle* \[entrée\]  
Handle vers la mémoire tampon d’entrée de console ou mémoire tampon d’écran de console. Le handle doit avoir le droit d’accès **GENERIC\_READ**. Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).

*dwMode* \[entrée\]  
Mode d’entrée ou de sortie à définir.

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

Pour déterminer le mode actuel d’une mémoire tampon d’entrée de console ou d’une mémoire tampon d’écran, utilisez la fonction [**GetConsoleMode**](getconsolemode.md).

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [Lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 2000 Professionnel - \[Applications de bureau uniquement\] |
| Serveur minimal pris en charge | Windows 2000 Server - \[Applications de bureau uniquement\] |
| En-tête | ConsoleApi.h (via WinCon.h, inclure Windows.h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de console](console-functions.md)

[Modes de la console](console-modes.md)

[**GetConsoleMode**](getconsolemode.md)

[**HandlerRoutine**](handlerroutine.md)

[**ReadConsole**](readconsole.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)
