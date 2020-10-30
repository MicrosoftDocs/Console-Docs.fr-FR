---
title: FillConsoleOutputCharacter fonction)
description: Écrit un caractère dans la mémoire tampon d’écran de la console un nombre spécifié de fois, en commençant aux coordonnées spécifiées.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/FillConsoleOutputCharacter
- wincon/FillConsoleOutputCharacter
- FillConsoleOutputCharacter
- consoleapi2/FillConsoleOutputCharacterA
- wincon/FillConsoleOutputCharacterA
- FillConsoleOutputCharacterA
- consoleapi2/FillConsoleOutputCharacterW
- wincon/FillConsoleOutputCharacterW
- FillConsoleOutputCharacterW
MS-HAID:
- '\_win32\_fillconsoleoutputcharacter'
- base.fillconsoleoutputcharacter
- consoles.fillconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 37579cc9-14b3-4fd9-81ed-abaad5c7bd1a
topic_type:
- apiref
api_name:
- FillConsoleOutputCharacter
- FillConsoleOutputCharacterA
- FillConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 8860a1feab39bc83f28a867fa9acc491cc00e4b7
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038187"
---
# <a name="fillconsoleoutputcharacter-function"></a>FillConsoleOutputCharacter fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Écrit un caractère dans la mémoire tampon d’écran de la console un nombre spécifié de fois, en commençant aux coordonnées spécifiées.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a>Paramètres

*hConsoleOutput* \[ dans\]  
Handle vers la mémoire tampon d’écran de la console. Le descripteur doit avoir le droit d’accès en **\_ écriture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*cCharacter* \[ dans\]  
Caractère à écrire dans la mémoire tampon d’écran de la console.

*nLength* \[ dans\]  
Nombre de cellules de caractères dans lesquelles le caractère doit être écrit.

*dwWriteCoord* \[ dans\]  
Structure de [**repère**](coord-str.md) qui spécifie les coordonnées de caractère de la première cellule dans laquelle le caractère doit être écrit.

*lpNumberOfCharsWritten* \[ à\]  
Pointeur vers une variable qui reçoit le nombre de caractères réellement écrits dans la mémoire tampon d’écran de la console.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Si le nombre de caractères à écrire dépasse la fin de la ligne spécifiée dans la mémoire tampon d’écran de la console, les caractères sont écrits sur la ligne suivante. Si le nombre de caractères à écrire dépasse la fin de la mémoire tampon d’écran de la console, les caractères sont écrits jusqu’à la fin de la mémoire tampon d’écran de la console.

Les valeurs d’attribut aux positions écrites ne sont pas modifiées.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Cette API n’est pas recommandée et n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** spécifique. Le remplissage de la région en dehors de la fenêtre affichable n’est pas pris en charge et est réservé à l’espace d’historique du terminal. Le remplissage d’une zone visible avec un nouveau texte ou une nouvelle couleur est effectué via **[le déplacement du curseur](console-virtual-terminal-sequences.md#cursor-positioning)** , la **[définition des nouveaux attributs](console-virtual-terminal-sequences.md#text-formatting)** , puis l’écriture du texte souhaité pour cette région, en répétant les caractères si nécessaire pour la longueur de la séquence de remplissage. Des mouvements de curseur supplémentaires peuvent être nécessaires, suivis par l’écriture du texte souhaité pour remplir une zone rectangulaire. L’application cliente doit conserver sa propre mémoire sur l’écran et ne peut pas interroger l’État distant. Vous trouverez plus d’informations dans la documentation de la **[console classique et du terminal virtuel](classic-vs-vt.md)** .

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | ConsoleApi2. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |
| Noms Unicode et ANSI | **FillConsoleOutputCharacterW** (Unicode) et **FillConsoleOutputCharacterA** (ANSI) |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[**COORDONNÉES**](coord-str.md)

[**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)

[Fonctions de sortie de la console de bas niveau](low-level-console-output-functions.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)
