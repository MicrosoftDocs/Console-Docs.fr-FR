---
title: CreateConsoleScreenBuffer fonction)
description: La fonction CreateConsoleScreenBuffer crée une mémoire tampon d’écran pour la console Windows.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
ms.openlocfilehash: 289908708fb1c89c3ec3d990c9e8bf2649914a1b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059237"
---
# <a name="createconsolescreenbuffer-function"></a>CreateConsoleScreenBuffer fonction)


Crée une mémoire tampon d’écran de la console.

<a name="syntax"></a>Syntaxe
------

```C
HANDLE WINAPI CreateConsoleScreenBuffer(
  _In_             DWORD               dwDesiredAccess,
  _In_             DWORD               dwShareMode,
  _In_opt_   const SECURITY_ATTRIBUTES *lpSecurityAttributes,
  _In_             DWORD               dwFlags,
  _Reserved_       LPVOID              lpScreenBufferData
);
```

<a name="parameters"></a>Paramètres
----------

*dwDesiredAccess* \[ dans\]  
Accès à la mémoire tampon d’écran de la console. Pour obtenir la liste des droits d’accès, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*dwShareMode* \[ dans\]  
Ce paramètre peut être égal à zéro, ce qui indique que la mémoire tampon ne peut pas être partagée ou qu’il peut s’agir d’une ou plusieurs des valeurs suivantes.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Value</th>
<th>Signification</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="FILE_SHARE_READ"></span><span id="file_share_read"></span>
<strong>FILE_SHARE_READ</strong> 0x00000001</td>
<td><p>D’autres opérations ouvertes peuvent être effectuées dans la mémoire tampon d’écran de la console pour l’accès en lecture.</p></td>
</tr>
<tr class="even">
<td><span id="FILE_SHARE_WRITE"></span><span id="file_share_write"></span>
<strong>FILE_SHARE_WRITE</strong> 0x00000002</td>
<td><p>D’autres opérations ouvertes peuvent être effectuées dans la mémoire tampon d’écran de la console pour l’accès en écriture.</p></td>
</tr>
</tbody>
</table>

 

*lpSecurityAttributes* \[ dans, facultatif\]  
Pointeur vers une structure [**d' \_ attributs de sécurité**](https://msdn.microsoft.com/library/windows/desktop/aa379560) qui détermine si le handle retourné peut être hérité par les processus enfants. Si *lpSecurityAttributes* a la **valeur null**, le handle ne peut pas être hérité. Le membre **lpSecurityDescriptor** de la structure spécifie un descripteur de sécurité pour la nouvelle mémoire tampon d’écran de la console. Si *lpSecurityAttributes* a la **valeur null**, la mémoire tampon d’écran de la console obtient un descripteur de sécurité par défaut. Les listes de contrôle d’accès dans le descripteur de sécurité par défaut pour une mémoire tampon d’écran de console proviennent du jeton principal ou d’emprunt d’identité du créateur.

*dwFlags* \[ dans\]  
Type de mémoire tampon d’écran de console à créer. Le seul type de mémoire tampon d’écran pris en charge est la ** \_ \_ mémoire tampon**de la console.

*lpScreenBufferData*   
Réservé doit avoir la **valeur null**.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est un handle vers la nouvelle mémoire tampon d’écran de la console.

Si la fonction échoue, la valeur de retour est une ** \_ \_ valeur de handle non valide**. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

Une console peut avoir plusieurs mémoires tampons d’écran, mais une seule mémoire tampon d’écran active. La lecture et l’écriture de tampons d’écran inactifs sont accessibles en lecture et en écriture, mais seule la mémoire tampon d’écran active s’affiche. Pour faire du nouvel écran la mémoire tampon d’écran active, utilisez la fonction [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) .

La mémoire tampon d’écran nouvellement créée copie des propriétés à partir de la mémoire tampon d’écran active au moment où cette fonction est appelée. Le comportement est le suivant :
- `Font` -copié à partir de la mémoire tampon d’écran active
- `Display Window Size` -copié à partir de la mémoire tampon d’écran active
- `Buffer Size` -correspond à `Display Window Size` (**non** copié)
- `Default Attributes` (couleurs)-copié à partir de la mémoire tampon d’écran active
- `Default Popup Attributes` (couleurs)-copié à partir de la mémoire tampon d’écran active

Le processus appelant peut utiliser le handle retourné dans toute fonction qui requiert un handle vers une mémoire tampon d’écran de la console, selon les limitations d’accès spécifiées par le paramètre *dwDesiredAccess* .

Le processus appelant peut utiliser la fonction [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) pour créer un handle de mémoire tampon d’écran en double qui a un accès ou une héritage différent du handle d’origine. Toutefois, vous ne pouvez pas utiliser **DuplicateHandle** pour créer un doublon valide pour un autre processus (sauf par héritage).

Pour fermer le descripteur de la mémoire tampon de l’écran de la console, utilisez la fonction [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) .

<a name="examples"></a>Exemples
--------

Pour obtenir un exemple, consultez [lecture et écriture de blocs de caractères et d’attributs](reading-and-writing-blocks-of-characters-and-attributes.md).

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
<td>ConsoleApi2. h (via wincon. h, incluez Windows. h)</td>
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
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Voir aussi


[Fonctions de la console](console-functions.md)

[Mémoires tampons d’écran de la console](console-screen-buffers.md)

[**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211)

[**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**attributs de sécurité \_**](https://msdn.microsoft.com/library/windows/desktop/aa379560)

[**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)

 

 




