---
title: WriteConsoleOutputAttribute fonction)
description: Copie un certain nombre d’attributs de caractères dans des cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/WriteConsoleOutputAttribute
- wincon/WriteConsoleOutputAttribute
- WriteConsoleOutputAttribute
MS-HAID:
- '\_win32\_writeconsoleoutputattribute'
- base.writeconsoleoutputattribute
- consoles.writeconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 52a9d6e5-072e-4411-9945-10bd3dd61e25
topic_type:
- apiref
api_name:
- WriteConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e7c684b2f450713eaa78730676a0148e9b090c79
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059509"
---
# <a name="writeconsoleoutputattribute-function"></a><span data-ttu-id="8d0f9-104">WriteConsoleOutputAttribute fonction)</span><span class="sxs-lookup"><span data-stu-id="8d0f9-104">WriteConsoleOutputAttribute function</span></span>


<span data-ttu-id="8d0f9-105">Copie un certain nombre d’attributs de caractères dans des cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="8d0f9-105">Copies a number of character attributes to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

<a name="syntax"></a><span data-ttu-id="8d0f9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d0f9-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

<a name="parameters"></a><span data-ttu-id="8d0f9-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8d0f9-107">Parameters</span></span>
----------

<span data-ttu-id="8d0f9-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="8d0f9-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="8d0f9-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="8d0f9-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="8d0f9-110">Le descripteur doit avoir le droit d’accès en \*\* \_ écriture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="8d0f9-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="8d0f9-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="8d0f9-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="8d0f9-112">*lpAttribute* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="8d0f9-112">*lpAttribute* \[in\]</span></span>  
<span data-ttu-id="8d0f9-113">Attributs à utiliser lors de l’écriture dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="8d0f9-113">The attributes to be used when writing to the console screen buffer.</span></span> <span data-ttu-id="8d0f9-114">Pour plus d’informations, consultez [attributs de caractères](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="8d0f9-114">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="8d0f9-115">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="8d0f9-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="8d0f9-116">Nombre de cellules de caractères de la mémoire tampon d’écran vers lesquelles les attributs seront copiés.</span><span class="sxs-lookup"><span data-stu-id="8d0f9-116">The number of screen buffer character cells to which the attributes will be copied.</span></span>

<span data-ttu-id="8d0f9-117">*dwWriteCoord* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="8d0f9-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="8d0f9-118">Structure de [**repère**](coord-str.md) qui spécifie les coordonnées de caractères de la première cellule dans la mémoire tampon d’écran de la console dans laquelle les attributs seront écrits.</span><span class="sxs-lookup"><span data-stu-id="8d0f9-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which the attributes will be written.</span></span>

<span data-ttu-id="8d0f9-119">*lpNumberOfAttrsWritten* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="8d0f9-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="8d0f9-120">Pointeur vers une variable qui reçoit le nombre d’attributs réellement écrits dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="8d0f9-120">A pointer to a variable that receives the number of attributes actually written to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="8d0f9-121">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="8d0f9-121">Return value</span></span>
------------

<span data-ttu-id="8d0f9-122">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="8d0f9-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="8d0f9-123">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="8d0f9-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="8d0f9-124">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="8d0f9-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="8d0f9-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="8d0f9-125">Remarks</span></span>
-------

<span data-ttu-id="8d0f9-126">Si le nombre d’attributs à écrire dans s’étend au-delà de la fin de la ligne spécifiée dans la mémoire tampon d’écran de la console, les attributs sont écrits sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="8d0f9-126">If the number of attributes to be written to extends beyond the end of the specified row in the console screen buffer, attributes are written to the next row.</span></span> <span data-ttu-id="8d0f9-127">Si le nombre d’attributs à écrire dans s’étend au-delà de la fin de la mémoire tampon d’écran de la console, les attributs sont écrits jusqu’à la fin de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="8d0f9-127">If the number of attributes to be written to extends beyond the end of the console screen buffer, the attributes are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="8d0f9-128">Les valeurs de caractère aux positions écrites dans ne sont pas modifiées.</span><span class="sxs-lookup"><span data-stu-id="8d0f9-128">The character values at the positions written to are not changed.</span></span>

<a name="requirements"></a><span data-ttu-id="8d0f9-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8d0f9-129">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="8d0f9-130">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="8d0f9-130">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="8d0f9-131">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="8d0f9-131">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="8d0f9-132">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="8d0f9-132">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="8d0f9-133">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="8d0f9-133">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="8d0f9-134">En-tête</span><span class="sxs-lookup"><span data-stu-id="8d0f9-134">Header</span></span></p></td>
<td><span data-ttu-id="8d0f9-135">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="8d0f9-135">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="8d0f9-136">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="8d0f9-136">Library</span></span></p></td>
<td><span data-ttu-id="8d0f9-137">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="8d0f9-137">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="8d0f9-138">DLL</span><span class="sxs-lookup"><span data-stu-id="8d0f9-138">DLL</span></span></p></td>
<td><span data-ttu-id="8d0f9-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="8d0f9-139">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="8d0f9-140"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d0f9-140"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="8d0f9-141">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="8d0f9-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="8d0f9-142">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="8d0f9-142">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="8d0f9-143">Fonctions de sortie de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="8d0f9-143">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="8d0f9-144">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="8d0f9-144">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="8d0f9-145">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="8d0f9-145">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="8d0f9-146">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="8d0f9-146">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="8d0f9-147">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="8d0f9-147">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="8d0f9-148">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="8d0f9-148">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




