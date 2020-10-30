---
title: GetConsoleDisplayMode fonction)
description: Consultez les informations de référence sur la fonction GetConsoleDisplayMode, qui récupère le mode d’affichage de la console actuelle.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 74dc06cbb7ecadb0f86c4c4a992e3526be8ab74d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038057"
---
# <a name="getconsoledisplaymode-function"></a>GetConsoleDisplayMode fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Récupère le mode d’affichage de la console actuelle.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

## <a name="parameters"></a>Paramètres

*lpModeFlags* \[ à\]  
Mode d’affichage de la console. Ce paramètre peut être une ou plusieurs des valeurs suivantes.

| Valeur | Signification |
|-|-|
| **CONSOLE_FULLSCREEN** 1 | Console plein écran. La console est dans ce mode dès que la fenêtre est agrandie. À ce stade, la transition vers le mode plein écran peut encore échouer. |
| **CONSOLE_FULLSCREEN_HARDWARE** 2 | La console plein écran communique directement avec le matériel vidéo. Ce mode est défini une fois que la console est en mode **CONSOLE_FULLSCREEN** pour indiquer que la transition vers le mode plein écran est terminée. |

> [!NOTE]
> La transition vers un mode matériel vidéo plein écran 100% a été supprimée dans Windows Vista avec le changement de plate-forme de la pile Graphics sur [WDDM](https://docs.microsoft.com//windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model). Dans les versions ultérieures de Windows, l’état maximal résultant est **CONSOLE_FULLSCREEN** représentant une fenêtre sans trame qui s’affiche en plein écran, mais qui n’est pas en contrôle exclusif du matériel.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0500 ou version ultérieure. Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows XP uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2003 \[ uniquement\] |
| En-tête | ConsoleApi3. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[Modes de la console](console-modes.md)

[**SetConsoleDisplayMode**](setconsoledisplaymode.md)
