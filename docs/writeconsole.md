---
title: WriteConsole fonction)
description: Écrit une chaîne de caractères dans une mémoire tampon d’écran de console en commençant à l’emplacement actuel du curseur.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
ms.openlocfilehash: de5138326c0800016cf5ca6e3232f032abcd01de
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059512"
---
# <a name="writeconsole-function"></a><span data-ttu-id="528e4-104">WriteConsole fonction)</span><span class="sxs-lookup"><span data-stu-id="528e4-104">WriteConsole function</span></span>


<span data-ttu-id="528e4-105">Écrit une chaîne de caractères dans une mémoire tampon d’écran de console en commençant à l’emplacement actuel du curseur.</span><span class="sxs-lookup"><span data-stu-id="528e4-105">Writes a character string to a console screen buffer beginning at the current cursor location.</span></span>

<a name="syntax"></a><span data-ttu-id="528e4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="528e4-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

<a name="parameters"></a><span data-ttu-id="528e4-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="528e4-107">Parameters</span></span>
----------

<span data-ttu-id="528e4-108">*hConsoleOutput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="528e4-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="528e4-109">Handle vers la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="528e4-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="528e4-110">Le descripteur doit avoir le droit d’accès en \*\* \_ écriture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="528e4-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="528e4-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="528e4-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="528e4-112">*lpBuffer* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="528e4-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="528e4-113">Pointeur vers une mémoire tampon qui contient les caractères à écrire dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="528e4-113">A pointer to a buffer that contains characters to be written to the console screen buffer.</span></span>

<span data-ttu-id="528e4-114">*nNumberOfCharsToWrite* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="528e4-114">*nNumberOfCharsToWrite* \[in\]</span></span>  
<span data-ttu-id="528e4-115">Nombre de caractères à écrire.</span><span class="sxs-lookup"><span data-stu-id="528e4-115">The number of characters to be written.</span></span> <span data-ttu-id="528e4-116">Si la taille totale du nombre spécifié de caractères dépasse le tas disponible, la fonction échoue avec une **erreur \_ de \_ \_ mémoire insuffisante**.</span><span class="sxs-lookup"><span data-stu-id="528e4-116">If the total size of the specified number of characters exceeds the available heap, the function fails with **ERROR\_NOT\_ENOUGH\_MEMORY**.</span></span>

<span data-ttu-id="528e4-117">*lpNumberOfCharsWritten* \[ out, facultatif\]</span><span class="sxs-lookup"><span data-stu-id="528e4-117">*lpNumberOfCharsWritten* \[out, optional\]</span></span>  
<span data-ttu-id="528e4-118">Pointeur vers une variable qui reçoit le nombre de caractères réellement écrits.</span><span class="sxs-lookup"><span data-stu-id="528e4-118">A pointer to a variable that receives the number of characters actually written.</span></span>

<span data-ttu-id="528e4-119">*lpReserved* </span><span class="sxs-lookup"><span data-stu-id="528e4-119">*lpReserved* </span></span>  
<span data-ttu-id="528e4-120">Réservé doit avoir la **valeur null**.</span><span class="sxs-lookup"><span data-stu-id="528e4-120">Reserved; must be **NULL**.</span></span>

<a name="return-value"></a><span data-ttu-id="528e4-121">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="528e4-121">Return value</span></span>
------------

<span data-ttu-id="528e4-122">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="528e4-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="528e4-123">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="528e4-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="528e4-124">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="528e4-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="528e4-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="528e4-125">Remarks</span></span>
-------

<span data-ttu-id="528e4-126">La fonction **WriteConsole** écrit des caractères dans la mémoire tampon d’écran de la console à la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="528e4-126">The **WriteConsole** function writes characters to the console screen buffer at the current cursor position.</span></span> <span data-ttu-id="528e4-127">La position du curseur avance à mesure que des caractères sont écrits.</span><span class="sxs-lookup"><span data-stu-id="528e4-127">The cursor position advances as characters are written.</span></span> <span data-ttu-id="528e4-128">La fonction [**SetConsoleCursorPosition**](setconsolecursorposition.md) définit la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="528e4-128">The [**SetConsoleCursorPosition**](setconsolecursorposition.md) function sets the current cursor position.</span></span>

<span data-ttu-id="528e4-129">Les caractères sont écrits à l’aide des attributs de couleur de premier plan et d’arrière-plan associés à la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="528e4-129">Characters are written using the foreground and background color attributes associated with the console screen buffer.</span></span> <span data-ttu-id="528e4-130">La fonction [**SetConsoleTextAttribute**](setconsoletextattribute.md) modifie ces couleurs.</span><span class="sxs-lookup"><span data-stu-id="528e4-130">The [**SetConsoleTextAttribute**](setconsoletextattribute.md) function changes these colors.</span></span> <span data-ttu-id="528e4-131">Pour déterminer les attributs de couleur actuelle et la position actuelle du curseur, utilisez [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span><span class="sxs-lookup"><span data-stu-id="528e4-131">To determine the current color attributes and the current cursor position, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span></span>

<span data-ttu-id="528e4-132">Tous les modes d’entrée qui affectent le comportement de la fonction [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ont le même effet sur **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="528e4-132">All of the input modes that affect the behavior of the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) function have the same effect on **WriteConsole**.</span></span> <span data-ttu-id="528e4-133">Pour récupérer et définir les modes de sortie d’une mémoire tampon d’écran de la console, utilisez les fonctions [**GetConsoleMode**](getconsolemode.md) et [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="528e4-133">To retrieve and set the output modes of a console screen buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

<span data-ttu-id="528e4-134">La fonction **WriteConsole** utilise des caractères Unicode ou ANSI à partir de la page de codes actuelle de la console.</span><span class="sxs-lookup"><span data-stu-id="528e4-134">The **WriteConsole** function uses either Unicode characters or ANSI characters from the console's current code page.</span></span> <span data-ttu-id="528e4-135">La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système.</span><span class="sxs-lookup"><span data-stu-id="528e4-135">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="528e4-136">Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="528e4-136">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<span data-ttu-id="528e4-137">**WriteConsole** échoue s’il est utilisé avec un handle standard qui est redirigé vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="528e4-137">**WriteConsole** fails if it is used with a standard handle that is redirected to a file.</span></span> <span data-ttu-id="528e4-138">Si une application traite une sortie multilingue qui peut être redirigée, déterminez si le descripteur de sortie est un handle de console (une méthode consiste à appeler la fonction [**GetConsoleMode**](getconsolemode.md) et à vérifier si elle est réussie).</span><span class="sxs-lookup"><span data-stu-id="528e4-138">If an application processes multilingual output that can be redirected, determine whether the output handle is a console handle (one method is to call the [**GetConsoleMode**](getconsolemode.md) function and check whether it succeeds).</span></span> <span data-ttu-id="528e4-139">Si le handle est un handle de console, appelez **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="528e4-139">If the handle is a console handle, call **WriteConsole**.</span></span> <span data-ttu-id="528e4-140">Si le handle n’est pas un handle de console, la sortie est redirigée et vous devez appeler [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) pour effectuer les e/s.</span><span class="sxs-lookup"><span data-stu-id="528e4-140">If the handle is not a console handle, the output is redirected and you should call [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) to perform the I/O.</span></span> <span data-ttu-id="528e4-141">Veillez à faire précéder un fichier texte brut Unicode d’une marque d’ordre d’octet.</span><span class="sxs-lookup"><span data-stu-id="528e4-141">Be sure to prefix a Unicode plain text file with a byte order mark.</span></span> <span data-ttu-id="528e4-142">Pour plus d’informations, consultez [utilisation des marques d’ordre des octets](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span><span class="sxs-lookup"><span data-stu-id="528e4-142">For more information, see [Using Byte Order Marks](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span></span>

<span data-ttu-id="528e4-143">Bien qu’une application puisse utiliser **WriteConsole** en mode ANSI pour écrire des caractères ANSI, les consoles ne prennent pas en charge les séquences d’échappement ANSI.</span><span class="sxs-lookup"><span data-stu-id="528e4-143">Although an application can use **WriteConsole** in ANSI mode to write ANSI characters, consoles do not support ANSI escape sequences.</span></span> <span data-ttu-id="528e4-144">Toutefois, certaines fonctions offrent des fonctionnalités équivalentes.</span><span class="sxs-lookup"><span data-stu-id="528e4-144">However, some functions provide equivalent functionality.</span></span> <span data-ttu-id="528e4-145">Pour plus d’informations, consultez [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md)et [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span><span class="sxs-lookup"><span data-stu-id="528e4-145">For more information, see [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md), and [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span></span>

<a name="requirements"></a><span data-ttu-id="528e4-146">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="528e4-146">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="528e4-147">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="528e4-147">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="528e4-148">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="528e4-148">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="528e4-149">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="528e4-149">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="528e4-150">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="528e4-150">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="528e4-151">En-tête</span><span class="sxs-lookup"><span data-stu-id="528e4-151">Header</span></span></p></td>
<td><span data-ttu-id="528e4-152">ConsoleApi. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="528e4-152">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="528e4-153">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="528e4-153">Library</span></span></p></td>
<td><span data-ttu-id="528e4-154">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="528e4-154">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="528e4-155">DLL</span><span class="sxs-lookup"><span data-stu-id="528e4-155">DLL</span></span></p></td>
<td><span data-ttu-id="528e4-156">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="528e4-156">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="528e4-157">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="528e4-157">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="528e4-158"><strong>WriteConsoleW</strong> (Unicode) et <strong>WriteConsoleA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="528e4-158"><strong>WriteConsoleW</strong> (Unicode) and <strong>WriteConsoleA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="528e4-159"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="528e4-159"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="528e4-160">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="528e4-160">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="528e4-161">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="528e4-161">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="528e4-162">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="528e4-162">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="528e4-163">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="528e4-163">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="528e4-164">Méthodes d’entrée et de sortie</span><span class="sxs-lookup"><span data-stu-id="528e4-164">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="528e4-165">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="528e4-165">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="528e4-166">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="528e4-166">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="528e4-167">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="528e4-167">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="528e4-168">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="528e4-168">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="528e4-169">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="528e4-169">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="528e4-170">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="528e4-170">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

<span data-ttu-id="528e4-171">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="528e4-171">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span></span>

[<span data-ttu-id="528e4-172">**Appel**</span><span class="sxs-lookup"><span data-stu-id="528e4-172">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




