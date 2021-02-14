---
title: Pages de code d’une console
description: Une page de codes est un mappage de 256 codes de caractères à des caractères individuels. Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_console\_code\_pages'
- base.console\_code\_pages
- consoles.console\_code\_pages
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98d56bb1-83d2-40aa-adac-fc2e8beab337
ms.openlocfilehash: 0ab9152c2be3f7487f43aee2a0a5c19766a433be
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358249"
---
# <a name="console-code-pages"></a><span data-ttu-id="c6fcd-105">Pages de code d’une console</span><span class="sxs-lookup"><span data-stu-id="c6fcd-105">Console Code Pages</span></span>

<span data-ttu-id="c6fcd-106">Une *page de codes* est un mappage de 256 codes de caractères à des caractères individuels.</span><span class="sxs-lookup"><span data-stu-id="c6fcd-106">A *code page* is a mapping of 256 character codes to individual characters.</span></span> <span data-ttu-id="c6fcd-107">Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.</span><span class="sxs-lookup"><span data-stu-id="c6fcd-107">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="c6fcd-108">Deux pages de codes sont associées à chaque console : une pour l’entrée et une pour la sortie.</span><span class="sxs-lookup"><span data-stu-id="c6fcd-108">Associated with each console are two code pages: one for input and one for output.</span></span> <span data-ttu-id="c6fcd-109">Une console utilise sa page de codes d’entrée pour convertir l’entrée au clavier en valeur de caractère correspondante.</span><span class="sxs-lookup"><span data-stu-id="c6fcd-109">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span> <span data-ttu-id="c6fcd-110">Elle utilise sa page de codes de sortie pour convertir les valeurs de caractères écrites par les différentes fonctions de sortie dans les images affichées dans la fenêtre de la console.</span><span class="sxs-lookup"><span data-stu-id="c6fcd-110">It uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span> <span data-ttu-id="c6fcd-111">Une application peut utiliser les fonctions [**SetConsoleCP**](setconsolecp.md) et [**GetConsoleCP**](getconsolecp.md) pour définir et récupérer les pages de codes d’entrée d’une console, ainsi que les fonctions [**SetConsoleOutputCP**](setconsoleoutputcp.md) et [**GetConsoleOutputCP**](getconsoleoutputcp.md) pour définir et récupérer les pages de codes de sortie.</span><span class="sxs-lookup"><span data-stu-id="c6fcd-111">An application can use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions to set and retrieve a console's input code pages and the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions to set and retrieve its output code pages.</span></span>

<span data-ttu-id="c6fcd-112">Les identificateurs des pages de codes disponibles sur l’ordinateur local sont stockés dans le Registre sous la clé suivante : `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`</span><span class="sxs-lookup"><span data-stu-id="c6fcd-112">The identifiers of the code pages available on the local computer are stored in the registry under the following key: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`</span></span>

<span data-ttu-id="c6fcd-113">Pour plus d’informations sur l’utilisation des fonctions de Registre pour déterminer les pages de codes disponibles, consultez [**Registry**](/windows/win32/sysinfo/registry).</span><span class="sxs-lookup"><span data-stu-id="c6fcd-113">For information about using the registry functions to determine the available code pages, see [**Registry**](/windows/win32/sysinfo/registry).</span></span>

> [!TIP]
> <span data-ttu-id="c6fcd-114">Il est recommandé pour toutes les applications de ligne de commande nouvelles et mises à jour d’éviter les pages de codes et d’utiliser **[Unicode](/windows/win32/intl/unicode)**.</span><span class="sxs-lookup"><span data-stu-id="c6fcd-114">It is recommended for all new and updated command-line applications to avoid code pages and use **[Unicode](/windows/win32/intl/unicode)**.</span></span> <span data-ttu-id="c6fcd-115">Le texte au format UTF-16 peut être envoyé à la famille *W* d’API de console.</span><span class="sxs-lookup"><span data-stu-id="c6fcd-115">UTF-16 formatted text can be sent to the *W* family of console APIs.</span></span> <span data-ttu-id="c6fcd-116">Le texte au format UTF-8 peut être envoyé à *une* famille d’API de console après avoir vérifié que la page de codes est d’abord définie sur **[65001 (CP_UTF8)](/windows/win32/intl/code-page-identifiers)** avec les fonctions [**SetConsoleCP**](setconsolecp.md) et [**SetConsoleOutputCP**](setconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="c6fcd-116">UTF-8 formatted text can be sent to the *A* family of console APIs after ensuring the code page is first set to **[65001 (CP_UTF8)](/windows/win32/intl/code-page-identifiers)** with the [**SetConsoleCP**](setconsolecp.md) and [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions.</span></span>