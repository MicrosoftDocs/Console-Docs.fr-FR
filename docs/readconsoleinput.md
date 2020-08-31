---
title: ReadConsoleInput fonction)
description: Lit les données à partir d’une mémoire tampon d’entrée de la console et les supprime de la mémoire tampon.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi/ReadConsoleInput
- wincon/ReadConsoleInput
- ReadConsoleInput
- consoleapi/ReadConsoleInputA
- wincon/ReadConsoleInputA
- ReadConsoleInputA
- consoleapi/ReadConsoleInputW
- wincon/ReadConsoleInputW
- ReadConsoleInputW
MS-HAID:
- '\_win32\_readconsoleinput'
- base.readconsoleinput
- consoles.readconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5a9f7b18-cdea-4041-a377-5532d30e0105
topic_type:
- apiref
api_name:
- ReadConsoleInput
- ReadConsoleInputA
- ReadConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 38a5ee0d1572d6e40ab103cfc402d616a99d2ca5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059469"
---
# <a name="readconsoleinput-function"></a>ReadConsoleInput fonction)


Lit les données à partir d’une mémoire tampon d’entrée de la console et les supprime de la mémoire tampon.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI ReadConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

<a name="parameters"></a>Paramètres
----------

*hConsoleInput* \[ dans\]  
Handle vers la mémoire tampon d’entrée de la console. Le handle doit avoir le droit d’accès ** \_ en lecture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ à\]  
Pointeur vers un tableau de structures [**d' \_ enregistrements d’entrée**](input-record-str.md) qui reçoit les données de la mémoire tampon d’entrée.

*nLength* \[ dans\]  
Taille du tableau vers lequel pointe le paramètre *lpBuffer* , dans les éléments de tableau.

*lpNumberOfEventsRead* \[ à\]  
Pointeur vers une variable qui reçoit le nombre d’enregistrements d’entrée lus.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

Si le nombre d’enregistrements demandés dans le paramètre *nLength* dépasse le nombre d’enregistrements disponibles dans la mémoire tampon, le nombre disponible est Read. La fonction ne retourne pas de données tant qu’au moins un enregistrement d’entrée n’a pas été lu.

Un processus peut spécifier un handle de mémoire tampon d’entrée de la console dans l’une des [fonctions Wait](https://msdn.microsoft.com/library/windows/desktop/ms687069) pour déterminer le moment où une entrée de console n’est pas lue. Lorsque la mémoire tampon d’entrée n’est pas vide, l’état d’un handle de mémoire tampon d’entrée de la console est signalé.

Pour déterminer le nombre d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée d’une console, utilisez la fonction [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) . Pour lire les enregistrements d’entrée d’une mémoire tampon d’entrée de la console sans affecter le nombre d’enregistrements non lus, utilisez la fonction [**PeekConsoleInput**](peekconsoleinput.md) . Pour ignorer tous les enregistrements non lus dans le tampon d’entrée d’une console, utilisez la fonction [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .

Cette fonction utilise des caractères Unicode ou 8 bits à partir de la page de codes actuelle de la console. La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système. Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .

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
<td><p>Noms Unicode et ANSI</p></td>
<td><p><strong>ReadConsoleInputW</strong> (Unicode) et <strong>ReadConsoleInputA</strong> (ANSI)</p></td>
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

[**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

[**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)

[**enregistrement d’entrée \_**](input-record-str.md)

[Fonctions d’entrée de la console de bas niveau](low-level-console-input-functions.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleInput**](writeconsoleinput.md)

 

 




