---
title: SetConsoleCP fonction)
description: Définit la page de codes d’entrée utilisée par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/SetConsoleCP
- wincon/SetConsoleCP
- SetConsoleCP
MS-HAID:
- '\_win32\_setconsolecp'
- base.setconsolecp
- consoles.setconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a1a9ba5-c792-491d-ae51-979f462dcb53
topic_type:
- apiref
api_name:
- SetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: cf7048f9042b6c516c6d8e7a6e0544fdc2ac7533
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059417"
---
# <a name="setconsolecp-function"></a>SetConsoleCP fonction)


Définit la page de codes d’entrée utilisée par la console associée au processus appelant. Une console utilise sa page de codes d’entrée pour convertir l’entrée au clavier en valeur de caractère correspondante.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI SetConsoleCP(
  _In_ UINT wCodePageID
);
```

<a name="parameters"></a>Paramètres
----------

*wCodePageID* \[ dans\]  
Identificateur de la page de codes à définir. Pour plus d'informations, consultez la section Notes.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

Une page de codes mappe 256 codes de caractères à des caractères individuels. Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.

Pour rechercher les pages de codes qui sont installées ou prises en charge par le système d’exploitation, utilisez la fonction [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) . Les identificateurs des pages de codes disponibles sur l’ordinateur local sont également stockés dans le Registre sous la clé suivante :

**HKEY \_ local \_ machine \\ System \\ CurrentControlSet \\ contrôler \\ la \\ page de codes nls**

Toutefois, il est préférable d’utiliser [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) pour énumérer les pages de code, car le registre peut différer dans différentes versions de Windows.

Pour déterminer si une page de codes particulière est valide, utilisez la fonction [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) . Pour obtenir plus d’informations sur une page de codes, y compris son nom, utilisez la fonction [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) . Pour obtenir la liste des identificateurs de page de codes disponibles, consultez [identificateurs de page de codes](https://msdn.microsoft.com/library/windows/desktop/dd317756).

Pour déterminer la page de codes d’entrée actuelle d’une console, utilisez la fonction [**GetConsoleCP**](getconsolecp.md) . Pour définir et récupérer la page de codes de sortie d’une console, utilisez les fonctions [**SetConsoleOutputCP**](setconsoleoutputcp.md) et [**GetConsoleOutputCP**](getconsoleoutputcp.md) .

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


[Pages de codes de la console](console-code-pages.md)

[Fonctions de la console](console-functions.md)

[**GetConsoleCP**](getconsolecp.md)

[**GetConsoleOutputCP**](getconsoleoutputcp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

 

 




