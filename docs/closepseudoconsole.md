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
ms.openlocfilehash: 0674fa9c02c54c9476e2844da69895905865d6f4
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059360"
---
# <a name="closepseudoconsole-function"></a><span data-ttu-id="d8eca-104">ClosePseudoConsole fonction)</span><span class="sxs-lookup"><span data-stu-id="d8eca-104">ClosePseudoConsole function</span></span>


<span data-ttu-id="d8eca-105">Ferme un pseudoconsole à partir du handle donné.</span><span class="sxs-lookup"><span data-stu-id="d8eca-105">Closes a pseudoconsole from the given handle.</span></span>

<a name="syntax"></a><span data-ttu-id="d8eca-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8eca-106">Syntax</span></span>
------

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC 
);
```

<a name="parameters"></a><span data-ttu-id="d8eca-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8eca-107">Parameters</span></span>
----------

<span data-ttu-id="d8eca-108">*hPC* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="d8eca-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="d8eca-109">Handle d’un psuedoconsole actif tel qu’il est ouvert par [CreatePseudoConsole](createpseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="d8eca-109">A handle to an active psuedoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

<a name="return-value"></a><span data-ttu-id="d8eca-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="d8eca-110">Return value</span></span>
------------

<span data-ttu-id="d8eca-111">*Aucune*</span><span class="sxs-lookup"><span data-stu-id="d8eca-111">*none*</span></span>

<a name="remarks"></a><span data-ttu-id="d8eca-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="d8eca-112">Remarks</span></span>
-------

<span data-ttu-id="d8eca-113">Lors de la fermeture d’un pseudoconsole, les applications clientes attachées à la session sont également arrêtées.</span><span class="sxs-lookup"><span data-stu-id="d8eca-113">Upon closing a pseudoconsole, client applications attached to the session will be terminated as well.</span></span>

<span data-ttu-id="d8eca-114">Un frame peint final peut arriver `hOutput` à partir du pseudoconsole quand cette API est appelée.</span><span class="sxs-lookup"><span data-stu-id="d8eca-114">A final painted frame may arrive on `hOutput` from the pseudoconsole when this API is called.</span></span> <span data-ttu-id="d8eca-115">Il est prévu que l’appelant draine ces informations à partir de la mémoire tampon du canal de communication, puis le présente ou l’ignore.</span><span class="sxs-lookup"><span data-stu-id="d8eca-115">It is expected that the caller will drain this information from the communication channel buffer and either present it or discard it.</span></span> <span data-ttu-id="d8eca-116">L’échec de la vidange de la mémoire tampon peut provoquer l’attente indéfinie de l’appel de fermeture jusqu’à ce qu’il soit vidé ou que les canaux de communication soient rompus d’une autre façon.</span><span class="sxs-lookup"><span data-stu-id="d8eca-116">Failure to drain the buffer may cause the Close call to wait indefinitely until it is drained or the communication channels are broken another way.</span></span>

<a name="requirements"></a><span data-ttu-id="d8eca-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d8eca-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="d8eca-118">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="d8eca-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="d8eca-119">Windows 10 1809 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="d8eca-119">Windows 10 1809 [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d8eca-120">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="d8eca-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="d8eca-121">Windows Server 2019 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="d8eca-121">Windows Server 2019 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d8eca-122">En-tête</span><span class="sxs-lookup"><span data-stu-id="d8eca-122">Header</span></span></p></td>
<td><span data-ttu-id="d8eca-123">ConsoleApi. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d8eca-123">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d8eca-124">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="d8eca-124">Library</span></span></p></td>
<td><span data-ttu-id="d8eca-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="d8eca-125">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d8eca-126">DLL</span><span class="sxs-lookup"><span data-stu-id="d8eca-126">DLL</span></span></p></td>
<td><span data-ttu-id="d8eca-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d8eca-127">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="d8eca-128"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8eca-128"><span id="see_also"></span>See also</span></span>

[<span data-ttu-id="d8eca-129">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="d8eca-129">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="d8eca-130">**CreatePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="d8eca-130">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="d8eca-131">**ResizePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="d8eca-131">**ResizePseudoConsole**</span></span>](resizepseudoconsole.md)
