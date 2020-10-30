---
title: Applications en mode caractère
description: Les consoles gèrent les entrées et sorties (e/s) des applications en mode caractère (les applications qui ne fournissent pas leur propre interface utilisateur graphique).
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_character\_mode\_applications'
- base.character\_mode\_applications
- consoles.character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ea3ea214-892c-4953-bc22-7905efbc173f
ms.openlocfilehash: 5e1b0b2b5162360122580f3ea7a100750b96272e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037347"
---
# <a name="character-mode-applications"></a><span data-ttu-id="f1a56-104">Applications en mode caractère</span><span class="sxs-lookup"><span data-stu-id="f1a56-104">Character Mode Applications</span></span>

<span data-ttu-id="f1a56-105">Les consoles gèrent les entrées et sorties (e/s) des applications en mode caractère (les applications qui ne fournissent pas leur propre interface utilisateur graphique).</span><span class="sxs-lookup"><span data-stu-id="f1a56-105">Consoles manage input and output (I/O) for character-mode applications (applications that do not provide their own graphical user interface).</span></span>

<span data-ttu-id="f1a56-106">Les fonctions de console permettent différents niveaux d’accès à une console.</span><span class="sxs-lookup"><span data-stu-id="f1a56-106">The console functions enable different levels of access to a console.</span></span> <span data-ttu-id="f1a56-107">Les fonctions d’e/s de console de haut niveau permettent à une application de lire à partir d’une entrée standard pour récupérer l’entrée au clavier stockée dans la mémoire tampon d’entrée d’une console.</span><span class="sxs-lookup"><span data-stu-id="f1a56-107">The high-level console I/O functions enable an application to read from standard input to retrieve keyboard input stored in a console's input buffer.</span></span> <span data-ttu-id="f1a56-108">Les fonctions permettent également à une application d’écrire dans une sortie standard ou une erreur standard d’afficher du texte dans la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="f1a56-108">The functions also enable an application to write to standard output or standard error to display text in the console's screen buffer.</span></span> <span data-ttu-id="f1a56-109">Les fonctions de haut niveau prennent également en charge la redirection des handles standard et le contrôle des modes de console pour différentes fonctionnalités d’e/s.</span><span class="sxs-lookup"><span data-stu-id="f1a56-109">The high-level functions also support redirection of standard handles and control of console modes for different I/O functionality.</span></span> <span data-ttu-id="f1a56-110">Les fonctions d’e/s de la console de bas niveau permettent aux applications de recevoir des informations détaillées sur les événements de clavier et de souris, ainsi que des événements impliquant des interactions de l’utilisateur avec la fenêtre de la console.</span><span class="sxs-lookup"><span data-stu-id="f1a56-110">The low-level console I/O functions enable applications to receive detailed input about keyboard and mouse events, as well as events involving user interactions with the console window.</span></span> <span data-ttu-id="f1a56-111">Les fonctions de bas niveau permettent également un meilleur contrôle de la sortie à l’écran.</span><span class="sxs-lookup"><span data-stu-id="f1a56-111">The low-level functions also enable greater control of output to the screen.</span></span>

<span data-ttu-id="f1a56-112">Cette vue d’ensemble décrit la prise en charge des applications en mode caractère.</span><span class="sxs-lookup"><span data-stu-id="f1a56-112">This overview describes support for character-mode applications.</span></span>

- [<span data-ttu-id="f1a56-113">À propos des consoles</span><span class="sxs-lookup"><span data-stu-id="f1a56-113">About Consoles</span></span>](about-character-mode-applications.md)
- [<span data-ttu-id="f1a56-114">Utilisation de la console</span><span class="sxs-lookup"><span data-stu-id="f1a56-114">Using the Console</span></span>](using-the-console.md)
- [<span data-ttu-id="f1a56-115">Informations de référence sur la console</span><span class="sxs-lookup"><span data-stu-id="f1a56-115">Console Reference</span></span>](console-reference.md)
