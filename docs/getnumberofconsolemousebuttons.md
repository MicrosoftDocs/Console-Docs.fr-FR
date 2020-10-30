---
title: GetNumberOfConsoleMouseButtons fonction)
description: Récupère le nombre de boutons de la souris utilisés par la console actuelle.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/GetNumberOfConsoleMouseButtons
- wincon/GetNumberOfConsoleMouseButtons
- GetNumberOfConsoleMouseButtons
MS-HAID:
- '\_win32\_getnumberofconsolemousebuttons'
- base.getnumberofconsolemousebuttons
- consoles.getnumberofconsolemousebuttons
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2
topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 96a63f3d35170ed419ceb90a063044a93c0b1951
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037827"
---
# <a name="getnumberofconsolemousebuttons-function"></a>GetNumberOfConsoleMouseButtons fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Récupère le nombre de boutons de la souris utilisés par la console actuelle.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

## <a name="parameters"></a>Paramètres

*lpNumberOfMouseButtons* \[ à\]  
Pointeur vers une variable qui reçoit le nombre de boutons de la souris.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Quand une console reçoit une entrée de souris, une structure [**d' \_ enregistrement d’entrée**](input-record-str.md) contenant une structure d' [**\_ \_ enregistrement d’événement de souris**](mouse-event-record-str.md) est placée dans la mémoire tampon d’entrée de la console. Le membre **dwButtonState** de **l' \_ \_ enregistrement d’événement de souris** a un bit qui indique l’état de chaque bouton de la souris. Le bit est 1 si le bouton est enfoncé et 0 si le bouton est actif. Pour déterminer le nombre de bits significatifs, utilisez **GetNumberOfConsoleMouseButtons** .

> [!TIP]
> Cette API n’est pas recommandée et n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** . Cette décision aligne intentionnellement la plateforme Windows avec d’autres systèmes d’exploitation. Cet État s’applique uniquement à l’utilisateur local, à la session et au contexte de privilège. La communication à distance des applications via des utilitaires multiplateforme et des transports comme SSH peut ne pas fonctionner comme prévu si vous utilisez cette API.

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | ConsoleApi3. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[Mémoire tampon d’entrée d’une console](console-input-buffer.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**enregistrement d’entrée \_**](input-record-str.md)

[**\_enregistrement d’événement de souris \_**](mouse-event-record-str.md)
