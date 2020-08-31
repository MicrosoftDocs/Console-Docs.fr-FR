---
title: Pages de codes de la console
description: Une page de codes est un mappage de 256 codes de caractères à des caractères individuels. Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_console\_code\_pages'
- base.console\_code\_pages
- consoles.console\_code\_pages
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98d56bb1-83d2-40aa-adac-fc2e8beab337
ms.openlocfilehash: cacc4cb1d88a7d2aa01c35e0f0d94b44c393d28c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059341"
---
# <a name="console-code-pages"></a><span data-ttu-id="9644c-105">Pages de codes de la console</span><span class="sxs-lookup"><span data-stu-id="9644c-105">Console Code Pages</span></span>


<span data-ttu-id="9644c-106">Une *page de codes* est un mappage de 256 codes de caractères à des caractères individuels.</span><span class="sxs-lookup"><span data-stu-id="9644c-106">A *code page* is a mapping of 256 character codes to individual characters.</span></span> <span data-ttu-id="9644c-107">Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.</span><span class="sxs-lookup"><span data-stu-id="9644c-107">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="9644c-108">Deux pages de codes sont associées à chaque console : une pour l’entrée et une pour la sortie.</span><span class="sxs-lookup"><span data-stu-id="9644c-108">Associated with each console are two code pages: one for input and one for output.</span></span> <span data-ttu-id="9644c-109">Une console utilise sa page de codes d’entrée pour convertir l’entrée au clavier en valeur de caractère correspondante.</span><span class="sxs-lookup"><span data-stu-id="9644c-109">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span> <span data-ttu-id="9644c-110">Elle utilise sa page de codes de sortie pour convertir les valeurs de caractères écrites par les différentes fonctions de sortie dans les images affichées dans la fenêtre de la console.</span><span class="sxs-lookup"><span data-stu-id="9644c-110">It uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span> <span data-ttu-id="9644c-111">Une application peut utiliser les fonctions [**SetConsoleCP**](setconsolecp.md) et [**GetConsoleCP**](getconsolecp.md) pour définir et récupérer les pages de codes d’entrée d’une console, ainsi que les fonctions [**SetConsoleOutputCP**](setconsoleoutputcp.md) et [**GetConsoleOutputCP**](getconsoleoutputcp.md) pour définir et récupérer les pages de codes de sortie.</span><span class="sxs-lookup"><span data-stu-id="9644c-111">An application can use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions to set and retrieve a console's input code pages and the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions to set and retrieve its output code pages.</span></span>

<span data-ttu-id="9644c-112">Les identificateurs des pages de codes disponibles sur l’ordinateur local sont stockés dans le Registre sous la clé suivante.</span><span class="sxs-lookup"><span data-stu-id="9644c-112">The identifiers of the code pages available on the local computer are stored in the registry under the following key.</span></span>

<span data-ttu-id="9644c-113">**HKEY \_ local \_ machine \\ System \\ CurrentControlSet \\ contrôler \\ la \\ page de codes nls**</span><span class="sxs-lookup"><span data-stu-id="9644c-113">**HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Nls\\CodePage**</span></span>

<span data-ttu-id="9644c-114">Pour plus d’informations sur l’utilisation des fonctions de Registre pour déterminer les pages de codes disponibles, consultez [**Registry**](https://msdn.microsoft.com/library/windows/desktop/ms724871).</span><span class="sxs-lookup"><span data-stu-id="9644c-114">For information about using the registry functions to determine the available code pages, see [**Registry**](https://msdn.microsoft.com/library/windows/desktop/ms724871).</span></span>

 

 




