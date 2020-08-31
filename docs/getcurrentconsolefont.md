---
title: GetCurrentConsoleFont fonction)
description: Récupère des informations sur la police de console actuelle pour une mémoire tampon d’écran de console spécifiée.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetCurrentConsoleFont
- wincon/GetCurrentConsoleFont
- GetCurrentConsoleFont
MS-HAID:
- '\_win32\_getcurrentconsolefont'
- base.getcurrentconsolefont
- consoles.getcurrentconsolefont
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 347508ea-5c15-4568-b99f-1e7f5cdac8c1
topic_type:
- apiref
api_name:
- GetCurrentConsoleFont
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 4116dcf034c619544ed1689e3161f4eca4250a81
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059109"
---
# <a name="getcurrentconsolefont-function"></a>GetCurrentConsoleFont fonction)


Récupère des informations sur la police de la console actuelle.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI GetCurrentConsoleFont(
  _In_  HANDLE             hConsoleOutput,
  _In_  BOOL               bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFO lpConsoleCurrentFont
);
```

<a name="parameters"></a>Paramètres
----------

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le handle doit avoir le droit d’accès ** \_ en lecture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*bMaximumWindow* \[ dans\]  
Si ce paramètre a la **valeur true**, les informations sur la police sont récupérées pour la taille maximale de la fenêtre. Si ce paramètre a la **valeur false**, les informations sur la police sont récupérées pour la taille de fenêtre actuelle.

*lpConsoleCurrentFont* \[ à\]  
Pointeur vers une structure [**d' \_ \_ informations de police de console**](console-font-info-str.md) qui reçoit les informations de police demandées.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

Pour compiler une application qui utilise cette fonction, définissez ** \_ Win32 \_ winnt** comme 0x0500 ou version ultérieure. Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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


[Fonctions de la console](console-functions.md)

[Mémoires tampons d’écran de la console](console-screen-buffers.md)

[**\_informations sur la police de la console \_**](console-font-info-str.md)

[**GetConsoleFontSize**](getconsolefontsize.md)

 

 




