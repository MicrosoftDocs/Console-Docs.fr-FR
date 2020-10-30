---
title: À propos des consoles
description: Les consoles fournissent une prise en charge de haut niveau pour les applications en mode caractères simples qui interagissent avec l’utilisateur à l’aide des fonctions qui lisent les entrées standard et écrivent dans une sortie standard ou une erreur standard.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: e20fa54434b4121abd3f77ee530945bf9aa590f2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037527"
---
# <a name="about-character-mode-applications"></a><span data-ttu-id="67c62-104">À propos des applications en mode caractère</span><span class="sxs-lookup"><span data-stu-id="67c62-104">About Character Mode Applications</span></span>

<span data-ttu-id="67c62-105">Applications en mode caractère (ou « ligne de commande ») :</span><span class="sxs-lookup"><span data-stu-id="67c62-105">Character mode (or "command-line") applications:</span></span>

1. <span data-ttu-id="67c62-106">\[Éventuellement \] , lire des données à partir d’une entrée standard (stdin)</span><span class="sxs-lookup"><span data-stu-id="67c62-106">\[Optionally\] Read data from standard input (stdin)</span></span>
2. <span data-ttu-id="67c62-107">Faire « travail »</span><span class="sxs-lookup"><span data-stu-id="67c62-107">Do "work"</span></span>
3. <span data-ttu-id="67c62-108">\[Vous pouvez \] écrire des données dans une sortie standard (stdout) ou une erreur standard (stderr).</span><span class="sxs-lookup"><span data-stu-id="67c62-108">\[Optionally\] Write data to standard output (stdout) or standard error (stderr)</span></span>

<span data-ttu-id="67c62-109">Les applications en mode caractère communiquent avec l’utilisateur final par le biais d’une application « console » (ou « terminal »).</span><span class="sxs-lookup"><span data-stu-id="67c62-109">Character mode applications communicate with the end-user through a "console" (or "terminal") application.</span></span> <span data-ttu-id="67c62-110">Une console convertit l’entrée utilisateur à partir du clavier, de la souris, de l’écran tactile, du stylet, etc., et l’envoie au stdin d’une application en mode caractère.</span><span class="sxs-lookup"><span data-stu-id="67c62-110">A console converts user input from keyboard, mouse, touch-screen, pen, etc., and sends it to a character mode application's stdin.</span></span> <span data-ttu-id="67c62-111">Une console peut également afficher une sortie de texte d’une application en mode caractère sur l’écran de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="67c62-111">A console may also display a character mode application's text output on the user's screen.</span></span>

<span data-ttu-id="67c62-112">Dans Windows, la console est intégrée et fournit une API riche par le biais de laquelle les applications en mode caractère peuvent interagir avec l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="67c62-112">In Windows, the console is built-in and provides a rich API through which character mode applications can interact with the user.</span></span> <span data-ttu-id="67c62-113">Toutefois, dans l’ère récente, l’équipe de la console encourage toutes les applications en mode caractère à être développées avec des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) sur les appels d’API classiques pour une compatibilité maximale entre Windows et d’autres systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="67c62-113">However, in the recent era, the console team is encouraging all character mode applications to be developed with [virtual terminal sequences](console-virtual-terminal-sequences.md) over the classic API calls for maximum compatibility between Windows and other operating systems.</span></span> <span data-ttu-id="67c62-114">Pour plus d’informations sur cette transition et les interruptions de service impliquées, consultez notre discussion sur les [API classiques et les séquences de terminaux virtuels](classic-vs-vt.md).</span><span class="sxs-lookup"><span data-stu-id="67c62-114">More details on this transition and the trade offs involved can be found in our discussion of [classic APIs versus virtual terminal sequences](classic-vs-vt.md).</span></span>

- [<span data-ttu-id="67c62-115">Consoles</span><span class="sxs-lookup"><span data-stu-id="67c62-115">Consoles</span></span>](consoles.md)
- [<span data-ttu-id="67c62-116">Méthodes d’entrée et de sortie</span><span class="sxs-lookup"><span data-stu-id="67c62-116">Input and Output Methods</span></span>](input-and-output-methods.md)
- [<span data-ttu-id="67c62-117">Pages de code d’une console</span><span class="sxs-lookup"><span data-stu-id="67c62-117">Console Code Pages</span></span>](console-code-pages.md)
- [<span data-ttu-id="67c62-118">Gestionnaires de contrôle d’une console</span><span class="sxs-lookup"><span data-stu-id="67c62-118">Console Control Handlers</span></span>](console-control-handlers.md)
- [<span data-ttu-id="67c62-119">Alias d’une console</span><span class="sxs-lookup"><span data-stu-id="67c62-119">Console Aliases</span></span>](console-aliases.md)
- [<span data-ttu-id="67c62-120">Sécurité de la mémoire tampon et droits d’accès d’une console</span><span class="sxs-lookup"><span data-stu-id="67c62-120">Console Buffer Security and Access Rights</span></span>](console-buffer-security-and-access-rights.md)
- [<span data-ttu-id="67c62-121">Problèmes des applications d’une console</span><span class="sxs-lookup"><span data-stu-id="67c62-121">Console Application Issues</span></span>](console-application-issues.md)
