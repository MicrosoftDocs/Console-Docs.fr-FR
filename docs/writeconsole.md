---
title: Fonction WriteConsole
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
ms.localizationpriority: high
ms.openlocfilehash: 27caf0b0a804b99fdfe695efef4c085bf0c51567
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357609"
---
# <a name="writeconsole-function"></a>Fonction WriteConsole

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

*hConsoleOutput* \[entrée\]  
Handle vers la mémoire tampon d’écran de console. Le handle doit avoir le droit d’accès **GENERIC\_WRITE**. Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).

*lpBuffer* \[entrée\]  
Pointeur vers une mémoire tampon qui contient les caractères à écrire dans la mémoire tampon d’écran de console. Il doit s’agir d’un tableau de `char` pour `WriteConsoleA` ou de `wchar_t` pour `WriteConsoleW`.

*nNumberOfCharsToWrite* \[entrée\]  
Nombre de caractères à écrire. Si la taille totale du nombre spécifié de caractères dépasse le tas disponible, la fonction échoue avec **ERROR\_NOT\_ENOUGH\_MEMORY**.

*lpNumberOfCharsWritten* \[sortie, facultatif\]  
Pointeur vers une variable qui reçoit le nombre de caractères réellement écrits.

*lpReserved* Réservé ; doit être **NULL**.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

La fonction **WriteConsole** écrit des caractères dans la mémoire tampon d’écran de console, à la position actuelle du curseur. La position du curseur avance à mesure que des caractères sont écrits. La fonction [**SetConsoleCursorPosition**](setconsolecursorposition.md) définit la position actuelle du curseur.

Les caractères sont écrits en utilisant les attributs de couleur de premier plan et d’arrière-plan associés à la mémoire tampon d’écran de console. La fonction [**SetConsoleTextAttribute**](setconsoletextattribute.md) change ces couleurs. Pour déterminer les attributs de couleur actuels et la position actuelle du curseur, utilisez [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).

Tous les modes d’entrée qui affectent le comportement de la fonction [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) ont le même effet sur **WriteConsole**. Pour récupérer et définir les modes de sortie d’une mémoire tampon d’écran de console, utilisez les fonctions [**GetConsoleMode**](getconsolemode.md) et [**SetConsoleMode**](setconsolemode.md).

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

**WriteConsole** échoue si elle est utilisée avec un handle standard qui est redirigé vers un fichier. Si une application traite une sortie multilingue qui peut être redirigée, déterminez si le handle de sortie est un handle de console (une méthode consiste à appeler la fonction [**GetConsoleMode**](getconsolemode.md) et à vérifier si elle a réussi). Si le handle est un handle de console, appelez **WriteConsole**. Si le handle n’est pas un handle de console, la sortie est redirigée et vous devez appeler [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) pour effectuer les E/S. Veillez à faire précéder un fichier texte brut Unicode par une marque d’ordre des octets. Pour plus d’informations, consultez [Utilisation des marques d’ordre des octets](/windows/win32/intl/using-byte-order-marks).

Bien qu’une application puisse utiliser **WriteConsole** en mode ANSI pour écrire des caractères ANSI, les consoles ne prennent pas en charge les séquences « échappement ANSI » ou « terminal virtuel », sauf si elles sont activées. Pour plus d’informations et l’applicabilité selon la version du système d’exploitation, consultez [**Séquences de terminal virtuel de la console**](console-virtual-terminal-sequences.md).

Quand les séquences d’échappement du terminal virtuel ne sont pas activées, les fonctions de la console peuvent fournir des fonctionnalités équivalentes. Pour plus d’informations, consultez [**SetCursorPos**](/windows/win32/api/winuser/nf-winuser-setcursorpos), [**SetConsoleTextAttribute**](setconsoletextattribute.md) et [**GetConsoleCursorInfo**](getconsolecursorinfo.md).

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 2000 Professionnel - \[Applications de bureau uniquement\] |
| Serveur minimal pris en charge | Windows 2000 Server - \[Applications de bureau uniquement\] |
| En-tête | ConsoleApi.h (via WinCon.h, inclure Windows.h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |
| Noms Unicode et ANSI | **WriteConsoleW** (Unicode) et **WriteConsoleA** (ANSI) |

## <a name="see-also"></a>Voir aussi

[Fonctions de console](console-functions.md)

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

[**SetCursorPos**](/windows/win32/api/winuser/nf-winuser-setcursorpos)

[**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)