---
title: GetConsoleOutputCP fonction)
description: Récupère la page de codes de sortie utilisée par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/GetConsoleOutputCP
- wincon/GetConsoleOutputCP
- GetConsoleOutputCP
MS-HAID:
- '\_win32\_getconsoleoutputcp'
- base.getconsoleoutputcp
- consoles.getconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c23706c7-ce17-4825-a494-20ca44534d45
topic_type:
- apiref
api_name:
- GetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 30276765b35e9179767fa4e82fc40643ee3b2558
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038817"
---
# <a name="getconsoleoutputcp-function"></a><span data-ttu-id="ec5bf-104">GetConsoleOutputCP fonction)</span><span class="sxs-lookup"><span data-stu-id="ec5bf-104">GetConsoleOutputCP function</span></span>

<span data-ttu-id="ec5bf-105">Récupère la page de codes de sortie utilisée par la console associée au processus appelant.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-105">Retrieves the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="ec5bf-106">Une console utilise sa page de codes de sortie pour convertir les valeurs de caractères écrites par les différentes fonctions de sortie dans les images affichées dans la fenêtre de la console.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="ec5bf-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec5bf-107">Syntax</span></span>

```C
UINT WINAPI GetConsoleOutputCP(void);
```

## <a name="parameters"></a><span data-ttu-id="ec5bf-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ec5bf-108">Parameters</span></span>

<span data-ttu-id="ec5bf-109">Cette fonction n’a pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-109">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="ec5bf-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="ec5bf-110">Return value</span></span>

<span data-ttu-id="ec5bf-111">La valeur de retour est un code qui identifie la page de codes.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-111">The return value is a code that identifies the code page.</span></span> <span data-ttu-id="ec5bf-112">Pour obtenir la liste des identificateurs, consultez [identificateurs de page de codes](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span><span class="sxs-lookup"><span data-stu-id="ec5bf-112">For a list of identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="ec5bf-113">Si la valeur de retour est égale à zéro, la fonction a échoué.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-113">If the return value is zero, the function has failed.</span></span> <span data-ttu-id="ec5bf-114">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="ec5bf-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="ec5bf-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="ec5bf-115">Remarks</span></span>

<span data-ttu-id="ec5bf-116">Une page de codes mappe 256 codes de caractères à des caractères individuels.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-116">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="ec5bf-117">Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-117">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span> <span data-ttu-id="ec5bf-118">Pour obtenir plus d’informations sur une page de codes, y compris son nom, consultez la fonction [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .</span><span class="sxs-lookup"><span data-stu-id="ec5bf-118">To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span>

<span data-ttu-id="ec5bf-119">Pour définir la page de codes de sortie d’une console, utilisez la fonction [**SetConsoleOutputCP**](setconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="ec5bf-119">To set a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) function.</span></span> <span data-ttu-id="ec5bf-120">Pour définir et interroger la page de codes d’entrée d’une console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) et [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="ec5bf-120">To set and query a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="ec5bf-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ec5bf-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ec5bf-122">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ec5bf-122">Minimum supported client</span></span> | <span data-ttu-id="ec5bf-123">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ec5bf-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="ec5bf-124">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="ec5bf-124">Minimum supported server</span></span> | <span data-ttu-id="ec5bf-125">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="ec5bf-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="ec5bf-126">En-tête</span><span class="sxs-lookup"><span data-stu-id="ec5bf-126">Header</span></span> | <span data-ttu-id="ec5bf-127">ConsoleApi. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ec5bf-127">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ec5bf-128">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="ec5bf-128">Library</span></span> | <span data-ttu-id="ec5bf-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ec5bf-129">Kernel32.lib</span></span> |
| <span data-ttu-id="ec5bf-130">DLL</span><span class="sxs-lookup"><span data-stu-id="ec5bf-130">DLL</span></span> | <span data-ttu-id="ec5bf-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ec5bf-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="ec5bf-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec5bf-132">See also</span></span>

[<span data-ttu-id="ec5bf-133">Pages de code d’une console</span><span class="sxs-lookup"><span data-stu-id="ec5bf-133">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="ec5bf-134">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="ec5bf-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ec5bf-135">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="ec5bf-135">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="ec5bf-136">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="ec5bf-136">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="ec5bf-137">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="ec5bf-137">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)
