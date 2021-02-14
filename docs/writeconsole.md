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
ms.openlocfilehash: 27caf0b0a804b99fdfe695efef4c085bf0c51567
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357609"
---
# <a name="writeconsole-function"></a><span data-ttu-id="2b7a8-104">Fonction WriteConsole</span><span class="sxs-lookup"><span data-stu-id="2b7a8-104">WriteConsole function</span></span>

<span data-ttu-id="2b7a8-105">Écrit une chaîne de caractères dans une mémoire tampon d’écran de console en commençant à l’emplacement actuel du curseur.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-105">Writes a character string to a console screen buffer beginning at the current cursor location.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b7a8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b7a8-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## <a name="parameters"></a><span data-ttu-id="2b7a8-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2b7a8-107">Parameters</span></span>

<span data-ttu-id="2b7a8-108">*hConsoleOutput* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="2b7a8-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="2b7a8-109">Handle vers la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="2b7a8-110">Le handle doit avoir le droit d’accès **GENERIC\_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="2b7a8-111">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="2b7a8-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="2b7a8-112">*lpBuffer* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="2b7a8-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="2b7a8-113">Pointeur vers une mémoire tampon qui contient les caractères à écrire dans la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-113">A pointer to a buffer that contains characters to be written to the console screen buffer.</span></span> <span data-ttu-id="2b7a8-114">Il doit s’agir d’un tableau de `char` pour `WriteConsoleA` ou de `wchar_t` pour `WriteConsoleW`.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-114">This is expected to be an array of either `char` for `WriteConsoleA` or `wchar_t` for `WriteConsoleW`.</span></span>

<span data-ttu-id="2b7a8-115">*nNumberOfCharsToWrite* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="2b7a8-115">*nNumberOfCharsToWrite* \[in\]</span></span>  
<span data-ttu-id="2b7a8-116">Nombre de caractères à écrire.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-116">The number of characters to be written.</span></span> <span data-ttu-id="2b7a8-117">Si la taille totale du nombre spécifié de caractères dépasse le tas disponible, la fonction échoue avec **ERROR\_NOT\_ENOUGH\_MEMORY**.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-117">If the total size of the specified number of characters exceeds the available heap, the function fails with **ERROR\_NOT\_ENOUGH\_MEMORY**.</span></span>

<span data-ttu-id="2b7a8-118">*lpNumberOfCharsWritten* \[sortie, facultatif\]</span><span class="sxs-lookup"><span data-stu-id="2b7a8-118">*lpNumberOfCharsWritten* \[out, optional\]</span></span>  
<span data-ttu-id="2b7a8-119">Pointeur vers une variable qui reçoit le nombre de caractères réellement écrits.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-119">A pointer to a variable that receives the number of characters actually written.</span></span>

<span data-ttu-id="2b7a8-120">*lpReserved* Réservé ; doit être **NULL**.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-120">*lpReserved* Reserved; must be **NULL**.</span></span>

## <a name="return-value"></a><span data-ttu-id="2b7a8-121">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="2b7a8-121">Return value</span></span>

<span data-ttu-id="2b7a8-122">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="2b7a8-123">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="2b7a8-124">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="2b7a8-124">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="2b7a8-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="2b7a8-125">Remarks</span></span>

<span data-ttu-id="2b7a8-126">La fonction **WriteConsole** écrit des caractères dans la mémoire tampon d’écran de console, à la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-126">The **WriteConsole** function writes characters to the console screen buffer at the current cursor position.</span></span> <span data-ttu-id="2b7a8-127">La position du curseur avance à mesure que des caractères sont écrits.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-127">The cursor position advances as characters are written.</span></span> <span data-ttu-id="2b7a8-128">La fonction [**SetConsoleCursorPosition**](setconsolecursorposition.md) définit la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-128">The [**SetConsoleCursorPosition**](setconsolecursorposition.md) function sets the current cursor position.</span></span>

<span data-ttu-id="2b7a8-129">Les caractères sont écrits en utilisant les attributs de couleur de premier plan et d’arrière-plan associés à la mémoire tampon d’écran de console.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-129">Characters are written using the foreground and background color attributes associated with the console screen buffer.</span></span> <span data-ttu-id="2b7a8-130">La fonction [**SetConsoleTextAttribute**](setconsoletextattribute.md) change ces couleurs.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-130">The [**SetConsoleTextAttribute**](setconsoletextattribute.md) function changes these colors.</span></span> <span data-ttu-id="2b7a8-131">Pour déterminer les attributs de couleur actuels et la position actuelle du curseur, utilisez [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span><span class="sxs-lookup"><span data-stu-id="2b7a8-131">To determine the current color attributes and the current cursor position, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span></span>

<span data-ttu-id="2b7a8-132">Tous les modes d’entrée qui affectent le comportement de la fonction [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) ont le même effet sur **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-132">All of the input modes that affect the behavior of the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) function have the same effect on **WriteConsole**.</span></span> <span data-ttu-id="2b7a8-133">Pour récupérer et définir les modes de sortie d’une mémoire tampon d’écran de console, utilisez les fonctions [**GetConsoleMode**](getconsolemode.md) et [**SetConsoleMode**](setconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="2b7a8-133">To retrieve and set the output modes of a console screen buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

<span data-ttu-id="2b7a8-134">**WriteConsole** échoue si elle est utilisée avec un handle standard qui est redirigé vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-134">**WriteConsole** fails if it is used with a standard handle that is redirected to a file.</span></span> <span data-ttu-id="2b7a8-135">Si une application traite une sortie multilingue qui peut être redirigée, déterminez si le handle de sortie est un handle de console (une méthode consiste à appeler la fonction [**GetConsoleMode**](getconsolemode.md) et à vérifier si elle a réussi).</span><span class="sxs-lookup"><span data-stu-id="2b7a8-135">If an application processes multilingual output that can be redirected, determine whether the output handle is a console handle (one method is to call the [**GetConsoleMode**](getconsolemode.md) function and check whether it succeeds).</span></span> <span data-ttu-id="2b7a8-136">Si le handle est un handle de console, appelez **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-136">If the handle is a console handle, call **WriteConsole**.</span></span> <span data-ttu-id="2b7a8-137">Si le handle n’est pas un handle de console, la sortie est redirigée et vous devez appeler [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) pour effectuer les E/S.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-137">If the handle is not a console handle, the output is redirected and you should call [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) to perform the I/O.</span></span> <span data-ttu-id="2b7a8-138">Veillez à faire précéder un fichier texte brut Unicode par une marque d’ordre des octets.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-138">Be sure to prefix a Unicode plain text file with a byte order mark.</span></span> <span data-ttu-id="2b7a8-139">Pour plus d’informations, consultez [Utilisation des marques d’ordre des octets](/windows/win32/intl/using-byte-order-marks).</span><span class="sxs-lookup"><span data-stu-id="2b7a8-139">For more information, see [Using Byte Order Marks](/windows/win32/intl/using-byte-order-marks).</span></span>

<span data-ttu-id="2b7a8-140">Bien qu’une application puisse utiliser **WriteConsole** en mode ANSI pour écrire des caractères ANSI, les consoles ne prennent pas en charge les séquences « échappement ANSI » ou « terminal virtuel », sauf si elles sont activées.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-140">Although an application can use **WriteConsole** in ANSI mode to write ANSI characters, consoles do not support "ANSI escape" or "virtual terminal" sequences unless enabled.</span></span> <span data-ttu-id="2b7a8-141">Pour plus d’informations et l’applicabilité selon la version du système d’exploitation, consultez [**Séquences de terminal virtuel de la console**](console-virtual-terminal-sequences.md).</span><span class="sxs-lookup"><span data-stu-id="2b7a8-141">See [**Console Virtual Terminal Sequences**](console-virtual-terminal-sequences.md) for more information and for operating system version applicability.</span></span>

<span data-ttu-id="2b7a8-142">Quand les séquences d’échappement du terminal virtuel ne sont pas activées, les fonctions de la console peuvent fournir des fonctionnalités équivalentes.</span><span class="sxs-lookup"><span data-stu-id="2b7a8-142">When virtual terminal escape sequences are not enabled, console functions can provide equivalent functionality.</span></span> <span data-ttu-id="2b7a8-143">Pour plus d’informations, consultez [**SetCursorPos**](/windows/win32/api/winuser/nf-winuser-setcursorpos), [**SetConsoleTextAttribute**](setconsoletextattribute.md) et [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span><span class="sxs-lookup"><span data-stu-id="2b7a8-143">For more information, see [**SetCursorPos**](/windows/win32/api/winuser/nf-winuser-setcursorpos), [**SetConsoleTextAttribute**](setconsoletextattribute.md), and [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="2b7a8-144">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2b7a8-144">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="2b7a8-145">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="2b7a8-145">Minimum supported client</span></span> | <span data-ttu-id="2b7a8-146">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="2b7a8-146">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="2b7a8-147">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="2b7a8-147">Minimum supported server</span></span> | <span data-ttu-id="2b7a8-148">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="2b7a8-148">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="2b7a8-149">En-tête</span><span class="sxs-lookup"><span data-stu-id="2b7a8-149">Header</span></span> | <span data-ttu-id="2b7a8-150">ConsoleApi.h (via WinCon.h, inclure Windows.h)</span><span class="sxs-lookup"><span data-stu-id="2b7a8-150">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="2b7a8-151">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="2b7a8-151">Library</span></span> | <span data-ttu-id="2b7a8-152">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="2b7a8-152">Kernel32.lib</span></span> |
| <span data-ttu-id="2b7a8-153">DLL</span><span class="sxs-lookup"><span data-stu-id="2b7a8-153">DLL</span></span> | <span data-ttu-id="2b7a8-154">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2b7a8-154">Kernel32.dll</span></span> |
| <span data-ttu-id="2b7a8-155">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="2b7a8-155">Unicode and ANSI names</span></span> | <span data-ttu-id="2b7a8-156">**WriteConsoleW** (Unicode) et **WriteConsoleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="2b7a8-156">**WriteConsoleW** (Unicode) and **WriteConsoleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="2b7a8-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b7a8-157">See also</span></span>

[<span data-ttu-id="2b7a8-158">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="2b7a8-158">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2b7a8-159">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="2b7a8-159">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="2b7a8-160">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="2b7a8-160">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="2b7a8-161">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="2b7a8-161">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="2b7a8-162">Méthodes d’entrée et de sortie</span><span class="sxs-lookup"><span data-stu-id="2b7a8-162">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="2b7a8-163">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="2b7a8-163">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="2b7a8-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="2b7a8-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="2b7a8-165">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="2b7a8-165">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="2b7a8-166">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="2b7a8-166">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="2b7a8-167">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="2b7a8-167">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="2b7a8-168">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="2b7a8-168">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

[<span data-ttu-id="2b7a8-169">**SetCursorPos**</span><span class="sxs-lookup"><span data-stu-id="2b7a8-169">**SetCursorPos**</span></span>](/windows/win32/api/winuser/nf-winuser-setcursorpos)

[<span data-ttu-id="2b7a8-170">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="2b7a8-170">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)