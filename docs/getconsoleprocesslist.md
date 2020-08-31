---
title: GetConsoleProcessList fonction)
description: Consultez les informations de référence sur la fonction GetConsoleProcessList, qui récupère une liste des processus attachés à la console actuelle.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetConsoleProcessList
- wincon/GetConsoleProcessList
- GetConsoleProcessList
MS-HAID:
- '\_win32\_getconsoleprocesslist'
- base.getconsoleprocesslist
- consoles.getconsoleprocesslist
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3d21103b-662d-4393-ae3f-773cd9e4a930
topic_type:
- apiref
api_name:
- GetConsoleProcessList
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 5b032754172886fd83a8152caeb5e2228b917930
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059157"
---
# <a name="getconsoleprocesslist-function"></a>GetConsoleProcessList fonction)


Récupère une liste des processus attachés à la console actuelle.

<a name="syntax"></a>Syntaxe
------

```C
DWORD WINAPI GetConsoleProcessList(
  _Out_ LPDWORD lpdwProcessList,
  _In_  DWORD   dwProcessCount
);
```

<a name="parameters"></a>Paramètres
----------

*lpdwProcessList* \[ à\]  
Pointeur vers une mémoire tampon qui reçoit un tableau d’identificateurs de processus en cas de réussite. Il doit s’agir d’une mémoire tampon valide qui ne peut pas être `NULL` . La mémoire tampon doit avoir un espace pour recevoir au moins 1 ID de processus retourné.

*dwProcessCount* \[ dans\]  
Nombre maximal d’identificateurs de processus qui peuvent être stockés dans la mémoire tampon *lpdwProcessList* . La valeur doit être supérieure à 0.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est inférieure ou égale à *dwProcessCount* et représente le nombre d’identificateurs de processus stockés dans la mémoire tampon *lpdwProcessList* .

Si la mémoire tampon est trop petite pour contenir tous les identificateurs de processus valides, la valeur de retour est le nombre requis d’éléments de tableau. La fonction n’a stocké aucun identificateur dans la mémoire tampon. Dans ce cas, utilisez la valeur de retour pour allouer une mémoire tampon suffisamment grande pour stocker la liste entière et appeler à nouveau la fonction.

Si la valeur de retour est égale à zéro, la fonction a échoué, car chaque console a au moins un processus associé. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Si une `NULL` liste de processus a été fournie ou si le nombre de processus est égal à 0, l’appel retourne 0 et `GetLastError` retourne `ERROR_INVALID_PARAMETER` . Indiquez une mémoire tampon d’au moins un élément pour appeler cette fonction. Allouez une mémoire tampon plus grande et rappelez si le code de retour est plus grand que la longueur de la mémoire tampon fournie.

<a name="remarks"></a>Remarques
-------

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


[**AttachConsole**](attachconsole.md)

[Fonctions de la console](console-functions.md)

 

 




