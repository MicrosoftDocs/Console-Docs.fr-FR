---
title: ReadConsole fonction)
description: Lit les entrées de caractères à partir de la mémoire tampon d’entrée de la console et les supprime de la mémoire tampon.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi/ReadConsole
- wincon/ReadConsole
- ReadConsole
- consoleapi/ReadConsoleA
- wincon/ReadConsoleA
- ReadConsoleA
- consoleapi/ReadConsoleW
- wincon/ReadConsoleW
- ReadConsoleW
MS-HAID:
- '\_win32\_readconsole'
- base.readconsole
- consoles.readconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1aa9ecac-a9b9-4e6d-9206-7a57013de657
topic_type:
- apiref
api_name:
- ReadConsole
- ReadConsoleA
- ReadConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 16287bec8e690e5d70483d6e6055e6badaca40ce
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059057"
---
# <a name="readconsole-function"></a><span data-ttu-id="4371a-104">ReadConsole fonction)</span><span class="sxs-lookup"><span data-stu-id="4371a-104">ReadConsole function</span></span>


<span data-ttu-id="4371a-105">Lit les entrées de caractères à partir de la mémoire tampon d’entrée de la console et les supprime de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="4371a-105">Reads character input from the console input buffer and removes it from the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="4371a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4371a-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsole(
  _In_     HANDLE  hConsoleInput,
  _Out_    LPVOID  lpBuffer,
  _In_     DWORD   nNumberOfCharsToRead,
  _Out_    LPDWORD lpNumberOfCharsRead,
  _In_opt_ LPVOID  pInputControl
);
```

<a name="parameters"></a><span data-ttu-id="4371a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4371a-107">Parameters</span></span>
----------

<span data-ttu-id="4371a-108">*hConsoleInput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="4371a-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="4371a-109">Handle vers la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="4371a-109">A handle to the console input buffer.</span></span> <span data-ttu-id="4371a-110">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="4371a-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="4371a-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="4371a-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="4371a-112">*lpBuffer* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="4371a-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="4371a-113">Pointeur vers une mémoire tampon qui reçoit les données lues à partir de la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="4371a-113">A pointer to a buffer that receives the data read from the console input buffer.</span></span>

<span data-ttu-id="4371a-114">*nNumberOfCharsToRead* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="4371a-114">*nNumberOfCharsToRead* \[in\]</span></span>  
<span data-ttu-id="4371a-115">Nombre de caractères à lire.</span><span class="sxs-lookup"><span data-stu-id="4371a-115">The number of characters to be read.</span></span> <span data-ttu-id="4371a-116">La taille de la mémoire tampon vers laquelle pointe le paramètre *lpBuffer* doit être au moins égale à `nNumberOfCharsToRead * sizeof(TCHAR)` octets.</span><span class="sxs-lookup"><span data-stu-id="4371a-116">The size of the buffer pointed to by the *lpBuffer* parameter should be at least `nNumberOfCharsToRead * sizeof(TCHAR)` bytes.</span></span>

<span data-ttu-id="4371a-117">*lpNumberOfCharsRead* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="4371a-117">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="4371a-118">Pointeur vers une variable qui reçoit le nombre de caractères réellement lus.</span><span class="sxs-lookup"><span data-stu-id="4371a-118">A pointer to a variable that receives the number of characters actually read.</span></span>

<span data-ttu-id="4371a-119">*pInputControl* \[ dans, facultatif\]</span><span class="sxs-lookup"><span data-stu-id="4371a-119">*pInputControl* \[in, optional\]</span></span>  
<span data-ttu-id="4371a-120">Pointeur vers une structure [**de \_ \_ contrôle READCONSOLE**](console-readconsole-control.md) de la console qui spécifie un caractère de contrôle pour signaler la fin de l’opération de lecture.</span><span class="sxs-lookup"><span data-stu-id="4371a-120">A pointer to a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure that specifies a control character to signal the end of the read operation.</span></span> <span data-ttu-id="4371a-121">Ce paramètre peut avoir la **valeur null**.</span><span class="sxs-lookup"><span data-stu-id="4371a-121">This parameter can be **NULL**.</span></span>

<span data-ttu-id="4371a-122">Ce paramètre nécessite une entrée Unicode par défaut.</span><span class="sxs-lookup"><span data-stu-id="4371a-122">This parameter requires Unicode input by default.</span></span> <span data-ttu-id="4371a-123">Pour le mode ANSI, attribuez la valeur **null**à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="4371a-123">For ANSI mode, set this parameter to **NULL**.</span></span>

<a name="return-value"></a><span data-ttu-id="4371a-124">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="4371a-124">Return value</span></span>
------------

<span data-ttu-id="4371a-125">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="4371a-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4371a-126">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="4371a-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4371a-127">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4371a-127">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="4371a-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="4371a-128">Remarks</span></span>
-------

<span data-ttu-id="4371a-129">**ReadConsole** lit l’entrée au clavier à partir de la mémoire tampon d’entrée d’une console.</span><span class="sxs-lookup"><span data-stu-id="4371a-129">**ReadConsole** reads keyboard input from a console's input buffer.</span></span> <span data-ttu-id="4371a-130">Il se comporte comme la fonction [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) , à la différence qu’il peut lire en mode Unicode (caractères larges) ou ANSI.</span><span class="sxs-lookup"><span data-stu-id="4371a-130">It behaves like the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) function, except that it can read in either Unicode (wide-character) or ANSI mode.</span></span> <span data-ttu-id="4371a-131">Pour que les applications qui maintiennent un seul ensemble de sources soient compatibles avec les deux modes, utilisez **ReadConsole** plutôt que **ReadFile**.</span><span class="sxs-lookup"><span data-stu-id="4371a-131">To have applications that maintain a single set of sources compatible with both modes, use **ReadConsole** rather than **ReadFile**.</span></span> <span data-ttu-id="4371a-132">Bien que **ReadConsole** puisse être utilisé uniquement avec un handle de mémoire tampon d’entrée de la console, **ReadFile** peut être utilisé avec d’autres Handles (tels que des fichiers ou des canaux).</span><span class="sxs-lookup"><span data-stu-id="4371a-132">Although **ReadConsole** can only be used with a console input buffer handle, **ReadFile** can be used with other handles (such as files or pipes).</span></span> <span data-ttu-id="4371a-133">**ReadConsole** échoue s’il est utilisé avec un handle standard qui a été redirigé pour être autre chose qu’un handle de console.</span><span class="sxs-lookup"><span data-stu-id="4371a-133">**ReadConsole** fails if used with a standard handle that has been redirected to be something other than a console handle.</span></span>

<span data-ttu-id="4371a-134">Tous les modes d’entrée qui affectent le comportement de [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ont le même effet sur **ReadConsole**.</span><span class="sxs-lookup"><span data-stu-id="4371a-134">All of the input modes that affect the behavior of [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) have the same effect on **ReadConsole**.</span></span> <span data-ttu-id="4371a-135">Pour récupérer et définir les modes d’entrée d’une mémoire tampon d’entrée de la console, utilisez les fonctions [**GetConsoleMode**](getconsolemode.md) et [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="4371a-135">To retrieve and set the input modes of a console input buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

<span data-ttu-id="4371a-136">Si la mémoire tampon d’entrée contient des événements d’entrée autres que des événements de clavier (tels que des événements de souris ou des événements de redimensionnement de fenêtre), ceux-ci sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="4371a-136">If the input buffer contains input events other than keyboard events (such as mouse events or window-resizing events), they are discarded.</span></span> <span data-ttu-id="4371a-137">Ces événements peuvent uniquement être lus à l’aide de la fonction [**ReadConsoleInput**](readconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="4371a-137">Those events can only be read by using the [**ReadConsoleInput**](readconsoleinput.md) function.</span></span>

<span data-ttu-id="4371a-138">Cette fonction utilise des caractères Unicode ou 8 bits à partir de la page de codes actuelle de la console.</span><span class="sxs-lookup"><span data-stu-id="4371a-138">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="4371a-139">La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système.</span><span class="sxs-lookup"><span data-stu-id="4371a-139">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="4371a-140">Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="4371a-140">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<span data-ttu-id="4371a-141">Le paramètre *pInputControl* peut être utilisé pour activer les réveils intermédiaires à partir de la lecture en réponse à un caractère de contrôle d’achèvement de fichier spécifié dans une structure de [\*\* \_ \_ contrôle READCONSOLE\*\*](console-readconsole-control.md) de la console.</span><span class="sxs-lookup"><span data-stu-id="4371a-141">The *pInputControl* parameter can be used to enable intermediate wakeups from the read in response to a file-completion control character specified in a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure.</span></span> <span data-ttu-id="4371a-142">Cette fonctionnalité nécessite l’activation des extensions de commande, le descripteur de sortie standard pour être un handle de sortie de console et l’entrée en Unicode.</span><span class="sxs-lookup"><span data-stu-id="4371a-142">This feature requires command extensions to be enabled, the standard output handle to be a console output handle, and input to be Unicode.</span></span>

<span data-ttu-id="4371a-143">**Windows Server 2003 et Windows XP/2000 :** La fonctionnalité de lecture intermédiaire n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="4371a-143">**Windows Server 2003 and Windows XP/2000:** The intermediate read feature is not supported.</span></span>

<a name="requirements"></a><span data-ttu-id="4371a-144">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4371a-144">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="4371a-145">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="4371a-145">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="4371a-146">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="4371a-146">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4371a-147">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="4371a-147">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="4371a-148">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="4371a-148">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4371a-149">En-tête</span><span class="sxs-lookup"><span data-stu-id="4371a-149">Header</span></span></p></td>
<td><span data-ttu-id="4371a-150">ConsoleApi. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4371a-150">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4371a-151">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="4371a-151">Library</span></span></p></td>
<td><span data-ttu-id="4371a-152">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4371a-152">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4371a-153">DLL</span><span class="sxs-lookup"><span data-stu-id="4371a-153">DLL</span></span></p></td>
<td><span data-ttu-id="4371a-154">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4371a-154">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4371a-155">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="4371a-155">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="4371a-156"><strong>ReadConsoleW</strong> (Unicode) et <strong>ReadConsoleA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="4371a-156"><strong>ReadConsoleW</strong> (Unicode) and <strong>ReadConsoleA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="4371a-157"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4371a-157"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="4371a-158">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="4371a-158">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4371a-159">**\_contrôle READCONSOLE de la console \_**</span><span class="sxs-lookup"><span data-stu-id="4371a-159">**CONSOLE\_READCONSOLE\_CONTROL**</span></span>](console-readconsole-control.md)

[<span data-ttu-id="4371a-160">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="4371a-160">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="4371a-161">Méthodes d’entrée et de sortie</span><span class="sxs-lookup"><span data-stu-id="4371a-161">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="4371a-162">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="4371a-162">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="4371a-163">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="4371a-163">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="4371a-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="4371a-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="4371a-165">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="4371a-165">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="4371a-166">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="4371a-166">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="4371a-167">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="4371a-167">**WriteConsole**</span></span>](writeconsole.md)

 

 




