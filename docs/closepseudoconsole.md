---
title: ClosePseudoConsole fonction)
description: Consultez les informations de référence sur la fonction ClosePseudoConsole, qui ferme un pseudoconsole à partir du handle donné.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API console, conpty, pseudoconsole
topic_type:
- apiref
api_name:
- ClosePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 067fa732f5badfe46ee6391c892aa037613cb4dd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037287"
---
# <a name="closepseudoconsole-function"></a><span data-ttu-id="c3220-104">ClosePseudoConsole fonction)</span><span class="sxs-lookup"><span data-stu-id="c3220-104">ClosePseudoConsole function</span></span>

<span data-ttu-id="c3220-105">Ferme un pseudoconsole à partir du handle donné.</span><span class="sxs-lookup"><span data-stu-id="c3220-105">Closes a pseudoconsole from the given handle.</span></span>

## <a name="syntax"></a><span data-ttu-id="c3220-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3220-106">Syntax</span></span>

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC
);
```

## <a name="parameters"></a><span data-ttu-id="c3220-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c3220-107">Parameters</span></span>

<span data-ttu-id="c3220-108">*hPC* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="c3220-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="c3220-109">Handle d’un pseudoconsole actif tel qu’il est ouvert par [CreatePseudoConsole](createpseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="c3220-109">A handle to an active pseudoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

## <a name="return-value"></a><span data-ttu-id="c3220-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="c3220-110">Return value</span></span>

<span data-ttu-id="c3220-111">*Aucune*</span><span class="sxs-lookup"><span data-stu-id="c3220-111">*none*</span></span>

## <a name="remarks"></a><span data-ttu-id="c3220-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="c3220-112">Remarks</span></span>

<span data-ttu-id="c3220-113">Lors de la fermeture d’un pseudoconsole, les applications clientes attachées à la session sont également arrêtées.</span><span class="sxs-lookup"><span data-stu-id="c3220-113">Upon closing a pseudoconsole, client applications attached to the session will be terminated as well.</span></span>

<span data-ttu-id="c3220-114">Un frame peint final peut arriver sur le `hOutput` handle initialement fourni à [CreatePsuedoConsole](createpseudoconsole.md) lorsque cette API est appelée.</span><span class="sxs-lookup"><span data-stu-id="c3220-114">A final painted frame may arrive on the `hOutput` handle originally provided to [CreatePsuedoConsole](createpseudoconsole.md) when this API is called.</span></span> <span data-ttu-id="c3220-115">Il est prévu que l’appelant draine ces informations à partir de la mémoire tampon du canal de communication, puis le présente ou l’ignore.</span><span class="sxs-lookup"><span data-stu-id="c3220-115">It is expected that the caller will drain this information from the communication channel buffer and either present it or discard it.</span></span> <span data-ttu-id="c3220-116">L’échec de la vidange de la mémoire tampon peut provoquer l’attente indéfinie de l’appel de fermeture jusqu’à ce qu’il soit vidé ou que les canaux de communication soient rompus d’une autre façon.</span><span class="sxs-lookup"><span data-stu-id="c3220-116">Failure to drain the buffer may cause the Close call to wait indefinitely until it is drained or the communication channels are broken another way.</span></span>

## <a name="requirements"></a><span data-ttu-id="c3220-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c3220-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c3220-118">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="c3220-118">Minimum supported client</span></span> | <span data-ttu-id="c3220-119">Windows 10 octobre 2018 mise à jour (version 1809) \[ applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="c3220-119">Windows 10 October 2018 Update (version 1809) \[desktop apps only\]</span></span> |
| <span data-ttu-id="c3220-120">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="c3220-120">Minimum supported server</span></span> | <span data-ttu-id="c3220-121">Applications de bureau Windows Server 2019 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="c3220-121">Windows Server 2019 \[desktop apps only\]</span></span> |
| <span data-ttu-id="c3220-122">En-tête</span><span class="sxs-lookup"><span data-stu-id="c3220-122">Header</span></span> | <span data-ttu-id="c3220-123">ConsoleApi. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c3220-123">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c3220-124">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="c3220-124">Library</span></span> | <span data-ttu-id="c3220-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="c3220-125">Kernel32.lib</span></span> |
| <span data-ttu-id="c3220-126">DLL</span><span class="sxs-lookup"><span data-stu-id="c3220-126">DLL</span></span> | <span data-ttu-id="c3220-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c3220-127">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="c3220-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3220-128">See also</span></span>

[<span data-ttu-id="c3220-129">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="c3220-129">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="c3220-130">**CreatePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="c3220-130">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="c3220-131">**ResizePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="c3220-131">**ResizePseudoConsole**</span></span>](resizepseudoconsole.md)
