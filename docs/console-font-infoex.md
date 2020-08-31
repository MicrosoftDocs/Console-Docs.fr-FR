---
title: Structure CONSOLE_FONT_INFOEX
description: Consultez les informations de référence sur la structure CONSOLE_FONT_INFOEX, qui contient des informations étendues pour une police de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/CONSOLE_FONT_INFOEX
- wincon/CONSOLE_FONT_INFOEX
- CONSOLE_FONT_INFOEX
- consoleapi3/PCONSOLE_FONT_INFOEX
- wincon/PCONSOLE_FONT_INFOEX
- PCONSOLE_FONT_INFOEX
MS-HAID:
- base.console\_font\_infoex
- consoles.console\_font\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e9a087e1-264d-4d48-8adb-771a0e35b511
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFOEX
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 12977e288a63397c581143683047239e4d410eec
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059320"
---
# <a name="console_font_infoex-structure"></a><span data-ttu-id="2cc99-104">Structure de la police de la CONSOLE \_ \_ INFOEX</span><span class="sxs-lookup"><span data-stu-id="2cc99-104">CONSOLE\_FONT\_INFOEX structure</span></span>


<span data-ttu-id="2cc99-105">Contient des informations étendues pour une police de console.</span><span class="sxs-lookup"><span data-stu-id="2cc99-105">Contains extended information for a console font.</span></span>

<a name="syntax"></a><span data-ttu-id="2cc99-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cc99-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_FONT_INFOEX {
  ULONG cbSize;
  DWORD nFont;
  COORD dwFontSize;
  UINT  FontFamily;
  UINT  FontWeight;
  WCHAR FaceName[LF_FACESIZE];
} CONSOLE_FONT_INFOEX, *PCONSOLE_FONT_INFOEX;
```

<a name="members"></a><span data-ttu-id="2cc99-107">Membres</span><span class="sxs-lookup"><span data-stu-id="2cc99-107">Members</span></span>
-------

<span data-ttu-id="2cc99-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="2cc99-108">**cbSize**</span></span>  
<span data-ttu-id="2cc99-109">Taille de cette structure, en octets.</span><span class="sxs-lookup"><span data-stu-id="2cc99-109">The size of this structure, in bytes.</span></span> <span data-ttu-id="2cc99-110">Ce membre doit être défini sur `sizeof(CONSOLE_FONT_INFOEX)` avant d’appeler [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) , sinon il échouera.</span><span class="sxs-lookup"><span data-stu-id="2cc99-110">This member must be set to `sizeof(CONSOLE_FONT_INFOEX)` before calling [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) or it will fail.</span></span>

<span data-ttu-id="2cc99-111">**nFont**</span><span class="sxs-lookup"><span data-stu-id="2cc99-111">**nFont**</span></span>  
<span data-ttu-id="2cc99-112">Index de la police dans la table des polices de la console du système.</span><span class="sxs-lookup"><span data-stu-id="2cc99-112">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="2cc99-113">**dwFontSize**</span><span class="sxs-lookup"><span data-stu-id="2cc99-113">**dwFontSize**</span></span>  
<span data-ttu-id="2cc99-114">Structure de [**repère**](coord-str.md) qui contient la largeur et la hauteur de chaque caractère de la police, en unités logiques.</span><span class="sxs-lookup"><span data-stu-id="2cc99-114">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="2cc99-115">Le membre **X** contient la largeur, tandis que le membre **Y** contient la hauteur.</span><span class="sxs-lookup"><span data-stu-id="2cc99-115">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="2cc99-116">**FontFamily**</span><span class="sxs-lookup"><span data-stu-id="2cc99-116">**FontFamily**</span></span>  
<span data-ttu-id="2cc99-117">L’espacement de la police et la famille.</span><span class="sxs-lookup"><span data-stu-id="2cc99-117">The font pitch and family.</span></span> <span data-ttu-id="2cc99-118">Pour plus d’informations sur les valeurs possibles de ce membre, consultez la description du membre **tmPitchAndFamily** de la structure [**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132) .</span><span class="sxs-lookup"><span data-stu-id="2cc99-118">For information about the possible values for this member, see the description of the **tmPitchAndFamily** member of the [**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132) structure.</span></span>

<span data-ttu-id="2cc99-119">**FontWeight**</span><span class="sxs-lookup"><span data-stu-id="2cc99-119">**FontWeight**</span></span>  
<span data-ttu-id="2cc99-120">Épaisseur de la police.</span><span class="sxs-lookup"><span data-stu-id="2cc99-120">The font weight.</span></span> <span data-ttu-id="2cc99-121">Le poids peut être compris entre 100 et 1000, par multiples de 100.</span><span class="sxs-lookup"><span data-stu-id="2cc99-121">The weight can range from 100 to 1000, in multiples of 100.</span></span> <span data-ttu-id="2cc99-122">Par exemple, le poids normal est 400, tandis que 700 est gras.</span><span class="sxs-lookup"><span data-stu-id="2cc99-122">For example, the normal weight is 400, while 700 is bold.</span></span>

<span data-ttu-id="2cc99-123">**FaceName**</span><span class="sxs-lookup"><span data-stu-id="2cc99-123">**FaceName**</span></span>  
<span data-ttu-id="2cc99-124">Nom du type de caractères (Courier ou Arial, par exemple).</span><span class="sxs-lookup"><span data-stu-id="2cc99-124">The name of the typeface (such as Courier or Arial).</span></span>

<a name="remarks"></a><span data-ttu-id="2cc99-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="2cc99-125">Remarks</span></span>
-------

<span data-ttu-id="2cc99-126">Pour obtenir la taille de la police, transmettez l’index de la police à la fonction [**GetConsoleFontSize**](getconsolefontsize.md) .</span><span class="sxs-lookup"><span data-stu-id="2cc99-126">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

<a name="requirements"></a><span data-ttu-id="2cc99-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2cc99-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="2cc99-128">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="2cc99-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="2cc99-129">Windows Vista [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="2cc99-129">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2cc99-130">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="2cc99-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="2cc99-131">Windows Server 2008 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="2cc99-131">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2cc99-132">En-tête</span><span class="sxs-lookup"><span data-stu-id="2cc99-132">Header</span></span></p></td>
<td><span data-ttu-id="2cc99-133">Wincon. h (inclure Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2cc99-133">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="2cc99-134"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cc99-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="2cc99-135">**GetCurrentConsoleFontEx**</span><span class="sxs-lookup"><span data-stu-id="2cc99-135">**GetCurrentConsoleFontEx**</span></span>](getcurrentconsolefontex.md)

 

 




