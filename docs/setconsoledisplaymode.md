---
title: SetConsoleDisplayMode fonction)
description: Consultez les informations de référence sur la fonction SetConsoleDisplayMode, qui définit le mode d’affichage de la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- base.setconsoledisplaymode
- consoles.setconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744
topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0d4564b9a7562fb495c9834df98708d5faff5334
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059321"
---
# <a name="setconsoledisplaymode-function"></a>SetConsoleDisplayMode fonction)


Définit le mode d’affichage de la mémoire tampon d’écran de console spécifiée.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

<a name="parameters"></a>Paramètres
----------

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console.

*dwFlags* \[ dans\]  
Mode d’affichage de la console. Ce paramètre peut être une ou plusieurs des valeurs suivantes.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Value</th>
<th>Signification</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="CONSOLE_FULLSCREEN_MODE"></span><span id="console_fullscreen_mode"></span>
<strong>CONSOLE_FULLSCREEN_MODE</strong> 1</td>
<td><p>Le texte est affiché en mode plein écran.</p></td>
</tr>
<tr class="even">
<td><span id="CONSOLE_WINDOWED_MODE"></span><span id="console_windowed_mode"></span>
<strong>CONSOLE_WINDOWED_MODE</strong> 2</td>
<td><p>Le texte est affiché dans une fenêtre de console.</p></td>
</tr>
</tbody>
</table>

 

*lpNewScreenBufferDimensions* \[ out, facultatif\]  
Pointeur vers une structure de [**repère**](coord-str.md) qui reçoit les nouvelles dimensions de la mémoire tampon d’écran, en caractères.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

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
<td><p>Windows XP [applications de bureau uniquement]</p></td>
</tr>
<tr class="even">
<td><p>Serveur minimal pris en charge</p></td>
<td><p>Windows Server 2003 [applications de bureau uniquement]</p></td>
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

[Modes de la console](console-modes.md)

[**GetConsoleDisplayMode**](getconsoledisplaymode.md)

 

 




