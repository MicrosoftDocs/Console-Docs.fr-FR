---
title: GetConsoleScreenBufferInfo fonction)
description: Consultez les informations de référence sur la fonction GetConsoleScreenBufferInfo, qui récupère des informations sur la mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfo
- wincon/GetConsoleScreenBufferInfo
- GetConsoleScreenBufferInfo
ms.assetid: eafe819e-a99a-4ce1-8898-8860444a31af
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 8ced380982705647b7944cee0f72c723c38776c3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059128"
---
# <a name="getconsolescreenbufferinfo-function"></a>GetConsoleScreenBufferInfo fonction)


Récupère des informations sur la mémoire tampon d’écran de console spécifiée.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

<a name="parameters"></a>Paramètres
----------

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le handle doit avoir le droit d’accès ** \_ en lecture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*lpConsoleScreenBufferInfo* \[ à\]  
Pointeur vers une structure [**d' \_ \_ \_ informations de mémoire tampon d’écran de console**](console-screen-buffer-info-str.md) qui reçoit les informations de mémoire tampon d’écran de la console.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

Le rectangle retourné dans le membre **srWindow** de la structure des [** \_ \_ \_ informations de mémoire tampon**](console-screen-buffer-info-str.md) de l’écran de la console peut être modifié, puis transmis à la fonction [**SetConsoleWindowInfo**](setconsolewindowinfo.md) pour faire défiler la mémoire tampon de l’écran de la console dans la fenêtre, pour modifier la taille de la fenêtre, ou les deux.

Toutes les coordonnées retournées dans la structure des [** \_ \_ \_ informations de mémoire tampon**](console-screen-buffer-info-str.md) de l’écran de la console sont exprimées en coordonnées de cellule de caractères, où l’origine (0,0) se trouve dans l’angle supérieur gauche de la mémoire tampon d’écran de la console.

<a name="examples"></a>Exemples
--------

Pour obtenir un exemple, consultez [défilement de la fenêtre d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-window.md).

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

[**\_ \_ informations sur la mémoire tampon d’écran de la console \_**](console-screen-buffer-info-str.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[Taille de la mémoire tampon de la fenêtre et de l’écran](window-and-screen-buffer-size.md)

 

 




