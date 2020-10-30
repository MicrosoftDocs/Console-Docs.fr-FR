---
title: GetConsoleTitle fonction)
description: Récupère le titre et la taille du titre pour la fenêtre de console active.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/GetConsoleTitle
- wincon/GetConsoleTitle
- GetConsoleTitle
- consoleapi2/GetConsoleTitleA
- wincon/GetConsoleTitleA
- GetConsoleTitleA
- consoleapi2/GetConsoleTitleW
- wincon/GetConsoleTitleW
- GetConsoleTitleW
MS-HAID:
- '\_win32\_getconsoletitle'
- base.getconsoletitle
- consoles.getconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c58bba36-9813-4bdc-83bf-30d55f8d7d79
topic_type:
- apiref
api_name:
- GetConsoleTitle
- GetConsoleTitleA
- GetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-Ms-Win-Core-Console-Ansi-L2-1-0.dll
- Kernel32Legacy.dll
api_type:
- DllExport
ms.openlocfilehash: 23b52ba1d5dde40ef842297249fdd2f87cebcb12
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037877"
---
# <a name="getconsoletitle-function"></a>GetConsoleTitle fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Récupère le titre de la fenêtre de console active.

## <a name="syntax"></a>Syntaxe

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a>Paramètres

*lpConsoleTitle* \[ à\]  
Pointeur vers une mémoire tampon qui reçoit une chaîne se terminant par null et contenant le titre. Si la mémoire tampon est trop petite pour stocker le titre, la fonction stocke autant de caractères du titre que ceux qui sont contenus dans la mémoire tampon, se terminant par une marque de fin null.

*nSize* \[ dans\]  
Taille de la mémoire tampon vers laquelle pointe le paramètre *lpConsoleTitle* , en caractères.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est la longueur du titre de la fenêtre de console, en caractères.

Si la fonction échoue, la valeur de retour est zéro et [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) retourne le code d’erreur.

## <a name="remarks"></a>Remarques

Pour définir le titre d’une fenêtre de console, utilisez la fonction [**SetConsoleTitle**](setconsoletitle.md) . Pour récupérer la chaîne de titre d’origine, utilisez la fonction [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) .

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Cette API n’est pas recommandée et n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** . Cette décision aligne intentionnellement la plateforme Windows avec d’autres systèmes d’exploitation. La communication à distance des applications via des utilitaires multiplateforme et des transports comme SSH peut ne pas fonctionner comme prévu si vous utilisez cette API.

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [**SetConsoleTitle**](setconsoletitle.md).

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | ConsoleApi2. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |
| Noms Unicode et ANSI | **GetConsoleTitleW** (Unicode) et **GetConsoleTitleA** (ANSI) |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleTitle**](setconsoletitle.md)
