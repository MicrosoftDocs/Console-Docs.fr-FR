---
title: GetStdHandle fonction)
description: Récupère un handle vers l’appareil standard spécifié (entrée standard, sortie standard ou erreur standard).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- processenv/GetStdHandle
- winbase/GetStdHandle
- GetStdHandle
MS-HAID:
- '\_win32\_getstdhandle'
- base.getstdhandle
- consoles.getstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 23cd76e9-671a-48d0-9b82-2beda8917348
topic_type:
- apiref
api_name:
- GetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 613aacf4052e8e3b38c0a3e254ac4dd2b55ced5d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059081"
---
# <a name="getstdhandle-function"></a>GetStdHandle fonction)


Récupère un handle vers l’appareil standard spécifié (entrée standard, sortie standard ou erreur standard).

<a name="syntax"></a>Syntaxe
------

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

<a name="parameters"></a>Paramètres
----------

*nStdHandle* \[ dans\]  
Appareil standard. Ce paramètre peut prendre l’une des valeurs suivantes.

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
<td><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</td>
<td><p>Périphérique d’entrée standard. Au départ, il s’agit de la mémoire tampon d’entrée de la console, CONIN $.</p></td>
</tr>
<tr class="even">
<td><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</td>
<td><p>Périphérique de sortie standard. Initialement, il s’agit de la mémoire tampon d’écran active de la console, CONOUT $.</p></td>
</tr>
<tr class="odd">
<td><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</td>
<td><p>Périphérique d’erreur standard. Initialement, il s’agit de la mémoire tampon d’écran active de la console, CONOUT $.</p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Valeur retournée
------------

Si la fonction s’exécute correctement, la valeur de retour est un handle vers l’appareil spécifié, ou un handle Redirigé défini par un appel précédent à [**SetStdHandle**](setstdhandle.md). Le descripteur dispose de droits d’accès en ** \_ écriture** génériques ** \_ en lecture** et génériques, sauf si l’application a utilisé **SetStdHandle** pour définir un descripteur standard avec un accès plus faible.

Si la fonction échoue, la valeur de retour est une ** \_ \_ valeur de handle non valide**. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Si une application n’a pas de descripteurs standard associés, comme un service s’exécutant sur un bureau interactif, et n’a pas été redirigée, la valeur de retour est **null**.

<a name="remarks"></a>Remarques
-------

Les handles retournés par **GetStdHandle** peuvent être utilisés par les applications qui doivent lire ou écrire dans la console. Quand une console est créée, le descripteur d’entrée standard est un handle de la mémoire tampon d’entrée de la console, et la sortie standard et les descripteurs d’erreur standard sont des handles de la mémoire tampon d’écran active de la console. Ces handles peuvent être utilisés par les fonctions [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) , ou par n’importe quelle fonction de console qui accède à la mémoire tampon d’entrée de la console ou à une mémoire tampon d’écran (par exemple, les fonctions [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md)ou [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) ).

Les handles standard d’un processus peuvent être redirigés par un appel à [**SetStdHandle**](setstdhandle.md), auquel cas **GetStdHandle** retourne le handle Redirigé. Si les handles standard ont été redirigés, vous pouvez spécifier la valeur CONIN $ dans un appel à la fonction [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) pour obtenir un handle vers la mémoire tampon d’entrée d’une console. De même, vous pouvez spécifier la valeur CONOUT $ pour obtenir un handle vers la mémoire tampon d’écran active d’une console.

### <a name="span-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanattachdetach-behavior"></a><span id="Attach_detach_behavior"></span><span id="attach_detach_behavior"></span><span id="ATTACH_DETACH_BEHAVIOR"></span>Comportement d’attachement/détachement

Lors de l’attachement à une nouvelle console, les handles standard sont toujours remplacés par des handles de console, sauf si **STARTF \_ USESTDHANDLES** a été spécifié lors de la création du processus.

Si la valeur existante du handle standard est **null**, ou si la valeur existante du handle standard ressemble à un pseudohandle de console, le handle est remplacé par un handle de console.

Lorsqu’un parent utilise à la fois **Create \_ New \_ console** et **STARTF \_ USESTDHANDLES** pour créer un processus de console, les handles standard ne sont pas remplacés, sauf si la valeur existante du handle standard est null ou un pseudohandle de console.

<a name="examples"></a>Exemples
--------

Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).

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
<td>ProcessEnv. h (via Winbase. h, incluez Windows. h)</td>
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

[Handles de la console](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetStdHandle**](setstdhandle.md)

[**WriteConsole**](writeconsole.md)

[**Appel**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




