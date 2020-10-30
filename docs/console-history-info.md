---
title: CONSOLE_HISTORY_INFO, structure
description: Consultez les informations de référence sur la structure CONSOLE_HISTORY_INFO, qui contient des informations sur l’historique de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/CONSOLE_HISTORY_INFO
- wincon/CONSOLE_HISTORY_INFO
- CONSOLE_HISTORY_INFO
- consoleapi3/PCONSOLE_HISTORY_INFO
- wincon/PCONSOLE_HISTORY_INFO
- PCONSOLE_HISTORY_INFO
MS-HAID:
- base.console\_history\_info
- consoles.console\_history\_info
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: df7d2f12-5299-47ed-b1f6-2db903dba81b
topic_type:
- apiref
api_name:
- CONSOLE_HISTORY_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 24d41dca61146cc3e835f405889400ae0d168e7f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039217"
---
# <a name="console_history_info-structure"></a>\_Structure des informations de l’historique de la console \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contient des informations sur l’historique de la console.

## <a name="syntax"></a>Syntaxe

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

## <a name="members"></a>Membres

**cbSize**  
Taille de la structure en octets. Affectez à ce membre la valeur `sizeof(CONSOLE_HISTORY_INFO)` .

**HistoryBufferSize**  
Nombre de commandes conservées dans chaque mémoire tampon de l’historique.

**NumberOfHistoryBuffers**  
Nombre de mémoires tampons d’historique conservées pour ce processus de console.

**dwFlags**  
Ce paramètre peut être égal à zéro ou à la valeur suivante.

| Valeur | Signification |
|-|-|
| **HISTORY_NO_DUP_FLAG** 0x1 | Les entrées en double ne sont pas stockées dans la mémoire tampon de l’historique.

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows Vista uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2008 \[ uniquement\] |
| En-tête | ConsoleApi3. h (via WinCon. h, incluez Windows. h) |

## <a name="see-also"></a>Voir aussi

[**GetConsoleHistoryInfo**](getconsolehistoryinfo.md)

[**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)
