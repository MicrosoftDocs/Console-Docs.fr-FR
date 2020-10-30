---
title: ReadConsoleOutputCharacter fonction)
description: Copie un nombre de caractères à partir de cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
ms.openlocfilehash: fa70841d5dccf3289807d29c67fab86e3b445279
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037720"
---
# <a name="readconsoleoutputcharacter-function"></a><span data-ttu-id="9bc5e-104">ReadConsoleOutputCharacter fonction)</span><span class="sxs-lookup"><span data-stu-id="9bc5e-104">ReadConsoleOutputCharacter function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="9bc5e-105">Copie un nombre de caractères à partir de cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="9bc5e-105">Copies a number of characters from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="9bc5e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bc5e-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPTSTR  lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfCharsRead
);
```

## <a name="parameters"></a><span data-ttu-id="9bc5e-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9bc5e-107">Parameters</span></span>

<span data-ttu-id="9bc5e-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="9bc5e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="9bc5e-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="9bc5e-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="9bc5e-110">Le handle doit avoir le droit d’accès **\_ en lecture générique** .</span><span class="sxs-lookup"><span data-stu-id="9bc5e-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="9bc5e-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="9bc5e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="9bc5e-112">*lpCharacter* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="9bc5e-112">*lpCharacter* \[out\]</span></span>  
<span data-ttu-id="9bc5e-113">Pointeur vers une mémoire tampon qui reçoit les caractères lus à partir de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="9bc5e-113">A pointer to a buffer that receives the characters read from the console screen buffer.</span></span>

<span data-ttu-id="9bc5e-114">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="9bc5e-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="9bc5e-115">Nombre de cellules de caractères de la mémoire tampon d’écran à partir desquelles lire.</span><span class="sxs-lookup"><span data-stu-id="9bc5e-115">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="9bc5e-116">La taille de la mémoire tampon vers laquelle pointe le paramètre *lpCharacter* doit être `nLength * sizeof(TCHAR)` .</span><span class="sxs-lookup"><span data-stu-id="9bc5e-116">The size of the buffer pointed to by the *lpCharacter* parameter should be `nLength * sizeof(TCHAR)`.</span></span>

<span data-ttu-id="9bc5e-117">*dwReadCoord* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="9bc5e-117">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="9bc5e-118">Coordonnées de la première cellule dans la mémoire tampon d’écran de la console à partir de laquelle lire, en caractères.</span><span class="sxs-lookup"><span data-stu-id="9bc5e-118">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="9bc5e-119">Le membre **X** de la structure [**Coord**](coord-str.md) est la colonne et le membre **Y** est la ligne.</span><span class="sxs-lookup"><span data-stu-id="9bc5e-119">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="9bc5e-120">*lpNumberOfCharsRead* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="9bc5e-120">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="9bc5e-121">Pointeur vers une variable qui reçoit le nombre de caractères réellement lus.</span><span class="sxs-lookup"><span data-stu-id="9bc5e-121">A pointer to a variable that receives the number of characters actually read.</span></span>

## <a name="return-value"></a><span data-ttu-id="9bc5e-122">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="9bc5e-122">Return value</span></span>

<span data-ttu-id="9bc5e-123">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="9bc5e-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="9bc5e-124">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="9bc5e-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="9bc5e-125">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="9bc5e-125">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="9bc5e-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="9bc5e-126">Remarks</span></span>

<span data-ttu-id="9bc5e-127">Si le nombre de caractères à lire à partir de s’étend au-delà de la fin de la ligne de mémoire tampon d’écran spécifiée, les caractères sont lus à partir de la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="9bc5e-127">If the number of characters to be read from extends beyond the end of the specified screen buffer row, characters are read from the next row.</span></span> <span data-ttu-id="9bc5e-128">Si le nombre de caractères à lire à partir de s’étend au-delà de la fin de la mémoire tampon d’écran de la console, les caractères jusqu’à la fin de la mémoire tampon d’écran de la console sont lus.</span><span class="sxs-lookup"><span data-stu-id="9bc5e-128">If the number of characters to be read from extends beyond the end of the console screen buffer, characters up to the end of the console screen buffer are read.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="requirements"></a><span data-ttu-id="9bc5e-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9bc5e-129">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="9bc5e-130">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="9bc5e-130">Minimum supported client</span></span> | <span data-ttu-id="9bc5e-131">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="9bc5e-131">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="9bc5e-132">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="9bc5e-132">Minimum supported server</span></span> | <span data-ttu-id="9bc5e-133">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="9bc5e-133">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="9bc5e-134">En-tête</span><span class="sxs-lookup"><span data-stu-id="9bc5e-134">Header</span></span> | <span data-ttu-id="9bc5e-135">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9bc5e-135">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="9bc5e-136">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="9bc5e-136">Library</span></span> | <span data-ttu-id="9bc5e-137">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="9bc5e-137">Kernel32.lib</span></span> |
| <span data-ttu-id="9bc5e-138">DLL</span><span class="sxs-lookup"><span data-stu-id="9bc5e-138">DLL</span></span> | <span data-ttu-id="9bc5e-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9bc5e-139">Kernel32.dll</span></span> |
| <span data-ttu-id="9bc5e-140">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="9bc5e-140">Unicode and ANSI names</span></span> | <span data-ttu-id="9bc5e-141">**ReadConsoleOutputCharacterW** (Unicode) et **ReadConsoleOutputCharacterA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="9bc5e-141">**ReadConsoleOutputCharacterW** (Unicode) and **ReadConsoleOutputCharacterA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="9bc5e-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9bc5e-142">See also</span></span>

[<span data-ttu-id="9bc5e-143">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="9bc5e-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="9bc5e-144">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="9bc5e-144">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="9bc5e-145">Fonctions de sortie de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="9bc5e-145">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="9bc5e-146">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="9bc5e-146">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="9bc5e-147">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="9bc5e-147">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="9bc5e-148">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="9bc5e-148">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="9bc5e-149">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="9bc5e-149">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="9bc5e-150">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="9bc5e-150">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="9bc5e-151">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="9bc5e-151">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="9bc5e-152">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="9bc5e-152">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
