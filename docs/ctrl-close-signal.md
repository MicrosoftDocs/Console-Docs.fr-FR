---
title: Signal CTRL + fermer
description: Le système génère un signal CTRL + fermer lorsque l’utilisateur ferme une console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_ctrl\_close\_signal'
- base.ctrl\_close\_signal
- consoles.ctrl\_close\_signal
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a327dd55-3250-40ee-b1c4-6ba3b80984a8
ms.openlocfilehash: d3775bf0b8536fc531905ee6665a1e2c294d0a68
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038227"
---
# <a name="ctrlclose-signal"></a><span data-ttu-id="04454-104">Signal CTRL + fermer</span><span class="sxs-lookup"><span data-stu-id="04454-104">CTRL+CLOSE Signal</span></span>

<span data-ttu-id="04454-105">Le système génère un signal CTRL + fermer lorsque l’utilisateur ferme une console.</span><span class="sxs-lookup"><span data-stu-id="04454-105">The system generates a CTRL+CLOSE signal when the user closes a console.</span></span> <span data-ttu-id="04454-106">Tous les processus attachés à la console reçoivent le signal, donnant à chaque processus la possibilité de le nettoyer avant son arrêt.</span><span class="sxs-lookup"><span data-stu-id="04454-106">All processes attached to the console receive the signal, giving each process an opportunity to clean up before termination.</span></span> <span data-ttu-id="04454-107">Lorsqu’un processus reçoit ce signal, la fonction de gestionnaire peut effectuer l’une des actions suivantes après avoir effectué des opérations de nettoyage :</span><span class="sxs-lookup"><span data-stu-id="04454-107">When a process receives this signal, the handler function can take one of the following actions after performing any cleanup operations:</span></span>

- <span data-ttu-id="04454-108">Appelez [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) pour terminer le processus.</span><span class="sxs-lookup"><span data-stu-id="04454-108">Call [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) to terminate the process.</span></span>
- <span data-ttu-id="04454-109">Retourne **false** .</span><span class="sxs-lookup"><span data-stu-id="04454-109">Return **FALSE** .</span></span> <span data-ttu-id="04454-110">Si aucune des fonctions de gestionnaire inscrites ne retourne la **valeur true** , le gestionnaire par défaut arrête le processus.</span><span class="sxs-lookup"><span data-stu-id="04454-110">If none of the registered handler functions returns **TRUE** , the default handler terminates the process.</span></span>
- <span data-ttu-id="04454-111">Retourne la **valeur true** .</span><span class="sxs-lookup"><span data-stu-id="04454-111">Return **TRUE** .</span></span> <span data-ttu-id="04454-112">Dans ce cas, aucune autre fonction de gestionnaire n’est appelée et le processus se termine.</span><span class="sxs-lookup"><span data-stu-id="04454-112">In this case, no other handler functions are called and the process terminates.</span></span>
