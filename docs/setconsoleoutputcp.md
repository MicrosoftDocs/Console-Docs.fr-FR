---
title: SetConsoleOutputCP fonction)
description: Définit la page de codes de sortie utilisée par la console associée au processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/SetConsoleOutputCP
- wincon/SetConsoleOutputCP
- SetConsoleOutputCP
MS-HAID:
- '\_win32\_setconsoleoutputcp'
- base.setconsoleoutputcp
- consoles.setconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0b41e66b-ca19-4d69-9f39-92da158344ef
topic_type:
- apiref
api_name:
- SetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 85b6ba4d829b86b99138efbdaa14284429d2aa81
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039337"
---
# <a name="setconsoleoutputcp-function"></a><span data-ttu-id="49679-104">SetConsoleOutputCP fonction)</span><span class="sxs-lookup"><span data-stu-id="49679-104">SetConsoleOutputCP function</span></span>

<span data-ttu-id="49679-105">Définit la page de codes de sortie utilisée par la console associée au processus appelant.</span><span class="sxs-lookup"><span data-stu-id="49679-105">Sets the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="49679-106">Une console utilise sa page de codes de sortie pour convertir les valeurs de caractères écrites par les différentes fonctions de sortie dans les images affichées dans la fenêtre de la console.</span><span class="sxs-lookup"><span data-stu-id="49679-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="49679-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49679-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleOutputCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a><span data-ttu-id="49679-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49679-108">Parameters</span></span>

<span data-ttu-id="49679-109">*wCodePageID* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="49679-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="49679-110">Identificateur de la page de codes à définir.</span><span class="sxs-lookup"><span data-stu-id="49679-110">The identifier of the code page to set.</span></span> <span data-ttu-id="49679-111">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="49679-111">For more information, see Remarks.</span></span>

## <a name="return-value"></a><span data-ttu-id="49679-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="49679-112">Return value</span></span>

<span data-ttu-id="49679-113">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="49679-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="49679-114">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="49679-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="49679-115">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="49679-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="49679-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="49679-116">Remarks</span></span>

<span data-ttu-id="49679-117">Une page de codes mappe 256 codes de caractères à des caractères individuels.</span><span class="sxs-lookup"><span data-stu-id="49679-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="49679-118">Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.</span><span class="sxs-lookup"><span data-stu-id="49679-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="49679-119">Si la police actuelle est une police Unicode à espacement fixe, **SetConsoleOutputCP** modifie le mappage des valeurs de caractère dans le jeu de glyphes de la police, plutôt que de charger une police distincte chaque fois qu’elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="49679-119">If the current font is a fixed-pitch Unicode font, **SetConsoleOutputCP** changes the mapping of the character values into the glyph set of the font, rather than loading a separate font each time it is called.</span></span> <span data-ttu-id="49679-120">Cela affecte la façon dont les caractères étendus (valeur ASCII supérieure à 127) sont affichés dans une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="49679-120">This affects how extended characters (ASCII value greater than 127) are displayed in a console window.</span></span> <span data-ttu-id="49679-121">Toutefois, si la police actuelle est une police raster, **SetConsoleOutputCP** n’affecte pas la manière dont les caractères étendus sont affichés.</span><span class="sxs-lookup"><span data-stu-id="49679-121">However, if the current font is a raster font, **SetConsoleOutputCP** does not affect how extended characters are displayed.</span></span>

<span data-ttu-id="49679-122">Pour rechercher les pages de codes qui sont installées ou prises en charge par le système d’exploitation, utilisez la fonction [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) .</span><span class="sxs-lookup"><span data-stu-id="49679-122">To find the code pages that are installed or supported by the operating system, use the [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) function.</span></span> <span data-ttu-id="49679-123">Les identificateurs des pages de codes disponibles sur l’ordinateur local sont également stockés dans le Registre sous la clé suivante :</span><span class="sxs-lookup"><span data-stu-id="49679-123">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

<span data-ttu-id="49679-124">Toutefois, il est préférable d’utiliser [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) pour énumérer les pages de code, car le registre peut différer dans différentes versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="49679-124">However, it is better to use [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>
<span data-ttu-id="49679-125">Pour déterminer si une page de codes particulière est valide, utilisez la fonction [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) .</span><span class="sxs-lookup"><span data-stu-id="49679-125">To determine whether a particular code page is valid, use the [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) function.</span></span> <span data-ttu-id="49679-126">Pour obtenir plus d’informations sur une page de codes, y compris son nom, utilisez la fonction [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .</span><span class="sxs-lookup"><span data-stu-id="49679-126">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span> <span data-ttu-id="49679-127">Pour obtenir la liste des identificateurs de page de codes disponibles, consultez [identificateurs de page de codes](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span><span class="sxs-lookup"><span data-stu-id="49679-127">For a list of available code page identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="49679-128">Pour déterminer la page de codes de sortie actuelle d’une console, utilisez la fonction [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="49679-128">To determine a console's current output code page, use the [**GetConsoleOutputCP**](getconsoleoutputcp.md) function.</span></span> <span data-ttu-id="49679-129">Pour définir et récupérer la page de codes d’entrée d’une console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) et [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="49679-129">To set and retrieve a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="49679-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="49679-130">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="49679-131">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="49679-131">Minimum supported client</span></span> | <span data-ttu-id="49679-132">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="49679-132">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="49679-133">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="49679-133">Minimum supported server</span></span> | <span data-ttu-id="49679-134">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="49679-134">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="49679-135">En-tête</span><span class="sxs-lookup"><span data-stu-id="49679-135">Header</span></span> | <span data-ttu-id="49679-136">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="49679-136">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="49679-137">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="49679-137">Library</span></span> | <span data-ttu-id="49679-138">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="49679-138">Kernel32.lib</span></span> |
| <span data-ttu-id="49679-139">DLL</span><span class="sxs-lookup"><span data-stu-id="49679-139">DLL</span></span> | <span data-ttu-id="49679-140">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="49679-140">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="49679-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49679-141">See also</span></span>

[<span data-ttu-id="49679-142">Pages de code d’une console</span><span class="sxs-lookup"><span data-stu-id="49679-142">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="49679-143">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="49679-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="49679-144">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="49679-144">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="49679-145">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="49679-145">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="49679-146">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="49679-146">**SetConsoleCP**</span></span>](setconsolecp.md)
