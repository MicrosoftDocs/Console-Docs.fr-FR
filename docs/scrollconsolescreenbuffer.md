---
title: ScrollConsoleScreenBuffer fonction)
description: Consultez les informations de référence sur la fonction ScrollConsoleScreenBuffer, qui déplace un bloc de données dans une mémoire tampon d’écran.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/ScrollConsoleScreenBuffer
- wincon/ScrollConsoleScreenBuffer
- ScrollConsoleScreenBuffer
- consoleapi2/ScrollConsoleScreenBufferA
- wincon/ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferA
- consoleapi2/ScrollConsoleScreenBufferW
- wincon/ScrollConsoleScreenBufferW
- ScrollConsoleScreenBufferW
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d78bf4c9-2314-466c-b617-619259c824b5
topic_type:
- apiref
api_name:
- ScrollConsoleScreenBuffer
- ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: f0dd67ecc28907913e10efa8c06a544656d08dc6
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059437"
---
# <a name="scrollconsolescreenbuffer-function"></a>ScrollConsoleScreenBuffer fonction)


Déplace un bloc de données dans une mémoire tampon d’écran. Les effets du déplacement peuvent être limités en spécifiant un rectangle de découpage, le contenu de la mémoire tampon d’écran de la console en dehors du rectangle de découpage n’est donc pas modifié.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI ScrollConsoleScreenBuffer(
  _In_           HANDLE     hConsoleOutput,
  _In_     const SMALL_RECT *lpScrollRectangle,
  _In_opt_ const SMALL_RECT *lpClipRectangle,
  _In_           COORD      dwDestinationOrigin,
  _In_     const CHAR_INFO  *lpFill
);
```

<a name="parameters"></a>Paramètres
----------

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le handle doit avoir le droit d’accès ** \_ en lecture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*lpScrollRectangle* \[ dans\]  
Pointeur vers une [**petite structure \_ Rect**](small-rect-str.md) dont les membres spécifient les coordonnées supérieure gauche et inférieure droite du rectangle de la mémoire tampon d’écran de la console à déplacer.

*lpClipRectangle* \[ dans, facultatif\]  
Pointeur vers une [**petite structure \_ Rect**](small-rect-str.md) dont les membres spécifient les coordonnées supérieure gauche et inférieure droite du rectangle de la mémoire tampon d’écran de la console qui est affectée par le défilement. Ce pointeur peut avoir la **valeur null**.

*dwDestinationOrigin* \[ dans\]  
Structure de [**repère**](coord-str.md) qui spécifie l’angle supérieur gauche du nouvel emplacement du contenu *lpScrollRectangle* , en caractères.

*lpFill* \[ dans\]  
Pointeur vers une structure [**d' \_ informations de type char**](char-info-str.md) qui spécifie les attributs de caractère et de couleur à utiliser pour remplir les cellules au sein de l’intersection de *lpScrollRectangle* et de *lpClipRectangle* qui ont été laissés vides suite au déplacement.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

**ScrollConsoleScreenBuffer** copie le contenu d’une zone rectangulaire d’une mémoire tampon d’écran, spécifiée par le paramètre *lpScrollRectangle* , dans une autre zone de la mémoire tampon d’écran de la console. Le rectangle cible a les mêmes dimensions que le rectangle *lpScrollRectangle* avec son coin supérieur gauche aux coordonnées spécifiées par le paramètre *dwDestinationOrigin* . Les éléments de *lpScrollRectangle* qui ne se chevauchent pas avec le rectangle cible sont renseignés avec les attributs de caractère et de couleur spécifiés par le paramètre *lpFill* .

Le rectangle de découpage s’applique aux modifications apportées à la fois dans le rectangle *lpScrollRectangle* et dans le rectangle cible. Par exemple, si le rectangle de découpage n’inclut pas une région qui aurait été remplie par le contenu de *lpFill*, le contenu d’origine de la région reste inchangé.

Si les régions de défilement ou cibles s’étendent au-delà des dimensions de la mémoire tampon d’écran de la console, elles sont découpées. Par exemple, si *lpScrollRectangle* est la région contenue par (0, 0) et (19, 19) et *dwDestinationOrigin* est (10, 15), le rectangle cible est la région contenue par (10, 15) et (29, 34). Toutefois, si la mémoire tampon de l’écran de la console est de 50 caractères de large à 30 caractères de haut, le rectangle cible est coupé à (10, 15) et (29, 29). Les modifications apportées à la mémoire tampon d’écran de la console sont également découpées selon *lpClipRectangle*, si le paramètre spécifie une [**petite structure \_ Rect**](small-rect-str.md) . Si le rectangle de découpage est spécifié sous la forme (0, 0) et (49, 19), seules les modifications qui se produisent dans cette région de la mémoire tampon de l’écran de la console sont effectuées.

Cette fonction utilise des caractères Unicode ou 8 bits à partir de la page de codes actuelle de la console. La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système. Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .

<a name="examples"></a>Exemples
--------

Pour obtenir un exemple, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).

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
<td><p><strong>ScrollConsoleScreenBufferW</strong> (Unicode) et <strong>ScrollConsoleScreenBufferA</strong> (ANSI)</p></td>
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


[**\_infos char**](char-info-str.md)

[Fonctions de la console](console-functions.md)

[**COORDONNÉES**](coord-str.md)

[Défilement de la mémoire tampon d’écran](scrolling-the-screen-buffer.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[**PETIT \_ Rect**](small-rect-str.md)

 

 




