---
title: GetConsoleOriginalTitle fonction)
description: Consultez les informations de référence sur la fonction GetConsoleOriginalTitle, qui récupère le titre d’origine de la fenêtre de console active.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 109d41a141083fc4691ebaf2546ec8f412f7b861
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059137"
---
# <a name="getconsoleoriginaltitle-function"></a>GetConsoleOriginalTitle fonction)


Récupère le titre d’origine de la fenêtre de console active.

<a name="syntax"></a>Syntaxe
------

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a>Paramètres
----------

*lpConsoleTitle* \[ à\]  
Pointeur vers une mémoire tampon qui reçoit une chaîne se terminant par null et contenant le titre d’origine.

*nSize* \[ dans\]  
Taille de la mémoire tampon *lpConsoleTitle* , en caractères.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est la longueur de la chaîne copiée dans la mémoire tampon, en caractères.

Si la mémoire tampon n’est pas assez grande pour stocker le titre, la valeur de retour est zéro et [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) retourne une **erreur de \_ réussite**.

Si la fonction échoue, la valeur de retour est zéro et [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) retourne le code d’erreur.

<a name="remarks"></a>Remarques
-------

Pour définir le titre d’une fenêtre de console, utilisez la fonction [**SetConsoleTitle**](setconsoletitle.md) . Pour récupérer la chaîne de titre actuelle, utilisez la fonction [**GetConsoleTitle**](getconsoletitle.md) .

Pour compiler une application qui utilise cette fonction, définissez ** \_ Win32 \_ winnt** comme 0x0600 ou version ultérieure. Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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
<td><p>Windows Vista [applications de bureau uniquement]</p></td>
</tr>
<tr class="even">
<td><p>Serveur minimal pris en charge</p></td>
<td><p>Windows Server 2008 [applications de bureau uniquement]</p></td>
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
<td><p><strong>GetConsoleOriginalTitleW</strong> (Unicode) et <strong>GetConsoleOriginalTitleA</strong> (ANSI)</p></td>
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

[**GetConsoleTitle**](getconsoletitle.md)

[**SetConsoleTitle**](setconsoletitle.md)

 

 




