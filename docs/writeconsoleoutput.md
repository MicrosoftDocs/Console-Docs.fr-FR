---
title: WriteConsoleOutput fonction)
description: Écrit des données d’attribut de caractère et de couleur dans un bloc rectangulaire spécifié de cellules de caractères dans une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/WriteConsoleOutput
- wincon/WriteConsoleOutput
- WriteConsoleOutput
- consoleapi2/WriteConsoleOutputA
- wincon/WriteConsoleOutputA
- WriteConsoleOutputA
- consoleapi2/WriteConsoleOutputW
- wincon/WriteConsoleOutputW
- WriteConsoleOutputW
MS-HAID:
- '\_win32\_writeconsoleoutput'
- base.writeconsoleoutput
- consoles.writeconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a98b8118-97ce-4dd4-a337-122d4a76f232
topic_type:
- apiref
api_name:
- WriteConsoleOutput
- WriteConsoleOutputA
- WriteConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e2f84f5c072a8404b129e27bec3464363b9dd3d0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059052"
---
# <a name="writeconsoleoutput-function"></a>WriteConsoleOutput fonction)


Écrit des données d’attribut de caractère et de couleur dans un bloc rectangulaire spécifié de cellules de caractères dans une mémoire tampon d’écran de la console. Les données à écrire proviennent d’un bloc rectangulaire de taille correspondante à un emplacement spécifié dans la mémoire tampon source.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI WriteConsoleOutput(
  _In_          HANDLE      hConsoleOutput,
  _In_    const CHAR_INFO   *lpBuffer,
  _In_          COORD       dwBufferSize,
  _In_          COORD       dwBufferCoord,
  _Inout_       PSMALL_RECT lpWriteRegion
);
```

<a name="parameters"></a>Paramètres
----------

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le descripteur doit avoir le droit d’accès en ** \_ écriture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ dans\]  
Données à écrire dans la mémoire tampon d’écran de la console. Ce pointeur est traité comme l’origine d’un tableau à deux dimensions de structures d' [** \_ informations de type char**](char-info-str.md) dont la taille est spécifiée par le paramètre *dwBufferSize* .

*dwBufferSize* \[ dans\]  
Taille de la mémoire tampon vers laquelle pointe le paramètre *lpBuffer* , dans les cellules de caractères. Le membre **X** de la structure [**Coord**](coord-str.md) est le nombre de colonnes ; le membre **Y** est le nombre de lignes.

*dwBufferCoord* \[ dans\]  
Coordonnées de la cellule supérieure gauche dans la mémoire tampon vers laquelle pointe le paramètre *lpBuffer* . Le membre **X** de la structure [**Coord**](coord-str.md) est la colonne et le membre **Y** est la ligne.

*lpWriteRegion* \[ in, out\]  
Pointeur vers une [**petite structure \_ Rect**](small-rect-str.md) . En entrée, les membres de structure spécifient les coordonnées supérieure gauche et inférieure droite du rectangle de mémoire tampon de l’écran de la console dans lequel écrire. Lors de la sortie, les membres de structure spécifient le rectangle réel qui a été utilisé.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

**WriteConsoleOutput** traite la mémoire tampon source et la mémoire tampon d’écran de destination en tant que tableaux à deux dimensions (colonnes et lignes de cellules de caractères). Le rectangle vers lequel pointe le paramètre *lpWriteRegion* spécifie la taille et l’emplacement du bloc dans lequel écrire dans la mémoire tampon de l’écran de la console. Un rectangle de même taille se trouve avec sa cellule supérieure gauche aux coordonnées du paramètre *dwBufferCoord* dans le tableau *lpBuffer* . Les données des cellules situées à l’intersection de ce rectangle et du rectangle de la mémoire tampon source (dont les dimensions sont spécifiées par le paramètre *dwBufferSize* ) sont écrites dans le rectangle de destination.

Les cellules du rectangle de destination dont l’emplacement source correspondant se trouve en dehors des limites du rectangle de la mémoire tampon source ne sont pas affectées par l’opération d’écriture. En d’autres termes, il s’agit des cellules pour lesquelles aucune donnée n’est disponible pour être écrite.

Avant que **WriteConsoleOutput** retourne, il définit les membres de *lpWriteRegion* sur le rectangle de mémoire tampon d’écran réel affecté par l’opération d’écriture. Ce rectangle reflète les cellules du rectangle de destination pour lesquelles il existait une cellule correspondante dans la mémoire tampon source, car **WriteConsoleOutput** découpe les dimensions du rectangle de destination aux limites de la mémoire tampon d’écran de la console.

Si le rectangle spécifié par *lpWriteRegion* se trouve complètement en dehors des limites de la mémoire tampon d’écran de la console, ou si le rectangle correspondant est positionné complètement en dehors des limites de la mémoire tampon source, aucune donnée n’est écrite. Dans ce cas, la fonction retourne avec les membres de la structure vers laquelle pointe le jeu de paramètres *lpWriteRegion* , de sorte que le membre de **droite** est inférieur à la **gauche**, ou le membre **inférieur** est inférieur au **haut**. Pour déterminer la taille de la mémoire tampon d’écran de la console, utilisez la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .

**WriteConsoleOutput** n’a aucun effet sur la position du curseur.

Cette fonction utilise des caractères Unicode ou 8 bits à partir de la page de codes actuelle de la console. La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système. Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .

<a name="examples"></a>Exemples
--------

Pour obtenir un exemple, consultez [lecture et écriture de blocs de caractères et d’attributs](reading-and-writing-blocks-of-characters-and-attributes.md).

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
<td><p><strong>WriteConsoleOutputW</strong> (Unicode) et <strong>WriteConsoleOutputA</strong> (ANSI)</p></td>
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

[**\_infos char**](char-info-str.md)

[**COORDONNÉES**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[Fonctions de sortie de la console de bas niveau](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**PETIT \_ Rect**](small-rect-str.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)

 

 




