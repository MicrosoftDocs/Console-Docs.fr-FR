---
title: GetConsoleOriginalTitle fonction)
description: Consultez les informations de référence sur la fonction GetConsoleOriginalTitle, qui récupère le titre d’origine de la fenêtre de console active.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: ad12ff7b931b6bbc36a7fb0e9e0ee2ac3512a1f5
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037997"
---
# <a name="getconsoleoriginaltitle-function"></a><span data-ttu-id="c70f3-104">GetConsoleOriginalTitle fonction)</span><span class="sxs-lookup"><span data-stu-id="c70f3-104">GetConsoleOriginalTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="c70f3-105">Récupère le titre d’origine de la fenêtre de console active.</span><span class="sxs-lookup"><span data-stu-id="c70f3-105">Retrieves the original title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="c70f3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c70f3-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a><span data-ttu-id="c70f3-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c70f3-107">Parameters</span></span>

<span data-ttu-id="c70f3-108">*lpConsoleTitle* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="c70f3-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="c70f3-109">Pointeur vers une mémoire tampon qui reçoit une chaîne se terminant par null et contenant le titre d’origine.</span><span class="sxs-lookup"><span data-stu-id="c70f3-109">A pointer to a buffer that receives a null-terminated string containing the original title.</span></span>

<span data-ttu-id="c70f3-110">*nSize* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="c70f3-110">*nSize* \[in\]</span></span>  
<span data-ttu-id="c70f3-111">Taille de la mémoire tampon *lpConsoleTitle* , en caractères.</span><span class="sxs-lookup"><span data-stu-id="c70f3-111">The size of the *lpConsoleTitle* buffer, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="c70f3-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="c70f3-112">Return value</span></span>

<span data-ttu-id="c70f3-113">Si la fonction est réussie, la valeur de retour est la longueur de la chaîne copiée dans la mémoire tampon, en caractères.</span><span class="sxs-lookup"><span data-stu-id="c70f3-113">If the function succeeds, the return value is the length of the string copied to the buffer, in characters.</span></span>

<span data-ttu-id="c70f3-114">Si la mémoire tampon n’est pas assez grande pour stocker le titre, la valeur de retour est zéro et [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) retourne une **erreur de \_ réussite** .</span><span class="sxs-lookup"><span data-stu-id="c70f3-114">If the buffer is not large enough to store the title, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns **ERROR\_SUCCESS** .</span></span>

<span data-ttu-id="c70f3-115">Si la fonction échoue, la valeur de retour est zéro et [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) retourne le code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c70f3-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c70f3-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="c70f3-116">Remarks</span></span>

<span data-ttu-id="c70f3-117">Pour définir le titre d’une fenêtre de console, utilisez la fonction [**SetConsoleTitle**](setconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="c70f3-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="c70f3-118">Pour récupérer la chaîne de titre actuelle, utilisez la fonction [**GetConsoleTitle**](getconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="c70f3-118">To retrieve the current title string, use the [**GetConsoleTitle**](getconsoletitle.md) function.</span></span>

<span data-ttu-id="c70f3-119">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0600 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="c70f3-119">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0600 or later.</span></span> <span data-ttu-id="c70f3-120">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="c70f3-120">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

> [!TIP]
> <span data-ttu-id="c70f3-121">Cette API n’est pas recommandée et n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="c70f3-121">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="c70f3-122">Cette décision aligne intentionnellement la plateforme Windows avec d’autres systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="c70f3-122">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="c70f3-123">La communication à distance des applications via des utilitaires multiplateforme et des transports comme SSH peut ne pas fonctionner comme prévu si vous utilisez cette API.</span><span class="sxs-lookup"><span data-stu-id="c70f3-123">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="c70f3-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c70f3-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c70f3-125">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="c70f3-125">Minimum supported client</span></span> | <span data-ttu-id="c70f3-126">Applications de \[ Bureau Windows Vista uniquement\]</span><span class="sxs-lookup"><span data-stu-id="c70f3-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="c70f3-127">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="c70f3-127">Minimum supported server</span></span> | <span data-ttu-id="c70f3-128">Applications de bureau Windows Server 2008 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="c70f3-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="c70f3-129">En-tête</span><span class="sxs-lookup"><span data-stu-id="c70f3-129">Header</span></span> | <span data-ttu-id="c70f3-130">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c70f3-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c70f3-131">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="c70f3-131">Library</span></span> | <span data-ttu-id="c70f3-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="c70f3-132">Kernel32.lib</span></span> |
| <span data-ttu-id="c70f3-133">DLL</span><span class="sxs-lookup"><span data-stu-id="c70f3-133">DLL</span></span> | <span data-ttu-id="c70f3-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c70f3-134">Kernel32.dll</span></span> |
| <span data-ttu-id="c70f3-135">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="c70f3-135">Unicode and ANSI names</span></span> | <span data-ttu-id="c70f3-136">**GetConsoleOriginalTitleW** (Unicode) et **GetConsoleOriginalTitleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="c70f3-136">**GetConsoleOriginalTitleW** (Unicode) and **GetConsoleOriginalTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="c70f3-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c70f3-137">See also</span></span>

[<span data-ttu-id="c70f3-138">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="c70f3-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c70f3-139">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="c70f3-139">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="c70f3-140">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="c70f3-140">**SetConsoleTitle**</span></span>](setconsoletitle.md)
