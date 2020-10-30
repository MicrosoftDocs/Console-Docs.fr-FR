---
title: GetConsoleScreenBufferInfoEx fonction)
description: Récupère des informations étendues sur la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfoEx
- wincon/GetConsoleScreenBufferInfoEx
- GetConsoleScreenBufferInfoEx
MS-HAID:
- base.getconsolescreenbufferinfoex
- consoles.getconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 60534226-d26f-44e2-a4cc-64811882e308
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 5f4b0f11821b7d5b61c61d4ab8f9774c4a69eec0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037937"
---
# <a name="getconsolescreenbufferinfoex-function"></a>GetConsoleScreenBufferInfoEx fonction)

Récupère des informations étendues sur la mémoire tampon d’écran de console spécifiée.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI GetConsoleScreenBufferInfoEx(
  _In_  HANDLE                        hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a>Paramètres

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le handle doit avoir le droit d’accès **\_ en lecture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*lpConsoleScreenBufferInfoEx* \[ à\]  
Une [**structure \_ \_ \_ INFOEX de mémoire tampon d’écran**](console-screen-buffer-infoex.md) de la console qui reçoit les informations de mémoire tampon d’écran de console demandées.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Le rectangle retourné dans le membre **srWindow** de la structure INFOEX de la [**\_ \_ mémoire tampon \_ d’écran**](console-screen-buffer-infoex.md) de la console peut être modifié, puis transmis à la fonction [**SetConsoleWindowInfo**](setconsolewindowinfo.md) pour faire défiler la mémoire tampon de l’écran de la console dans la fenêtre, pour modifier la taille de la fenêtre, ou les deux.

Toutes les coordonnées retournées dans la structure INFOEX de la [**\_ \_ mémoire tampon \_ d’écran**](console-screen-buffer-infoex.md) de la console sont exprimées en coordonnées de cellule de caractères, où l’origine (0,0) se trouve dans l’angle supérieur gauche de la mémoire tampon d’écran de la console.

> [!TIP]
> Cette API n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** . Son utilisation peut toujours être requise pour les applications qui tentent de dessiner des colonnes, des grilles ou de remplir l’affichage pour récupérer la taille de la fenêtre. Cet état de la fenêtre est géré par TTY/PTY/Pseudoconsole en dehors du flux de flux normal, et est généralement considéré comme un privilège utilisateur non réglable par l’application cliente. Les mises à jour peuvent être reçues sur [**ReadConsoleInput**](readconsoleinput.md).

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows Vista uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2008 \[ uniquement\] |
| En-tête | ConsoleApi2. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[**mémoire tampon d’écran de la CONSOLE \_ \_ \_ INFOEX**](console-screen-buffer-infoex.md)

[**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md)
