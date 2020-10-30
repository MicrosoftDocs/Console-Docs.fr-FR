---
title: GetConsoleHistoryInfo fonction)
description: Consultez les informations de référence sur la fonction GetConsoleHistoryInfo, qui récupère les paramètres d’historique de la console du processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/GetConsoleHistoryInfo
- wincon/GetConsoleHistoryInfo
- GetConsoleHistoryInfo
MS-HAID:
- base.getconsolehistoryinfo
- consoles.getconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 145008b3-8a4a-4e6a-9144-ee787ce90ef4
topic_type:
- apiref
api_name:
- GetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 8335b7e23ffec0e894221f97f2c01be5b081d31f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038027"
---
# <a name="getconsolehistoryinfo-function"></a>GetConsoleHistoryInfo fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Récupère les paramètres d’historique pour la console du processus appelant.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a>Paramètres

*lpConsoleHistoryInfo* \[ à\]  
Pointeur vers une structure [**d' \_ \_ informations d’historique**](console-history-info.md) de la console qui reçoit les paramètres d’historique de la console du processus appelant.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Si le processus appelant n’est pas un processus de console, la fonction échoue et définit la dernière erreur sur **erreur \_ accès \_ refusé** .

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows Vista uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2008 \[ uniquement\] |
| En-tête | ConsoleApi3. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[**\_informations sur l’historique de la console \_**](console-history-info.md)

[**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)
