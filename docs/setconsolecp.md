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
ms.openlocfilehash: 644f4d925b31da94f42a465d4bce21bb2dc2ecf9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039407"
---
# <a name="setconsolecp-function"></a><span data-ttu-id="608c6-104">SetConsoleCP fonction)</span><span class="sxs-lookup"><span data-stu-id="608c6-104">SetConsoleCP function</span></span>

<span data-ttu-id="608c6-105">Définit la page de codes d’entrée utilisée par la console associée au processus appelant.</span><span class="sxs-lookup"><span data-stu-id="608c6-105">Sets the input code page used by the console associated with the calling process.</span></span> <span data-ttu-id="608c6-106">Une console utilise sa page de codes d’entrée pour convertir l’entrée au clavier en valeur de caractère correspondante.</span><span class="sxs-lookup"><span data-stu-id="608c6-106">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span>

## <a name="syntax"></a><span data-ttu-id="608c6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="608c6-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a><span data-ttu-id="608c6-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="608c6-108">Parameters</span></span>

<span data-ttu-id="608c6-109">*wCodePageID* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="608c6-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="608c6-110">Identificateur de la page de codes à définir.</span><span class="sxs-lookup"><span data-stu-id="608c6-110">The identifier of the code page to be set.</span></span> <span data-ttu-id="608c6-111">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="608c6-111">For more information, see Remarks.</span></span>

## <a name="return-value"></a><span data-ttu-id="608c6-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="608c6-112">Return value</span></span>

<span data-ttu-id="608c6-113">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="608c6-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="608c6-114">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="608c6-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="608c6-115">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="608c6-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="608c6-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="608c6-116">Remarks</span></span>

<span data-ttu-id="608c6-117">Une page de codes mappe 256 codes de caractères à des caractères individuels.</span><span class="sxs-lookup"><span data-stu-id="608c6-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="608c6-118">Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.</span><span class="sxs-lookup"><span data-stu-id="608c6-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="608c6-119">Pour rechercher les pages de codes qui sont installées ou prises en charge par le système d’exploitation, utilisez la fonction [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) .</span><span class="sxs-lookup"><span data-stu-id="608c6-119">To find the code pages that are installed or supported by the operating system, use the [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) function.</span></span> <span data-ttu-id="608c6-120">Les identificateurs des pages de codes disponibles sur l’ordinateur local sont également stockés dans le Registre sous la clé suivante :</span><span class="sxs-lookup"><span data-stu-id="608c6-120">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

<span data-ttu-id="608c6-121">Toutefois, il est préférable d’utiliser [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) pour énumérer les pages de code, car le registre peut différer dans différentes versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="608c6-121">However, it is better to use [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>

<span data-ttu-id="608c6-122">Pour déterminer si une page de codes particulière est valide, utilisez la fonction [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) .</span><span class="sxs-lookup"><span data-stu-id="608c6-122">To determine whether a particular code page is valid, use the [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) function.</span></span> <span data-ttu-id="608c6-123">Pour obtenir plus d’informations sur une page de codes, y compris son nom, utilisez la fonction [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .</span><span class="sxs-lookup"><span data-stu-id="608c6-123">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span> <span data-ttu-id="608c6-124">Pour obtenir la liste des identificateurs de page de codes disponibles, consultez [identificateurs de page de codes](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span><span class="sxs-lookup"><span data-stu-id="608c6-124">For a list of available code page identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="608c6-125">Pour déterminer la page de codes d’entrée actuelle d’une console, utilisez la fonction [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="608c6-125">To determine a console's current input code page, use the [**GetConsoleCP**](getconsolecp.md) function.</span></span> <span data-ttu-id="608c6-126">Pour définir et récupérer la page de codes de sortie d’une console, utilisez les fonctions [**SetConsoleOutputCP**](setconsoleoutputcp.md) et [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="608c6-126">To set and retrieve a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="608c6-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="608c6-127">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="608c6-128">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="608c6-128">Minimum supported client</span></span> | <span data-ttu-id="608c6-129">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="608c6-129">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="608c6-130">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="608c6-130">Minimum supported server</span></span> | <span data-ttu-id="608c6-131">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="608c6-131">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="608c6-132">En-tête</span><span class="sxs-lookup"><span data-stu-id="608c6-132">Header</span></span> | <span data-ttu-id="608c6-133">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="608c6-133">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="608c6-134">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="608c6-134">Library</span></span> | <span data-ttu-id="608c6-135">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="608c6-135">Kernel32.lib</span></span> |
| <span data-ttu-id="608c6-136">DLL</span><span class="sxs-lookup"><span data-stu-id="608c6-136">DLL</span></span> | <span data-ttu-id="608c6-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="608c6-137">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="608c6-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="608c6-138">See also</span></span>

[<span data-ttu-id="608c6-139">Pages de code d’une console</span><span class="sxs-lookup"><span data-stu-id="608c6-139">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="608c6-140">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="608c6-140">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="608c6-141">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="608c6-141">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="608c6-142">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="608c6-142">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="608c6-143">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="608c6-143">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)
