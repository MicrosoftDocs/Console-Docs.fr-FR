---
title: ResizePseudoConsole fonction)
description: Consultez les informations de référence sur la fonction ResizePseudoConsole, qui redimensionne les mémoires tampons internes pour un pseudoconsole à la taille donnée.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API console, conpty, pseudoconsole
f1_keywords:
- consoleapi/ResizePseudoConsole
- ResizePseudoConsole
topic_type:
- apiref
api_name:
- ResizePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a4f6ff773538eda4d4c84c4b0bac2e647f6b80d8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059444"
---
# <a name="resizepseudoconsole-function"></a>ResizePseudoConsole fonction)


Redimensionne les mémoires tampons internes pour un pseudoconsole à la taille donnée.

<a name="syntax"></a>Syntaxe
------

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

<a name="parameters"></a>Paramètres
----------

*hPC* \[ dans\]  
Handle d’un psuedoconsole actif tel qu’il est ouvert par [CreatePseudoConsole](createpseudoconsole.md).

*taille* \[ dans\]  
Dimensions de la fenêtre/mémoire tampon en nombre de caractères qui seront utilisés pour la mémoire tampon interne de ce pseudoconsole. 

<a name="return-value"></a>Valeur retournée
------------

Type : **HRESULT**

Si cette méthode est réussie, elle retourne **S_OK**. Sinon, elle retourne un code d’erreur **HRESULT** .

<a name="remarks"></a>Remarques
-------

Cette fonction peut redimensionner les mémoires tampons internes de la session pseudoconsole pour qu’elles correspondent à la taille de la fenêtre/de la mémoire tampon utilisée pour l’affichage sur l’extrémité terminal. Cela permet de s’assurer que les applications de l’interface de ligne de commande (CUI) attachées utilisant les fonctions de la [console](console-functions.md) pour communiquer auront les dimensions correctes retournées dans leurs appels.

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

[**ClosePseudoConsole**](closepseudoconsole.md)
