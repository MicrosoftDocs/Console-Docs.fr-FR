---
title: WriteConsoleOutputCharacter fonction)
description: Copie un nombre de caractères dans les cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
ms.openlocfilehash: bc313abbcb28016968355cc405e0cc2de3d36cb0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059505"
---
# <a name="writeconsoleoutputcharacter-function"></a><span data-ttu-id="2d22a-104">WriteConsoleOutputCharacter fonction)</span><span class="sxs-lookup"><span data-stu-id="2d22a-104">WriteConsoleOutputCharacter function</span></span>


<span data-ttu-id="2d22a-105">Copie un nombre de caractères dans les cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="2d22a-105">Copies a number of characters to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

<a name="syntax"></a><span data-ttu-id="2d22a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d22a-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  LPCTSTR lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

<a name="parameters"></a><span data-ttu-id="2d22a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2d22a-107">Parameters</span></span>
----------

<span data-ttu-id="2d22a-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="2d22a-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="2d22a-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="2d22a-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="2d22a-110">Le descripteur doit avoir le droit d’accès en \*\* \_ écriture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="2d22a-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="2d22a-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="2d22a-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="2d22a-112">*lpCharacter* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="2d22a-112">*lpCharacter* \[in\]</span></span>  
<span data-ttu-id="2d22a-113">Caractères à écrire dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="2d22a-113">The characters to be written to the console screen buffer.</span></span>

<span data-ttu-id="2d22a-114">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="2d22a-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="2d22a-115">Nombre de caractères à écrire.</span><span class="sxs-lookup"><span data-stu-id="2d22a-115">The number of characters to be written.</span></span>

<span data-ttu-id="2d22a-116">*dwWriteCoord* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="2d22a-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="2d22a-117">Structure de [**repère**](coord-str.md) qui spécifie les coordonnées de caractères de la première cellule dans la mémoire tampon d’écran de la console dans laquelle les caractères seront écrits.</span><span class="sxs-lookup"><span data-stu-id="2d22a-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which characters will be written.</span></span>

<span data-ttu-id="2d22a-118">*lpNumberOfCharsWritten* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="2d22a-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="2d22a-119">Pointeur vers une variable qui reçoit le nombre de caractères réellement écrits.</span><span class="sxs-lookup"><span data-stu-id="2d22a-119">A pointer to a variable that receives the number of characters actually written.</span></span>

<a name="return-value"></a><span data-ttu-id="2d22a-120">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="2d22a-120">Return value</span></span>
------------

<span data-ttu-id="2d22a-121">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="2d22a-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="2d22a-122">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="2d22a-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="2d22a-123">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="2d22a-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="2d22a-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="2d22a-124">Remarks</span></span>
-------

<span data-ttu-id="2d22a-125">Si le nombre de caractères à écrire dans s’étend au-delà de la fin de la ligne spécifiée dans la mémoire tampon d’écran de la console, les caractères sont écrits sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="2d22a-125">If the number of characters to be written to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="2d22a-126">Si le nombre de caractères à écrire dans s’étend au-delà de la fin de la mémoire tampon d’écran de la console, les caractères sont écrits jusqu’à la fin de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="2d22a-126">If the number of characters to be written to extends beyond the end of the console screen buffer, characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="2d22a-127">Les valeurs d’attribut aux positions écrites dans ne sont pas modifiées.</span><span class="sxs-lookup"><span data-stu-id="2d22a-127">The attribute values at the positions written to are not changed.</span></span>

<span data-ttu-id="2d22a-128">Cette fonction utilise des caractères Unicode ou 8 bits à partir de la page de codes actuelle de la console.</span><span class="sxs-lookup"><span data-stu-id="2d22a-128">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="2d22a-129">La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système.</span><span class="sxs-lookup"><span data-stu-id="2d22a-129">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="2d22a-130">Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="2d22a-130">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="2d22a-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2d22a-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="2d22a-132">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="2d22a-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="2d22a-133">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="2d22a-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2d22a-134">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="2d22a-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="2d22a-135">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="2d22a-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2d22a-136">En-tête</span><span class="sxs-lookup"><span data-stu-id="2d22a-136">Header</span></span></p></td>
<td><span data-ttu-id="2d22a-137">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2d22a-137">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2d22a-138">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="2d22a-138">Library</span></span></p></td>
<td><span data-ttu-id="2d22a-139">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="2d22a-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2d22a-140">DLL</span><span class="sxs-lookup"><span data-stu-id="2d22a-140">DLL</span></span></p></td>
<td><span data-ttu-id="2d22a-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2d22a-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2d22a-142">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="2d22a-142">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="2d22a-143"><strong>WriteConsoleOutputCharacterW</strong> (Unicode) et <strong>WriteConsoleOutputCharacterA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="2d22a-143"><strong>WriteConsoleOutputCharacterW</strong> (Unicode) and <strong>WriteConsoleOutputCharacterA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="2d22a-144"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d22a-144"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="2d22a-145">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="2d22a-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2d22a-146">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="2d22a-146">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="2d22a-147">Fonctions de sortie de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="2d22a-147">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="2d22a-148">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="2d22a-148">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="2d22a-149">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="2d22a-149">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="2d22a-150">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="2d22a-150">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="2d22a-151">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="2d22a-151">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="2d22a-152">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="2d22a-152">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="2d22a-153">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="2d22a-153">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="2d22a-154">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="2d22a-154">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

 

 




