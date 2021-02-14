---
title: GetConsoleAliasExes fonction)
description: Récupère les noms de tous les fichiers exécutables avec les alias de console définis.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/GetConsoleAliasExes
- wincon/GetConsoleAliasExes
- GetConsoleAliasExes
- consoleapi3/GetConsoleAliasExesA
- wincon/GetConsoleAliasExesA
- GetConsoleAliasExesA
- consoleapi3/GetConsoleAliasExesW
- wincon/GetConsoleAliasExesW
- GetConsoleAliasExesW
MS-HAID:
- base.getconsolealiasexes
- consoles.getconsolealiasexes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c229de09-cfa6-4829-9c9a-8ff63500eaf4
topic_type:
- apiref
api_name:
- GetConsoleAliasExes
- GetConsoleAliasExesA
- GetConsoleAliasExesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 1a97df0c22f084389e9bd6df1c4a2e8863090b45
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357492"
---
# <a name="getconsolealiasexes-function"></a>GetConsoleAliasExes fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Récupère les noms de tous les fichiers exécutables avec les alias de console définis.

## <a name="syntax"></a>Syntaxe

```C
DWORD WINAPI GetConsoleAliasExes(
  _Out_ LPTSTR lpExeNameBuffer,
  _In_  DWORD  ExeNameBufferLength
);
```

## <a name="parameters"></a>Paramètres

*lpExeNameBuffer* \[ à\]  
Pointeur vers une mémoire tampon qui reçoit les noms des fichiers exécutables.

*ExeNameBufferLength* \[ dans\]  
Taille de la mémoire tampon vers laquelle pointe *lpExeNameBuffer*, en octets.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

Pour déterminer la taille requise pour la mémoire tampon *lpExeNameBuffer* , utilisez la fonction [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) .

Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0501 ou version ultérieure. Pour plus d’informations, consultez [utilisation des en-têtes Windows](/windows/win32/winprog/using-the-windows-headers).

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 2000 Professionnel - \[Applications de bureau uniquement\] |
| Serveur minimal pris en charge | Windows 2000 Server - \[Applications de bureau uniquement\] |
| En-tête | ConsoleApi3. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |
| Noms Unicode et ANSI | **GetConsoleAliasExesW** (Unicode) et **GetConsoleAliasExesA** (ANSI) |

## <a name="see-also"></a>Voir aussi

[**AddConsoleAlias**](addconsolealias.md)

[Alias d’une console](console-aliases.md)

[Fonctions de console](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliasExesLength**](getconsolealiasexeslength.md)

[**GetConsoleAliases**](getconsolealiases.md)