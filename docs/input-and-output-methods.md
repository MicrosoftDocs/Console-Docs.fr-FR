---
title: Méthodes d’entrée et de sortie
description: Il existe deux approches différentes pour les e/s de la console, dont le choix dépend de la flexibilité et du contrôle dont une application a besoin.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_input\_and\_output\_methods'
- base.input\_and\_output\_methods
- consoles.input\_and\_output\_methods
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 55a86d5d-d0b1-4d0c-b42f-7342809289ad
ms.openlocfilehash: 29f4ca8f4851c73f79d810f56b57f490995cad04
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059488"
---
# <a name="input-and-output-methods"></a><span data-ttu-id="6df1c-104">Méthodes d’entrée et de sortie</span><span class="sxs-lookup"><span data-stu-id="6df1c-104">Input and Output Methods</span></span>


<span data-ttu-id="6df1c-105">Il existe deux approches différentes pour les e/s de la console, dont le choix dépend de la flexibilité et du contrôle dont une application a besoin.</span><span class="sxs-lookup"><span data-stu-id="6df1c-105">There are two different approaches to console I/O, the choice of which depends on how much flexibility and control an application needs.</span></span> <span data-ttu-id="6df1c-106">L’approche de haut niveau permet d’effectuer des e/s de flux de caractères simples, mais elle limite l’accès aux mémoires tampons d’entrée et d’écran d’une console.</span><span class="sxs-lookup"><span data-stu-id="6df1c-106">The high-level approach enables simple character stream I/O, but it limits access to a console's input and screen buffers.</span></span> <span data-ttu-id="6df1c-107">L’approche de bas niveau oblige les développeurs à écrire davantage de code et à choisir parmi une plus grande gamme de fonctions, mais il offre également une plus grande flexibilité à une application.</span><span class="sxs-lookup"><span data-stu-id="6df1c-107">The low-level approach requires that developers write more code and choose among a greater range of functions, but it also gives an application more flexibility.</span></span>

<span data-ttu-id="6df1c-108">Une application peut utiliser les fonctions d’e/s de fichier, [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747), ainsi que les fonctions de console, [**ReadConsole**](readconsole.md) et [**WriteConsole**](writeconsole.md), pour les e/s de haut niveau qui fournissent un accès indirect aux mémoires tampons d’entrée et d’écran d’une console.</span><span class="sxs-lookup"><span data-stu-id="6df1c-108">An application can use the file I/O functions, [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747), and the console functions, [**ReadConsole**](readconsole.md) and [**WriteConsole**](writeconsole.md), for high-level I/O that provides indirect access to a console's input and screen buffers.</span></span> <span data-ttu-id="6df1c-109">Les fonctions d’entrée de haut niveau filtrent et traitent les données dans la mémoire tampon d’entrée d’une console pour retourner les entrées sous la forme d’un flux de caractères, en ignorant la souris et l’entrée de redimensionnement de mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="6df1c-109">The high-level input functions filter and process the data in a console's input buffer to return input as a stream of characters, discarding mouse and buffer-resizing input.</span></span> <span data-ttu-id="6df1c-110">De même, les fonctions de sortie de haut niveau écrivent un flux de caractères qui s’affichent à l’emplacement du curseur actuel dans une mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="6df1c-110">Similarly, the high-level output functions write a stream of characters that are displayed at the current cursor location in a screen buffer.</span></span> <span data-ttu-id="6df1c-111">Une application contrôle la façon dont ces fonctions fonctionnent en définissant les modes d’e/s d’une console.</span><span class="sxs-lookup"><span data-stu-id="6df1c-111">An application controls the way these functions work by setting a console's I/O modes.</span></span>

<span data-ttu-id="6df1c-112">Les fonctions d’e/s de bas niveau fournissent un accès direct aux mémoires tampons d’entrée et d’écran d’une console, ce qui permet à une application d’accéder aux événements d’entrée et aux informations étendues pour le redimensionnement de la souris et de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="6df1c-112">The low-level I/O functions provide direct access to a console's input and screen buffers, enabling an application to access mouse and buffer-resizing input events and extended information for keyboard events.</span></span> <span data-ttu-id="6df1c-113">Les fonctions de sortie de bas niveau permettent à une application de lire ou d’écrire dans un nombre spécifié de cellules de caractères consécutives dans une mémoire tampon d’écran, ou de lire ou d’écrire dans des blocs rectangulaires de cellules de caractères à un emplacement spécifié dans une mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="6df1c-113">Low-level output functions enable an application to read from or write to a specified number of consecutive character cells in a screen buffer, or to read or write to rectangular blocks of character cells at a specified location in a screen buffer.</span></span> <span data-ttu-id="6df1c-114">Les modes d’entrée d’une console affectent l’entrée de bas niveau en permettant à l’application de déterminer si les événements de redimensionnement de la souris et de la mémoire tampon sont placés dans la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="6df1c-114">A console's input modes affect low-level input by enabling the application to determine whether mouse and buffer-resizing events are placed in the input buffer.</span></span> <span data-ttu-id="6df1c-115">Les modes de sortie d’une console n’ont aucun effet sur la sortie de bas niveau.</span><span class="sxs-lookup"><span data-stu-id="6df1c-115">A console's output modes have no effect on low-level output.</span></span>

<span data-ttu-id="6df1c-116">Les méthodes d’e/s de niveau supérieur et bas ne sont pas mutuellement exclusives et une application peut utiliser n’importe quelle combinaison de ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="6df1c-116">The high-level and low-level I/O methods are not mutually exclusive, and an application can use any combination of these functions.</span></span> <span data-ttu-id="6df1c-117">Toutefois, en général, une application utilise une approche ou l’autre uniquement.</span><span class="sxs-lookup"><span data-stu-id="6df1c-117">Typically, however, an application uses one approach or the other exclusively.</span></span>

<span data-ttu-id="6df1c-118">Les rubriques suivantes décrivent les modes de la console, ainsi que les fonctions d’e/s de haut niveau et de bas niveau.</span><span class="sxs-lookup"><span data-stu-id="6df1c-118">The following topics describe the console modes and the high-level and low-level I/O functions.</span></span>

- [<span data-ttu-id="6df1c-119">Modes de la console</span><span class="sxs-lookup"><span data-stu-id="6df1c-119">Console Modes</span></span>](console-modes.md)
- [<span data-ttu-id="6df1c-120">E/s de console de haut niveau</span><span class="sxs-lookup"><span data-stu-id="6df1c-120">High-Level Console I/O</span></span>](high-level-console-i-o.md)
- [<span data-ttu-id="6df1c-121">Modes de console de haut niveau</span><span class="sxs-lookup"><span data-stu-id="6df1c-121">High-Level Console Modes</span></span>](high-level-console-modes.md)
- [<span data-ttu-id="6df1c-122">Fonctions d’entrée et de sortie de la console de haut niveau</span><span class="sxs-lookup"><span data-stu-id="6df1c-122">High-Level Console Input and Output Functions</span></span>](high-level-console-input-and-output-functions.md)
- [<span data-ttu-id="6df1c-123">E/s de console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="6df1c-123">Low-Level Console I/O</span></span>](low-level-console-i-o.md)
- [<span data-ttu-id="6df1c-124">Modes de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="6df1c-124">Low-Level Console Modes</span></span>](low-level-console-modes.md)
- [<span data-ttu-id="6df1c-125">Fonctions d’entrée de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="6df1c-125">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)
- [<span data-ttu-id="6df1c-126">Fonctions de sortie de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="6df1c-126">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

 

 




