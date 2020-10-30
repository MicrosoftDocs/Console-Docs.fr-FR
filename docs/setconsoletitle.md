---
title: SetConsoleTitle fonction)
description: Consultez les informations de référence sur la fonction SetConsoleTitle, qui définit le titre de la fenêtre de console active.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/SetConsoleTitle
- wincon/SetConsoleTitle
- SetConsoleTitle
- consoleapi2/SetConsoleTitleA
- wincon/SetConsoleTitleA
- SetConsoleTitleA
- consoleapi2/SetConsoleTitleW
- wincon/SetConsoleTitleW
- SetConsoleTitleW
MS-HAID:
- '\_win32\_setconsoletitle'
- base.setconsoletitle
- consoles.setconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f1db449b-0dd0-4d61-bb79-b7da9a5168f4
topic_type:
- apiref
api_name:
- SetConsoleTitle
- SetConsoleTitleA
- SetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: fa4f79925af870f3d345f384dab52ff4b98c182c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037031"
---
# <a name="setconsoletitle-function"></a>SetConsoleTitle fonction)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Définit le titre de la fenêtre de console active.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI SetConsoleTitle(
  _In_ LPCTSTR lpConsoleTitle
);
```

## <a name="parameters"></a>Paramètres

*lpConsoleTitle* \[ dans\]  
Chaîne à afficher dans la barre de titre de la fenêtre de console. La taille totale doit être inférieure à 64 Ko.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Remarques

Lorsque le processus se termine, le système restaure le titre de la console d’origine.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Cette API a un équivalent **[terminal virtuel](console-virtual-terminal-sequences.md)** dans les séquences de titre de la **[fenêtre](console-virtual-terminal-sequences.md#window-title)** . Les _séquences de terminaux virtuels_ sont recommandées pour tout développement nouveau et en cours.

## <a name="examples"></a>Exemples

L’exemple suivant montre comment récupérer et modifier le titre de la console.

```C
#include <windows.h>
#include <tchar.h>
#include <conio.h>
#include <strsafe.h>

int main( void )
{
   TCHAR szOldTitle[MAX_PATH];
   TCHAR szNewTitle[MAX_PATH];

   // Save current console title.

   if( GetConsoleTitle(szOldTitle, MAX_PATH) )
   {
      // Build new console title string.

      StringCchPrintf(szNewTitle, MAX_PATH, TEXT("TEST: %s"), szOldTitle);

      // Set console title to new title
      if( !SetConsoleTitle(szNewTitle) )
      {
         _tprintf(TEXT("SetConsoleTitle failed (%d)\n"), GetLastError());
         return 1;
      }
      else
      {
         _tprintf(TEXT("SetConsoleTitle succeeded.\n"));
      }
   }
   return 0;
}
```

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | ConsoleApi2. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |
| Noms Unicode et ANSI | **SetConsoleTitleW** (Unicode) et **SetConsoleTitleA** (ANSI) |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md)

[**GetConsoleTitle**](getconsoletitle.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)
