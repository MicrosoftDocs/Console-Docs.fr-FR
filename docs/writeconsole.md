---
title: WriteConsole fonction)
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
ms.openlocfilehash: 9023372cf585e9b3645e7dc0a54e46a665935ad4
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037127"
---
# <a name="writeconsole-function"></a><span data-ttu-id="50897-104">WriteConsole fonction)</span><span class="sxs-lookup"><span data-stu-id="50897-104">WriteConsole function</span></span>

<span data-ttu-id="50897-105">Écrit une chaîne de caractères dans une mémoire tampon d’écran de console en commençant à l’emplacement actuel du curseur.</span><span class="sxs-lookup"><span data-stu-id="50897-105">Writes a character string to a console screen buffer beginning at the current cursor location.</span></span>

## <a name="syntax"></a><span data-ttu-id="50897-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50897-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## <a name="parameters"></a><span data-ttu-id="50897-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="50897-107">Parameters</span></span>

<span data-ttu-id="50897-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="50897-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="50897-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="50897-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="50897-110">Le descripteur doit avoir le droit d’accès en **\_ écriture générique** .</span><span class="sxs-lookup"><span data-stu-id="50897-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="50897-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="50897-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="50897-112">*lpBuffer* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="50897-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="50897-113">Pointeur vers une mémoire tampon qui contient les caractères à écrire dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="50897-113">A pointer to a buffer that contains characters to be written to the console screen buffer.</span></span> <span data-ttu-id="50897-114">Il doit s’agir d’un tableau de `char` pour `WriteConsoleA` ou `wchar_t` pour `WriteConsoleW` .</span><span class="sxs-lookup"><span data-stu-id="50897-114">This is expected to be an array of either `char` for `WriteConsoleA` or `wchar_t` for `WriteConsoleW`.</span></span>

<span data-ttu-id="50897-115">*nNumberOfCharsToWrite* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="50897-115">*nNumberOfCharsToWrite* \[in\]</span></span>  
<span data-ttu-id="50897-116">Nombre de caractères à écrire.</span><span class="sxs-lookup"><span data-stu-id="50897-116">The number of characters to be written.</span></span> <span data-ttu-id="50897-117">Si la taille totale du nombre spécifié de caractères dépasse le tas disponible, la fonction échoue avec une **erreur \_ de \_ \_ mémoire insuffisante** .</span><span class="sxs-lookup"><span data-stu-id="50897-117">If the total size of the specified number of characters exceeds the available heap, the function fails with **ERROR\_NOT\_ENOUGH\_MEMORY** .</span></span>

<span data-ttu-id="50897-118">*lpNumberOfCharsWritten* \[ out, facultatif\]</span><span class="sxs-lookup"><span data-stu-id="50897-118">*lpNumberOfCharsWritten* \[out, optional\]</span></span>  
<span data-ttu-id="50897-119">Pointeur vers une variable qui reçoit le nombre de caractères réellement écrits.</span><span class="sxs-lookup"><span data-stu-id="50897-119">A pointer to a variable that receives the number of characters actually written.</span></span>

<span data-ttu-id="50897-120">*lpReserved* Réservé doit avoir la **valeur null** .</span><span class="sxs-lookup"><span data-stu-id="50897-120">*lpReserved* Reserved; must be **NULL** .</span></span>

## <a name="return-value"></a><span data-ttu-id="50897-121">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="50897-121">Return value</span></span>

<span data-ttu-id="50897-122">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="50897-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="50897-123">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="50897-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="50897-124">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="50897-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="50897-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="50897-125">Remarks</span></span>

<span data-ttu-id="50897-126">La fonction **WriteConsole** écrit des caractères dans la mémoire tampon d’écran de la console à la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="50897-126">The **WriteConsole** function writes characters to the console screen buffer at the current cursor position.</span></span> <span data-ttu-id="50897-127">La position du curseur avance à mesure que des caractères sont écrits.</span><span class="sxs-lookup"><span data-stu-id="50897-127">The cursor position advances as characters are written.</span></span> <span data-ttu-id="50897-128">La fonction [**SetConsoleCursorPosition**](setconsolecursorposition.md) définit la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="50897-128">The [**SetConsoleCursorPosition**](setconsolecursorposition.md) function sets the current cursor position.</span></span>

<span data-ttu-id="50897-129">Les caractères sont écrits à l’aide des attributs de couleur de premier plan et d’arrière-plan associés à la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="50897-129">Characters are written using the foreground and background color attributes associated with the console screen buffer.</span></span> <span data-ttu-id="50897-130">La fonction [**SetConsoleTextAttribute**](setconsoletextattribute.md) modifie ces couleurs.</span><span class="sxs-lookup"><span data-stu-id="50897-130">The [**SetConsoleTextAttribute**](setconsoletextattribute.md) function changes these colors.</span></span> <span data-ttu-id="50897-131">Pour déterminer les attributs de couleur actuelle et la position actuelle du curseur, utilisez [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span><span class="sxs-lookup"><span data-stu-id="50897-131">To determine the current color attributes and the current cursor position, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span></span>

<span data-ttu-id="50897-132">Tous les modes d’entrée qui affectent le comportement de la fonction [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ont le même effet sur **WriteConsole** .</span><span class="sxs-lookup"><span data-stu-id="50897-132">All of the input modes that affect the behavior of the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) function have the same effect on **WriteConsole** .</span></span> <span data-ttu-id="50897-133">Pour récupérer et définir les modes de sortie d’une mémoire tampon d’écran de la console, utilisez les fonctions [**GetConsoleMode**](getconsolemode.md) et [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="50897-133">To retrieve and set the output modes of a console screen buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

<span data-ttu-id="50897-134">**WriteConsole** échoue s’il est utilisé avec un handle standard qui est redirigé vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="50897-134">**WriteConsole** fails if it is used with a standard handle that is redirected to a file.</span></span> <span data-ttu-id="50897-135">Si une application traite une sortie multilingue qui peut être redirigée, déterminez si le descripteur de sortie est un handle de console (une méthode consiste à appeler la fonction [**GetConsoleMode**](getconsolemode.md) et à vérifier si elle est réussie).</span><span class="sxs-lookup"><span data-stu-id="50897-135">If an application processes multilingual output that can be redirected, determine whether the output handle is a console handle (one method is to call the [**GetConsoleMode**](getconsolemode.md) function and check whether it succeeds).</span></span> <span data-ttu-id="50897-136">Si le handle est un handle de console, appelez **WriteConsole** .</span><span class="sxs-lookup"><span data-stu-id="50897-136">If the handle is a console handle, call **WriteConsole** .</span></span> <span data-ttu-id="50897-137">Si le handle n’est pas un handle de console, la sortie est redirigée et vous devez appeler [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) pour effectuer les e/s.</span><span class="sxs-lookup"><span data-stu-id="50897-137">If the handle is not a console handle, the output is redirected and you should call [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) to perform the I/O.</span></span> <span data-ttu-id="50897-138">Veillez à faire précéder un fichier texte brut Unicode d’une marque d’ordre d’octet.</span><span class="sxs-lookup"><span data-stu-id="50897-138">Be sure to prefix a Unicode plain text file with a byte order mark.</span></span> <span data-ttu-id="50897-139">Pour plus d’informations, consultez [utilisation des marques d’ordre des octets](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span><span class="sxs-lookup"><span data-stu-id="50897-139">For more information, see [Using Byte Order Marks](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span></span>

<span data-ttu-id="50897-140">Bien qu’une application puisse utiliser **WriteConsole** en mode ANSI pour écrire des caractères ANSI, les consoles ne prennent pas en charge les séquences « ANSI Escape » ou « terminal virtuel », sauf si elles sont activées.</span><span class="sxs-lookup"><span data-stu-id="50897-140">Although an application can use **WriteConsole** in ANSI mode to write ANSI characters, consoles do not support "ANSI escape" or "virtual terminal" sequences unless enabled.</span></span> <span data-ttu-id="50897-141">Pour plus d’informations et pour la version d’applicabilité du système d’exploitation, consultez [**séquences de terminaux virtuels de la console**](console-virtual-terminal-sequences.md) .</span><span class="sxs-lookup"><span data-stu-id="50897-141">See [**Console Virtual Terminal Sequences**](console-virtual-terminal-sequences.md) for more information and for operating system version applicability.</span></span>

<span data-ttu-id="50897-142">Lorsque les séquences d’échappement des terminaux virtuels ne sont pas activées, les fonctions de la console peuvent fournir des fonctionnalités équivalentes.</span><span class="sxs-lookup"><span data-stu-id="50897-142">When virtual terminal escape sequences are not enabled, console functions can provide equivalent functionality.</span></span> <span data-ttu-id="50897-143">Pour plus d’informations, consultez [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md)et [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span><span class="sxs-lookup"><span data-stu-id="50897-143">For more information, see [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md), and [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="50897-144">Spécifications</span><span class="sxs-lookup"><span data-stu-id="50897-144">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="50897-145">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="50897-145">Minimum supported client</span></span> | <span data-ttu-id="50897-146">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="50897-146">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="50897-147">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="50897-147">Minimum supported server</span></span> | <span data-ttu-id="50897-148">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="50897-148">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="50897-149">En-tête</span><span class="sxs-lookup"><span data-stu-id="50897-149">Header</span></span> | <span data-ttu-id="50897-150">ConsoleApi. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="50897-150">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="50897-151">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="50897-151">Library</span></span> | <span data-ttu-id="50897-152">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="50897-152">Kernel32.lib</span></span> |
| <span data-ttu-id="50897-153">DLL</span><span class="sxs-lookup"><span data-stu-id="50897-153">DLL</span></span> | <span data-ttu-id="50897-154">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="50897-154">Kernel32.dll</span></span> |
| <span data-ttu-id="50897-155">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="50897-155">Unicode and ANSI names</span></span> | <span data-ttu-id="50897-156">**WriteConsoleW** (Unicode) et **WriteConsoleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="50897-156">**WriteConsoleW** (Unicode) and **WriteConsoleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="50897-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50897-157">See also</span></span>

[<span data-ttu-id="50897-158">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="50897-158">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="50897-159">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="50897-159">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="50897-160">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="50897-160">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="50897-161">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="50897-161">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="50897-162">Méthodes d’entrée et de sortie</span><span class="sxs-lookup"><span data-stu-id="50897-162">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="50897-163">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="50897-163">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="50897-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="50897-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="50897-165">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="50897-165">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="50897-166">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="50897-166">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="50897-167">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="50897-167">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="50897-168">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="50897-168">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

<span data-ttu-id="50897-169">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="50897-169">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span></span>

[<span data-ttu-id="50897-170">**Appel**</span><span class="sxs-lookup"><span data-stu-id="50897-170">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
