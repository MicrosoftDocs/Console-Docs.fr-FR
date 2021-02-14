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
ms.openlocfilehash: 10ee932ba8c09b8e28092d4289b7da64da749b76
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357829"
---
# <a name="console-aliases"></a>Alias d’une console

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Les alias de console sont utilisés pour mapper les chaînes sources aux chaînes cibles. Par exemple, vous pouvez définir un alias de console qui mappe « test » à « CD \\ a \_ très \_ long \_ path \\ test ». Quand vous tapez « test » sur la ligne de commande, le sous-système de la console développe l’alias et exécute la commande CD spécifiée.

Pour définir un alias de console, utilisez [**Doskey.exe**](/windows-server/administration/windows-commands/doskey) pour créer une macro ou utilisez la fonction [**AddConsoleAlias**](addconsolealias.md) . L'exemple suivant utilise `Doskey.exe` :

**test Doskey = CD \\** **\\ test** <em>de \_ \_ \_ chemin d’accès très long</em>

L’appel suivant à [**AddConsoleAlias**](addconsolealias.md) crée le même alias de console :

``` C
AddConsoleAlias( TEXT("test"),
                 TEXT("cd \\<a_very_long_path>\\test"),
                 TEXT("cmd.exe"));
```

Pour ajouter des paramètres à une macro d’alias de console à l’aide de `Doskey.exe` , utilisez les paramètres de traitement par le `$1` biais de `$9` . Pour plus d’informations sur les codes spéciaux qui peuvent être utilisés dans les définitions de macros Doskey, consultez l’aide de la ligne de commande pour `Doskey.exe` ou [doskey](/previous-versions/windows/it-pro/windows-xp/bb490894(v=technet.10)) sur TechNet.

Toutes les instances d’un fichier exécutable s’exécutant dans la même fenêtre de console partagent tous les alias de console définis. Plusieurs instances du même fichier exécutable s’exécutant dans différentes fenêtres de console ne partagent pas les alias de la console. Les différents fichiers exécutables qui s’exécutent dans la même fenêtre de console ne partagent pas les alias de la console.

Pour récupérer la chaîne cible pour une chaîne source et un fichier exécutable spécifiés, utilisez la fonction [**GetConsoleAlias**](getconsolealias.md) . Pour récupérer tous les alias d’un fichier exécutable spécifié, utilisez la fonction [**GetConsoleAliases**](getconsolealiases.md) . Pour récupérer les noms de tous les alias pour lesquels des alias de console ont été définis, utilisez la fonction [**GetConsoleAliasExes**](getconsolealiasexes.md) .