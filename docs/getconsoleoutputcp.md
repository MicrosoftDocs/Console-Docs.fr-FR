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
ms.openlocfilehash: 858b0de83c7b1c4678e992b5f9d0ca3d4876ba49
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358949"
---
# <a name="getconsoleoutputcp-function"></a><span data-ttu-id="7e578-104">GetConsoleOutputCP fonction)</span><span class="sxs-lookup"><span data-stu-id="7e578-104">GetConsoleOutputCP function</span></span>

<span data-ttu-id="7e578-105">Récupère la page de codes de sortie utilisée par la console associée au processus appelant.</span><span class="sxs-lookup"><span data-stu-id="7e578-105">Retrieves the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="7e578-106">Une console utilise sa page de codes de sortie pour convertir les valeurs de caractères écrites par les différentes fonctions de sortie dans les images affichées dans la fenêtre de la console.</span><span class="sxs-lookup"><span data-stu-id="7e578-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e578-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e578-107">Syntax</span></span>

```C
UINT WINAPI GetConsoleOutputCP(void);
```

## <a name="parameters"></a><span data-ttu-id="7e578-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7e578-108">Parameters</span></span>

<span data-ttu-id="7e578-109">Cette fonction n’a pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="7e578-109">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="7e578-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="7e578-110">Return value</span></span>

<span data-ttu-id="7e578-111">La valeur de retour est un code qui identifie la page de codes.</span><span class="sxs-lookup"><span data-stu-id="7e578-111">The return value is a code that identifies the code page.</span></span> <span data-ttu-id="7e578-112">Pour obtenir la liste des identificateurs, consultez [identificateurs de page de codes](/windows/win32/intl/code-page-identifiers).</span><span class="sxs-lookup"><span data-stu-id="7e578-112">For a list of identifiers, see [Code Page Identifiers](/windows/win32/intl/code-page-identifiers).</span></span>

<span data-ttu-id="7e578-113">Si la valeur de retour est égale à zéro, la fonction a échoué.</span><span class="sxs-lookup"><span data-stu-id="7e578-113">If the return value is zero, the function has failed.</span></span> <span data-ttu-id="7e578-114">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="7e578-114">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="7e578-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="7e578-115">Remarks</span></span>

<span data-ttu-id="7e578-116">Une page de codes mappe 256 codes de caractères à des caractères individuels.</span><span class="sxs-lookup"><span data-stu-id="7e578-116">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="7e578-117">Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.</span><span class="sxs-lookup"><span data-stu-id="7e578-117">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span> <span data-ttu-id="7e578-118">Pour obtenir plus d’informations sur une page de codes, y compris son nom, consultez la fonction [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) .</span><span class="sxs-lookup"><span data-stu-id="7e578-118">To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) function.</span></span>

<span data-ttu-id="7e578-119">Pour définir la page de codes de sortie d’une console, utilisez la fonction [**SetConsoleOutputCP**](setconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="7e578-119">To set a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) function.</span></span> <span data-ttu-id="7e578-120">Pour définir et interroger la page de codes d’entrée d’une console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) et [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="7e578-120">To set and query a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="7e578-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7e578-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="7e578-122">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7e578-122">Minimum supported client</span></span> | <span data-ttu-id="7e578-123">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="7e578-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="7e578-124">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7e578-124">Minimum supported server</span></span> | <span data-ttu-id="7e578-125">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="7e578-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="7e578-126">En-tête</span><span class="sxs-lookup"><span data-stu-id="7e578-126">Header</span></span> | <span data-ttu-id="7e578-127">ConsoleApi.h (via WinCon.h, inclure Windows.h)</span><span class="sxs-lookup"><span data-stu-id="7e578-127">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="7e578-128">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="7e578-128">Library</span></span> | <span data-ttu-id="7e578-129">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="7e578-129">Kernel32.lib</span></span> |
| <span data-ttu-id="7e578-130">DLL</span><span class="sxs-lookup"><span data-stu-id="7e578-130">DLL</span></span> | <span data-ttu-id="7e578-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7e578-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="7e578-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e578-132">See also</span></span>

[<span data-ttu-id="7e578-133">Pages de code d’une console</span><span class="sxs-lookup"><span data-stu-id="7e578-133">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="7e578-134">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="7e578-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="7e578-135">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="7e578-135">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="7e578-136">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="7e578-136">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="7e578-137">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="7e578-137">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)