---
title: WriteConsoleOutputCharacter fonction)
description: Copie un nombre de caractères dans les cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/WriteConsoleOutputCharacter
- wincon/WriteConsoleOutputCharacter
- WriteConsoleOutputCharacter
- consoleapi2/WriteConsoleOutputCharacterA
- wincon/WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterA
- consoleapi2/WriteConsoleOutputCharacterW
- wincon/WriteConsoleOutputCharacterW
- WriteConsoleOutputCharacterW
MS-HAID:
- '\_win32\_writeconsoleoutputcharacter'
- base.writeconsoleoutputcharacter
- consoles.writeconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 7cc935ea-6b19-4494-b746-259aa7aaa9cc
topic_type:
- apiref
api_name:
- WriteConsoleOutputCharacter
- WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 462ebfaed09a5c18fa9a075227a5568a789685bd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037207"
---
# <a name="writeconsoleoutputcharacter-function"></a>WriteConsoleOutputCharacter fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Copie un nombre de caractères dans les cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI WriteConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  LPCTSTR lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a>Paramètres

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le descripteur doit avoir le droit d’accès en **\_ écriture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*lpCharacter* \[ dans\]  
Caractères à écrire dans la mémoire tampon d’écran de la console.

*nLength* \[ dans\]  
Nombre de caractères à écrire.

*dwWriteCoord* \[ dans\]  
Structure de [**repère**](coord-str.md) qui spécifie les coordonnées de caractères de la première cellule dans la mémoire tampon d’écran de la console dans laquelle les caractères seront écrits.

*lpNumberOfCharsWritten* \[ à\]  
Pointeur vers une variable qui reçoit le nombre de caractères réellement écrits.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Si le nombre de caractères à écrire dans s’étend au-delà de la fin de la ligne spécifiée dans la mémoire tampon d’écran de la console, les caractères sont écrits sur la ligne suivante. Si le nombre de caractères à écrire dans s’étend au-delà de la fin de la mémoire tampon d’écran de la console, les caractères sont écrits jusqu’à la fin de la mémoire tampon d’écran de la console.

Les valeurs d’attribut aux positions écrites dans ne sont pas modifiées.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Cette API possède un **[terminal virtuel](console-virtual-terminal-sequences.md)** équivalent dans les séquences de **[mise en forme du texte](console-virtual-terminal-sequences.md#text-formatting)** et de **[positionnement des curseurs](console-virtual-terminal-sequences.md#cursor-positioning)** . Placez le curseur à l’emplacement à insérer, appliquez la mise en forme souhaitée, puis écrivez le texte à remplir. Il n’existe aucun équivalent pour émettre du texte dans une zone sans appliquer également la mise en forme des couleurs active. Cette décision aligne intentionnellement la plateforme Windows avec d’autres systèmes d’exploitation, où l’application cliente individuelle est supposée se souvenir de son propre État dessiné pour une manipulation ultérieure.

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | ConsoleApi2. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |
| Noms Unicode et ANSI | **WriteConsoleOutputCharacterW** (Unicode) et **WriteConsoleOutputCharacterA** (ANSI) |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[**COORDONNÉES**](coord-str.md)

[Fonctions de sortie de la console de bas niveau](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)
