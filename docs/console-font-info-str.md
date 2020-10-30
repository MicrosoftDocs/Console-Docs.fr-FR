---
title: Structure CONSOLE_FONT_INFO
description: Consultez les informations de référence sur la structure CONSOLE_FONT_INFO, qui contient l’index et la taille d’une police de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- wincontypes/CONSOLE_FONT_INFO
- wincon/CONSOLE_FONT_INFO
- CONSOLE_FONT_INFO
- wincontypes/PCONSOLE_FONT_INFO
- wincon/PCONSOLE_FONT_INFO
- PCONSOLE_FONT_INFO
MS-HAID:
- '\_win32\_console\_font\_info\_str'
- base.console\_font\_info\_str
- consoles.console\_font\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 380b8183-1964-46f2-a511-01f39f21f5c5
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 6c437e626ed6d207da4672a3a5ea60c2ea0ee008
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037137"
---
# <a name="console_font_info-structure"></a><span data-ttu-id="e8847-104">Structure des informations de \_ police de la console \_</span><span class="sxs-lookup"><span data-stu-id="e8847-104">CONSOLE\_FONT\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="e8847-105">Contient des informations pour une police de console.</span><span class="sxs-lookup"><span data-stu-id="e8847-105">Contains information for a console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8847-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8847-106">Syntax</span></span>

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

## <a name="members"></a><span data-ttu-id="e8847-107">Membres</span><span class="sxs-lookup"><span data-stu-id="e8847-107">Members</span></span>

<span data-ttu-id="e8847-108">**nFont**</span><span class="sxs-lookup"><span data-stu-id="e8847-108">**nFont**</span></span>  
<span data-ttu-id="e8847-109">Index de la police dans la table des polices de la console du système.</span><span class="sxs-lookup"><span data-stu-id="e8847-109">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="e8847-110">**dwFontSize**</span><span class="sxs-lookup"><span data-stu-id="e8847-110">**dwFontSize**</span></span>  
<span data-ttu-id="e8847-111">Structure de [**repère**](coord-str.md) qui contient la largeur et la hauteur de chaque caractère de la police, en unités logiques.</span><span class="sxs-lookup"><span data-stu-id="e8847-111">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="e8847-112">Le membre **X** contient la largeur, tandis que le membre **Y** contient la hauteur.</span><span class="sxs-lookup"><span data-stu-id="e8847-112">The **X** member contains the width, while the **Y** member contains the height.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8847-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="e8847-113">Remarks</span></span>

<span data-ttu-id="e8847-114">Pour obtenir la taille de la police, transmettez l’index de la police à la fonction [**GetConsoleFontSize**](getconsolefontsize.md) .</span><span class="sxs-lookup"><span data-stu-id="e8847-114">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8847-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e8847-115">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e8847-116">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="e8847-116">Minimum supported client</span></span> | <span data-ttu-id="e8847-117">Applications de \[ Bureau Windows XP uniquement\]</span><span class="sxs-lookup"><span data-stu-id="e8847-117">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="e8847-118">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="e8847-118">Minimum supported server</span></span> | <span data-ttu-id="e8847-119">Applications de bureau Windows Server 2003 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="e8847-119">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="e8847-120">En-tête</span><span class="sxs-lookup"><span data-stu-id="e8847-120">Header</span></span> | <span data-ttu-id="e8847-121">WinCon. h (inclure Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e8847-121">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="e8847-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8847-122">See also</span></span>

[<span data-ttu-id="e8847-123">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="e8847-123">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="e8847-124">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="e8847-124">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)
