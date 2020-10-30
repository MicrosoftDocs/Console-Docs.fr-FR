---
title: GetConsoleFontSize fonction)
description: Récupère la taille de la police utilisée par la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/GetConsoleFontSize
- wincon/GetConsoleFontSize
- GetConsoleFontSize
MS-HAID:
- '\_win32\_getconsolefontsize'
- base.getconsolefontsize
- consoles.getconsolefontsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 51b1f58d-b3fb-4e09-8398-671b3959bb01
topic_type:
- apiref
api_name:
- GetConsoleFontSize
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 39a27f2bd2c4578296ee5699503ce86487060db3
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038897"
---
# <a name="getconsolefontsize-function"></a>GetConsoleFontSize fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Récupère la taille de la police utilisée par la mémoire tampon d’écran de console spécifiée.

## <a name="syntax"></a>Syntaxe

```C
COORD WINAPI GetConsoleFontSize(
  _In_ HANDLE hConsoleOutput,
  _In_ DWORD  nFont
);
```

## <a name="parameters"></a>Paramètres

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le handle doit avoir le droit d’accès **\_ en lecture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*nFont* \[ dans\]  
Index de la police dont la taille doit être récupérée. Cet index est obtenu en appelant la fonction [**GetCurrentConsoleFont**](getcurrentconsolefont.md) .

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est une structure de [**repère**](coord-str.md) qui contient la largeur et la hauteur de chaque caractère de la police, en unités logiques. Le membre **X** contient la largeur, tandis que le membre **Y** contient la hauteur.

Si la fonction échoue, la largeur et la hauteur sont égales à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0500 ou version ultérieure. Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows XP uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2003 \[ uniquement\] |
| En-tête | ConsoleApi3. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[Mémoires tampons d’écran d’une console](console-screen-buffers.md)

[**COORDONNÉES**](coord-str.md)

[**GetCurrentConsoleFont**](getcurrentconsolefont.md)
