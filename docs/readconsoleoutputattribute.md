---
title: ReadConsoleOutputAttribute fonction)
description: Copie un nombre spécifié d’attributs de caractères à partir de cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/ReadConsoleOutputAttribute
- wincon/ReadConsoleOutputAttribute
- ReadConsoleOutputAttribute
MS-HAID:
- '\_win32\_readconsoleoutputattribute'
- base.readconsoleoutputattribute
- consoles.readconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c3e35779-a487-47f1-8d07-0d5fae99d54a
topic_type:
- apiref
api_name:
- ReadConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d4cf3ac9b85c3eab73c3530c1fd9991a7fbbf5a5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059465"
---
# <a name="readconsoleoutputattribute-function"></a>ReadConsoleOutputAttribute fonction)


Copie un nombre spécifié d’attributs de caractères à partir de cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI ReadConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPWORD  lpAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfAttrsRead
);
```

<a name="parameters"></a>Paramètres
----------

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le handle doit avoir le droit d’accès ** \_ en lecture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*lpAttribute* \[ à\]  
Pointeur vers une mémoire tampon qui reçoit les attributs utilisés par la mémoire tampon d’écran de la console.

Pour plus d’informations, consultez [attributs de caractères](console-screen-buffers.md#_win32_font_attributes).

*nLength* \[ dans\]  
Nombre de cellules de caractères de la mémoire tampon d’écran à partir desquelles lire. La taille de la mémoire tampon vers laquelle pointe le paramètre *lpAttribute* doit être `nLength * sizeof(WORD)` .

*dwReadCoord* \[ dans\]  
Coordonnées de la première cellule dans la mémoire tampon d’écran de la console à partir de laquelle lire, en caractères. Le membre **X** de la structure [**Coord**](coord-str.md) est la colonne et le membre **Y** est la ligne.

*lpNumberOfAttrsRead* \[ à\]  
Pointeur vers une variable qui reçoit le nombre d’attributs réellement lus.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

Si le nombre d’attributs à lire est supérieur à la fin de la ligne de mémoire tampon d’écran spécifiée, les attributs sont lus à partir de la ligne suivante. Si le nombre d’attributs à lire s’étend au-delà de la fin de la mémoire tampon de l’écran de la console, les attributs jusqu’à la fin de la mémoire tampon de l’écran de la console sont lus.

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

[**COORDONNÉES**](coord-str.md)

[Fonctions de sortie de la console de bas niveau](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)

 

 




