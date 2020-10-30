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
ms.openlocfilehash: 4bbb14dd501d483f35fbce5e1a729eaf002b1579
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039397"
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

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le handle doit avoir le droit d’accès **\_ en lecture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*lpConsoleCursorInfo* \[ dans\]  
Pointeur vers une structure [**d' \_ \_ informations de curseur de console**](console-cursor-info-str.md) qui fournit les nouvelles spécifications pour le curseur de la mémoire tampon d’écran de la console.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Lorsque le curseur d’une mémoire tampon d’écran est visible, son apparence peut varier, du remplissage complet d’une cellule de caractère à l’affichage sous forme de ligne horizontale au bas de la cellule. Le membre **dwSize nul** de la structure d' [**\_ \_ informations du curseur**](console-cursor-info-str.md) de la console spécifie le pourcentage d’une cellule de caractère qui est remplie par le curseur. Si ce membre est inférieur à 1 ou supérieur à 100, **SetConsoleCursorInfo** échoue.

> [!TIP]
> Cette API a un **[terminal virtuel](console-virtual-terminal-sequences.md)** équivalent dans la section **[visibilité du curseur](console-virtual-terminal-sequences.md#cursor-visibility)** avec les `^[[?25h` `^[[?25l` séquences et. 

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | ConsoleApi2. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[Mémoires tampons d’écran d’une console](console-screen-buffers.md)

[**\_informations sur le curseur de la console \_**](console-cursor-info-str.md)

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)
