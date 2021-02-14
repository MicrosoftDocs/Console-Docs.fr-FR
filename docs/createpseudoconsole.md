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
ms.openlocfilehash: 91958b23348895f7454c9228e3c730d231dc4f0b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357939"
---
# <a name="createpseudoconsole-function"></a><span data-ttu-id="e73f7-104">CreatePseudoConsole fonction)</span><span class="sxs-lookup"><span data-stu-id="e73f7-104">CreatePseudoConsole function</span></span>

<span data-ttu-id="e73f7-105">Crée un nouvel objet pseudoconsole pour le processus appelant.</span><span class="sxs-lookup"><span data-stu-id="e73f7-105">Creates a new pseudoconsole object for the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="e73f7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e73f7-106">Syntax</span></span>

```C
HRESULT WINAPI CreatePseudoConsole(
    _In_ COORD size,
    _In_ HANDLE hInput,
    _In_ HANDLE hOutput,
    _In_ DWORD dwFlags,
    _Out_ HPCON* phPC
);
```

## <a name="parameters"></a><span data-ttu-id="e73f7-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e73f7-107">Parameters</span></span>

<span data-ttu-id="e73f7-108">*taille* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="e73f7-108">*size* \[in\]</span></span>  
<span data-ttu-id="e73f7-109">Dimensions de la fenêtre/mémoire tampon en nombre de caractères qui seront utilisés lors de la création initiale du pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="e73f7-109">The dimensions of the window/buffer in count of characters that will be used on initial creation of the pseudoconsole.</span></span> <span data-ttu-id="e73f7-110">Cela peut être ajusté ultérieurement avec [ResizePseudoConsole](resizepseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="e73f7-110">This can be adjusted later with [ResizePseudoConsole](resizepseudoconsole.md).</span></span>

<span data-ttu-id="e73f7-111">*hInput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="e73f7-111">*hInput* \[in\]</span></span>  
<span data-ttu-id="e73f7-112">Handle ouvert d’un flux de données qui représente l’entrée d’utilisateur sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="e73f7-112">An open handle to a stream of data that represents user input to the device.</span></span> <span data-ttu-id="e73f7-113">Cela est actuellement limité à des e/s [synchrones](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .</span><span class="sxs-lookup"><span data-stu-id="e73f7-113">This is currently restricted to [synchronous](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.</span></span>

<span data-ttu-id="e73f7-114">*hOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="e73f7-114">*hOutput* \[in\]</span></span>  
<span data-ttu-id="e73f7-115">Handle ouvert d’un flux de données qui représente la sortie de l’application à partir de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="e73f7-115">An open handle to a stream of data that represents application output from the device.</span></span> <span data-ttu-id="e73f7-116">Cela est actuellement limité à des e/s [synchrones](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .</span><span class="sxs-lookup"><span data-stu-id="e73f7-116">This is currently restricted to [synchronous](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.</span></span>

<span data-ttu-id="e73f7-117">*dwFlags* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="e73f7-117">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="e73f7-118">Il peut s'agir de l'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="e73f7-118">The value can be one of the following:</span></span>

| <span data-ttu-id="e73f7-119">Valeur</span><span class="sxs-lookup"><span data-stu-id="e73f7-119">Value</span></span> | <span data-ttu-id="e73f7-120">Signification</span><span class="sxs-lookup"><span data-stu-id="e73f7-120">Meaning</span></span> |
|-|-|
| <span data-ttu-id="e73f7-121">**0**</span><span class="sxs-lookup"><span data-stu-id="e73f7-121">**0**</span></span> | <span data-ttu-id="e73f7-122">Effectuez une création pseudoconsole standard.</span><span class="sxs-lookup"><span data-stu-id="e73f7-122">Perform a standard pseudoconsole creation.</span></span> |
| <span data-ttu-id="e73f7-123">**PSEUDOCONSOLE_INHERIT_CURSOR** (DWORD) 1</span><span class="sxs-lookup"><span data-stu-id="e73f7-123">**PSEUDOCONSOLE_INHERIT_CURSOR** (DWORD)1</span></span> | <span data-ttu-id="e73f7-124">La session pseudoconsole créée va essayer d’hériter de la position du curseur de la console parente.</span><span class="sxs-lookup"><span data-stu-id="e73f7-124">The created pseudoconsole session will attempt to inherit the cursor position of the parent console.</span></span> |

<span data-ttu-id="e73f7-125">*phPC* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="e73f7-125">*phPC* \[out\]</span></span>  
<span data-ttu-id="e73f7-126">Pointeur vers un emplacement qui recevra un handle vers le nouvel appareil pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="e73f7-126">Pointer to a location that will receive a handle to the new pseudoconsole device.</span></span>

## <a name="return-value"></a><span data-ttu-id="e73f7-127">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e73f7-127">Return value</span></span>

<span data-ttu-id="e73f7-128">Type : **HRESULT**</span><span class="sxs-lookup"><span data-stu-id="e73f7-128">Type: **HRESULT**</span></span>

<span data-ttu-id="e73f7-129">Si cette méthode est réussie, elle retourne **S_OK**.</span><span class="sxs-lookup"><span data-stu-id="e73f7-129">If this method succeeds, it returns **S_OK**.</span></span> <span data-ttu-id="e73f7-130">Sinon, elle retourne un code d’erreur **HRESULT** .</span><span class="sxs-lookup"><span data-stu-id="e73f7-130">Otherwise, it returns an **HRESULT** error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e73f7-131">Notes</span><span class="sxs-lookup"><span data-stu-id="e73f7-131">Remarks</span></span>

<span data-ttu-id="e73f7-132">Cette fonction est principalement utilisée par les applications qui tentent d’être une fenêtre de terminal pour une application d’interface utilisateur de ligne de commande (CUI).</span><span class="sxs-lookup"><span data-stu-id="e73f7-132">This function is primarily used by applications attempting to be a terminal window for a command-line user interface (CUI) application.</span></span> <span data-ttu-id="e73f7-133">Les appelants sont responsables de la présentation des informations sur le flux de sortie et de la collecte des entrées d’utilisateur et de leur sérialisation dans le flux d’entrée.</span><span class="sxs-lookup"><span data-stu-id="e73f7-133">The callers become responsible for presentation of the information on the output stream and for collecting user input and serializing it into the input stream.</span></span>

<span data-ttu-id="e73f7-134">Les flux d’entrée et de sortie encodés au format UTF-8 contiennent du texte brut entrelacé avec des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md).</span><span class="sxs-lookup"><span data-stu-id="e73f7-134">The input and output streams encoded as UTF-8 contain plain text interleaved with [Virtual Terminal Sequences](console-virtual-terminal-sequences.md).</span></span>

<span data-ttu-id="e73f7-135">Dans le flux de sortie, les [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) peuvent être décodées par l’application appelante pour mettre en forme et présenter le texte brut dans une fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="e73f7-135">On the output stream, the [virtual terminal sequences](console-virtual-terminal-sequences.md) can be decoded by the calling application to layout and present the plain text in a display window.</span></span>

<span data-ttu-id="e73f7-136">Dans le flux d’entrée, le texte brut représente les touches de clavier standard entrées par un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e73f7-136">On the input stream, plain text represents standard keyboard keys input by a user.</span></span> <span data-ttu-id="e73f7-137">Des opérations plus compliquées sont représentées par l’encodage des clés de contrôle et des mouvements de la souris en tant que [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) incorporées dans ce flux.</span><span class="sxs-lookup"><span data-stu-id="e73f7-137">More complicated operations are represented by encoding control keys and mouse movements as [virtual terminal sequences](console-virtual-terminal-sequences.md) embedded in this stream.</span></span>

<span data-ttu-id="e73f7-138">Le descripteur créé par cette fonction doit être fermé avec [ClosePseudoConsole](closepseudoconsole.md) lorsque les opérations sont terminées.</span><span class="sxs-lookup"><span data-stu-id="e73f7-138">The handle created by this function must be closed with [ClosePseudoConsole](closepseudoconsole.md) when operations are complete.</span></span>

<span data-ttu-id="e73f7-139">Si `PSEUDOCONSOLE_INHERIT_CURSOR` vous utilisez, l’application appelante doit être préparée à répondre à la demande d’état de curseur de manière asynchrone sur un thread d’arrière-plan en transférant ou en interprétant la demande d’informations de curseur qui seront reçues `hOutput` et répondant à `hInput` .</span><span class="sxs-lookup"><span data-stu-id="e73f7-139">If using `PSEUDOCONSOLE_INHERIT_CURSOR`, the calling application should be prepared to respond to the request for the cursor state in an asynchronous fashion on a background thread by forwarding or interpreting the request for cursor information that will be received on `hOutput` and replying on `hInput`.</span></span> <span data-ttu-id="e73f7-140">Si vous ne le faites pas, l’application appelante risque de se bloquer lors de l’exécution d’une autre demande du système pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="e73f7-140">Failure to do so may cause the calling application to hang while making another request of the pseudoconsole system.</span></span>

## <a name="examples"></a><span data-ttu-id="e73f7-141">Exemples</span><span class="sxs-lookup"><span data-stu-id="e73f7-141">Examples</span></span>

<span data-ttu-id="e73f7-142">Pour une procédure pas à pas complète sur l’utilisation de cette fonction pour établir une session pseudoconsole, consultez [création d’une session pseudoconsole](creating-a-pseudoconsole-session.md).</span><span class="sxs-lookup"><span data-stu-id="e73f7-142">For a full walkthrough on using this function to establish a pseudoconsole session, please see [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="e73f7-143">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e73f7-143">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e73f7-144">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="e73f7-144">Minimum supported client</span></span> | <span data-ttu-id="e73f7-145">Windows 10 octobre 2018 mise à jour (version 1809) \[ applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="e73f7-145">Windows 10 October 2018 Update (version 1809) \[desktop apps only\]</span></span> |
| <span data-ttu-id="e73f7-146">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="e73f7-146">Minimum supported server</span></span> | <span data-ttu-id="e73f7-147">Applications de bureau Windows Server 2019 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="e73f7-147">Windows Server 2019 \[desktop apps only\]</span></span> |
| <span data-ttu-id="e73f7-148">En-tête</span><span class="sxs-lookup"><span data-stu-id="e73f7-148">Header</span></span> | <span data-ttu-id="e73f7-149">ConsoleApi.h (via WinCon.h, inclure Windows.h)</span><span class="sxs-lookup"><span data-stu-id="e73f7-149">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="e73f7-150">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="e73f7-150">Library</span></span> | <span data-ttu-id="e73f7-151">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="e73f7-151">Kernel32.lib</span></span> |
| <span data-ttu-id="e73f7-152">DLL</span><span class="sxs-lookup"><span data-stu-id="e73f7-152">DLL</span></span> | <span data-ttu-id="e73f7-153">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e73f7-153">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="e73f7-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e73f7-154">See also</span></span>

[<span data-ttu-id="e73f7-155">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="e73f7-155">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="e73f7-156">Création d’une session pseudo-console</span><span class="sxs-lookup"><span data-stu-id="e73f7-156">Creating a Pseudoconsole Session</span></span>](creating-a-pseudoconsole-session.md)

[<span data-ttu-id="e73f7-157">**ResizePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="e73f7-157">**ResizePseudoConsole**</span></span>](resizepseudoconsole.md)

[<span data-ttu-id="e73f7-158">**ClosePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="e73f7-158">**ClosePseudoConsole**</span></span>](closepseudoconsole.md)