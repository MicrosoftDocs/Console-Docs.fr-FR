---
title: SetConsoleCursorPosition fonction)
description: Consultez les informations de référence sur la fonction SetConsoleCursorPosition, qui définit la position du curseur dans la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/SetConsoleCursorPosition
- wincon/SetConsoleCursorPosition
- SetConsoleCursorPosition
MS-HAID:
- '\_win32\_setconsolecursorposition'
- base.setconsolecursorposition
- consoles.setconsolecursorposition
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8e9abada-a64e-429f-8286-ced1169c7104
topic_type:
- apiref
api_name:
- SetConsoleCursorPosition
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: eaa50df16248597f1054f0741113ecc9be1f3264
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059405"
---
# <a name="setconsolecursorposition-function"></a>SetConsoleCursorPosition fonction)


Définit la position du curseur dans la mémoire tampon d’écran de console spécifiée.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

<a name="parameters"></a>Paramètres
----------

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le handle doit avoir le droit d’accès ** \_ en lecture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*dwCursorPosition* \[ dans\]  
Structure de [**repère**](coord-str.md) qui spécifie la nouvelle position du curseur, en caractères. Les coordonnées sont la colonne et la ligne d’une cellule de caractère de mémoire tampon d’écran. Les coordonnées doivent se trouver dans les limites de la mémoire tampon d’écran de la console.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

La position du curseur détermine l’emplacement d’affichage des caractères écrits par la fonction [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ou [**WriteConsole**](writeconsole.md) , ou renvoyé par la fonction [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ou [**ReadConsole**](readconsole.md) . Pour déterminer la position actuelle du curseur, utilisez la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .

Si la nouvelle position du curseur ne se trouve pas dans les limites de la fenêtre de la mémoire tampon de l’écran de la console, l’origine de la fenêtre change pour rendre le curseur visible.

<a name="examples"></a>Exemples
--------

Pour obtenir un exemple, consultez [utilisation des fonctions d’entrée et de sortie de haut niveau](using-the-high-level-input-and-output-functions.md).

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

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetConsoleCursorInfo**](setconsolecursorinfo.md)

[**WriteConsole**](writeconsole.md)

[**Appel**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




