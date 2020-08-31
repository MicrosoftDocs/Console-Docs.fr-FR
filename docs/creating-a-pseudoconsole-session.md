---
title: Création d’une session Pseudoconsole
description: Une session pseudoconsole permettra à une application d’héberger les activités d’une application en mode caractère
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API console, conpty, pseudoconsole, Windows Pty, Pseudo console
ms.openlocfilehash: ec63cf4bfc1502aa37b0b336f1ffdc7bab2be07e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059221"
---
# <a name="creating-a-pseudoconsole-session"></a><span data-ttu-id="820ab-104">Création d’une session Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="820ab-104">Creating a Pseudoconsole session</span></span>

<span data-ttu-id="820ab-105">Le Pseudoconsole Windows, parfois également appelé Pseudo console, ConPTY ou Windows PTY, est un mécanisme conçu pour créer un hôte externe pour les activités du sous-système en mode caractère qui remplacent la partie interactivité de l’utilisateur de la fenêtre hôte de la console par défaut.</span><span class="sxs-lookup"><span data-stu-id="820ab-105">The Windows Pseudoconsole, sometimes also referred to as pseudo console, ConPTY, or the Windows PTY, is a mechanism designed for creating an external host for character-mode subsystem activities that replace the user interactivity portion of the default console host window.</span></span>

<span data-ttu-id="820ab-106">L’hébergement d’une session pseudoconsole est un peu différent d’une session de console traditionnelle.</span><span class="sxs-lookup"><span data-stu-id="820ab-106">Hosting a pseudoconsole session is a bit different than a traditional console session.</span></span> <span data-ttu-id="820ab-107">Les sessions de console traditionnelles démarrent automatiquement lorsque le système d’exploitation reconnaît qu’une application en mode caractères est sur le point de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="820ab-107">Traditional console sessions automatically start when the operating system recognizes that a character-mode application is about to run.</span></span> <span data-ttu-id="820ab-108">En revanche, une session pseudoconsole et les canaux de communication doivent être créés par l’application d’hébergement avant de créer le processus avec l’application en mode caractère enfant à héberger.</span><span class="sxs-lookup"><span data-stu-id="820ab-108">In contrast, a pseudoconsole session and the communication channels need to be created by the hosting application prior to creating the process with the child character-mode application to be hosted.</span></span> <span data-ttu-id="820ab-109">Le processus enfant sera toujours créé à l’aide de la fonction [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) , mais avec des informations supplémentaires qui indiqueront au système d’exploitation d’établir l’environnement approprié.</span><span class="sxs-lookup"><span data-stu-id="820ab-109">The child process will still be created using the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function, but with some additional information that will direct the operating system to establish the appropriate environment.</span></span>

<span data-ttu-id="820ab-110">Vous trouverez des informations générales supplémentaires sur ce système dans le billet de [blog d’annonce initiale](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span><span class="sxs-lookup"><span data-stu-id="820ab-110">You can find additional background information about this system on the [initial announcement blog post](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span></span>

<span data-ttu-id="820ab-111">Des exemples complets d’utilisation de Pseudoconsole sont disponibles dans notre référentiel GitHub [Microsoft/console](https://github.com/Microsoft/console) dans le répertoire Samples.</span><span class="sxs-lookup"><span data-stu-id="820ab-111">Complete examples of using the Pseudoconsole are available on our GitHub repository [Microsoft/console](https://github.com/Microsoft/console) in the samples directory.</span></span>

## <a name="preparing-the-communication-channels"></a><span data-ttu-id="820ab-112">Préparation des canaux de communication</span><span class="sxs-lookup"><span data-stu-id="820ab-112">Preparing the communication channels</span></span>

<span data-ttu-id="820ab-113">La première étape consiste à créer une paire de canaux de communication synchrones qui sera fournie lors de la création de la session pseudoconsole pour une communication bidirectionnelle avec l’application hébergée.</span><span class="sxs-lookup"><span data-stu-id="820ab-113">The first step is to create a pair of synchronous communication channels that will be provided during creation of the pseudoconsole session for bidirectional communication with the hosted application.</span></span> <span data-ttu-id="820ab-114">Ces canaux sont traités par le système pseudoconsole à l’aide de [**ReadFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) et [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) avec des [e/s synchrones](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output).</span><span class="sxs-lookup"><span data-stu-id="820ab-114">These channels are processed by the pseudoconsole system using [**ReadFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) and [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) with [synchronous I/O](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output).</span></span> <span data-ttu-id="820ab-115">Les handles de fichiers ou d’e/s d’appareil comme un flux de fichier ou un canal sont acceptables tant qu’une structure [**OVERLAPPED**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) n’est pas requise pour la communication asynchrone.</span><span class="sxs-lookup"><span data-stu-id="820ab-115">File or I/O device handles like a file stream or pipe are acceptable as long as an [**OVERLAPPED**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) structure is not required for asynchronous communication.</span></span>

<span data-ttu-id="820ab-116">**OBSERVE**</span><span class="sxs-lookup"><span data-stu-id="820ab-116">**NOTE:**</span></span>

<span data-ttu-id="820ab-117">Pour éviter les blocages et les conditions de concurrence, nous vous recommandons vivement de traiter chacun des canaux de communication sur un thread distinct qui gère son propre état de tampon client et sa file d’attente de messagerie dans votre application.</span><span class="sxs-lookup"><span data-stu-id="820ab-117">To prevent race conditions and deadlocks, we highly recommend that each of the communication channels is serviced on a separate thread that maintains its own client buffer state and messaging queue inside your application.</span></span> <span data-ttu-id="820ab-118">La maintenance de toutes les activités pseudoconsole sur le même thread peut entraîner un interblocage dans lequel l’une des mémoires tampons de communication est remplie et en attente de votre action pendant que vous tentez de distribuer une demande de blocage sur un autre canal.</span><span class="sxs-lookup"><span data-stu-id="820ab-118">Servicing all of the pseudoconsole activities on the same thread may result in a deadlock where one of the communications buffers is filled and waiting for your action while you attempt to dispatch a blocking request on another channel.</span></span>

## <a name="creating-the-pseudoconsole"></a><span data-ttu-id="820ab-119">Création du Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="820ab-119">Creating the Pseudoconsole</span></span>

<span data-ttu-id="820ab-120">Avec les canaux de communication qui ont été établis, identifiez l’extrémité « Read » du canal d’entrée et l’extrémité « Write » du canal de sortie.</span><span class="sxs-lookup"><span data-stu-id="820ab-120">With the communications channels that have been established, identify the "read" end of the input channel and the "write" end of the output channel.</span></span> <span data-ttu-id="820ab-121">Cette paire de handles est fournie lors de l’appel de [**CreatePseudoConsole**](createpseudoconsole.md) pour créer l’objet.</span><span class="sxs-lookup"><span data-stu-id="820ab-121">This pair of handles is provided on calling [**CreatePseudoConsole**](createpseudoconsole.md) to create the object.</span></span>

<span data-ttu-id="820ab-122">Lors de la création de, une taille représentant les dimensions X et Y (en nombre de caractères) est également fournie.</span><span class="sxs-lookup"><span data-stu-id="820ab-122">When creating, a size representing the X and Y dimensions (in count of characters) is also provided.</span></span> <span data-ttu-id="820ab-123">Il s’agit des dimensions qui s’appliquent à la surface d’affichage pour la fenêtre de présentation finale (terminal).</span><span class="sxs-lookup"><span data-stu-id="820ab-123">This is the dimensions that will apply to the display surface for the final (terminal) presentation window.</span></span> <span data-ttu-id="820ab-124">Les valeurs sont utilisées pour créer une mémoire tampon en mémoire à l’intérieur du système pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="820ab-124">The values are used to create an in-memory buffer inside the pseudoconsole system.</span></span> 

<span data-ttu-id="820ab-125">La taille de la mémoire tampon fournit des réponses aux applications en mode caractère du client qui sondent les informations à l’aide des fonctions de la [console côté client](console-functions.md) comme [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) et déterminent la disposition et le positionnement du texte lorsque les clients utilisent des fonctions telles que [**WriteConsoleOutput**](writeconsoleoutput.md).</span><span class="sxs-lookup"><span data-stu-id="820ab-125">The buffer size provide answers to client character-mode applications that probe for information using the [client-side console functions](console-functions.md) like [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) and dictates the layout and positioning of text when clients use functions like [**WriteConsoleOutput**](writeconsoleoutput.md).</span></span>

<span data-ttu-id="820ab-126">Enfin, un champ Flags est fourni lors de la création d’un pseudoconsole pour effectuer des fonctionnalités spéciales.</span><span class="sxs-lookup"><span data-stu-id="820ab-126">Finally, a flags field is provided on creation of a pseudoconsole to perform special functionality.</span></span> <span data-ttu-id="820ab-127">Par défaut, affectez-lui la valeur 0 pour ne pas avoir de fonctionnalités spéciales.</span><span class="sxs-lookup"><span data-stu-id="820ab-127">By default, set this to 0 to have no special functionality.</span></span>

<span data-ttu-id="820ab-128">À ce stade, un seul indicateur spécial est disponible pour demander l’héritage de la position du curseur à partir d’une session de console déjà attachée à l’appelant de l’API pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="820ab-128">At this time, only one special flag is available to request the inheritence of the cursor position from a console session already attached to the caller of the pseudoconsole API.</span></span> <span data-ttu-id="820ab-129">Elle est destinée à être utilisée dans des scénarios plus avancés où une application d’hébergement qui prépare une session pseudoconsole est elle-même une application cliente en mode caractère d’un autre environnement de console.</span><span class="sxs-lookup"><span data-stu-id="820ab-129">This is intended for use in more advanced scenarios where a hosting application that is preparing a pseudoconsole session is itself also a client character-mode application of a another console environment.</span></span> 

<span data-ttu-id="820ab-130">Un exemple d’extrait de code est fourni ci-dessous en utilisant [**CreatePipe**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) pour établir une paire de canaux de communication et créer le pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="820ab-130">A sample snippet is provided below utilizing [**CreatePipe**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) to establish a pair of communication channels and create the pseudoconsole.</span></span>

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


<span data-ttu-id="820ab-131">**REMARQUE** :</span><span class="sxs-lookup"><span data-stu-id="820ab-131">**NOTE**:</span></span> 

<span data-ttu-id="820ab-132">Cet extrait de code est incomplet et utilisé pour la démonstration de cet appel spécifique uniquement.</span><span class="sxs-lookup"><span data-stu-id="820ab-132">This snippet is incomplete and used for demonstration of this specific call only.</span></span> <span data-ttu-id="820ab-133">Vous devez gérer la durée de vie des **Handles**de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="820ab-133">You will need to manage the lifetime of the **HANDLE**s appropriately.</span></span> <span data-ttu-id="820ab-134">L’échec de la gestion de la durée de vie des **Handles**peut entraîner des scénarios de blocage, en particulier avec les appels d’e/s synchrones.</span><span class="sxs-lookup"><span data-stu-id="820ab-134">Failure to manage the lifetime of **HANDLE**s correctly can result in deadlock scenarios, especially with synchronous I/O calls.</span></span>

<span data-ttu-id="820ab-135">À la fin de l’appel [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) pour créer l’application cliente en mode caractère attachée à pseudoconsole, les handles donnés lors de la création doivent être libérés de ce processus.</span><span class="sxs-lookup"><span data-stu-id="820ab-135">Upon completion of the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) call to create the client character-mode application attached to the pseudoconsole, the handles given during creation should be freed from this process.</span></span> <span data-ttu-id="820ab-136">Cela réduira le décompte de références sur l’objet périphérique sous-jacent et autorisera les opérations d’e/s à détecter correctement un canal rompu lorsque la session pseudoconsole ferme sa copie des handles.</span><span class="sxs-lookup"><span data-stu-id="820ab-136">This will decrease the reference count on the underlying device object and allow I/O operations to properly detect a broken channel when the pseudoconsole session closes its copy of the handles.</span></span>

## <a name="preparing-for-creation-of-the-child-process"></a><span data-ttu-id="820ab-137">Préparation de la création du processus enfant</span><span class="sxs-lookup"><span data-stu-id="820ab-137">Preparing for Creation of the Child Process</span></span>

<span data-ttu-id="820ab-138">La phase suivante consiste à préparer la structure [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) qui communiquera les informations de pseudoconsole lors du démarrage du processus enfant.</span><span class="sxs-lookup"><span data-stu-id="820ab-138">The next phase is to prepare the [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure that will convey the pseudoconsole information while starting the child process.</span></span>

<span data-ttu-id="820ab-139">Cette structure contient la possibilité de fournir des informations de démarrage complexes, y compris des attributs pour la création de processus et de threads.</span><span class="sxs-lookup"><span data-stu-id="820ab-139">This structure contains the ability to provide complex startup information including attributes for process and thread creation.</span></span>

<span data-ttu-id="820ab-140">Utilisez [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) à deux reprises pour calculer d’abord le nombre d’octets requis pour contenir la liste, allouer la mémoire demandée, puis appeler à nouveau en fournissant le pointeur de mémoire opaque pour qu’il soit configuré comme liste d’attributs.</span><span class="sxs-lookup"><span data-stu-id="820ab-140">Use [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) in a double-call fashion to first calculate the number of bytes required to hold the list, allocate the memory requested, then call again providing the opaque memory pointer to have it set up as the attribute list.</span></span>

<span data-ttu-id="820ab-141">Ensuite, appelez [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) en transmettant la liste d’attributs initialisée avec l’indicateur **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, le handle PSEUDOCONSOLE et la taille du descripteur PSEUDOCONSOLE.</span><span class="sxs-lookup"><span data-stu-id="820ab-141">Next, call [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) passing the initialized attribute list with the flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, the pseudoconsole handle, and the size of the pseudoconsole handle.</span></span>

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

## <a name="creating-the-hosted-process"></a><span data-ttu-id="820ab-142">Création du processus hébergé</span><span class="sxs-lookup"><span data-stu-id="820ab-142">Creating the Hosted Process</span></span>

<span data-ttu-id="820ab-143">Ensuite, appelez [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) en passant la structure [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) avec le chemin d’accès à l’exécutable et toutes les informations de configuration supplémentaires, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="820ab-143">Next, call [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) passing the [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure along with the path to the executable and any additional configuration information if applicable.</span></span> <span data-ttu-id="820ab-144">Il est important de définir l’indicateur **EXTENDED_STARTUPINFO_PRESENT** lors de l’appel de pour alerter le système que la référence pseudoconsole est contenue dans les informations étendues.</span><span class="sxs-lookup"><span data-stu-id="820ab-144">It is important to set the **EXTENDED_STARTUPINFO_PRESENT** flag when calling to alert the system that the pseudoconsole reference is contained in the extended information.</span></span>

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

<span data-ttu-id="820ab-145">**OBSERVE**</span><span class="sxs-lookup"><span data-stu-id="820ab-145">**NOTE:**</span></span>

<span data-ttu-id="820ab-146">La fermeture de la session pseudoconsole pendant que le processus hébergé est toujours en cours de démarrage et la connexion peut entraîner l’affichage d’une boîte de dialogue d’erreur par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="820ab-146">Closing the pseudoconsole session while the hosted process is still starting up and connecting can result in an error dialog being shown by the client application.</span></span> <span data-ttu-id="820ab-147">La même boîte de dialogue d’erreur s’affiche si le processus hébergé reçoit un handle pseudoconsole non valide pour le démarrage.</span><span class="sxs-lookup"><span data-stu-id="820ab-147">The same error dialog is shown if the hosted process is given an invalid pseudoconsole handle for startup.</span></span> <span data-ttu-id="820ab-148">Dans le code d’initialisation du processus hébergé, les deux circonstances sont identiques.</span><span class="sxs-lookup"><span data-stu-id="820ab-148">To the hosted process initialization code, the two circumstances are identical.</span></span> <span data-ttu-id="820ab-149">La boîte de dialogue contextuelle de l’application cliente hébergée en cas d’échec est lue `0xc0000142` avec un message localisé détaillant l’échec de l’initialisation.</span><span class="sxs-lookup"><span data-stu-id="820ab-149">The pop-up dialog from the hosted client application on failure will read `0xc0000142` with a localized message detailing failure to initialize.</span></span>

## <a name="communicating-with-the-pseudoconsole-session"></a><span data-ttu-id="820ab-150">Communication avec la session Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="820ab-150">Communicating with the Pseudoconsole Session</span></span>

<span data-ttu-id="820ab-151">Une fois le processus créé, l’application d’hébergement peut utiliser l’extrémité écriture du canal d’entrée pour envoyer des informations sur l’interaction de l’utilisateur dans le pseudoconsole et l’extrémité de lecture du canal de sortie pour recevoir des informations graphiques de présentation à partir de la console.</span><span class="sxs-lookup"><span data-stu-id="820ab-151">Once the process is created successfully, the hosting application can use the write end of the input pipe to send user interaction information into the pseudoconsole and the read end of the output pipe to receive graphical presentation information from the pseudo console.</span></span> 

<span data-ttu-id="820ab-152">Il revient entièrement à l’application d’hébergement de décider comment gérer les activités supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="820ab-152">It is completely up to the hosting application to decide how to handle further activity.</span></span> <span data-ttu-id="820ab-153">L’application d’hébergement peut lancer une fenêtre dans un autre thread pour collecter l’entrée d’interaction de l’utilisateur et la sérialiser dans l’extrémité d’écriture du canal d’entrée pour le pseudoconsole et l’application en mode caractères hébergée.</span><span class="sxs-lookup"><span data-stu-id="820ab-153">The hosting application could launch a window in another thread to collect user interaction input and serialize it into the write end of the input pipe for the pseudoconsole and the hosted character-mode application.</span></span> <span data-ttu-id="820ab-154">Un autre thread peut être lancé pour vider l’extrémité de lecture du canal de sortie pour le pseudoconsole, décoder les informations de [séquence de terminal virtuel](console-virtual-terminal-sequences.md) et de texte, et le présenter à l’écran.</span><span class="sxs-lookup"><span data-stu-id="820ab-154">Another thread could be launched to drain the read end of the output pipe for the pseudoconsole, decode the text and [virtual terminal sequence](console-virtual-terminal-sequences.md) information, and present that to the screen.</span></span> 

<span data-ttu-id="820ab-155">Les threads peuvent également être utilisés pour relayer les informations des canaux pseudoconsole vers un autre canal ou périphérique, y compris un réseau vers des informations distantes vers un autre processus ou un autre ordinateur, tout en évitant tout transcodage local des informations.</span><span class="sxs-lookup"><span data-stu-id="820ab-155">Threads could also be used to relay the information from the pseudoconsole channels out to a different channel or device including a network to remote information to another process or machine and avoiding any local transcoding of the information.</span></span>

## <a name="resizing-the-pseudoconsole"></a><span data-ttu-id="820ab-156">Redimensionnement du Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="820ab-156">Resizing the Pseudoconsole</span></span>

<span data-ttu-id="820ab-157">Tout au long du runtime, il peut y avoir une circonstance selon laquelle la taille de la mémoire tampon doit être modifiée en raison d’une interaction de l’utilisateur ou d’une demande reçue hors bande à partir d’un autre périphérique d’affichage/interaction.</span><span class="sxs-lookup"><span data-stu-id="820ab-157">Throughout the course of runtime, there may be a circumstance by which the size of the buffer needs to be changed due to a user interaction or a request received out of band from another display/interaction device.</span></span>

<span data-ttu-id="820ab-158">Pour ce faire, vous pouvez utiliser la fonction [**ResizePseudoConsole**](resizepseudoconsole.md) en spécifiant à la fois la hauteur et la largeur de la mémoire tampon en nombre de caractères.</span><span class="sxs-lookup"><span data-stu-id="820ab-158">This can be done with the [**ResizePseudoConsole**](resizepseudoconsole.md) function specifying both the height and width of the buffer in a count of characters.</span></span>

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

## <a name="ending-the-pseudoconsole-session"></a><span data-ttu-id="820ab-159">Fin de la session Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="820ab-159">Ending the Pseudoconsole Session</span></span>

<span data-ttu-id="820ab-160">Pour mettre fin à la session, appelez la fonction [**ClosePseudoConsole**](closepseudoconsole.md) avec le descripteur de la création du pseudoconsole d’origine.</span><span class="sxs-lookup"><span data-stu-id="820ab-160">To end the session, call the [**ClosePseudoConsole**](closepseudoconsole.md) function with the handle from the original pseudoconsole creation.</span></span> <span data-ttu-id="820ab-161">Toutes les applications en mode caractère du client jointes, telles que celles de l’appel [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) , sont arrêtées lorsque la session est fermée.</span><span class="sxs-lookup"><span data-stu-id="820ab-161">Any attached client character-mode applications, such as the one from the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) call, will be terminated when the session is closed.</span></span> <span data-ttu-id="820ab-162">Si l’enfant d’origine était une application de type Shell qui crée d’autres processus, tous les processus attachés associés dans l’arborescence seront également arrêtés.</span><span class="sxs-lookup"><span data-stu-id="820ab-162">If the original child was a shell-type application that creates other processes, any related attached processes in the tree will also be terminated.</span></span>

<span data-ttu-id="820ab-163">**OBSERVE**</span><span class="sxs-lookup"><span data-stu-id="820ab-163">**NOTE:**</span></span>

<span data-ttu-id="820ab-164">La fermeture de la session a plusieurs effets secondaires qui peuvent entraîner une condition de blocage si le pseudoconsole est utilisé en mode synchrone à thread unique.</span><span class="sxs-lookup"><span data-stu-id="820ab-164">Closing the session has several side effects which can result in a deadlock condition if the pseudoconsole is used in a single-threaded synchronous fashion.</span></span> <span data-ttu-id="820ab-165">Le fait de fermer la session pseudoconsole peut émettre une mise à jour de frame finale `hOutput` qui doit être vidée de la mémoire tampon du canal de communication.</span><span class="sxs-lookup"><span data-stu-id="820ab-165">The act of closing the pseudoconsole session may emit a final frame update to `hOutput` which should be drained from the communications channel buffer.</span></span> <span data-ttu-id="820ab-166">En outre, si `PSEUDOCONSOLE_INHERIT_CURSOR` a été sélectionné lors de la création du pseudoconsole, la tentative de fermeture du pseudoconsole sans répondre au message de requête d’héritage de curseur (reçue sur `hOutput` et ayant répondu à via `hInput` ) peut entraîner une autre condition de blocage.</span><span class="sxs-lookup"><span data-stu-id="820ab-166">Additionally, if `PSEUDOCONSOLE_INHERIT_CURSOR` was selected while creating the pseudoconsole, attempting to close the pseudoconsole without responding to the cursor inheritence query message (received on `hOutput` and replied to via `hInput`) may result in another deadlock condition.</span></span> <span data-ttu-id="820ab-167">Il est recommandé de traiter les canaux de communication pour les pseudoconsole sur des threads individuels et de les traiter jusqu’à ce qu’ils soient interrompus par l’application cliente en cours de fermeture ou par l’achèvement des activités de destruction lors de l’appel de la fonction [**ClosePseudoConsole**](closepseudoconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="820ab-167">It is recommended that communications channels for the pseudoconsole are serviced on individual threads and remain drained and processed until broken of their own accord by the client application exiting or by the completion of teardown activities in calling the [**ClosePseudoConsole**](closepseudoconsole.md) function.</span></span>
