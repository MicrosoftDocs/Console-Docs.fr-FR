---
title: ResizePseudoConsole fonction)
description: Consultez les informations de référence sur la fonction ResizePseudoConsole, qui redimensionne les mémoires tampons internes pour un pseudoconsole à la taille donnée.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API console, conpty, pseudoconsole
f1_keywords:
- consoleapi/ResizePseudoConsole
- ResizePseudoConsole
topic_type:
- apiref
api_name:
- ResizePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a4f6ff773538eda4d4c84c4b0bac2e647f6b80d8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059444"
---
# <a name="resizepseudoconsole-function"></a><span data-ttu-id="7285c-104">ResizePseudoConsole fonction)</span><span class="sxs-lookup"><span data-stu-id="7285c-104">ResizePseudoConsole function</span></span>


<span data-ttu-id="7285c-105">Redimensionne les mémoires tampons internes pour un pseudoconsole à la taille donnée.</span><span class="sxs-lookup"><span data-stu-id="7285c-105">Resizes the internal buffers for a pseudoconsole to the given size.</span></span>

<a name="syntax"></a><span data-ttu-id="7285c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7285c-106">Syntax</span></span>
------

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

<a name="parameters"></a><span data-ttu-id="7285c-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7285c-107">Parameters</span></span>
----------

<span data-ttu-id="7285c-108">*hPC* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="7285c-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="7285c-109">Handle d’un psuedoconsole actif tel qu’il est ouvert par [CreatePseudoConsole](createpseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="7285c-109">A handle to an active psuedoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

<span data-ttu-id="7285c-110">*taille* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="7285c-110">*size* \[in\]</span></span>  
<span data-ttu-id="7285c-111">Dimensions de la fenêtre/mémoire tampon en nombre de caractères qui seront utilisés pour la mémoire tampon interne de ce pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="7285c-111">The dimensions of the window/buffer in count of characters that will be used for the internal buffer of this pseudoconsole.</span></span> 

<a name="return-value"></a><span data-ttu-id="7285c-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="7285c-112">Return value</span></span>
------------

<span data-ttu-id="7285c-113">Type : **HRESULT**</span><span class="sxs-lookup"><span data-stu-id="7285c-113">Type: **HRESULT**</span></span>

<span data-ttu-id="7285c-114">Si cette méthode est réussie, elle retourne **S_OK**.</span><span class="sxs-lookup"><span data-stu-id="7285c-114">If this method succeeds, it returns **S_OK**.</span></span> <span data-ttu-id="7285c-115">Sinon, elle retourne un code d’erreur **HRESULT** .</span><span class="sxs-lookup"><span data-stu-id="7285c-115">Otherwise, it returns an **HRESULT** error code.</span></span>

<a name="remarks"></a><span data-ttu-id="7285c-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="7285c-116">Remarks</span></span>
-------

<span data-ttu-id="7285c-117">Cette fonction peut redimensionner les mémoires tampons internes de la session pseudoconsole pour qu’elles correspondent à la taille de la fenêtre/de la mémoire tampon utilisée pour l’affichage sur l’extrémité terminal.</span><span class="sxs-lookup"><span data-stu-id="7285c-117">This function can resize the internal buffers in the pseudoconsole session to match the window/buffer size being used for display on the terminal end.</span></span> <span data-ttu-id="7285c-118">Cela permet de s’assurer que les applications de l’interface de ligne de commande (CUI) attachées utilisant les fonctions de la [console](console-functions.md) pour communiquer auront les dimensions correctes retournées dans leurs appels.</span><span class="sxs-lookup"><span data-stu-id="7285c-118">This ensures that attached Command-Line Interface (CUI) applications using the [Console Functions](console-functions.md) to communicate will have the correct dimensions returned in their calls.</span></span>

<a name="requirements"></a><span data-ttu-id="7285c-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7285c-119">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="7285c-120">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7285c-120">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="7285c-121">Windows 10 1809 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="7285c-121">Windows 10 1809 [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7285c-122">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7285c-122">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="7285c-123">Windows Server 2019 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="7285c-123">Windows Server 2019 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7285c-124">En-tête</span><span class="sxs-lookup"><span data-stu-id="7285c-124">Header</span></span></p></td>
<td><span data-ttu-id="7285c-125">ConsoleApi. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="7285c-125">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7285c-126">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="7285c-126">Library</span></span></p></td>
<td><span data-ttu-id="7285c-127">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="7285c-127">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7285c-128">DLL</span><span class="sxs-lookup"><span data-stu-id="7285c-128">DLL</span></span></p></td>
<td><span data-ttu-id="7285c-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7285c-129">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="7285c-130"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7285c-130"><span id="see_also"></span>See also</span></span>

[<span data-ttu-id="7285c-131">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="7285c-131">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="7285c-132">**CreatePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="7285c-132">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="7285c-133">**ClosePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="7285c-133">**ClosePseudoConsole**</span></span>](closepseudoconsole.md)
