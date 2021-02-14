---
title: GetConsoleScreenBufferInfo fonction)
description: Consultez les informations de référence sur la fonction GetConsoleScreenBufferInfo, qui récupère des informations sur la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfo
- wincon/GetConsoleScreenBufferInfo
- GetConsoleScreenBufferInfo
ms.assetid: eafe819e-a99a-4ce1-8898-8860444a31af
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 2f80f77b749fc9e9dc0aebf4507b0c41f589e40c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358909"
---
# <a name="getconsolescreenbufferinfo-function"></a>GetConsoleScreenBufferInfo fonction)

Récupère des informations sur la mémoire tampon d’écran de console spécifiée.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

## <a name="parameters"></a>Paramètres

*hConsoleOutput* \[entrée\]  
Handle vers la mémoire tampon d’écran de console. Le handle doit avoir le droit d’accès **GENERIC\_READ**. Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).

*lpConsoleScreenBufferInfo* \[ à\]  
Pointeur vers une structure [**d' \_ \_ \_ informations de mémoire tampon d’écran de console**](console-screen-buffer-info-str.md) qui reçoit les informations de mémoire tampon d’écran de la console.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

Le rectangle retourné dans le membre **srWindow** de la structure des [**\_ \_ \_ informations de mémoire tampon**](console-screen-buffer-info-str.md) de l’écran de la console peut être modifié, puis transmis à la fonction [**SetConsoleWindowInfo**](setconsolewindowinfo.md) pour faire défiler la mémoire tampon de l’écran de la console dans la fenêtre, pour modifier la taille de la fenêtre, ou les deux.

Toutes les coordonnées retournées dans la structure des [**\_ \_ \_ informations de mémoire tampon**](console-screen-buffer-info-str.md) de l’écran de la console sont exprimées en coordonnées de cellule de caractères, où l’origine (0,0) se trouve dans l’angle supérieur gauche de la mémoire tampon d’écran de la console.

> [!TIP]
> Cette API n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** . Son utilisation peut toujours être requise pour les applications qui tentent de dessiner des colonnes, des grilles ou de remplir l’affichage pour récupérer la taille de la fenêtre. Cet état de la fenêtre est géré par TTY/PTY/Pseudoconsole en dehors du flux de flux normal, et est généralement considéré comme un privilège utilisateur non réglable par l’application cliente. Les mises à jour peuvent être reçues sur [**ReadConsoleInput**](readconsoleinput.md).

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [défilement de la fenêtre d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-window.md).

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

[**\_ \_ informations sur la mémoire tampon d’écran de la console \_**](console-screen-buffer-info-str.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[Taille de la mémoire tampon de la fenêtre et de l’écran](window-and-screen-buffer-size.md)