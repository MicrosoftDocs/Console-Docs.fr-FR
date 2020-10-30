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
ms.openlocfilehash: b07938d6ac58744533711c91a04b1a0188f7daf6
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037377"
---
# <a name="char_info-structure"></a><span data-ttu-id="52ba6-105">CHAR \_ info (structure)</span><span class="sxs-lookup"><span data-stu-id="52ba6-105">CHAR\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="52ba6-106">Spécifie un caractère Unicode ou ANSI et ses attributs.</span><span class="sxs-lookup"><span data-stu-id="52ba6-106">Specifies a Unicode or ANSI character and its attributes.</span></span> <span data-ttu-id="52ba6-107">Cette structure est utilisée par les fonctions de la console pour lire et écrire dans une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="52ba6-107">This structure is used by console functions to read from and write to a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="52ba6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52ba6-108">Syntax</span></span>

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

## <a name="members"></a><span data-ttu-id="52ba6-109">Membres</span><span class="sxs-lookup"><span data-stu-id="52ba6-109">Members</span></span>

<span data-ttu-id="52ba6-110">**Char**</span><span class="sxs-lookup"><span data-stu-id="52ba6-110">**Char**</span></span>  
<span data-ttu-id="52ba6-111">Union des membres suivants.</span><span class="sxs-lookup"><span data-stu-id="52ba6-111">A union of the following members.</span></span>

<span data-ttu-id="52ba6-112">**UnicodeChar**</span><span class="sxs-lookup"><span data-stu-id="52ba6-112">**UnicodeChar**</span></span>  
<span data-ttu-id="52ba6-113">Caractère Unicode d’une cellule de caractère de mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="52ba6-113">Unicode character of a screen buffer character cell.</span></span>

<span data-ttu-id="52ba6-114">**AsciiChar**</span><span class="sxs-lookup"><span data-stu-id="52ba6-114">**AsciiChar**</span></span>  
<span data-ttu-id="52ba6-115">Caractère ANSI d’une cellule de caractère de mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="52ba6-115">ANSI character of a screen buffer character cell.</span></span>

<span data-ttu-id="52ba6-116">**Attributs**</span><span class="sxs-lookup"><span data-stu-id="52ba6-116">**Attributes**</span></span>  
<span data-ttu-id="52ba6-117">Attributs de caractère.</span><span class="sxs-lookup"><span data-stu-id="52ba6-117">The character attributes.</span></span> <span data-ttu-id="52ba6-118">Ce membre peut être égal à zéro ou n’importe quelle combinaison des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="52ba6-118">This member can be zero or any combination of the following values.</span></span>

| <span data-ttu-id="52ba6-119">Valeur</span><span class="sxs-lookup"><span data-stu-id="52ba6-119">Value</span></span> | <span data-ttu-id="52ba6-120">Signification</span><span class="sxs-lookup"><span data-stu-id="52ba6-120">Meaning</span></span> |
|-|-|
| <span data-ttu-id="52ba6-121">**FOREGROUND_BLUE**`0x0001`</span><span class="sxs-lookup"><span data-stu-id="52ba6-121">**FOREGROUND_BLUE** `0x0001`</span></span> | <span data-ttu-id="52ba6-122">La couleur du texte contient le bleu.</span><span class="sxs-lookup"><span data-stu-id="52ba6-122">Text color contains blue.</span></span> |
| <span data-ttu-id="52ba6-123">**FOREGROUND_GREEN**`0x0002`</span><span class="sxs-lookup"><span data-stu-id="52ba6-123">**FOREGROUND_GREEN** `0x0002`</span></span> | <span data-ttu-id="52ba6-124">La couleur du texte contient du vert.</span><span class="sxs-lookup"><span data-stu-id="52ba6-124">Text color contains green.</span></span> |
| <span data-ttu-id="52ba6-125">**FOREGROUND_RED**`0x0004`</span><span class="sxs-lookup"><span data-stu-id="52ba6-125">**FOREGROUND_RED** `0x0004`</span></span> | <span data-ttu-id="52ba6-126">La couleur du texte contient le rouge.</span><span class="sxs-lookup"><span data-stu-id="52ba6-126">Text color contains red.</span></span> |
| <span data-ttu-id="52ba6-127">**FOREGROUND_INTENSITY**`0x0008`</span><span class="sxs-lookup"><span data-stu-id="52ba6-127">**FOREGROUND_INTENSITY** `0x0008`</span></span> | <span data-ttu-id="52ba6-128">La couleur du texte est intensifiée.</span><span class="sxs-lookup"><span data-stu-id="52ba6-128">Text color is intensified.</span></span> |
| <span data-ttu-id="52ba6-129">**BACKGROUND_BLUE**`0x0010`</span><span class="sxs-lookup"><span data-stu-id="52ba6-129">**BACKGROUND_BLUE** `0x0010`</span></span> | <span data-ttu-id="52ba6-130">La couleur d’arrière-plan contient le bleu.</span><span class="sxs-lookup"><span data-stu-id="52ba6-130">Background color contains blue.</span></span> |
| <span data-ttu-id="52ba6-131">**BACKGROUND_GREEN**`0x0020`</span><span class="sxs-lookup"><span data-stu-id="52ba6-131">**BACKGROUND_GREEN** `0x0020`</span></span> | <span data-ttu-id="52ba6-132">La couleur d’arrière-plan contient du vert.</span><span class="sxs-lookup"><span data-stu-id="52ba6-132">Background color contains green.</span></span> |
| <span data-ttu-id="52ba6-133">**BACKGROUND_RED**`0x0040`</span><span class="sxs-lookup"><span data-stu-id="52ba6-133">**BACKGROUND_RED** `0x0040`</span></span> | <span data-ttu-id="52ba6-134">La couleur d’arrière-plan contient le rouge.</span><span class="sxs-lookup"><span data-stu-id="52ba6-134">Background color contains red.</span></span> |
| <span data-ttu-id="52ba6-135">**BACKGROUND_INTENSITY**`0x0080`</span><span class="sxs-lookup"><span data-stu-id="52ba6-135">**BACKGROUND_INTENSITY** `0x0080`</span></span> | <span data-ttu-id="52ba6-136">La couleur d’arrière-plan est intensifiée.</span><span class="sxs-lookup"><span data-stu-id="52ba6-136">Background color is intensified.</span></span> |
| <span data-ttu-id="52ba6-137">**COMMON_LVB_LEADING_BYTE**`0x0100`</span><span class="sxs-lookup"><span data-stu-id="52ba6-137">**COMMON_LVB_LEADING_BYTE** `0x0100`</span></span> | <span data-ttu-id="52ba6-138">Octet de début.</span><span class="sxs-lookup"><span data-stu-id="52ba6-138">Leading byte.</span></span> |
| <span data-ttu-id="52ba6-139">**COMMON_LVB_TRAILING_BYTE**`0x0200`</span><span class="sxs-lookup"><span data-stu-id="52ba6-139">**COMMON_LVB_TRAILING_BYTE** `0x0200`</span></span> | <span data-ttu-id="52ba6-140">Octet de fin.</span><span class="sxs-lookup"><span data-stu-id="52ba6-140">Trailing byte.</span></span> |
| <span data-ttu-id="52ba6-141">**COMMON_LVB_GRID_HORIZONTAL**`0x0400`</span><span class="sxs-lookup"><span data-stu-id="52ba6-141">**COMMON_LVB_GRID_HORIZONTAL** `0x0400`</span></span> | <span data-ttu-id="52ba6-142">Horizontal supérieur.</span><span class="sxs-lookup"><span data-stu-id="52ba6-142">Top horizontal.</span></span> |
| <span data-ttu-id="52ba6-143">**COMMON_LVB_GRID_LVERTICAL**`0x0800`</span><span class="sxs-lookup"><span data-stu-id="52ba6-143">**COMMON_LVB_GRID_LVERTICAL** `0x0800`</span></span> | <span data-ttu-id="52ba6-144">Vertical gauche.</span><span class="sxs-lookup"><span data-stu-id="52ba6-144">Left vertical.</span></span> |
| <span data-ttu-id="52ba6-145">**COMMON_LVB_GRID_RVERTICAL**`0x1000`</span><span class="sxs-lookup"><span data-stu-id="52ba6-145">**COMMON_LVB_GRID_RVERTICAL** `0x1000`</span></span> | <span data-ttu-id="52ba6-146">Verticale droite.</span><span class="sxs-lookup"><span data-stu-id="52ba6-146">Right vertical.</span></span> |
| <span data-ttu-id="52ba6-147">**COMMON_LVB_REVERSE_VIDEO**`0x4000`</span><span class="sxs-lookup"><span data-stu-id="52ba6-147">**COMMON_LVB_REVERSE_VIDEO** `0x4000`</span></span> | <span data-ttu-id="52ba6-148">Attribut de premier plan et d’arrière-plan inversé.</span><span class="sxs-lookup"><span data-stu-id="52ba6-148">Reverse foreground and background attribute.</span></span> |
| <span data-ttu-id="52ba6-149">**COMMON_LVB_UNDERSCORE**`0x8000`</span><span class="sxs-lookup"><span data-stu-id="52ba6-149">**COMMON_LVB_UNDERSCORE** `0x8000`</span></span> | <span data-ttu-id="52ba6-150">Soulignement.</span><span class="sxs-lookup"><span data-stu-id="52ba6-150">Underscore.</span></span> |

## <a name="examples"></a><span data-ttu-id="52ba6-151">Exemples</span><span class="sxs-lookup"><span data-stu-id="52ba6-151">Examples</span></span>

<span data-ttu-id="52ba6-152">Pour obtenir un exemple, consultez [défilement du contenu d’une mémoire tampon d’écran](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="52ba6-152">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="52ba6-153">Spécifications</span><span class="sxs-lookup"><span data-stu-id="52ba6-153">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="52ba6-154">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="52ba6-154">Minimum supported client</span></span> | <span data-ttu-id="52ba6-155">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="52ba6-155">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="52ba6-156">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="52ba6-156">Minimum supported server</span></span> | <span data-ttu-id="52ba6-157">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="52ba6-157">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="52ba6-158">En-tête</span><span class="sxs-lookup"><span data-stu-id="52ba6-158">Header</span></span> | <span data-ttu-id="52ba6-159">WinCon. h (inclure Windows. h)</span><span class="sxs-lookup"><span data-stu-id="52ba6-159">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="52ba6-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52ba6-160">See also</span></span>

[<span data-ttu-id="52ba6-161">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="52ba6-161">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="52ba6-162">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="52ba6-162">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="52ba6-163">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="52ba6-163">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)
