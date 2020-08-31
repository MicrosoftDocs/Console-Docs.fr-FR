---
title: ClosePseudoConsole fonction)
description: Consultez les informations de référence sur la fonction ClosePseudoConsole, qui ferme un pseudoconsole à partir du handle donné.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API console, conpty, pseudoconsole
topic_type:
- apiref
api_name:
- ClosePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 0674fa9c02c54c9476e2844da69895905865d6f4
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059360"
---
# <a name="closepseudoconsole-function"></a>ClosePseudoConsole fonction)


Ferme un pseudoconsole à partir du handle donné.

<a name="syntax"></a>Syntaxe
------

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC 
);
```

<a name="parameters"></a>Paramètres
----------

*hPC* \[ dans\]  
Handle d’un psuedoconsole actif tel qu’il est ouvert par [CreatePseudoConsole](createpseudoconsole.md).

<a name="return-value"></a>Valeur retournée
------------

*Aucune*

<a name="remarks"></a>Remarques
-------

Lors de la fermeture d’un pseudoconsole, les applications clientes attachées à la session sont également arrêtées.

Un frame peint final peut arriver `hOutput` à partir du pseudoconsole quand cette API est appelée. Il est prévu que l’appelant draine ces informations à partir de la mémoire tampon du canal de communication, puis le présente ou l’ignore. L’échec de la vidange de la mémoire tampon peut provoquer l’attente indéfinie de l’appel de fermeture jusqu’à ce qu’il soit vidé ou que les canaux de communication soient rompus d’une autre façon.

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
<td><p>Windows 10 1809 [applications de bureau uniquement]</p></td>
</tr>
<tr class="even">
<td><p>Serveur minimal pris en charge</p></td>
<td><p>Windows Server 2019 [applications de bureau uniquement]</p></td>
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

[Pseudoconsoles](pseudoconsoles.md)

[**CreatePseudoConsole**](createpseudoconsole.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)
