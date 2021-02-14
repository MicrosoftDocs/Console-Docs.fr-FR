---
title: Fonction GetStdHandle
description: Récupère un handle vers l’appareil standard spécifié (entrée standard, sortie standard ou erreur standard).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- processenv/GetStdHandle
- winbase/GetStdHandle
- GetStdHandle
MS-HAID:
- '\_win32\_getstdhandle'
- base.getstdhandle
- consoles.getstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 23cd76e9-671a-48d0-9b82-2beda8917348
topic_type:
- apiref
api_name:
- GetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 0804e12ff7510cd41bec66e1a45f8a31add7c17a
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358749"
---
# <a name="getstdhandle-function"></a><span data-ttu-id="e65b7-104">Fonction GetStdHandle</span><span class="sxs-lookup"><span data-stu-id="e65b7-104">GetStdHandle function</span></span>

<span data-ttu-id="e65b7-105">Récupère un handle vers l’appareil standard spécifié (entrée standard, sortie standard ou erreur standard).</span><span class="sxs-lookup"><span data-stu-id="e65b7-105">Retrieves a handle to the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="e65b7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e65b7-106">Syntax</span></span>

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a><span data-ttu-id="e65b7-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e65b7-107">Parameters</span></span>

<span data-ttu-id="e65b7-108">*nStdHandle* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="e65b7-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="e65b7-109">Périphérique standard.</span><span class="sxs-lookup"><span data-stu-id="e65b7-109">The standard device.</span></span> <span data-ttu-id="e65b7-110">Ce paramètre peut prendre les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="e65b7-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="e65b7-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="e65b7-111">Value</span></span> | <span data-ttu-id="e65b7-112">Signification</span><span class="sxs-lookup"><span data-stu-id="e65b7-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="e65b7-113">**STD_INPUT_HANDLE** (DWORD) -10</span><span class="sxs-lookup"><span data-stu-id="e65b7-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="e65b7-114">Périphérique d’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="e65b7-114">The standard input device.</span></span> <span data-ttu-id="e65b7-115">À la base, il s’agit de la mémoire tampon d’entrée de la console, `CONIN$`.</span><span class="sxs-lookup"><span data-stu-id="e65b7-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="e65b7-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span><span class="sxs-lookup"><span data-stu-id="e65b7-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="e65b7-117">Périphérique de sortie standard.</span><span class="sxs-lookup"><span data-stu-id="e65b7-117">The standard output device.</span></span> <span data-ttu-id="e65b7-118">À la base, il s’agit de la mémoire tampon d’écran de la console active, `CONOUT$`.</span><span class="sxs-lookup"><span data-stu-id="e65b7-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="e65b7-119">**STD_ERROR_HANDLE** (DWORD) -12</span><span class="sxs-lookup"><span data-stu-id="e65b7-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="e65b7-120">Périphérique d’erreur standard.</span><span class="sxs-lookup"><span data-stu-id="e65b7-120">The standard error device.</span></span> <span data-ttu-id="e65b7-121">À la base, il s’agit de la mémoire tampon d’écran de la console active, `CONOUT$`.</span><span class="sxs-lookup"><span data-stu-id="e65b7-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

## <a name="return-value"></a><span data-ttu-id="e65b7-122">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="e65b7-122">Return value</span></span>

<span data-ttu-id="e65b7-123">Si la fonction réussit, la valeur de retour est un handle vers le périphérique spécifié, ou un handle redirigé défini par un appel précédent à [**SetStdHandle**](setstdhandle.md).</span><span class="sxs-lookup"><span data-stu-id="e65b7-123">If the function succeeds, the return value is a handle to the specified device, or a redirected handle set by a previous call to [**SetStdHandle**](setstdhandle.md).</span></span> <span data-ttu-id="e65b7-124">Le handle a les droits d’accès **GENERIC\_READ** et **GENERIC\_WRITE**, sauf si l’application a utilisé **SetStdHandle** pour définir un handle standard avec un accès plus restreint.</span><span class="sxs-lookup"><span data-stu-id="e65b7-124">The handle has **GENERIC\_READ** and **GENERIC\_WRITE** access rights, unless the application has used **SetStdHandle** to set a standard handle with lesser access.</span></span>

<span data-ttu-id="e65b7-125">Si la fonction échoue, la valeur de retour est **INVALID\_HANDLE\_VALUE**.</span><span class="sxs-lookup"><span data-stu-id="e65b7-125">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="e65b7-126">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="e65b7-126">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

<span data-ttu-id="e65b7-127">Si une application n’a pas de handles standard associés, comme un service s’exécutant sur un bureau interactif, et qu’elle ne les a pas redirigés, la valeur de retour est **NULL**.</span><span class="sxs-lookup"><span data-stu-id="e65b7-127">If an application does not have associated standard handles, such as a service running on an interactive desktop, and has not redirected them, the return value is **NULL**.</span></span>

## <a name="remarks"></a><span data-ttu-id="e65b7-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="e65b7-128">Remarks</span></span>

<span data-ttu-id="e65b7-129">Les handles retournés par **GetStdHandle** peuvent être utilisés par les applications qui doivent lire ou écrire dans la console.</span><span class="sxs-lookup"><span data-stu-id="e65b7-129">Handles returned by **GetStdHandle** can be used by applications that need to read from or write to the console.</span></span> <span data-ttu-id="e65b7-130">Quand une console est créée, le handle d’entrée standard est un handle vers la mémoire tampon d’entrée de la console, et les handles de sortie standard et d’erreur standard sont des handles vers la mémoire tampon d’écran active de la console.</span><span class="sxs-lookup"><span data-stu-id="e65b7-130">When a console is created, the standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles of the console's active screen buffer.</span></span> <span data-ttu-id="e65b7-131">Ces handles peuvent être utilisés par les fonctions [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) et [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile), ou par une des fonctions de console qui accèdent à la mémoire tampon d’entrée de la console ou à une mémoire tampon d’écran (par exemple, les fonctions [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md) ou [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)).</span><span class="sxs-lookup"><span data-stu-id="e65b7-131">These handles can be used by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) and [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) functions, or by any of the console functions that access the console input buffer or a screen buffer (for example, the [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md), or [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) functions).</span></span>

<span data-ttu-id="e65b7-132">Les handles standard d’un processus peuvent être redirigés par un appel à [**SetStdHandle**](setstdhandle.md), auquel cas **GetStdHandle** retourne le handle redirigé.</span><span class="sxs-lookup"><span data-stu-id="e65b7-132">The standard handles of a process may be redirected by a call to [**SetStdHandle**](setstdhandle.md), in which case **GetStdHandle** returns the redirected handle.</span></span> <span data-ttu-id="e65b7-133">Si les handles standard ont été redirigés, vous pouvez spécifier la valeur `CONIN$` dans un appel à la fonction [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) pour obtenir un handle vers la mémoire tampon d’entrée d’une console.</span><span class="sxs-lookup"><span data-stu-id="e65b7-133">If the standard handles have been redirected, you can specify the `CONIN$` value in a call to the [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="e65b7-134">De même, vous pouvez spécifier la valeur `CONOUT$` pour obtenir un handle vers la mémoire tampon d’écran active d’une console.</span><span class="sxs-lookup"><span data-stu-id="e65b7-134">Similarly, you can specify the `CONOUT$` value to get a handle to a console's active screen buffer.</span></span>

<span data-ttu-id="e65b7-135">Les handles standard d’un processus sur l’entrée de la méthode main sont dictés par la configuration de l’indicateur [ **/SUBSYSTEM**](/cpp/build/reference/subsystem-specify-subsystem) passé à l’éditeur de liens lors de la génération de l’application.</span><span class="sxs-lookup"><span data-stu-id="e65b7-135">The standard handles of a process on entry of the main method are dictated by the configuration of the [**/SUBSYSTEM**](/cpp/build/reference/subsystem-specify-subsystem) flag passed to the linker when the application was built.</span></span> <span data-ttu-id="e65b7-136">La spécification de **/SUBSYSTEM : CONSOLE** demande que le système d’exploitation remplisse les handles avec une session de console au démarrage si le parent n’a pas déjà rempli la table de handles standard par héritage.</span><span class="sxs-lookup"><span data-stu-id="e65b7-136">Specifying **/SUBSYSTEM:CONSOLE** requests that the operating system fill the handles with a console session on startup, if the parent didn't already fill the standard handle table by inheritance.</span></span> <span data-ttu-id="e65b7-137">En revanche, **/SUBSYSTEM:WINDOWS** implique que l’application n’a pas besoin d’une console et qu’elle ne va probablement pas utiliser les handles standard.</span><span class="sxs-lookup"><span data-stu-id="e65b7-137">On the contrary, **/SUBSYSTEM:WINDOWS** implies that the application does not need a console and will likely not be making use of the standard handles.</span></span> <span data-ttu-id="e65b7-138">Vous trouverez plus d’informations sur l’héritage des handles dans la documentation pour [**STARTF\_USESTDHANDLES**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).</span><span class="sxs-lookup"><span data-stu-id="e65b7-138">More information on handle inheritance can be found in the documentation for [**STARTF\_USESTDHANDLES**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).</span></span>

<span data-ttu-id="e65b7-139">Certaines applications fonctionnent en dehors des limites de leur sous-système déclaré. Par exemple, une application **/SUBSYSTEM:WINDOWS** peut vérifier/utiliser des handles standard à des fins de journalisation ou de débogage, mais elle fonctionne normalement avec une interface graphique utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e65b7-139">Some applications operate outside the boundaries of their declared subsystem; for instance, a **/SUBSYSTEM:WINDOWS** application might check/use standard handles for logging or debugging purposes but operate normally with a graphical user interface.</span></span> <span data-ttu-id="e65b7-140">Ces applications doivent soigneusement interroger l’état des handles standard au démarrage et utiliser [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md) et [**FreeConsole**](freeconsole.md) pour ajouter/supprimer une console si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e65b7-140">These applications will need to carefully probe the state of standard handles on startup and make use of [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md), and [**FreeConsole**](freeconsole.md) to add/remove a console if desired.</span></span>

<span data-ttu-id="e65b7-141">Certaines applications peuvent également modifier leur comportement selon le type de handle hérité.</span><span class="sxs-lookup"><span data-stu-id="e65b7-141">Some applications may also vary their behavior on the type of inherited handle.</span></span> <span data-ttu-id="e65b7-142">La levée des ambiguïtés de type entre console, canal, fichier et d’autres éléments peut être effectué avec [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype).</span><span class="sxs-lookup"><span data-stu-id="e65b7-142">Disambiguating the type between console, pipe, file, and others can be performed with [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype).</span></span>

### <a name="attachdetach-behavior"></a><span data-ttu-id="e65b7-143">Comportement d’attachement/détachement</span><span class="sxs-lookup"><span data-stu-id="e65b7-143">Attach/detach behavior</span></span>

<span data-ttu-id="e65b7-144">Lors de l’attachement à une nouvelle console, les handles standard sont toujours remplacés par des handles de console, sauf si **STARTF\_USESTDHANDLES** a été spécifié lors de la création du processus.</span><span class="sxs-lookup"><span data-stu-id="e65b7-144">When attaching to a new console, standard handles are always replaced with console handles unless **STARTF\_USESTDHANDLES** was specified during process creation.</span></span>

<span data-ttu-id="e65b7-145">Si la valeur existante du handle standard est **NULL** ou si la valeur existante du handle standard ressemble à un pseudohandle de console, le handle est remplacé par un handle de console.</span><span class="sxs-lookup"><span data-stu-id="e65b7-145">If the existing value of the standard handle is **NULL**, or the existing value of the standard handle looks like a console pseudohandle, the handle is replaced with a console handle.</span></span>

<span data-ttu-id="e65b7-146">Quand un parent utilise à la fois **CREATE\_NEW\_CONSOLE** et **STARTF\_USESTDHANDLES** pour créer un processus de console, les handles standard ne sont pas remplacés, sauf si la valeur existante du handle standard est **NULL** ou un pseudohandle de console.</span><span class="sxs-lookup"><span data-stu-id="e65b7-146">When a parent uses both **CREATE\_NEW\_CONSOLE** and **STARTF\_USESTDHANDLES** to create a console process, standard handles will not be replaced unless the existing value of the standard handle is **NULL** or a console pseudohandle.</span></span>

> [!NOTE]
><span data-ttu-id="e65b7-147">Les processus de console *doivent* démarrer avec les handles standard remplis ; sinon, ils seront renseignés automatiquement avec les handles appropriés pour une nouvelle console.</span><span class="sxs-lookup"><span data-stu-id="e65b7-147">Console processes *must* start with the standard handles filled or they will be filled automatically with appropriate handles to a new console.</span></span> <span data-ttu-id="e65b7-148">Les applications avec interface graphique utilisateur peuvent être démarrées sans les handles standard ; ils ne seront pas renseignés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="e65b7-148">Graphical user interface (GUI) applications can be started without the standard handles and they will not be automatically filled.</span></span>

## <a name="examples"></a><span data-ttu-id="e65b7-149">Exemples</span><span class="sxs-lookup"><span data-stu-id="e65b7-149">Examples</span></span>

<span data-ttu-id="e65b7-150">Pour obtenir un exemple, consultez [Lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="e65b7-150">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="e65b7-151">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e65b7-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e65b7-152">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="e65b7-152">Minimum supported client</span></span> | <span data-ttu-id="e65b7-153">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="e65b7-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="e65b7-154">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="e65b7-154">Minimum supported server</span></span> | <span data-ttu-id="e65b7-155">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="e65b7-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="e65b7-156">En-tête</span><span class="sxs-lookup"><span data-stu-id="e65b7-156">Header</span></span> | <span data-ttu-id="e65b7-157">ProcessEnv.h (via Winbase.h, inclure Windows.h)</span><span class="sxs-lookup"><span data-stu-id="e65b7-157">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="e65b7-158">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="e65b7-158">Library</span></span> | <span data-ttu-id="e65b7-159">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="e65b7-159">Kernel32.lib</span></span> |
| <span data-ttu-id="e65b7-160">DLL</span><span class="sxs-lookup"><span data-stu-id="e65b7-160">DLL</span></span> | <span data-ttu-id="e65b7-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e65b7-161">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="e65b7-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e65b7-162">See also</span></span>

[<span data-ttu-id="e65b7-163">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="e65b7-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e65b7-164">Handles de console</span><span class="sxs-lookup"><span data-stu-id="e65b7-164">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="e65b7-165">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="e65b7-165">**CreateFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-createfilea)

[<span data-ttu-id="e65b7-166">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="e65b7-166">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="e65b7-167">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="e65b7-167">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="e65b7-168">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="e65b7-168">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="e65b7-169">**SetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="e65b7-169">**SetStdHandle**</span></span>](setstdhandle.md)

[<span data-ttu-id="e65b7-170">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="e65b7-170">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="e65b7-171">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="e65b7-171">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)