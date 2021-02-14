---
title: ReadConsole fonction)
description: Lit les entrées de caractères à partir de la mémoire tampon d’entrée de la console et les supprime de la mémoire tampon.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
ms.openlocfilehash: 757d770bc7fea543d15678af5f80f15c17dd0e82
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358279"
---
# <a name="readconsole-function"></a><span data-ttu-id="703f9-104">ReadConsole fonction)</span><span class="sxs-lookup"><span data-stu-id="703f9-104">ReadConsole function</span></span>

<span data-ttu-id="703f9-105">Lit les entrées de caractères à partir de la mémoire tampon d’entrée de la console et les supprime de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="703f9-105">Reads character input from the console input buffer and removes it from the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="703f9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="703f9-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsole(
  _In_     HANDLE  hConsoleInput,
  _Out_    LPVOID  lpBuffer,
  _In_     DWORD   nNumberOfCharsToRead,
  _Out_    LPDWORD lpNumberOfCharsRead,
  _In_opt_ LPVOID  pInputControl
);
```

## <a name="parameters"></a><span data-ttu-id="703f9-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="703f9-107">Parameters</span></span>

<span data-ttu-id="703f9-108">*hConsoleInput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="703f9-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="703f9-109">Handle vers la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="703f9-109">A handle to the console input buffer.</span></span> <span data-ttu-id="703f9-110">Le handle doit avoir le droit d’accès **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="703f9-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="703f9-111">Pour plus d’informations, consultez [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="703f9-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="703f9-112">*lpBuffer* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="703f9-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="703f9-113">Pointeur vers une mémoire tampon qui reçoit les données lues à partir de la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="703f9-113">A pointer to a buffer that receives the data read from the console input buffer.</span></span>

<span data-ttu-id="703f9-114">*nNumberOfCharsToRead* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="703f9-114">*nNumberOfCharsToRead* \[in\]</span></span>  
<span data-ttu-id="703f9-115">Nombre de caractères à lire.</span><span class="sxs-lookup"><span data-stu-id="703f9-115">The number of characters to be read.</span></span> <span data-ttu-id="703f9-116">La taille de la mémoire tampon vers laquelle pointe le paramètre *lpBuffer* doit être au moins égale à `nNumberOfCharsToRead * sizeof(TCHAR)` octets.</span><span class="sxs-lookup"><span data-stu-id="703f9-116">The size of the buffer pointed to by the *lpBuffer* parameter should be at least `nNumberOfCharsToRead * sizeof(TCHAR)` bytes.</span></span>

<span data-ttu-id="703f9-117">*lpNumberOfCharsRead* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="703f9-117">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="703f9-118">Pointeur vers une variable qui reçoit le nombre de caractères réellement lus.</span><span class="sxs-lookup"><span data-stu-id="703f9-118">A pointer to a variable that receives the number of characters actually read.</span></span>

<span data-ttu-id="703f9-119">*pInputControl* \[ dans, facultatif\]</span><span class="sxs-lookup"><span data-stu-id="703f9-119">*pInputControl* \[in, optional\]</span></span>  
<span data-ttu-id="703f9-120">Pointeur vers une structure [**de \_ \_ contrôle READCONSOLE**](console-readconsole-control.md) de la console qui spécifie un caractère de contrôle pour signaler la fin de l’opération de lecture.</span><span class="sxs-lookup"><span data-stu-id="703f9-120">A pointer to a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure that specifies a control character to signal the end of the read operation.</span></span> <span data-ttu-id="703f9-121">Ce paramètre peut être **NULL**.</span><span class="sxs-lookup"><span data-stu-id="703f9-121">This parameter can be **NULL**.</span></span>

<span data-ttu-id="703f9-122">Ce paramètre nécessite une entrée Unicode par défaut.</span><span class="sxs-lookup"><span data-stu-id="703f9-122">This parameter requires Unicode input by default.</span></span> <span data-ttu-id="703f9-123">Pour le mode ANSI, attribuez la valeur **null** à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="703f9-123">For ANSI mode, set this parameter to **NULL**.</span></span>

## <a name="return-value"></a><span data-ttu-id="703f9-124">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="703f9-124">Return value</span></span>

<span data-ttu-id="703f9-125">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="703f9-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="703f9-126">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="703f9-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="703f9-127">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="703f9-127">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="703f9-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="703f9-128">Remarks</span></span>

<span data-ttu-id="703f9-129">**ReadConsole** lit l’entrée au clavier à partir de la mémoire tampon d’entrée d’une console.</span><span class="sxs-lookup"><span data-stu-id="703f9-129">**ReadConsole** reads keyboard input from a console's input buffer.</span></span> <span data-ttu-id="703f9-130">Il se comporte comme la fonction [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) , à la différence qu’il peut lire en mode Unicode (caractères larges) ou ANSI.</span><span class="sxs-lookup"><span data-stu-id="703f9-130">It behaves like the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) function, except that it can read in either Unicode (wide-character) or ANSI mode.</span></span> <span data-ttu-id="703f9-131">Pour que les applications qui maintiennent un seul ensemble de sources soient compatibles avec les deux modes, utilisez **ReadConsole** plutôt que **ReadFile**.</span><span class="sxs-lookup"><span data-stu-id="703f9-131">To have applications that maintain a single set of sources compatible with both modes, use **ReadConsole** rather than **ReadFile**.</span></span> <span data-ttu-id="703f9-132">Bien que **ReadConsole** puisse être utilisé uniquement avec un handle de mémoire tampon d’entrée de la console, **ReadFile** peut être utilisé avec d’autres Handles (tels que des fichiers ou des canaux).</span><span class="sxs-lookup"><span data-stu-id="703f9-132">Although **ReadConsole** can only be used with a console input buffer handle, **ReadFile** can be used with other handles (such as files or pipes).</span></span> <span data-ttu-id="703f9-133">**ReadConsole** échoue s’il est utilisé avec un handle standard qui a été redirigé pour être autre chose qu’un handle de console.</span><span class="sxs-lookup"><span data-stu-id="703f9-133">**ReadConsole** fails if used with a standard handle that has been redirected to be something other than a console handle.</span></span>

<span data-ttu-id="703f9-134">Tous les modes d’entrée qui affectent le comportement de [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) ont le même effet sur **ReadConsole**.</span><span class="sxs-lookup"><span data-stu-id="703f9-134">All of the input modes that affect the behavior of [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) have the same effect on **ReadConsole**.</span></span> <span data-ttu-id="703f9-135">Pour récupérer et définir les modes d’entrée d’une mémoire tampon d’entrée de la console, utilisez les fonctions [**GetConsoleMode**](getconsolemode.md) et [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="703f9-135">To retrieve and set the input modes of a console input buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

<span data-ttu-id="703f9-136">Si la mémoire tampon d’entrée contient des événements d’entrée autres que des événements de clavier (tels que des événements de souris ou des événements de redimensionnement de fenêtre), ceux-ci sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="703f9-136">If the input buffer contains input events other than keyboard events (such as mouse events or window-resizing events), they are discarded.</span></span> <span data-ttu-id="703f9-137">Ces événements peuvent uniquement être lus à l’aide de la fonction [**ReadConsoleInput**](readconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="703f9-137">Those events can only be read by using the [**ReadConsoleInput**](readconsoleinput.md) function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

<span data-ttu-id="703f9-138">Le paramètre *pInputControl* peut être utilisé pour activer les réveils intermédiaires à partir de la lecture en réponse à un caractère de contrôle d’achèvement de fichier spécifié dans une structure de [**\_ \_ contrôle READCONSOLE**](console-readconsole-control.md) de la console.</span><span class="sxs-lookup"><span data-stu-id="703f9-138">The *pInputControl* parameter can be used to enable intermediate wakeups from the read in response to a file-completion control character specified in a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure.</span></span> <span data-ttu-id="703f9-139">Cette fonctionnalité nécessite l’activation des extensions de commande, le descripteur de sortie standard pour être un handle de sortie de console et l’entrée en Unicode.</span><span class="sxs-lookup"><span data-stu-id="703f9-139">This feature requires command extensions to be enabled, the standard output handle to be a console output handle, and input to be Unicode.</span></span>

<span data-ttu-id="703f9-140">**Windows Server 2003 et Windows XP/2000 :** La fonctionnalité de lecture intermédiaire n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="703f9-140">**Windows Server 2003 and Windows XP/2000:** The intermediate read feature is not supported.</span></span>

## <a name="requirements"></a><span data-ttu-id="703f9-141">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="703f9-141">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="703f9-142">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="703f9-142">Minimum supported client</span></span> | <span data-ttu-id="703f9-143">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="703f9-143">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="703f9-144">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="703f9-144">Minimum supported server</span></span> | <span data-ttu-id="703f9-145">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="703f9-145">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="703f9-146">En-tête</span><span class="sxs-lookup"><span data-stu-id="703f9-146">Header</span></span> | <span data-ttu-id="703f9-147">ConsoleApi.h (via WinCon.h, inclure Windows.h)</span><span class="sxs-lookup"><span data-stu-id="703f9-147">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="703f9-148">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="703f9-148">Library</span></span> | <span data-ttu-id="703f9-149">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="703f9-149">Kernel32.lib</span></span> |
| <span data-ttu-id="703f9-150">DLL</span><span class="sxs-lookup"><span data-stu-id="703f9-150">DLL</span></span> | <span data-ttu-id="703f9-151">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="703f9-151">Kernel32.dll</span></span> |
| <span data-ttu-id="703f9-152">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="703f9-152">Unicode and ANSI names</span></span> | <span data-ttu-id="703f9-153">**ReadConsoleW** (Unicode) et **ReadConsoleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="703f9-153">**ReadConsoleW** (Unicode) and **ReadConsoleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="703f9-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="703f9-154">See also</span></span>

[<span data-ttu-id="703f9-155">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="703f9-155">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="703f9-156">**\_contrôle READCONSOLE de la console \_**</span><span class="sxs-lookup"><span data-stu-id="703f9-156">**CONSOLE\_READCONSOLE\_CONTROL**</span></span>](console-readconsole-control.md)

[<span data-ttu-id="703f9-157">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="703f9-157">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="703f9-158">Méthodes d’entrée et de sortie</span><span class="sxs-lookup"><span data-stu-id="703f9-158">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="703f9-159">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="703f9-159">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="703f9-160">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="703f9-160">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="703f9-161">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="703f9-161">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="703f9-162">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="703f9-162">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="703f9-163">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="703f9-163">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="703f9-164">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="703f9-164">**WriteConsole**</span></span>](writeconsole.md)