---
title: FillConsoleOutputCharacter fonction)
description: Écrit un caractère dans la mémoire tampon d’écran de la console un nombre spécifié de fois, en commençant aux coordonnées spécifiées.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
ms.openlocfilehash: d11e0ef196f9923f1478e17faacd41b43a0511eb
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059212"
---
# <a name="fillconsoleoutputcharacter-function"></a><span data-ttu-id="796bd-104">FillConsoleOutputCharacter fonction)</span><span class="sxs-lookup"><span data-stu-id="796bd-104">FillConsoleOutputCharacter function</span></span>


<span data-ttu-id="796bd-105">Écrit un caractère dans la mémoire tampon d’écran de la console un nombre spécifié de fois, en commençant aux coordonnées spécifiées.</span><span class="sxs-lookup"><span data-stu-id="796bd-105">Writes a character to the console screen buffer a specified number of times, beginning at the specified coordinates.</span></span>

<a name="syntax"></a><span data-ttu-id="796bd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="796bd-106">Syntax</span></span>
------

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

<a name="parameters"></a><span data-ttu-id="796bd-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="796bd-107">Parameters</span></span>
----------

<span data-ttu-id="796bd-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="796bd-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="796bd-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="796bd-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="796bd-110">Le descripteur doit avoir le droit d’accès en \*\* \_ écriture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="796bd-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="796bd-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="796bd-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="796bd-112">*cCharacter* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="796bd-112">*cCharacter* \[in\]</span></span>  
<span data-ttu-id="796bd-113">Caractère à écrire dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="796bd-113">The character to be written to the console screen buffer.</span></span>

<span data-ttu-id="796bd-114">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="796bd-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="796bd-115">Nombre de cellules de caractères dans lesquelles le caractère doit être écrit.</span><span class="sxs-lookup"><span data-stu-id="796bd-115">The number of character cells to which the character should be written.</span></span>

<span data-ttu-id="796bd-116">*dwWriteCoord* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="796bd-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="796bd-117">Structure de [**repère**](coord-str.md) qui spécifie les coordonnées de caractère de la première cellule dans laquelle le caractère doit être écrit.</span><span class="sxs-lookup"><span data-stu-id="796bd-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell to which the character is to be written.</span></span>

<span data-ttu-id="796bd-118">*lpNumberOfCharsWritten* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="796bd-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="796bd-119">Pointeur vers une variable qui reçoit le nombre de caractères réellement écrits dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="796bd-119">A pointer to a variable that receives the number of characters actually written to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="796bd-120">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="796bd-120">Return value</span></span>
------------

<span data-ttu-id="796bd-121">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="796bd-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="796bd-122">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="796bd-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="796bd-123">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="796bd-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="796bd-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="796bd-124">Remarks</span></span>
-------

<span data-ttu-id="796bd-125">Si le nombre de caractères à écrire dépasse la fin de la ligne spécifiée dans la mémoire tampon d’écran de la console, les caractères sont écrits sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="796bd-125">If the number of characters to write to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="796bd-126">Si le nombre de caractères à écrire dépasse la fin de la mémoire tampon d’écran de la console, les caractères sont écrits jusqu’à la fin de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="796bd-126">If the number of characters to write to extends beyond the end of the console screen buffer, the characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="796bd-127">Les valeurs d’attribut aux positions écrites ne sont pas modifiées.</span><span class="sxs-lookup"><span data-stu-id="796bd-127">The attribute values at the positions written are not changed.</span></span>

<span data-ttu-id="796bd-128">Cette fonction utilise des caractères Unicode ou 8 bits à partir de la page de codes actuelle de la console.</span><span class="sxs-lookup"><span data-stu-id="796bd-128">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="796bd-129">La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système.</span><span class="sxs-lookup"><span data-stu-id="796bd-129">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="796bd-130">Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="796bd-130">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="796bd-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="796bd-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="796bd-132">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="796bd-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="796bd-133">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="796bd-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="796bd-134">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="796bd-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="796bd-135">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="796bd-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="796bd-136">En-tête</span><span class="sxs-lookup"><span data-stu-id="796bd-136">Header</span></span></p></td>
<td><span data-ttu-id="796bd-137">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="796bd-137">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="796bd-138">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="796bd-138">Library</span></span></p></td>
<td><span data-ttu-id="796bd-139">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="796bd-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="796bd-140">DLL</span><span class="sxs-lookup"><span data-stu-id="796bd-140">DLL</span></span></p></td>
<td><span data-ttu-id="796bd-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="796bd-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="796bd-142">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="796bd-142">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="796bd-143"><strong>FillConsoleOutputCharacterW</strong> (Unicode) et <strong>FillConsoleOutputCharacterA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="796bd-143"><strong>FillConsoleOutputCharacterW</strong> (Unicode) and <strong>FillConsoleOutputCharacterA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="796bd-144"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="796bd-144"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="796bd-145">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="796bd-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="796bd-146">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="796bd-146">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="796bd-147">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="796bd-147">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="796bd-148">Fonctions de sortie de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="796bd-148">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="796bd-149">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="796bd-149">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="796bd-150">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="796bd-150">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="796bd-151">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="796bd-151">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




