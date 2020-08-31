---
title: GetConsoleHistoryInfo fonction)
description: Consultez les informations de référence sur la fonction GetConsoleHistoryInfo, qui récupère les paramètres d’historique de la console du processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetConsoleHistoryInfo
- wincon/GetConsoleHistoryInfo
- GetConsoleHistoryInfo
MS-HAID:
- base.getconsolehistoryinfo
- consoles.getconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 145008b3-8a4a-4e6a-9144-ee787ce90ef4
topic_type:
- apiref
api_name:
- GetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 176cf5517f18f022f00824de02872adcb916f231
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059141"
---
# <a name="getconsolehistoryinfo-function"></a>GetConsoleHistoryInfo fonction)


Récupère les paramètres d’historique pour la console du processus appelant.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

<a name="parameters"></a>Paramètres
----------

*lpConsoleHistoryInfo* \[ à\]  
Pointeur vers une structure [**d' \_ \_ informations d’historique**](console-history-info.md) de la console qui reçoit les paramètres d’historique de la console du processus appelant.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

Si le processus appelant n’est pas un processus de console, la fonction échoue et définit la dernière erreur sur **erreur \_ accès \_ refusé**.

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
<td><p>Windows Vista [applications de bureau uniquement]</p></td>
</tr>
<tr class="even">
<td><p>Serveur minimal pris en charge</p></td>
<td><p>Windows Server 2008 [applications de bureau uniquement]</p></td>
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

[**\_informations sur l’historique de la console \_**](console-history-info.md)

[**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)

 

 




