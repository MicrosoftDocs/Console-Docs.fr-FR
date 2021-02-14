---
title: SetConsoleDisplayMode fonction)
description: Consultez les informations de référence sur la fonction SetConsoleDisplayMode, qui définit le mode d’affichage de la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- base.setconsoledisplaymode
- consoles.setconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744
topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: af61d897269311ccfa9db336083e898f6d75da80
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357699"
---
# <a name="setconsoledisplaymode-function"></a>SetConsoleDisplayMode fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Définit le mode d’affichage de la mémoire tampon d’écran de console spécifiée.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

## <a name="parameters"></a>Paramètres

*hConsoleOutput* \[entrée\]  
Handle vers la mémoire tampon d’écran de console.

*dwFlags* \[ dans\]  
Mode d’affichage de la console. Ce paramètre peut être une ou plusieurs des valeurs suivantes.

| Valeur | Signification |
|-|-|
| **CONSOLE_FULLSCREEN_MODE** 1 | Le texte est affiché en mode plein écran. |
| **CONSOLE_WINDOWED_MODE** 2 | Le texte est affiché dans une fenêtre de console. |

*lpNewScreenBufferDimensions* \[ out, facultatif\]  
Pointeur vers une structure de [**repère**](coord-str.md) qui reçoit les nouvelles dimensions de la mémoire tampon d’écran, en caractères.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Notes

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows XP uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2003 \[ uniquement\] |
| En-tête | ConsoleApi3. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de console](console-functions.md)

[Modes de la console](console-modes.md)

[**GetConsoleDisplayMode**](getconsoledisplaymode.md)