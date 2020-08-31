---
title: Consoles – Windows Desktop
description: Une console est une application qui fournit des e/s à des applications en ligne de commande.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: 7b447e3c1d6d72c58890797177f6668f5d835d35
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059241"
---
# <a name="consoles"></a><span data-ttu-id="9eb6e-104">Consoles</span><span class="sxs-lookup"><span data-stu-id="9eb6e-104">Consoles</span></span>

<span data-ttu-id="9eb6e-105">Une *console* (ou un *Terminal*) est une application qui fournit des e/s à des applications en mode caractère.</span><span class="sxs-lookup"><span data-stu-id="9eb6e-105">A *console* (or *terminal*) is an application that provides I/O to character-mode applications.</span></span> <span data-ttu-id="9eb6e-106">Ce mécanisme indépendant du processeur facilite le portage des applications en mode caractère existantes ou la création d’outils et d’applications en mode caractères.</span><span class="sxs-lookup"><span data-stu-id="9eb6e-106">This processor-independent mechanism makes it easy to port existing character-mode applications or to create new character-mode tools and applications.</span></span>

<span data-ttu-id="9eb6e-107">Une console se compose d’une mémoire tampon d’entrée et d’une ou plusieurs mémoires tampons d’écran.</span><span class="sxs-lookup"><span data-stu-id="9eb6e-107">A console consists of an input buffer and one or more screen buffers.</span></span> <span data-ttu-id="9eb6e-108">La *mémoire tampon d’entrée* contient une file d’attente d’enregistrements d’entrée, chacun contenant des informations sur un événement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="9eb6e-108">The *input buffer* contains a queue of input records, each of which contains information about an input event.</span></span> <span data-ttu-id="9eb6e-109">La file d’attente d’entrée comprend toujours des événements touche-pression et clé-version.</span><span class="sxs-lookup"><span data-stu-id="9eb6e-109">The input queue always includes key-press and key-release events.</span></span> <span data-ttu-id="9eb6e-110">Il peut également inclure des événements de souris (mouvements de pointeurs et presses de bouton et mises en production) et des événements au cours desquels les actions de l’utilisateur affectent la taille de la mémoire tampon d’écran active.</span><span class="sxs-lookup"><span data-stu-id="9eb6e-110">It may also include mouse events (pointer movements and button presses and releases) and events during which user actions affect the size of the active screen buffer.</span></span> <span data-ttu-id="9eb6e-111">Une *mémoire tampon d’écran* est un tableau à deux dimensions de données de caractères et de couleur pour la sortie dans une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="9eb6e-111">A *screen buffer* is a two-dimensional array of character and color data for output in a console window.</span></span> <span data-ttu-id="9eb6e-112">Un nombre quelconque de processus peuvent partager une console.</span><span class="sxs-lookup"><span data-stu-id="9eb6e-112">Any number of processes can share a console.</span></span>

- [<span data-ttu-id="9eb6e-113">Création d’une console</span><span class="sxs-lookup"><span data-stu-id="9eb6e-113">Creation of a Console</span></span>](creation-of-a-console.md)
- [<span data-ttu-id="9eb6e-114">Attachement à une console</span><span class="sxs-lookup"><span data-stu-id="9eb6e-114">Attaching to a Console</span></span>](attaching-to-a-console.md)
- [<span data-ttu-id="9eb6e-115">Fermeture d’une console</span><span class="sxs-lookup"><span data-stu-id="9eb6e-115">Closing a Console</span></span>](closing-a-console.md)
- [<span data-ttu-id="9eb6e-116">Handles de la console</span><span class="sxs-lookup"><span data-stu-id="9eb6e-116">Console Handles</span></span>](console-handles.md)
- [<span data-ttu-id="9eb6e-117">Mémoire tampon d’entrée de la console</span><span class="sxs-lookup"><span data-stu-id="9eb6e-117">Console Input Buffer</span></span>](console-input-buffer.md)
- [<span data-ttu-id="9eb6e-118">Mémoires tampons d’écran de la console</span><span class="sxs-lookup"><span data-stu-id="9eb6e-118">Console Screen Buffers</span></span>](console-screen-buffers.md)
- [<span data-ttu-id="9eb6e-119">Taille de la mémoire tampon de la fenêtre et de l’écran</span><span class="sxs-lookup"><span data-stu-id="9eb6e-119">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)
- [<span data-ttu-id="9eb6e-120">Sélection de la console</span><span class="sxs-lookup"><span data-stu-id="9eb6e-120">Console Selection</span></span>](console-selection.md)
- [<span data-ttu-id="9eb6e-121">Défilement de la mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="9eb6e-121">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)
