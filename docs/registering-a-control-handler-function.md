---
title: Enregistrement d’une fonction du gestionnaire de contrôle
description: Il s’agit d’un exemple de la fonction SetConsoleCtrlHandler utilisée pour installer un gestionnaire de contrôle.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_registering\_a\_control\_handler\_function'
- base.registering\_a\_control\_handler\_function
- consoles.registering\_a\_control\_handler\_function
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f1c72277-f06c-4147-a74c-6aaf6feb730e
ms.openlocfilehash: 4142f4f0871bd11a56085324195702ab47301227
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039447"
---
# <a name="registering-a-control-handler-function"></a><span data-ttu-id="482fc-104">Enregistrement d’une fonction du gestionnaire de contrôle</span><span class="sxs-lookup"><span data-stu-id="482fc-104">Registering a Control Handler Function</span></span>

<span data-ttu-id="482fc-105">Il s’agit d’un exemple de la fonction [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) utilisée pour installer un gestionnaire de contrôle.</span><span class="sxs-lookup"><span data-stu-id="482fc-105">This is an example of the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function that is used to install a control handler.</span></span>

<span data-ttu-id="482fc-106">Quand un signal CTRL + C est reçu, le gestionnaire de contrôle retourne la **valeur true** , ce qui indique qu’il a géré le signal.</span><span class="sxs-lookup"><span data-stu-id="482fc-106">When a CTRL+C signal is received, the control handler returns **TRUE** , indicating that it has handled the signal.</span></span> <span data-ttu-id="482fc-107">Cela empêche l’appel d’autres gestionnaires de contrôle.</span><span class="sxs-lookup"><span data-stu-id="482fc-107">Doing this prevents other control handlers from being called.</span></span>

<span data-ttu-id="482fc-108">Lorsqu’un signal d' **\_ \_ événement Ctrl Close** est reçu, le gestionnaire de contrôle retourne la **valeur true** et le processus se termine.</span><span class="sxs-lookup"><span data-stu-id="482fc-108">When a **CTRL\_CLOSE\_EVENT** signal is received, the control handler returns **TRUE** and the process terminates.</span></span>

<span data-ttu-id="482fc-109">Lors de la réception d’un événement **CTRL \_ break \_** , d’un **\_ \_ événement Ctrl Logoff** ou de **CTRL \_ Shutdown \_** , le gestionnaire de contrôle retourne la **valeur false** .</span><span class="sxs-lookup"><span data-stu-id="482fc-109">When a **CTRL\_BREAK\_EVENT** , **CTRL\_LOGOFF\_EVENT** , or **CTRL\_SHUTDOWN\_EVENT** signal is received, the control handler returns **FALSE** .</span></span> <span data-ttu-id="482fc-110">Cela entraîne le passage du signal à la fonction de gestionnaire de contrôle suivante.</span><span class="sxs-lookup"><span data-stu-id="482fc-110">Doing this causes the signal to be passed to the next control handler function.</span></span> <span data-ttu-id="482fc-111">Si aucun autre gestionnaire de contrôles n’a été inscrit ou si aucun des gestionnaires inscrits ne retourne la **valeur true** , le gestionnaire par défaut est utilisé, ce qui entraîne l’arrêt du processus.</span><span class="sxs-lookup"><span data-stu-id="482fc-111">If no other control handlers have been registered or none of the registered handlers returns **TRUE** , the default handler will be used, resulting in the process being terminated.</span></span>

```C
// CtrlHandler.cpp : This file contains the 'main' function. Program execution begins and ends there.
//

#include "pch.h"

#include <windows.h>
#include <stdio.h>

BOOL WINAPI CtrlHandler(DWORD fdwCtrlType)
{
    switch (fdwCtrlType)
    {
        // Handle the CTRL-C signal.
    case CTRL_C_EVENT:
        printf("Ctrl-C event\n\n");
        Beep(750, 300);
        return TRUE;

        // CTRL-CLOSE: confirm that the user wants to exit.
    case CTRL_CLOSE_EVENT:
        Beep(600, 200);
        printf("Ctrl-Close event\n\n");
        return TRUE;

        // Pass other signals to the next handler.
    case CTRL_BREAK_EVENT:
        Beep(900, 200);
        printf("Ctrl-Break event\n\n");
        return FALSE;

    case CTRL_LOGOFF_EVENT:
        Beep(1000, 200);
        printf("Ctrl-Logoff event\n\n");
        return FALSE;

    case CTRL_SHUTDOWN_EVENT:
        Beep(750, 500);
        printf("Ctrl-Shutdown event\n\n");
        return FALSE;

    default:
        return FALSE;
    }
}

int main(void)
{
    if (SetConsoleCtrlHandler(CtrlHandler, TRUE))
    {
        printf("\nThe Control Handler is installed.\n");
        printf("\n -- Now try pressing Ctrl+C or Ctrl+Break, or");
        printf("\n    try logging off or closing the console...\n");
        printf("\n(...waiting in a loop for events...)\n\n");

        while (1) {}
    }
    else
    {
        printf("\nERROR: Could not set control handler");
        return 1;
    }
    return 0;
}
```
