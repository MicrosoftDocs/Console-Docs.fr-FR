---
title: Fonction SetConsoleCtrlHandler
description: Ajoute ou supprime une fonction HandlerRoutine définie par l’application dans la liste des fonctions de gestionnaire pour le processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/SetConsoleCtrlHandler
- wincon/SetConsoleCtrlHandler
- SetConsoleCtrlHandler
MS-HAID:
- '\_win32\_setconsolectrlhandler'
- base.setconsolectrlhandler
- consoles.setconsolectrlhandler
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6fc64265-1403-45ea-925c-c5eb31d56734
topic_type:
- apiref
api_name:
- SetConsoleCtrlHandler
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 03e7166f84be2f760a4ffea385225390bdb3ffa1
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357709"
---
# <a name="setconsolectrlhandler-function"></a><span data-ttu-id="7f47f-104">Fonction SetConsoleCtrlHandler</span><span class="sxs-lookup"><span data-stu-id="7f47f-104">SetConsoleCtrlHandler function</span></span>

<span data-ttu-id="7f47f-105">Ajoute ou supprime une fonction [**HandlerRoutine**](handlerroutine.md) définie par l’application dans la liste des fonctions de gestionnaire pour le processus appelant.</span><span class="sxs-lookup"><span data-stu-id="7f47f-105">Adds or removes an application-defined [**HandlerRoutine**](handlerroutine.md) function from the list of handler functions for the calling process.</span></span>

<span data-ttu-id="7f47f-106">Si aucune fonction de gestionnaire n’est spécifiée, la fonction définit un attribut pouvant être hérité qui détermine si le processus appelant ignore les signaux <kbd>CTRL</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="7f47f-106">If no handler function is specified, the function sets an inheritable attribute that determines whether the calling process ignores <kbd>CTRL</kbd>+<kbd>C</kbd> signals.</span></span>

## <a name="syntax"></a><span data-ttu-id="7f47f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f47f-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

## <a name="parameters"></a><span data-ttu-id="7f47f-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7f47f-108">Parameters</span></span>

<span data-ttu-id="7f47f-109">*HandlerRoutine* \[entrée, facultatif\]</span><span class="sxs-lookup"><span data-stu-id="7f47f-109">*HandlerRoutine* \[in, optional\]</span></span>  
<span data-ttu-id="7f47f-110">Pointeur vers la fonction [**HandlerRoutine**](handlerroutine.md) définie par l’application à ajouter ou à supprimer.</span><span class="sxs-lookup"><span data-stu-id="7f47f-110">A pointer to the application-defined [**HandlerRoutine**](handlerroutine.md) function to be added or removed.</span></span> <span data-ttu-id="7f47f-111">Ce paramètre peut être **NULL**.</span><span class="sxs-lookup"><span data-stu-id="7f47f-111">This parameter can be **NULL**.</span></span>

<span data-ttu-id="7f47f-112">*Add* \[entrée\]</span><span class="sxs-lookup"><span data-stu-id="7f47f-112">*Add* \[in\]</span></span>  
<span data-ttu-id="7f47f-113">Si ce paramètre est **TRUE**, le gestionnaire est ajouté ; si la valeur est **FALSE**, le gestionnaire est supprimé.</span><span class="sxs-lookup"><span data-stu-id="7f47f-113">If this parameter is **TRUE**, the handler is added; if it is **FALSE**, the handler is removed.</span></span>

<span data-ttu-id="7f47f-114">Si le paramètre *HandlerRoutine* est **NULL**, une valeur **TRUE** fait que le processus appelant ignore l’entrée <kbd>CTRL</kbd>+<kbd>C</kbd>, et une valeur **FALSE** restaure le traitement normal de <kbd>CTRL</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="7f47f-114">If the *HandlerRoutine* parameter is **NULL**, a **TRUE** value causes the calling process to ignore <kbd>CTRL</kbd>+<kbd>C</kbd> input, and a **FALSE** value restores normal processing of <kbd>CTRL</kbd>+<kbd>C</kbd> input.</span></span> <span data-ttu-id="7f47f-115">Cet attribut pour ignorer ou traiter <kbd>CTRL</kbd>+<kbd>C</kbd> est hérité par les processus enfants.</span><span class="sxs-lookup"><span data-stu-id="7f47f-115">This attribute of ignoring or processing <kbd>CTRL</kbd>+<kbd>C</kbd> is inherited by child processes.</span></span>

## <a name="return-value"></a><span data-ttu-id="7f47f-116">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="7f47f-116">Return value</span></span>

<span data-ttu-id="7f47f-117">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="7f47f-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="7f47f-118">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="7f47f-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="7f47f-119">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="7f47f-119">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="7f47f-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="7f47f-120">Remarks</span></span>

<span data-ttu-id="7f47f-121">Cette fonction fournit une notification similaire pour l’application console et les services fournis par [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) pour les applications graphiques avec une pompe de messages.</span><span class="sxs-lookup"><span data-stu-id="7f47f-121">This function provides a similar notification for console application and services that [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) provides for graphical applications with a message pump.</span></span> <span data-ttu-id="7f47f-122">Vous pouvez également utiliser cette fonction à partir d’une application graphique, mais il n’y a aucune garantie qu’elle arrive avant la notification de **WM\_QUERYENDSESSION**.</span><span class="sxs-lookup"><span data-stu-id="7f47f-122">You could also use this function from a graphical application, but there is no guarantee it would arrive before the notification from **WM\_QUERYENDSESSION**.</span></span>

<span data-ttu-id="7f47f-123">Chaque processus de console a sa propre liste de fonctions [**HandlerRoutine**](handlerroutine.md) définies par l’application qui gèrent les signaux <kbd>CTRL</kbd>+<kbd>C</kbd> et <kbd>CTRL</kbd>+<kbd>BREAK</kbd>.</span><span class="sxs-lookup"><span data-stu-id="7f47f-123">Each console process has its own list of application-defined [**HandlerRoutine**](handlerroutine.md) functions that handle <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> signals.</span></span> <span data-ttu-id="7f47f-124">Les fonctions du gestionnaire gèrent également les signaux générés par le système quand l’utilisateur ferme la console, se déconnecte ou arrête le système.</span><span class="sxs-lookup"><span data-stu-id="7f47f-124">The handler functions also handle signals generated by the system when the user closes the console, logs off, or shuts down the system.</span></span> <span data-ttu-id="7f47f-125">À la base, la liste de gestionnaires de chaque processus contient seulement une fonction de gestionnaire par défaut qui appelle la fonction [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess).</span><span class="sxs-lookup"><span data-stu-id="7f47f-125">Initially, the handler list for each process contains only a default handler function that calls the [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) function.</span></span> <span data-ttu-id="7f47f-126">Un processus de console ajoute ou supprime des fonctions de gestionnaire supplémentaires en appelant la fonction **SetConsoleCtrlHandler**, qui n’affecte pas la liste des fonctions de gestionnaire pour d’autres processus.</span><span class="sxs-lookup"><span data-stu-id="7f47f-126">A console process adds or removes additional handler functions by calling the **SetConsoleCtrlHandler** function, which does not affect the list of handler functions for other processes.</span></span> <span data-ttu-id="7f47f-127">Quand un processus de console reçoit un des signaux de contrôle, ses fonctions de gestionnaire sont appelées selon le principe « dernier enregistré, premier appelé », jusqu’à ce qu’un des gestionnaires retourne `TRUE`.</span><span class="sxs-lookup"><span data-stu-id="7f47f-127">When a console process receives any of the control signals, its handler functions are called on a last-registered, first-called basis until one of the handlers returns `TRUE`.</span></span> <span data-ttu-id="7f47f-128">Si aucun des gestionnaires ne retourne `TRUE`, le gestionnaire par défaut est appelé.</span><span class="sxs-lookup"><span data-stu-id="7f47f-128">If none of the handlers returns `TRUE`, the default handler is called.</span></span>

<span data-ttu-id="7f47f-129">Pour les processus de la console, les combinaisons de touches <kbd>Ctrl</kbd>+<kbd>C</kbd> et <kbd>Ctrl</kbd>+<kbd>Pause</kbd> sont généralement traitées comme des signaux (**CTRL\_C\_EVENT** et **CTRL\_BREAK\_EVENT**).</span><span class="sxs-lookup"><span data-stu-id="7f47f-129">For console processes, the <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations are typically treated as signals (**CTRL\_C\_EVENT** and **CTRL\_BREAK\_EVENT**).</span></span> <span data-ttu-id="7f47f-130">Quand une fenêtre de console avec le focus au clavier reçoit <kbd>CTRL</kbd>+<kbd>C</kbd> ou <kbd>CTRL</kbd>+<kbd>BREAK</kbd>, le signal est généralement passé à tous les processus qui partagent cette console.</span><span class="sxs-lookup"><span data-stu-id="7f47f-130">When a console window with the keyboard focus receives <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd>, the signal is typically passed to all processes sharing that console.</span></span>

<span data-ttu-id="7f47f-131"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> est toujours traitée comme un signal, mais le comportement habituel de <kbd>CTRL</kbd>+<kbd>C</kbd> peut être changé de trois façons qui empêchent l’appel des fonctions du gestionnaire :</span><span class="sxs-lookup"><span data-stu-id="7f47f-131"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but typical <kbd>CTRL</kbd>+<kbd>C</kbd> behavior can be changed in three ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="7f47f-132">La fonction [**SetConsoleMode**](setconsolemode.md) peut désactiver le mode **ENABLE\_PROCESSED\_INPUT** pour la mémoire tampon d’entrée d’une console : <kbd>CTRL</kbd>+<kbd>C</kbd> est donc signalé comme étant une entrée du clavier au lieu d’un signal.</span><span class="sxs-lookup"><span data-stu-id="7f47f-132">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** mode for a console's input buffer, so <kbd>CTRL</kbd>+<kbd>C</kbd> is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="7f47f-133">L’appel de **SetConsoleCtrlHandler** avec les arguments **NULL** et **TRUE** fait que le processus appelant ignore les signaux <kbd>CTRL</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="7f47f-133">Calling **SetConsoleCtrlHandler** with the **NULL** and **TRUE** arguments causes the calling process to ignore <kbd>CTRL</kbd>+<kbd>C</kbd> signals.</span></span> <span data-ttu-id="7f47f-134">Cet attribut est hérité par les processus enfants, mais il peut être activé ou désactivé par n’importe quel processus sans affecter les processus existants.</span><span class="sxs-lookup"><span data-stu-id="7f47f-134">This attribute is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>
- <span data-ttu-id="7f47f-135">Si un processus de console est en cours de débogage et que les signaux <kbd>CTRL</kbd>+<kbd>C</kbd> n’ont pas été désactivés, le système génère une exception **DBG\_CONTROL\_C**.</span><span class="sxs-lookup"><span data-stu-id="7f47f-135">If a console process is being debugged and <kbd>CTRL</kbd>+<kbd>C</kbd> signals have not been disabled, the system generates a **DBG\_CONTROL\_C** exception.</span></span> <span data-ttu-id="7f47f-136">Cette exception est déclenchée seulement à destination du débogueur, et une application ne doit jamais utiliser un gestionnaire d’exceptions pour le gérer.</span><span class="sxs-lookup"><span data-stu-id="7f47f-136">This exception is raised only for the benefit of the debugger, and an application should never use an exception handler to deal with it.</span></span> <span data-ttu-id="7f47f-137">Si le débogueur gère l’exception, une application ne va pas détecter le <kbd>CTRL</kbd>+<kbd>C</kbd>, à une exception près : les attentes susceptibles de déclencher des alertes vont se terminer.</span><span class="sxs-lookup"><span data-stu-id="7f47f-137">If the debugger handles the exception, an application will not notice the <kbd>CTRL</kbd>+<kbd>C</kbd>, with one exception: alertable waits will terminate.</span></span> <span data-ttu-id="7f47f-138">Si le débogueur passe l’exception en « non géré », <kbd>CTRL</kbd>+<kbd>C</kbd> est passé au processus de console et est traité en tant que signal, comme indiqué précédemment.</span><span class="sxs-lookup"><span data-stu-id="7f47f-138">If the debugger passes the exception on unhandled, <kbd>CTRL</kbd>+<kbd>C</kbd> is passed to the console process and treated as a signal, as previously discussed.</span></span>

<span data-ttu-id="7f47f-139">Un processus de console peut utiliser la fonction [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) pour envoyer un signal <kbd>CTRL</kbd>+<kbd>C</kbd> ou <kbd>CTRL</kbd>+<kbd>BREAK</kbd> à un groupe de processus de console.</span><span class="sxs-lookup"><span data-stu-id="7f47f-139">A console process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> signal to a console process group.</span></span>

<span data-ttu-id="7f47f-140">Le système génère des signaux **CTRL\_CLOSE\_EVENT**, **CTRL\_LOGOFF\_EVENT** et **CTRL\_SHUTDOWN\_EVENT** quand l’utilisateur ferme la console, ferme une session ou arrête le système afin que le processus puisse être nettoyé avant l’arrêt.</span><span class="sxs-lookup"><span data-stu-id="7f47f-140">The system generates **CTRL\_CLOSE\_EVENT**, **CTRL\_LOGOFF\_EVENT**, and **CTRL\_SHUTDOWN\_EVENT** signals when the user closes the console, logs off, or shuts down the system so that the process has an opportunity to clean up before termination.</span></span> <span data-ttu-id="7f47f-141">Les fonctions de console, ou les fonctions du runtime C qui appellent des fonctions de console, risquent de ne pas fonctionner de façon fiable lors du traitement des trois signaux mentionnés précédemment.</span><span class="sxs-lookup"><span data-stu-id="7f47f-141">Console functions, or any C run-time functions that call console functions, may not work reliably during processing of any of the three signals mentioned previously.</span></span> <span data-ttu-id="7f47f-142">La raison en est que tout ou partie des routines de nettoyage de la console interne peuvent avoir été appelées avant l’exécution du gestionnaire de signaux du processus.</span><span class="sxs-lookup"><span data-stu-id="7f47f-142">The reason is that some or all of the internal console cleanup routines may have been called before executing the process signal handler.</span></span>

<span data-ttu-id="7f47f-143">**Windows 7, Windows 8, Windows 8.1 et Windows 10 :**</span><span class="sxs-lookup"><span data-stu-id="7f47f-143">**Windows 7, Windows 8, Windows 8.1 and Windows 10:**</span></span>

<span data-ttu-id="7f47f-144">Si une application console charge la bibliothèque gdi32.dll ou user32.dll, la fonction [**HandlerRoutine**](handlerroutine.md) que vous spécifiez quand vous appelez **SetConsoleCtrlHandler** n’est pas appelée pour les événements **CTRL\_LOGOFF\_EVENT** et **CTRL\_SHUTDOWN\_EVENT**.</span><span class="sxs-lookup"><span data-stu-id="7f47f-144">If a console application loads the gdi32.dll or user32.dll library, the [**HandlerRoutine**](handlerroutine.md) function that you specify when you call **SetConsoleCtrlHandler** does not get called for the **CTRL\_LOGOFF\_EVENT** and **CTRL\_SHUTDOWN\_EVENT** events.</span></span> <span data-ttu-id="7f47f-145">Le système d’exploitation reconnaît les processus qui chargent gdi32.dll ou user32.dll en tant qu’applications Windows et non pas en tant qu’applications console.</span><span class="sxs-lookup"><span data-stu-id="7f47f-145">The operating system recognizes processes that load gdi32.dll or user32.dll as Windows applications rather than console applications.</span></span> <span data-ttu-id="7f47f-146">Ce comportement se produit également pour les applications console qui n’appellent pas directement des fonctions dans gdi32.dll ou user32.dll, mais qui appellent des fonctions comme des [fonctions Shell](/previous-versions/windows/desktop/legacy/bb776426(v=vs.85)) qui appellent à leur tour des fonctions dans gdi32.dll ou user32.dll.</span><span class="sxs-lookup"><span data-stu-id="7f47f-146">This behavior also occurs for console applications that do not call functions in gdi32.dll or user32.dll directly, but do call functions such as [Shell functions](/previous-versions/windows/desktop/legacy/bb776426(v=vs.85)) that do in turn call functions in gdi32.dll or user32.dll.</span></span>

<span data-ttu-id="7f47f-147">Pour recevoir des événements quand un utilisateur se déconnecte ou que l’appareil s’arrête dans ces circonstances, créez une fenêtre masquée dans votre application console, puis gérez les messages de fenêtre [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) et [**WM\_ENDSESSION**](/windows/win32/shutdown/wm-endsession) que la fenêtre masquée reçoit.</span><span class="sxs-lookup"><span data-stu-id="7f47f-147">To receive events when a user signs out or the device shuts down in these circumstances, create a hidden window in your console application, and then handle the [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) and [**WM\_ENDSESSION**](/windows/win32/shutdown/wm-endsession) window messages that the hidden window receives.</span></span> <span data-ttu-id="7f47f-148">Vous pouvez créer une fenêtre masquée en appelant la méthode [**CreateWindowEx**](/windows/win32/api/winuser/nf-winuser-createwindowexa) avec le paramètre *dwExStyle* défini sur 0.</span><span class="sxs-lookup"><span data-stu-id="7f47f-148">You can create a hidden window by calling the [**CreateWindowEx**](/windows/win32/api/winuser/nf-winuser-createwindowexa) method with the *dwExStyle* parameter set to 0.</span></span>

## <a name="examples"></a><span data-ttu-id="7f47f-149">Exemples</span><span class="sxs-lookup"><span data-stu-id="7f47f-149">Examples</span></span>

<span data-ttu-id="7f47f-150">Pour obtenir un exemple, consultez [Inscription d’une fonction de gestionnaire de contrôle](registering-a-control-handler-function.md).</span><span class="sxs-lookup"><span data-stu-id="7f47f-150">For an example, see [Registering a Control Handler Function](registering-a-control-handler-function.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="7f47f-151">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7f47f-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="7f47f-152">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7f47f-152">Minimum supported client</span></span> | <span data-ttu-id="7f47f-153">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="7f47f-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="7f47f-154">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7f47f-154">Minimum supported server</span></span> | <span data-ttu-id="7f47f-155">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="7f47f-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="7f47f-156">En-tête</span><span class="sxs-lookup"><span data-stu-id="7f47f-156">Header</span></span> | <span data-ttu-id="7f47f-157">ConsoleApi.h (via WinCon.h, inclure Windows.h)</span><span class="sxs-lookup"><span data-stu-id="7f47f-157">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="7f47f-158">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="7f47f-158">Library</span></span> | <span data-ttu-id="7f47f-159">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="7f47f-159">Kernel32.lib</span></span> |
| <span data-ttu-id="7f47f-160">DLL</span><span class="sxs-lookup"><span data-stu-id="7f47f-160">DLL</span></span> | <span data-ttu-id="7f47f-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7f47f-161">Kernel32.dll</span></span> |
| <span data-ttu-id="7f47f-162">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="7f47f-162">Unicode and ANSI names</span></span> | |

## <a name="see-also"></a><span data-ttu-id="7f47f-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f47f-163">See also</span></span>

[<span data-ttu-id="7f47f-164">Gestionnaires de contrôle d’une console</span><span class="sxs-lookup"><span data-stu-id="7f47f-164">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="7f47f-165">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="7f47f-165">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="7f47f-166">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="7f47f-166">**ExitProcess**</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess)

[<span data-ttu-id="7f47f-167">**GenerateConsoleCtrlEvent**</span><span class="sxs-lookup"><span data-stu-id="7f47f-167">**GenerateConsoleCtrlEvent**</span></span>](generateconsolectrlevent.md)

[<span data-ttu-id="7f47f-168">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="7f47f-168">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="7f47f-169">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="7f47f-169">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="7f47f-170">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="7f47f-170">**SetConsoleMode**</span></span>](setconsolemode.md)