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
ms.openlocfilehash: b08f4b0b628f4d20029b81873b4fc25077a11029
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358559"
---
# <a name="setconsoletextattribute-function"></a><span data-ttu-id="e8f08-104">SetConsoleTextAttribute fonction)</span><span class="sxs-lookup"><span data-stu-id="e8f08-104">SetConsoleTextAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="e8f08-105">Définit les attributs des caractères écrits dans la mémoire tampon d’écran de la console par la fonction [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) ou [**WriteConsole**](writeconsole.md) , ou en écho par la fonction [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) ou [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="e8f08-105">Sets the attributes of characters written to the console screen buffer by the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) or [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="e8f08-106">Cette fonction affecte le texte écrit après l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="e8f08-106">This function affects text written after the function call.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8f08-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8f08-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleTextAttribute(
  _In_ HANDLE hConsoleOutput,
  _In_ WORD   wAttributes
);
```

## <a name="parameters"></a><span data-ttu-id="e8f08-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8f08-108">Parameters</span></span>

<span data-ttu-id="e8f08-109">*hConsoleOutput* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="e8f08-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="e8f08-110">Handle vers la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="e8f08-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="e8f08-111">Le handle doit avoir le droit d’accès **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="e8f08-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="e8f08-112">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="e8f08-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="e8f08-113">*wAttributes* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="e8f08-113">*wAttributes* \[in\]</span></span>  
<span data-ttu-id="e8f08-114">[Attributs de caractère](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="e8f08-114">The [character attributes](console-screen-buffers.md#character-attributes).</span></span>

## <a name="return-value"></a><span data-ttu-id="e8f08-115">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="e8f08-115">Return value</span></span>

<span data-ttu-id="e8f08-116">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="e8f08-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e8f08-117">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="e8f08-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e8f08-118">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="e8f08-118">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="e8f08-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="e8f08-119">Remarks</span></span>

<span data-ttu-id="e8f08-120">Pour déterminer les attributs de couleur actuels d’une mémoire tampon d’écran, appelez la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="e8f08-120">To determine the current color attributes of a screen buffer, call the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

> [!TIP]
> <span data-ttu-id="e8f08-121">Cette API possède un **[terminal virtuel](console-virtual-terminal-sequences.md)** équivalent dans les séquences de **[mise en forme du texte](console-virtual-terminal-sequences.md#text-formatting)** .</span><span class="sxs-lookup"><span data-stu-id="e8f08-121">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** sequences.</span></span> <span data-ttu-id="e8f08-122">Les _séquences de terminaux virtuels_ sont recommandées pour tout développement nouveau et en cours.</span><span class="sxs-lookup"><span data-stu-id="e8f08-122">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="e8f08-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="e8f08-123">Examples</span></span>

<span data-ttu-id="e8f08-124">Pour obtenir un exemple, consultez [utilisation des fonctions d’entrée et de sortie High-Level](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="e8f08-124">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="e8f08-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e8f08-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e8f08-126">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="e8f08-126">Minimum supported client</span></span> | <span data-ttu-id="e8f08-127">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="e8f08-127">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="e8f08-128">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="e8f08-128">Minimum supported server</span></span> | <span data-ttu-id="e8f08-129">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="e8f08-129">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="e8f08-130">En-tête</span><span class="sxs-lookup"><span data-stu-id="e8f08-130">Header</span></span> | <span data-ttu-id="e8f08-131">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e8f08-131">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="e8f08-132">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="e8f08-132">Library</span></span> | <span data-ttu-id="e8f08-133">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="e8f08-133">Kernel32.lib</span></span> |
| <span data-ttu-id="e8f08-134">DLL</span><span class="sxs-lookup"><span data-stu-id="e8f08-134">DLL</span></span> | <span data-ttu-id="e8f08-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e8f08-135">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="e8f08-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8f08-136">See also</span></span>

[<span data-ttu-id="e8f08-137">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="e8f08-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e8f08-138">Mémoires tampons d’écran d’une console</span><span class="sxs-lookup"><span data-stu-id="e8f08-138">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="e8f08-139">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="e8f08-139">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="e8f08-140">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="e8f08-140">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="e8f08-141">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="e8f08-141">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="e8f08-142">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="e8f08-142">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="e8f08-143">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="e8f08-143">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)