---
title: GetConsoleCP fonction)
description: Récupère la page de codes d’entrée utilisée par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/GetConsoleCP
- wincon/GetConsoleCP
- GetConsoleCP
MS-HAID:
- '\_win32\_getconsolecp'
- base.getconsolecp
- consoles.getconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9e0af6d9-0f5c-45b3-a686-22449d26de47
topic_type:
- apiref
api_name:
- GetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 75570acba7d8572d1bd3f132ac379598d82ec73f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038017"
---
# <a name="getconsolecp-function"></a><span data-ttu-id="ff324-104">GetConsoleCP fonction)</span><span class="sxs-lookup"><span data-stu-id="ff324-104">GetConsoleCP function</span></span>

<span data-ttu-id="ff324-105">Récupère la page de codes d’entrée utilisée par la console associée au processus appelant.</span><span class="sxs-lookup"><span data-stu-id="ff324-105">Retrieves the input code page used by the console associated with the calling process.</span></span> <span data-ttu-id="ff324-106">Une console utilise sa page de codes d’entrée pour convertir l’entrée au clavier en valeur de caractère correspondante.</span><span class="sxs-lookup"><span data-stu-id="ff324-106">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span>

## <a name="syntax"></a><span data-ttu-id="ff324-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff324-107">Syntax</span></span>

```C
UINT WINAPI GetConsoleCP(void);
```

## <a name="parameters"></a><span data-ttu-id="ff324-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ff324-108">Parameters</span></span>

<span data-ttu-id="ff324-109">Cette fonction n’a pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="ff324-109">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="ff324-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="ff324-110">Return value</span></span>

<span data-ttu-id="ff324-111">La valeur de retour est un code qui identifie la page de codes.</span><span class="sxs-lookup"><span data-stu-id="ff324-111">The return value is a code that identifies the code page.</span></span> <span data-ttu-id="ff324-112">Pour obtenir la liste des identificateurs, consultez [identificateurs de page de codes](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span><span class="sxs-lookup"><span data-stu-id="ff324-112">For a list of identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="ff324-113">Si la valeur de retour est égale à zéro, la fonction a échoué.</span><span class="sxs-lookup"><span data-stu-id="ff324-113">If the return value is zero, the function has failed.</span></span> <span data-ttu-id="ff324-114">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="ff324-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="ff324-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="ff324-115">Remarks</span></span>

<span data-ttu-id="ff324-116">Une page de codes mappe 256 codes de caractères à des caractères individuels.</span><span class="sxs-lookup"><span data-stu-id="ff324-116">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="ff324-117">Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.</span><span class="sxs-lookup"><span data-stu-id="ff324-117">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span> <span data-ttu-id="ff324-118">Pour obtenir plus d’informations sur une page de codes, y compris son nom, consultez la fonction [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .</span><span class="sxs-lookup"><span data-stu-id="ff324-118">To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span>

<span data-ttu-id="ff324-119">Pour définir la page de codes d’entrée d’une console, utilisez la fonction [**SetConsoleCP**](setconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="ff324-119">To set a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) function.</span></span> <span data-ttu-id="ff324-120">Pour définir et interroger la page de codes de sortie d’une console, utilisez les fonctions [**SetConsoleOutputCP**](setconsoleoutputcp.md) et [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="ff324-120">To set and query a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="ff324-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ff324-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ff324-122">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ff324-122">Minimum supported client</span></span> | <span data-ttu-id="ff324-123">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ff324-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="ff324-124">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ff324-124">Minimum supported server</span></span> | <span data-ttu-id="ff324-125">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ff324-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="ff324-126">En-tête</span><span class="sxs-lookup"><span data-stu-id="ff324-126">Header</span></span> | <span data-ttu-id="ff324-127">ConsoleApi. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ff324-127">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ff324-128">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="ff324-128">Library</span></span> | <span data-ttu-id="ff324-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ff324-129">Kernel32.lib</span></span> |
| <span data-ttu-id="ff324-130">DLL</span><span class="sxs-lookup"><span data-stu-id="ff324-130">DLL</span></span> | <span data-ttu-id="ff324-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ff324-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="ff324-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff324-132">See also</span></span>

[<span data-ttu-id="ff324-133">Pages de code d’une console</span><span class="sxs-lookup"><span data-stu-id="ff324-133">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="ff324-134">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="ff324-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ff324-135">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="ff324-135">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="ff324-136">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="ff324-136">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="ff324-137">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="ff324-137">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)
