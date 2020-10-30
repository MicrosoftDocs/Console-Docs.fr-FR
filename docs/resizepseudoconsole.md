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
ms.openlocfilehash: 0d5a4ff954c8ebea688573f23d3981ee9c5d7d2a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037537"
---
# <a name="resizepseudoconsole-function"></a><span data-ttu-id="91e51-104">ResizePseudoConsole fonction)</span><span class="sxs-lookup"><span data-stu-id="91e51-104">ResizePseudoConsole function</span></span>

<span data-ttu-id="91e51-105">Redimensionne les mémoires tampons internes pour un pseudoconsole à la taille donnée.</span><span class="sxs-lookup"><span data-stu-id="91e51-105">Resizes the internal buffers for a pseudoconsole to the given size.</span></span>

## <a name="syntax"></a><span data-ttu-id="91e51-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91e51-106">Syntax</span></span>

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

## <a name="parameters"></a><span data-ttu-id="91e51-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="91e51-107">Parameters</span></span>

<span data-ttu-id="91e51-108">*hPC* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="91e51-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="91e51-109">Handle d’un pseudoconsole actif tel qu’il est ouvert par [CreatePseudoConsole](createpseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="91e51-109">A handle to an active pseudoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

<span data-ttu-id="91e51-110">*taille* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="91e51-110">*size* \[in\]</span></span>  
<span data-ttu-id="91e51-111">Dimensions de la fenêtre/mémoire tampon en nombre de caractères qui seront utilisés pour la mémoire tampon interne de ce pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="91e51-111">The dimensions of the window/buffer in count of characters that will be used for the internal buffer of this pseudoconsole.</span></span>

## <a name="return-value"></a><span data-ttu-id="91e51-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="91e51-112">Return value</span></span>

<span data-ttu-id="91e51-113">Type : **HRESULT**</span><span class="sxs-lookup"><span data-stu-id="91e51-113">Type: **HRESULT**</span></span>

<span data-ttu-id="91e51-114">Si cette méthode est réussie, elle retourne **S_OK** .</span><span class="sxs-lookup"><span data-stu-id="91e51-114">If this method succeeds, it returns **S_OK** .</span></span> <span data-ttu-id="91e51-115">Sinon, elle retourne un code d’erreur **HRESULT** .</span><span class="sxs-lookup"><span data-stu-id="91e51-115">Otherwise, it returns an **HRESULT** error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="91e51-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="91e51-116">Remarks</span></span>

<span data-ttu-id="91e51-117">Cette fonction peut redimensionner les mémoires tampons internes de la session pseudoconsole pour qu’elles correspondent à la taille de la fenêtre/de la mémoire tampon utilisée pour l’affichage sur l’extrémité terminal.</span><span class="sxs-lookup"><span data-stu-id="91e51-117">This function can resize the internal buffers in the pseudoconsole session to match the window/buffer size being used for display on the terminal end.</span></span> <span data-ttu-id="91e51-118">Cela garantit que les applications CUI (attached Command-Line interface) utilisant les fonctions de la [console](console-functions.md) pour communiquer auront les dimensions correctes retournées dans leurs appels.</span><span class="sxs-lookup"><span data-stu-id="91e51-118">This ensures that attached Command-Line Interface (CUI) applications using the [Console Functions](console-functions.md) to communicate will have the correct dimensions returned in their calls.</span></span>

## <a name="requirements"></a><span data-ttu-id="91e51-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="91e51-119">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="91e51-120">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="91e51-120">Minimum supported client</span></span> | <span data-ttu-id="91e51-121">Windows 10 octobre 2018 mise à jour (version 1809) \[ applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="91e51-121">Windows 10 October 2018 Update (version 1809) \[desktop apps only\]</span></span> |
| <span data-ttu-id="91e51-122">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="91e51-122">Minimum supported server</span></span> | <span data-ttu-id="91e51-123">Applications de bureau Windows Server 2019 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="91e51-123">Windows Server 2019 \[desktop apps only\]</span></span> |
| <span data-ttu-id="91e51-124">En-tête</span><span class="sxs-lookup"><span data-stu-id="91e51-124">Header</span></span> | <span data-ttu-id="91e51-125">ConsoleApi. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="91e51-125">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="91e51-126">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="91e51-126">Library</span></span> | <span data-ttu-id="91e51-127">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="91e51-127">Kernel32.lib</span></span> |
| <span data-ttu-id="91e51-128">DLL</span><span class="sxs-lookup"><span data-stu-id="91e51-128">DLL</span></span> | <span data-ttu-id="91e51-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="91e51-129">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="91e51-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91e51-130">See also</span></span>

[<span data-ttu-id="91e51-131">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="91e51-131">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="91e51-132">**CreatePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="91e51-132">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="91e51-133">**ClosePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="91e51-133">**ClosePseudoConsole**</span></span>](closepseudoconsole.md)
