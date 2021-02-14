---
title: WriteConsoleOutputCharacter fonction)
description: Copie un nombre de caractères dans les cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
ms.openlocfilehash: 87d6e8768f55135536b1c0f752cc8f7827c643f1
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359039"
---
# <a name="writeconsoleoutputcharacter-function"></a><span data-ttu-id="2476d-104">WriteConsoleOutputCharacter fonction)</span><span class="sxs-lookup"><span data-stu-id="2476d-104">WriteConsoleOutputCharacter function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="2476d-105">Copie un nombre de caractères dans les cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="2476d-105">Copies a number of characters to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="2476d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2476d-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  LPCTSTR lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="2476d-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2476d-107">Parameters</span></span>

<span data-ttu-id="2476d-108">*hConsoleOutput* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="2476d-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="2476d-109">Handle vers la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="2476d-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="2476d-110">Le handle doit avoir le droit d’accès **GENERIC\_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="2476d-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="2476d-111">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="2476d-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="2476d-112">*lpCharacter* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="2476d-112">*lpCharacter* \[in\]</span></span>  
<span data-ttu-id="2476d-113">Caractères à écrire dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="2476d-113">The characters to be written to the console screen buffer.</span></span>

<span data-ttu-id="2476d-114">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="2476d-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="2476d-115">Nombre de caractères à écrire.</span><span class="sxs-lookup"><span data-stu-id="2476d-115">The number of characters to be written.</span></span>

<span data-ttu-id="2476d-116">*dwWriteCoord* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="2476d-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="2476d-117">Structure de [**repère**](coord-str.md) qui spécifie les coordonnées de caractères de la première cellule dans la mémoire tampon d’écran de la console dans laquelle les caractères seront écrits.</span><span class="sxs-lookup"><span data-stu-id="2476d-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which characters will be written.</span></span>

<span data-ttu-id="2476d-118">*lpNumberOfCharsWritten* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="2476d-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="2476d-119">Pointeur vers une variable qui reçoit le nombre de caractères réellement écrits.</span><span class="sxs-lookup"><span data-stu-id="2476d-119">A pointer to a variable that receives the number of characters actually written.</span></span>

## <a name="return-value"></a><span data-ttu-id="2476d-120">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="2476d-120">Return value</span></span>

<span data-ttu-id="2476d-121">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="2476d-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="2476d-122">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="2476d-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="2476d-123">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="2476d-123">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="2476d-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="2476d-124">Remarks</span></span>

<span data-ttu-id="2476d-125">Si le nombre de caractères à écrire dans s’étend au-delà de la fin de la ligne spécifiée dans la mémoire tampon d’écran de la console, les caractères sont écrits sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="2476d-125">If the number of characters to be written to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="2476d-126">Si le nombre de caractères à écrire dans s’étend au-delà de la fin de la mémoire tampon d’écran de la console, les caractères sont écrits jusqu’à la fin de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="2476d-126">If the number of characters to be written to extends beyond the end of the console screen buffer, characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="2476d-127">Les valeurs d’attribut aux positions écrites dans ne sont pas modifiées.</span><span class="sxs-lookup"><span data-stu-id="2476d-127">The attribute values at the positions written to are not changed.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="2476d-128">Cette API possède un **[terminal virtuel](console-virtual-terminal-sequences.md)** équivalent dans les séquences de **[mise en forme du texte](console-virtual-terminal-sequences.md#text-formatting)** et de **[positionnement des curseurs](console-virtual-terminal-sequences.md#cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="2476d-128">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sequences.</span></span> <span data-ttu-id="2476d-129">Placez le curseur à l’emplacement à insérer, appliquez la mise en forme souhaitée, puis écrivez le texte à remplir.</span><span class="sxs-lookup"><span data-stu-id="2476d-129">Move the cursor to the location to insert, apply the formatting desired, and write out text to fill.</span></span> <span data-ttu-id="2476d-130">Il n’existe aucun équivalent pour émettre du texte dans une zone sans appliquer également la mise en forme des couleurs active.</span><span class="sxs-lookup"><span data-stu-id="2476d-130">There is no equivalent to emit text to an area without also applying the active color formatting.</span></span> <span data-ttu-id="2476d-131">Cette décision aligne intentionnellement la plateforme Windows avec d’autres systèmes d’exploitation, où l’application cliente individuelle est supposée se souvenir de son propre État dessiné pour une manipulation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="2476d-131">This decision intentionally aligns the Windows platform with other operating systems where the individual client application is expected to remember its own drawn state for further manipulation.</span></span>

## <a name="requirements"></a><span data-ttu-id="2476d-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2476d-132">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="2476d-133">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="2476d-133">Minimum supported client</span></span> | <span data-ttu-id="2476d-134">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="2476d-134">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="2476d-135">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="2476d-135">Minimum supported server</span></span> | <span data-ttu-id="2476d-136">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="2476d-136">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="2476d-137">En-tête</span><span class="sxs-lookup"><span data-stu-id="2476d-137">Header</span></span> | <span data-ttu-id="2476d-138">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2476d-138">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="2476d-139">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="2476d-139">Library</span></span> | <span data-ttu-id="2476d-140">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="2476d-140">Kernel32.lib</span></span> |
| <span data-ttu-id="2476d-141">DLL</span><span class="sxs-lookup"><span data-stu-id="2476d-141">DLL</span></span> | <span data-ttu-id="2476d-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2476d-142">Kernel32.dll</span></span> |
| <span data-ttu-id="2476d-143">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="2476d-143">Unicode and ANSI names</span></span> | <span data-ttu-id="2476d-144">**WriteConsoleOutputCharacterW** (Unicode) et **WriteConsoleOutputCharacterA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="2476d-144">**WriteConsoleOutputCharacterW** (Unicode) and **WriteConsoleOutputCharacterA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="2476d-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2476d-145">See also</span></span>

[<span data-ttu-id="2476d-146">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="2476d-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2476d-147">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="2476d-147">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="2476d-148">Fonctions de sortie de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="2476d-148">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="2476d-149">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="2476d-149">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="2476d-150">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="2476d-150">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="2476d-151">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="2476d-151">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="2476d-152">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="2476d-152">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="2476d-153">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="2476d-153">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="2476d-154">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="2476d-154">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="2476d-155">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="2476d-155">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)