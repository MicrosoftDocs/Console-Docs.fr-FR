---
title: ReadConsoleOutput fonction)
description: Lit les données d’attribut de caractère et de couleur à partir d’un bloc rectangulaire de cellules de caractères dans une mémoire tampon d’écran de la console et écrit des données dans la mémoire tampon de destination.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/ReadConsoleOutput
- wincon/ReadConsoleOutput
- ReadConsoleOutput
- consoleapi2/ReadConsoleOutputA
- wincon/ReadConsoleOutputA
- ReadConsoleOutputA
- consoleapi2/ReadConsoleOutputW
- wincon/ReadConsoleOutputW
- ReadConsoleOutputW
MS-HAID:
- '\_win32\_readconsoleoutput'
- base.readconsoleoutput
- consoles.readconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d1391684-6a8f-4b5e-9706-11970a957710
topic_type:
- apiref
api_name:
- ReadConsoleOutput
- ReadConsoleOutputA
- ReadConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 382ed9cd06586ab86097c6efd2f6b8ea92f03eaf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059473"
---
# <a name="readconsoleoutput-function"></a>ReadConsoleOutput fonction)


Lit les données d’attribut de caractère et de couleur à partir d’un bloc rectangulaire de cellules de caractères dans une mémoire tampon d’écran de la console, et la fonction écrit les données dans un bloc rectangulaire à un emplacement spécifié dans la mémoire tampon de destination.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI ReadConsoleOutput(
  _In_    HANDLE      hConsoleOutput,
  _Out_   PCHAR_INFO  lpBuffer,
  _In_    COORD       dwBufferSize,
  _In_    COORD       dwBufferCoord,
  _Inout_ PSMALL_RECT lpReadRegion
);
```

<a name="parameters"></a>Paramètres
----------

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le handle doit avoir le droit d’accès ** \_ en lecture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ à\]  
Pointeur vers une mémoire tampon de destination qui reçoit les données lues à partir de la mémoire tampon d’écran de la console. Ce pointeur est traité comme l’origine d’un tableau à deux dimensions de structures d' [** \_ informations de type char**](char-info-str.md) dont la taille est spécifiée par le paramètre *dwBufferSize* .

*dwBufferSize* \[ dans\]  
Taille du paramètre *lpBuffer* , dans les cellules de caractères. Le membre **X** de la structure [**Coord**](coord-str.md) est le nombre de colonnes ; le membre **Y** est le nombre de lignes.

*dwBufferCoord* \[ dans\]  
Coordonnées de la cellule supérieure gauche dans le paramètre *lpBuffer* qui reçoit les données lues à partir de la mémoire tampon d’écran de la console. Le membre **X** de la structure [**Coord**](coord-str.md) est la colonne et le membre **Y** est la ligne.

*lpReadRegion* \[ in, out\]  
Pointeur vers une [**petite structure \_ Rect**](small-rect-str.md) . En entrée, les membres de structure spécifient les coordonnées supérieure gauche et inférieure droite du rectangle de la mémoire tampon d’écran de la console à partir duquel la fonction doit être lue. Lors de la sortie, les membres de structure spécifient le rectangle réel qui a été utilisé.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

**ReadConsoleOutput** traite la mémoire tampon d’écran de la console et la mémoire tampon de destination en tant que tableaux à deux dimensions (colonnes et lignes de cellules de caractères). Le rectangle vers lequel pointe le paramètre *lpReadRegion* spécifie la taille et l’emplacement du bloc à lire à partir de la mémoire tampon d’écran de la console. Un rectangle de destination de la même taille se trouve avec sa cellule supérieure gauche aux coordonnées du paramètre *dwBufferCoord* dans le tableau *lpBuffer* . Les données lues à partir des cellules du rectangle source de la mémoire tampon d’écran de la console sont copiées dans les cellules correspondantes de la mémoire tampon de destination. Si la cellule correspondante se trouve en dehors des limites du rectangle de la mémoire tampon de destination (dont les dimensions sont spécifiées par le paramètre *dwBufferSize* ), les données ne sont pas copiées.

Les cellules de la mémoire tampon de destination correspondant à des coordonnées qui ne se trouvent pas dans les limites de la mémoire tampon de l’écran de la console restent inchangées. En d’autres termes, il s’agit des cellules pour lesquelles aucune donnée de mémoire tampon d’écran n’est disponible pour la lecture.

Avant que **ReadConsoleOutput** retourne, il définit les membres de la structure vers laquelle pointe le paramètre *lpReadRegion* vers le rectangle de mémoire tampon d’écran réel dont les cellules ont été copiées dans la mémoire tampon de destination. Ce rectangle reflète les cellules du rectangle source pour lesquelles il existait une cellule correspondante dans la mémoire tampon de destination, car **ReadConsoleOutput** découpe les dimensions du rectangle source pour les adapter aux limites de la mémoire tampon d’écran de la console.

Si le rectangle spécifié par *lpReadRegion* se trouve complètement en dehors des limites de la mémoire tampon d’écran de la console, ou si le rectangle correspondant est positionné complètement en dehors des limites de la mémoire tampon de destination, aucune donnée n’est copiée. Dans ce cas, la fonction retourne avec les membres de la structure vers laquelle pointe le jeu de paramètres *lpReadRegion* , de sorte que le membre de **droite** est inférieur à la **gauche**, ou le membre **inférieur** est inférieur au **haut**. Pour déterminer la taille de la mémoire tampon d’écran de la console, utilisez la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .

La fonction **ReadConsoleOutput** n’a aucun effet sur la position du curseur de la mémoire tampon de l’écran de la console. Le contenu de la mémoire tampon d’écran de la console n’est pas modifié par la fonction.

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
<td><p><strong>ReadConsoleOutputW</strong> (Unicode) et <strong>ReadConsoleOutputA</strong> (ANSI)</p></td>
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

[Fonctions de sortie de la console de bas niveau](low-level-console-output-functions.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**PETIT \_ Rect**](small-rect-str.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**\_infos char**](char-info-str.md)

[**COORDONNÉES**](coord-str.md)

 

 




