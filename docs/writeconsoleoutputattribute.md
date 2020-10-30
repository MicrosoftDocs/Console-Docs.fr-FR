---
title: WriteConsoleOutputAttribute fonction)
description: Copie un certain nombre d’attributs de caractères dans des cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
ms.openlocfilehash: 04c7799cd98479d3b776b1933994b60f5ed9fc9f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039277"
---
# <a name="writeconsoleoutputattribute-function"></a><span data-ttu-id="ff70b-104">WriteConsoleOutputAttribute fonction)</span><span class="sxs-lookup"><span data-stu-id="ff70b-104">WriteConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="ff70b-105">Copie un certain nombre d’attributs de caractères dans des cellules consécutives d’une mémoire tampon d’écran de la console, en commençant à un emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="ff70b-105">Copies a number of character attributes to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="ff70b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff70b-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="ff70b-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ff70b-107">Parameters</span></span>

<span data-ttu-id="ff70b-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="ff70b-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="ff70b-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="ff70b-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="ff70b-110">Le descripteur doit avoir le droit d’accès en **\_ écriture générique** .</span><span class="sxs-lookup"><span data-stu-id="ff70b-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="ff70b-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="ff70b-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="ff70b-112">*lpAttribute* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="ff70b-112">*lpAttribute* \[in\]</span></span>  
<span data-ttu-id="ff70b-113">Attributs à utiliser lors de l’écriture dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="ff70b-113">The attributes to be used when writing to the console screen buffer.</span></span> <span data-ttu-id="ff70b-114">Pour plus d’informations, consultez [attributs de caractères](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="ff70b-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="ff70b-115">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="ff70b-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="ff70b-116">Nombre de cellules de caractères de la mémoire tampon d’écran vers lesquelles les attributs seront copiés.</span><span class="sxs-lookup"><span data-stu-id="ff70b-116">The number of screen buffer character cells to which the attributes will be copied.</span></span>

<span data-ttu-id="ff70b-117">*dwWriteCoord* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="ff70b-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="ff70b-118">Structure de [**repère**](coord-str.md) qui spécifie les coordonnées de caractères de la première cellule dans la mémoire tampon d’écran de la console dans laquelle les attributs seront écrits.</span><span class="sxs-lookup"><span data-stu-id="ff70b-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which the attributes will be written.</span></span>

<span data-ttu-id="ff70b-119">*lpNumberOfAttrsWritten* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="ff70b-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="ff70b-120">Pointeur vers une variable qui reçoit le nombre d’attributs réellement écrits dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="ff70b-120">A pointer to a variable that receives the number of attributes actually written to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="ff70b-121">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="ff70b-121">Return value</span></span>

<span data-ttu-id="ff70b-122">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="ff70b-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ff70b-123">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="ff70b-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ff70b-124">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="ff70b-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="ff70b-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="ff70b-125">Remarks</span></span>

<span data-ttu-id="ff70b-126">Si le nombre d’attributs à écrire dans s’étend au-delà de la fin de la ligne spécifiée dans la mémoire tampon d’écran de la console, les attributs sont écrits sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="ff70b-126">If the number of attributes to be written to extends beyond the end of the specified row in the console screen buffer, attributes are written to the next row.</span></span> <span data-ttu-id="ff70b-127">Si le nombre d’attributs à écrire dans s’étend au-delà de la fin de la mémoire tampon d’écran de la console, les attributs sont écrits jusqu’à la fin de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="ff70b-127">If the number of attributes to be written to extends beyond the end of the console screen buffer, the attributes are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="ff70b-128">Les valeurs de caractère aux positions écrites dans ne sont pas modifiées.</span><span class="sxs-lookup"><span data-stu-id="ff70b-128">The character values at the positions written to are not changed.</span></span>

> [!TIP]
> <span data-ttu-id="ff70b-129">Cette API possède un **[terminal virtuel](console-virtual-terminal-sequences.md)** équivalent dans les séquences de **[mise en forme du texte](console-virtual-terminal-sequences.md#text-formatting)** et de **[positionnement des curseurs](console-virtual-terminal-sequences.md#cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="ff70b-129">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sequences.</span></span> <span data-ttu-id="ff70b-130">Placez le curseur à l’emplacement à insérer, appliquez la mise en forme souhaitée, puis écrivez le texte à remplir.</span><span class="sxs-lookup"><span data-stu-id="ff70b-130">Move the cursor to the location to insert, apply the formatting desired, and write out text to fill.</span></span> <span data-ttu-id="ff70b-131">Il n’existe aucun équivalent pour appliquer une couleur à une zone sans également émettre de texte.</span><span class="sxs-lookup"><span data-stu-id="ff70b-131">There is no equivalent to apply color to an area without also emitting text.</span></span> <span data-ttu-id="ff70b-132">Cette décision aligne intentionnellement la plateforme Windows avec d’autres systèmes d’exploitation, où l’application cliente individuelle est supposée se souvenir de son propre État dessiné pour une manipulation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="ff70b-132">This decision intentionally aligns the Windows platform with other operating systems where the individual client application is expected to remember its own drawn state for further manipulation.</span></span>

## <a name="requirements"></a><span data-ttu-id="ff70b-133">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ff70b-133">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ff70b-134">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ff70b-134">Minimum supported client</span></span> | <span data-ttu-id="ff70b-135">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ff70b-135">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="ff70b-136">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ff70b-136">Minimum supported server</span></span> | <span data-ttu-id="ff70b-137">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ff70b-137">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="ff70b-138">En-tête</span><span class="sxs-lookup"><span data-stu-id="ff70b-138">Header</span></span> | <span data-ttu-id="ff70b-139">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ff70b-139">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ff70b-140">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="ff70b-140">Library</span></span> | <span data-ttu-id="ff70b-141">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ff70b-141">Kernel32.lib</span></span> |
| <span data-ttu-id="ff70b-142">DLL</span><span class="sxs-lookup"><span data-stu-id="ff70b-142">DLL</span></span> | <span data-ttu-id="ff70b-143">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ff70b-143">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="ff70b-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff70b-144">See also</span></span>

[<span data-ttu-id="ff70b-145">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="ff70b-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ff70b-146">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="ff70b-146">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="ff70b-147">Fonctions de sortie de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="ff70b-147">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="ff70b-148">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="ff70b-148">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="ff70b-149">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="ff70b-149">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="ff70b-150">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="ff70b-150">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="ff70b-151">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="ff70b-151">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="ff70b-152">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="ff70b-152">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
