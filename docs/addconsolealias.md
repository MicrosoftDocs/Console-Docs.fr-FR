---
title: AddConsoleAlias fonction)
description: Consultez les informations de référence sur la fonction AddConsoleAlias, qui définit un alias de console pour l’exécutable spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/AddConsoleAlias
- consoleapi3/AddConsoleAliasA
- consoleapi3/AddConsoleAliasW
- wincon/AddConsoleAlias
- wincon/AddConsoleAliasA
- wincon/AddConsoleAliasW
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
MS-HAID:
- base.addconsolealias
- consoles.addconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e4072c3c-cf32-4992-847e-efdb846e5784
topic_type:
- apiref
api_name:
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 2f2396122e693ab76ddf4e4e0bcdb2d38a2c042b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037550"
---
# <a name="addconsolealias-function"></a>AddConsoleAlias fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Définit un alias de console pour l’exécutable spécifié.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

## <a name="parameters"></a>Paramètres

*Source* \[ dans\]  
Alias de la console à mapper au texte spécifié par la *cible* .

*Cible* \[ dans\]  
Texte à substituer à la *source* . Si ce paramètre a la **valeur null** , l’alias de la console est supprimé.

*ExeName* \[ dans\]  
Nom du fichier exécutable pour lequel l’alias de console doit être défini.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est **true** .

Si la fonction échoue, la valeur de retour est **false** . Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0501 ou version ultérieure. Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [alias de console](console-aliases.md).

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | ConsoleApi3. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |
| Noms Unicode et ANSI | **AddConsoleAliasW** (Unicode) et **AddConsoleAliasA** (ANSI) |

## <a name="see-also"></a>Voir aussi

[Alias d’une console](console-aliases.md)

[Fonctions de la console](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)
