---
title: Pseudoconsoles – Bureau Windows
description: Un pseudoconsole est un concept utilisé pour fournir l’aspect d’hébergement ou de maintenance d’une application en mode caractère.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API console, conpty, pseudoconsole
ms.openlocfilehash: 2b2d28065ec4f0e4121decb906e76b34ac1871fc
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039477"
---
# <a name="pseudoconsoles"></a><span data-ttu-id="bce05-104">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="bce05-104">Pseudoconsoles</span></span>

<span data-ttu-id="bce05-105">Un *pseudoconsole* est un type d’appareil qui permet aux applications de devenir l’hôte des applications en mode caractère.</span><span class="sxs-lookup"><span data-stu-id="bce05-105">A *pseudoconsole* is a device type that allows applications to become the host for character-mode applications.</span></span>

<span data-ttu-id="bce05-106">Contrairement à une session de console classique, le système d’exploitation crée une fenêtre d’hébergement pour le compte de l’application en mode caractères pour gérer la sortie graphique et l’entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bce05-106">This is in contrast to a typical console session where the operating system will create a hosting window on behalf of the character-mode application to handle graphical output and user input.</span></span>

<span data-ttu-id="bce05-107">Avec un pseudoconsole, la fenêtre d’hébergement n’est pas créée.</span><span class="sxs-lookup"><span data-stu-id="bce05-107">With a pseudoconsole, the hosting window is not created.</span></span> <span data-ttu-id="bce05-108">L’application qui rend le pseudoconsole doit être responsable de l’affichage de la sortie graphique et de la collecte de l’entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bce05-108">The application that makes the pseudoconsole must become responsible for displaying the graphical output and collecting user input.</span></span> <span data-ttu-id="bce05-109">Les informations peuvent également être relayées plus en détail vers une autre application responsable de ces activités à un point ultérieur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="bce05-109">Alternatively, the information can be relayed further to another application responsible for these activities at a later point in the chain.</span></span>

<span data-ttu-id="bce05-110">Cette fonctionnalité est conçue pour les applications tierces de « fenêtre de terminal » qui existent sur la plateforme ou pour la redirection des activités en mode caractère vers une session « fenêtre de terminal » distante sur un autre ordinateur, voire sur une autre plateforme.</span><span class="sxs-lookup"><span data-stu-id="bce05-110">This functionality is designed for third-party "terminal window" applications to exist on the platform or for redirection of character-mode activities to a remote "terminal window" session on another machine or even on another platform.</span></span>

<span data-ttu-id="bce05-111">Notez que la session de console sous-jacente sera toujours créée pour le compte de l’application demandant le pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="bce05-111">Note that the underlying console session will still be created on behalf of the application requesting the pseudoconsole.</span></span> <span data-ttu-id="bce05-112">Toutes les règles des [sessions de console](consoles.md) s’appliquent toujours, y compris la possibilité pour plusieurs applications en mode caractères client de se connecter à la session.</span><span class="sxs-lookup"><span data-stu-id="bce05-112">All the rules of [console sessions](consoles.md) still apply including the ability for multiple client character-mode applications to connect to the session.</span></span>

<span data-ttu-id="bce05-113">Pour assurer une compatibilité maximale avec le monde existant de la fonctionnalité pseudoterminal, les informations fournies sur le canal pseudoconsole seront toujours encodées au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="bce05-113">To provide maximum compatibility with the existing world of pseudoterminal functionality, the information provided over the pseudoconsole channel will always be encoded in UTF-8.</span></span> <span data-ttu-id="bce05-114">Cela n’affecte pas la page de codes ou l’encodage des applications clientes qui sont attachées.</span><span class="sxs-lookup"><span data-stu-id="bce05-114">This does not affect the codepage or encoding of the client applications that are attached.</span></span> <span data-ttu-id="bce05-115">La traduction se produit à l’intérieur du système pseudoconsole si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="bce05-115">Translation will happen inside the pseudoconsole system as necessary.</span></span>

<span data-ttu-id="bce05-116">Vous trouverez un exemple de mise en route dans [la rubrique Création d’une session Pseudoconsole](creating-a-pseudoconsole-session.md).</span><span class="sxs-lookup"><span data-stu-id="bce05-116">An example for getting started can be found at [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).</span></span>

<span data-ttu-id="bce05-117">Vous trouverez des informations générales supplémentaires sur pseudoconsoles dans le billet de blog d’annonce : [Windows Command-Line : présentation de la console Windows (ConPTY)](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span><span class="sxs-lookup"><span data-stu-id="bce05-117">Some additional background information on pseudoconsoles can be found at the announcement blog post: [Windows Command-Line: Introducing the Windows Pseudo Console (ConPTY)](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span></span>
