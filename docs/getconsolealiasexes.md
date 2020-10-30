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
ms.openlocfilehash: 0e818c8ecee8ac777f7cc3cf2394d8846bebd034
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038077"
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
Taille de la mémoire tampon vers laquelle pointe *lpExeNameBuffer* , en octets.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Pour déterminer la taille requise pour la mémoire tampon *lpExeNameBuffer* , utilisez la fonction [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) .

Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0501 ou version ultérieure. Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | ConsoleApi3. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |
| Noms Unicode et ANSI | **GetConsoleAliasExesW** (Unicode) et **GetConsoleAliasExesA** (ANSI) |

## <a name="see-also"></a>Voir aussi

[**AddConsoleAlias**](addconsolealias.md)

[Alias d’une console](console-aliases.md)

[Fonctions de la console](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliasExesLength**](getconsolealiasexeslength.md)

[**GetConsoleAliases**](getconsolealiases.md)
