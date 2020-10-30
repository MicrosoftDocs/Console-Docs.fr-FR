---
title: GetConsoleTitle fonction)
description: Récupère le titre et la taille du titre pour la fenêtre de console active.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/GetConsoleTitle
- wincon/GetConsoleTitle
- GetConsoleTitle
- consoleapi2/GetConsoleTitleA
- wincon/GetConsoleTitleA
- GetConsoleTitleA
- consoleapi2/GetConsoleTitleW
- wincon/GetConsoleTitleW
- GetConsoleTitleW
MS-HAID:
- '\_win32\_getconsoletitle'
- base.getconsoletitle
- consoles.getconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c58bba36-9813-4bdc-83bf-30d55f8d7d79
topic_type:
- apiref
api_name:
- GetConsoleTitle
- GetConsoleTitleA
- GetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-Ms-Win-Core-Console-Ansi-L2-1-0.dll
- Kernel32Legacy.dll
api_type:
- DllExport
ms.openlocfilehash: 23b52ba1d5dde40ef842297249fdd2f87cebcb12
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037877"
---
# <a name="getconsoletitle-function"></a><span data-ttu-id="89e87-104">GetConsoleTitle fonction)</span><span class="sxs-lookup"><span data-stu-id="89e87-104">GetConsoleTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="89e87-105">Récupère le titre de la fenêtre de console active.</span><span class="sxs-lookup"><span data-stu-id="89e87-105">Retrieves the title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="89e87-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89e87-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a><span data-ttu-id="89e87-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="89e87-107">Parameters</span></span>

<span data-ttu-id="89e87-108">*lpConsoleTitle* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="89e87-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="89e87-109">Pointeur vers une mémoire tampon qui reçoit une chaîne se terminant par null et contenant le titre.</span><span class="sxs-lookup"><span data-stu-id="89e87-109">A pointer to a buffer that receives a null-terminated string containing the title.</span></span> <span data-ttu-id="89e87-110">Si la mémoire tampon est trop petite pour stocker le titre, la fonction stocke autant de caractères du titre que ceux qui sont contenus dans la mémoire tampon, se terminant par une marque de fin null.</span><span class="sxs-lookup"><span data-stu-id="89e87-110">If the buffer is too small to store the title, the function stores as many characters of the title as will fit in the buffer, ending with a null terminator.</span></span>

<span data-ttu-id="89e87-111">*nSize* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="89e87-111">*nSize* \[in\]</span></span>  
<span data-ttu-id="89e87-112">Taille de la mémoire tampon vers laquelle pointe le paramètre *lpConsoleTitle* , en caractères.</span><span class="sxs-lookup"><span data-stu-id="89e87-112">The size of the buffer pointed to by the *lpConsoleTitle* parameter, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="89e87-113">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="89e87-113">Return value</span></span>

<span data-ttu-id="89e87-114">Si la fonction est réussie, la valeur de retour est la longueur du titre de la fenêtre de console, en caractères.</span><span class="sxs-lookup"><span data-stu-id="89e87-114">If the function succeeds, the return value is the length of the console window's title, in characters.</span></span>

<span data-ttu-id="89e87-115">Si la fonction échoue, la valeur de retour est zéro et [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) retourne le code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="89e87-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="89e87-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="89e87-116">Remarks</span></span>

<span data-ttu-id="89e87-117">Pour définir le titre d’une fenêtre de console, utilisez la fonction [**SetConsoleTitle**](setconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="89e87-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="89e87-118">Pour récupérer la chaîne de titre d’origine, utilisez la fonction [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) .</span><span class="sxs-lookup"><span data-stu-id="89e87-118">To retrieve the original title string, use the [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="89e87-119">Cette API n’est pas recommandée et n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="89e87-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="89e87-120">Cette décision aligne intentionnellement la plateforme Windows avec d’autres systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="89e87-120">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="89e87-121">La communication à distance des applications via des utilitaires multiplateforme et des transports comme SSH peut ne pas fonctionner comme prévu si vous utilisez cette API.</span><span class="sxs-lookup"><span data-stu-id="89e87-121">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="examples"></a><span data-ttu-id="89e87-122">Exemples</span><span class="sxs-lookup"><span data-stu-id="89e87-122">Examples</span></span>

<span data-ttu-id="89e87-123">Pour obtenir un exemple, consultez [**SetConsoleTitle**](setconsoletitle.md).</span><span class="sxs-lookup"><span data-stu-id="89e87-123">For an example, see [**SetConsoleTitle**](setconsoletitle.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="89e87-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="89e87-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="89e87-125">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="89e87-125">Minimum supported client</span></span> | <span data-ttu-id="89e87-126">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="89e87-126">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="89e87-127">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="89e87-127">Minimum supported server</span></span> | <span data-ttu-id="89e87-128">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="89e87-128">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="89e87-129">En-tête</span><span class="sxs-lookup"><span data-stu-id="89e87-129">Header</span></span> | <span data-ttu-id="89e87-130">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="89e87-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="89e87-131">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="89e87-131">Library</span></span> | <span data-ttu-id="89e87-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="89e87-132">Kernel32.lib</span></span> |
| <span data-ttu-id="89e87-133">DLL</span><span class="sxs-lookup"><span data-stu-id="89e87-133">DLL</span></span> | <span data-ttu-id="89e87-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="89e87-134">Kernel32.dll</span></span> |
| <span data-ttu-id="89e87-135">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="89e87-135">Unicode and ANSI names</span></span> | <span data-ttu-id="89e87-136">**GetConsoleTitleW** (Unicode) et **GetConsoleTitleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="89e87-136">**GetConsoleTitleW** (Unicode) and **GetConsoleTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="89e87-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89e87-137">See also</span></span>

[<span data-ttu-id="89e87-138">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="89e87-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="89e87-139">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="89e87-139">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="89e87-140">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="89e87-140">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="89e87-141">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="89e87-141">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="89e87-142">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="89e87-142">**SetConsoleTitle**</span></span>](setconsoletitle.md)
