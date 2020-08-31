---
title: CreatePseudoConsole fonction)
description: Consultez les informations de référence sur la fonction CreatePseudoConsole, qui alloue un nouveau pseudoconsole pour le processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API console, conpty, pseudoconsole
f1_keywords:
- consoleapi/CreatePseudoConsole
- CreatePseudoConsole
topic_type:
- apiref
api_name:
- CreatePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 7d707423d7fca7c55d06bff11d6cbc904512e62b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059233"
---
# <a name="createpseudoconsole-function"></a><span data-ttu-id="b14ab-104">CreatePseudoConsole fonction)</span><span class="sxs-lookup"><span data-stu-id="b14ab-104">CreatePseudoConsole function</span></span>


<span data-ttu-id="b14ab-105">Crée un nouvel objet pseudoconsole pour le processus appelant.</span><span class="sxs-lookup"><span data-stu-id="b14ab-105">Creates a new pseudoconsole object for the calling process.</span></span>

<a name="syntax"></a><span data-ttu-id="b14ab-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b14ab-106">Syntax</span></span>
------

```C
HRESULT WINAPI CreatePseudoConsole(
    _In_ COORD size,
    _In_ HANDLE hInput,
    _In_ HANDLE hOutput,
    _In_ DWORD dwFlags,
    _Out_ HPCON* phPC
);
```

<a name="parameters"></a><span data-ttu-id="b14ab-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b14ab-107">Parameters</span></span>
----------

<span data-ttu-id="b14ab-108">*taille* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="b14ab-108">*size* \[in\]</span></span>  
<span data-ttu-id="b14ab-109">Dimensions de la fenêtre/mémoire tampon en nombre de caractères qui seront utilisés lors de la création initiale du pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="b14ab-109">The dimensions of the window/buffer in count of characters that will be used on initial creation of the pseudoconsole.</span></span> <span data-ttu-id="b14ab-110">Cela peut être ajusté ultérieurement avec [ResizePseudoConsole](resizepseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="b14ab-110">This can be adjusted later with [ResizePseudoConsole](resizepseudoconsole.md).</span></span>

<span data-ttu-id="b14ab-111">*hInput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="b14ab-111">*hInput* \[in\]</span></span>  
<span data-ttu-id="b14ab-112">Handle ouvert d’un flux de données qui représente l’entrée d’utilisateur sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="b14ab-112">An open handle to a stream of data that represents user input to the device.</span></span> <span data-ttu-id="b14ab-113">Cela est actuellement limité à des e/s [synchrones](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .</span><span class="sxs-lookup"><span data-stu-id="b14ab-113">This is currently restricted to [synchronous](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.</span></span>

<span data-ttu-id="b14ab-114">*hOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="b14ab-114">*hOutput* \[in\]</span></span>  
<span data-ttu-id="b14ab-115">Handle ouvert d’un flux de données qui représente la sortie de l’application à partir de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="b14ab-115">An open handle to a stream of data that represents application output from the device.</span></span> <span data-ttu-id="b14ab-116">Cela est actuellement limité à des e/s [synchrones](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .</span><span class="sxs-lookup"><span data-stu-id="b14ab-116">This is currently restricted to [synchronous](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.</span></span>

<span data-ttu-id="b14ab-117">*dwFlags* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="b14ab-117">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="b14ab-118">Il peut s'agir de l'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="b14ab-118">The value can be one of the following:</span></span>
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="b14ab-119">Value</span><span class="sxs-lookup"><span data-stu-id="b14ab-119">Value</span></span></th>
<th><span data-ttu-id="b14ab-120">Signification</span><span class="sxs-lookup"><span data-stu-id="b14ab-120">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="b14ab-121"><strong>0</strong></span><span class="sxs-lookup"><span data-stu-id="b14ab-121"><strong>0</strong></span></span></td>
<td><p><span data-ttu-id="b14ab-122">Effectuez une création pseudoconsole standard.</span><span class="sxs-lookup"><span data-stu-id="b14ab-122">Perform a standard pseudoconsole creation.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="b14ab-123"><span id="PSEUDOCONSOLE_INHERIT_CURSOR"></span><span id="pseudoconsole_inherit_cursor"></span>
<strong>PSEUDOCONSOLE_INHERIT_CURSOR</strong> (DWORD) 1</span><span class="sxs-lookup"><span data-stu-id="b14ab-123"><span id="PSEUDOCONSOLE_INHERIT_CURSOR"></span><span id="pseudoconsole_inherit_cursor"></span>
<strong>PSEUDOCONSOLE_INHERIT_CURSOR</strong> (DWORD)1</span></span></td>
<td><p><span data-ttu-id="b14ab-124">La session pseudoconsole créée va essayer d’hériter de la position du curseur de la console parente.</span><span class="sxs-lookup"><span data-stu-id="b14ab-124">The created pseudoconsole session will attempt to inherit the cursor position of the parent console.</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="b14ab-125">*phPC* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="b14ab-125">*phPC* \[out\]</span></span>  
<span data-ttu-id="b14ab-126">Pointeur vers un emplacement qui recevra un handle vers le nouvel appareil pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="b14ab-126">Pointer to a location that will receive a handle to the new pseudoconsole device.</span></span>

<a name="return-value"></a><span data-ttu-id="b14ab-127">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="b14ab-127">Return value</span></span>
------------

<span data-ttu-id="b14ab-128">Type : **HRESULT**</span><span class="sxs-lookup"><span data-stu-id="b14ab-128">Type: **HRESULT**</span></span>

<span data-ttu-id="b14ab-129">Si cette méthode est réussie, elle retourne **S_OK**.</span><span class="sxs-lookup"><span data-stu-id="b14ab-129">If this method succeeds, it returns **S_OK**.</span></span> <span data-ttu-id="b14ab-130">Sinon, elle retourne un code d’erreur **HRESULT** .</span><span class="sxs-lookup"><span data-stu-id="b14ab-130">Otherwise, it returns an **HRESULT** error code.</span></span>

<a name="remarks"></a><span data-ttu-id="b14ab-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="b14ab-131">Remarks</span></span>
-------

<span data-ttu-id="b14ab-132">Cette fonction est principalement utilisée par les applications qui tentent d’être une fenêtre de terminal pour une application d’interface utilisateur de ligne de commande (CUI).</span><span class="sxs-lookup"><span data-stu-id="b14ab-132">This function is primarily used by applications attempting to be a terminal window for a command-line user interface (CUI) application.</span></span> <span data-ttu-id="b14ab-133">Les appelants sont responsables de la présentation des informations sur le flux de sortie et de la collecte des entrées d’utilisateur et de leur sérialisation dans le flux d’entrée.</span><span class="sxs-lookup"><span data-stu-id="b14ab-133">The callers become responsible for presentation of the information on the output stream and for collecting user input and serializing it into the input stream.</span></span>

<span data-ttu-id="b14ab-134">Les flux d’entrée et de sortie encodés au format UTF-8 contiennent du texte brut entrelacé avec des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md).</span><span class="sxs-lookup"><span data-stu-id="b14ab-134">The input and output streams encoded as UTF-8 contain plain text interleaved with [Virtual Terminal Sequences](console-virtual-terminal-sequences.md).</span></span> 

<span data-ttu-id="b14ab-135">Dans le flux de sortie, les [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) peuvent être décodées par l’application appelante pour mettre en forme et présenter le texte brut dans une fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="b14ab-135">On the output stream, the [virtual terminal sequences](console-virtual-terminal-sequences.md) can be decoded by the calling application to layout and present the plain text in a display window.</span></span> 

<span data-ttu-id="b14ab-136">Dans le flux d’entrée, le texte brut représente les touches de clavier standard entrées par un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b14ab-136">On the input stream, plain text represents standard keyboard keys input by a user.</span></span> <span data-ttu-id="b14ab-137">Des opérations plus compliquées sont représentées par l’encodage des clés de contrôle et des mouvements de la souris en tant que [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) incorporées dans ce flux.</span><span class="sxs-lookup"><span data-stu-id="b14ab-137">More complicated operations are represented by encoding control keys and mouse movements as [virtual terminal sequences](console-virtual-terminal-sequences.md) embedded in this stream.</span></span>

<span data-ttu-id="b14ab-138">Le descripteur créé par cette fonction doit être fermé avec [ClosePseudoConsole](closepseudoconsole.md) lorsque les opérations sont terminées.</span><span class="sxs-lookup"><span data-stu-id="b14ab-138">The handle created by this function must be closed with [ClosePseudoConsole](closepseudoconsole.md) when operations are complete.</span></span>

<span data-ttu-id="b14ab-139">Si `PSEUDOCONSOLE_INHERIT_CURSOR` vous utilisez, l’application appelante doit être préparée à répondre à la demande d’état de curseur de manière asynchrone sur un thread d’arrière-plan en transférant ou en interprétant la demande d’informations de curseur qui seront reçues `hOutput` et répondant à `hInput` .</span><span class="sxs-lookup"><span data-stu-id="b14ab-139">If using `PSEUDOCONSOLE_INHERIT_CURSOR`, the calling application should be prepared to respond to the request for the cursor state in an asynchronous fashion on a background thread by forwarding or interpreting the request for cursor information that will be received on `hOutput` and replying on `hInput`.</span></span> <span data-ttu-id="b14ab-140">Si vous ne le faites pas, l’application appelante risque de se bloquer lors de l’exécution d’une autre demande du système pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="b14ab-140">Failure to do so may cause the calling application to hang while making another request of the pseudoconsole system.</span></span>

<a name="examples"></a><span data-ttu-id="b14ab-141">Exemples</span><span class="sxs-lookup"><span data-stu-id="b14ab-141">Examples</span></span>
--------

<span data-ttu-id="b14ab-142">Pour une procédure pas à pas complète sur l’utilisation de cette fonction pour établir une session psuedoconsole, consultez [création d’une session Pseudoconsole](creating-a-pseudoconsole-session.md).</span><span class="sxs-lookup"><span data-stu-id="b14ab-142">For a full walkthrough on using this function to establish a psuedoconsole session, please see [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).</span></span>

<a name="requirements"></a><span data-ttu-id="b14ab-143">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b14ab-143">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b14ab-144">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="b14ab-144">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="b14ab-145">Windows 10 1809 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="b14ab-145">Windows 10 1809 [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b14ab-146">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="b14ab-146">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="b14ab-147">Windows Server 2019 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="b14ab-147">Windows Server 2019 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b14ab-148">En-tête</span><span class="sxs-lookup"><span data-stu-id="b14ab-148">Header</span></span></p></td>
<td><span data-ttu-id="b14ab-149">ConsoleApi. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b14ab-149">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b14ab-150">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="b14ab-150">Library</span></span></p></td>
<td><span data-ttu-id="b14ab-151">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="b14ab-151">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b14ab-152">DLL</span><span class="sxs-lookup"><span data-stu-id="b14ab-152">DLL</span></span></p></td>
<td><span data-ttu-id="b14ab-153">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b14ab-153">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="b14ab-154"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b14ab-154"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="b14ab-155">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="b14ab-155">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="b14ab-156">Création d’une session Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="b14ab-156">Creating a Pseudoconsole Session</span></span>](creating-a-pseudoconsole-session.md)

[<span data-ttu-id="b14ab-157">**ResizePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="b14ab-157">**ResizePseudoConsole**</span></span>](resizepseudoconsole.md)

[<span data-ttu-id="b14ab-158">**ClosePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="b14ab-158">**ClosePseudoConsole**</span></span>](closepseudoconsole.md)
