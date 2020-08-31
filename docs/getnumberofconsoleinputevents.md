---
title: GetNumberOfConsoleInputEvents fonction)
description: Récupère le nombre d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi/GetNumberOfConsoleInputEvents
- wincon/GetNumberOfConsoleInputEvents
- GetNumberOfConsoleInputEvents
MS-HAID:
- '\_win32\_getnumberofconsoleinputevents'
- base.getnumberofconsoleinputevents
- consoles.getnumberofconsoleinputevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1083b4f1-8fa6-4054-a516-3b447c3b0130
topic_type:
- apiref
api_name:
- GetNumberOfConsoleInputEvents
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: c5e3a59308239898f78796170d08f8b21ca1b667
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059117"
---
# <a name="getnumberofconsoleinputevents-function"></a>GetNumberOfConsoleInputEvents fonction)


Récupère le nombre d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée de la console.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

<a name="parameters"></a>Paramètres
----------

*hConsoleInput* \[ dans\]  
Handle vers la mémoire tampon d’entrée de la console. Le handle doit avoir le droit d’accès ** \_ en lecture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*lpcNumberOfEvents* \[ à\]  
Pointeur vers une variable qui reçoit le nombre d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée de la console.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

La fonction **GetNumberOfConsoleInputEvents** signale le nombre total d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée, y compris les enregistrements d’entrée de clavier, de souris et de redimensionnement de fenêtre. Les processus utilisant la fonction [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ou [**ReadConsole**](readconsole.md) peuvent uniquement lire les entrées au clavier. Les processus qui utilisent la fonction [**ReadConsoleInput**](readconsoleinput.md) peuvent lire tous les types d’enregistrements d’entrée.

Un processus peut spécifier un handle de mémoire tampon d’entrée de la console dans l’une des [fonctions Wait](https://msdn.microsoft.com/library/windows/desktop/ms687069) pour déterminer le moment où une entrée de console n’est pas lue. Lorsque la mémoire tampon d’entrée n’est pas vide, l’état d’un handle de mémoire tampon d’entrée de la console est signalé.

Pour lire les enregistrements d’entrée d’une mémoire tampon d’entrée de la console sans affecter le nombre d’enregistrements non lus, utilisez la fonction [**PeekConsoleInput**](peekconsoleinput.md) . Pour ignorer tous les enregistrements non lus dans le tampon d’entrée d’une console, utilisez la fonction [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .

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
<td>ConsoleApi. h (via wincon. h, incluez Windows. h)</td>
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

[**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

[Fonctions d’entrée de la console de bas niveau](low-level-console-input-functions.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsole**](readconsole.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

 

 




