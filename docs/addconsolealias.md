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
ms.openlocfilehash: 9ff901615fa2a17ee9902bd028a2f63ee6b7a4b4
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357869"
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
Alias de la console à mapper au texte spécifié par la *cible*.

*Cible* \[ dans\]  
Texte à substituer à la *source*. Si ce paramètre a la **valeur null**, l’alias de la console est supprimé.

*ExeName* \[ dans\]  
Nom du fichier exécutable pour lequel l’alias de console doit être défini.

## <a name="return-value"></a>Valeur de retour

Si la fonction est réussie, la valeur de retour est **true**.

Si la fonction échoue, la valeur de retour est **false**. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0501 ou version ultérieure. Pour plus d’informations, consultez [utilisation des en-têtes Windows](/windows/win32/winprog/using-the-windows-headers).

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [alias de console](console-aliases.md).

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 2000 Professionnel - \[Applications de bureau uniquement\] |
| Serveur minimal pris en charge | Windows 2000 Server - \[Applications de bureau uniquement\] |
| En-tête | ConsoleApi3. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |
| Noms Unicode et ANSI | **AddConsoleAliasW** (Unicode) et **AddConsoleAliasA** (ANSI) |

## <a name="see-also"></a>Voir aussi

[Alias d’une console](console-aliases.md)

[Fonctions de console](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)