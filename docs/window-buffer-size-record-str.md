---
title: Structure WINDOW_BUFFER_SIZE_RECORD
description: Consultez les informations de référence sur la structure WINDOW_BUFFER_SIZE_RECORD, qui décrit une modification de la taille de la mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- wincontypes/WINDOW_BUFFER_SIZE_RECORD
- wincon/WINDOW_BUFFER_SIZE_RECORD
- WINDOW_BUFFER_SIZE_RECORD
- wincontypes/PWINDOW_BUFFER_SIZE_RECORD
- wincon/PWINDOW_BUFFER_SIZE_RECORD
- PWINDOW_BUFFER_SIZE_RECORD
MS-HAID:
- '\_win32\_window\_buffer\_size\_record\_str'
- base.window\_buffer\_size\_record\_str
- consoles.window\_buffer\_size\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f2875e8-aa09-455b-a923-7cc388525b98
topic_type:
- apiref
api_name:
- WINDOW_BUFFER_SIZE_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 0041c4390fe331302df458965faec0ace2d1888f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060543"
---
# <a name="window_buffer_size_record-structure"></a><span data-ttu-id="2cf50-104">\_Structure d' \_ enregistrement de taille de mémoire tampon de fenêtre \_</span><span class="sxs-lookup"><span data-stu-id="2cf50-104">WINDOW\_BUFFER\_SIZE\_RECORD structure</span></span>


<span data-ttu-id="2cf50-105">Décrit une modification de la taille de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="2cf50-105">Describes a change in the size of the console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="2cf50-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cf50-106">Syntax</span></span>
------

```C
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

<a name="members"></a><span data-ttu-id="2cf50-107">Membres</span><span class="sxs-lookup"><span data-stu-id="2cf50-107">Members</span></span>
-------

<span data-ttu-id="2cf50-108">**dwSize nul**</span><span class="sxs-lookup"><span data-stu-id="2cf50-108">**dwSize**</span></span>  
<span data-ttu-id="2cf50-109">Structure de [**repère**](coord-str.md) qui contient la taille de la mémoire tampon de l’écran de la console, dans les colonnes et les lignes des cellules de caractères.</span><span class="sxs-lookup"><span data-stu-id="2cf50-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character cell columns and rows.</span></span>

<a name="remarks"></a><span data-ttu-id="2cf50-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="2cf50-110">Remarks</span></span>
-------

<span data-ttu-id="2cf50-111">Les événements de taille de mémoire tampon sont placés dans la mémoire tampon d’entrée lorsque la console est en mode compatible avec les fenêtres (**activer l' \_ \_ entrée**de la fenêtre).</span><span class="sxs-lookup"><span data-stu-id="2cf50-111">Buffer size events are placed in the input buffer when the console is in window-aware mode (**ENABLE\_WINDOW\_INPUT**).</span></span>

<a name="examples"></a><span data-ttu-id="2cf50-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="2cf50-112">Examples</span></span>
--------

<span data-ttu-id="2cf50-113">Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="2cf50-113">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="2cf50-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2cf50-114">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="2cf50-115">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="2cf50-115">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="2cf50-116">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="2cf50-116">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2cf50-117">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="2cf50-117">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="2cf50-118">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="2cf50-118">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2cf50-119">En-tête</span><span class="sxs-lookup"><span data-stu-id="2cf50-119">Header</span></span></p></td>
<td><span data-ttu-id="2cf50-120">WinConTypes. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2cf50-120">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="2cf50-121"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cf50-121"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="2cf50-122">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="2cf50-122">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="2cf50-123">**enregistrement d’entrée \_**</span><span class="sxs-lookup"><span data-stu-id="2cf50-123">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="2cf50-124">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="2cf50-124">**ReadConsoleInput**</span></span>](readconsoleinput.md)

 

 




