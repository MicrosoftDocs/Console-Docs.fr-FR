---
title: GetConsoleAliasesLength fonction)
description: Récupère la taille requise pour la mémoire tampon utilisée par la fonction GetConsoleAliases.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetConsoleAliasesLength
- wincon/GetConsoleAliasesLength
- GetConsoleAliasesLength
- consoleapi3/GetConsoleAliasesLengthA
- wincon/GetConsoleAliasesLengthA
- GetConsoleAliasesLengthA
- consoleapi3/GetConsoleAliasesLengthW
- wincon/GetConsoleAliasesLengthW
- GetConsoleAliasesLengthW
MS-HAID:
- base.getconsolealiaseslength
- consoles.getconsolealiaseslength
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 29e49eba-0864-4ed7-af82-1ba639261c40
topic_type:
- apiref
api_name:
- GetConsoleAliasesLength
- GetConsoleAliasesLengthA
- GetConsoleAliasesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 23d820574aab837c89f2598e9934536b91715426
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059173"
---
# <a name="getconsolealiaseslength-function"></a>GetConsoleAliasesLength fonction)


Récupère la taille requise pour la mémoire tampon utilisée par la fonction [**GetConsoleAliases**](getconsolealiases.md) .

<a name="syntax"></a>Syntaxe
------

```C
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

<a name="parameters"></a>Paramètres
----------

*lpExeName* \[ dans\]  
Nom du fichier exécutable dont les alias de console doivent être récupérés.

<a name="return-value"></a>Valeur retournée
------------

Taille de la mémoire tampon requise pour stocker tous les alias de console définis pour ce fichier exécutable, en octets.

<a name="remarks"></a>Remarques
-------

Pour compiler une application qui utilise cette fonction, définissez ** \_ Win32 \_ winnt** comme 0x0501 ou version ultérieure. Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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
<td>ConsoleApi3. h (via wincon. h, incluez Windows. h)</td>
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
<td><p><strong>GetConsoleAliasesLengthW</strong> (Unicode) et <strong>GetConsoleAliasesLengthA</strong> (ANSI)</p></td>
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


[**AddConsoleAlias**](addconsolealias.md)

[Alias de console](console-aliases.md)

[Fonctions de la console](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)

 

 




