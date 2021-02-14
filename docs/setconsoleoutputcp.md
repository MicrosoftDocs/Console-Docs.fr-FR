---
title: SetConsoleOutputCP fonction)
description: Définit la page de codes de sortie utilisée par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/SetConsoleOutputCP
- wincon/SetConsoleOutputCP
- SetConsoleOutputCP
MS-HAID:
- '\_win32\_setconsoleoutputcp'
- base.setconsoleoutputcp
- consoles.setconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0b41e66b-ca19-4d69-9f39-92da158344ef
topic_type:
- apiref
api_name:
- SetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: abe04e2be5256097e19742bfbc8566c3ab613c4d
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357519"
---
# <a name="setconsoleoutputcp-function"></a>SetConsoleOutputCP fonction)

Définit la page de codes de sortie utilisée par la console associée au processus appelant. Une console utilise sa page de codes de sortie pour convertir les valeurs de caractères écrites par les différentes fonctions de sortie dans les images affichées dans la fenêtre de la console.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI SetConsoleOutputCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a>Paramètres

*wCodePageID* \[ dans\]  
Identificateur de la page de codes à définir. Pour plus d'informations, consultez la section Notes.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

Une page de codes mappe 256 codes de caractères à des caractères individuels. Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.

Si la police actuelle est une police Unicode à espacement fixe, **SetConsoleOutputCP** modifie le mappage des valeurs de caractère dans le jeu de glyphes de la police, plutôt que de charger une police distincte chaque fois qu’elle est appelée. Cela affecte la façon dont les caractères étendus (valeur ASCII supérieure à 127) sont affichés dans une fenêtre de console. Toutefois, si la police actuelle est une police raster, **SetConsoleOutputCP** n’affecte pas la manière dont les caractères étendus sont affichés.

Pour rechercher les pages de codes qui sont installées ou prises en charge par le système d’exploitation, utilisez la fonction [EnumSystemCodePages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) . Les identificateurs des pages de codes disponibles sur l’ordinateur local sont également stockés dans le Registre sous la clé suivante :

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

Toutefois, il est préférable d’utiliser [EnumSystemCodePages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) pour énumérer les pages de code, car le registre peut différer dans différentes versions de Windows.
Pour déterminer si une page de codes particulière est valide, utilisez la fonction [IsValidCodePage](/windows/win32/api/winnls/nf-winnls-isvalidcodepage) . Pour obtenir plus d’informations sur une page de codes, y compris son nom, utilisez la fonction [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) . Pour obtenir la liste des identificateurs de page de codes disponibles, consultez [identificateurs de page de codes](/windows/win32/intl/code-page-identifiers).

Pour déterminer la page de codes de sortie actuelle d’une console, utilisez la fonction [**GetConsoleOutputCP**](getconsoleoutputcp.md) . Pour définir et récupérer la page de codes d’entrée d’une console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) et [**GetConsoleCP**](getconsolecp.md) .

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 2000 Professionnel - \[Applications de bureau uniquement\] |
| Serveur minimal pris en charge | Windows 2000 Server - \[Applications de bureau uniquement\] |
| En-tête | ConsoleApi2. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Pages de code d’une console](console-code-pages.md)

[Fonctions de console](console-functions.md)

[**GetConsoleCP**](getconsolecp.md)

[**GetConsoleOutputCP**](getconsoleoutputcp.md)

[**SetConsoleCP**](setconsolecp.md)