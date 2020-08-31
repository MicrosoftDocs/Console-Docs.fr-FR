---
title: GetNumberOfConsoleMouseButtons fonction)
description: Récupère le nombre de boutons de la souris utilisés par la console actuelle.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetNumberOfConsoleMouseButtons
- wincon/GetNumberOfConsoleMouseButtons
- GetNumberOfConsoleMouseButtons
MS-HAID:
- '\_win32\_getnumberofconsolemousebuttons'
- base.getnumberofconsolemousebuttons
- consoles.getnumberofconsolemousebuttons
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2
topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 67089bd301ac2632f9a99ca24cc2042789f6a3e8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059492"
---
# <a name="getnumberofconsolemousebuttons-function"></a>GetNumberOfConsoleMouseButtons fonction)


Récupère le nombre de boutons de la souris utilisés par la console actuelle.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

<a name="parameters"></a>Paramètres
----------

*lpNumberOfMouseButtons* \[ à\]  
Pointeur vers une variable qui reçoit le nombre de boutons de la souris.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

Quand une console reçoit une entrée de souris, une structure [**d' \_ enregistrement d’entrée**](input-record-str.md) contenant une structure d' [** \_ \_ enregistrement d’événement de souris**](mouse-event-record-str.md) est placée dans la mémoire tampon d’entrée de la console. Le membre **dwButtonState** de **l' \_ \_ enregistrement d’événement de souris** a un bit qui indique l’état de chaque bouton de la souris. Le bit est 1 si le bouton est enfoncé et 0 si le bouton est actif. Pour déterminer le nombre de bits significatifs, utilisez **GetNumberOfConsoleMouseButtons**.

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
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Voir aussi


[Fonctions de la console](console-functions.md)

[Mémoire tampon d’entrée de la console](console-input-buffer.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**enregistrement d’entrée \_**](input-record-str.md)

[**\_enregistrement d’événement de souris \_**](mouse-event-record-str.md)

 

 




