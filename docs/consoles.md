---
title: Consoles – Windows Desktop
description: Une console est une application qui fournit des e/s à des applications en ligne de commande.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: b50ccd3d38b70ce67498451c8272b832c59fcef9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039117"
---
# <a name="consoles"></a><span data-ttu-id="dd300-104">Consoles</span><span class="sxs-lookup"><span data-stu-id="dd300-104">Consoles</span></span>

<span data-ttu-id="dd300-105">Une *console* est une application qui fournit des services d’e/s aux applications en mode caractère.</span><span class="sxs-lookup"><span data-stu-id="dd300-105">A *console* is an application that provides I/O services to character-mode applications.</span></span>

<span data-ttu-id="dd300-106">Une console se compose d’une mémoire tampon d’entrée et d’une ou plusieurs mémoires tampons d’écran.</span><span class="sxs-lookup"><span data-stu-id="dd300-106">A console consists of an input buffer and one or more screen buffers.</span></span> <span data-ttu-id="dd300-107">La *mémoire tampon d’entrée* contient une file d’attente d’enregistrements d’entrée, chacun contenant des informations sur un événement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="dd300-107">The *input buffer* contains a queue of input records, each of which contains information about an input event.</span></span> <span data-ttu-id="dd300-108">La file d’attente d’entrée comprend toujours des événements touche-pression et clé-version.</span><span class="sxs-lookup"><span data-stu-id="dd300-108">The input queue always includes key-press and key-release events.</span></span> <span data-ttu-id="dd300-109">Il peut également inclure des événements de souris (mouvements de pointeurs et presses de bouton et mises en production) et des événements au cours desquels les actions de l’utilisateur affectent la taille de la mémoire tampon d’écran active.</span><span class="sxs-lookup"><span data-stu-id="dd300-109">It may also include mouse events (pointer movements and button presses and releases) and events during which user actions affect the size of the active screen buffer.</span></span> <span data-ttu-id="dd300-110">Une *mémoire tampon d’écran* est un tableau à deux dimensions de données de caractères et de couleur pour la sortie dans une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="dd300-110">A *screen buffer* is a two-dimensional array of character and color data for output in a console window.</span></span> <span data-ttu-id="dd300-111">Un nombre quelconque de processus peuvent partager une console.</span><span class="sxs-lookup"><span data-stu-id="dd300-111">Any number of processes can share a console.</span></span>

> [!TIP]
><span data-ttu-id="dd300-112">Une idée plus large des consoles et de la façon dont elles sont liées aux terminaux et aux applications clientes de ligne de commande est disponible dans la feuille de route de l' **[écosystème](ecosystem-roadmap.md)** .</span><span class="sxs-lookup"><span data-stu-id="dd300-112">A broader idea of consoles and how they relate to terminals and command-line client applications can be found in the **[ecosystem roadmap](ecosystem-roadmap.md)** .</span></span>

- [<span data-ttu-id="dd300-113">Création d’une console</span><span class="sxs-lookup"><span data-stu-id="dd300-113">Creation of a Console</span></span>](creation-of-a-console.md)
- [<span data-ttu-id="dd300-114">Attachement à une console</span><span class="sxs-lookup"><span data-stu-id="dd300-114">Attaching to a Console</span></span>](attaching-to-a-console.md)
- [<span data-ttu-id="dd300-115">Fermeture d’une console</span><span class="sxs-lookup"><span data-stu-id="dd300-115">Closing a Console</span></span>](closing-a-console.md)
- [<span data-ttu-id="dd300-116">Handles de console</span><span class="sxs-lookup"><span data-stu-id="dd300-116">Console Handles</span></span>](console-handles.md)
- [<span data-ttu-id="dd300-117">Mémoire tampon d’entrée d’une console</span><span class="sxs-lookup"><span data-stu-id="dd300-117">Console Input Buffer</span></span>](console-input-buffer.md)
- [<span data-ttu-id="dd300-118">Mémoires tampons d’écran d’une console</span><span class="sxs-lookup"><span data-stu-id="dd300-118">Console Screen Buffers</span></span>](console-screen-buffers.md)
- [<span data-ttu-id="dd300-119">Taille de la mémoire tampon de la fenêtre et de l’écran</span><span class="sxs-lookup"><span data-stu-id="dd300-119">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)
- [<span data-ttu-id="dd300-120">Sélection de consoles</span><span class="sxs-lookup"><span data-stu-id="dd300-120">Console Selection</span></span>](console-selection.md)
- [<span data-ttu-id="dd300-121">Défilement de la mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="dd300-121">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)
