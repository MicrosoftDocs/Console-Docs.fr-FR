---
title: GetLargestConsoleWindowSize fonction)
description: Récupère la taille de la plus grande fenêtre de console possible, en fonction de la police actuelle et de la taille de l’affichage.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/GetLargestConsoleWindowSize
- wincon/GetLargestConsoleWindowSize
- GetLargestConsoleWindowSize
MS-HAID:
- '\_win32\_getlargestconsolewindowsize'
- base.getlargestconsolewindowsize
- consoles.getlargestconsolewindowsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3e5897f3-4987-4a82-ab19-06c0b231ba67
topic_type:
- apiref
api_name:
- GetLargestConsoleWindowSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 086c09b00ba15ad3e1922655fbd9b5f39d872d41
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059113"
---
# <a name="getlargestconsolewindowsize-function"></a>GetLargestConsoleWindowSize fonction)


Récupère la taille de la plus grande fenêtre de console possible, en fonction de la police actuelle et de la taille de l’affichage.

<a name="syntax"></a>Syntaxe
------

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

<a name="parameters"></a>Paramètres
----------

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est une structure de [**repère**](coord-str.md) qui spécifie le nombre de colonnes de cellule de caractères (membre**X** ) et de lignes (membre**Y** ) dans la plus grande fenêtre de console possible. Sinon, les membres de la structure sont nuls.

Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

La fonction ne prend pas en compte la taille de la mémoire tampon d’écran de la console, ce qui signifie que la taille de fenêtre retournée peut être supérieure à la taille de la mémoire tampon d’écran de la console. La fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) peut être utilisée pour déterminer la taille maximale de la fenêtre de console, en fonction de la taille actuelle de la mémoire tampon de l’écran, de la police actuelle et de la taille d’affichage.

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

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[Taille de la mémoire tampon de la fenêtre et de l’écran](window-and-screen-buffer-size.md)

 

 




