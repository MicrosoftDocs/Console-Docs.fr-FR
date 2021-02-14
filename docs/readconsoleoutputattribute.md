---
title: ReadConsoleOutputAttribute fonction)
description: Copie un nombre spécifié d’attributs de caractères à partir de cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/ReadConsoleOutputAttribute
- wincon/ReadConsoleOutputAttribute
- ReadConsoleOutputAttribute
MS-HAID:
- '\_win32\_readconsoleoutputattribute'
- base.readconsoleoutputattribute
- consoles.readconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c3e35779-a487-47f1-8d07-0d5fae99d54a
topic_type:
- apiref
api_name:
- ReadConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: bf140d9f6721196caa5f62a064ed434554067d62
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358696"
---
# <a name="readconsoleoutputattribute-function"></a><span data-ttu-id="f6d6d-104">ReadConsoleOutputAttribute fonction)</span><span class="sxs-lookup"><span data-stu-id="f6d6d-104">ReadConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="f6d6d-105">Copie un nombre spécifié d’attributs de caractères à partir de cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="f6d6d-105">Copies a specified number of character attributes from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="f6d6d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6d6d-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPWORD  lpAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfAttrsRead
);
```

## <a name="parameters"></a><span data-ttu-id="f6d6d-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f6d6d-107">Parameters</span></span>

<span data-ttu-id="f6d6d-108">*hConsoleOutput* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="f6d6d-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="f6d6d-109">Handle vers la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="f6d6d-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="f6d6d-110">Le handle doit avoir le droit d’accès **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="f6d6d-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="f6d6d-111">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="f6d6d-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="f6d6d-112">*lpAttribute* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="f6d6d-112">*lpAttribute* \[out\]</span></span>  
<span data-ttu-id="f6d6d-113">Pointeur vers une mémoire tampon qui reçoit les attributs utilisés par la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="f6d6d-113">A pointer to a buffer that receives the attributes being used by the console screen buffer.</span></span>

<span data-ttu-id="f6d6d-114">Pour plus d’informations, consultez [attributs de caractères](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="f6d6d-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="f6d6d-115">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="f6d6d-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="f6d6d-116">Nombre de cellules de caractères de la mémoire tampon d’écran à partir desquelles lire.</span><span class="sxs-lookup"><span data-stu-id="f6d6d-116">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="f6d6d-117">La taille de la mémoire tampon vers laquelle pointe le paramètre *lpAttribute* doit être `nLength * sizeof(WORD)` .</span><span class="sxs-lookup"><span data-stu-id="f6d6d-117">The size of the buffer pointed to by the *lpAttribute* parameter should be `nLength * sizeof(WORD)`.</span></span>

<span data-ttu-id="f6d6d-118">*dwReadCoord* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="f6d6d-118">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="f6d6d-119">Coordonnées de la première cellule dans la mémoire tampon d’écran de la console à partir de laquelle lire, en caractères.</span><span class="sxs-lookup"><span data-stu-id="f6d6d-119">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="f6d6d-120">Le membre **X** de la structure [**Coord**](coord-str.md) est la colonne et le membre **Y** est la ligne.</span><span class="sxs-lookup"><span data-stu-id="f6d6d-120">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="f6d6d-121">*lpNumberOfAttrsRead* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="f6d6d-121">*lpNumberOfAttrsRead* \[out\]</span></span>  
<span data-ttu-id="f6d6d-122">Pointeur vers une variable qui reçoit le nombre d’attributs réellement lus.</span><span class="sxs-lookup"><span data-stu-id="f6d6d-122">A pointer to a variable that receives the number of attributes actually read.</span></span>

## <a name="return-value"></a><span data-ttu-id="f6d6d-123">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="f6d6d-123">Return value</span></span>

<span data-ttu-id="f6d6d-124">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="f6d6d-124">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="f6d6d-125">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="f6d6d-125">If the function fails, the return value is zero.</span></span> <span data-ttu-id="f6d6d-126">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="f6d6d-126">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="f6d6d-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="f6d6d-127">Remarks</span></span>

<span data-ttu-id="f6d6d-128">Si le nombre d’attributs à lire est supérieur à la fin de la ligne de mémoire tampon d’écran spécifiée, les attributs sont lus à partir de la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="f6d6d-128">If the number of attributes to be read from extends beyond the end of the specified screen buffer row, attributes are read from the next row.</span></span> <span data-ttu-id="f6d6d-129">Si le nombre d’attributs à lire s’étend au-delà de la fin de la mémoire tampon de l’écran de la console, les attributs jusqu’à la fin de la mémoire tampon de l’écran de la console sont lus.</span><span class="sxs-lookup"><span data-stu-id="f6d6d-129">If the number of attributes to be read from extends beyond the end of the console screen buffer, attributes up to the end of the console screen buffer are read.</span></span>

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="requirements"></a><span data-ttu-id="f6d6d-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f6d6d-130">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="f6d6d-131">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="f6d6d-131">Minimum supported client</span></span> | <span data-ttu-id="f6d6d-132">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="f6d6d-132">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="f6d6d-133">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="f6d6d-133">Minimum supported server</span></span> | <span data-ttu-id="f6d6d-134">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="f6d6d-134">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="f6d6d-135">En-tête</span><span class="sxs-lookup"><span data-stu-id="f6d6d-135">Header</span></span> | <span data-ttu-id="f6d6d-136">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f6d6d-136">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="f6d6d-137">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="f6d6d-137">Library</span></span> | <span data-ttu-id="f6d6d-138">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="f6d6d-138">Kernel32.lib</span></span> |
| <span data-ttu-id="f6d6d-139">DLL</span><span class="sxs-lookup"><span data-stu-id="f6d6d-139">DLL</span></span> | <span data-ttu-id="f6d6d-140">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f6d6d-140">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="f6d6d-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6d6d-141">See also</span></span>

[<span data-ttu-id="f6d6d-142">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="f6d6d-142">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f6d6d-143">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="f6d6d-143">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="f6d6d-144">Fonctions de sortie de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="f6d6d-144">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="f6d6d-145">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="f6d6d-145">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="f6d6d-146">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="f6d6d-146">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="f6d6d-147">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="f6d6d-147">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="f6d6d-148">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="f6d6d-148">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="f6d6d-149">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="f6d6d-149">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)