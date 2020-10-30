---
title: ReadConsoleOutput fonction)
description: Lit les données d’attribut de caractère et de couleur à partir d’un bloc rectangulaire de cellules de caractères dans une mémoire tampon d’écran de la console et écrit des données dans la mémoire tampon de destination.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/ReadConsoleOutput
- wincon/ReadConsoleOutput
- ReadConsoleOutput
- consoleapi2/ReadConsoleOutputA
- wincon/ReadConsoleOutputA
- ReadConsoleOutputA
- consoleapi2/ReadConsoleOutputW
- wincon/ReadConsoleOutputW
- ReadConsoleOutputW
MS-HAID:
- '\_win32\_readconsoleoutput'
- base.readconsoleoutput
- consoles.readconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d1391684-6a8f-4b5e-9706-11970a957710
topic_type:
- apiref
api_name:
- ReadConsoleOutput
- ReadConsoleOutputA
- ReadConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0ce2a5a62ee7719d0184247c9ef3327850e12c1b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037757"
---
# <a name="readconsoleoutput-function"></a><span data-ttu-id="851e9-104">ReadConsoleOutput fonction)</span><span class="sxs-lookup"><span data-stu-id="851e9-104">ReadConsoleOutput function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="851e9-105">Lit les données d’attribut de caractère et de couleur à partir d’un bloc rectangulaire de cellules de caractères dans une mémoire tampon d’écran de la console, et la fonction écrit les données dans un bloc rectangulaire à un emplacement spécifié dans la mémoire tampon de destination.</span><span class="sxs-lookup"><span data-stu-id="851e9-105">Reads character and color attribute data from a rectangular block of character cells in a console screen buffer, and the function writes the data to a rectangular block at a specified location in the destination buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="851e9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="851e9-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleOutput(
  _In_    HANDLE      hConsoleOutput,
  _Out_   PCHAR_INFO  lpBuffer,
  _In_    COORD       dwBufferSize,
  _In_    COORD       dwBufferCoord,
  _Inout_ PSMALL_RECT lpReadRegion
);
```

## <a name="parameters"></a><span data-ttu-id="851e9-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="851e9-107">Parameters</span></span>

<span data-ttu-id="851e9-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="851e9-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="851e9-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="851e9-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="851e9-110">Le handle doit avoir le droit d’accès **\_ en lecture générique** .</span><span class="sxs-lookup"><span data-stu-id="851e9-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="851e9-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="851e9-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="851e9-112">*lpBuffer* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="851e9-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="851e9-113">Pointeur vers une mémoire tampon de destination qui reçoit les données lues à partir de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="851e9-113">A pointer to a destination buffer that receives the data read from the console screen buffer.</span></span> <span data-ttu-id="851e9-114">Ce pointeur est traité comme l’origine d’un tableau à deux dimensions de structures d' [**\_ informations de type char**](char-info-str.md) dont la taille est spécifiée par le paramètre *dwBufferSize* .</span><span class="sxs-lookup"><span data-stu-id="851e9-114">This pointer is treated as the origin of a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures whose size is specified by the *dwBufferSize* parameter.</span></span>

<span data-ttu-id="851e9-115">*dwBufferSize* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="851e9-115">*dwBufferSize* \[in\]</span></span>  
<span data-ttu-id="851e9-116">Taille du paramètre *lpBuffer* , dans les cellules de caractères.</span><span class="sxs-lookup"><span data-stu-id="851e9-116">The size of the *lpBuffer* parameter, in character cells.</span></span> <span data-ttu-id="851e9-117">Le membre **X** de la structure [**Coord**](coord-str.md) est le nombre de colonnes ; le membre **Y** est le nombre de lignes.</span><span class="sxs-lookup"><span data-stu-id="851e9-117">The **X** member of the [**COORD**](coord-str.md) structure is the number of columns; the **Y** member is the number of rows.</span></span>

<span data-ttu-id="851e9-118">*dwBufferCoord* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="851e9-118">*dwBufferCoord* \[in\]</span></span>  
<span data-ttu-id="851e9-119">Coordonnées de la cellule supérieure gauche dans le paramètre *lpBuffer* qui reçoit les données lues à partir de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="851e9-119">The coordinates of the upper-left cell in the *lpBuffer* parameter that receives the data read from the console screen buffer.</span></span> <span data-ttu-id="851e9-120">Le membre **X** de la structure [**Coord**](coord-str.md) est la colonne et le membre **Y** est la ligne.</span><span class="sxs-lookup"><span data-stu-id="851e9-120">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="851e9-121">*lpReadRegion* \[ in, out\]</span><span class="sxs-lookup"><span data-stu-id="851e9-121">*lpReadRegion* \[in, out\]</span></span>  
<span data-ttu-id="851e9-122">Pointeur vers une [**petite structure \_ Rect**](small-rect-str.md) .</span><span class="sxs-lookup"><span data-stu-id="851e9-122">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="851e9-123">En entrée, les membres de structure spécifient les coordonnées supérieure gauche et inférieure droite du rectangle de la mémoire tampon d’écran de la console à partir duquel la fonction doit être lue.</span><span class="sxs-lookup"><span data-stu-id="851e9-123">On input, the structure members specify the upper-left and lower-right coordinates of the console screen buffer rectangle from which the function is to read.</span></span> <span data-ttu-id="851e9-124">Lors de la sortie, les membres de structure spécifient le rectangle réel qui a été utilisé.</span><span class="sxs-lookup"><span data-stu-id="851e9-124">On output, the structure members specify the actual rectangle that was used.</span></span>

## <a name="return-value"></a><span data-ttu-id="851e9-125">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="851e9-125">Return value</span></span>

<span data-ttu-id="851e9-126">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="851e9-126">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="851e9-127">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="851e9-127">If the function fails, the return value is zero.</span></span> <span data-ttu-id="851e9-128">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="851e9-128">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="851e9-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="851e9-129">Remarks</span></span>

<span data-ttu-id="851e9-130">**ReadConsoleOutput** traite la mémoire tampon d’écran de la console et la mémoire tampon de destination en tant que tableaux à deux dimensions (colonnes et lignes de cellules de caractères).</span><span class="sxs-lookup"><span data-stu-id="851e9-130">**ReadConsoleOutput** treats the console screen buffer and the destination buffer as two-dimensional arrays (columns and rows of character cells).</span></span> <span data-ttu-id="851e9-131">Le rectangle vers lequel pointe le paramètre *lpReadRegion* spécifie la taille et l’emplacement du bloc à lire à partir de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="851e9-131">The rectangle pointed to by the *lpReadRegion* parameter specifies the size and location of the block to be read from the console screen buffer.</span></span> <span data-ttu-id="851e9-132">Un rectangle de destination de la même taille se trouve avec sa cellule supérieure gauche aux coordonnées du paramètre *dwBufferCoord* dans le tableau *lpBuffer* .</span><span class="sxs-lookup"><span data-stu-id="851e9-132">A destination rectangle of the same size is located with its upper-left cell at the coordinates of the *dwBufferCoord* parameter in the *lpBuffer* array.</span></span> <span data-ttu-id="851e9-133">Les données lues à partir des cellules du rectangle source de la mémoire tampon d’écran de la console sont copiées dans les cellules correspondantes de la mémoire tampon de destination.</span><span class="sxs-lookup"><span data-stu-id="851e9-133">Data read from the cells in the console screen buffer source rectangle is copied to the corresponding cells in the destination buffer.</span></span> <span data-ttu-id="851e9-134">Si la cellule correspondante se trouve en dehors des limites du rectangle de la mémoire tampon de destination (dont les dimensions sont spécifiées par le paramètre *dwBufferSize* ), les données ne sont pas copiées.</span><span class="sxs-lookup"><span data-stu-id="851e9-134">If the corresponding cell is outside the boundaries of the destination buffer rectangle (whose dimensions are specified by the *dwBufferSize* parameter), the data is not copied.</span></span>

<span data-ttu-id="851e9-135">Les cellules de la mémoire tampon de destination correspondant à des coordonnées qui ne se trouvent pas dans les limites de la mémoire tampon de l’écran de la console restent inchangées.</span><span class="sxs-lookup"><span data-stu-id="851e9-135">Cells in the destination buffer corresponding to coordinates that are not within the boundaries of the console screen buffer are left unchanged.</span></span> <span data-ttu-id="851e9-136">En d’autres termes, il s’agit des cellules pour lesquelles aucune donnée de mémoire tampon d’écran n’est disponible pour la lecture.</span><span class="sxs-lookup"><span data-stu-id="851e9-136">In other words, these are the cells for which no screen buffer data is available to be read.</span></span>

<span data-ttu-id="851e9-137">Avant que **ReadConsoleOutput** retourne, il définit les membres de la structure vers laquelle pointe le paramètre *lpReadRegion* vers le rectangle de mémoire tampon d’écran réel dont les cellules ont été copiées dans la mémoire tampon de destination.</span><span class="sxs-lookup"><span data-stu-id="851e9-137">Before **ReadConsoleOutput** returns, it sets the members of the structure pointed to by the *lpReadRegion* parameter to the actual screen buffer rectangle whose cells were copied into the destination buffer.</span></span> <span data-ttu-id="851e9-138">Ce rectangle reflète les cellules du rectangle source pour lesquelles il existait une cellule correspondante dans la mémoire tampon de destination, car **ReadConsoleOutput** découpe les dimensions du rectangle source pour les adapter aux limites de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="851e9-138">This rectangle reflects the cells in the source rectangle for which there existed a corresponding cell in the destination buffer, because **ReadConsoleOutput** clips the dimensions of the source rectangle to fit the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="851e9-139">Si le rectangle spécifié par *lpReadRegion* se trouve complètement en dehors des limites de la mémoire tampon d’écran de la console, ou si le rectangle correspondant est positionné complètement en dehors des limites de la mémoire tampon de destination, aucune donnée n’est copiée.</span><span class="sxs-lookup"><span data-stu-id="851e9-139">If the rectangle specified by *lpReadRegion* lies completely outside the boundaries of the console screen buffer, or if the corresponding rectangle is positioned completely outside the boundaries of the destination buffer, no data is copied.</span></span> <span data-ttu-id="851e9-140">Dans ce cas, la fonction retourne avec les membres de la structure vers laquelle pointe le jeu de paramètres *lpReadRegion* , de sorte que le membre de **droite** est inférieur à la **gauche** , ou le membre **inférieur** est inférieur au **haut** .</span><span class="sxs-lookup"><span data-stu-id="851e9-140">In this case, the function returns with the members of the structure pointed to by the *lpReadRegion* parameter set such that the **Right** member is less than the **Left** , or the **Bottom** member is less than the **Top** .</span></span> <span data-ttu-id="851e9-141">Pour déterminer la taille de la mémoire tampon d’écran de la console, utilisez la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="851e9-141">To determine the size of the console screen buffer, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="851e9-142">La fonction **ReadConsoleOutput** n’a aucun effet sur la position du curseur de la mémoire tampon de l’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="851e9-142">The **ReadConsoleOutput** function has no effect on the console screen buffer's cursor position.</span></span> <span data-ttu-id="851e9-143">Le contenu de la mémoire tampon d’écran de la console n’est pas modifié par la fonction.</span><span class="sxs-lookup"><span data-stu-id="851e9-143">The contents of the console screen buffer are not changed by the function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="examples"></a><span data-ttu-id="851e9-144">Exemples</span><span class="sxs-lookup"><span data-stu-id="851e9-144">Examples</span></span>

<span data-ttu-id="851e9-145">Pour obtenir un exemple, consultez [lecture et écriture de blocs de caractères et d’attributs](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="851e9-145">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="851e9-146">Spécifications</span><span class="sxs-lookup"><span data-stu-id="851e9-146">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="851e9-147">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="851e9-147">Minimum supported client</span></span> | <span data-ttu-id="851e9-148">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="851e9-148">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="851e9-149">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="851e9-149">Minimum supported server</span></span> | <span data-ttu-id="851e9-150">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="851e9-150">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="851e9-151">En-tête</span><span class="sxs-lookup"><span data-stu-id="851e9-151">Header</span></span> | <span data-ttu-id="851e9-152">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="851e9-152">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="851e9-153">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="851e9-153">Library</span></span> | <span data-ttu-id="851e9-154">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="851e9-154">Kernel32.lib</span></span> |
| <span data-ttu-id="851e9-155">DLL</span><span class="sxs-lookup"><span data-stu-id="851e9-155">DLL</span></span> | <span data-ttu-id="851e9-156">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="851e9-156">Kernel32.dll</span></span> |
| <span data-ttu-id="851e9-157">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="851e9-157">Unicode and ANSI names</span></span> | <span data-ttu-id="851e9-158">**ReadConsoleOutputW** (Unicode) et **ReadConsoleOutputA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="851e9-158">**ReadConsoleOutputW** (Unicode) and **ReadConsoleOutputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="851e9-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="851e9-159">See also</span></span>

[<span data-ttu-id="851e9-160">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="851e9-160">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="851e9-161">Fonctions de sortie de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="851e9-161">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="851e9-162">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="851e9-162">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="851e9-163">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="851e9-163">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="851e9-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="851e9-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="851e9-165">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="851e9-165">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="851e9-166">**PETIT \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="851e9-166">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="851e9-167">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="851e9-167">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="851e9-168">**\_infos char**</span><span class="sxs-lookup"><span data-stu-id="851e9-168">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="851e9-169">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="851e9-169">**COORD**</span></span>](coord-str.md)
