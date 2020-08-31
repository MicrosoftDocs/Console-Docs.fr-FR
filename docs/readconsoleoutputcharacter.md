---
title: ReadConsoleOutputCharacter fonction)
description: Copie un nombre de caractères à partir de cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/ReadConsoleOutputCharacter
- wincon/ReadConsoleOutputCharacter
- ReadConsoleOutputCharacter
- consoleapi2/ReadConsoleOutputCharacterA
- wincon/ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterA
- consoleapi2/ReadConsoleOutputCharacterW
- wincon/ReadConsoleOutputCharacterW
- ReadConsoleOutputCharacterW
MS-HAID:
- '\_win32\_readconsoleoutputcharacter'
- base.readconsoleoutputcharacter
- consoles.readconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f47464a9-6c59-4f15-abd0-be29ab515698
topic_type:
- apiref
api_name:
- ReadConsoleOutputCharacter
- ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 8f761d10951e6df77a54fd075c29379657204a99
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059452"
---
# <a name="readconsoleoutputcharacter-function"></a><span data-ttu-id="97943-104">ReadConsoleOutputCharacter fonction)</span><span class="sxs-lookup"><span data-stu-id="97943-104">ReadConsoleOutputCharacter function</span></span>


<span data-ttu-id="97943-105">Copie un nombre de caractères à partir de cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="97943-105">Copies a number of characters from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

<a name="syntax"></a><span data-ttu-id="97943-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97943-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPTSTR  lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfCharsRead
);
```

<a name="parameters"></a><span data-ttu-id="97943-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="97943-107">Parameters</span></span>
----------

<span data-ttu-id="97943-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="97943-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="97943-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="97943-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="97943-110">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="97943-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="97943-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="97943-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="97943-112">*lpCharacter* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="97943-112">*lpCharacter* \[out\]</span></span>  
<span data-ttu-id="97943-113">Pointeur vers une mémoire tampon qui reçoit les caractères lus à partir de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="97943-113">A pointer to a buffer that receives the characters read from the console screen buffer.</span></span>

<span data-ttu-id="97943-114">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="97943-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="97943-115">Nombre de cellules de caractères de la mémoire tampon d’écran à partir desquelles lire.</span><span class="sxs-lookup"><span data-stu-id="97943-115">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="97943-116">La taille de la mémoire tampon vers laquelle pointe le paramètre *lpCharacter* doit être `nLength * sizeof(TCHAR)` .</span><span class="sxs-lookup"><span data-stu-id="97943-116">The size of the buffer pointed to by the *lpCharacter* parameter should be `nLength * sizeof(TCHAR)`.</span></span>

<span data-ttu-id="97943-117">*dwReadCoord* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="97943-117">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="97943-118">Coordonnées de la première cellule dans la mémoire tampon d’écran de la console à partir de laquelle lire, en caractères.</span><span class="sxs-lookup"><span data-stu-id="97943-118">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="97943-119">Le membre **X** de la structure [**Coord**](coord-str.md) est la colonne et le membre **Y** est la ligne.</span><span class="sxs-lookup"><span data-stu-id="97943-119">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="97943-120">*lpNumberOfCharsRead* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="97943-120">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="97943-121">Pointeur vers une variable qui reçoit le nombre de caractères réellement lus.</span><span class="sxs-lookup"><span data-stu-id="97943-121">A pointer to a variable that receives the number of characters actually read.</span></span>

<a name="return-value"></a><span data-ttu-id="97943-122">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="97943-122">Return value</span></span>
------------

<span data-ttu-id="97943-123">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="97943-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="97943-124">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="97943-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="97943-125">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="97943-125">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="97943-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="97943-126">Remarks</span></span>
-------

<span data-ttu-id="97943-127">Si le nombre de caractères à lire à partir de s’étend au-delà de la fin de la ligne de mémoire tampon d’écran spécifiée, les caractères sont lus à partir de la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="97943-127">If the number of characters to be read from extends beyond the end of the specified screen buffer row, characters are read from the next row.</span></span> <span data-ttu-id="97943-128">Si le nombre de caractères à lire à partir de s’étend au-delà de la fin de la mémoire tampon d’écran de la console, les caractères jusqu’à la fin de la mémoire tampon d’écran de la console sont lus.</span><span class="sxs-lookup"><span data-stu-id="97943-128">If the number of characters to be read from extends beyond the end of the console screen buffer, characters up to the end of the console screen buffer are read.</span></span>

<span data-ttu-id="97943-129">Cette fonction utilise des caractères Unicode ou 8 bits à partir de la page de codes actuelle de la console.</span><span class="sxs-lookup"><span data-stu-id="97943-129">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="97943-130">La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système.</span><span class="sxs-lookup"><span data-stu-id="97943-130">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="97943-131">Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="97943-131">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="97943-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="97943-132">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="97943-133">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="97943-133">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="97943-134">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="97943-134">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="97943-135">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="97943-135">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="97943-136">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="97943-136">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="97943-137">En-tête</span><span class="sxs-lookup"><span data-stu-id="97943-137">Header</span></span></p></td>
<td><span data-ttu-id="97943-138">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="97943-138">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="97943-139">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="97943-139">Library</span></span></p></td>
<td><span data-ttu-id="97943-140">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="97943-140">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="97943-141">DLL</span><span class="sxs-lookup"><span data-stu-id="97943-141">DLL</span></span></p></td>
<td><span data-ttu-id="97943-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="97943-142">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="97943-143">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="97943-143">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="97943-144"><strong>ReadConsoleOutputCharacterW</strong> (Unicode) et <strong>ReadConsoleOutputCharacterA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="97943-144"><strong>ReadConsoleOutputCharacterW</strong> (Unicode) and <strong>ReadConsoleOutputCharacterA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="97943-145"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97943-145"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="97943-146">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="97943-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="97943-147">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="97943-147">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="97943-148">Fonctions de sortie de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="97943-148">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="97943-149">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="97943-149">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="97943-150">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="97943-150">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="97943-151">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="97943-151">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="97943-152">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="97943-152">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="97943-153">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="97943-153">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="97943-154">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="97943-154">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="97943-155">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="97943-155">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




