---
title: GetNumberOfConsoleInputEvents fonction)
description: Récupère le nombre d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/GetNumberOfConsoleInputEvents
- wincon/GetNumberOfConsoleInputEvents
- GetNumberOfConsoleInputEvents
MS-HAID:
- '\_win32\_getnumberofconsoleinputevents'
- base.getnumberofconsoleinputevents
- consoles.getnumberofconsoleinputevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1083b4f1-8fa6-4054-a516-3b447c3b0130
topic_type:
- apiref
api_name:
- GetNumberOfConsoleInputEvents
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: b4cad78d35114c509f4e810a858e6ae3b8bfb644
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038687"
---
# <a name="getnumberofconsoleinputevents-function"></a>GetNumberOfConsoleInputEvents fonction)

Récupère le nombre d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée de la console.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

## <a name="parameters"></a>Paramètres

*hConsoleInput* \[ dans\]  
Handle vers la mémoire tampon d’entrée de la console. Le handle doit avoir le droit d’accès **\_ en lecture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*lpcNumberOfEvents* \[ à\]  
Pointeur vers une variable qui reçoit le nombre d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée de la console.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

La fonction **GetNumberOfConsoleInputEvents** signale le nombre total d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée, y compris les enregistrements d’entrée de clavier, de souris et de redimensionnement de fenêtre. Les processus utilisant la fonction [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ou [**ReadConsole**](readconsole.md) peuvent uniquement lire les entrées au clavier. Les processus qui utilisent la fonction [**ReadConsoleInput**](readconsoleinput.md) peuvent lire tous les types d’enregistrements d’entrée.

Un processus peut spécifier un handle de mémoire tampon d’entrée de la console dans l’une des [fonctions Wait](https://msdn.microsoft.com/library/windows/desktop/ms687069) pour déterminer le moment où une entrée de console n’est pas lue. Lorsque la mémoire tampon d’entrée n’est pas vide, l’état d’un handle de mémoire tampon d’entrée de la console est signalé.

Pour lire les enregistrements d’entrée d’une mémoire tampon d’entrée de la console sans affecter le nombre d’enregistrements non lus, utilisez la fonction [**PeekConsoleInput**](peekconsoleinput.md) . Pour ignorer tous les enregistrements non lus dans le tampon d’entrée d’une console, utilisez la fonction [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | ConsoleApi. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

[Fonctions d’entrée de la console de bas niveau](low-level-console-input-functions.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsole**](readconsole.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)
