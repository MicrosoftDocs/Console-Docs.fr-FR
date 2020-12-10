---
title: Fonction AllocConsole
description: Consultez les informations de référence sur la fonction AllocConsole, qui alloue une nouvelle console pour le processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/AllocConsole
- wincon/AllocConsole
- AllocConsole
MS-HAID:
- '\_win32\_allocconsole'
- base.allocconsole
- consoles.allocconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bdf3bf2f-8eb8-4ba6-bf3a-a67b29dffda2
topic_type:
- apiref
api_name:
- AllocConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: c63c9a176c0d8ca2ef4342f7bee1b427eae00014
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420168"
---
# <a name="allocconsole-function"></a>Fonction AllocConsole

Alloue une nouvelle console pour le processus appelant.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI AllocConsole(void);
```

## <a name="parameters"></a>Paramètres

Cette fonction n’a pas de paramètres.

## <a name="return-value"></a>Valeur retournée

Si la fonction aboutit, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Un processus peut être associé à une seule console. Par conséquent, la fonction **AllocConsole** échoue si le processus appelant dispose déjà d’une console. Un processus peut utiliser la fonction [**FreeConsole**](freeconsole.md) pour se détacher de sa console actuelle, puis appeler **AllocConsole** pour créer une nouvelle console ou [**AttachConsole**](attachconsole.md) pour effectuer l’attachement à une autre console.

Si le processus appelant crée un processus enfant, l’enfant hérite de la nouvelle console.

**AllocConsole** Initialise une entrée standard, une sortie standard et des handles d’erreur standard pour la nouvelle console. Le handle d’entrée standard est un handle vers la mémoire tampon d’entrée de la console, et les handles de sortie standard et d’erreur standard sont des handles vers la mémoire tampon d’écran de la console. Pour récupérer ces handles, utilisez la fonction [**GetStdHandle**](getstdhandle.md).

Cette fonction est principalement utilisée par une application d’interface graphique utilisateur (GUI) pour créer une fenêtre de console. Les applications GUI sont initialisées sans console. Les applications console sont initialisées à l’aide d’une console, sauf si elles sont créées en tant que processus détachés (en appelant la fonction [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) avec l’indicateur **DETACHED\_PROCESS**).

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 2000 Professionnel \[applications de bureau uniquement\] |
| Serveur minimal pris en charge | Windows 2000 Server \[applications de bureau uniquement\] |
| En-tête | ConsoleApi.h (via WinCon.h, include Windows.h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de console](console-functions.md)

[Consoles](consoles.md)

[**AttachConsole**](attachconsole.md)

[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[**FreeConsole**](freeconsole.md)

[**GetStdHandle**](getstdhandle.md)
