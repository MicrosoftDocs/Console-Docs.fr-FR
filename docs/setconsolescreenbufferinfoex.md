---
title: SetConsoleScreenBufferInfoEx fonction)
description: Définit les informations étendues relatives à la mémoire tampon d’écran de console spécifiée dans la mémoire tampon spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/SetConsoleScreenBufferInfoEx
- wincon/SetConsoleScreenBufferInfoEx
- SetConsoleScreenBufferInfoEx
MS-HAID:
- base.setconsolescreenbufferinfoex
- consoles.setconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ff851144-eee9-4410-8fd1-28aa24fc25f1
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 677df94d6397c1515ad96757788c9a044b6ed87e
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358649"
---
# <a name="setconsolescreenbufferinfoex-function"></a>SetConsoleScreenBufferInfoEx fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Définit des informations étendues sur la mémoire tampon d’écran de console spécifiée.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI SetConsoleScreenBufferInfoEx(
  _In_ HANDLE                        hConsoleOutput,
  _In_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a>Paramètres

*hConsoleOutput* \[entrée\]  
Handle vers la mémoire tampon d’écran de console. Le handle doit avoir le droit d’accès **GENERIC\_WRITE**. Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).

*lpConsoleScreenBufferInfoEx* \[ dans\]  
Une [**structure \_ \_ \_ INFOEX de mémoire tampon d’écran**](console-screen-buffer-infoex.md) de la console qui contient les informations de mémoire tampon d’écran de la console.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

> [!TIP]
> Cette API a un équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** partiel. La **[mémoire tampon de positionnement des curseurs](console-virtual-terminal-sequences.md#cursor-positioning)** et les **[attributs de texte](console-virtual-terminal-sequences.md#text-formatting)** ont des équivalents de séquence spécifiques. La table des couleurs n’est pas configurable, mais les **[couleurs étendues](console-virtual-terminal-sequences.md#extended-colors)** sont disponibles au-delà de ce qui est normalement disponible via les fonctions de la **[console](console-functions.md)**. Les attributs Popup ne sont pas équivalents à ceux des menus contextuels qui sont la responsabilité de l’application cliente de ligne de commande dans le monde des **terminaux virtuels** . Enfin, la taille de la fenêtre et l’État plein écran sont considérés comme des privilèges détenus par l’utilisateur dans le monde des **terminaux virtuels** et n’ont pas de séquence équivalente.

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows Vista uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2008 \[ uniquement\] |
| En-tête | ConsoleApi2. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de console](console-functions.md)

[**mémoire tampon d’écran de la CONSOLE \_ \_ \_ INFOEX**](console-screen-buffer-infoex.md)

[**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md)