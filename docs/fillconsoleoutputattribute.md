---
title: FillConsoleOutputAttribute fonction)
description: Définit les attributs de caractère pour un nombre spécifié de cellules de caractères, en commençant aux coordonnées spécifiées dans une mémoire tampon d’écran.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/FillConsoleOutputAttribute
- wincon/FillConsoleOutputAttribute
- FillConsoleOutputAttribute
MS-HAID:
- '\_win32\_fillconsoleoutputattribute'
- base.fillconsoleoutputattribute
- consoles.fillconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 09440263-71c4-4b7a-8fc6-a2b4fcd677ff
topic_type:
- apiref
api_name:
- FillConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4b3df3a9922655835979136a33628e2be0663f4e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059209"
---
# <a name="fillconsoleoutputattribute-function"></a><span data-ttu-id="9957e-104">FillConsoleOutputAttribute fonction)</span><span class="sxs-lookup"><span data-stu-id="9957e-104">FillConsoleOutputAttribute function</span></span>


<span data-ttu-id="9957e-105">Définit les attributs de caractère pour un nombre spécifié de cellules de caractères, en commençant aux coordonnées spécifiées dans une mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="9957e-105">Sets the character attributes for a specified number of character cells, beginning at the specified coordinates in a screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="9957e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9957e-106">Syntax</span></span>
------

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

<a name="parameters"></a><span data-ttu-id="9957e-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9957e-107">Parameters</span></span>
----------

<span data-ttu-id="9957e-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="9957e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="9957e-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="9957e-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="9957e-110">Le descripteur doit avoir le droit d’accès en \*\* \_ écriture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="9957e-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="9957e-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="9957e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="9957e-112">*wAttribute* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="9957e-112">*wAttribute* \[in\]</span></span>  
<span data-ttu-id="9957e-113">Attributs à utiliser lors de l’écriture dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="9957e-113">The attributes to use when writing to the console screen buffer.</span></span> <span data-ttu-id="9957e-114">Pour plus d’informations, consultez [attributs de caractères](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="9957e-114">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="9957e-115">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="9957e-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="9957e-116">Nombre de cellules de caractères à définir avec les attributs de couleur spécifiés.</span><span class="sxs-lookup"><span data-stu-id="9957e-116">The number of character cells to be set to the specified color attributes.</span></span>

<span data-ttu-id="9957e-117">*dwWriteCoord* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="9957e-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="9957e-118">Structure de [**repère**](coord-str.md) qui spécifie les coordonnées de caractère de la première cellule dont les attributs doivent être définis.</span><span class="sxs-lookup"><span data-stu-id="9957e-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell whose attributes are to be set.</span></span>

<span data-ttu-id="9957e-119">*lpNumberOfAttrsWritten* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="9957e-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="9957e-120">Pointeur vers une variable qui reçoit le nombre de cellules de caractères dont les attributs ont été réellement définis.</span><span class="sxs-lookup"><span data-stu-id="9957e-120">A pointer to a variable that receives the number of character cells whose attributes were actually set.</span></span>

<a name="return-value"></a><span data-ttu-id="9957e-121">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="9957e-121">Return value</span></span>
------------

<span data-ttu-id="9957e-122">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="9957e-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="9957e-123">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="9957e-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="9957e-124">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="9957e-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="9957e-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="9957e-125">Remarks</span></span>
-------

<span data-ttu-id="9957e-126">Si le nombre de cellules de caractères dont les attributs doivent être définis s’étend au-delà de la fin de la ligne spécifiée dans la mémoire tampon d’écran de la console, les cellules de la ligne suivante sont définies.</span><span class="sxs-lookup"><span data-stu-id="9957e-126">If the number of character cells whose attributes are to be set extends beyond the end of the specified row in the console screen buffer, the cells of the next row are set.</span></span> <span data-ttu-id="9957e-127">Si le nombre de cellules à écrire dépasse la fin de la mémoire tampon d’écran de la console, les cellules sont écrites jusqu’à la fin de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="9957e-127">If the number of cells to write to extends beyond the end of the console screen buffer, the cells are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="9957e-128">Les valeurs de caractère aux positions écrites dans ne sont pas modifiées.</span><span class="sxs-lookup"><span data-stu-id="9957e-128">The character values at the positions written to are not changed.</span></span>

<a name="requirements"></a><span data-ttu-id="9957e-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9957e-129">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="9957e-130">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="9957e-130">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="9957e-131">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="9957e-131">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="9957e-132">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="9957e-132">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="9957e-133">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="9957e-133">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="9957e-134">En-tête</span><span class="sxs-lookup"><span data-stu-id="9957e-134">Header</span></span></p></td>
<td><span data-ttu-id="9957e-135">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9957e-135">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="9957e-136">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="9957e-136">Library</span></span></p></td>
<td><span data-ttu-id="9957e-137">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="9957e-137">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="9957e-138">DLL</span><span class="sxs-lookup"><span data-stu-id="9957e-138">DLL</span></span></p></td>
<td><span data-ttu-id="9957e-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9957e-139">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="9957e-140"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9957e-140"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="9957e-141">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="9957e-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="9957e-142">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="9957e-142">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="9957e-143">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="9957e-143">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="9957e-144">Fonctions de sortie de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="9957e-144">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="9957e-145">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="9957e-145">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

[<span data-ttu-id="9957e-146">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="9957e-146">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

 

 




