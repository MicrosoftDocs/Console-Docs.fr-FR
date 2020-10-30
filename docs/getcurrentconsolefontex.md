---
title: GetCurrentConsoleFontEx fonction)
description: Consultez les informations de référence sur la fonction GetCurrentConsoleFontEx, qui récupère des informations étendues sur la police de console actuellement utilisée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/GetCurrentConsoleFontEx
- wincon/GetCurrentConsoleFontEx
- GetCurrentConsoleFontEx
MS-HAID:
- base.getcurrentconsolefontex
- consoles.getcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 97d8e730-4110-4be5-b099-0acc1b6f8eb5
topic_type:
- apiref
api_name:
- GetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: e499cdb51a5ca71948dd40ebd3d4d151f2d71a8a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038727"
---
# <a name="getcurrentconsolefontex-function"></a>GetCurrentConsoleFontEx fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Récupère des informations étendues sur la police de la console actuelle.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI GetCurrentConsoleFontEx(
  _In_  HANDLE               hConsoleOutput,
  _In_  BOOL                 bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

## <a name="parameters"></a>Paramètres

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le handle doit avoir le droit d’accès **\_ en lecture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*bMaximumWindow* \[ dans\]  
Si ce paramètre a la **valeur true** , les informations sur la police sont récupérées pour la taille maximale de la fenêtre. Si ce paramètre a la **valeur false** , les informations sur la police sont récupérées pour la taille de fenêtre actuelle.

*lpConsoleCurrentFontEx* \[ à\]  
Pointeur vers une structure [**de \_ police \_ de console INFOEX**](console-font-infoex.md) qui reçoit les informations de police demandées.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows Vista uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2008 \[ uniquement\] |
| En-tête | ConsoleApi3. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[**police de la CONSOLE \_ \_ INFOEX**](console-font-infoex.md)
