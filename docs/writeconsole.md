---
title: WriteConsole fonction)
description: Écrit une chaîne de caractères dans une mémoire tampon d’écran de console en commençant à l’emplacement actuel du curseur.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
ms.openlocfilehash: de5138326c0800016cf5ca6e3232f032abcd01de
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059512"
---
# <a name="writeconsole-function"></a>WriteConsole fonction)


Écrit une chaîne de caractères dans une mémoire tampon d’écran de console en commençant à l’emplacement actuel du curseur.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

<a name="parameters"></a>Paramètres
----------

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le descripteur doit avoir le droit d’accès en ** \_ écriture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ dans\]  
Pointeur vers une mémoire tampon qui contient les caractères à écrire dans la mémoire tampon d’écran de la console.

*nNumberOfCharsToWrite* \[ dans\]  
Nombre de caractères à écrire. Si la taille totale du nombre spécifié de caractères dépasse le tas disponible, la fonction échoue avec une **erreur \_ de \_ \_ mémoire insuffisante**.

*lpNumberOfCharsWritten* \[ out, facultatif\]  
Pointeur vers une variable qui reçoit le nombre de caractères réellement écrits.

*lpReserved*   
Réservé doit avoir la **valeur null**.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

La fonction **WriteConsole** écrit des caractères dans la mémoire tampon d’écran de la console à la position actuelle du curseur. La position du curseur avance à mesure que des caractères sont écrits. La fonction [**SetConsoleCursorPosition**](setconsolecursorposition.md) définit la position actuelle du curseur.

Les caractères sont écrits à l’aide des attributs de couleur de premier plan et d’arrière-plan associés à la mémoire tampon d’écran de la console. La fonction [**SetConsoleTextAttribute**](setconsoletextattribute.md) modifie ces couleurs. Pour déterminer les attributs de couleur actuelle et la position actuelle du curseur, utilisez [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).

Tous les modes d’entrée qui affectent le comportement de la fonction [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ont le même effet sur **WriteConsole**. Pour récupérer et définir les modes de sortie d’une mémoire tampon d’écran de la console, utilisez les fonctions [**GetConsoleMode**](getconsolemode.md) et [**SetConsoleMode**](setconsolemode.md) .

La fonction **WriteConsole** utilise des caractères Unicode ou ANSI à partir de la page de codes actuelle de la console. La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système. Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .

**WriteConsole** échoue s’il est utilisé avec un handle standard qui est redirigé vers un fichier. Si une application traite une sortie multilingue qui peut être redirigée, déterminez si le descripteur de sortie est un handle de console (une méthode consiste à appeler la fonction [**GetConsoleMode**](getconsolemode.md) et à vérifier si elle est réussie). Si le handle est un handle de console, appelez **WriteConsole**. Si le handle n’est pas un handle de console, la sortie est redirigée et vous devez appeler [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) pour effectuer les e/s. Veillez à faire précéder un fichier texte brut Unicode d’une marque d’ordre d’octet. Pour plus d’informations, consultez [utilisation des marques d’ordre des octets](https://msdn.microsoft.com/library/windows/desktop/dd374101).

Bien qu’une application puisse utiliser **WriteConsole** en mode ANSI pour écrire des caractères ANSI, les consoles ne prennent pas en charge les séquences d’échappement ANSI. Toutefois, certaines fonctions offrent des fonctionnalités équivalentes. Pour plus d’informations, consultez [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md)et [**GetConsoleCursorInfo**](getconsolecursorinfo.md).

<a name="requirements"></a>Configuration requise
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Client minimal pris en charge</p></td>
<td><p>Windows 2000 professionnel [applications de bureau uniquement]</p></td>
</tr>
<tr class="even">
<td><p>Serveur minimal pris en charge</p></td>
<td><p>Serveur Windows 2000 [applications de bureau uniquement]</p></td>
</tr>
<tr class="odd">
<td><p>En-tête</p></td>
<td>ConsoleApi. h (via wincon. h, incluez Windows. h)</td>
</tr>
<tr class="even">
<td><p>Bibliothèque</p></td>
<td>Kernel32. lib</td>
</tr>
<tr class="odd">
<td><p>DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
<td><p>Noms Unicode et ANSI</p></td>
<td><p><strong>WriteConsoleW</strong> (Unicode) et <strong>WriteConsoleA</strong> (ANSI)</p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Voir aussi


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

 

 




