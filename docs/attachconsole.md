---
title: AttachConsole fonction)
description: Consultez les informations de référence sur la fonction AttachConsole, qui attache le processus appelant à la console du processus spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- base.attachconsole
- consoles.attachconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: bfc71c10a02e9ed8a0bc18fd26cffa855012c692
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037477"
---
# <a name="attachconsole-function"></a>AttachConsole fonction)

Joint le processus appelant à la console du processus spécifié en tant qu’application cliente.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

## <a name="parameters"></a>Paramètres

*dwProcessId* \[ dans\]  
Identificateur du processus dont la console doit être utilisée. Ce paramètre peut prendre l’une des valeurs suivantes.

| Valeur | Signification |
|-|-|
| *ELECTRIQUE* | Utilisez la console du processus spécifié. |
| **Attacher \_ \_processus parent**`(DWORD)-1` | Utilisez la console du parent du processus en cours. |

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Un processus peut être attaché à au plus une console. Si le processus appelant est déjà attaché à une console, le code d’erreur retourné est **erreur \_ accès \_ refusé** ( `5` ). Si le processus spécifié n’a pas de console, le code d’erreur retourné **est \_ erreur \_ handle non valide** ( `6` ). Si le processus spécifié n’existe pas, le code d’erreur retourné est **erreur : \_ \_ paramètre non valide** ( `87` ).

Un processus peut utiliser la fonction [**FreeConsole**](freeconsole.md) pour se détacher de sa console. Si d’autres processus partagent la console, la console n’est pas détruite, mais le processus qui a appelé **FreeConsole** ne peut pas y faire référence. Une console est fermée lorsque le dernier processus qui lui est associé se termine ou appelle **FreeConsole** . Une fois qu’un processus a appelé **FreeConsole** , il peut appeler la fonction [**AllocConsole**](allocconsole.md) pour créer une nouvelle console ou **AttachConsole** à attacher à une autre console.

Cette fonction est surtout utile pour les applications qui ont été liées avec [**/SUBSYSTEM : Windows**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem), ce qui implique au système d’exploitation qu’une console n’est pas nécessaire avant d’entrer dans la méthode main du programme. Dans cette instance, les handles standard récupérés avec [**GetStdHandle**](getstdhandle.md) seront probablement non valides au démarrage tant que **AttachConsole** n’est pas appelé. L’exception est si l’application est lancée avec l’héritage de handle par son processus parent.

Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme `0x0501` ou une version ultérieure. Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows XP uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2003 \[ uniquement\] |
| En-tête | ConsoleApi. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[Consoles](consoles.md)

[**AllocConsole**](allocconsole.md)

[**FreeConsole**](freeconsole.md)

[**GetConsoleProcessList**](getconsoleprocesslist.md)
