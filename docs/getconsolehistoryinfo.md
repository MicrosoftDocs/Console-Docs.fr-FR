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
ms.openlocfilehash: a26dbeb2a873bd780f91c240bf2658cde11b45ec
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359019"
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

## <a name="return-value"></a>Valeur de retour

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

Si le processus appelant n’est pas un processus de console, la fonction échoue et définit la dernière erreur sur **erreur \_ accès \_ refusé**.

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows Vista uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2008 \[ uniquement\] |
| En-tête | ConsoleApi3. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de console](console-functions.md)

[**\_informations sur l’historique de la console \_**](console-history-info.md)

[**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)