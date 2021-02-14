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
ms.openlocfilehash: 5955bba0c7b317dbcdbc9593b60bfb3092376dc1
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358539"
---
# <a name="setconsoletitle-function"></a><span data-ttu-id="b32da-104">SetConsoleTitle fonction)</span><span class="sxs-lookup"><span data-stu-id="b32da-104">SetConsoleTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="b32da-105">Définit le titre de la fenêtre de console active.</span><span class="sxs-lookup"><span data-stu-id="b32da-105">Sets the title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="b32da-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b32da-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleTitle(
  _In_ LPCTSTR lpConsoleTitle
);
```

## <a name="parameters"></a><span data-ttu-id="b32da-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b32da-107">Parameters</span></span>

<span data-ttu-id="b32da-108">*lpConsoleTitle* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="b32da-108">*lpConsoleTitle* \[in\]</span></span>  
<span data-ttu-id="b32da-109">Chaîne à afficher dans la barre de titre de la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="b32da-109">The string to be displayed in the title bar of the console window.</span></span> <span data-ttu-id="b32da-110">La taille totale doit être inférieure à 64 Ko.</span><span class="sxs-lookup"><span data-stu-id="b32da-110">The total size must be less than 64K.</span></span>

## <a name="return-value"></a><span data-ttu-id="b32da-111">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="b32da-111">Return value</span></span>

<span data-ttu-id="b32da-112">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="b32da-112">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b32da-113">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="b32da-113">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b32da-114">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="b32da-114">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="b32da-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="b32da-115">Remarks</span></span>

<span data-ttu-id="b32da-116">Lorsque le processus se termine, le système restaure le titre de la console d’origine.</span><span class="sxs-lookup"><span data-stu-id="b32da-116">When the process terminates, the system restores the original console title.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="b32da-117">Cette API a un équivalent **[terminal virtuel](console-virtual-terminal-sequences.md)** dans les séquences de titre de la **[fenêtre](console-virtual-terminal-sequences.md#window-title)** .</span><span class="sxs-lookup"><span data-stu-id="b32da-117">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[window title](console-virtual-terminal-sequences.md#window-title)** sequences.</span></span> <span data-ttu-id="b32da-118">Les _séquences de terminaux virtuels_ sont recommandées pour tout développement nouveau et en cours.</span><span class="sxs-lookup"><span data-stu-id="b32da-118">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="b32da-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="b32da-119">Examples</span></span>

<span data-ttu-id="b32da-120">L’exemple suivant montre comment récupérer et modifier le titre de la console.</span><span class="sxs-lookup"><span data-stu-id="b32da-120">The following example shows how to retrieve and modify the console title.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="b32da-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b32da-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b32da-122">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="b32da-122">Minimum supported client</span></span> | <span data-ttu-id="b32da-123">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="b32da-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="b32da-124">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="b32da-124">Minimum supported server</span></span> | <span data-ttu-id="b32da-125">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="b32da-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="b32da-126">En-tête</span><span class="sxs-lookup"><span data-stu-id="b32da-126">Header</span></span> | <span data-ttu-id="b32da-127">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b32da-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="b32da-128">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="b32da-128">Library</span></span> | <span data-ttu-id="b32da-129">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="b32da-129">Kernel32.lib</span></span> |
| <span data-ttu-id="b32da-130">DLL</span><span class="sxs-lookup"><span data-stu-id="b32da-130">DLL</span></span> | <span data-ttu-id="b32da-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b32da-131">Kernel32.dll</span></span> |
| <span data-ttu-id="b32da-132">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="b32da-132">Unicode and ANSI names</span></span> | <span data-ttu-id="b32da-133">**SetConsoleTitleW** (Unicode) et **SetConsoleTitleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="b32da-133">**SetConsoleTitleW** (Unicode) and **SetConsoleTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="b32da-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b32da-134">See also</span></span>

[<span data-ttu-id="b32da-135">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="b32da-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b32da-136">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="b32da-136">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="b32da-137">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="b32da-137">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="b32da-138">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="b32da-138">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="b32da-139">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="b32da-139">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)