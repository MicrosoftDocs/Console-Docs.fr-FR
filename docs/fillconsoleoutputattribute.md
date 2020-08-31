---
title: FillConsoleOutputAttribute fonction)
description: Définit les attributs de caractère pour un nombre spécifié de cellules de caractères, en commençant aux coordonnées spécifiées dans une mémoire tampon d’écran.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/FillConsoleOutputAttribute
- wincon/FillConsoleOutputAttribute
- FillConsoleOutputAttribute
MS-HAID:
- '\_win32\_fillconsoleoutputattribute'
- base.fillconsoleoutputattribute
- consoles.fillconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 09440263-71c4-4b7a-8fc6-a2b4fcd677ff
topic_type:
- apiref
api_name:
- FillConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4b3df3a9922655835979136a33628e2be0663f4e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059209"
---
# <a name="fillconsoleoutputattribute-function"></a>FillConsoleOutputAttribute fonction)


Définit les attributs de caractère pour un nombre spécifié de cellules de caractères, en commençant aux coordonnées spécifiées dans une mémoire tampon d’écran.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

<a name="parameters"></a>Paramètres
----------

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le descripteur doit avoir le droit d’accès en ** \_ écriture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*wAttribute* \[ dans\]  
Attributs à utiliser lors de l’écriture dans la mémoire tampon d’écran de la console. Pour plus d’informations, consultez [attributs de caractères](console-screen-buffers.md#_win32_font_attributes).

*nLength* \[ dans\]  
Nombre de cellules de caractères à définir avec les attributs de couleur spécifiés.

*dwWriteCoord* \[ dans\]  
Structure de [**repère**](coord-str.md) qui spécifie les coordonnées de caractère de la première cellule dont les attributs doivent être définis.

*lpNumberOfAttrsWritten* \[ à\]  
Pointeur vers une variable qui reçoit le nombre de cellules de caractères dont les attributs ont été réellement définis.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

Si le nombre de cellules de caractères dont les attributs doivent être définis s’étend au-delà de la fin de la ligne spécifiée dans la mémoire tampon d’écran de la console, les cellules de la ligne suivante sont définies. Si le nombre de cellules à écrire dépasse la fin de la mémoire tampon d’écran de la console, les cellules sont écrites jusqu’à la fin de la mémoire tampon d’écran de la console.

Les valeurs de caractère aux positions écrites dans ne sont pas modifiées.

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

[**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)

[Fonctions de sortie de la console de bas niveau](low-level-console-output-functions.md)

[**SetConsoleTextAttribute**](setconsoletextattribute.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

 

 




