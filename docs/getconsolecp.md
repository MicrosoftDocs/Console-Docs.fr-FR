---
title: GetConsoleCP fonction)
description: Récupère la page de codes d’entrée utilisée par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/GetConsoleCP
- wincon/GetConsoleCP
- GetConsoleCP
MS-HAID:
- '\_win32\_getconsolecp'
- base.getconsolecp
- consoles.getconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9e0af6d9-0f5c-45b3-a686-22449d26de47
topic_type:
- apiref
api_name:
- GetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 75570acba7d8572d1bd3f132ac379598d82ec73f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038017"
---
# <a name="getconsolecp-function"></a>GetConsoleCP fonction)

Récupère la page de codes d’entrée utilisée par la console associée au processus appelant. Une console utilise sa page de codes d’entrée pour convertir l’entrée au clavier en valeur de caractère correspondante.

## <a name="syntax"></a>Syntaxe

```C
UINT WINAPI GetConsoleCP(void);
```

## <a name="parameters"></a>Paramètres

Cette fonction n’a pas de paramètres.

## <a name="return-value"></a>Valeur retournée

La valeur de retour est un code qui identifie la page de codes. Pour obtenir la liste des identificateurs, consultez [identificateurs de page de codes](https://msdn.microsoft.com/library/windows/desktop/dd317756).

Si la valeur de retour est égale à zéro, la fonction a échoué. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Une page de codes mappe 256 codes de caractères à des caractères individuels. Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues. Pour obtenir plus d’informations sur une page de codes, y compris son nom, consultez la fonction [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .

Pour définir la page de codes d’entrée d’une console, utilisez la fonction [**SetConsoleCP**](setconsolecp.md) . Pour définir et interroger la page de codes de sortie d’une console, utilisez les fonctions [**SetConsoleOutputCP**](setconsoleoutputcp.md) et [**GetConsoleOutputCP**](getconsoleoutputcp.md) .

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | ConsoleApi. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Pages de code d’une console](console-code-pages.md)

[Fonctions de la console](console-functions.md)

[**GetConsoleOutputCP**](getconsoleoutputcp.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)
