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
# <a name="setconsoletitle-function"></a><span data-ttu-id="b9315-104">SetConsoleTitle fonction)</span><span class="sxs-lookup"><span data-stu-id="b9315-104">SetConsoleTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="b9315-105">Définit le titre de la fenêtre de console active.</span><span class="sxs-lookup"><span data-stu-id="b9315-105">Sets the title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9315-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9315-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleTitle(
  _In_ LPCTSTR lpConsoleTitle
);
```

## <a name="parameters"></a><span data-ttu-id="b9315-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b9315-107">Parameters</span></span>

<span data-ttu-id="b9315-108">*lpConsoleTitle* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="b9315-108">*lpConsoleTitle* \[in\]</span></span>  
<span data-ttu-id="b9315-109">Chaîne à afficher dans la barre de titre de la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="b9315-109">The string to be displayed in the title bar of the console window.</span></span> <span data-ttu-id="b9315-110">La taille totale doit être inférieure à 64 Ko.</span><span class="sxs-lookup"><span data-stu-id="b9315-110">The total size must be less than 64K.</span></span>

## <a name="return-value"></a><span data-ttu-id="b9315-111">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="b9315-111">Return value</span></span>

<span data-ttu-id="b9315-112">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="b9315-112">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b9315-113">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="b9315-113">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b9315-114">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="b9315-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="b9315-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="b9315-115">Remarks</span></span>

<span data-ttu-id="b9315-116">Lorsque le processus se termine, le système restaure le titre de la console d’origine.</span><span class="sxs-lookup"><span data-stu-id="b9315-116">When the process terminates, the system restores the original console title.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="b9315-117">Cette API a un équivalent **[terminal virtuel](console-virtual-terminal-sequences.md)** dans les séquences de titre de la **[fenêtre](console-virtual-terminal-sequences.md#window-title)** .</span><span class="sxs-lookup"><span data-stu-id="b9315-117">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[window title](console-virtual-terminal-sequences.md#window-title)** sequences.</span></span> <span data-ttu-id="b9315-118">Les _séquences de terminaux virtuels_ sont recommandées pour tout développement nouveau et en cours.</span><span class="sxs-lookup"><span data-stu-id="b9315-118">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="b9315-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="b9315-119">Examples</span></span>

<span data-ttu-id="b9315-120">L’exemple suivant montre comment récupérer et modifier le titre de la console.</span><span class="sxs-lookup"><span data-stu-id="b9315-120">The following example shows how to retrieve and modify the console title.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="b9315-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b9315-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b9315-122">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="b9315-122">Minimum supported client</span></span> | <span data-ttu-id="b9315-123">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="b9315-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="b9315-124">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="b9315-124">Minimum supported server</span></span> | <span data-ttu-id="b9315-125">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="b9315-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="b9315-126">En-tête</span><span class="sxs-lookup"><span data-stu-id="b9315-126">Header</span></span> | <span data-ttu-id="b9315-127">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b9315-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="b9315-128">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="b9315-128">Library</span></span> | <span data-ttu-id="b9315-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="b9315-129">Kernel32.lib</span></span> |
| <span data-ttu-id="b9315-130">DLL</span><span class="sxs-lookup"><span data-stu-id="b9315-130">DLL</span></span> | <span data-ttu-id="b9315-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b9315-131">Kernel32.dll</span></span> |
| <span data-ttu-id="b9315-132">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="b9315-132">Unicode and ANSI names</span></span> | <span data-ttu-id="b9315-133">**SetConsoleTitleW** (Unicode) et **SetConsoleTitleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="b9315-133">**SetConsoleTitleW** (Unicode) and **SetConsoleTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="b9315-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9315-134">See also</span></span>

[<span data-ttu-id="b9315-135">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="b9315-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b9315-136">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="b9315-136">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="b9315-137">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="b9315-137">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="b9315-138">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="b9315-138">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="b9315-139">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="b9315-139">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)
