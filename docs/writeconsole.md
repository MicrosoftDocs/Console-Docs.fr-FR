---
title: Fonction WriteConsole
description: Écrit une chaîne de caractères dans une mémoire tampon d’écran de console en commençant à l’emplacement actuel du curseur.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/WriteConsole
- wincon/WriteConsole
- WriteConsole
- consoleapi/WriteConsoleA
- wincon/WriteConsoleA
- WriteConsoleA
- consoleapi/WriteConsoleW
- wincon/WriteConsoleW
- WriteConsoleW
MS-HAID:
- '\_win32\_writeconsole'
- base.writeconsole
- consoles.writeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1a13d9ef-75a9-49fd-9717-207f18612b59
topic_type:
- apiref
api_name:
- WriteConsole
- WriteConsoleA
- WriteConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 426aa6711e46e0d5cda1eb1b7dab7b2b0b7156d6
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420288"
---
# <a name="writeconsole-function"></a><span data-ttu-id="24154-104">Fonction WriteConsole</span><span class="sxs-lookup"><span data-stu-id="24154-104">WriteConsole function</span></span>

<span data-ttu-id="24154-105">Écrit une chaîne de caractères dans une mémoire tampon d’écran de console en commençant à l’emplacement actuel du curseur.</span><span class="sxs-lookup"><span data-stu-id="24154-105">Writes a character string to a console screen buffer beginning at the current cursor location.</span></span>

## <a name="syntax"></a><span data-ttu-id="24154-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24154-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## <a name="parameters"></a><span data-ttu-id="24154-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="24154-107">Parameters</span></span>

<span data-ttu-id="24154-108">*hConsoleOutput* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="24154-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="24154-109">Handle vers la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="24154-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="24154-110">Le handle doit avoir le droit d’accès **GENERIC\_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="24154-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="24154-111">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="24154-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="24154-112">*lpBuffer* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="24154-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="24154-113">Pointeur vers une mémoire tampon qui contient les caractères à écrire dans la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="24154-113">A pointer to a buffer that contains characters to be written to the console screen buffer.</span></span> <span data-ttu-id="24154-114">Il doit s’agir d’un tableau de `char` pour `WriteConsoleA` ou de `wchar_t` pour `WriteConsoleW`.</span><span class="sxs-lookup"><span data-stu-id="24154-114">This is expected to be an array of either `char` for `WriteConsoleA` or `wchar_t` for `WriteConsoleW`.</span></span>

<span data-ttu-id="24154-115">*nNumberOfCharsToWrite* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="24154-115">*nNumberOfCharsToWrite* \[in\]</span></span>  
<span data-ttu-id="24154-116">Nombre de caractères à écrire.</span><span class="sxs-lookup"><span data-stu-id="24154-116">The number of characters to be written.</span></span> <span data-ttu-id="24154-117">Si la taille totale du nombre spécifié de caractères dépasse le tas disponible, la fonction échoue avec **ERROR\_NOT\_ENOUGH\_MEMORY**.</span><span class="sxs-lookup"><span data-stu-id="24154-117">If the total size of the specified number of characters exceeds the available heap, the function fails with **ERROR\_NOT\_ENOUGH\_MEMORY**.</span></span>

<span data-ttu-id="24154-118">*lpNumberOfCharsWritten* \[sortie, facultatif\]</span><span class="sxs-lookup"><span data-stu-id="24154-118">*lpNumberOfCharsWritten* \[out, optional\]</span></span>  
<span data-ttu-id="24154-119">Pointeur vers une variable qui reçoit le nombre de caractères réellement écrits.</span><span class="sxs-lookup"><span data-stu-id="24154-119">A pointer to a variable that receives the number of characters actually written.</span></span>

<span data-ttu-id="24154-120">*lpReserved* Réservé ; doit être **NULL**.</span><span class="sxs-lookup"><span data-stu-id="24154-120">*lpReserved* Reserved; must be **NULL**.</span></span>

## <a name="return-value"></a><span data-ttu-id="24154-121">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="24154-121">Return value</span></span>

<span data-ttu-id="24154-122">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="24154-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="24154-123">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="24154-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="24154-124">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="24154-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="24154-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="24154-125">Remarks</span></span>

<span data-ttu-id="24154-126">La fonction **WriteConsole** écrit des caractères dans la mémoire tampon d’écran de console, à la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="24154-126">The **WriteConsole** function writes characters to the console screen buffer at the current cursor position.</span></span> <span data-ttu-id="24154-127">La position du curseur avance à mesure que des caractères sont écrits.</span><span class="sxs-lookup"><span data-stu-id="24154-127">The cursor position advances as characters are written.</span></span> <span data-ttu-id="24154-128">La fonction [**SetConsoleCursorPosition**](setconsolecursorposition.md) définit la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="24154-128">The [**SetConsoleCursorPosition**](setconsolecursorposition.md) function sets the current cursor position.</span></span>

<span data-ttu-id="24154-129">Les caractères sont écrits en utilisant les attributs de couleur de premier plan et d’arrière-plan associés à la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="24154-129">Characters are written using the foreground and background color attributes associated with the console screen buffer.</span></span> <span data-ttu-id="24154-130">La fonction [**SetConsoleTextAttribute**](setconsoletextattribute.md) change ces couleurs.</span><span class="sxs-lookup"><span data-stu-id="24154-130">The [**SetConsoleTextAttribute**](setconsoletextattribute.md) function changes these colors.</span></span> <span data-ttu-id="24154-131">Pour déterminer les attributs de couleur actuels et la position actuelle du curseur, utilisez [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span><span class="sxs-lookup"><span data-stu-id="24154-131">To determine the current color attributes and the current cursor position, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span></span>

<span data-ttu-id="24154-132">Tous les modes d’entrée qui affectent le comportement de la fonction [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ont le même effet sur **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="24154-132">All of the input modes that affect the behavior of the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) function have the same effect on **WriteConsole**.</span></span> <span data-ttu-id="24154-133">Pour récupérer et définir les modes de sortie d’une mémoire tampon d’écran de console, utilisez les fonctions [**GetConsoleMode**](getconsolemode.md) et [**SetConsoleMode**](setconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="24154-133">To retrieve and set the output modes of a console screen buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

<span data-ttu-id="24154-134">**WriteConsole** échoue si elle est utilisée avec un handle standard qui est redirigé vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="24154-134">**WriteConsole** fails if it is used with a standard handle that is redirected to a file.</span></span> <span data-ttu-id="24154-135">Si une application traite une sortie multilingue qui peut être redirigée, déterminez si le handle de sortie est un handle de console (une méthode consiste à appeler la fonction [**GetConsoleMode**](getconsolemode.md) et à vérifier si elle a réussi).</span><span class="sxs-lookup"><span data-stu-id="24154-135">If an application processes multilingual output that can be redirected, determine whether the output handle is a console handle (one method is to call the [**GetConsoleMode**](getconsolemode.md) function and check whether it succeeds).</span></span> <span data-ttu-id="24154-136">Si le handle est un handle de console, appelez **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="24154-136">If the handle is a console handle, call **WriteConsole**.</span></span> <span data-ttu-id="24154-137">Si le handle n’est pas un handle de console, la sortie est redirigée et vous devez appeler [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) pour effectuer les E/S.</span><span class="sxs-lookup"><span data-stu-id="24154-137">If the handle is not a console handle, the output is redirected and you should call [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) to perform the I/O.</span></span> <span data-ttu-id="24154-138">Veillez à faire précéder un fichier texte brut Unicode par une marque d’ordre des octets.</span><span class="sxs-lookup"><span data-stu-id="24154-138">Be sure to prefix a Unicode plain text file with a byte order mark.</span></span> <span data-ttu-id="24154-139">Pour plus d’informations, consultez [Utilisation des marques d’ordre des octets](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span><span class="sxs-lookup"><span data-stu-id="24154-139">For more information, see [Using Byte Order Marks](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span></span>

<span data-ttu-id="24154-140">Bien qu’une application puisse utiliser **WriteConsole** en mode ANSI pour écrire des caractères ANSI, les consoles ne prennent pas en charge les séquences « échappement ANSI » ou « terminal virtuel », sauf si elles sont activées.</span><span class="sxs-lookup"><span data-stu-id="24154-140">Although an application can use **WriteConsole** in ANSI mode to write ANSI characters, consoles do not support "ANSI escape" or "virtual terminal" sequences unless enabled.</span></span> <span data-ttu-id="24154-141">Pour plus d’informations et l’applicabilité selon la version du système d’exploitation, consultez [**Séquences de terminal virtuel de la console**](console-virtual-terminal-sequences.md).</span><span class="sxs-lookup"><span data-stu-id="24154-141">See [**Console Virtual Terminal Sequences**](console-virtual-terminal-sequences.md) for more information and for operating system version applicability.</span></span>

<span data-ttu-id="24154-142">Quand les séquences d’échappement du terminal virtuel ne sont pas activées, les fonctions de la console peuvent fournir des fonctionnalités équivalentes.</span><span class="sxs-lookup"><span data-stu-id="24154-142">When virtual terminal escape sequences are not enabled, console functions can provide equivalent functionality.</span></span> <span data-ttu-id="24154-143">Pour plus d’informations, consultez [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md) et [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span><span class="sxs-lookup"><span data-stu-id="24154-143">For more information, see [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md), and [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="24154-144">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="24154-144">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="24154-145">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="24154-145">Minimum supported client</span></span> | <span data-ttu-id="24154-146">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="24154-146">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="24154-147">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="24154-147">Minimum supported server</span></span> | <span data-ttu-id="24154-148">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="24154-148">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="24154-149">En-tête</span><span class="sxs-lookup"><span data-stu-id="24154-149">Header</span></span> | <span data-ttu-id="24154-150">ConsoleApi.h (via WinCon.h, inclure Windows.h)</span><span class="sxs-lookup"><span data-stu-id="24154-150">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="24154-151">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="24154-151">Library</span></span> | <span data-ttu-id="24154-152">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="24154-152">Kernel32.lib</span></span> |
| <span data-ttu-id="24154-153">DLL</span><span class="sxs-lookup"><span data-stu-id="24154-153">DLL</span></span> | <span data-ttu-id="24154-154">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="24154-154">Kernel32.dll</span></span> |
| <span data-ttu-id="24154-155">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="24154-155">Unicode and ANSI names</span></span> | <span data-ttu-id="24154-156">**WriteConsoleW** (Unicode) et **WriteConsoleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="24154-156">**WriteConsoleW** (Unicode) and **WriteConsoleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="24154-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24154-157">See also</span></span>

[<span data-ttu-id="24154-158">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="24154-158">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="24154-159">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="24154-159">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="24154-160">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="24154-160">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="24154-161">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="24154-161">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="24154-162">Méthodes d’entrée et de sortie</span><span class="sxs-lookup"><span data-stu-id="24154-162">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="24154-163">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="24154-163">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="24154-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="24154-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="24154-165">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="24154-165">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="24154-166">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="24154-166">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="24154-167">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="24154-167">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="24154-168">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="24154-168">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

<span data-ttu-id="24154-169">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="24154-169">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span></span>

[<span data-ttu-id="24154-170">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="24154-170">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
