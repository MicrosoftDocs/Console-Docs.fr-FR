---
title: WriteConsoleInput fonction)
description: Consultez les informations de référence sur la fonction WriteConsoleInput, qui écrit les données directement dans la mémoire tampon d’entrée de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/WriteConsoleInput
- wincon/WriteConsoleInput
- WriteConsoleInput
- consoleapi2/WriteConsoleInputA
- wincon/WriteConsoleInputA
- WriteConsoleInputA
- consoleapi2/WriteConsoleInputW
- wincon/WriteConsoleInputW
- WriteConsoleInputW
MS-HAID:
- '\_win32\_writeconsoleinput'
- base.writeconsoleinput
- consoles.writeconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad06231f-5063-4aff-b14d-8df5e6e42430
topic_type:
- apiref
api_name:
- WriteConsoleInput
- WriteConsoleInputA
- WriteConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e4b9cdae52da2e23ff93e1904c4cb24ebac62831
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357779"
---
# <a name="writeconsoleinput-function"></a>WriteConsoleInput fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Écrit les données directement dans la mémoire tampon d’entrée de la console.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

## <a name="parameters"></a>Paramètres

*hConsoleInput* \[ dans\]  
Handle vers la mémoire tampon d’entrée de la console. Le handle doit avoir le droit d’accès **GENERIC\_WRITE**. Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).

*lpBuffer* \[entrée\]  
Pointeur vers un tableau de structures [**d' \_ enregistrements d’entrée**](input-record-str.md) qui contiennent les données à écrire dans la mémoire tampon d’entrée.

*nLength* \[ dans\]  
Nombre d’enregistrements d’entrée à écrire.

*lpNumberOfEventsWritten* \[ à\]  
Pointeur vers une variable qui reçoit le nombre d’enregistrements d’entrée réellement écrits.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

**WriteConsoleInput** place les enregistrements d’entrée dans la mémoire tampon d’entrée derrière les événements en attente dans la mémoire tampon. Le tampon d’entrée augmente de manière dynamique, si nécessaire, pour contenir autant d’événements que ceux écrits.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Cette API n’est pas recommandée et n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** . Cette décision aligne intentionnellement la plateforme Windows avec d’autres systèmes d’exploitation. Cette opération est considérée comme un **[verbe incorrect](console-buffer-security-and-access-rights.md#wrong-way-verbs)** pour cette mémoire tampon. La communication à distance des applications via des utilitaires multiplateforme et des transports comme SSH peut ne pas fonctionner comme prévu si vous utilisez cette API.

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 2000 Professionnel - \[Applications de bureau uniquement\] |
| Serveur minimal pris en charge | Windows 2000 Server - \[Applications de bureau uniquement\] |
| En-tête | ConsoleApi2. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |
| Noms Unicode et ANSI | **WriteConsoleInputW** (Unicode) et **WriteConsoleInputA** (ANSI) |

## <a name="see-also"></a>Voir aussi

[Fonctions de console](console-functions.md)

[**enregistrement d’entrée \_**](input-record-str.md)

[Fonctions d’entrée de la console de bas niveau](low-level-console-input-functions.md)

[**MapVirtualKey**](/windows/win32/api/winuser/nf-winuser-mapvirtualkeya)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**VkKeyScan**](/windows/win32/api/winuser/nf-winuser-vkkeyscana)