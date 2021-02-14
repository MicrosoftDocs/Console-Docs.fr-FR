---
title: ReadConsole fonction)
description: Lit les entrées de caractères à partir de la mémoire tampon d’entrée de la console et les supprime de la mémoire tampon.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/ReadConsole
- wincon/ReadConsole
- ReadConsole
- consoleapi/ReadConsoleA
- wincon/ReadConsoleA
- ReadConsoleA
- consoleapi/ReadConsoleW
- wincon/ReadConsoleW
- ReadConsoleW
MS-HAID:
- '\_win32\_readconsole'
- base.readconsole
- consoles.readconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1aa9ecac-a9b9-4e6d-9206-7a57013de657
topic_type:
- apiref
api_name:
- ReadConsole
- ReadConsoleA
- ReadConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 757d770bc7fea543d15678af5f80f15c17dd0e82
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358279"
---
# <a name="readconsole-function"></a>ReadConsole fonction)

Lit les entrées de caractères à partir de la mémoire tampon d’entrée de la console et les supprime de la mémoire tampon.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI ReadConsole(
  _In_     HANDLE  hConsoleInput,
  _Out_    LPVOID  lpBuffer,
  _In_     DWORD   nNumberOfCharsToRead,
  _Out_    LPDWORD lpNumberOfCharsRead,
  _In_opt_ LPVOID  pInputControl
);
```

## <a name="parameters"></a>Paramètres

*hConsoleInput* \[ dans\]  
Handle vers la mémoire tampon d’entrée de la console. Le handle doit avoir le droit d’accès **GENERIC\_READ**. Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ à\]  
Pointeur vers une mémoire tampon qui reçoit les données lues à partir de la mémoire tampon d’entrée de la console.

*nNumberOfCharsToRead* \[ dans\]  
Nombre de caractères à lire. La taille de la mémoire tampon vers laquelle pointe le paramètre *lpBuffer* doit être au moins égale à `nNumberOfCharsToRead * sizeof(TCHAR)` octets.

*lpNumberOfCharsRead* \[ à\]  
Pointeur vers une variable qui reçoit le nombre de caractères réellement lus.

*pInputControl* \[ dans, facultatif\]  
Pointeur vers une structure [**de \_ \_ contrôle READCONSOLE**](console-readconsole-control.md) de la console qui spécifie un caractère de contrôle pour signaler la fin de l’opération de lecture. Ce paramètre peut être **NULL**.

Ce paramètre nécessite une entrée Unicode par défaut. Pour le mode ANSI, attribuez la valeur **null** à ce paramètre.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

**ReadConsole** lit l’entrée au clavier à partir de la mémoire tampon d’entrée d’une console. Il se comporte comme la fonction [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) , à la différence qu’il peut lire en mode Unicode (caractères larges) ou ANSI. Pour que les applications qui maintiennent un seul ensemble de sources soient compatibles avec les deux modes, utilisez **ReadConsole** plutôt que **ReadFile**. Bien que **ReadConsole** puisse être utilisé uniquement avec un handle de mémoire tampon d’entrée de la console, **ReadFile** peut être utilisé avec d’autres Handles (tels que des fichiers ou des canaux). **ReadConsole** échoue s’il est utilisé avec un handle standard qui a été redirigé pour être autre chose qu’un handle de console.

Tous les modes d’entrée qui affectent le comportement de [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) ont le même effet sur **ReadConsole**. Pour récupérer et définir les modes d’entrée d’une mémoire tampon d’entrée de la console, utilisez les fonctions [**GetConsoleMode**](getconsolemode.md) et [**SetConsoleMode**](setconsolemode.md) .

Si la mémoire tampon d’entrée contient des événements d’entrée autres que des événements de clavier (tels que des événements de souris ou des événements de redimensionnement de fenêtre), ceux-ci sont ignorés. Ces événements peuvent uniquement être lus à l’aide de la fonction [**ReadConsoleInput**](readconsoleinput.md) .

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

Le paramètre *pInputControl* peut être utilisé pour activer les réveils intermédiaires à partir de la lecture en réponse à un caractère de contrôle d’achèvement de fichier spécifié dans une structure de [**\_ \_ contrôle READCONSOLE**](console-readconsole-control.md) de la console. Cette fonctionnalité nécessite l’activation des extensions de commande, le descripteur de sortie standard pour être un handle de sortie de console et l’entrée en Unicode.

**Windows Server 2003 et Windows XP/2000 :** La fonctionnalité de lecture intermédiaire n’est pas prise en charge.

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 2000 Professionnel - \[Applications de bureau uniquement\] |
| Serveur minimal pris en charge | Windows 2000 Server - \[Applications de bureau uniquement\] |
| En-tête | ConsoleApi.h (via WinCon.h, inclure Windows.h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |
| Noms Unicode et ANSI | **ReadConsoleW** (Unicode) et **ReadConsoleA** (ANSI) |

## <a name="see-also"></a>Voir aussi

[Fonctions de console](console-functions.md)

[**\_contrôle READCONSOLE de la console \_**](console-readconsole-control.md)

[**GetConsoleMode**](getconsolemode.md)

[Méthodes d’entrée et de sortie](input-and-output-methods.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleMode**](setconsolemode.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsole**](writeconsole.md)