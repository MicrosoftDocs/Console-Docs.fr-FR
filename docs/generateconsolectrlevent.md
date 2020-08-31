---
title: GenerateConsoleCtrlEvent fonction)
description: Envoie un signal spécifié à un groupe de processus de console qui partage la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/GenerateConsoleCtrlEvent
- wincon/GenerateConsoleCtrlEvent
- GenerateConsoleCtrlEvent
MS-HAID:
- '\_win32\_generateconsolectrlevent'
- base.generateconsolectrlevent
- consoles.generateconsolectrlevent
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ed392d97-6fd0-4256-a783-bc7d27d01a10
topic_type:
- apiref
api_name:
- GenerateConsoleCtrlEvent
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 31c0330a002362542a799ab7e038d3f65497ded3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059200"
---
# <a name="generateconsolectrlevent-function"></a>GenerateConsoleCtrlEvent fonction)


Envoie un signal spécifié à un groupe de processus de console qui partage la console associée au processus appelant.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI GenerateConsoleCtrlEvent(
  _In_ DWORD dwCtrlEvent,
  _In_ DWORD dwProcessGroupId
);
```

<a name="parameters"></a>Paramètres
----------

*dwCtrlEvent* \[ dans\]  
Type de signal à générer. Ce paramètre peut prendre l’une des valeurs suivantes.

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
<td><span id="CTRL_C_EVENT"></span><span id="ctrl_c_event"></span>
<strong>CTRL_C_EVENT</strong> 0</td>
<td><p>Génère un signal CTRL + C. Ce signal ne peut pas être généré pour les groupes de processus. Si <em>dwProcessGroupId</em> est différent de zéro, cette fonction est réussie, mais le signal Ctrl + C n’est pas reçu par les processus au sein du groupe de processus spécifié.</p></td>
</tr>
<tr class="even">
<td><span id="CTRL_BREAK_EVENT"></span><span id="ctrl_break_event"></span>
<strong>CTRL_BREAK_EVENT</strong> 1</td>
<td><p>Génère un signal CTRL + ATTN.</p></td>
</tr>
</tbody>
</table>

 

*dwProcessGroupId* \[ dans\]  
Identificateur du groupe de processus devant recevoir le signal. Un groupe de processus est créé lorsque l’indicateur de création d’un ** \_ nouveau \_ \_ groupe de processus** est spécifié dans un appel à la fonction [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) . L’identificateur de processus du nouveau processus est également l’identificateur de groupe de processus d’un nouveau groupe de processus. Le groupe de processus comprend tous les processus qui sont des descendants du processus racine. Seuls les processus du groupe qui partagent la même console que le processus appelant reçoivent le signal. En d’autres termes, si un processus du groupe crée une nouvelle console, ce processus ne reçoit pas le signal, ni ses descendants.

Si ce paramètre est égal à zéro, le signal est généré dans tous les processus qui partagent la console du processus appelant.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

**GenerateConsoleCtrlEvent** entraîne l’appel des fonctions du gestionnaire de contrôle des processus dans le groupe cible. Tous les processus de console ont une fonction de gestionnaire par défaut qui appelle la fonction [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) . Un processus de console peut utiliser la fonction [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) pour installer ou supprimer d’autres fonctions de gestionnaire.

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) peut également activer un attribut pouvant être hérité qui amène le processus appelant à ignorer les signaux Ctrl + C. Si **GenerateConsoleCtrlEvent** envoie un signal Ctrl + C à un processus pour lequel cet attribut est activé, les fonctions de gestionnaire pour ce processus ne sont pas appelées. Les signaux CTRL + ATTN entraînent toujours l’appel des fonctions du gestionnaire.

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


[Gestionnaires de contrôle de console](console-control-handlers.md)

[Fonctions de la console](console-functions.md)

[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md)

 

 




