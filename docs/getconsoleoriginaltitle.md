---
title: GetConsoleOriginalTitle fonction)
description: Consultez les informations de référence sur la fonction GetConsoleOriginalTitle, qui récupère le titre d’origine de la fenêtre de console active.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: ad12ff7b931b6bbc36a7fb0e9e0ee2ac3512a1f5
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037997"
---
# <a name="getconsoleoriginaltitle-function"></a>GetConsoleOriginalTitle fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Récupère le titre d’origine de la fenêtre de console active.

## <a name="syntax"></a>Syntaxe

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a>Paramètres

*lpConsoleTitle* \[ à\]  
Pointeur vers une mémoire tampon qui reçoit une chaîne se terminant par null et contenant le titre d’origine.

*nSize* \[ dans\]  
Taille de la mémoire tampon *lpConsoleTitle* , en caractères.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est la longueur de la chaîne copiée dans la mémoire tampon, en caractères.

Si la mémoire tampon n’est pas assez grande pour stocker le titre, la valeur de retour est zéro et [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) retourne une **erreur de \_ réussite** .

Si la fonction échoue, la valeur de retour est zéro et [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) retourne le code d’erreur.

## <a name="remarks"></a>Remarques

Pour définir le titre d’une fenêtre de console, utilisez la fonction [**SetConsoleTitle**](setconsoletitle.md) . Pour récupérer la chaîne de titre actuelle, utilisez la fonction [**GetConsoleTitle**](getconsoletitle.md) .

Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0600 ou version ultérieure. Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

> [!TIP]
> Cette API n’est pas recommandée et n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** . Cette décision aligne intentionnellement la plateforme Windows avec d’autres systèmes d’exploitation. La communication à distance des applications via des utilitaires multiplateforme et des transports comme SSH peut ne pas fonctionner comme prévu si vous utilisez cette API.

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows Vista uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2008 \[ uniquement\] |
| En-tête | ConsoleApi2. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |
| Noms Unicode et ANSI | **GetConsoleOriginalTitleW** (Unicode) et **GetConsoleOriginalTitleA** (ANSI) |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[**GetConsoleTitle**](getconsoletitle.md)

[**SetConsoleTitle**](setconsoletitle.md)
