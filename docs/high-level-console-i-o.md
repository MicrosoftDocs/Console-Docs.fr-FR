---
title: E/s de console de haut niveau
description: Les fonctions d’e/s de haut niveau offrent un moyen simple de lire un flux de caractères à partir de l’entrée de la console ou d’écrire un flux de caractères dans la sortie de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_high\_level\_console\_i\_o'
- base.high\_level\_console\_i\_o
- consoles.high\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6d191fee-87bb-4659-8056-910149e591f7
ms.openlocfilehash: 2209259f604bb8653bca6ab38ca763b63f65713f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059076"
---
# <a name="high-level-console-io"></a><span data-ttu-id="0da6d-104">E/s de console de haut niveau</span><span class="sxs-lookup"><span data-stu-id="0da6d-104">High-Level Console I/O</span></span>


<span data-ttu-id="0da6d-105">Les fonctions d’e/s de haut niveau offrent un moyen simple de lire un flux de caractères à partir de l’entrée de la console ou d’écrire un flux de caractères dans la sortie de la console.</span><span class="sxs-lookup"><span data-stu-id="0da6d-105">The high-level I/O functions provide a simple way to read a stream of characters from console input or to write a stream of characters to console output.</span></span> <span data-ttu-id="0da6d-106">Une opération de lecture de haut niveau obtient des caractères d’entrée à partir de la mémoire tampon d’entrée d’une console et les stocke dans une mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0da6d-106">A high-level read operation gets input characters from a console's input buffer and stores them in a specified buffer.</span></span> <span data-ttu-id="0da6d-107">Une opération d’écriture de haut niveau prend les caractères d’une mémoire tampon spécifiée et les écrit dans une mémoire tampon d’écran à l’emplacement actuel du curseur, en avançant le curseur à mesure que chaque caractère est écrit.</span><span class="sxs-lookup"><span data-stu-id="0da6d-107">A high-level write operation takes characters from a specified buffer and writes them to a screen buffer at the current cursor location, advancing the cursor as each character is written.</span></span>

<span data-ttu-id="0da6d-108">Les e/s de haut niveau vous permettent de choisir entre les fonctions [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) et les fonctions [**ReadConsole**](readconsole.md) et [**WriteConsole**](writeconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="0da6d-108">High-level I/O gives you a choice between the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) functions and the [**ReadConsole**](readconsole.md) and [**WriteConsole**](writeconsole.md) functions.</span></span> <span data-ttu-id="0da6d-109">Ils sont identiques, à l’exception de deux différences importantes.</span><span class="sxs-lookup"><span data-stu-id="0da6d-109">They are identical, except for two important differences.</span></span> <span data-ttu-id="0da6d-110">Les fonctions de console prennent en charge l’utilisation de caractères Unicode ou du jeu de caractères ANSI. les fonctions d’e/s de fichier ne prennent pas en charge Unicode.</span><span class="sxs-lookup"><span data-stu-id="0da6d-110">The console functions support the use of either Unicode characters or the ANSI character set; the file I/O functions do not support Unicode.</span></span> <span data-ttu-id="0da6d-111">En outre, les fonctions d’e/s de fichier peuvent être utilisées pour accéder aux fichiers, aux canaux et aux périphériques de communication série. les fonctions de console peuvent uniquement être utilisées avec des handles de console.</span><span class="sxs-lookup"><span data-stu-id="0da6d-111">Also, the file I/O functions can be used to access files, pipes, and serial communications devices; the console functions can only be used with console handles.</span></span> <span data-ttu-id="0da6d-112">Cette distinction est importante si une application s’appuie sur des handles standard qui ont peut-être été redirigés.</span><span class="sxs-lookup"><span data-stu-id="0da6d-112">This distinction is important if an application relies on standard handles that may have been redirected.</span></span>

<span data-ttu-id="0da6d-113">Lors de l’utilisation d’un ensemble de fonctions de haut niveau, une application peut contrôler les couleurs de texte et d’arrière-plan utilisées pour afficher les caractères écrits par la suite dans une mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="0da6d-113">When using either set of high-level functions, an application can control the text and background colors used to display characters subsequently written to a screen buffer.</span></span> <span data-ttu-id="0da6d-114">Une application peut également utiliser les modes de console qui affectent les e/s de console de haut niveau pour activer ou désactiver les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="0da6d-114">An application can also use the console modes that affect high-level console I/O to enable or disable the following properties:</span></span>

- <span data-ttu-id="0da6d-115">Écho de l’entrée au clavier vers la mémoire tampon d’écran active</span><span class="sxs-lookup"><span data-stu-id="0da6d-115">Echoing of keyboard input to the active screen buffer</span></span>
- <span data-ttu-id="0da6d-116">Entrée de ligne, dans laquelle une opération de lecture n’est pas retournée tant que la touche entrée n’est pas enfoncée</span><span class="sxs-lookup"><span data-stu-id="0da6d-116">Line input, in which a read operation does not return until the ENTER key is pressed</span></span>
- <span data-ttu-id="0da6d-117">Traitement automatique de l’entrée au clavier pour gérer les retours chariot, CTRL + C et d’autres détails d’entrée</span><span class="sxs-lookup"><span data-stu-id="0da6d-117">Automatic processing of keyboard input to handle carriage returns, CTRL+C, and other input details</span></span>
- <span data-ttu-id="0da6d-118">Traitement automatique de la sortie pour gérer le retour à la ligne, les retours chariot, les retours à la ligne et d’autres détails de sortie</span><span class="sxs-lookup"><span data-stu-id="0da6d-118">Automatic processing of output to handle line wrapping, carriage returns, backspaces, and other output details</span></span>

<span data-ttu-id="0da6d-119">Pour plus d'informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="0da6d-119">For more information, see the following topics:</span></span>

- [<span data-ttu-id="0da6d-120">Modes de la console</span><span class="sxs-lookup"><span data-stu-id="0da6d-120">Console Modes</span></span>](console-modes.md)
- [<span data-ttu-id="0da6d-121">Modes de console de haut niveau</span><span class="sxs-lookup"><span data-stu-id="0da6d-121">High-Level Console Modes</span></span>](high-level-console-modes.md)
- [<span data-ttu-id="0da6d-122">Fonctions d’entrée et de sortie de la console de haut niveau</span><span class="sxs-lookup"><span data-stu-id="0da6d-122">High-Level Console Input and Output Functions</span></span>](high-level-console-input-and-output-functions.md)

 

 




