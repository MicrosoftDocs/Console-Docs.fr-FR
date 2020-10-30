---
title: GetConsoleOutputCP fonction)
description: Récupère la page de codes de sortie utilisée par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/GetConsoleOutputCP
- wincon/GetConsoleOutputCP
- GetConsoleOutputCP
MS-HAID:
- '\_win32\_getconsoleoutputcp'
- base.getconsoleoutputcp
- consoles.getconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c23706c7-ce17-4825-a494-20ca44534d45
topic_type:
- apiref
api_name:
- GetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 30276765b35e9179767fa4e82fc40643ee3b2558
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038817"
---
# <a name="getconsoleoutputcp-function"></a>GetConsoleOutputCP fonction)

Récupère la page de codes de sortie utilisée par la console associée au processus appelant. Une console utilise sa page de codes de sortie pour convertir les valeurs de caractères écrites par les différentes fonctions de sortie dans les images affichées dans la fenêtre de la console.

## <a name="syntax"></a>Syntaxe

```C
UINT WINAPI GetConsoleOutputCP(void);
```

## <a name="parameters"></a>Paramètres

Cette fonction n’a pas de paramètres.

## <a name="return-value"></a>Valeur retournée

La valeur de retour est un code qui identifie la page de codes. Pour obtenir la liste des identificateurs, consultez [identificateurs de page de codes](https://msdn.microsoft.com/library/windows/desktop/dd317756).

Si la valeur de retour est égale à zéro, la fonction a échoué. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Une page de codes mappe 256 codes de caractères à des caractères individuels. Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues. Pour obtenir plus d’informations sur une page de codes, y compris son nom, consultez la fonction [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .

Pour définir la page de codes de sortie d’une console, utilisez la fonction [**SetConsoleOutputCP**](setconsoleoutputcp.md) . Pour définir et interroger la page de codes d’entrée d’une console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) et [**GetConsoleCP**](getconsolecp.md) .

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

[**GetConsoleCP**](getconsolecp.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)
