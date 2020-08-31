---
title: GetConsoleWindow fonction)
description: Récupère le handle de fenêtre utilisé par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetConsoleWindow
- wincon/GetConsoleWindow
- GetConsoleWindow
MS-HAID:
- '\_win32\_getconsolewindow'
- base.getconsolewindow
- consoles.getconsolewindow
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a5ab0b37-45ac-4413-b6ff-73876556ad38
topic_type:
- apiref
api_name:
- GetConsoleWindow
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: dd356bab4674da0cc090e42911829dee994fa8b1
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059108"
---
# <a name="getconsolewindow-function"></a>GetConsoleWindow fonction)


Récupère le handle de fenêtre utilisé par la console associée au processus appelant.

<a name="syntax"></a>Syntaxe
------

```C
HWND WINAPI GetConsoleWindow(void);
```

<a name="parameters"></a>Paramètres
----------

Cette fonction n’a pas de paramètres.

<a name="return-value"></a>Valeur retournée
------------

La valeur de retour est un handle de la fenêtre utilisée par la console associée au processus appelant ou **null** s’il n’existe aucune console associée.

<a name="remarks"></a>Remarques
-------

Pour compiler une application qui utilise cette fonction, définissez ** \_ Win32 \_ winnt** comme 0x0500 ou version ultérieure. Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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

 

 




