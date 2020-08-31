---
title: ScrollConsoleScreenBuffer fonction)
description: Consultez les informations de référence sur la fonction ScrollConsoleScreenBuffer, qui déplace un bloc de données dans une mémoire tampon d’écran.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
ms.openlocfilehash: f0dd67ecc28907913e10efa8c06a544656d08dc6
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059437"
---
# <a name="scrollconsolescreenbuffer-function"></a><span data-ttu-id="bd0ee-104">ScrollConsoleScreenBuffer fonction)</span><span class="sxs-lookup"><span data-stu-id="bd0ee-104">ScrollConsoleScreenBuffer function</span></span>


<span data-ttu-id="bd0ee-105">Déplace un bloc de données dans une mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-105">Moves a block of data in a screen buffer.</span></span> <span data-ttu-id="bd0ee-106">Les effets du déplacement peuvent être limités en spécifiant un rectangle de découpage, le contenu de la mémoire tampon d’écran de la console en dehors du rectangle de découpage n’est donc pas modifié.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-106">The effects of the move can be limited by specifying a clipping rectangle, so the contents of the console screen buffer outside the clipping rectangle are unchanged.</span></span>

<a name="syntax"></a><span data-ttu-id="bd0ee-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd0ee-107">Syntax</span></span>
------

```C
BOOL WINAPI ScrollConsoleScreenBuffer(
  _In_           HANDLE     hConsoleOutput,
  _In_     const SMALL_RECT *lpScrollRectangle,
  _In_opt_ const SMALL_RECT *lpClipRectangle,
  _In_           COORD      dwDestinationOrigin,
  _In_     const CHAR_INFO  *lpFill
);
```

<a name="parameters"></a><span data-ttu-id="bd0ee-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bd0ee-108">Parameters</span></span>
----------

<span data-ttu-id="bd0ee-109">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="bd0ee-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="bd0ee-110">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="bd0ee-111">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="bd0ee-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="bd0ee-112">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="bd0ee-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="bd0ee-113">*lpScrollRectangle* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="bd0ee-113">*lpScrollRectangle* \[in\]</span></span>  
<span data-ttu-id="bd0ee-114">Pointeur vers une [**petite structure \_ Rect**](small-rect-str.md) dont les membres spécifient les coordonnées supérieure gauche et inférieure droite du rectangle de la mémoire tampon d’écran de la console à déplacer.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-114">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure whose members specify the upper-left and lower-right coordinates of the console screen buffer rectangle to be moved.</span></span>

<span data-ttu-id="bd0ee-115">*lpClipRectangle* \[ dans, facultatif\]</span><span class="sxs-lookup"><span data-stu-id="bd0ee-115">*lpClipRectangle* \[in, optional\]</span></span>  
<span data-ttu-id="bd0ee-116">Pointeur vers une [**petite structure \_ Rect**](small-rect-str.md) dont les membres spécifient les coordonnées supérieure gauche et inférieure droite du rectangle de la mémoire tampon d’écran de la console qui est affectée par le défilement.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-116">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure whose members specify the upper-left and lower-right coordinates of the console screen buffer rectangle that is affected by the scrolling.</span></span> <span data-ttu-id="bd0ee-117">Ce pointeur peut avoir la **valeur null**.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-117">This pointer can be **NULL**.</span></span>

<span data-ttu-id="bd0ee-118">*dwDestinationOrigin* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="bd0ee-118">*dwDestinationOrigin* \[in\]</span></span>  
<span data-ttu-id="bd0ee-119">Structure de [**repère**](coord-str.md) qui spécifie l’angle supérieur gauche du nouvel emplacement du contenu *lpScrollRectangle* , en caractères.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-119">A [**COORD**](coord-str.md) structure that specifies the upper-left corner of the new location of the *lpScrollRectangle* contents, in characters.</span></span>

<span data-ttu-id="bd0ee-120">*lpFill* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="bd0ee-120">*lpFill* \[in\]</span></span>  
<span data-ttu-id="bd0ee-121">Pointeur vers une structure [**d' \_ informations de type char**](char-info-str.md) qui spécifie les attributs de caractère et de couleur à utiliser pour remplir les cellules au sein de l’intersection de *lpScrollRectangle* et de *lpClipRectangle* qui ont été laissés vides suite au déplacement.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-121">A pointer to a [**CHAR\_INFO**](char-info-str.md) structure that specifies the character and color attributes to be used in filling the cells within the intersection of *lpScrollRectangle* and *lpClipRectangle* that were left empty as a result of the move.</span></span>

<a name="return-value"></a><span data-ttu-id="bd0ee-122">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="bd0ee-122">Return value</span></span>
------------

<span data-ttu-id="bd0ee-123">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="bd0ee-124">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="bd0ee-125">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="bd0ee-125">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="bd0ee-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="bd0ee-126">Remarks</span></span>
-------

<span data-ttu-id="bd0ee-127">**ScrollConsoleScreenBuffer** copie le contenu d’une zone rectangulaire d’une mémoire tampon d’écran, spécifiée par le paramètre *lpScrollRectangle* , dans une autre zone de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-127">**ScrollConsoleScreenBuffer** copies the contents of a rectangular region of a screen buffer, specified by the *lpScrollRectangle* parameter, to another area of the console screen buffer.</span></span> <span data-ttu-id="bd0ee-128">Le rectangle cible a les mêmes dimensions que le rectangle *lpScrollRectangle* avec son coin supérieur gauche aux coordonnées spécifiées par le paramètre *dwDestinationOrigin* .</span><span class="sxs-lookup"><span data-stu-id="bd0ee-128">The target rectangle has the same dimensions as the *lpScrollRectangle* rectangle with its upper-left corner at the coordinates specified by the *dwDestinationOrigin* parameter.</span></span> <span data-ttu-id="bd0ee-129">Les éléments de *lpScrollRectangle* qui ne se chevauchent pas avec le rectangle cible sont renseignés avec les attributs de caractère et de couleur spécifiés par le paramètre *lpFill* .</span><span class="sxs-lookup"><span data-stu-id="bd0ee-129">Those parts of *lpScrollRectangle* that do not overlap with the target rectangle are filled in with the character and color attributes specified by the *lpFill* parameter.</span></span>

<span data-ttu-id="bd0ee-130">Le rectangle de découpage s’applique aux modifications apportées à la fois dans le rectangle *lpScrollRectangle* et dans le rectangle cible.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-130">The clipping rectangle applies to changes made in both the *lpScrollRectangle* rectangle and the target rectangle.</span></span> <span data-ttu-id="bd0ee-131">Par exemple, si le rectangle de découpage n’inclut pas une région qui aurait été remplie par le contenu de *lpFill*, le contenu d’origine de la région reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-131">For example, if the clipping rectangle does not include a region that would have been filled by the contents of *lpFill*, the original contents of the region are left unchanged.</span></span>

<span data-ttu-id="bd0ee-132">Si les régions de défilement ou cibles s’étendent au-delà des dimensions de la mémoire tampon d’écran de la console, elles sont découpées.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-132">If the scroll or target regions extend beyond the dimensions of the console screen buffer, they are clipped.</span></span> <span data-ttu-id="bd0ee-133">Par exemple, si *lpScrollRectangle* est la région contenue par (0, 0) et (19, 19) et *dwDestinationOrigin* est (10, 15), le rectangle cible est la région contenue par (10, 15) et (29, 34).</span><span class="sxs-lookup"><span data-stu-id="bd0ee-133">For example, if *lpScrollRectangle* is the region contained by (0,0) and (19,19) and *dwDestinationOrigin* is (10,15), the target rectangle is the region contained by (10,15) and (29,34).</span></span> <span data-ttu-id="bd0ee-134">Toutefois, si la mémoire tampon de l’écran de la console est de 50 caractères de large à 30 caractères de haut, le rectangle cible est coupé à (10, 15) et (29, 29).</span><span class="sxs-lookup"><span data-stu-id="bd0ee-134">However, if the console screen buffer is 50 characters wide and 30 characters high, the target rectangle is clipped to (10,15) and (29,29).</span></span> <span data-ttu-id="bd0ee-135">Les modifications apportées à la mémoire tampon d’écran de la console sont également découpées selon *lpClipRectangle*, si le paramètre spécifie une [**petite structure \_ Rect**](small-rect-str.md) .</span><span class="sxs-lookup"><span data-stu-id="bd0ee-135">Changes to the console screen buffer are also clipped according to *lpClipRectangle*, if the parameter specifies a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="bd0ee-136">Si le rectangle de découpage est spécifié sous la forme (0, 0) et (49, 19), seules les modifications qui se produisent dans cette région de la mémoire tampon de l’écran de la console sont effectuées.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-136">If the clipping rectangle is specified as (0,0) and (49,19), only the changes that occur in that region of the console screen buffer are made.</span></span>

<span data-ttu-id="bd0ee-137">Cette fonction utilise des caractères Unicode ou 8 bits à partir de la page de codes actuelle de la console.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-137">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="bd0ee-138">La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système.</span><span class="sxs-lookup"><span data-stu-id="bd0ee-138">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="bd0ee-139">Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="bd0ee-139">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="bd0ee-140">Exemples</span><span class="sxs-lookup"><span data-stu-id="bd0ee-140">Examples</span></span>
--------

<span data-ttu-id="bd0ee-141">Pour obtenir un exemple, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="bd0ee-141">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="bd0ee-142">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bd0ee-142">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="bd0ee-143">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="bd0ee-143">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="bd0ee-144">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="bd0ee-144">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bd0ee-145">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="bd0ee-145">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="bd0ee-146">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="bd0ee-146">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bd0ee-147">En-tête</span><span class="sxs-lookup"><span data-stu-id="bd0ee-147">Header</span></span></p></td>
<td><span data-ttu-id="bd0ee-148">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="bd0ee-148">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bd0ee-149">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="bd0ee-149">Library</span></span></p></td>
<td><span data-ttu-id="bd0ee-150">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="bd0ee-150">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bd0ee-151">DLL</span><span class="sxs-lookup"><span data-stu-id="bd0ee-151">DLL</span></span></p></td>
<td><span data-ttu-id="bd0ee-152">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="bd0ee-152">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bd0ee-153">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="bd0ee-153">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="bd0ee-154"><strong>ScrollConsoleScreenBufferW</strong> (Unicode) et <strong>ScrollConsoleScreenBufferA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="bd0ee-154"><strong>ScrollConsoleScreenBufferW</strong> (Unicode) and <strong>ScrollConsoleScreenBufferA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="bd0ee-155"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd0ee-155"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="bd0ee-156">**\_infos char**</span><span class="sxs-lookup"><span data-stu-id="bd0ee-156">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="bd0ee-157">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="bd0ee-157">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="bd0ee-158">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="bd0ee-158">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="bd0ee-159">Défilement de la mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="bd0ee-159">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

[<span data-ttu-id="bd0ee-160">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="bd0ee-160">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="bd0ee-161">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="bd0ee-161">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="bd0ee-162">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="bd0ee-162">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="bd0ee-163">**PETIT \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="bd0ee-163">**SMALL\_RECT**</span></span>](small-rect-str.md)

 

 




