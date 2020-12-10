---
title: Création d’une session pseudoconsole
description: Une session pseudoconsole permet à une application d’héberger les activités d’une application en mode caractère.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, api console, conpty, pseudoconsole, windows pty, pseudo console
ms.localizationpriority: high
ms.openlocfilehash: 8cd057d3e74659fdeff6c569ddb053c881af1de8
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420228"
---
# <a name="creating-a-pseudoconsole-session"></a><span data-ttu-id="151df-104">Création d’une session pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="151df-104">Creating a Pseudoconsole session</span></span>

<span data-ttu-id="151df-105">La pseudoconsole Windows, également appelée ConPTY ou Windows PTY, est un mécanisme qui a été conçu dans le but de créer un hôte externe pour les activités de sous-système en mode caractère qui remplacent la partie interactivité avec l’utilisateur dans la fenêtre hôte de la console par défaut.</span><span class="sxs-lookup"><span data-stu-id="151df-105">The Windows Pseudoconsole, sometimes also referred to as pseudo console, ConPTY, or the Windows PTY, is a mechanism designed for creating an external host for character-mode subsystem activities that replace the user interactivity portion of the default console host window.</span></span>

<span data-ttu-id="151df-106">L’hébergement d’une session pseudoconsole est un peu différent d’une session de console traditionnelle.</span><span class="sxs-lookup"><span data-stu-id="151df-106">Hosting a pseudoconsole session is a bit different than a traditional console session.</span></span> <span data-ttu-id="151df-107">Les sessions de console traditionnelles démarrent automatiquement lorsque le système d’exploitation reconnaît qu’une application en mode caractère est sur le point de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="151df-107">Traditional console sessions automatically start when the operating system recognizes that a character-mode application is about to run.</span></span> <span data-ttu-id="151df-108">En revanche, il faut que l’application d’hébergement crée une session pseudoconsole et les canaux de communication nécessaires avant la création du processus impliquant l’application enfant en mode caractère qui doit être hébergée.</span><span class="sxs-lookup"><span data-stu-id="151df-108">In contrast, a pseudoconsole session and the communication channels need to be created by the hosting application prior to creating the process with the child character-mode application to be hosted.</span></span> <span data-ttu-id="151df-109">Le processus enfant est toujours créé à l’aide de la fonction [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425), mais avec des informations supplémentaires qui indiquent au système d’exploitation d’établir l’environnement approprié.</span><span class="sxs-lookup"><span data-stu-id="151df-109">The child process will still be created using the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function, but with some additional information that will direct the operating system to establish the appropriate environment.</span></span>

<span data-ttu-id="151df-110">Vous trouverez des informations générales sur ce système dans le [billet de blog présentant la pseudoconsole Windows](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span><span class="sxs-lookup"><span data-stu-id="151df-110">You can find additional background information about this system on the [initial announcement blog post](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span></span>

<span data-ttu-id="151df-111">Des exemples complets d’utilisation de la pseudoconsole sont disponibles dans le référentiel samples du dépôt GitHub [microsoft/terminal](https://github.com/microsoft/terminal).</span><span class="sxs-lookup"><span data-stu-id="151df-111">Complete examples of using the Pseudoconsole are available on our GitHub repository [microsoft/terminal](https://github.com/microsoft/terminal) in the samples directory.</span></span>

## <a name="preparing-the-communication-channels"></a><span data-ttu-id="151df-112">Préparation des canaux de communication</span><span class="sxs-lookup"><span data-stu-id="151df-112">Preparing the communication channels</span></span>

<span data-ttu-id="151df-113">La première étape consiste à créer une paire de canaux de communication synchrones devant être fournie lors de la création de la session pseudoconsole pour une communication bidirectionnelle avec l’application hébergée.</span><span class="sxs-lookup"><span data-stu-id="151df-113">The first step is to create a pair of synchronous communication channels that will be provided during creation of the pseudoconsole session for bidirectional communication with the hosted application.</span></span> <span data-ttu-id="151df-114">Ces canaux sont traités par le système pseudoconsole à l’aide de [**ReadFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) et [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) avec des [E/S synchrones](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output).</span><span class="sxs-lookup"><span data-stu-id="151df-114">These channels are processed by the pseudoconsole system using [**ReadFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) and [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) with [synchronous I/O](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output).</span></span> <span data-ttu-id="151df-115">Les handles de fichier ou de dispositif d’E/S, comme les flux de fichier ou les canaux, sont acceptables tant qu’une structure [**OVERLAPPED**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) n’est pas demandée pour une communication asynchrone.</span><span class="sxs-lookup"><span data-stu-id="151df-115">File or I/O device handles like a file stream or pipe are acceptable as long as an [**OVERLAPPED**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) structure is not required for asynchronous communication.</span></span>

> [!WARNING]
><span data-ttu-id="151df-116">Pour éviter les blocages et les conditions de concurrence, nous vous recommandons vivement de traiter chacun des canaux de communication sur un thread distinct qui gère sa propre mémoire tampon cliente et sa propre file d’attente de messagerie à l’intérieur de votre application.</span><span class="sxs-lookup"><span data-stu-id="151df-116">To prevent race conditions and deadlocks, we highly recommend that each of the communication channels is serviced on a separate thread that maintains its own client buffer state and messaging queue inside your application.</span></span> <span data-ttu-id="151df-117">Le fait de gérer toutes les activités de pseudoconsole sur un même thread peut entraîner un blocage, où l’une des mémoires tampons de communication est pleine et attend votre action pendant que vous tentez de distribuer une requête de blocage sur un autre canal.</span><span class="sxs-lookup"><span data-stu-id="151df-117">Servicing all of the pseudoconsole activities on the same thread may result in a deadlock where one of the communications buffers is filled and waiting for your action while you attempt to dispatch a blocking request on another channel.</span></span>

## <a name="creating-the-pseudoconsole"></a><span data-ttu-id="151df-118">Création de la pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="151df-118">Creating the Pseudoconsole</span></span>

<span data-ttu-id="151df-119">Avec les canaux de communication qui ont été établis, identifiez l’extrémité « read » du canal d’entrée et l’extrémité « write » du canal de sortie.</span><span class="sxs-lookup"><span data-stu-id="151df-119">With the communications channels that have been established, identify the "read" end of the input channel and the "write" end of the output channel.</span></span> <span data-ttu-id="151df-120">Cette paire de handles est fournie lorsque vous appelez [**CreatePseudoConsole**](createpseudoconsole.md) pour créer l’objet.</span><span class="sxs-lookup"><span data-stu-id="151df-120">This pair of handles is provided on calling [**CreatePseudoConsole**](createpseudoconsole.md) to create the object.</span></span>

<span data-ttu-id="151df-121">Lors de la création, vous devez indiquer une taille représentant les dimensions X et Y (en nombre de caractères).</span><span class="sxs-lookup"><span data-stu-id="151df-121">On creation, a size representing the X and Y dimensions (in count of characters) is required.</span></span> <span data-ttu-id="151df-122">Il s’agit des dimensions qui s’appliqueront à la zone d’affichage pour la fenêtre de présentation finale (terminal).</span><span class="sxs-lookup"><span data-stu-id="151df-122">These are the dimensions that will apply to the display surface for the final (terminal) presentation window.</span></span> <span data-ttu-id="151df-123">Ces valeurs sont utilisées pour créer une mémoire tampon en mémoire à l’intérieur du système pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="151df-123">The values are used to create an in-memory buffer inside the pseudoconsole system.</span></span>

<span data-ttu-id="151df-124">La taille de la mémoire tampon fournit des réponses aux applications clientes en mode caractère qui sondent les informations à l’aide des [fonctions de console côté client](console-functions.md) comme [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md), et déterminent la disposition et le positionnement du texte lorsque les clients utilisent des fonctions comme [**WriteConsoleOutput**](writeconsoleoutput.md).</span><span class="sxs-lookup"><span data-stu-id="151df-124">The buffer size provide answers to client character-mode applications that probe for information using the [client-side console functions](console-functions.md) like [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) and dictates the layout and positioning of text when clients use functions like [**WriteConsoleOutput**](writeconsoleoutput.md).</span></span>

<span data-ttu-id="151df-125">Enfin, un champ d’indicateur est fourni lors de la création d’une pseudoconsole pour exécuter des fonctionnalités spéciales.</span><span class="sxs-lookup"><span data-stu-id="151df-125">Finally, a flags field is provided on creation of a pseudoconsole to perform special functionality.</span></span> <span data-ttu-id="151df-126">Par défaut, affectez-lui la valeur 0 pour ne pas avoir de fonctionnalités spéciales.</span><span class="sxs-lookup"><span data-stu-id="151df-126">By default, set this to 0 to have no special functionality.</span></span>

<span data-ttu-id="151df-127">À ce stade, un seul indicateur spécial permet de demander l’héritage de la position du curseur à partir d’une session de console déjà attachée à l’appelant de l’API pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="151df-127">At this time, only one special flag is available to request the inheritence of the cursor position from a console session already attached to the caller of the pseudoconsole API.</span></span> <span data-ttu-id="151df-128">Cet indicateur est destiné à être utilisé dans des scénarios plus avancés, dans lesquels une application d’hébergement qui prépare une session pseudoconsole est elle-même une application cliente en mode caractère dans un autre environnement de console.</span><span class="sxs-lookup"><span data-stu-id="151df-128">This is intended for use in more advanced scenarios where a hosting application that is preparing a pseudoconsole session is itself also a client character-mode application of a another console environment.</span></span>

<span data-ttu-id="151df-129">L’exemple d’extrait de code fourni ci-dessous utilise [**CreatePipe**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) pour établir une paire de canaux de communication et créer la pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="151df-129">A sample snippet is provided below utilizing [**CreatePipe**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) to establish a pair of communication channels and create the pseudoconsole.</span></span>

```C

HRESULT SetUpPseudoConsole(COORD size)
{
    HRESULT hr = S_OK;

    // Create communication channels

    // - Close these after CreateProcess of child application with pseudoconsole object.
    HANDLE inputReadSide, outputWriteSide;

    // - Hold onto these and use them for communication with the child through the pseudoconsole.
    HANDLE outputReadSide, inputWriteSide;

    if (!CreatePipe(&inputReadSide, &inputWriteSide, NULL, 0))
    {
        return HRESULT_FROM_WIN32(GetLastError());
    }

    if (!CreatePipe(&outputReadSide, &outputWriteSide, NULL, 0))
    {
        return HRESULT_FROM_WIN32(GetLastError());
    }

    HPCON hPC;
    hr = CreatePseudoConsole(size, inputReadSide, outputWriteSide, 0, &hPC);
    if (FAILED(hr))
    {
        return hr;
    }

    // ...

}
```

> [!NOTE]
><span data-ttu-id="151df-130">Cet extrait de code est incomplet. Nous l’utilisons uniquement pour la démonstration de cet appel.</span><span class="sxs-lookup"><span data-stu-id="151df-130">This snippet is incomplete and used for demonstration of this specific call only.</span></span> <span data-ttu-id="151df-131">Vous devrez gérer la durée de vie des **handles** en conséquence.</span><span class="sxs-lookup"><span data-stu-id="151df-131">You will need to manage the lifetime of the **HANDLE** s appropriately.</span></span> <span data-ttu-id="151df-132">Si vous ne parvenez pas à gérer correctement la durée de vie des **handles**, cela peut entraîner des blocages, en particulier avec les appels d’E/S synchrones.</span><span class="sxs-lookup"><span data-stu-id="151df-132">Failure to manage the lifetime of **HANDLE** s correctly can result in deadlock scenarios, especially with synchronous I/O calls.</span></span>

<span data-ttu-id="151df-133">À la fin de l’appel à [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) pour créer l’application cliente en mode caractère qui est attachée à la pseudoconsole, les handles reçus lors de la création doivent être libérés de ce processus.</span><span class="sxs-lookup"><span data-stu-id="151df-133">Upon completion of the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) call to create the client character-mode application attached to the pseudoconsole, the handles given during creation should be freed from this process.</span></span> <span data-ttu-id="151df-134">Cela réduira le nombre de références de l’objet d’appareil sous-jacent et permettra aux opérations d’E/S de détecter correctement un canal interrompu lorsque la session pseudoconsole ferme sa copie des handles.</span><span class="sxs-lookup"><span data-stu-id="151df-134">This will decrease the reference count on the underlying device object and allow I/O operations to properly detect a broken channel when the pseudoconsole session closes its copy of the handles.</span></span>

## <a name="preparing-for-creation-of-the-child-process"></a><span data-ttu-id="151df-135">Préparation de la création du processus enfant</span><span class="sxs-lookup"><span data-stu-id="151df-135">Preparing for Creation of the Child Process</span></span>

<span data-ttu-id="151df-136">La phase suivante consiste à préparer la structure [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) qui communiquera les informations sur la pseudoconsole lors du démarrage du processus enfant.</span><span class="sxs-lookup"><span data-stu-id="151df-136">The next phase is to prepare the [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure that will convey the pseudoconsole information while starting the child process.</span></span>

<span data-ttu-id="151df-137">Cette structure donne la possibilité de fournir des informations complexes sur le démarrage, y compris des attributs pour la création des processus et des threads.</span><span class="sxs-lookup"><span data-stu-id="151df-137">This structure contains the ability to provide complex startup information including attributes for process and thread creation.</span></span>

<span data-ttu-id="151df-138">Utilisez [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) dans un double appel afin de calculer le nombre d’octets nécessaires pour contenir la liste, puis allouez la mémoire demandée et effectuez un nouvel appel en indiquant le pointeur de mémoire opaque pour qu’il soit configuré comme la liste d’attributs.</span><span class="sxs-lookup"><span data-stu-id="151df-138">Use [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) in a double-call fashion to first calculate the number of bytes required to hold the list, allocate the memory requested, then call again providing the opaque memory pointer to have it set up as the attribute list.</span></span>

<span data-ttu-id="151df-139">Ensuite, appelez [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) en passant la liste d’attributs initialisée avec l’indicateur **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, le handle de la pseudoconsole et la taille du handle de la pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="151df-139">Next, call [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) passing the initialized attribute list with the flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, the pseudoconsole handle, and the size of the pseudoconsole handle.</span></span>

```C

HRESULT PrepareStartupInformation(HPCON hpc, STARTUPINFOEX* psi)
{
    // Prepare Startup Information structure
    STARTUPINFOEX si;
    ZeroMemory(&si, sizeof(si));
    si.StartupInfo.cb = sizeof(STARTUPINFOEX);

    // Discover the size required for the list
    size_t bytesRequired;
    InitializeProcThreadAttributeList(NULL, 1, 0, &bytesRequired);

    // Allocate memory to represent the list
    si.lpAttributeList = (PPROC_THREAD_ATTRIBUTE_LIST)HeapAlloc(GetProcessHeap(), 0, bytesRequired);
    if (!si.lpAttributeList)
    {
        return E_OUTOFMEMORY;
    }

    // Initialize the list memory location
    if (!InitializeProcThreadAttributeList(si.lpAttributeList, 1, 0, &bytesRequired))
    {
        HeapFree(GetProcessHeap(), 0, si.lpAttributeList);
        return HRESULT_FROM_WIN32(GetLastError());
    }

    // Set the pseudoconsole information into the list
    if (!UpdateProcThreadAttribute(attributeList,
                                   0,
                                   PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE,
                                   hpc,
                                   sizeof(hpc),
                                   NULL,
                                   NULL))
    {
        HeapFree(GetProcessHeap(), 0, si.lpAttributeList);
        return HRESULT_FROM_WIN32(GetLastError());
    }

    *psi = si;

    return S_OK;
}

```

## <a name="creating-the-hosted-process"></a><span data-ttu-id="151df-140">Création du processus hébergé</span><span class="sxs-lookup"><span data-stu-id="151df-140">Creating the Hosted Process</span></span>

<span data-ttu-id="151df-141">Ensuite, appelez [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) en passant la structure [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw), ainsi que le chemin du fichier exécutable et toute autre information de configuration, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="151df-141">Next, call [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) passing the [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure along with the path to the executable and any additional configuration information if applicable.</span></span> <span data-ttu-id="151df-142">Il est important de définir l’indicateur **EXTENDED_STARTUPINFO_PRESENT** lors de l’appel, afin d’alerter le système que la référence à la pseudoconsole est contenue dans les informations détaillées.</span><span class="sxs-lookup"><span data-stu-id="151df-142">It is important to set the **EXTENDED_STARTUPINFO_PRESENT** flag when calling to alert the system that the pseudoconsole reference is contained in the extended information.</span></span>

```C
HRESULT SetUpPseudoConsole(COORD size)
{
    // ...

    PCWSTR childApplication = L"C:\\windows\\system32\\cmd.exe";

    // Create mutable text string for CreateProcessW command line string.
    const size_t charsRequired = wcslen(childApplication) + 1; // +1 null terminator
    PWSTR cmdLineMutable = (PWSTR)HeapAlloc(GetProcessHeap(), 0, sizeof(wchar_t) * charsRequired);

    if (!cmdLineMutable)
    {
        return E_OUTOFMEMORY;
    }

    wcscpy_s(cmdLineMutable, bytesRequired, childApplication);

    PROCESS_INFORMATION pi;
    ZeroMemory(&pi, sizeof(pi));

    // Call CreateProcess
    if (!CreateProcessW(NULL,
                        cmdLineMutable,
                        NULL,
                        NULL,
                        FALSE,
                        EXTENDED_STARTUPINFO_PRESENT,
                        NULL,
                        NULL,
                        &siEx.StartupInfo,
                        &pi))
    {
        HeapFree(GetProcessHeap(), 0, cmdLineMutable);
        return HRESULT_FROM_WIN32(GetLastError());
    }

    // ...
}
```

> [!NOTE]
> <span data-ttu-id="151df-143">Si vous fermez la session pseudoconsole alors que le processus hébergé est toujours en cours de démarrage et de connexion, l’application cliente peut afficher une boîte de dialogue d’erreur.</span><span class="sxs-lookup"><span data-stu-id="151df-143">Closing the pseudoconsole session while the hosted process is still starting up and connecting can result in an error dialog being shown by the client application.</span></span> <span data-ttu-id="151df-144">La même boîte de dialogue d’erreur s’affichera si le processus hébergé reçoit un handle de pseudoconsole non valide pour le démarrage.</span><span class="sxs-lookup"><span data-stu-id="151df-144">The same error dialog is shown if the hosted process is given an invalid pseudoconsole handle for startup.</span></span> <span data-ttu-id="151df-145">Dans le code d’initialisation du processus hébergé, les deux circonstances sont identiques.</span><span class="sxs-lookup"><span data-stu-id="151df-145">To the hosted process initialization code, the two circumstances are identical.</span></span> <span data-ttu-id="151df-146">La boîte de dialogue qui est affichée par l’application cliente hébergée en cas d’échec indique `0xc0000142`, ainsi qu’un message détaillant l’échec de l’initialisation.</span><span class="sxs-lookup"><span data-stu-id="151df-146">The pop-up dialog from the hosted client application on failure will read `0xc0000142` with a localized message detailing failure to initialize.</span></span>

## <a name="communicating-with-the-pseudoconsole-session"></a><span data-ttu-id="151df-147">Communication avec la session pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="151df-147">Communicating with the Pseudoconsole Session</span></span>

<span data-ttu-id="151df-148">Une fois le processus créé, l’application d’hébergement peut utiliser l’extrémité d’écriture du canal d’entrée pour envoyer des informations sur l’interaction avec l’utilisateur dans la pseudoconsole, et l’extrémité de lecture du canal de sortie pour recevoir des informations graphiques provenant de la console.</span><span class="sxs-lookup"><span data-stu-id="151df-148">Once the process is created successfully, the hosting application can use the write end of the input pipe to send user interaction information into the pseudoconsole and the read end of the output pipe to receive graphical presentation information from the pseudo console.</span></span>

<span data-ttu-id="151df-149">Il revient entièrement à l’application d’hébergement de décider comment gérer les activités qui suivront.</span><span class="sxs-lookup"><span data-stu-id="151df-149">It is completely up to the hosting application to decide how to handle further activity.</span></span> <span data-ttu-id="151df-150">L’application d’hébergement peut lancer une fenêtre dans un autre thread pour collecter les entrées d’interaction utilisateur, et les sérialiser dans l’extrémité d’écriture du canal d’entrée pour la pseudoconsole et l’application en mode caractère hébergée.</span><span class="sxs-lookup"><span data-stu-id="151df-150">The hosting application could launch a window in another thread to collect user interaction input and serialize it into the write end of the input pipe for the pseudoconsole and the hosted character-mode application.</span></span> <span data-ttu-id="151df-151">Un autre thread peut être lancé pour vider l’extrémité de lecture du canal de sortie de la pseudoconsole, décoder le texte et les informations sur les [séquences de terminal virtuel](console-virtual-terminal-sequences.md), et afficher le tout à l’écran.</span><span class="sxs-lookup"><span data-stu-id="151df-151">Another thread could be launched to drain the read end of the output pipe for the pseudoconsole, decode the text and [virtual terminal sequence](console-virtual-terminal-sequences.md) information, and present that to the screen.</span></span>

<span data-ttu-id="151df-152">Les threads peuvent également être utilisés afin de relayer des informations entre les canaux de la pseudoconsole et un autre canal ou appareil (par exemple, des informations réseau vers un autre processus ou ordinateur), évitant ainsi tout transcodage local des informations.</span><span class="sxs-lookup"><span data-stu-id="151df-152">Threads could also be used to relay the information from the pseudoconsole channels out to a different channel or device including a network to remote information to another process or machine and avoiding any local transcoding of the information.</span></span>

## <a name="resizing-the-pseudoconsole"></a><span data-ttu-id="151df-153">Redimensionnement de la pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="151df-153">Resizing the Pseudoconsole</span></span>

<span data-ttu-id="151df-154">Pendant l’exécution, il peut arriver que la taille de la mémoire tampon doive être modifiée en raison d’une interaction avec l’utilisateur ou d’une demande reçue hors bande, provenant d’un autre appareil d’affichage ou d’interaction.</span><span class="sxs-lookup"><span data-stu-id="151df-154">Throughout the course of runtime, there may be a circumstance by which the size of the buffer needs to be changed due to a user interaction or a request received out of band from another display/interaction device.</span></span>

<span data-ttu-id="151df-155">Pour ce faire, vous pouvez utiliser la fonction [**ResizePseudoConsole**](resizepseudoconsole.md) en spécifiant à la fois la hauteur et la largeur de la mémoire tampon en nombre de caractères.</span><span class="sxs-lookup"><span data-stu-id="151df-155">This can be done with the [**ResizePseudoConsole**](resizepseudoconsole.md) function specifying both the height and width of the buffer in a count of characters.</span></span>

```C
// Theoretical event handler function with theoretical
// event that has associated display properties
// on Source property.
void OnWindowResize(Event e)
{
    // Retrieve width and height dimensions of display in
    // characters using theoretical height/width functions
    // that can retrieve the properties from the display
    // attached to the event.
    COORD size;
    size.X = GetViewWidth(e.Source);
    size.Y = GetViewHeight(e.Source);

    // Call pseudoconsole API to inform buffer dimension update
    ResizePseudoConsole(m_hpc, size);
}
```

## <a name="ending-the-pseudoconsole-session"></a><span data-ttu-id="151df-156">Fermeture d’une session pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="151df-156">Ending the Pseudoconsole Session</span></span>

<span data-ttu-id="151df-157">Pour mettre fin à la session, appelez la fonction [**ClosePseudoConsole**](closepseudoconsole.md) avec le handle issu de la création de la pseudoconsole d’origine.</span><span class="sxs-lookup"><span data-stu-id="151df-157">To end the session, call the [**ClosePseudoConsole**](closepseudoconsole.md) function with the handle from the original pseudoconsole creation.</span></span> <span data-ttu-id="151df-158">Toutes les applications clientes en mode caractère qui sont jointes, comme celle de l’appel [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425), seront arrêtées à la fermeture de la session.</span><span class="sxs-lookup"><span data-stu-id="151df-158">Any attached client character-mode applications, such as the one from the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) call, will be terminated when the session is closed.</span></span> <span data-ttu-id="151df-159">Si l’enfant d’origine était une application de type shell qui créait d’autres processus, tous les processus attachés associés de l’arborescence seront également arrêtés.</span><span class="sxs-lookup"><span data-stu-id="151df-159">If the original child was a shell-type application that creates other processes, any related attached processes in the tree will also be terminated.</span></span>

> [!WARNING]
><span data-ttu-id="151df-160">La fermeture de la session a plusieurs effets secondaires qui peuvent entraîner un blocage si la pseudoconsole est utilisée en mode synchrone à thread unique.</span><span class="sxs-lookup"><span data-stu-id="151df-160">Closing the session has several side effects which can result in a deadlock condition if the pseudoconsole is used in a single-threaded synchronous fashion.</span></span> <span data-ttu-id="151df-161">Le fait de fermer la session pseudoconsole peut envoyer une mise à jour de frame finale à `hOutput`, qui devra être vidée de la mémoire tampon du canal de communication.</span><span class="sxs-lookup"><span data-stu-id="151df-161">The act of closing the pseudoconsole session may emit a final frame update to `hOutput` which should be drained from the communications channel buffer.</span></span> <span data-ttu-id="151df-162">En outre, si vous avez sélectionné `PSEUDOCONSOLE_INHERIT_CURSOR` lors de la création de la pseudoconsole et tentez de fermer la pseudoconsole sans répondre au message de requête concernant l’héritage de curseur (reçu sur `hOutput` avec une réponse via `hInput`), un autre blocage peut se produire.</span><span class="sxs-lookup"><span data-stu-id="151df-162">Additionally, if `PSEUDOCONSOLE_INHERIT_CURSOR` was selected while creating the pseudoconsole, attempting to close the pseudoconsole without responding to the cursor inheritence query message (received on `hOutput` and replied to via `hInput`) may result in another deadlock condition.</span></span> <span data-ttu-id="151df-163">Il est recommandé de s’occuper de chacun des canaux de communication de la pseudoconsole sur un thread distinct, ainsi que de les vider et de les traiter jusqu’à ce qu’ils donnent leur accord pour être interrompus par l’application cliente qui se ferme ou par les activités de désactivation lors de l’appel de la fonction [**ClosePseudoConsole**](closepseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="151df-163">It is recommended that communications channels for the pseudoconsole are serviced on individual threads and remain drained and processed until broken of their own accord by the client application exiting or by the completion of teardown activities in calling the [**ClosePseudoConsole**](closepseudoconsole.md) function.</span></span>
