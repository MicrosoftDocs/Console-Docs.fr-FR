---
title: SetConsoleCursorInfo fonction)
description: Définit la taille et la visibilité du curseur pour la mémoire tampon d’écran de la console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/SetConsoleCursorInfo
- wincon/SetConsoleCursorInfo
- SetConsoleCursorInfo
MS-HAID:
- '\_win32\_setconsolecursorinfo'
- base.setconsolecursorinfo
- consoles.setconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c98cbffb-18de-41e8-bba7-5fb46a0c5d25
topic_type:
- apiref
api_name:
- SetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 565ed3bda8bd864fb52aac0106f01cee96eb78ba
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357689"
---
# <a name="setconsolecursorinfo-function"></a>SetConsoleCursorInfo fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Définit la taille et la visibilité du curseur pour la mémoire tampon d’écran de la console spécifiée.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

## <a name="parameters"></a>Paramètres

*hConsoleOutput* \[entrée\]  
Handle vers la mémoire tampon d’écran de console. Le handle doit avoir le droit d’accès **GENERIC\_READ**. Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).

*lpConsoleCursorInfo* \[ dans\]  
Pointeur vers une structure [**d' \_ \_ informations de curseur de console**](console-cursor-info-str.md) qui fournit les nouvelles spécifications pour le curseur de la mémoire tampon d’écran de la console.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

Lorsque le curseur d’une mémoire tampon d’écran est visible, son apparence peut varier, du remplissage complet d’une cellule de caractère à l’affichage sous forme de ligne horizontale au bas de la cellule. Le membre **dwSize nul** de la structure d' [**\_ \_ informations du curseur**](console-cursor-info-str.md) de la console spécifie le pourcentage d’une cellule de caractère qui est remplie par le curseur. Si ce membre est inférieur à 1 ou supérieur à 100, **SetConsoleCursorInfo** échoue.

> [!TIP]
> Cette API a un **[terminal virtuel](console-virtual-terminal-sequences.md)** équivalent dans la section **[visibilité du curseur](console-virtual-terminal-sequences.md#cursor-visibility)** avec les `^[[?25h` `^[[?25l` séquences et. 

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 2000 Professionnel - \[Applications de bureau uniquement\] |
| Serveur minimal pris en charge | Windows 2000 Server - \[Applications de bureau uniquement\] |
| En-tête | ConsoleApi2. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de console](console-functions.md)

[Mémoires tampons d’écran d’une console](console-screen-buffers.md)

[**\_informations sur le curseur de la console \_**](console-cursor-info-str.md)

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)