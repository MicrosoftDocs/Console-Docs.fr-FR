---
title: SetConsoleTextAttribute fonction)
description: Définit les attributs des caractères écrits dans la mémoire tampon d’écran de la console par la fonction WriteFile ou WriteConsole, ou en écho par la fonction ReadFile ou ReadConsole.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/SetConsoleTextAttribute
- wincon/SetConsoleTextAttribute
- SetConsoleTextAttribute
MS-HAID:
- '\_win32\_setconsoletextattribute'
- base.setconsoletextattribute
- consoles.setconsoletextattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9fba5bb5-b999-4abd-ab39-7a63d58b8074
topic_type:
- apiref
api_name:
- SetConsoleTextAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 03925af2668774a36de33bfe6ea5fcdc1b475d5b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039317"
---
# <a name="setconsoletextattribute-function"></a><span data-ttu-id="9afc1-104">SetConsoleTextAttribute fonction)</span><span class="sxs-lookup"><span data-stu-id="9afc1-104">SetConsoleTextAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="9afc1-105">Définit les attributs des caractères écrits dans la mémoire tampon d’écran de la console par la fonction [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ou [**WriteConsole**](writeconsole.md) , ou en écho par la fonction [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ou [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="9afc1-105">Sets the attributes of characters written to the console screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="9afc1-106">Cette fonction affecte le texte écrit après l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="9afc1-106">This function affects text written after the function call.</span></span>

## <a name="syntax"></a><span data-ttu-id="9afc1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9afc1-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleTextAttribute(
  _In_ HANDLE hConsoleOutput,
  _In_ WORD   wAttributes
);
```

## <a name="parameters"></a><span data-ttu-id="9afc1-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9afc1-108">Parameters</span></span>

<span data-ttu-id="9afc1-109">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="9afc1-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="9afc1-110">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="9afc1-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="9afc1-111">Le handle doit avoir le droit d’accès **\_ en lecture générique** .</span><span class="sxs-lookup"><span data-stu-id="9afc1-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="9afc1-112">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="9afc1-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="9afc1-113">*wAttributes* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="9afc1-113">*wAttributes* \[in\]</span></span>  
<span data-ttu-id="9afc1-114">[Attributs de caractère](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="9afc1-114">The [character attributes](console-screen-buffers.md#character-attributes).</span></span>

## <a name="return-value"></a><span data-ttu-id="9afc1-115">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="9afc1-115">Return value</span></span>

<span data-ttu-id="9afc1-116">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="9afc1-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="9afc1-117">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="9afc1-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="9afc1-118">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="9afc1-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="9afc1-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="9afc1-119">Remarks</span></span>

<span data-ttu-id="9afc1-120">Pour déterminer les attributs de couleur actuels d’une mémoire tampon d’écran, appelez la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="9afc1-120">To determine the current color attributes of a screen buffer, call the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

> [!TIP]
> <span data-ttu-id="9afc1-121">Cette API possède un **[terminal virtuel](console-virtual-terminal-sequences.md)** équivalent dans les séquences de **[mise en forme du texte](console-virtual-terminal-sequences.md#text-formatting)** .</span><span class="sxs-lookup"><span data-stu-id="9afc1-121">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** sequences.</span></span> <span data-ttu-id="9afc1-122">Les _séquences de terminaux virtuels_ sont recommandées pour tout développement nouveau et en cours.</span><span class="sxs-lookup"><span data-stu-id="9afc1-122">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="9afc1-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="9afc1-123">Examples</span></span>

<span data-ttu-id="9afc1-124">Pour obtenir un exemple, consultez [utilisation des fonctions d’entrée et de sortie High-Level](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="9afc1-124">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="9afc1-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9afc1-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="9afc1-126">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="9afc1-126">Minimum supported client</span></span> | <span data-ttu-id="9afc1-127">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="9afc1-127">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="9afc1-128">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="9afc1-128">Minimum supported server</span></span> | <span data-ttu-id="9afc1-129">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="9afc1-129">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="9afc1-130">En-tête</span><span class="sxs-lookup"><span data-stu-id="9afc1-130">Header</span></span> | <span data-ttu-id="9afc1-131">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9afc1-131">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="9afc1-132">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="9afc1-132">Library</span></span> | <span data-ttu-id="9afc1-133">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="9afc1-133">Kernel32.lib</span></span> |
| <span data-ttu-id="9afc1-134">DLL</span><span class="sxs-lookup"><span data-stu-id="9afc1-134">DLL</span></span> | <span data-ttu-id="9afc1-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9afc1-135">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="9afc1-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9afc1-136">See also</span></span>

[<span data-ttu-id="9afc1-137">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="9afc1-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="9afc1-138">Mémoires tampons d’écran d’une console</span><span class="sxs-lookup"><span data-stu-id="9afc1-138">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="9afc1-139">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="9afc1-139">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="9afc1-140">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="9afc1-140">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="9afc1-141">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="9afc1-141">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="9afc1-142">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="9afc1-142">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="9afc1-143">**Appel**</span><span class="sxs-lookup"><span data-stu-id="9afc1-143">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
