---
title: AttachConsole fonction)
description: Consultez les informations de référence sur la fonction AttachConsole, qui attache le processus appelant à la console du processus spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- base.attachconsole
- consoles.attachconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c4048a2fb4c93d9f286ffc1ef7f38923836f37bf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059385"
---
# <a name="attachconsole-function"></a>AttachConsole fonction)


Joint le processus appelant à la console du processus spécifié.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

<a name="parameters"></a>Paramètres
----------

*dwProcessId* \[ dans\]  
Identificateur du processus dont la console doit être utilisée. Ce paramètre peut prendre l’une des valeurs suivantes.

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
<td><em>ELECTRIQUE</em></td>
<td><p>Utilisez la console du processus spécifié.</p></td>
</tr>
<tr class="even">
<td><span id="ATTACH_PARENT_PROCESS"></span><span id="attach_parent_process"></span>
<strong>ATTACH_PARENT_PROCESS</strong> (DWORD)-1</td>
<td><p>Utilisez la console du parent du processus en cours.</p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

Un processus peut être attaché à au plus une console. Si le processus appelant est déjà attaché à une console, le code d’erreur retourné est **erreur \_ accès \_ refusé** (5). Si le processus spécifié n’a pas de console, le code d’erreur retourné **est \_ erreur \_ handle non valide** (6). Si le processus spécifié n’existe pas, le code d’erreur retourné est un **paramètre d’erreur \_ non valide \_ ** (87).

Un processus peut utiliser la fonction [**FreeConsole**](freeconsole.md) pour se détacher de sa console. Si d’autres processus partagent la console, la console n’est pas détruite, mais le processus qui a appelé **FreeConsole** ne peut pas y faire référence. Une console est fermée lorsque le dernier processus qui lui est associé se termine ou appelle **FreeConsole**. Une fois qu’un processus a appelé **FreeConsole**, il peut appeler la fonction [**AllocConsole**](allocconsole.md) pour créer une nouvelle console ou **AttachConsole** à attacher à une autre console.

Pour compiler une application qui utilise cette fonction, définissez ** \_ Win32 \_ winnt** comme 0x0501 ou version ultérieure. Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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

[Consoles](consoles.md)

[**AllocConsole**](allocconsole.md)

[**FreeConsole**](freeconsole.md)

[**GetConsoleProcessList**](getconsoleprocesslist.md)

 

 




