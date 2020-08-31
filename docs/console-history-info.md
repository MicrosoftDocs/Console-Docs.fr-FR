---
title: Structure CONSOLE_HISTORY_INFO
description: Consultez les informations de référence sur la structure CONSOLE_HISTORY_INFO, qui contient des informations sur l’historique de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/CONSOLE_HISTORY_INFO
- wincon/CONSOLE_HISTORY_INFO
- CONSOLE_HISTORY_INFO
- consoleapi3/PCONSOLE_HISTORY_INFO
- wincon/PCONSOLE_HISTORY_INFO
- PCONSOLE_HISTORY_INFO
MS-HAID:
- base.console\_history\_info
- consoles.console\_history\_info
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: df7d2f12-5299-47ed-b1f6-2db903dba81b
topic_type:
- apiref
api_name:
- CONSOLE_HISTORY_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: ee0161f0c4aac5a280fd18260ebbb1f7ca57d54a
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059500"
---
# <a name="console_history_info-structure"></a>\_Structure des informations de l’historique de la console \_


Contient des informations sur l’historique de la console.

<a name="syntax"></a>Syntaxe
------

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

<a name="members"></a>Membres
-------

**cbSize**  
Taille de la structure en octets. Affectez à ce membre la valeur `sizeof(CONSOLE_HISTORY_INFO)` .

**HistoryBufferSize**  
Nombre de commandes conservées dans chaque mémoire tampon de l’historique.

**NumberOfHistoryBuffers**  
Nombre de mémoires tampons d’historique conservées pour ce processus de console.

**dwFlags**  
Ce paramètre peut être égal à zéro ou à la valeur suivante.

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
<td><span id="HISTORY_NO_DUP_FLAG"></span><span id="history_no_dup_flag"></span>
<strong>HISTORY_NO_DUP_FLAG</strong> 0x1</td>
<td><p>Les entrées en double ne sont pas stockées dans la mémoire tampon de l’historique.</p></td>
</tr>
</tbody>
</table>

 

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
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Voir aussi


[**GetConsoleHistoryInfo**](getconsolehistoryinfo.md)

[**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)

 

 




