---
title: SetConsoleCtrlHandler fonction)
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
ms.openlocfilehash: 208eebc92b718fed9856a48dfaf5cbebdaddc1e1
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420268"
---
# <a name="setconsolectrlhandler-function"></a><span data-ttu-id="11868-104">SetConsoleCtrlHandler fonction)</span><span class="sxs-lookup"><span data-stu-id="11868-104">SetConsoleCtrlHandler function</span></span>

<span data-ttu-id="11868-105">Ajoute ou supprime une fonction [**HandlerRoutine**](handlerroutine.md) définie par l’application dans la liste des fonctions de gestionnaire pour le processus appelant.</span><span class="sxs-lookup"><span data-stu-id="11868-105">Adds or removes an application-defined [**HandlerRoutine**](handlerroutine.md) function from the list of handler functions for the calling process.</span></span>

<span data-ttu-id="11868-106">Si aucune fonction de gestionnaire n’est spécifiée, la fonction définit un attribut pouvant être hérité qui détermine si le processus appelant ignore les signaux <kbd>CTRL</kbd> + <kbd>C</kbd> .</span><span class="sxs-lookup"><span data-stu-id="11868-106">If no handler function is specified, the function sets an inheritable attribute that determines whether the calling process ignores <kbd>CTRL</kbd>+<kbd>C</kbd> signals.</span></span>

## <a name="syntax"></a><span data-ttu-id="11868-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11868-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

## <a name="parameters"></a><span data-ttu-id="11868-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="11868-108">Parameters</span></span>

<span data-ttu-id="11868-109">*HandlerRoutine* \[ dans, facultatif\]</span><span class="sxs-lookup"><span data-stu-id="11868-109">*HandlerRoutine* \[in, optional\]</span></span>  
<span data-ttu-id="11868-110">Pointeur vers la fonction [**HandlerRoutine**](handlerroutine.md) définie par l’application à ajouter ou à supprimer.</span><span class="sxs-lookup"><span data-stu-id="11868-110">A pointer to the application-defined [**HandlerRoutine**](handlerroutine.md) function to be added or removed.</span></span> <span data-ttu-id="11868-111">Ce paramètre peut avoir la **valeur null**.</span><span class="sxs-lookup"><span data-stu-id="11868-111">This parameter can be **NULL**.</span></span>

<span data-ttu-id="11868-112">*Ajouter* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="11868-112">*Add* \[in\]</span></span>  
<span data-ttu-id="11868-113">Si ce paramètre a la **valeur true**, le gestionnaire est ajouté ; Si la **valeur est false**, le gestionnaire est supprimé.</span><span class="sxs-lookup"><span data-stu-id="11868-113">If this parameter is **TRUE**, the handler is added; if it is **FALSE**, the handler is removed.</span></span>

<span data-ttu-id="11868-114">Si le paramètre *HandlerRoutine* est **null**, une **valeur true** fait que le processus appelant ignore l’entrée <kbd>CTRL</kbd> + <kbd>c</kbd> , et une valeur **false** restaure le traitement normal de l’entrée <kbd>CTRL</kbd> + <kbd>c</kbd> .</span><span class="sxs-lookup"><span data-stu-id="11868-114">If the *HandlerRoutine* parameter is **NULL**, a **TRUE** value causes the calling process to ignore <kbd>CTRL</kbd>+<kbd>C</kbd> input, and a **FALSE** value restores normal processing of <kbd>CTRL</kbd>+<kbd>C</kbd> input.</span></span> <span data-ttu-id="11868-115">Cet attribut de l’ignorance ou du traitement de <kbd>CTRL</kbd> + <kbd>C</kbd> est hérité par les processus enfants.</span><span class="sxs-lookup"><span data-stu-id="11868-115">This attribute of ignoring or processing <kbd>CTRL</kbd>+<kbd>C</kbd> is inherited by child processes.</span></span>

## <a name="return-value"></a><span data-ttu-id="11868-116">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="11868-116">Return value</span></span>

<span data-ttu-id="11868-117">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="11868-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="11868-118">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="11868-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="11868-119">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="11868-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="11868-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="11868-120">Remarks</span></span>

<span data-ttu-id="11868-121">Cette fonction fournit une notification similaire pour l’application console et les services que [**WM \_ QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) fournit pour les applications graphiques avec une pompe de messages.</span><span class="sxs-lookup"><span data-stu-id="11868-121">This function provides a similar notification for console application and services that [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) provides for graphical applications with a message pump.</span></span> <span data-ttu-id="11868-122">Vous pouvez également utiliser cette fonction à partir d’une application graphique, mais il n’y a aucune garantie qu’elle arriverait avant la notification de **WM \_ QUERYENDSESSION**.</span><span class="sxs-lookup"><span data-stu-id="11868-122">You could also use this function from a graphical application, but there is no guarantee it would arrive before the notification from **WM\_QUERYENDSESSION**.</span></span>

<span data-ttu-id="11868-123">Chaque processus de console possède sa propre liste de fonctions [**HandlerRoutine**](handlerroutine.md) définies par l’application qui gèrent les signaux d’arrêt <kbd>CTRL</kbd> + <kbd>C</kbd> et <kbd>CTRL</kbd> + <kbd>BREAK</kbd> .</span><span class="sxs-lookup"><span data-stu-id="11868-123">Each console process has its own list of application-defined [**HandlerRoutine**](handlerroutine.md) functions that handle <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> signals.</span></span> <span data-ttu-id="11868-124">Les fonctions de gestionnaire gèrent également les signaux générés par le système lorsque l’utilisateur ferme la console, se déconnecte ou arrête le système.</span><span class="sxs-lookup"><span data-stu-id="11868-124">The handler functions also handle signals generated by the system when the user closes the console, logs off, or shuts down the system.</span></span> <span data-ttu-id="11868-125">Initialement, la liste de gestionnaires de chaque processus contient uniquement une fonction de gestionnaire par défaut qui appelle la fonction [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) .</span><span class="sxs-lookup"><span data-stu-id="11868-125">Initially, the handler list for each process contains only a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function.</span></span> <span data-ttu-id="11868-126">Un processus de console ajoute ou supprime des fonctions gestionnaires supplémentaires en appelant la fonction **SetConsoleCtrlHandler** , qui n’affecte pas la liste des fonctions de gestionnaire pour d’autres processus.</span><span class="sxs-lookup"><span data-stu-id="11868-126">A console process adds or removes additional handler functions by calling the **SetConsoleCtrlHandler** function, which does not affect the list of handler functions for other processes.</span></span> <span data-ttu-id="11868-127">Lorsqu’un processus de console reçoit l’un des signaux de contrôle, ses fonctions de gestionnaire sont appelées sur une base de dernier enregistrement, première appel, jusqu’à ce que l’un des gestionnaires retourne `TRUE` .</span><span class="sxs-lookup"><span data-stu-id="11868-127">When a console process receives any of the control signals, its handler functions are called on a last-registered, first-called basis until one of the handlers returns `TRUE`.</span></span> <span data-ttu-id="11868-128">Si aucun des gestionnaires `TRUE` ne retourne, le gestionnaire par défaut est appelé.</span><span class="sxs-lookup"><span data-stu-id="11868-128">If none of the handlers returns `TRUE`, the default handler is called.</span></span>

<span data-ttu-id="11868-129">Pour les processus de console, les combinaisons de touches de séparation <kbd>CTRL</kbd> + <kbd>c</kbd> et <kbd>CTRL</kbd> + <kbd>BREAK</kbd> sont généralement traitées comme des signaux (événement **CTRL + \_ c \_** et **CTRL + \_ \_ événement**).</span><span class="sxs-lookup"><span data-stu-id="11868-129">For console processes, the <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations are typically treated as signals (**CTRL\_C\_EVENT** and **CTRL\_BREAK\_EVENT**).</span></span> <span data-ttu-id="11868-130">Quand une fenêtre de console avec le focus clavier reçoit la <kbd>touche Ctrl</kbd> + <kbd>C</kbd> ou <kbd>CTRL</kbd> + <kbd>BREAK</kbd>, le signal est généralement passé à tous les processus qui partagent cette console.</span><span class="sxs-lookup"><span data-stu-id="11868-130">When a console window with the keyboard focus receives <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd>, the signal is typically passed to all processes sharing that console.</span></span>

<span data-ttu-id="11868-131"><kbd>CTRL</kbd> + L' <kbd>interruption</kbd> est toujours traitée comme un signal, mais le comportement par défaut de <kbd>CTRL</kbd> + <kbd>C</kbd> peut être modifié de trois manières qui empêchent l’appel des fonctions du gestionnaire :</span><span class="sxs-lookup"><span data-stu-id="11868-131"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but typical <kbd>CTRL</kbd>+<kbd>C</kbd> behavior can be changed in three ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="11868-132">La fonction [**SetConsoleMode**](setconsolemode.md) peut désactiver l' **activation du mode \_ \_ d’entrée traité** pour la mémoire tampon d’entrée d’une console. par conséquent, la <kbd>combinaison de touches Ctrl</kbd> + <kbd>C</kbd> est indiquée comme entrée au clavier et non pas comme signal.</span><span class="sxs-lookup"><span data-stu-id="11868-132">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** mode for a console's input buffer, so <kbd>CTRL</kbd>+<kbd>C</kbd> is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="11868-133">L’appel de **SetConsoleCtrlHandler** avec les arguments **null** et **true** fait que le processus appelant ignore les signaux <kbd>CTRL</kbd> + <kbd>C</kbd> .</span><span class="sxs-lookup"><span data-stu-id="11868-133">Calling **SetConsoleCtrlHandler** with the **NULL** and **TRUE** arguments causes the calling process to ignore <kbd>CTRL</kbd>+<kbd>C</kbd> signals.</span></span> <span data-ttu-id="11868-134">Cet attribut est hérité par les processus enfants, mais il peut être activé ou désactivé par n’importe quel processus sans affecter les processus existants.</span><span class="sxs-lookup"><span data-stu-id="11868-134">This attribute is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>
- <span data-ttu-id="11868-135">Si un processus de console est en cours de débogage et <kbd>CTRL</kbd> + que les signaux Ctrl <kbd>c</kbd> n’ont pas été désactivés, le système génère une exception **\_ \_ C de contrôle dbg** .</span><span class="sxs-lookup"><span data-stu-id="11868-135">If a console process is being debugged and <kbd>CTRL</kbd>+<kbd>C</kbd> signals have not been disabled, the system generates a **DBG\_CONTROL\_C** exception.</span></span> <span data-ttu-id="11868-136">Cette exception est déclenchée uniquement pour l’avantage du débogueur, et une application ne doit jamais utiliser un gestionnaire d’exceptions pour le gérer.</span><span class="sxs-lookup"><span data-stu-id="11868-136">This exception is raised only for the benefit of the debugger, and an application should never use an exception handler to deal with it.</span></span> <span data-ttu-id="11868-137">Si le débogueur gère l’exception, une application ne remarquera pas la <kbd>touche Ctrl</kbd> + <kbd>C</kbd>, à une exception près : les attentes alertables se terminent.</span><span class="sxs-lookup"><span data-stu-id="11868-137">If the debugger handles the exception, an application will not notice the <kbd>CTRL</kbd>+<kbd>C</kbd>, with one exception: alertable waits will terminate.</span></span> <span data-ttu-id="11868-138">Si le débogueur passe l’exception sur non géré, <kbd>CTRL</kbd> + <kbd>C</kbd> est passé au processus de console et traité comme un signal, comme indiqué précédemment.</span><span class="sxs-lookup"><span data-stu-id="11868-138">If the debugger passes the exception on unhandled, <kbd>CTRL</kbd>+<kbd>C</kbd> is passed to the console process and treated as a signal, as previously discussed.</span></span>

<span data-ttu-id="11868-139">Un processus de console peut utiliser la fonction [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) pour envoyer un signal d’interruption <kbd>CTRL</kbd> + <kbd>C</kbd> ou <kbd>CTRL</kbd> + <kbd>BREAK</kbd> à un groupe de processus de la console.</span><span class="sxs-lookup"><span data-stu-id="11868-139">A console process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> signal to a console process group.</span></span>

<span data-ttu-id="11868-140">Le système génère des signaux d’événement **CTRL \_ Close \_**, **CTRL de fermeture de \_ session \_** et **CTRL \_ Shutdown \_** quand l’utilisateur ferme la console, ferme une session ou arrête le système afin que le processus puisse effectuer un nettoyage avant son arrêt.</span><span class="sxs-lookup"><span data-stu-id="11868-140">The system generates **CTRL\_CLOSE\_EVENT**, **CTRL\_LOGOFF\_EVENT**, and **CTRL\_SHUTDOWN\_EVENT** signals when the user closes the console, logs off, or shuts down the system so that the process has an opportunity to clean up before termination.</span></span> <span data-ttu-id="11868-141">Les fonctions de console, ou toutes les fonctions runtime C qui appellent des fonctions de console, peuvent ne pas fonctionner de manière fiable pendant le traitement de l’un des trois signaux mentionnés précédemment.</span><span class="sxs-lookup"><span data-stu-id="11868-141">Console functions, or any C run-time functions that call console functions, may not work reliably during processing of any of the three signals mentioned previously.</span></span> <span data-ttu-id="11868-142">En effet, une partie ou la totalité des routines de nettoyage de la console interne peut avoir été appelée avant l’exécution du gestionnaire de signal de processus.</span><span class="sxs-lookup"><span data-stu-id="11868-142">The reason is that some or all of the internal console cleanup routines may have been called before executing the process signal handler.</span></span>

<span data-ttu-id="11868-143">**Windows 7, Windows 8, Windows 8.1 et Windows 10 :**</span><span class="sxs-lookup"><span data-stu-id="11868-143">**Windows 7, Windows 8, Windows 8.1 and Windows 10:**</span></span>

<span data-ttu-id="11868-144">Si une application console charge la gdi32.dll ou la bibliothèque de user32.dll, la fonction [**HandlerRoutine**](handlerroutine.md) que vous spécifiez lorsque vous appelez **SetConsoleCtrlHandler** n’est pas appelée pour les événements **CTRL \_ Logoff \_** et **CTRL \_ Shutdown \_ Event** .</span><span class="sxs-lookup"><span data-stu-id="11868-144">If a console application loads the gdi32.dll or user32.dll library, the [**HandlerRoutine**](handlerroutine.md) function that you specify when you call **SetConsoleCtrlHandler** does not get called for the **CTRL\_LOGOFF\_EVENT** and **CTRL\_SHUTDOWN\_EVENT** events.</span></span> <span data-ttu-id="11868-145">Le système d’exploitation reconnaît les processus qui chargent gdi32.dll ou user32.dll en tant qu’applications Windows plutôt qu’en tant qu’applications console.</span><span class="sxs-lookup"><span data-stu-id="11868-145">The operating system recognizes processes that load gdi32.dll or user32.dll as Windows applications rather than console applications.</span></span> <span data-ttu-id="11868-146">Ce comportement se produit également pour les applications de console qui n’appellent pas directement des fonctions dans gdi32.dll ou user32.dll, mais qui appellent des fonctions telles que des [fonctions Shell](https://msdn.microsoft.com/library/windows/desktop/bb776426) qui appellent à leur tour des fonctions dans gdi32.dll ou user32.dll.</span><span class="sxs-lookup"><span data-stu-id="11868-146">This behavior also occurs for console applications that do not call functions in gdi32.dll or user32.dll directly, but do call functions such as [Shell functions](https://msdn.microsoft.com/library/windows/desktop/bb776426) that do in turn call functions in gdi32.dll or user32.dll.</span></span>

<span data-ttu-id="11868-147">Pour recevoir des événements lorsqu’un utilisateur se déconnecte ou que l’appareil s’arrête dans ces circonstances, créez une fenêtre masquée dans votre application console, puis gérez les messages de fenêtre [**WM \_ QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) et [**WM \_ ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) que la fenêtre masquée reçoit.</span><span class="sxs-lookup"><span data-stu-id="11868-147">To receive events when a user signs out or the device shuts down in these circumstances, create a hidden window in your console application, and then handle the [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) and [**WM\_ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) window messages that the hidden window receives.</span></span> <span data-ttu-id="11868-148">Vous pouvez créer une fenêtre masquée en appelant la méthode [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) avec le paramètre *dwExStyle* défini sur 0.</span><span class="sxs-lookup"><span data-stu-id="11868-148">You can create a hidden window by calling the [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) method with the *dwExStyle* parameter set to 0.</span></span>

## <a name="examples"></a><span data-ttu-id="11868-149">Exemples</span><span class="sxs-lookup"><span data-stu-id="11868-149">Examples</span></span>

<span data-ttu-id="11868-150">Pour obtenir un exemple, consultez [inscription d’une fonction de gestionnaire de contrôle](registering-a-control-handler-function.md).</span><span class="sxs-lookup"><span data-stu-id="11868-150">For an example, see [Registering a Control Handler Function](registering-a-control-handler-function.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="11868-151">Spécifications</span><span class="sxs-lookup"><span data-stu-id="11868-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="11868-152">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="11868-152">Minimum supported client</span></span> | <span data-ttu-id="11868-153">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="11868-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="11868-154">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="11868-154">Minimum supported server</span></span> | <span data-ttu-id="11868-155">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="11868-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="11868-156">En-tête</span><span class="sxs-lookup"><span data-stu-id="11868-156">Header</span></span> | <span data-ttu-id="11868-157">ConsoleApi. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="11868-157">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="11868-158">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="11868-158">Library</span></span> | <span data-ttu-id="11868-159">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="11868-159">Kernel32.lib</span></span> |
| <span data-ttu-id="11868-160">DLL</span><span class="sxs-lookup"><span data-stu-id="11868-160">DLL</span></span> | <span data-ttu-id="11868-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="11868-161">Kernel32.dll</span></span> |
| <span data-ttu-id="11868-162">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="11868-162">Unicode and ANSI names</span></span> | |

## <a name="see-also"></a><span data-ttu-id="11868-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11868-163">See also</span></span>

[<span data-ttu-id="11868-164">Gestionnaires de contrôle d’une console</span><span class="sxs-lookup"><span data-stu-id="11868-164">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="11868-165">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="11868-165">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="11868-166">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="11868-166">**ExitProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[<span data-ttu-id="11868-167">**GenerateConsoleCtrlEvent**</span><span class="sxs-lookup"><span data-stu-id="11868-167">**GenerateConsoleCtrlEvent**</span></span>](generateconsolectrlevent.md)

[<span data-ttu-id="11868-168">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="11868-168">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="11868-169">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="11868-169">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="11868-170">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="11868-170">**SetConsoleMode**</span></span>](setconsolemode.md)
