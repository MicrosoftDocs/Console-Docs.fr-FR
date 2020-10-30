---
title: GetConsoleWindow fonction)
description: Récupère le handle de fenêtre utilisé par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/GetConsoleWindow
- wincon/GetConsoleWindow
- GetConsoleWindow
MS-HAID:
- '\_win32\_getconsolewindow'
- base.getconsolewindow
- consoles.getconsolewindow
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a5ab0b37-45ac-4413-b6ff-73876556ad38
topic_type:
- apiref
api_name:
- GetConsoleWindow
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: c74fe1a29b9ba2ea721e874eb624ea2f8517094c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038807"
---
# <a name="getconsolewindow-function"></a>GetConsoleWindow fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Récupère le handle de fenêtre utilisé par la console associée au processus appelant.

## <a name="syntax"></a>Syntaxe

```C
HWND WINAPI GetConsoleWindow(void);
```

## <a name="parameters"></a>Paramètres

Cette fonction n’a pas de paramètres.

## <a name="return-value"></a>Valeur retournée

La valeur de retour est un handle de la fenêtre utilisée par la console associée au processus appelant ou **null** s’il n’existe aucune console associée.

## <a name="remarks"></a>Remarques

Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0500 ou version ultérieure. Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).


[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

Pour une application hébergée dans une session [**pseudoconsole**](pseudoconsoles.md) , cette fonction retourne un handle de fenêtre pour la file d’attente des messages uniquement. La fenêtre associée n’est pas affichée localement, car _pseudoconsole_ sérialise toutes les actions dans un flux de présentation dans une autre fenêtre de terminal à un autre endroit.

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | ConsoleApi3. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |

</table>

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)
