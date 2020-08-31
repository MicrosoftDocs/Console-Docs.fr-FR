---
title: GetConsoleOutputCP fonction)
description: Récupère la page de codes de sortie utilisée par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi/GetConsoleOutputCP
- wincon/GetConsoleOutputCP
- GetConsoleOutputCP
MS-HAID:
- '\_win32\_getconsoleoutputcp'
- base.getconsoleoutputcp
- consoles.getconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c23706c7-ce17-4825-a494-20ca44534d45
topic_type:
- apiref
api_name:
- GetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: e80618ebd5c6b29f00e79594c55bfa15fab315ba
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059148"
---
# <a name="getconsoleoutputcp-function"></a>GetConsoleOutputCP fonction)


Récupère la page de codes de sortie utilisée par la console associée au processus appelant. Une console utilise sa page de codes de sortie pour convertir les valeurs de caractères écrites par les différentes fonctions de sortie dans les images affichées dans la fenêtre de la console.

<a name="syntax"></a>Syntaxe
------

```C
UINT WINAPI GetConsoleOutputCP(void);
```

<a name="parameters"></a>Paramètres
----------

Cette fonction n’a pas de paramètres.

<a name="return-value"></a>Valeur retournée
------------

La valeur de retour est un code qui identifie la page de codes. Pour obtenir la liste des identificateurs, consultez [identificateurs de page de codes](https://msdn.microsoft.com/library/windows/desktop/dd317756).

Si la valeur de retour est égale à zéro, la fonction a échoué. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

Une page de codes mappe 256 codes de caractères à des caractères individuels. Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues. Pour obtenir plus d’informations sur une page de codes, y compris son nom, consultez la fonction [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .

Pour définir la page de codes de sortie d’une console, utilisez la fonction [**SetConsoleOutputCP**](setconsoleoutputcp.md) . Pour définir et interroger la page de codes d’entrée d’une console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) et [**GetConsoleCP**](getconsolecp.md) .

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


[Pages de codes de la console](console-code-pages.md)

[Fonctions de la console](console-functions.md)

[**GetConsoleCP**](getconsolecp.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

 

 




