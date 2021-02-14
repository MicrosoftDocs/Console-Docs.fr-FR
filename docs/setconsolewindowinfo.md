---
title: SetConsoleWindowInfo fonction)
description: Définit la taille actuelle et la position de la fenêtre d’une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/SetConsoleWindowInfo
- wincon/SetConsoleWindowInfo
- SetConsoleWindowInfo
MS-HAID:
- '\_win32\_setconsolewindowinfo'
- base.setconsolewindowinfo
- consoles.setconsolewindowinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad16a8fe-ca91-41d6-93b1-8cce6d54b1da
topic_type:
- apiref
api_name:
- SetConsoleWindowInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: af3f9d63b01697a2ab0735014a4836d9ab11d8cf
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358529"
---
# <a name="setconsolewindowinfo-function"></a>SetConsoleWindowInfo fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Définit la taille actuelle et la position de la fenêtre d’une mémoire tampon d’écran de la console.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI SetConsoleWindowInfo(
  _In_       HANDLE     hConsoleOutput,
  _In_       BOOL       bAbsolute,
  _In_ const SMALL_RECT *lpConsoleWindow
);
```

## <a name="parameters"></a>Paramètres

*hConsoleOutput* \[entrée\]  
Handle vers la mémoire tampon d’écran de console. Le handle doit avoir le droit d’accès **GENERIC\_READ**. Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).

*bAbsolute* \[ dans\]  
Si ce paramètre a la **valeur true**, les coordonnées spécifient les nouveaux angles supérieur gauche et inférieur droit de la fenêtre. Si la **valeur est false**, les coordonnées sont relatives aux coordonnées de l’angle de la fenêtre active.

*lpConsoleWindow* \[ dans\]  
Pointeur vers une [**petite structure \_ Rect**](small-rect-str.md) qui spécifie les nouveaux angles supérieur gauche et inférieur droit de la fenêtre.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

La fonction échoue si le rectangle de fenêtre spécifié s’étend au-delà des limites de la mémoire tampon d’écran de la console. Cela signifie que les membres **supérieur** et **gauche** du rectangle *lpConsoleWindow* (ou les coordonnées supérieure et gauche CALCULées, si *bAbsolute* est false) ne peuvent pas être inférieurs à zéro. De même, les membres **inférieurs** et **droits** (ou les coordonnées en bas et à droite calculés) ne peuvent pas être supérieurs à (hauteur de la mémoire tampon d’écran – 1) et (largeur de la mémoire tampon de l’écran – 1), respectivement. La fonction échoue également si le membre de **droite** (ou la coordonnée droite calculée) est inférieur ou égal au membre de **gauche** (ou la coordonnée gauche calculée) ou si le membre **inférieur** (ou la coordonnée inférieure calculée) est inférieur ou égal au membre **supérieur** (ou coordonnée supérieure calculée).

Pour les consoles avec plus d’une mémoire tampon d’écran, la modification de l’emplacement de la fenêtre pour une mémoire tampon d’écran n’affecte pas les emplacements des fenêtres des autres mémoires tampons d’écran.

Pour déterminer la taille actuelle et la position de la fenêtre d’une mémoire tampon d’écran, utilisez la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) . Cette fonction retourne également la taille maximale de la fenêtre, selon la taille de la mémoire tampon d’écran actuelle, la taille actuelle de la police et la taille de l’écran. La fonction [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) retourne la taille maximale de la fenêtre en fonction de la taille actuelle de la police et de l’écran, mais elle ne tient pas compte de la taille de la mémoire tampon de l’écran de la console.

**SetConsoleWindowInfo** peut être utilisé pour faire défiler le contenu de la mémoire tampon de l’écran de la console en décalant la position du rectangle de la fenêtre sans modifier sa taille.

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

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

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[Défilement de la mémoire tampon d’écran](scrolling-the-screen-buffer.md)

[**PETIT \_ Rect**](small-rect-str.md)