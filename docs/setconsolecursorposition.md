---
title: SetConsoleCursorPosition fonction)
description: Consultez les informations de référence sur la fonction SetConsoleCursorPosition, qui définit la position du curseur dans la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/SetConsoleCursorPosition
- wincon/SetConsoleCursorPosition
- SetConsoleCursorPosition
MS-HAID:
- '\_win32\_setconsolecursorposition'
- base.setconsolecursorposition
- consoles.setconsolecursorposition
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8e9abada-a64e-429f-8286-ced1169c7104
topic_type:
- apiref
api_name:
- SetConsoleCursorPosition
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 48671b9c54e61733c2936ac1f112e2d499f31a1a
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357669"
---
# <a name="setconsolecursorposition-function"></a>SetConsoleCursorPosition fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Définit la position du curseur dans la mémoire tampon d’écran de console spécifiée.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

## <a name="parameters"></a>Paramètres

*hConsoleOutput* \[entrée\]  
Handle vers la mémoire tampon d’écran de console. Le handle doit avoir le droit d’accès **GENERIC\_READ**. Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).

*dwCursorPosition* \[ dans\]  
Structure de [**repère**](coord-str.md) qui spécifie la nouvelle position du curseur, en caractères. Les coordonnées sont la colonne et la ligne d’une cellule de caractère de mémoire tampon d’écran. Les coordonnées doivent se trouver dans les limites de la mémoire tampon d’écran de la console.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

La position du curseur détermine l’emplacement d’affichage des caractères écrits par la fonction [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) ou [**WriteConsole**](writeconsole.md) , ou renvoyé par la fonction [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) ou [**ReadConsole**](readconsole.md) . Pour déterminer la position actuelle du curseur, utilisez la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .

Si la nouvelle position du curseur ne se trouve pas dans les limites de la fenêtre de la mémoire tampon de l’écran de la console, l’origine de la fenêtre change pour rendre le curseur visible.

> [!TIP]
> Cette API possède un **[terminal virtuel](console-virtual-terminal-sequences.md)** équivalent dans les sections de positionnement de curseur et **[de positionnement de](console-virtual-terminal-sequences.md#cursor-positioning)** curseur **[simples](console-virtual-terminal-sequences.md#simple-cursor-positioning)** . L’utilisation des séquences de saut de ligne, de retour chariot, de retour arrière et de contrôle Tab peut également faciliter le positionnement du curseur.

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [utilisation des fonctions d’entrée et de sortie High-Level](using-the-high-level-input-and-output-functions.md).

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

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**SetConsoleCursorInfo**](setconsolecursorinfo.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)