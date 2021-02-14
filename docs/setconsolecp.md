---
title: SetConsoleCP fonction)
description: Définit la page de codes d’entrée utilisée par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/SetConsoleCP
- wincon/SetConsoleCP
- SetConsoleCP
MS-HAID:
- '\_win32\_setconsolecp'
- base.setconsolecp
- consoles.setconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a1a9ba5-c792-491d-ae51-979f462dcb53
topic_type:
- apiref
api_name:
- SetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 040a97360f455fec2ebd043de21e390959f1db0a
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357719"
---
# <a name="setconsolecp-function"></a><span data-ttu-id="75d65-104">SetConsoleCP fonction)</span><span class="sxs-lookup"><span data-stu-id="75d65-104">SetConsoleCP function</span></span>

<span data-ttu-id="75d65-105">Définit la page de codes d’entrée utilisée par la console associée au processus appelant.</span><span class="sxs-lookup"><span data-stu-id="75d65-105">Sets the input code page used by the console associated with the calling process.</span></span> <span data-ttu-id="75d65-106">Une console utilise sa page de codes d’entrée pour convertir l’entrée au clavier en valeur de caractère correspondante.</span><span class="sxs-lookup"><span data-stu-id="75d65-106">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span>

## <a name="syntax"></a><span data-ttu-id="75d65-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75d65-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a><span data-ttu-id="75d65-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="75d65-108">Parameters</span></span>

<span data-ttu-id="75d65-109">*wCodePageID* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="75d65-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="75d65-110">Identificateur de la page de codes à définir.</span><span class="sxs-lookup"><span data-stu-id="75d65-110">The identifier of the code page to be set.</span></span> <span data-ttu-id="75d65-111">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="75d65-111">For more information, see Remarks.</span></span>

## <a name="return-value"></a><span data-ttu-id="75d65-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="75d65-112">Return value</span></span>

<span data-ttu-id="75d65-113">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="75d65-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="75d65-114">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="75d65-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="75d65-115">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="75d65-115">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="75d65-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="75d65-116">Remarks</span></span>

<span data-ttu-id="75d65-117">Une page de codes mappe 256 codes de caractères à des caractères individuels.</span><span class="sxs-lookup"><span data-stu-id="75d65-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="75d65-118">Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.</span><span class="sxs-lookup"><span data-stu-id="75d65-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="75d65-119">Pour rechercher les pages de codes qui sont installées ou prises en charge par le système d’exploitation, utilisez la fonction [**EnumSystemCodePages**](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) .</span><span class="sxs-lookup"><span data-stu-id="75d65-119">To find the code pages that are installed or supported by the operating system, use the [**EnumSystemCodePages**](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) function.</span></span> <span data-ttu-id="75d65-120">Les identificateurs des pages de codes disponibles sur l’ordinateur local sont également stockés dans le Registre sous la clé suivante :</span><span class="sxs-lookup"><span data-stu-id="75d65-120">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

<span data-ttu-id="75d65-121">Toutefois, il est préférable d’utiliser [**EnumSystemCodePages**](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) pour énumérer les pages de code, car le registre peut différer dans différentes versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="75d65-121">However, it is better to use [**EnumSystemCodePages**](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>

<span data-ttu-id="75d65-122">Pour déterminer si une page de codes particulière est valide, utilisez la fonction [**IsValidCodePage**](/windows/win32/api/winnls/nf-winnls-isvalidcodepage) .</span><span class="sxs-lookup"><span data-stu-id="75d65-122">To determine whether a particular code page is valid, use the [**IsValidCodePage**](/windows/win32/api/winnls/nf-winnls-isvalidcodepage) function.</span></span> <span data-ttu-id="75d65-123">Pour obtenir plus d’informations sur une page de codes, y compris son nom, utilisez la fonction [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) .</span><span class="sxs-lookup"><span data-stu-id="75d65-123">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) function.</span></span> <span data-ttu-id="75d65-124">Pour obtenir la liste des identificateurs de page de codes disponibles, consultez [identificateurs de page de codes](/windows/win32/intl/code-page-identifiers).</span><span class="sxs-lookup"><span data-stu-id="75d65-124">For a list of available code page identifiers, see [Code Page Identifiers](/windows/win32/intl/code-page-identifiers).</span></span>

<span data-ttu-id="75d65-125">Pour déterminer la page de codes d’entrée actuelle d’une console, utilisez la fonction [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="75d65-125">To determine a console's current input code page, use the [**GetConsoleCP**](getconsolecp.md) function.</span></span> <span data-ttu-id="75d65-126">Pour définir et récupérer la page de codes de sortie d’une console, utilisez les fonctions [**SetConsoleOutputCP**](setconsoleoutputcp.md) et [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="75d65-126">To set and retrieve a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="75d65-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="75d65-127">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="75d65-128">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="75d65-128">Minimum supported client</span></span> | <span data-ttu-id="75d65-129">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="75d65-129">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="75d65-130">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="75d65-130">Minimum supported server</span></span> | <span data-ttu-id="75d65-131">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="75d65-131">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="75d65-132">En-tête</span><span class="sxs-lookup"><span data-stu-id="75d65-132">Header</span></span> | <span data-ttu-id="75d65-133">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="75d65-133">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="75d65-134">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="75d65-134">Library</span></span> | <span data-ttu-id="75d65-135">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="75d65-135">Kernel32.lib</span></span> |
| <span data-ttu-id="75d65-136">DLL</span><span class="sxs-lookup"><span data-stu-id="75d65-136">DLL</span></span> | <span data-ttu-id="75d65-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="75d65-137">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="75d65-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75d65-138">See also</span></span>

[<span data-ttu-id="75d65-139">Pages de code d’une console</span><span class="sxs-lookup"><span data-stu-id="75d65-139">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="75d65-140">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="75d65-140">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="75d65-141">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="75d65-141">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="75d65-142">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="75d65-142">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="75d65-143">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="75d65-143">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)