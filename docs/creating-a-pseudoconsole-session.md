---
title: Création d’une session pseudoconsole
description: Une session pseudoconsole permet à une application d’héberger les activités d’une application en mode caractère.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, api console, conpty, pseudoconsole, windows pty, pseudo console
ms.localizationpriority: high
ms.openlocfilehash: c1a83b308e4d9a23fdb6b2778561030e619dfdb3
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357929"
---
# <a name="creating-a-pseudoconsole-session"></a>Création d’une session pseudoconsole

La pseudoconsole Windows, également appelée ConPTY ou Windows PTY, est un mécanisme qui a été conçu dans le but de créer un hôte externe pour les activités de sous-système en mode caractère qui remplacent la partie interactivité avec l’utilisateur dans la fenêtre hôte de la console par défaut.

L’hébergement d’une session pseudoconsole est un peu différent d’une session de console traditionnelle. Les sessions de console traditionnelles démarrent automatiquement lorsque le système d’exploitation reconnaît qu’une application en mode caractère est sur le point de s’exécuter. En revanche, il faut que l’application d’hébergement crée une session pseudoconsole et les canaux de communication nécessaires avant la création du processus impliquant l’application enfant en mode caractère qui doit être hébergée. Le processus enfant est toujours créé à l’aide de la fonction [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa), mais avec des informations supplémentaires qui indiquent au système d’exploitation d’établir l’environnement approprié.

Vous trouverez des informations générales sur ce système dans le [billet de blog présentant la pseudoconsole Windows](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).

Des exemples complets d’utilisation de la pseudoconsole sont disponibles dans le référentiel samples du dépôt GitHub [microsoft/terminal](https://github.com/microsoft/terminal).

## <a name="preparing-the-communication-channels"></a>Préparation des canaux de communication

La première étape consiste à créer une paire de canaux de communication synchrones devant être fournie lors de la création de la session pseudoconsole pour une communication bidirectionnelle avec l’application hébergée. Ces canaux sont traités par le système pseudoconsole à l’aide de [**ReadFile**](/windows/desktop/api/fileapi/nf-fileapi-readfile) et [**WriteFile**](/windows/desktop/api/fileapi/nf-fileapi-writefile) avec des [E/S synchrones](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output). Les handles de fichier ou de dispositif d’E/S, comme les flux de fichier ou les canaux, sont acceptables tant qu’une structure [**OVERLAPPED**](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) n’est pas demandée pour une communication asynchrone.

> [!WARNING]
>Pour éviter les blocages et les conditions de concurrence, nous vous recommandons vivement de traiter chacun des canaux de communication sur un thread distinct qui gère sa propre mémoire tampon cliente et sa propre file d’attente de messagerie à l’intérieur de votre application. Le fait de gérer toutes les activités de pseudoconsole sur un même thread peut entraîner un blocage, où l’une des mémoires tampons de communication est pleine et attend votre action pendant que vous tentez de distribuer une requête de blocage sur un autre canal.

## <a name="creating-the-pseudoconsole"></a>Création de la pseudoconsole

Avec les canaux de communication qui ont été établis, identifiez l’extrémité « read » du canal d’entrée et l’extrémité « write » du canal de sortie. Cette paire de handles est fournie lorsque vous appelez [**CreatePseudoConsole**](createpseudoconsole.md) pour créer l’objet.

Lors de la création, vous devez indiquer une taille représentant les dimensions X et Y (en nombre de caractères). Il s’agit des dimensions qui s’appliqueront à la zone d’affichage pour la fenêtre de présentation finale (terminal). Ces valeurs sont utilisées pour créer une mémoire tampon en mémoire à l’intérieur du système pseudoconsole.

La taille de la mémoire tampon fournit des réponses aux applications clientes en mode caractère qui sondent les informations à l’aide des [fonctions de console côté client](console-functions.md) comme [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md), et déterminent la disposition et le positionnement du texte lorsque les clients utilisent des fonctions comme [**WriteConsoleOutput**](writeconsoleoutput.md).

Enfin, un champ d’indicateur est fourni lors de la création d’une pseudoconsole pour exécuter des fonctionnalités spéciales. Par défaut, affectez-lui la valeur 0 pour ne pas avoir de fonctionnalités spéciales.

À ce stade, un seul indicateur spécial permet de demander l’héritage de la position du curseur à partir d’une session de console déjà attachée à l’appelant de l’API pseudoconsole. Cet indicateur est destiné à être utilisé dans des scénarios plus avancés, dans lesquels une application d’hébergement qui prépare une session pseudoconsole est elle-même une application cliente en mode caractère dans un autre environnement de console.

L’exemple d’extrait de code fourni ci-dessous utilise [**CreatePipe**](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe) pour établir une paire de canaux de communication et créer la pseudoconsole.

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
>Cet extrait de code est incomplet. Nous l’utilisons uniquement pour la démonstration de cet appel. Vous devrez gérer la durée de vie des **handles** en conséquence. Si vous ne parvenez pas à gérer correctement la durée de vie des **handles**, cela peut entraîner des blocages, en particulier avec les appels d’E/S synchrones.

À la fin de l’appel à [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) pour créer l’application cliente en mode caractère qui est attachée à la pseudoconsole, les handles reçus lors de la création doivent être libérés de ce processus. Cela réduira le nombre de références de l’objet d’appareil sous-jacent et permettra aux opérations d’E/S de détecter correctement un canal interrompu lorsque la session pseudoconsole ferme sa copie des handles.

## <a name="preparing-for-creation-of-the-child-process"></a>Préparation de la création du processus enfant

La phase suivante consiste à préparer la structure [**STARTUPINFOEX**](/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) qui communiquera les informations sur la pseudoconsole lors du démarrage du processus enfant.

Cette structure donne la possibilité de fournir des informations complexes sur le démarrage, y compris des attributs pour la création des processus et des threads.

Utilisez [**InitializeProcThreadAttributeList**](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) dans un double appel afin de calculer le nombre d’octets nécessaires pour contenir la liste, puis allouez la mémoire demandée et effectuez un nouvel appel en indiquant le pointeur de mémoire opaque pour qu’il soit configuré comme la liste d’attributs.

Ensuite, appelez [**UpdateProcThreadAttribute**](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) en passant la liste d’attributs initialisée avec l’indicateur **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, le handle de la pseudoconsole et la taille du handle de la pseudoconsole.

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

## <a name="creating-the-hosted-process"></a>Création du processus hébergé

Ensuite, appelez [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) en passant la structure [**STARTUPINFOEX**](/windows/desktop/api/winbase/ns-winbase-_startupinfoexw), ainsi que le chemin du fichier exécutable et toute autre information de configuration, le cas échéant. Il est important de définir l’indicateur **EXTENDED_STARTUPINFO_PRESENT** lors de l’appel, afin d’alerter le système que la référence à la pseudoconsole est contenue dans les informations détaillées.

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
> Si vous fermez la session pseudoconsole alors que le processus hébergé est toujours en cours de démarrage et de connexion, l’application cliente peut afficher une boîte de dialogue d’erreur. La même boîte de dialogue d’erreur s’affichera si le processus hébergé reçoit un handle de pseudoconsole non valide pour le démarrage. Dans le code d’initialisation du processus hébergé, les deux circonstances sont identiques. La boîte de dialogue qui est affichée par l’application cliente hébergée en cas d’échec indique `0xc0000142`, ainsi qu’un message détaillant l’échec de l’initialisation.

## <a name="communicating-with-the-pseudoconsole-session"></a>Communication avec la session pseudoconsole

Une fois le processus créé, l’application d’hébergement peut utiliser l’extrémité d’écriture du canal d’entrée pour envoyer des informations sur l’interaction avec l’utilisateur dans la pseudoconsole, et l’extrémité de lecture du canal de sortie pour recevoir des informations graphiques provenant de la console.

Il revient entièrement à l’application d’hébergement de décider comment gérer les activités qui suivront. L’application d’hébergement peut lancer une fenêtre dans un autre thread pour collecter les entrées d’interaction utilisateur, et les sérialiser dans l’extrémité d’écriture du canal d’entrée pour la pseudoconsole et l’application en mode caractère hébergée. Un autre thread peut être lancé pour vider l’extrémité de lecture du canal de sortie de la pseudoconsole, décoder le texte et les informations sur les [séquences de terminal virtuel](console-virtual-terminal-sequences.md), et afficher le tout à l’écran.

Les threads peuvent également être utilisés afin de relayer des informations entre les canaux de la pseudoconsole et un autre canal ou appareil (par exemple, des informations réseau vers un autre processus ou ordinateur), évitant ainsi tout transcodage local des informations.

## <a name="resizing-the-pseudoconsole"></a>Redimensionnement de la pseudoconsole

Pendant l’exécution, il peut arriver que la taille de la mémoire tampon doive être modifiée en raison d’une interaction avec l’utilisateur ou d’une demande reçue hors bande, provenant d’un autre appareil d’affichage ou d’interaction.

Pour ce faire, vous pouvez utiliser la fonction [**ResizePseudoConsole**](resizepseudoconsole.md) en spécifiant à la fois la hauteur et la largeur de la mémoire tampon en nombre de caractères.

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

## <a name="ending-the-pseudoconsole-session"></a>Fermeture d’une session pseudoconsole

Pour mettre fin à la session, appelez la fonction [**ClosePseudoConsole**](closepseudoconsole.md) avec le handle issu de la création de la pseudoconsole d’origine. Toutes les applications clientes en mode caractère qui sont jointes, comme celle de l’appel [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa), seront arrêtées à la fermeture de la session. Si l’enfant d’origine était une application de type shell qui créait d’autres processus, tous les processus attachés associés de l’arborescence seront également arrêtés.

> [!WARNING]
>La fermeture de la session a plusieurs effets secondaires qui peuvent entraîner un blocage si la pseudoconsole est utilisée en mode synchrone à thread unique. Le fait de fermer la session pseudoconsole peut envoyer une mise à jour de frame finale à `hOutput`, qui devra être vidée de la mémoire tampon du canal de communication. En outre, si vous avez sélectionné `PSEUDOCONSOLE_INHERIT_CURSOR` lors de la création de la pseudoconsole et tentez de fermer la pseudoconsole sans répondre au message de requête concernant l’héritage de curseur (reçu sur `hOutput` avec une réponse via `hInput`), un autre blocage peut se produire. Il est recommandé de s’occuper de chacun des canaux de communication de la pseudoconsole sur un thread distinct, ainsi que de les vider et de les traiter jusqu’à ce qu’ils donnent leur accord pour être interrompus par l’application cliente qui se ferme ou par les activités de désactivation lors de l’appel de la fonction [**ClosePseudoConsole**](closepseudoconsole.md).