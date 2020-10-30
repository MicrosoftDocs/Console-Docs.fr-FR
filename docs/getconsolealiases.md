---
title: GetConsoleAliases fonction)
description: Récupère tous les alias de console définis pour l’exécutable spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/GetConsoleAliases
- wincon/GetConsoleAliases
- GetConsoleAliases
- consoleapi3/GetConsoleAliasesA
- wincon/GetConsoleAliasesA
- GetConsoleAliasesA
- consoleapi3/GetConsoleAliasesW
- wincon/GetConsoleAliasesW
- GetConsoleAliasesW
MS-HAID:
- base.getconsolealiases
- consoles.getconsolealiases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 92eefa4e-ffde-4886-afde-5aecf450b425
topic_type:
- apiref
api_name:
- GetConsoleAliases
- GetConsoleAliasesA
- GetConsoleAliasesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: a84579ce7bf27787e986ded2e1f21520f8d442b9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038117"
---
# <a name="getconsolealiases-function"></a>GetConsoleAliases fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Récupère tous les alias de console définis pour l’exécutable spécifié.

## <a name="syntax"></a>Syntaxe

```C
DWORD WINAPI GetConsoleAliases(
  _Out_ LPTSTR lpAliasBuffer,
  _In_  DWORD  AliasBufferLength,
  _In_  LPTSTR lpExeName
);
```

## <a name="parameters"></a>Paramètres

*lpAliasBuffer* \[ à\]  
Pointeur vers une mémoire tampon qui reçoit les alias.

Le format des données est le suivant : *Source1* = *target1* \\ 0 *source2* = *TARGET2* \\ 0... *SourceN* = *Ciblen* \\ 0, où *N* est le nombre d’alias de console définis.

*AliasBufferLength* \[ dans\]  
Taille de la mémoire tampon vers laquelle pointe *lpAliasBuffer* , en octets.

*lpExeName* \[ dans\]  
Fichier exécutable dont les alias doivent être récupérés.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Pour déterminer la taille requise pour la mémoire tampon *lpExeName* , utilisez la fonction [**GetConsoleAliasesLength**](getconsolealiaseslength.md) .

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
| Noms Unicode et ANSI | **GetConsoleAliasesW** (Unicode) et **GetConsoleAliasesA** (ANSI) |

## <a name="see-also"></a>Voir aussi

[**AddConsoleAlias**](addconsolealias.md)

[Alias d’une console](console-aliases.md)

[Fonctions de la console](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliasesLength**](getconsolealiaseslength.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)
