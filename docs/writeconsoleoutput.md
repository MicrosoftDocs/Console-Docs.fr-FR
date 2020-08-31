---
title: WriteConsoleOutput fonction)
description: Écrit des données d’attribut de caractère et de couleur dans un bloc rectangulaire spécifié de cellules de caractères dans une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/WriteConsoleOutput
- wincon/WriteConsoleOutput
- WriteConsoleOutput
- consoleapi2/WriteConsoleOutputA
- wincon/WriteConsoleOutputA
- WriteConsoleOutputA
- consoleapi2/WriteConsoleOutputW
- wincon/WriteConsoleOutputW
- WriteConsoleOutputW
MS-HAID:
- '\_win32\_writeconsoleoutput'
- base.writeconsoleoutput
- consoles.writeconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a98b8118-97ce-4dd4-a337-122d4a76f232
topic_type:
- apiref
api_name:
- WriteConsoleOutput
- WriteConsoleOutputA
- WriteConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e2f84f5c072a8404b129e27bec3464363b9dd3d0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059052"
---
# <a name="writeconsoleoutput-function"></a><span data-ttu-id="85d90-104">WriteConsoleOutput fonction)</span><span class="sxs-lookup"><span data-stu-id="85d90-104">WriteConsoleOutput function</span></span>


<span data-ttu-id="85d90-105">Écrit des données d’attribut de caractère et de couleur dans un bloc rectangulaire spécifié de cellules de caractères dans une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="85d90-105">Writes character and color attribute data to a specified rectangular block of character cells in a console screen buffer.</span></span> <span data-ttu-id="85d90-106">Les données à écrire proviennent d’un bloc rectangulaire de taille correspondante à un emplacement spécifié dans la mémoire tampon source.</span><span class="sxs-lookup"><span data-stu-id="85d90-106">The data to be written is taken from a correspondingly sized rectangular block at a specified location in the source buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="85d90-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85d90-107">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleOutput(
  _In_          HANDLE      hConsoleOutput,
  _In_    const CHAR_INFO   *lpBuffer,
  _In_          COORD       dwBufferSize,
  _In_          COORD       dwBufferCoord,
  _Inout_       PSMALL_RECT lpWriteRegion
);
```

<a name="parameters"></a><span data-ttu-id="85d90-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="85d90-108">Parameters</span></span>
----------

<span data-ttu-id="85d90-109">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="85d90-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="85d90-110">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="85d90-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="85d90-111">Le descripteur doit avoir le droit d’accès en \*\* \_ écriture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="85d90-111">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="85d90-112">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="85d90-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="85d90-113">*lpBuffer* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="85d90-113">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="85d90-114">Données à écrire dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="85d90-114">The data to be written to the console screen buffer.</span></span> <span data-ttu-id="85d90-115">Ce pointeur est traité comme l’origine d’un tableau à deux dimensions de structures d' [\*\* \_ informations de type char\*\*](char-info-str.md) dont la taille est spécifiée par le paramètre *dwBufferSize* .</span><span class="sxs-lookup"><span data-stu-id="85d90-115">This pointer is treated as the origin of a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures whose size is specified by the *dwBufferSize* parameter.</span></span>

<span data-ttu-id="85d90-116">*dwBufferSize* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="85d90-116">*dwBufferSize* \[in\]</span></span>  
<span data-ttu-id="85d90-117">Taille de la mémoire tampon vers laquelle pointe le paramètre *lpBuffer* , dans les cellules de caractères.</span><span class="sxs-lookup"><span data-stu-id="85d90-117">The size of the buffer pointed to by the *lpBuffer* parameter, in character cells.</span></span> <span data-ttu-id="85d90-118">Le membre **X** de la structure [**Coord**](coord-str.md) est le nombre de colonnes ; le membre **Y** est le nombre de lignes.</span><span class="sxs-lookup"><span data-stu-id="85d90-118">The **X** member of the [**COORD**](coord-str.md) structure is the number of columns; the **Y** member is the number of rows.</span></span>

<span data-ttu-id="85d90-119">*dwBufferCoord* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="85d90-119">*dwBufferCoord* \[in\]</span></span>  
<span data-ttu-id="85d90-120">Coordonnées de la cellule supérieure gauche dans la mémoire tampon vers laquelle pointe le paramètre *lpBuffer* .</span><span class="sxs-lookup"><span data-stu-id="85d90-120">The coordinates of the upper-left cell in the buffer pointed to by the *lpBuffer* parameter.</span></span> <span data-ttu-id="85d90-121">Le membre **X** de la structure [**Coord**](coord-str.md) est la colonne et le membre **Y** est la ligne.</span><span class="sxs-lookup"><span data-stu-id="85d90-121">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="85d90-122">*lpWriteRegion* \[ in, out\]</span><span class="sxs-lookup"><span data-stu-id="85d90-122">*lpWriteRegion* \[in, out\]</span></span>  
<span data-ttu-id="85d90-123">Pointeur vers une [**petite structure \_ Rect**](small-rect-str.md) .</span><span class="sxs-lookup"><span data-stu-id="85d90-123">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="85d90-124">En entrée, les membres de structure spécifient les coordonnées supérieure gauche et inférieure droite du rectangle de mémoire tampon de l’écran de la console dans lequel écrire.</span><span class="sxs-lookup"><span data-stu-id="85d90-124">On input, the structure members specify the upper-left and lower-right coordinates of the console screen buffer rectangle to write to.</span></span> <span data-ttu-id="85d90-125">Lors de la sortie, les membres de structure spécifient le rectangle réel qui a été utilisé.</span><span class="sxs-lookup"><span data-stu-id="85d90-125">On output, the structure members specify the actual rectangle that was used.</span></span>

<a name="return-value"></a><span data-ttu-id="85d90-126">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="85d90-126">Return value</span></span>
------------

<span data-ttu-id="85d90-127">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="85d90-127">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="85d90-128">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="85d90-128">If the function fails, the return value is zero.</span></span> <span data-ttu-id="85d90-129">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="85d90-129">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="85d90-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="85d90-130">Remarks</span></span>
-------

<span data-ttu-id="85d90-131">**WriteConsoleOutput** traite la mémoire tampon source et la mémoire tampon d’écran de destination en tant que tableaux à deux dimensions (colonnes et lignes de cellules de caractères).</span><span class="sxs-lookup"><span data-stu-id="85d90-131">**WriteConsoleOutput** treats the source buffer and the destination screen buffer as two-dimensional arrays (columns and rows of character cells).</span></span> <span data-ttu-id="85d90-132">Le rectangle vers lequel pointe le paramètre *lpWriteRegion* spécifie la taille et l’emplacement du bloc dans lequel écrire dans la mémoire tampon de l’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="85d90-132">The rectangle pointed to by the *lpWriteRegion* parameter specifies the size and location of the block to be written to in the console screen buffer.</span></span> <span data-ttu-id="85d90-133">Un rectangle de même taille se trouve avec sa cellule supérieure gauche aux coordonnées du paramètre *dwBufferCoord* dans le tableau *lpBuffer* .</span><span class="sxs-lookup"><span data-stu-id="85d90-133">A rectangle of the same size is located with its upper-left cell at the coordinates of the *dwBufferCoord* parameter in the *lpBuffer* array.</span></span> <span data-ttu-id="85d90-134">Les données des cellules situées à l’intersection de ce rectangle et du rectangle de la mémoire tampon source (dont les dimensions sont spécifiées par le paramètre *dwBufferSize* ) sont écrites dans le rectangle de destination.</span><span class="sxs-lookup"><span data-stu-id="85d90-134">Data from the cells that are in the intersection of this rectangle and the source buffer rectangle (whose dimensions are specified by the *dwBufferSize* parameter) is written to the destination rectangle.</span></span>

<span data-ttu-id="85d90-135">Les cellules du rectangle de destination dont l’emplacement source correspondant se trouve en dehors des limites du rectangle de la mémoire tampon source ne sont pas affectées par l’opération d’écriture.</span><span class="sxs-lookup"><span data-stu-id="85d90-135">Cells in the destination rectangle whose corresponding source location are outside the boundaries of the source buffer rectangle are left unaffected by the write operation.</span></span> <span data-ttu-id="85d90-136">En d’autres termes, il s’agit des cellules pour lesquelles aucune donnée n’est disponible pour être écrite.</span><span class="sxs-lookup"><span data-stu-id="85d90-136">In other words, these are the cells for which no data is available to be written.</span></span>

<span data-ttu-id="85d90-137">Avant que **WriteConsoleOutput** retourne, il définit les membres de *lpWriteRegion* sur le rectangle de mémoire tampon d’écran réel affecté par l’opération d’écriture.</span><span class="sxs-lookup"><span data-stu-id="85d90-137">Before **WriteConsoleOutput** returns, it sets the members of *lpWriteRegion* to the actual screen buffer rectangle affected by the write operation.</span></span> <span data-ttu-id="85d90-138">Ce rectangle reflète les cellules du rectangle de destination pour lesquelles il existait une cellule correspondante dans la mémoire tampon source, car **WriteConsoleOutput** découpe les dimensions du rectangle de destination aux limites de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="85d90-138">This rectangle reflects the cells in the destination rectangle for which there existed a corresponding cell in the source buffer, because **WriteConsoleOutput** clips the dimensions of the destination rectangle to the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="85d90-139">Si le rectangle spécifié par *lpWriteRegion* se trouve complètement en dehors des limites de la mémoire tampon d’écran de la console, ou si le rectangle correspondant est positionné complètement en dehors des limites de la mémoire tampon source, aucune donnée n’est écrite.</span><span class="sxs-lookup"><span data-stu-id="85d90-139">If the rectangle specified by *lpWriteRegion* lies completely outside the boundaries of the console screen buffer, or if the corresponding rectangle is positioned completely outside the boundaries of the source buffer, no data is written.</span></span> <span data-ttu-id="85d90-140">Dans ce cas, la fonction retourne avec les membres de la structure vers laquelle pointe le jeu de paramètres *lpWriteRegion* , de sorte que le membre de **droite** est inférieur à la **gauche**, ou le membre **inférieur** est inférieur au **haut**.</span><span class="sxs-lookup"><span data-stu-id="85d90-140">In this case, the function returns with the members of the structure pointed to by the *lpWriteRegion* parameter set such that the **Right** member is less than the **Left**, or the **Bottom** member is less than the **Top**.</span></span> <span data-ttu-id="85d90-141">Pour déterminer la taille de la mémoire tampon d’écran de la console, utilisez la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="85d90-141">To determine the size of the console screen buffer, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="85d90-142">**WriteConsoleOutput** n’a aucun effet sur la position du curseur.</span><span class="sxs-lookup"><span data-stu-id="85d90-142">**WriteConsoleOutput** has no effect on the cursor position.</span></span>

<span data-ttu-id="85d90-143">Cette fonction utilise des caractères Unicode ou 8 bits à partir de la page de codes actuelle de la console.</span><span class="sxs-lookup"><span data-stu-id="85d90-143">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="85d90-144">La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système.</span><span class="sxs-lookup"><span data-stu-id="85d90-144">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="85d90-145">Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="85d90-145">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="85d90-146">Exemples</span><span class="sxs-lookup"><span data-stu-id="85d90-146">Examples</span></span>
--------

<span data-ttu-id="85d90-147">Pour obtenir un exemple, consultez [lecture et écriture de blocs de caractères et d’attributs](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="85d90-147">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

<a name="requirements"></a><span data-ttu-id="85d90-148">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="85d90-148">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="85d90-149">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="85d90-149">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="85d90-150">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="85d90-150">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="85d90-151">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="85d90-151">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="85d90-152">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="85d90-152">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="85d90-153">En-tête</span><span class="sxs-lookup"><span data-stu-id="85d90-153">Header</span></span></p></td>
<td><span data-ttu-id="85d90-154">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="85d90-154">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="85d90-155">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="85d90-155">Library</span></span></p></td>
<td><span data-ttu-id="85d90-156">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="85d90-156">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="85d90-157">DLL</span><span class="sxs-lookup"><span data-stu-id="85d90-157">DLL</span></span></p></td>
<td><span data-ttu-id="85d90-158">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="85d90-158">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="85d90-159">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="85d90-159">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="85d90-160"><strong>WriteConsoleOutputW</strong> (Unicode) et <strong>WriteConsoleOutputA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="85d90-160"><strong>WriteConsoleOutputW</strong> (Unicode) and <strong>WriteConsoleOutputA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="85d90-161"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85d90-161"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="85d90-162">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="85d90-162">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="85d90-163">**\_infos char**</span><span class="sxs-lookup"><span data-stu-id="85d90-163">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="85d90-164">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="85d90-164">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="85d90-165">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="85d90-165">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="85d90-166">Fonctions de sortie de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="85d90-166">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="85d90-167">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="85d90-167">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="85d90-168">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="85d90-168">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="85d90-169">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="85d90-169">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="85d90-170">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="85d90-170">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="85d90-171">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="85d90-171">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="85d90-172">**PETIT \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="85d90-172">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="85d90-173">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="85d90-173">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="85d90-174">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="85d90-174">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




