---
title: FillConsoleOutputCharacter fonction)
description: Écrit un caractère dans la mémoire tampon d’écran de la console un nombre spécifié de fois, en commençant aux coordonnées spécifiées.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/FillConsoleOutputCharacter
- wincon/FillConsoleOutputCharacter
- FillConsoleOutputCharacter
- consoleapi2/FillConsoleOutputCharacterA
- wincon/FillConsoleOutputCharacterA
- FillConsoleOutputCharacterA
- consoleapi2/FillConsoleOutputCharacterW
- wincon/FillConsoleOutputCharacterW
- FillConsoleOutputCharacterW
MS-HAID:
- '\_win32\_fillconsoleoutputcharacter'
- base.fillconsoleoutputcharacter
- consoles.fillconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 37579cc9-14b3-4fd9-81ed-abaad5c7bd1a
topic_type:
- apiref
api_name:
- FillConsoleOutputCharacter
- FillConsoleOutputCharacterA
- FillConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d11e0ef196f9923f1478e17faacd41b43a0511eb
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059212"
---
# <a name="fillconsoleoutputcharacter-function"></a>FillConsoleOutputCharacter fonction)


Écrit un caractère dans la mémoire tampon d’écran de la console un nombre spécifié de fois, en commençant aux coordonnées spécifiées.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

<a name="parameters"></a>Paramètres
----------

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le descripteur doit avoir le droit d’accès en ** \_ écriture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*cCharacter* \[ dans\]  
Caractère à écrire dans la mémoire tampon d’écran de la console.

*nLength* \[ dans\]  
Nombre de cellules de caractères dans lesquelles le caractère doit être écrit.

*dwWriteCoord* \[ dans\]  
Structure de [**repère**](coord-str.md) qui spécifie les coordonnées de caractère de la première cellule dans laquelle le caractère doit être écrit.

*lpNumberOfCharsWritten* \[ à\]  
Pointeur vers une variable qui reçoit le nombre de caractères réellement écrits dans la mémoire tampon d’écran de la console.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

Si le nombre de caractères à écrire dépasse la fin de la ligne spécifiée dans la mémoire tampon d’écran de la console, les caractères sont écrits sur la ligne suivante. Si le nombre de caractères à écrire dépasse la fin de la mémoire tampon d’écran de la console, les caractères sont écrits jusqu’à la fin de la mémoire tampon d’écran de la console.

Les valeurs d’attribut aux positions écrites ne sont pas modifiées.

Cette fonction utilise des caractères Unicode ou 8 bits à partir de la page de codes actuelle de la console. La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système. Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .

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
<td><p>Noms Unicode et ANSI</p></td>
<td><p><strong>FillConsoleOutputCharacterW</strong> (Unicode) et <strong>FillConsoleOutputCharacterA</strong> (ANSI)</p></td>
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

[**COORDONNÉES**](coord-str.md)

[**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)

[Fonctions de sortie de la console de bas niveau](low-level-console-output-functions.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)

 

 




