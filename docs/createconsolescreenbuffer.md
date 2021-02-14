---
title: CreateConsoleScreenBuffer fonction)
description: La fonction CreateConsoleScreenBuffer crée une mémoire tampon d’écran pour la console Windows.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/CreateConsoleScreenBuffer
- wincon/CreateConsoleScreenBuffer
- CreateConsoleScreenBuffer
MS-HAID:
- '\_win32\_createconsolescreenbuffer'
- base.createconsolescreenbuffer
- consoles.createconsolescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98bb74e4-dad2-4615-9263-48ba778a06ff
topic_type:
- apiref
api_name:
- CreateConsoleScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0e7e4606e561454a2037650cc8d1f3b685ff2d5d
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357959"
---
# <a name="createconsolescreenbuffer-function"></a>CreateConsoleScreenBuffer fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Crée une mémoire tampon d’écran de la console.

## <a name="syntax"></a>Syntaxe

```C
HANDLE WINAPI CreateConsoleScreenBuffer(
  _In_             DWORD               dwDesiredAccess,
  _In_             DWORD               dwShareMode,
  _In_opt_   const SECURITY_ATTRIBUTES *lpSecurityAttributes,
  _In_             DWORD               dwFlags,
  _Reserved_       LPVOID              lpScreenBufferData
);
```

## <a name="parameters"></a>Paramètres

*dwDesiredAccess* \[ dans\]  
Accès à la mémoire tampon d’écran de la console. Pour obtenir la liste des droits d’accès, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*dwShareMode* \[ dans\]  
Ce paramètre peut être égal à zéro, ce qui indique que la mémoire tampon ne peut pas être partagée ou qu’il peut s’agir d’une ou plusieurs des valeurs suivantes.

| Valeur | Signification |
|-|-|
| **FILE_SHARE_READ** 0x00000001 | D’autres opérations ouvertes peuvent être effectuées dans la mémoire tampon d’écran de la console pour l’accès en lecture. |
| **FILE_SHARE_WRITE** 0x00000002 | D’autres opérations ouvertes peuvent être effectuées dans la mémoire tampon d’écran de la console pour l’accès en écriture. |

*lpSecurityAttributes* \[ dans, facultatif\]  
Pointeur vers une structure [**d' \_ attributs de sécurité**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85)) qui détermine si le handle retourné peut être hérité par les processus enfants. Si *lpSecurityAttributes* a la **valeur null**, le handle ne peut pas être hérité. Le membre **lpSecurityDescriptor** de la structure spécifie un descripteur de sécurité pour la nouvelle mémoire tampon d’écran de la console. Si *lpSecurityAttributes* a la **valeur null**, la mémoire tampon d’écran de la console obtient un descripteur de sécurité par défaut. Les listes de contrôle d’accès dans le descripteur de sécurité par défaut pour une mémoire tampon d’écran de console proviennent du jeton principal ou d’emprunt d’identité du créateur.

*dwFlags* \[ dans\]  
Type de mémoire tampon d’écran de console à créer. Le seul type de mémoire tampon d’écran pris en charge est la **\_ \_ mémoire tampon** de la console.

*lpScreenBufferData*  
Réservé doit avoir la **valeur null**.

## <a name="return-value"></a>Valeur de retour

Si la fonction est réussie, la valeur de retour est un handle vers la nouvelle mémoire tampon d’écran de la console.

Si la fonction échoue, la valeur de retour est **INVALID\_HANDLE\_VALUE**. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

Une console peut avoir plusieurs mémoires tampons d’écran, mais une seule mémoire tampon d’écran active. La lecture et l’écriture de tampons d’écran inactifs sont accessibles en lecture et en écriture, mais seule la mémoire tampon d’écran active s’affiche. Pour faire du nouvel écran la mémoire tampon d’écran active, utilisez la fonction [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) .

La mémoire tampon d’écran nouvellement créée copie des propriétés à partir de la mémoire tampon d’écran active au moment où cette fonction est appelée. Le comportement est le suivant :

- `Font` -copié à partir de la mémoire tampon d’écran active
- `Display Window Size` -copié à partir de la mémoire tampon d’écran active
- `Buffer Size` -correspond à `Display Window Size` (**non** copié)
- `Default Attributes` (couleurs)-copié à partir de la mémoire tampon d’écran active
- `Default Popup Attributes` (couleurs)-copié à partir de la mémoire tampon d’écran active

Le processus appelant peut utiliser le handle retourné dans toute fonction qui requiert un handle vers une mémoire tampon d’écran de la console, selon les limitations d’accès spécifiées par le paramètre *dwDesiredAccess* .

Le processus appelant peut utiliser la fonction [**DuplicateHandle**](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle) pour créer un handle de mémoire tampon d’écran en double qui a un accès ou une héritage différent du handle d’origine. Toutefois, vous ne pouvez pas utiliser **DuplicateHandle** pour créer un doublon valide pour un autre processus (sauf par héritage).

Pour fermer le descripteur de la mémoire tampon de l’écran de la console, utilisez la fonction [**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle) .

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [lecture et écriture de blocs de caractères et d’attributs](reading-and-writing-blocks-of-characters-and-attributes.md).

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 2000 Professionnel - \[Applications de bureau uniquement\] |
| Serveur minimal pris en charge | Windows 2000 Server - \[Applications de bureau uniquement\] |
| En-tête | ConsoleApi2. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de console](console-functions.md)

[Mémoires tampons d’écran d’une console](console-screen-buffers.md)

[**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle)

[**DuplicateHandle**](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**attributs de sécurité \_**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85))

[**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)