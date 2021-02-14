---
title: Structure CHAR_INFO
description: Spécifie un caractère Unicode ou ANSI et ses attributs. Cette structure est utilisée par les fonctions de la console pour lire et écrire dans une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- wincontypes/CHAR_INFO
- wincon/CHAR_INFO
- CHAR_INFO
- wincontypes/PCHAR_INFO
- wincon/PCHAR_INFO
- PCHAR_INFO
MS-HAID:
- '\_win32\_char\_info\_str'
- base.char\_info\_str
- consoles.char\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5574a862-b262-41af-8862-e9837c5c7b5f
topic_type:
- apiref
api_name:
- CHAR_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: a16fb23d148f75480437211204a0fd7c1f161bfe
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357849"
---
# `CHAR\_INFO structure`

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="0710e-105">Spécifie un caractère Unicode ou ANSI et ses attributs.</span><span class="sxs-lookup"><span data-stu-id="0710e-105">Specifies a Unicode or ANSI character and its attributes.</span></span> <span data-ttu-id="0710e-106">Cette structure est utilisée par les fonctions de la console pour lire et écrire dans une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="0710e-106">This structure is used by console functions to read from and write to a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="0710e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0710e-107">Syntax</span></span>

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

## <a name="members"></a><span data-ttu-id="0710e-108">Membres</span><span class="sxs-lookup"><span data-stu-id="0710e-108">Members</span></span>

<span data-ttu-id="0710e-109">**Char**</span><span class="sxs-lookup"><span data-stu-id="0710e-109">**Char**</span></span>  
<span data-ttu-id="0710e-110">Union des membres suivants.</span><span class="sxs-lookup"><span data-stu-id="0710e-110">A union of the following members.</span></span>

<span data-ttu-id="0710e-111">**UnicodeChar**</span><span class="sxs-lookup"><span data-stu-id="0710e-111">**UnicodeChar**</span></span>  
<span data-ttu-id="0710e-112">Caractère Unicode d’une cellule de caractère de mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="0710e-112">Unicode character of a screen buffer character cell.</span></span>

<span data-ttu-id="0710e-113">**AsciiChar**</span><span class="sxs-lookup"><span data-stu-id="0710e-113">**AsciiChar**</span></span>  
<span data-ttu-id="0710e-114">Caractère ANSI d’une cellule de caractère de mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="0710e-114">ANSI character of a screen buffer character cell.</span></span>

<span data-ttu-id="0710e-115">**Attributs**</span><span class="sxs-lookup"><span data-stu-id="0710e-115">**Attributes**</span></span>  
<span data-ttu-id="0710e-116">Attributs de caractère.</span><span class="sxs-lookup"><span data-stu-id="0710e-116">The character attributes.</span></span> <span data-ttu-id="0710e-117">Ce membre peut être égal à zéro ou n’importe quelle combinaison des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="0710e-117">This member can be zero or any combination of the following values.</span></span>

| <span data-ttu-id="0710e-118">Valeur</span><span class="sxs-lookup"><span data-stu-id="0710e-118">Value</span></span> | <span data-ttu-id="0710e-119">Signification</span><span class="sxs-lookup"><span data-stu-id="0710e-119">Meaning</span></span> |
|-|-|
| <span data-ttu-id="0710e-120">**FOREGROUND_BLUE**`0x0001`</span><span class="sxs-lookup"><span data-stu-id="0710e-120">**FOREGROUND_BLUE** `0x0001`</span></span> | <span data-ttu-id="0710e-121">La couleur du texte contient du bleu.</span><span class="sxs-lookup"><span data-stu-id="0710e-121">Text color contains blue.</span></span> |
| <span data-ttu-id="0710e-122">**FOREGROUND_GREEN**`0x0002`</span><span class="sxs-lookup"><span data-stu-id="0710e-122">**FOREGROUND_GREEN** `0x0002`</span></span> | <span data-ttu-id="0710e-123">La couleur du texte contient du vert.</span><span class="sxs-lookup"><span data-stu-id="0710e-123">Text color contains green.</span></span> |
| <span data-ttu-id="0710e-124">**FOREGROUND_RED**`0x0004`</span><span class="sxs-lookup"><span data-stu-id="0710e-124">**FOREGROUND_RED** `0x0004`</span></span> | <span data-ttu-id="0710e-125">La couleur du texte contient du rouge.</span><span class="sxs-lookup"><span data-stu-id="0710e-125">Text color contains red.</span></span> |
| <span data-ttu-id="0710e-126">**FOREGROUND_INTENSITY**`0x0008`</span><span class="sxs-lookup"><span data-stu-id="0710e-126">**FOREGROUND_INTENSITY** `0x0008`</span></span> | <span data-ttu-id="0710e-127">La couleur du texte est intensifiée.</span><span class="sxs-lookup"><span data-stu-id="0710e-127">Text color is intensified.</span></span> |
| <span data-ttu-id="0710e-128">**BACKGROUND_BLUE**`0x0010`</span><span class="sxs-lookup"><span data-stu-id="0710e-128">**BACKGROUND_BLUE** `0x0010`</span></span> | <span data-ttu-id="0710e-129">La couleur d’arrière-plan contient du bleu.</span><span class="sxs-lookup"><span data-stu-id="0710e-129">Background color contains blue.</span></span> |
| <span data-ttu-id="0710e-130">**BACKGROUND_GREEN**`0x0020`</span><span class="sxs-lookup"><span data-stu-id="0710e-130">**BACKGROUND_GREEN** `0x0020`</span></span> | <span data-ttu-id="0710e-131">La couleur d’arrière-plan contient du vert.</span><span class="sxs-lookup"><span data-stu-id="0710e-131">Background color contains green.</span></span> |
| <span data-ttu-id="0710e-132">**BACKGROUND_RED**`0x0040`</span><span class="sxs-lookup"><span data-stu-id="0710e-132">**BACKGROUND_RED** `0x0040`</span></span> | <span data-ttu-id="0710e-133">La couleur d’arrière-plan contient du rouge.</span><span class="sxs-lookup"><span data-stu-id="0710e-133">Background color contains red.</span></span> |
| <span data-ttu-id="0710e-134">**BACKGROUND_INTENSITY**`0x0080`</span><span class="sxs-lookup"><span data-stu-id="0710e-134">**BACKGROUND_INTENSITY** `0x0080`</span></span> | <span data-ttu-id="0710e-135">La couleur d’arrière-plan est intensifiée.</span><span class="sxs-lookup"><span data-stu-id="0710e-135">Background color is intensified.</span></span> |
| <span data-ttu-id="0710e-136">**COMMON_LVB_LEADING_BYTE**`0x0100`</span><span class="sxs-lookup"><span data-stu-id="0710e-136">**COMMON_LVB_LEADING_BYTE** `0x0100`</span></span> | <span data-ttu-id="0710e-137">Octet de début.</span><span class="sxs-lookup"><span data-stu-id="0710e-137">Leading byte.</span></span> |
| <span data-ttu-id="0710e-138">**COMMON_LVB_TRAILING_BYTE**`0x0200`</span><span class="sxs-lookup"><span data-stu-id="0710e-138">**COMMON_LVB_TRAILING_BYTE** `0x0200`</span></span> | <span data-ttu-id="0710e-139">Octet de fin.</span><span class="sxs-lookup"><span data-stu-id="0710e-139">Trailing byte.</span></span> |
| <span data-ttu-id="0710e-140">**COMMON_LVB_GRID_HORIZONTAL**`0x0400`</span><span class="sxs-lookup"><span data-stu-id="0710e-140">**COMMON_LVB_GRID_HORIZONTAL** `0x0400`</span></span> | <span data-ttu-id="0710e-141">Supérieur horizontal.</span><span class="sxs-lookup"><span data-stu-id="0710e-141">Top horizontal.</span></span> |
| <span data-ttu-id="0710e-142">**COMMON_LVB_GRID_LVERTICAL**`0x0800`</span><span class="sxs-lookup"><span data-stu-id="0710e-142">**COMMON_LVB_GRID_LVERTICAL** `0x0800`</span></span> | <span data-ttu-id="0710e-143">Gauche vertical.</span><span class="sxs-lookup"><span data-stu-id="0710e-143">Left vertical.</span></span> |
| <span data-ttu-id="0710e-144">**COMMON_LVB_GRID_RVERTICAL**`0x1000`</span><span class="sxs-lookup"><span data-stu-id="0710e-144">**COMMON_LVB_GRID_RVERTICAL** `0x1000`</span></span> | <span data-ttu-id="0710e-145">Droite vertical.</span><span class="sxs-lookup"><span data-stu-id="0710e-145">Right vertical.</span></span> |
| <span data-ttu-id="0710e-146">**COMMON_LVB_REVERSE_VIDEO**`0x4000`</span><span class="sxs-lookup"><span data-stu-id="0710e-146">**COMMON_LVB_REVERSE_VIDEO** `0x4000`</span></span> | <span data-ttu-id="0710e-147">Attribut de premier plan et d’arrière-plan inversé.</span><span class="sxs-lookup"><span data-stu-id="0710e-147">Reverse foreground and background attribute.</span></span> |
| <span data-ttu-id="0710e-148">**COMMON_LVB_UNDERSCORE**`0x8000`</span><span class="sxs-lookup"><span data-stu-id="0710e-148">**COMMON_LVB_UNDERSCORE** `0x8000`</span></span> | <span data-ttu-id="0710e-149">Caractère de soulignement.</span><span class="sxs-lookup"><span data-stu-id="0710e-149">Underscore.</span></span> |

## <a name="examples"></a><span data-ttu-id="0710e-150">Exemples</span><span class="sxs-lookup"><span data-stu-id="0710e-150">Examples</span></span>

<span data-ttu-id="0710e-151">Pour obtenir un exemple, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="0710e-151">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="0710e-152">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0710e-152">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="0710e-153">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="0710e-153">Minimum supported client</span></span> | <span data-ttu-id="0710e-154">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="0710e-154">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="0710e-155">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="0710e-155">Minimum supported server</span></span> | <span data-ttu-id="0710e-156">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="0710e-156">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="0710e-157">En-tête</span><span class="sxs-lookup"><span data-stu-id="0710e-157">Header</span></span> | <span data-ttu-id="0710e-158">WinCon. h (inclure Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0710e-158">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="0710e-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0710e-159">See also</span></span>

[<span data-ttu-id="0710e-160">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="0710e-160">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="0710e-161">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="0710e-161">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="0710e-162">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="0710e-162">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)
