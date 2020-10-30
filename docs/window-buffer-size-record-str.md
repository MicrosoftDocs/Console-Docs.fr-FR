---
title: WINDOW_BUFFER_SIZE_RECORD, structure
description: Consultez les informations de référence sur la structure WINDOW_BUFFER_SIZE_RECORD, qui décrit une modification de la taille de la mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 355482dfd162e2c29944d53e5b17b0315ea15950
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039267"
---
# <a name="window_buffer_size_record-structure"></a><span data-ttu-id="1fff2-104">\_Structure d' \_ enregistrement de taille de mémoire tampon de fenêtre \_</span><span class="sxs-lookup"><span data-stu-id="1fff2-104">WINDOW\_BUFFER\_SIZE\_RECORD structure</span></span>

<span data-ttu-id="1fff2-105">Décrit une modification de la taille de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="1fff2-105">Describes a change in the size of the console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="1fff2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fff2-106">Syntax</span></span>

```C
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

## <a name="members"></a><span data-ttu-id="1fff2-107">Membres</span><span class="sxs-lookup"><span data-stu-id="1fff2-107">Members</span></span>

<span data-ttu-id="1fff2-108">**dwSize nul**</span><span class="sxs-lookup"><span data-stu-id="1fff2-108">**dwSize**</span></span>  
<span data-ttu-id="1fff2-109">Structure de [**repère**](coord-str.md) qui contient la taille de la mémoire tampon de l’écran de la console, dans les colonnes et les lignes des cellules de caractères.</span><span class="sxs-lookup"><span data-stu-id="1fff2-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character cell columns and rows.</span></span>

## <a name="remarks"></a><span data-ttu-id="1fff2-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="1fff2-110">Remarks</span></span>

<span data-ttu-id="1fff2-111">Les événements de taille de mémoire tampon sont placés dans la mémoire tampon d’entrée lorsque la console est en mode compatible avec les fenêtres ( **activer l' \_ \_ entrée** de la fenêtre).</span><span class="sxs-lookup"><span data-stu-id="1fff2-111">Buffer size events are placed in the input buffer when the console is in window-aware mode ( **ENABLE\_WINDOW\_INPUT** ).</span></span>

## <a name="examples"></a><span data-ttu-id="1fff2-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="1fff2-112">Examples</span></span>

<span data-ttu-id="1fff2-113">Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="1fff2-113">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="1fff2-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1fff2-114">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1fff2-115">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="1fff2-115">Minimum supported client</span></span> | <span data-ttu-id="1fff2-116">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="1fff2-116">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="1fff2-117">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="1fff2-117">Minimum supported server</span></span> | <span data-ttu-id="1fff2-118">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="1fff2-118">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="1fff2-119">En-tête</span><span class="sxs-lookup"><span data-stu-id="1fff2-119">Header</span></span> | <span data-ttu-id="1fff2-120">WinConTypes. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1fff2-120">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="1fff2-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fff2-121">See also</span></span>

[<span data-ttu-id="1fff2-122">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="1fff2-122">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="1fff2-123">**enregistrement d’entrée \_**</span><span class="sxs-lookup"><span data-stu-id="1fff2-123">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="1fff2-124">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="1fff2-124">**ReadConsoleInput**</span></span>](readconsoleinput.md)
