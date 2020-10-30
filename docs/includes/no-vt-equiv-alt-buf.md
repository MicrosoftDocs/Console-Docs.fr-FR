---
ms.openlocfilehash: ef8a068fe6edd2a7d2013c930c238235326b8c1d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039131"
---
> [!TIP]
> <span data-ttu-id="18e25-101">Cette API n’est pas recommandée, mais elle possède un équivalent de **[terminal virtuel](../console-virtual-terminal-sequences.md)** approximatif dans l’autre séquence de **[mémoire tampon d’écran](../console-virtual-terminal-sequences.md#alternate-screen-buffer)** .</span><span class="sxs-lookup"><span data-stu-id="18e25-101">This API is not recommended but it does have an approximate **[virtual terminal](../console-virtual-terminal-sequences.md)** equivalent in the **[alternate screen buffer](../console-virtual-terminal-sequences.md#alternate-screen-buffer)** sequence.</span></span> <span data-ttu-id="18e25-102">La définition de l' _autre mémoire tampon d’écran_ peut fournir à une application un espace isolé distinct pour le dessin au cours de son exécution de session tout en conservant le contenu affiché par le demandeur de l’application.</span><span class="sxs-lookup"><span data-stu-id="18e25-102">Setting the _alternate screen buffer_ can provide an application with a separate, isolated space for drawing over the course of its session runtime while preserving the content that was displayed by the application's invoker.</span></span> <span data-ttu-id="18e25-103">Cela maintient les informations de dessin pour une restauration simple lors de la sortie du processus.</span><span class="sxs-lookup"><span data-stu-id="18e25-103">This maintains that drawing information for simple restoration on process exit.</span></span>
