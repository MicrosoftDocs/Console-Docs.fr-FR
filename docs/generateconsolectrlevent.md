---
title: GenerateConsoleCtrlEvent fonction)
description: Envoie un signal spécifié à un groupe de processus de console qui partage la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/GenerateConsoleCtrlEvent
- wincon/GenerateConsoleCtrlEvent
- GenerateConsoleCtrlEvent
MS-HAID:
- '\_win32\_generateconsolectrlevent'
- base.generateconsolectrlevent
- consoles.generateconsolectrlevent
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ed392d97-6fd0-4256-a783-bc7d27d01a10
topic_type:
- apiref
api_name:
- GenerateConsoleCtrlEvent
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4002ec67000edda38c7b14476528a0167e521bbf
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357529"
---
# <a name="generateconsolectrlevent-function"></a>GenerateConsoleCtrlEvent fonction)

Envoie un signal spécifié à un groupe de processus de console qui partage la console associée au processus appelant.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI GenerateConsoleCtrlEvent(
  _In_ DWORD dwCtrlEvent,
  _In_ DWORD dwProcessGroupId
);
```

## <a name="parameters"></a>Paramètres

*dwCtrlEvent* \[ dans\]  
Type de signal à générer. Ce paramètre peut prendre les valeurs suivantes.

| Valeur | Signification |
|-|-|
| **CTRL_C_EVENT** 0 | Génère un signal CTRL + C. Ce signal ne peut pas être généré pour les groupes de processus. Si *dwProcessGroupId* est différent de zéro, cette fonction est réussie, mais le signal Ctrl + C n’est pas reçu par les processus au sein du groupe de processus spécifié. |
| **CTRL_BREAK_EVENT** 1 | Génère un signal CTRL + ATTN. |

*dwProcessGroupId* \[ dans\]  
Identificateur du groupe de processus devant recevoir le signal. Un groupe de processus est créé lorsque l’indicateur de création d’un **\_ nouveau \_ \_ groupe de processus** est spécifié dans un appel à la fonction [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) . L’identificateur de processus du nouveau processus est également l’identificateur de groupe de processus d’un nouveau groupe de processus. Le groupe de processus comprend tous les processus qui sont des descendants du processus racine. Seuls les processus du groupe qui partagent la même console que le processus appelant reçoivent le signal. En d’autres termes, si un processus du groupe crée une nouvelle console, ce processus ne reçoit pas le signal, ni ses descendants.

Si ce paramètre est égal à zéro, le signal est généré dans tous les processus qui partagent la console du processus appelant.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

**GenerateConsoleCtrlEvent** entraîne l’appel des fonctions du gestionnaire de contrôle des processus dans le groupe cible. Tous les processus de console ont une fonction de gestionnaire par défaut qui appelle la fonction [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) . Un processus de console peut utiliser la fonction [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) pour installer ou supprimer d’autres fonctions de gestionnaire.

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) peut également activer un attribut pouvant être hérité qui amène le processus appelant à ignorer les signaux Ctrl + C. Si **GenerateConsoleCtrlEvent** envoie un signal Ctrl + C à un processus pour lequel cet attribut est activé, les fonctions de gestionnaire pour ce processus ne sont pas appelées. Les signaux CTRL + ATTN entraînent toujours l’appel des fonctions du gestionnaire.

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 2000 Professionnel - \[Applications de bureau uniquement\] |
| Serveur minimal pris en charge | Windows 2000 Server - \[Applications de bureau uniquement\] |
| En-tête | ConsoleApi2. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Gestionnaires de contrôle d’une console](console-control-handlers.md)

[Fonctions de console](console-functions.md)

[**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)

[**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess)

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md)