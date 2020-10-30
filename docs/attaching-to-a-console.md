---
title: Attachement à une console
description: Un processus peut utiliser la fonction AttachConsole pour s’attacher à une console. Un processus peut être attaché à une console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_attaching\_to\_a\_console'
- base.attaching\_to\_a\_console
- consoles.attaching\_to\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 348e572f-2448-4384-9822-fab01d4ba255
ms.openlocfilehash: 793cc83c0af1f8b0ae4be026f966a79dd034250e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037457"
---
# <a name="attaching-to-a-console"></a><span data-ttu-id="6ee81-105">Attachement à une console</span><span class="sxs-lookup"><span data-stu-id="6ee81-105">Attaching to a Console</span></span>

<span data-ttu-id="6ee81-106">Un processus peut utiliser la fonction [**AttachConsole**](attachconsole.md) pour attacher une console en tant que client.</span><span class="sxs-lookup"><span data-stu-id="6ee81-106">A process can use the [**AttachConsole**](attachconsole.md) function to attach to a console as a client.</span></span> <span data-ttu-id="6ee81-107">Un processus peut être attaché à une console.</span><span class="sxs-lookup"><span data-stu-id="6ee81-107">A process can be attached to one console.</span></span>

<span data-ttu-id="6ee81-108">Un grand nombre de processus peuvent être attachés à une console.</span><span class="sxs-lookup"><span data-stu-id="6ee81-108">A console can have many processes attached to it.</span></span> <span data-ttu-id="6ee81-109">Pour récupérer une liste des processus attachés à une console, appelez la fonction [**GetConsoleProcessList**](getconsoleprocesslist.md) .</span><span class="sxs-lookup"><span data-stu-id="6ee81-109">To retrieve a list of the processes attached to a console, call the [**GetConsoleProcessList**](getconsoleprocesslist.md) function.</span></span>

<span data-ttu-id="6ee81-110">Pour attacher en tant que serveur, consultez les informations relatives à [**Pseudoconsoles**](pseudoconsoles.md).</span><span class="sxs-lookup"><span data-stu-id="6ee81-110">To attach as a server, see information about [**Pseudoconsoles**](pseudoconsoles.md).</span></span>
