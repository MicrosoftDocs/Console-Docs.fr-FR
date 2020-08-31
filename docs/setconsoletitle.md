---
title: SetConsoleTitle fonction)
description: Consultez les informations de référence sur la fonction SetConsoleTitle, qui définit le titre de la fenêtre de console active.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
ms.openlocfilehash: e1789243fd5c184221dd53038d8ec87c9b010749
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059513"
---
# <a name="setconsoletitle-function"></a><span data-ttu-id="007d2-104">SetConsoleTitle fonction)</span><span class="sxs-lookup"><span data-stu-id="007d2-104">SetConsoleTitle function</span></span>


<span data-ttu-id="007d2-105">Définit le titre de la fenêtre de console active.</span><span class="sxs-lookup"><span data-stu-id="007d2-105">Sets the title for the current console window.</span></span>

<a name="syntax"></a><span data-ttu-id="007d2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="007d2-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleTitle(
  _In_ LPCTSTR lpConsoleTitle
);
```

<a name="parameters"></a><span data-ttu-id="007d2-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="007d2-107">Parameters</span></span>
----------

<span data-ttu-id="007d2-108">*lpConsoleTitle* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="007d2-108">*lpConsoleTitle* \[in\]</span></span>  
<span data-ttu-id="007d2-109">Chaîne à afficher dans la barre de titre de la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="007d2-109">The string to be displayed in the title bar of the console window.</span></span> <span data-ttu-id="007d2-110">La taille totale doit être inférieure à 64 Ko.</span><span class="sxs-lookup"><span data-stu-id="007d2-110">The total size must be less than 64K.</span></span>

<a name="return-value"></a><span data-ttu-id="007d2-111">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="007d2-111">Return value</span></span>
------------

<span data-ttu-id="007d2-112">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="007d2-112">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="007d2-113">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="007d2-113">If the function fails, the return value is zero.</span></span> <span data-ttu-id="007d2-114">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="007d2-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="007d2-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="007d2-115">Remarks</span></span>
-------

<span data-ttu-id="007d2-116">Lorsque le processus se termine, le système restaure le titre de la console d’origine.</span><span class="sxs-lookup"><span data-stu-id="007d2-116">When the process terminates, the system restores the original console title.</span></span>

<span data-ttu-id="007d2-117">Cette fonction utilise des caractères Unicode ou 8 bits à partir de la page de codes actuelle de la console.</span><span class="sxs-lookup"><span data-stu-id="007d2-117">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="007d2-118">La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système.</span><span class="sxs-lookup"><span data-stu-id="007d2-118">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="007d2-119">Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="007d2-119">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="007d2-120">Exemples</span><span class="sxs-lookup"><span data-stu-id="007d2-120">Examples</span></span>
--------

<span data-ttu-id="007d2-121">L’exemple suivant montre comment récupérer et modifier le titre de la console.</span><span class="sxs-lookup"><span data-stu-id="007d2-121">The following example shows how to retrieve and modify the console title.</span></span>

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

<a name="requirements"></a><span data-ttu-id="007d2-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="007d2-122">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="007d2-123">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="007d2-123">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="007d2-124">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="007d2-124">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="007d2-125">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="007d2-125">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="007d2-126">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="007d2-126">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="007d2-127">En-tête</span><span class="sxs-lookup"><span data-stu-id="007d2-127">Header</span></span></p></td>
<td><span data-ttu-id="007d2-128">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="007d2-128">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="007d2-129">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="007d2-129">Library</span></span></p></td>
<td><span data-ttu-id="007d2-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="007d2-130">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="007d2-131">DLL</span><span class="sxs-lookup"><span data-stu-id="007d2-131">DLL</span></span></p></td>
<td><span data-ttu-id="007d2-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="007d2-132">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="007d2-133">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="007d2-133">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="007d2-134"><strong>SetConsoleTitleW</strong> (Unicode) et <strong>SetConsoleTitleA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="007d2-134"><strong>SetConsoleTitleW</strong> (Unicode) and <strong>SetConsoleTitleA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="007d2-135"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="007d2-135"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="007d2-136">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="007d2-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="007d2-137">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="007d2-137">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="007d2-138">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="007d2-138">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="007d2-139">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="007d2-139">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="007d2-140">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="007d2-140">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

 

 




