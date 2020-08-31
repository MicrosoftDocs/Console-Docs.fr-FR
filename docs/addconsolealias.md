---
title: AddConsoleAlias fonction)
description: Consultez les informations de référence sur la fonction AddConsoleAlias, qui définit un alias de console pour l’exécutable spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/AddConsoleAlias
- consoleapi3/AddConsoleAliasA
- consoleapi3/AddConsoleAliasW
- wincon/AddConsoleAlias
- wincon/AddConsoleAliasA
- wincon/AddConsoleAliasW
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
MS-HAID:
- base.addconsolealias
- consoles.addconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e4072c3c-cf32-4992-847e-efdb846e5784
topic_type:
- apiref
api_name:
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 108a77b3178e7695e7477ea198df616fa8bcb199
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059389"
---
# <a name="addconsolealias-function"></a>AddConsoleAlias fonction)


Définit un alias de console pour l’exécutable spécifié.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

<a name="parameters"></a>Paramètres
----------

*Source* \[ dans\]  
Alias de la console à mapper au texte spécifié par la *cible*.

*Cible* \[ dans\]  
Texte à substituer à la *source*. Si ce paramètre a la **valeur null**, l’alias de la console est supprimé.

*ExeName* \[ dans\]  
Nom du fichier exécutable pour lequel l’alias de console doit être défini.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est **true**.

Si la fonction échoue, la valeur de retour est **false**. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

Pour compiler une application qui utilise cette fonction, définissez ** \_ Win32 \_ winnt** comme 0x0501 ou version ultérieure. Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

<a name="examples"></a>Exemples
--------

Pour obtenir un exemple, consultez [alias de console](console-aliases.md).

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
<td><p><strong>AddConsoleAliasW</strong> (Unicode) et <strong>AddConsoleAliasA</strong> (ANSI)</p></td>
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


[Alias de console](console-aliases.md)

[Fonctions de la console](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)

 

 




