---
title: FillConsoleOutputAttribute fonction)
description: Définit les attributs de caractère pour un nombre spécifié de cellules de caractères, en commençant aux coordonnées spécifiées dans une mémoire tampon d’écran.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
ms.openlocfilehash: 40eb97e43e406d68ff625db110998ebf69eb26f7
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039067"
---
# <a name="fillconsoleoutputattribute-function"></a><span data-ttu-id="344c3-104">FillConsoleOutputAttribute fonction)</span><span class="sxs-lookup"><span data-stu-id="344c3-104">FillConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="344c3-105">Définit les attributs de caractère pour un nombre spécifié de cellules de caractères, en commençant aux coordonnées spécifiées dans une mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="344c3-105">Sets the character attributes for a specified number of character cells, beginning at the specified coordinates in a screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="344c3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="344c3-106">Syntax</span></span>

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="344c3-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="344c3-107">Parameters</span></span>

<span data-ttu-id="344c3-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="344c3-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="344c3-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="344c3-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="344c3-110">Le descripteur doit avoir le droit d’accès en **\_ écriture générique** .</span><span class="sxs-lookup"><span data-stu-id="344c3-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="344c3-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="344c3-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="344c3-112">*wAttribute* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="344c3-112">*wAttribute* \[in\]</span></span>  
<span data-ttu-id="344c3-113">Attributs à utiliser lors de l’écriture dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="344c3-113">The attributes to use when writing to the console screen buffer.</span></span> <span data-ttu-id="344c3-114">Pour plus d’informations, consultez [attributs de caractères](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="344c3-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="344c3-115">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="344c3-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="344c3-116">Nombre de cellules de caractères à définir avec les attributs de couleur spécifiés.</span><span class="sxs-lookup"><span data-stu-id="344c3-116">The number of character cells to be set to the specified color attributes.</span></span>

<span data-ttu-id="344c3-117">*dwWriteCoord* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="344c3-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="344c3-118">Structure de [**repère**](coord-str.md) qui spécifie les coordonnées de caractère de la première cellule dont les attributs doivent être définis.</span><span class="sxs-lookup"><span data-stu-id="344c3-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell whose attributes are to be set.</span></span>

<span data-ttu-id="344c3-119">*lpNumberOfAttrsWritten* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="344c3-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="344c3-120">Pointeur vers une variable qui reçoit le nombre de cellules de caractères dont les attributs ont été réellement définis.</span><span class="sxs-lookup"><span data-stu-id="344c3-120">A pointer to a variable that receives the number of character cells whose attributes were actually set.</span></span>

## <a name="return-value"></a><span data-ttu-id="344c3-121">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="344c3-121">Return value</span></span>

<span data-ttu-id="344c3-122">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="344c3-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="344c3-123">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="344c3-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="344c3-124">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="344c3-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="344c3-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="344c3-125">Remarks</span></span>

<span data-ttu-id="344c3-126">Si le nombre de cellules de caractères dont les attributs doivent être définis s’étend au-delà de la fin de la ligne spécifiée dans la mémoire tampon d’écran de la console, les cellules de la ligne suivante sont définies.</span><span class="sxs-lookup"><span data-stu-id="344c3-126">If the number of character cells whose attributes are to be set extends beyond the end of the specified row in the console screen buffer, the cells of the next row are set.</span></span> <span data-ttu-id="344c3-127">Si le nombre de cellules à écrire dépasse la fin de la mémoire tampon d’écran de la console, les cellules sont écrites jusqu’à la fin de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="344c3-127">If the number of cells to write to extends beyond the end of the console screen buffer, the cells are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="344c3-128">Les valeurs de caractère aux positions écrites dans ne sont pas modifiées.</span><span class="sxs-lookup"><span data-stu-id="344c3-128">The character values at the positions written to are not changed.</span></span>

> [!TIP]
> <span data-ttu-id="344c3-129">Cette API n’est pas recommandée et n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** spécifique.</span><span class="sxs-lookup"><span data-stu-id="344c3-129">This API is not recommended and does not have a specific **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="344c3-130">Le remplissage de la région en dehors de la fenêtre affichable n’est pas pris en charge et est réservé à l’espace d’historique du terminal.</span><span class="sxs-lookup"><span data-stu-id="344c3-130">Filling the region outside the viewable window is not supported and is reserved for the terminal's history space.</span></span> <span data-ttu-id="344c3-131">Le remplissage d’une zone visible avec un nouveau texte ou une nouvelle couleur est effectué via **[le déplacement du curseur](console-virtual-terminal-sequences.md#cursor-positioning)** , la **[définition des nouveaux attributs](console-virtual-terminal-sequences.md#text-formatting)** , puis l’écriture du texte souhaité pour cette région, en répétant les caractères si nécessaire pour la longueur de la séquence de remplissage.</span><span class="sxs-lookup"><span data-stu-id="344c3-131">Filling a visible region with new text or color is performed through **[moving the cursor](console-virtual-terminal-sequences.md#cursor-positioning)** , **[setting the new attributes](console-virtual-terminal-sequences.md#text-formatting)** , then writing the desired text for that region, repeating characters if necessary for the length of the fill run.</span></span> <span data-ttu-id="344c3-132">Des mouvements de curseur supplémentaires peuvent être nécessaires, suivis par l’écriture du texte souhaité pour remplir une zone rectangulaire.</span><span class="sxs-lookup"><span data-stu-id="344c3-132">Additional cursor movement may be required followed by writing the desired text to fill a rectangular region.</span></span> <span data-ttu-id="344c3-133">L’application cliente doit conserver sa propre mémoire sur l’écran et ne peut pas interroger l’État distant.</span><span class="sxs-lookup"><span data-stu-id="344c3-133">The client application is expected to keep its own memory of what is on the screen and is not able to query the remote state.</span></span> <span data-ttu-id="344c3-134">Vous trouverez plus d’informations dans la documentation de la **[console classique et du terminal virtuel](classic-vs-vt.md)** .</span><span class="sxs-lookup"><span data-stu-id="344c3-134">More information can be found in **[classic console versus virtual terminal](classic-vs-vt.md)** documentation.</span></span>

## <a name="requirements"></a><span data-ttu-id="344c3-135">Spécifications</span><span class="sxs-lookup"><span data-stu-id="344c3-135">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="344c3-136">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="344c3-136">Minimum supported client</span></span> | <span data-ttu-id="344c3-137">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="344c3-137">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="344c3-138">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="344c3-138">Minimum supported server</span></span> | <span data-ttu-id="344c3-139">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="344c3-139">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="344c3-140">En-tête</span><span class="sxs-lookup"><span data-stu-id="344c3-140">Header</span></span> | <span data-ttu-id="344c3-141">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="344c3-141">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="344c3-142">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="344c3-142">Library</span></span> | <span data-ttu-id="344c3-143">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="344c3-143">Kernel32.lib</span></span> |
| <span data-ttu-id="344c3-144">DLL</span><span class="sxs-lookup"><span data-stu-id="344c3-144">DLL</span></span> | <span data-ttu-id="344c3-145">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="344c3-145">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="344c3-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="344c3-146">See also</span></span>

[<span data-ttu-id="344c3-147">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="344c3-147">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="344c3-148">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="344c3-148">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="344c3-149">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="344c3-149">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="344c3-150">Fonctions de sortie de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="344c3-150">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="344c3-151">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="344c3-151">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

[<span data-ttu-id="344c3-152">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="344c3-152">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)
