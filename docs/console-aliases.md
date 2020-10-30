---
title: Alias d’une console
description: Décrit les alias de console et la façon dont ils sont utilisés pour mapper les chaînes sources aux chaînes cibles.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- base.console\_aliases
- consoles.console\_aliases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8169708b-83da-47ef-94be-eca3ca7d0a5b
ms.openlocfilehash: b31ae10faf2c8500b0100d1a4cbc126014bf8790
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037277"
---
# <a name="console-aliases"></a><span data-ttu-id="bbe63-104">Alias d’une console</span><span class="sxs-lookup"><span data-stu-id="bbe63-104">Console Aliases</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="bbe63-105">Les alias de console sont utilisés pour mapper les chaînes sources aux chaînes cibles.</span><span class="sxs-lookup"><span data-stu-id="bbe63-105">Console aliases are used to map source strings to target strings.</span></span> <span data-ttu-id="bbe63-106">Par exemple, vous pouvez définir un alias de console qui mappe « test » à « CD \\ a \_ très \_ long \_ path \\ test ».</span><span class="sxs-lookup"><span data-stu-id="bbe63-106">For example, you can define a console alias that maps "test" to "cd \\a\_very\_long\_path\\test".</span></span> <span data-ttu-id="bbe63-107">Quand vous tapez « test » sur la ligne de commande, le sous-système de la console développe l’alias et exécute la commande CD spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bbe63-107">When you type "test" at the command line, the console subsystem expands the alias and executes the specified cd command.</span></span>

<span data-ttu-id="bbe63-108">Pour définir un alias de console, utilisez [**Doskey.exe**](https://docs.microsoft.com/windows-server/administration/windows-commands/doskey) pour créer une macro ou utilisez la fonction [**AddConsoleAlias**](addconsolealias.md) .</span><span class="sxs-lookup"><span data-stu-id="bbe63-108">To define a console alias, use [**Doskey.exe**](https://docs.microsoft.com/windows-server/administration/windows-commands/doskey) to create a macro, or use the [**AddConsoleAlias**](addconsolealias.md) function.</span></span> <span data-ttu-id="bbe63-109">L'exemple suivant utilise `Doskey.exe` :</span><span class="sxs-lookup"><span data-stu-id="bbe63-109">The following example uses `Doskey.exe`:</span></span>

<span data-ttu-id="bbe63-110">**test Doskey = CD \\** **\\ test** <em>de \_ \_ \_ chemin d’accès très long</em></span><span class="sxs-lookup"><span data-stu-id="bbe63-110">**doskey test=cd \\**<em>a\_very\_long\_path</em>**\\test**</span></span>

<span data-ttu-id="bbe63-111">L’appel suivant à [**AddConsoleAlias**](addconsolealias.md) crée le même alias de console :</span><span class="sxs-lookup"><span data-stu-id="bbe63-111">The following call to [**AddConsoleAlias**](addconsolealias.md) creates the same console alias:</span></span>

``` C
AddConsoleAlias( TEXT("test"),
                 TEXT("cd \\<a_very_long_path>\\test"),
                 TEXT("cmd.exe"));
```

<span data-ttu-id="bbe63-112">Pour ajouter des paramètres à une macro d’alias de console à l’aide de `Doskey.exe` , utilisez les paramètres de traitement par le `$1` biais de `$9` .</span><span class="sxs-lookup"><span data-stu-id="bbe63-112">To add parameters to a console alias macro using `Doskey.exe`, use the batch parameters `$1` through `$9`.</span></span> <span data-ttu-id="bbe63-113">Pour plus d’informations sur les codes spéciaux qui peuvent être utilisés dans les définitions de macros Doskey, consultez l’aide de la ligne de commande pour `Doskey.exe` ou [doskey](https://go.microsoft.com/fwlink/p/?linkid=196265) sur TechNet.</span><span class="sxs-lookup"><span data-stu-id="bbe63-113">For more information on the special codes that can be used in Doskey macro definitions, see the command-line help for `Doskey.exe` or [Doskey](https://go.microsoft.com/fwlink/p/?linkid=196265) on TechNet.</span></span>

<span data-ttu-id="bbe63-114">Toutes les instances d’un fichier exécutable s’exécutant dans la même fenêtre de console partagent tous les alias de console définis.</span><span class="sxs-lookup"><span data-stu-id="bbe63-114">All instances of an executable file running in the same console window share any defined console aliases.</span></span> <span data-ttu-id="bbe63-115">Plusieurs instances du même fichier exécutable s’exécutant dans différentes fenêtres de console ne partagent pas les alias de la console.</span><span class="sxs-lookup"><span data-stu-id="bbe63-115">Multiple instances of the same executable file running in different console windows do not share console aliases.</span></span> <span data-ttu-id="bbe63-116">Les différents fichiers exécutables qui s’exécutent dans la même fenêtre de console ne partagent pas les alias de la console.</span><span class="sxs-lookup"><span data-stu-id="bbe63-116">Different executable files running in the same console window do not share console aliases.</span></span>

<span data-ttu-id="bbe63-117">Pour récupérer la chaîne cible pour une chaîne source et un fichier exécutable spécifiés, utilisez la fonction [**GetConsoleAlias**](getconsolealias.md) .</span><span class="sxs-lookup"><span data-stu-id="bbe63-117">To retrieve the target string for a specified source string and executable file, use the [**GetConsoleAlias**](getconsolealias.md) function.</span></span> <span data-ttu-id="bbe63-118">Pour récupérer tous les alias d’un fichier exécutable spécifié, utilisez la fonction [**GetConsoleAliases**](getconsolealiases.md) .</span><span class="sxs-lookup"><span data-stu-id="bbe63-118">To retrieve all aliases for a specified executable file, use the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span> <span data-ttu-id="bbe63-119">Pour récupérer les noms de tous les alias pour lesquels des alias de console ont été définis, utilisez la fonction [**GetConsoleAliasExes**](getconsolealiasexes.md) .</span><span class="sxs-lookup"><span data-stu-id="bbe63-119">To retrieve the names of all aliases for which console aliases have been defined, use the [**GetConsoleAliasExes**](getconsolealiasexes.md) function.</span></span>
