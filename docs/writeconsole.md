---
title: WriteConsole fonction)
description: Écrit une chaîne de caractères dans une mémoire tampon d’écran de console en commençant à l’emplacement actuel du curseur.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/WriteConsole
- wincon/WriteConsole
- WriteConsole
- consoleapi/WriteConsoleA
- wincon/WriteConsoleA
- WriteConsoleA
- consoleapi/WriteConsoleW
- wincon/WriteConsoleW
- WriteConsoleW
MS-HAID:
- '\_win32\_writeconsole'
- base.writeconsole
- consoles.writeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1a13d9ef-75a9-49fd-9717-207f18612b59
topic_type:
- apiref
api_name:
- WriteConsole
- WriteConsoleA
- WriteConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 9023372cf585e9b3645e7dc0a54e46a665935ad4
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037127"
---
# <a name="writeconsole-function"></a>WriteConsole fonction)

Écrit une chaîne de caractères dans une mémoire tampon d’écran de console en commençant à l’emplacement actuel du curseur.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## <a name="parameters"></a>Paramètres

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le descripteur doit avoir le droit d’accès en **\_ écriture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ dans\]  
Pointeur vers une mémoire tampon qui contient les caractères à écrire dans la mémoire tampon d’écran de la console. Il doit s’agir d’un tableau de `char` pour `WriteConsoleA` ou `wchar_t` pour `WriteConsoleW` .

*nNumberOfCharsToWrite* \[ dans\]  
Nombre de caractères à écrire. Si la taille totale du nombre spécifié de caractères dépasse le tas disponible, la fonction échoue avec une **erreur \_ de \_ \_ mémoire insuffisante** .

*lpNumberOfCharsWritten* \[ out, facultatif\]  
Pointeur vers une variable qui reçoit le nombre de caractères réellement écrits.

*lpReserved* Réservé doit avoir la **valeur null** .

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

La fonction **WriteConsole** écrit des caractères dans la mémoire tampon d’écran de la console à la position actuelle du curseur. La position du curseur avance à mesure que des caractères sont écrits. La fonction [**SetConsoleCursorPosition**](setconsolecursorposition.md) définit la position actuelle du curseur.

Les caractères sont écrits à l’aide des attributs de couleur de premier plan et d’arrière-plan associés à la mémoire tampon d’écran de la console. La fonction [**SetConsoleTextAttribute**](setconsoletextattribute.md) modifie ces couleurs. Pour déterminer les attributs de couleur actuelle et la position actuelle du curseur, utilisez [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).

Tous les modes d’entrée qui affectent le comportement de la fonction [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ont le même effet sur **WriteConsole** . Pour récupérer et définir les modes de sortie d’une mémoire tampon d’écran de la console, utilisez les fonctions [**GetConsoleMode**](getconsolemode.md) et [**SetConsoleMode**](setconsolemode.md) .

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

**WriteConsole** échoue s’il est utilisé avec un handle standard qui est redirigé vers un fichier. Si une application traite une sortie multilingue qui peut être redirigée, déterminez si le descripteur de sortie est un handle de console (une méthode consiste à appeler la fonction [**GetConsoleMode**](getconsolemode.md) et à vérifier si elle est réussie). Si le handle est un handle de console, appelez **WriteConsole** . Si le handle n’est pas un handle de console, la sortie est redirigée et vous devez appeler [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) pour effectuer les e/s. Veillez à faire précéder un fichier texte brut Unicode d’une marque d’ordre d’octet. Pour plus d’informations, consultez [utilisation des marques d’ordre des octets](https://msdn.microsoft.com/library/windows/desktop/dd374101).

Bien qu’une application puisse utiliser **WriteConsole** en mode ANSI pour écrire des caractères ANSI, les consoles ne prennent pas en charge les séquences « ANSI Escape » ou « terminal virtuel », sauf si elles sont activées. Pour plus d’informations et pour la version d’applicabilité du système d’exploitation, consultez [**séquences de terminaux virtuels de la console**](console-virtual-terminal-sequences.md) .

Lorsque les séquences d’échappement des terminaux virtuels ne sont pas activées, les fonctions de la console peuvent fournir des fonctionnalités équivalentes. Pour plus d’informations, consultez [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md)et [**GetConsoleCursorInfo**](getconsolecursorinfo.md).

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | ConsoleApi. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |
| Noms Unicode et ANSI | **WriteConsoleW** (Unicode) et **WriteConsoleA** (ANSI) |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**GetConsoleMode**](getconsolemode.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[Méthodes d’entrée et de sortie](input-and-output-methods.md)

[**ReadConsole**](readconsole.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleMode**](setconsolemode.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleTextAttribute**](setconsoletextattribute.md)

[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)

[**Appel**](https://msdn.microsoft.com/library/windows/desktop/aa365747)
