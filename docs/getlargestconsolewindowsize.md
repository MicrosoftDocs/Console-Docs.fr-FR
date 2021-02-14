---
title: GetLargestConsoleWindowSize fonction)
description: Récupère la taille de la plus grande fenêtre de console possible, en fonction de la police actuelle et de la taille de l’affichage.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/GetLargestConsoleWindowSize
- wincon/GetLargestConsoleWindowSize
- GetLargestConsoleWindowSize
MS-HAID:
- '\_win32\_getlargestconsolewindowsize'
- base.getlargestconsolewindowsize
- consoles.getlargestconsolewindowsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3e5897f3-4987-4a82-ab19-06c0b231ba67
topic_type:
- apiref
api_name:
- GetLargestConsoleWindowSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 3fe4ddf83f25f1951defed52eaf8fea18e1ff2dc
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358869"
---
# <a name="getlargestconsolewindowsize-function"></a>GetLargestConsoleWindowSize fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Récupère la taille de la plus grande fenêtre de console possible, en fonction de la police actuelle et de la taille de l’affichage.

## <a name="syntax"></a>Syntaxe

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a>Paramètres

*hConsoleOutput* \[entrée\]  
Handle vers la mémoire tampon d’écran de console.

## <a name="return-value"></a>Valeur de retour

Si la fonction est réussie, la valeur de retour est une structure de [**repère**](coord-str.md) qui spécifie le nombre de colonnes de cellule de caractères (membre **X** ) et de lignes (membre **Y** ) dans la plus grande fenêtre de console possible. Sinon, les membres de la structure sont nuls.

Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

La fonction ne prend pas en compte la taille de la mémoire tampon d’écran de la console, ce qui signifie que la taille de fenêtre retournée peut être supérieure à la taille de la mémoire tampon d’écran de la console. La fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) peut être utilisée pour déterminer la taille maximale de la fenêtre de console, en fonction de la taille actuelle de la mémoire tampon de l’écran, de la police actuelle et de la taille d’affichage.

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

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

[**COORDONNÉES**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[Taille de la mémoire tampon de la fenêtre et de l’écran](window-and-screen-buffer-size.md)