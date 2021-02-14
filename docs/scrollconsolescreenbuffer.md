---
title: ScrollConsoleScreenBuffer fonction)
description: Consultez les informations de référence sur la fonction ScrollConsoleScreenBuffer, qui déplace un bloc de données dans une mémoire tampon d’écran.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/ScrollConsoleScreenBuffer
- wincon/ScrollConsoleScreenBuffer
- ScrollConsoleScreenBuffer
- consoleapi2/ScrollConsoleScreenBufferA
- wincon/ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferA
- consoleapi2/ScrollConsoleScreenBufferW
- wincon/ScrollConsoleScreenBufferW
- ScrollConsoleScreenBufferW
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d78bf4c9-2314-466c-b617-619259c824b5
topic_type:
- apiref
api_name:
- ScrollConsoleScreenBuffer
- ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 1bf009a91063c12ad14604349d68ca0de1d8eaa1
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358669"
---
# <a name="scrollconsolescreenbuffer-function"></a><span data-ttu-id="f3955-104">ScrollConsoleScreenBuffer fonction)</span><span class="sxs-lookup"><span data-stu-id="f3955-104">ScrollConsoleScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="f3955-105">Déplace un bloc de données dans une mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="f3955-105">Moves a block of data in a screen buffer.</span></span> <span data-ttu-id="f3955-106">Les effets du déplacement peuvent être limités en spécifiant un rectangle de découpage, le contenu de la mémoire tampon d’écran de la console en dehors du rectangle de découpage n’est donc pas modifié.</span><span class="sxs-lookup"><span data-stu-id="f3955-106">The effects of the move can be limited by specifying a clipping rectangle, so the contents of the console screen buffer outside the clipping rectangle are unchanged.</span></span>

## <a name="syntax"></a><span data-ttu-id="f3955-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3955-107">Syntax</span></span>

```C
BOOL WINAPI ScrollConsoleScreenBuffer(
  _In_           HANDLE     hConsoleOutput,
  _In_     const SMALL_RECT *lpScrollRectangle,
  _In_opt_ const SMALL_RECT *lpClipRectangle,
  _In_           COORD      dwDestinationOrigin,
  _In_     const CHAR_INFO  *lpFill
);
```

## <a name="parameters"></a><span data-ttu-id="f3955-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f3955-108">Parameters</span></span>

<span data-ttu-id="f3955-109">*hConsoleOutput* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="f3955-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="f3955-110">Handle vers la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="f3955-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="f3955-111">Le handle doit avoir le droit d’accès **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="f3955-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="f3955-112">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="f3955-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="f3955-113">*lpScrollRectangle* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="f3955-113">*lpScrollRectangle* \[in\]</span></span>  
<span data-ttu-id="f3955-114">Pointeur vers une [**petite structure \_ Rect**](small-rect-str.md) dont les membres spécifient les coordonnées supérieure gauche et inférieure droite du rectangle de la mémoire tampon d’écran de la console à déplacer.</span><span class="sxs-lookup"><span data-stu-id="f3955-114">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure whose members specify the upper-left and lower-right coordinates of the console screen buffer rectangle to be moved.</span></span>

<span data-ttu-id="f3955-115">*lpClipRectangle* \[ dans, facultatif\]</span><span class="sxs-lookup"><span data-stu-id="f3955-115">*lpClipRectangle* \[in, optional\]</span></span>  
<span data-ttu-id="f3955-116">Pointeur vers une [**petite structure \_ Rect**](small-rect-str.md) dont les membres spécifient les coordonnées supérieure gauche et inférieure droite du rectangle de la mémoire tampon d’écran de la console qui est affectée par le défilement.</span><span class="sxs-lookup"><span data-stu-id="f3955-116">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure whose members specify the upper-left and lower-right coordinates of the console screen buffer rectangle that is affected by the scrolling.</span></span> <span data-ttu-id="f3955-117">Ce pointeur peut avoir la **valeur null**.</span><span class="sxs-lookup"><span data-stu-id="f3955-117">This pointer can be **NULL**.</span></span>

<span data-ttu-id="f3955-118">*dwDestinationOrigin* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="f3955-118">*dwDestinationOrigin* \[in\]</span></span>  
<span data-ttu-id="f3955-119">Structure de [**repère**](coord-str.md) qui spécifie l’angle supérieur gauche du nouvel emplacement du contenu *lpScrollRectangle* , en caractères.</span><span class="sxs-lookup"><span data-stu-id="f3955-119">A [**COORD**](coord-str.md) structure that specifies the upper-left corner of the new location of the *lpScrollRectangle* contents, in characters.</span></span>

<span data-ttu-id="f3955-120">*lpFill* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="f3955-120">*lpFill* \[in\]</span></span>  
<span data-ttu-id="f3955-121">Pointeur vers une structure [**d' \_ informations de type char**](char-info-str.md) qui spécifie les attributs de caractère et de couleur à utiliser pour remplir les cellules au sein de l’intersection de *lpScrollRectangle* et de *lpClipRectangle* qui ont été laissés vides suite au déplacement.</span><span class="sxs-lookup"><span data-stu-id="f3955-121">A pointer to a [**CHAR\_INFO**](char-info-str.md) structure that specifies the character and color attributes to be used in filling the cells within the intersection of *lpScrollRectangle* and *lpClipRectangle* that were left empty as a result of the move.</span></span>

## <a name="return-value"></a><span data-ttu-id="f3955-122">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="f3955-122">Return value</span></span>

<span data-ttu-id="f3955-123">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="f3955-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="f3955-124">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="f3955-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="f3955-125">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="f3955-125">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="f3955-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="f3955-126">Remarks</span></span>

<span data-ttu-id="f3955-127">**ScrollConsoleScreenBuffer** copie le contenu d’une zone rectangulaire d’une mémoire tampon d’écran, spécifiée par le paramètre *lpScrollRectangle* , dans une autre zone de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="f3955-127">**ScrollConsoleScreenBuffer** copies the contents of a rectangular region of a screen buffer, specified by the *lpScrollRectangle* parameter, to another area of the console screen buffer.</span></span> <span data-ttu-id="f3955-128">Le rectangle cible a les mêmes dimensions que le rectangle *lpScrollRectangle* avec son coin supérieur gauche aux coordonnées spécifiées par le paramètre *dwDestinationOrigin* .</span><span class="sxs-lookup"><span data-stu-id="f3955-128">The target rectangle has the same dimensions as the *lpScrollRectangle* rectangle with its upper-left corner at the coordinates specified by the *dwDestinationOrigin* parameter.</span></span> <span data-ttu-id="f3955-129">Les éléments de *lpScrollRectangle* qui ne se chevauchent pas avec le rectangle cible sont renseignés avec les attributs de caractère et de couleur spécifiés par le paramètre *lpFill* .</span><span class="sxs-lookup"><span data-stu-id="f3955-129">Those parts of *lpScrollRectangle* that do not overlap with the target rectangle are filled in with the character and color attributes specified by the *lpFill* parameter.</span></span>

<span data-ttu-id="f3955-130">Le rectangle de découpage s’applique aux modifications apportées à la fois dans le rectangle *lpScrollRectangle* et dans le rectangle cible.</span><span class="sxs-lookup"><span data-stu-id="f3955-130">The clipping rectangle applies to changes made in both the *lpScrollRectangle* rectangle and the target rectangle.</span></span> <span data-ttu-id="f3955-131">Par exemple, si le rectangle de découpage n’inclut pas une région qui aurait été remplie par le contenu de *lpFill*, le contenu d’origine de la région reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="f3955-131">For example, if the clipping rectangle does not include a region that would have been filled by the contents of *lpFill*, the original contents of the region are left unchanged.</span></span>

<span data-ttu-id="f3955-132">Si les régions de défilement ou cibles s’étendent au-delà des dimensions de la mémoire tampon d’écran de la console, elles sont découpées.</span><span class="sxs-lookup"><span data-stu-id="f3955-132">If the scroll or target regions extend beyond the dimensions of the console screen buffer, they are clipped.</span></span> <span data-ttu-id="f3955-133">Par exemple, si *lpScrollRectangle* est la région contenue par (0, 0) et (19, 19) et *dwDestinationOrigin* est (10, 15), le rectangle cible est la région contenue par (10, 15) et (29, 34).</span><span class="sxs-lookup"><span data-stu-id="f3955-133">For example, if *lpScrollRectangle* is the region contained by (0,0) and (19,19) and *dwDestinationOrigin* is (10,15), the target rectangle is the region contained by (10,15) and (29,34).</span></span> <span data-ttu-id="f3955-134">Toutefois, si la mémoire tampon de l’écran de la console est de 50 caractères de large à 30 caractères de haut, le rectangle cible est coupé à (10, 15) et (29, 29).</span><span class="sxs-lookup"><span data-stu-id="f3955-134">However, if the console screen buffer is 50 characters wide and 30 characters high, the target rectangle is clipped to (10,15) and (29,29).</span></span> <span data-ttu-id="f3955-135">Les modifications apportées à la mémoire tampon d’écran de la console sont également découpées selon *lpClipRectangle*, si le paramètre spécifie une [**petite structure \_ Rect**](small-rect-str.md) .</span><span class="sxs-lookup"><span data-stu-id="f3955-135">Changes to the console screen buffer are also clipped according to *lpClipRectangle*, if the parameter specifies a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="f3955-136">Si le rectangle de découpage est spécifié sous la forme (0, 0) et (49, 19), seules les modifications qui se produisent dans cette région de la mémoire tampon de l’écran de la console sont effectuées.</span><span class="sxs-lookup"><span data-stu-id="f3955-136">If the clipping rectangle is specified as (0,0) and (49,19), only the changes that occur in that region of the console screen buffer are made.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="f3955-137">Cette API n’est pas recommandée et n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="f3955-137">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="f3955-138">L’utilisation de peut être approximative avec les **[marges de défilement](console-virtual-terminal-sequences.md#scrolling-margins)** pour corriger une zone de l’écran, le **[positionnement du curseur](console-virtual-terminal-sequences.md#cursor-positioning)** pour définir la position active en dehors de la région et les nouvelles lignes pour forcer le déplacement du texte.</span><span class="sxs-lookup"><span data-stu-id="f3955-138">Use can be approximated with **[scroll margins](console-virtual-terminal-sequences.md#scrolling-margins)** to fix an area of the screen, **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** to set the active position outside the region, and newlines to force text to move.</span></span> <span data-ttu-id="f3955-139">Vous pouvez remplir l’espace restant en déplaçant le curseur, en **[définissant des attributs graphiques](console-virtual-terminal-sequences.md#text-formatting)** et en écrivant du texte normal.</span><span class="sxs-lookup"><span data-stu-id="f3955-139">The remaining space can be filled by moving the cursor, **[setting graphical attributes](console-virtual-terminal-sequences.md#text-formatting)**, and writing normal text.</span></span>

## <a name="examples"></a><span data-ttu-id="f3955-140">Exemples</span><span class="sxs-lookup"><span data-stu-id="f3955-140">Examples</span></span>

<span data-ttu-id="f3955-141">Pour obtenir un exemple, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="f3955-141">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="f3955-142">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f3955-142">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="f3955-143">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="f3955-143">Minimum supported client</span></span> | <span data-ttu-id="f3955-144">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="f3955-144">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="f3955-145">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="f3955-145">Minimum supported server</span></span> | <span data-ttu-id="f3955-146">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="f3955-146">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="f3955-147">En-tête</span><span class="sxs-lookup"><span data-stu-id="f3955-147">Header</span></span> | <span data-ttu-id="f3955-148">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f3955-148">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="f3955-149">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="f3955-149">Library</span></span> | <span data-ttu-id="f3955-150">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="f3955-150">Kernel32.lib</span></span> |
| <span data-ttu-id="f3955-151">DLL</span><span class="sxs-lookup"><span data-stu-id="f3955-151">DLL</span></span> | <span data-ttu-id="f3955-152">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f3955-152">Kernel32.dll</span></span> |
| <span data-ttu-id="f3955-153">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="f3955-153">Unicode and ANSI names</span></span> | <span data-ttu-id="f3955-154">**ScrollConsoleScreenBufferW** (Unicode) et **ScrollConsoleScreenBufferA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="f3955-154">**ScrollConsoleScreenBufferW** (Unicode) and **ScrollConsoleScreenBufferA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="f3955-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3955-155">See also</span></span>

[<span data-ttu-id="f3955-156">**\_infos char**</span><span class="sxs-lookup"><span data-stu-id="f3955-156">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="f3955-157">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="f3955-157">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f3955-158">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="f3955-158">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="f3955-159">Défilement de la mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="f3955-159">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

[<span data-ttu-id="f3955-160">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="f3955-160">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="f3955-161">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="f3955-161">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="f3955-162">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="f3955-162">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="f3955-163">**PETIT \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="f3955-163">**SMALL\_RECT**</span></span>](small-rect-str.md)