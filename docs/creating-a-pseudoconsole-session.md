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
# <a name="creating-a-pseudoconsole-session"></a>Création d’une session Pseudoconsole

Le Pseudoconsole Windows, parfois également appelé Pseudo console, ConPTY ou Windows PTY, est un mécanisme conçu pour créer un hôte externe pour les activités du sous-système en mode caractère qui remplacent la partie interactivité de l’utilisateur de la fenêtre hôte de la console par défaut.

L’hébergement d’une session pseudoconsole est un peu différent d’une session de console traditionnelle. Les sessions de console traditionnelles démarrent automatiquement lorsque le système d’exploitation reconnaît qu’une application en mode caractères est sur le point de s’exécuter. En revanche, une session pseudoconsole et les canaux de communication doivent être créés par l’application d’hébergement avant de créer le processus avec l’application en mode caractère enfant à héberger. Le processus enfant sera toujours créé à l’aide de la fonction [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) , mais avec des informations supplémentaires qui indiqueront au système d’exploitation d’établir l’environnement approprié.

Vous trouverez des informations générales supplémentaires sur ce système dans le billet de [blog d’annonce initiale](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).

Des exemples complets d’utilisation de Pseudoconsole sont disponibles dans notre référentiel GitHub [Microsoft/console](https://github.com/Microsoft/console) dans le répertoire Samples.

## <a name="preparing-the-communication-channels"></a>Préparation des canaux de communication

La première étape consiste à créer une paire de canaux de communication synchrones qui sera fournie lors de la création de la session pseudoconsole pour une communication bidirectionnelle avec l’application hébergée. Ces canaux sont traités par le système pseudoconsole à l’aide de [**ReadFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) et [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) avec des [e/s synchrones](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output). Les handles de fichiers ou d’e/s d’appareil comme un flux de fichier ou un canal sont acceptables tant qu’une structure [**OVERLAPPED**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) n’est pas requise pour la communication asynchrone.

**OBSERVE**

Pour éviter les blocages et les conditions de concurrence, nous vous recommandons vivement de traiter chacun des canaux de communication sur un thread distinct qui gère son propre état de tampon client et sa file d’attente de messagerie dans votre application. La maintenance de toutes les activités pseudoconsole sur le même thread peut entraîner un interblocage dans lequel l’une des mémoires tampons de communication est remplie et en attente de votre action pendant que vous tentez de distribuer une demande de blocage sur un autre canal.

## <a name="creating-the-pseudoconsole"></a>Création du Pseudoconsole

Avec les canaux de communication qui ont été établis, identifiez l’extrémité « Read » du canal d’entrée et l’extrémité « Write » du canal de sortie. Cette paire de handles est fournie lors de l’appel de [**CreatePseudoConsole**](createpseudoconsole.md) pour créer l’objet.

Lors de la création de, une taille représentant les dimensions X et Y (en nombre de caractères) est également fournie. Il s’agit des dimensions qui s’appliquent à la surface d’affichage pour la fenêtre de présentation finale (terminal). Les valeurs sont utilisées pour créer une mémoire tampon en mémoire à l’intérieur du système pseudoconsole. 

La taille de la mémoire tampon fournit des réponses aux applications en mode caractère du client qui sondent les informations à l’aide des fonctions de la [console côté client](console-functions.md) comme [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) et déterminent la disposition et le positionnement du texte lorsque les clients utilisent des fonctions telles que [**WriteConsoleOutput**](writeconsoleoutput.md).

Enfin, un champ Flags est fourni lors de la création d’un pseudoconsole pour effectuer des fonctionnalités spéciales. Par défaut, affectez-lui la valeur 0 pour ne pas avoir de fonctionnalités spéciales.

À ce stade, un seul indicateur spécial est disponible pour demander l’héritage de la position du curseur à partir d’une session de console déjà attachée à l’appelant de l’API pseudoconsole. Elle est destinée à être utilisée dans des scénarios plus avancés où une application d’hébergement qui prépare une session pseudoconsole est elle-même une application cliente en mode caractère d’un autre environnement de console. 

Un exemple d’extrait de code est fourni ci-dessous en utilisant [**CreatePipe**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) pour établir une paire de canaux de communication et créer le pseudoconsole.

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


**REMARQUE** : 

Cet extrait de code est incomplet et utilisé pour la démonstration de cet appel spécifique uniquement. Vous devez gérer la durée de vie des **Handles**de manière appropriée. L’échec de la gestion de la durée de vie des **Handles**peut entraîner des scénarios de blocage, en particulier avec les appels d’e/s synchrones.

À la fin de l’appel [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) pour créer l’application cliente en mode caractère attachée à pseudoconsole, les handles donnés lors de la création doivent être libérés de ce processus. Cela réduira le décompte de références sur l’objet périphérique sous-jacent et autorisera les opérations d’e/s à détecter correctement un canal rompu lorsque la session pseudoconsole ferme sa copie des handles.

## <a name="preparing-for-creation-of-the-child-process"></a>Préparation de la création du processus enfant

La phase suivante consiste à préparer la structure [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) qui communiquera les informations de pseudoconsole lors du démarrage du processus enfant.

Cette structure contient la possibilité de fournir des informations de démarrage complexes, y compris des attributs pour la création de processus et de threads.

Utilisez [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) à deux reprises pour calculer d’abord le nombre d’octets requis pour contenir la liste, allouer la mémoire demandée, puis appeler à nouveau en fournissant le pointeur de mémoire opaque pour qu’il soit configuré comme liste d’attributs.

Ensuite, appelez [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) en transmettant la liste d’attributs initialisée avec l’indicateur **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, le handle PSEUDOCONSOLE et la taille du descripteur PSEUDOCONSOLE.

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

Ensuite, appelez [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) en passant la structure [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) avec le chemin d’accès à l’exécutable et toutes les informations de configuration supplémentaires, le cas échéant. Il est important de définir l’indicateur **EXTENDED_STARTUPINFO_PRESENT** lors de l’appel de pour alerter le système que la référence pseudoconsole est contenue dans les informations étendues.

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

**OBSERVE**

La fermeture de la session pseudoconsole pendant que le processus hébergé est toujours en cours de démarrage et la connexion peut entraîner l’affichage d’une boîte de dialogue d’erreur par l’application cliente. La même boîte de dialogue d’erreur s’affiche si le processus hébergé reçoit un handle pseudoconsole non valide pour le démarrage. Dans le code d’initialisation du processus hébergé, les deux circonstances sont identiques. La boîte de dialogue contextuelle de l’application cliente hébergée en cas d’échec est lue `0xc0000142` avec un message localisé détaillant l’échec de l’initialisation.

## <a name="communicating-with-the-pseudoconsole-session"></a>Communication avec la session Pseudoconsole

Une fois le processus créé, l’application d’hébergement peut utiliser l’extrémité écriture du canal d’entrée pour envoyer des informations sur l’interaction de l’utilisateur dans le pseudoconsole et l’extrémité de lecture du canal de sortie pour recevoir des informations graphiques de présentation à partir de la console. 

Il revient entièrement à l’application d’hébergement de décider comment gérer les activités supplémentaires. L’application d’hébergement peut lancer une fenêtre dans un autre thread pour collecter l’entrée d’interaction de l’utilisateur et la sérialiser dans l’extrémité d’écriture du canal d’entrée pour le pseudoconsole et l’application en mode caractères hébergée. Un autre thread peut être lancé pour vider l’extrémité de lecture du canal de sortie pour le pseudoconsole, décoder les informations de [séquence de terminal virtuel](console-virtual-terminal-sequences.md) et de texte, et le présenter à l’écran. 

Les threads peuvent également être utilisés pour relayer les informations des canaux pseudoconsole vers un autre canal ou périphérique, y compris un réseau vers des informations distantes vers un autre processus ou un autre ordinateur, tout en évitant tout transcodage local des informations.

## <a name="resizing-the-pseudoconsole"></a>Redimensionnement du Pseudoconsole

Tout au long du runtime, il peut y avoir une circonstance selon laquelle la taille de la mémoire tampon doit être modifiée en raison d’une interaction de l’utilisateur ou d’une demande reçue hors bande à partir d’un autre périphérique d’affichage/interaction.

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

## <a name="ending-the-pseudoconsole-session"></a>Fin de la session Pseudoconsole

Pour mettre fin à la session, appelez la fonction [**ClosePseudoConsole**](closepseudoconsole.md) avec le descripteur de la création du pseudoconsole d’origine. Toutes les applications en mode caractère du client jointes, telles que celles de l’appel [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) , sont arrêtées lorsque la session est fermée. Si l’enfant d’origine était une application de type Shell qui crée d’autres processus, tous les processus attachés associés dans l’arborescence seront également arrêtés.

**OBSERVE**

La fermeture de la session a plusieurs effets secondaires qui peuvent entraîner une condition de blocage si le pseudoconsole est utilisé en mode synchrone à thread unique. Le fait de fermer la session pseudoconsole peut émettre une mise à jour de frame finale `hOutput` qui doit être vidée de la mémoire tampon du canal de communication. En outre, si `PSEUDOCONSOLE_INHERIT_CURSOR` a été sélectionné lors de la création du pseudoconsole, la tentative de fermeture du pseudoconsole sans répondre au message de requête d’héritage de curseur (reçue sur `hOutput` et ayant répondu à via `hInput` ) peut entraîner une autre condition de blocage. Il est recommandé de traiter les canaux de communication pour les pseudoconsole sur des threads individuels et de les traiter jusqu’à ce qu’ils soient interrompus par l’application cliente en cours de fermeture ou par l’achèvement des activités de destruction lors de l’appel de la fonction [**ClosePseudoConsole**](closepseudoconsole.md) .
