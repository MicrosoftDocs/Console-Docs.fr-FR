---
title: FillConsoleOutputCharacter fonction)
description: Écrit un caractère dans la mémoire tampon d’écran de la console un nombre spécifié de fois, en commençant aux coordonnées spécifiées.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
ms.openlocfilehash: 8860a1feab39bc83f28a867fa9acc491cc00e4b7
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038187"
---
# <a name="fillconsoleoutputcharacter-function"></a><span data-ttu-id="08d12-104">FillConsoleOutputCharacter fonction)</span><span class="sxs-lookup"><span data-stu-id="08d12-104">FillConsoleOutputCharacter function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="08d12-105">Écrit un caractère dans la mémoire tampon d’écran de la console un nombre spécifié de fois, en commençant aux coordonnées spécifiées.</span><span class="sxs-lookup"><span data-stu-id="08d12-105">Writes a character to the console screen buffer a specified number of times, beginning at the specified coordinates.</span></span>

## <a name="syntax"></a><span data-ttu-id="08d12-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08d12-106">Syntax</span></span>

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="08d12-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="08d12-107">Parameters</span></span>

<span data-ttu-id="08d12-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="08d12-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="08d12-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="08d12-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="08d12-110">Le descripteur doit avoir le droit d’accès en **\_ écriture générique** .</span><span class="sxs-lookup"><span data-stu-id="08d12-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="08d12-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="08d12-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="08d12-112">*cCharacter* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="08d12-112">*cCharacter* \[in\]</span></span>  
<span data-ttu-id="08d12-113">Caractère à écrire dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="08d12-113">The character to be written to the console screen buffer.</span></span>

<span data-ttu-id="08d12-114">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="08d12-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="08d12-115">Nombre de cellules de caractères dans lesquelles le caractère doit être écrit.</span><span class="sxs-lookup"><span data-stu-id="08d12-115">The number of character cells to which the character should be written.</span></span>

<span data-ttu-id="08d12-116">*dwWriteCoord* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="08d12-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="08d12-117">Structure de [**repère**](coord-str.md) qui spécifie les coordonnées de caractère de la première cellule dans laquelle le caractère doit être écrit.</span><span class="sxs-lookup"><span data-stu-id="08d12-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell to which the character is to be written.</span></span>

<span data-ttu-id="08d12-118">*lpNumberOfCharsWritten* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="08d12-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="08d12-119">Pointeur vers une variable qui reçoit le nombre de caractères réellement écrits dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="08d12-119">A pointer to a variable that receives the number of characters actually written to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="08d12-120">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="08d12-120">Return value</span></span>

<span data-ttu-id="08d12-121">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="08d12-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="08d12-122">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="08d12-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="08d12-123">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="08d12-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="08d12-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="08d12-124">Remarks</span></span>

<span data-ttu-id="08d12-125">Si le nombre de caractères à écrire dépasse la fin de la ligne spécifiée dans la mémoire tampon d’écran de la console, les caractères sont écrits sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="08d12-125">If the number of characters to write to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="08d12-126">Si le nombre de caractères à écrire dépasse la fin de la mémoire tampon d’écran de la console, les caractères sont écrits jusqu’à la fin de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="08d12-126">If the number of characters to write to extends beyond the end of the console screen buffer, the characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="08d12-127">Les valeurs d’attribut aux positions écrites ne sont pas modifiées.</span><span class="sxs-lookup"><span data-stu-id="08d12-127">The attribute values at the positions written are not changed.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="08d12-128">Cette API n’est pas recommandée et n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** spécifique.</span><span class="sxs-lookup"><span data-stu-id="08d12-128">This API is not recommended and does not have a specific **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="08d12-129">Le remplissage de la région en dehors de la fenêtre affichable n’est pas pris en charge et est réservé à l’espace d’historique du terminal.</span><span class="sxs-lookup"><span data-stu-id="08d12-129">Filling the region outside the viewable window is not supported and is reserved for the terminal's history space.</span></span> <span data-ttu-id="08d12-130">Le remplissage d’une zone visible avec un nouveau texte ou une nouvelle couleur est effectué via **[le déplacement du curseur](console-virtual-terminal-sequences.md#cursor-positioning)** , la **[définition des nouveaux attributs](console-virtual-terminal-sequences.md#text-formatting)** , puis l’écriture du texte souhaité pour cette région, en répétant les caractères si nécessaire pour la longueur de la séquence de remplissage.</span><span class="sxs-lookup"><span data-stu-id="08d12-130">Filling a visible region with new text or color is performed through **[moving the cursor](console-virtual-terminal-sequences.md#cursor-positioning)** , **[setting the new attributes](console-virtual-terminal-sequences.md#text-formatting)** , then writing the desired text for that region, repeating characters if necessary for the length of the fill run.</span></span> <span data-ttu-id="08d12-131">Des mouvements de curseur supplémentaires peuvent être nécessaires, suivis par l’écriture du texte souhaité pour remplir une zone rectangulaire.</span><span class="sxs-lookup"><span data-stu-id="08d12-131">Additional cursor movement may be required followed by writing the desired text to fill a rectangular region.</span></span> <span data-ttu-id="08d12-132">L’application cliente doit conserver sa propre mémoire sur l’écran et ne peut pas interroger l’État distant.</span><span class="sxs-lookup"><span data-stu-id="08d12-132">The client application is expected to keep its own memory of what is on the screen and is not able to query the remote state.</span></span> <span data-ttu-id="08d12-133">Vous trouverez plus d’informations dans la documentation de la **[console classique et du terminal virtuel](classic-vs-vt.md)** .</span><span class="sxs-lookup"><span data-stu-id="08d12-133">More information can be found in **[classic console versus virtual terminal](classic-vs-vt.md)** documentation.</span></span>

## <a name="requirements"></a><span data-ttu-id="08d12-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="08d12-134">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="08d12-135">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="08d12-135">Minimum supported client</span></span> | <span data-ttu-id="08d12-136">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="08d12-136">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="08d12-137">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="08d12-137">Minimum supported server</span></span> | <span data-ttu-id="08d12-138">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="08d12-138">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="08d12-139">En-tête</span><span class="sxs-lookup"><span data-stu-id="08d12-139">Header</span></span> | <span data-ttu-id="08d12-140">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="08d12-140">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="08d12-141">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="08d12-141">Library</span></span> | <span data-ttu-id="08d12-142">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="08d12-142">Kernel32.lib</span></span> |
| <span data-ttu-id="08d12-143">DLL</span><span class="sxs-lookup"><span data-stu-id="08d12-143">DLL</span></span> | <span data-ttu-id="08d12-144">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="08d12-144">Kernel32.dll</span></span> |
| <span data-ttu-id="08d12-145">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="08d12-145">Unicode and ANSI names</span></span> | <span data-ttu-id="08d12-146">**FillConsoleOutputCharacterW** (Unicode) et **FillConsoleOutputCharacterA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="08d12-146">**FillConsoleOutputCharacterW** (Unicode) and **FillConsoleOutputCharacterA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="08d12-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08d12-147">See also</span></span>

[<span data-ttu-id="08d12-148">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="08d12-148">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="08d12-149">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="08d12-149">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="08d12-150">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="08d12-150">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="08d12-151">Fonctions de sortie de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="08d12-151">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="08d12-152">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="08d12-152">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="08d12-153">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="08d12-153">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="08d12-154">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="08d12-154">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
