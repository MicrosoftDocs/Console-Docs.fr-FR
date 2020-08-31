---
title: E/s de console de bas niveau
description: Les fonctions d’e/s de la console de bas niveau étendent le contrôle d’une application sur les e/s de la console en permettant un accès direct aux mémoires tampons d’entrée et d’écran d’une console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_low\_level\_console\_i\_o'
- base.low\_level\_console\_i\_o
- consoles.low\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c874aff4-6129-4dbc-8949-24d46382d81c
ms.openlocfilehash: b548a188189b597a270faac1cfbc83a2af699fab
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059472"
---
# <a name="low-level-console-io"></a><span data-ttu-id="20c81-104">E/s de console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="20c81-104">Low-Level Console I/O</span></span>


<span data-ttu-id="20c81-105">Les fonctions d’e/s de la console de bas niveau étendent le contrôle d’une application sur les e/s de la console en permettant un accès direct aux mémoires tampons d’entrée et d’écran d’une console.</span><span class="sxs-lookup"><span data-stu-id="20c81-105">The low-level console I/O functions expand an application's control over console I/O by enabling direct access to a console's input and screen buffers.</span></span> <span data-ttu-id="20c81-106">Ces fonctions permettent à une application d’effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="20c81-106">These functions enable an application to perform the following tasks:</span></span>

- <span data-ttu-id="20c81-107">Recevoir une entrée à propos des événements de redimensionnement de la souris et de la mémoire tampon</span><span class="sxs-lookup"><span data-stu-id="20c81-107">Receive input about mouse and buffer-resizing events</span></span>
- <span data-ttu-id="20c81-108">Recevoir des informations étendues sur les événements d’entrée au clavier</span><span class="sxs-lookup"><span data-stu-id="20c81-108">Receive extended information about keyboard input events</span></span>
- <span data-ttu-id="20c81-109">Écrire des enregistrements d’entrée dans la mémoire tampon d’entrée</span><span class="sxs-lookup"><span data-stu-id="20c81-109">Write input records to the input buffer</span></span>
- <span data-ttu-id="20c81-110">Lire les enregistrements d’entrée sans les supprimer de la mémoire tampon d’entrée</span><span class="sxs-lookup"><span data-stu-id="20c81-110">Read input records without removing them from the input buffer</span></span>
- <span data-ttu-id="20c81-111">Déterminer le nombre d’événements en attente dans la mémoire tampon d’entrée</span><span class="sxs-lookup"><span data-stu-id="20c81-111">Determine the number of pending events in the input buffer</span></span>
- <span data-ttu-id="20c81-112">Vider la mémoire tampon d’entrée</span><span class="sxs-lookup"><span data-stu-id="20c81-112">Flush the input buffer</span></span>
- <span data-ttu-id="20c81-113">Lire et écrire des chaînes de caractères Unicode ou ANSI à un emplacement spécifié dans une mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="20c81-113">Read and write strings of Unicode or ANSI characters at a specified location in a screen buffer</span></span>
- <span data-ttu-id="20c81-114">Lire et écrire des chaînes de texte et des attributs de couleur d’arrière-plan à l’emplacement spécifié dans la mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="20c81-114">Read and write strings of text and background color attributes at a specified screen buffer location</span></span>
- <span data-ttu-id="20c81-115">Lire et écrire des blocs rectangulaires de données de caractère et de couleur à un emplacement de mémoire tampon d’écran spécifié</span><span class="sxs-lookup"><span data-stu-id="20c81-115">Read and write rectangular blocks of character and color data at a specified screen buffer location</span></span>
- <span data-ttu-id="20c81-116">Écrire un caractère Unicode ou ANSI unique, ou une combinaison d’attributs de couleur de texte et d’arrière-plan, à un nombre spécifié de cellules consécutives en commençant à l’emplacement de mémoire tampon d’écran spécifié</span><span class="sxs-lookup"><span data-stu-id="20c81-116">Write a single Unicode or ANSI character, or a text and background color attribute combination, to a specified number of consecutive cells beginning at a specified screen buffer location</span></span>

<span data-ttu-id="20c81-117">Pour plus d'informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="20c81-117">For more information, see the following topics:</span></span>

- [<span data-ttu-id="20c81-118">Modes de la console</span><span class="sxs-lookup"><span data-stu-id="20c81-118">Console Modes</span></span>](console-modes.md)
- [<span data-ttu-id="20c81-119">Modes de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="20c81-119">Low-Level Console Modes</span></span>](low-level-console-modes.md)
- [<span data-ttu-id="20c81-120">Fonctions d’entrée de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="20c81-120">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)
- [<span data-ttu-id="20c81-121">Fonctions de sortie de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="20c81-121">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

 

 




