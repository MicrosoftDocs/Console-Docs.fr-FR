---
title: Structure CONSOLE_FONT_INFO
description: Consultez les informations de référence sur la structure CONSOLE_FONT_INFO, qui contient l’index et la taille d’une police de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: c4218c53eacd95d67f3dc9056f5a1024ac1a8ab0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059333"
---
# <a name="console_font_info-structure"></a><span data-ttu-id="67e89-104">Structure des informations de \_ police de la console \_</span><span class="sxs-lookup"><span data-stu-id="67e89-104">CONSOLE\_FONT\_INFO structure</span></span>


<span data-ttu-id="67e89-105">Contient des informations pour une police de console.</span><span class="sxs-lookup"><span data-stu-id="67e89-105">Contains information for a console font.</span></span>

<a name="syntax"></a><span data-ttu-id="67e89-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67e89-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

<a name="members"></a><span data-ttu-id="67e89-107">Membres</span><span class="sxs-lookup"><span data-stu-id="67e89-107">Members</span></span>
-------

<span data-ttu-id="67e89-108">**nFont**</span><span class="sxs-lookup"><span data-stu-id="67e89-108">**nFont**</span></span>  
<span data-ttu-id="67e89-109">Index de la police dans la table des polices de la console du système.</span><span class="sxs-lookup"><span data-stu-id="67e89-109">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="67e89-110">**dwFontSize**</span><span class="sxs-lookup"><span data-stu-id="67e89-110">**dwFontSize**</span></span>  
<span data-ttu-id="67e89-111">Structure de [**repère**](coord-str.md) qui contient la largeur et la hauteur de chaque caractère de la police, en unités logiques.</span><span class="sxs-lookup"><span data-stu-id="67e89-111">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="67e89-112">Le membre **X** contient la largeur, tandis que le membre **Y** contient la hauteur.</span><span class="sxs-lookup"><span data-stu-id="67e89-112">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<a name="remarks"></a><span data-ttu-id="67e89-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="67e89-113">Remarks</span></span>
-------

<span data-ttu-id="67e89-114">Pour obtenir la taille de la police, transmettez l’index de la police à la fonction [**GetConsoleFontSize**](getconsolefontsize.md) .</span><span class="sxs-lookup"><span data-stu-id="67e89-114">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

<a name="requirements"></a><span data-ttu-id="67e89-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="67e89-115">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="67e89-116">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="67e89-116">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="67e89-117">Windows XP [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="67e89-117">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="67e89-118">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="67e89-118">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="67e89-119">Windows Server 2003 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="67e89-119">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="67e89-120">En-tête</span><span class="sxs-lookup"><span data-stu-id="67e89-120">Header</span></span></p></td>
<td><span data-ttu-id="67e89-121">Wincon. h (inclure Windows. h)</span><span class="sxs-lookup"><span data-stu-id="67e89-121">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="67e89-122"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67e89-122"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="67e89-123">**COORDONNÉES**</span><span class="sxs-lookup"><span data-stu-id="67e89-123">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="67e89-124">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="67e89-124">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)

 

 




