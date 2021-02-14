---
title: Groupes de processus de la console
description: Lorsqu’un processus utilise la fonction CreateProcess pour créer un nouveau processus de console, il peut spécifier l' \_ indicateur de création d’un nouveau \_ \_ groupe de processus pour faire du nouveau processus le processus racine d’un groupe de processus de la console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_console\_process\_groups'
- base.console\_process\_groups
- consoles.console\_process\_groups
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6cfe5b4b-d677-4747-bbf2-c7243db2346e
ms.openlocfilehash: 8df877eca9a52ef9072685c673461723dda78a0b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358099"
---
# <a name="console-process-groups"></a><span data-ttu-id="a0286-104">Groupes de processus de la console</span><span class="sxs-lookup"><span data-stu-id="a0286-104">Console Process Groups</span></span>

<span data-ttu-id="a0286-105">Lorsqu’un processus utilise la fonction [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) pour créer un nouveau processus de console, il peut spécifier l’indicateur de création d’un **\_ nouveau \_ \_ groupe de processus** pour faire du nouveau processus le processus racine d’un groupe de processus de la console.</span><span class="sxs-lookup"><span data-stu-id="a0286-105">When a process uses the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) function to create a new console process, it can specify the **CREATE\_NEW\_PROCESS\_GROUP** flag to make the new process the root process of a console process group.</span></span> <span data-ttu-id="a0286-106">Le groupe de processus comprend tous les processus qui sont des descendants du processus racine.</span><span class="sxs-lookup"><span data-stu-id="a0286-106">The process group includes all processes that are descendants of the root process.</span></span>

<span data-ttu-id="a0286-107">Un processus peut utiliser la fonction [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) pour envoyer un signal Ctrl + C ou Ctrl + Pause à tous les processus d’un groupe de processus de la console.</span><span class="sxs-lookup"><span data-stu-id="a0286-107">A process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a CTRL+C or CTRL+BREAK signal to all processes in a console process group.</span></span> <span data-ttu-id="a0286-108">Le signal est reçu uniquement par les processus du groupe qui sont attachés à la même console que le processus qui a appelé **GenerateConsoleCtrlEvent**.</span><span class="sxs-lookup"><span data-stu-id="a0286-108">The signal is only received by those processes in the group that are attached to the same console as the process that called **GenerateConsoleCtrlEvent**.</span></span>