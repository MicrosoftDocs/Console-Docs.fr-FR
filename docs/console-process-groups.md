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
ms.openlocfilehash: 26a1b0b9001f64ea2dc7465fa298b1383f30aa61
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038447"
---
# <a name="console-process-groups"></a><span data-ttu-id="566c7-104">Groupes de processus de la console</span><span class="sxs-lookup"><span data-stu-id="566c7-104">Console Process Groups</span></span>

<span data-ttu-id="566c7-105">Lorsqu’un processus utilise la fonction [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) pour créer un nouveau processus de console, il peut spécifier l’indicateur de création d’un **\_ nouveau \_ \_ groupe de processus** pour faire du nouveau processus le processus racine d’un groupe de processus de la console.</span><span class="sxs-lookup"><span data-stu-id="566c7-105">When a process uses the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function to create a new console process, it can specify the **CREATE\_NEW\_PROCESS\_GROUP** flag to make the new process the root process of a console process group.</span></span> <span data-ttu-id="566c7-106">Le groupe de processus comprend tous les processus qui sont des descendants du processus racine.</span><span class="sxs-lookup"><span data-stu-id="566c7-106">The process group includes all processes that are descendants of the root process.</span></span>

<span data-ttu-id="566c7-107">Un processus peut utiliser la fonction [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) pour envoyer un signal Ctrl + C ou Ctrl + Pause à tous les processus d’un groupe de processus de la console.</span><span class="sxs-lookup"><span data-stu-id="566c7-107">A process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a CTRL+C or CTRL+BREAK signal to all processes in a console process group.</span></span> <span data-ttu-id="566c7-108">Le signal est reçu uniquement par les processus du groupe qui sont attachés à la même console que le processus qui a appelé **GenerateConsoleCtrlEvent** .</span><span class="sxs-lookup"><span data-stu-id="566c7-108">The signal is only received by those processes in the group that are attached to the same console as the process that called **GenerateConsoleCtrlEvent** .</span></span>
