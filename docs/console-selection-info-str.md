---
title: Structure CONSOLE_SELECTION_INFO
description: Consultez les informations de référence sur la structure CONSOLE_SELECTION_INFO, qui contient des informations pour une sélection de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/CONSOLE_SELECTION_INFO
- wincon/CONSOLE_SELECTION_INFO
- CONSOLE_SELECTION_INFO
- consoleapi3/PCONSOLE_SELECTION_INFO
- wincon/PCONSOLE_SELECTION_INFO
- PCONSOLE_SELECTION_INFO
MS-HAID:
- '\_win32\_console\_selection\_info\_str'
- base.console\_selection\_info\_str
- consoles.console\_selection\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9530b249-8db4-4516-9cc8-2b452c6751f9
topic_type:
- apiref
api_name:
- CONSOLE_SELECTION_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: aaf1cfaea2a8822c142aab87f6dcf1b022b7160c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038367"
---
# <a name="console_selection_info-structure"></a><span data-ttu-id="873fe-104">Structure des informations de \_ sélection de la console \_</span><span class="sxs-lookup"><span data-stu-id="873fe-104">CONSOLE\_SELECTION\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="873fe-105">Contient des informations pour une sélection de la console.</span><span class="sxs-lookup"><span data-stu-id="873fe-105">Contains information for a console selection.</span></span>

## <a name="syntax"></a><span data-ttu-id="873fe-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="873fe-106">Syntax</span></span>

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

## <a name="members"></a><span data-ttu-id="873fe-107">Membres</span><span class="sxs-lookup"><span data-stu-id="873fe-107">Members</span></span>

<span data-ttu-id="873fe-108">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="873fe-108">**dwFlags**</span></span>  
<span data-ttu-id="873fe-109">Indicateur de sélection.</span><span class="sxs-lookup"><span data-stu-id="873fe-109">The selection indicator.</span></span> <span data-ttu-id="873fe-110">Ce membre peut être une ou plusieurs des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="873fe-110">This member can be one or more of the following values.</span></span>

| <span data-ttu-id="873fe-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="873fe-111">Value</span></span> | <span data-ttu-id="873fe-112">Signification</span><span class="sxs-lookup"><span data-stu-id="873fe-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="873fe-113">**CONSOLE_MOUSE_DOWN** 0x0008</span><span class="sxs-lookup"><span data-stu-id="873fe-113">**CONSOLE_MOUSE_DOWN** 0x0008</span></span> | <span data-ttu-id="873fe-114">Le bouton de la souris est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="873fe-114">Mouse is down.</span></span> <span data-ttu-id="873fe-115">L’utilisateur ajuste activement le rectangle de sélection à l’aide d’une souris.</span><span class="sxs-lookup"><span data-stu-id="873fe-115">The user is actively adjusting the selection rectangle with a mouse.</span></span> |
| <span data-ttu-id="873fe-116">**CONSOLE_MOUSE_SELECTION** 0x0004</span><span class="sxs-lookup"><span data-stu-id="873fe-116">**CONSOLE_MOUSE_SELECTION** 0x0004</span></span> | <span data-ttu-id="873fe-117">Sélection à l’aide de la souris.</span><span class="sxs-lookup"><span data-stu-id="873fe-117">Selecting with the mouse.</span></span> <span data-ttu-id="873fe-118">Si la valeur est OFF, l’utilisateur est `conhost.exe` sélectionné pour le mode de marquage avec le clavier.</span><span class="sxs-lookup"><span data-stu-id="873fe-118">If off, the user is operating `conhost.exe` mark mode selection with the keyboard.</span></span> |
| <span data-ttu-id="873fe-119">**CONSOLE_NO_SELECTION** 0x0000</span><span class="sxs-lookup"><span data-stu-id="873fe-119">**CONSOLE_NO_SELECTION** 0x0000</span></span> | <span data-ttu-id="873fe-120">Aucune sélection.</span><span class="sxs-lookup"><span data-stu-id="873fe-120">No selection.</span></span> |
| <span data-ttu-id="873fe-121">**CONSOLE_SELECTION_IN_PROGRESS** 0x0001</span><span class="sxs-lookup"><span data-stu-id="873fe-121">**CONSOLE_SELECTION_IN_PROGRESS** 0x0001</span></span> | <span data-ttu-id="873fe-122">La sélection a commencé.</span><span class="sxs-lookup"><span data-stu-id="873fe-122">Selection has begun.</span></span> <span data-ttu-id="873fe-123">Si vous sélectionnez une souris, cela ne se produit généralement pas sans l' `CONSOLE_SELECTION_NOT_EMPTY` indicateur.</span><span class="sxs-lookup"><span data-stu-id="873fe-123">If a mouse selection, this will typically not occur without the `CONSOLE_SELECTION_NOT_EMPTY` flag.</span></span> <span data-ttu-id="873fe-124">Dans le cas d’une sélection de clavier, cela peut se produire lorsque le mode marque a été entré, mais que l’utilisateur accède toujours à la position initiale.</span><span class="sxs-lookup"><span data-stu-id="873fe-124">If a keyboard selection, this may occur when mark mode has been entered but the user is still navigating to the initial position.</span></span> |
| <span data-ttu-id="873fe-125">**CONSOLE_SELECTION_NOT_EMPTY** 0x0002</span><span class="sxs-lookup"><span data-stu-id="873fe-125">**CONSOLE_SELECTION_NOT_EMPTY** 0x0002</span></span> | <span data-ttu-id="873fe-126">Le rectangle de sélection n’est pas vide.</span><span class="sxs-lookup"><span data-stu-id="873fe-126">Selection rectangle not empty.</span></span> <span data-ttu-id="873fe-127">La charge utile de *dwSelectionAnchor* et *srSelection* est valide.</span><span class="sxs-lookup"><span data-stu-id="873fe-127">The payload of *dwSelectionAnchor* and *srSelection* are valid.</span></span>  |

<span data-ttu-id="873fe-128">**dwSelectionAnchor**</span><span class="sxs-lookup"><span data-stu-id="873fe-128">**dwSelectionAnchor**</span></span>  
<span data-ttu-id="873fe-129">Structure de [**repère**](coord-str.md) qui spécifie l’ancre de sélection, en caractères.</span><span class="sxs-lookup"><span data-stu-id="873fe-129">A [**COORD**](coord-str.md) structure that specifies the selection anchor, in characters.</span></span>

<span data-ttu-id="873fe-130">**srSelection**</span><span class="sxs-lookup"><span data-stu-id="873fe-130">**srSelection**</span></span>  
<span data-ttu-id="873fe-131">[**Petite structure \_ Rect**](small-rect-str.md) qui spécifie le rectangle de sélection.</span><span class="sxs-lookup"><span data-stu-id="873fe-131">A [**SMALL\_RECT**](small-rect-str.md) structure that specifies the selection rectangle.</span></span>

## <a name="requirements"></a><span data-ttu-id="873fe-132">Spécifications</span><span class="sxs-lookup"><span data-stu-id="873fe-132">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="873fe-133">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="873fe-133">Minimum supported client</span></span> | <span data-ttu-id="873fe-134">Applications de \[ Bureau Windows XP uniquement\]</span><span class="sxs-lookup"><span data-stu-id="873fe-134">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="873fe-135">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="873fe-135">Minimum supported server</span></span> | <span data-ttu-id="873fe-136">Applications de bureau Windows Server 2003 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="873fe-136">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="873fe-137">En-tête</span><span class="sxs-lookup"><span data-stu-id="873fe-137">Header</span></span> | <span data-ttu-id="873fe-138">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="873fe-138">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="873fe-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="873fe-139">See also</span></span>

[<span data-ttu-id="873fe-140">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="873fe-140">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="873fe-141">**GetConsoleSelectionInfo**</span><span class="sxs-lookup"><span data-stu-id="873fe-141">**GetConsoleSelectionInfo**</span></span>](getconsoleselectioninfo.md)

[<span data-ttu-id="873fe-142">**PETIT \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="873fe-142">**SMALL\_RECT**</span></span>](small-rect-str.md)
