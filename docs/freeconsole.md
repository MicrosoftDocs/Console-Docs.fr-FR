---
title: FreeConsole fonction)
description: Consultez les informations de référence sur la fonction FreeConsole, qui détache le processus appelant à partir de sa console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi/FreeConsole
- wincon/FreeConsole
- FreeConsole
MS-HAID:
- '\_win32\_freeconsole'
- base.freeconsole
- consoles.freeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6c525325-696e-4d8b-8337-cbf9e31c900c
topic_type:
- apiref
api_name:
- FreeConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 3c8ba7b236b379bb57729538e065afebb68cc0cf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059204"
---
# <a name="freeconsole-function"></a>FreeConsole fonction)


Détache le processus appelant de sa console.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI FreeConsole(void);
```

<a name="parameters"></a>Paramètres
----------

Cette fonction n’a pas de paramètres.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

Un processus peut être attaché à au plus une console. Si le processus appelant n’est pas déjà attaché à une console, le code d’erreur retourné est **erreur : \_ \_ paramètre non valide** (87).

Un processus peut utiliser la fonction **FreeConsole** pour se détacher de sa console. Si d’autres processus partagent la console, la console n’est pas détruite, mais le processus qui a appelé **FreeConsole** ne peut pas y faire référence. Une console est fermée lorsque le dernier processus qui lui est associé se termine ou appelle **FreeConsole**. Une fois qu’un processus a appelé **FreeConsole**, il peut appeler la fonction [**AllocConsole**](allocconsole.md) pour créer une nouvelle console ou [**AttachConsole**](attachconsole.md) à attacher à une autre console.

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


[**AllocConsole**](allocconsole.md)

[**AttachConsole**](attachconsole.md)

[Fonctions de la console](console-functions.md)

[Consoles](consoles.md)

 

 




