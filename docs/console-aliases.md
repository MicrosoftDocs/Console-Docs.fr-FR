---
title: Alias de console
description: Décrit les alias de console et la façon dont ils sont utilisés pour mapper les chaînes sources aux chaînes cibles.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- base.console\_aliases
- consoles.console\_aliases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8169708b-83da-47ef-94be-eca3ca7d0a5b
ms.openlocfilehash: bce57b152262da06b1950eb3566ca8b67d0bb580
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059356"
---
# <a name="console-aliases"></a>Alias de console


Les alias de console sont utilisés pour mapper les chaînes sources aux chaînes cibles. Par exemple, vous pouvez définir un alias de console qui mappe « test » à « CD \\ a \_ très \_ long \_ path \\ test ». Quand vous tapez « test » sur la ligne de commande, le sous-système de la console développe l’alias et exécute la commande CD spécifiée.

Pour définir un alias de console, utilisez Doskey.exe pour créer une macro ou utilisez la fonction [**AddConsoleAlias**](addconsolealias.md) . L’exemple suivant utilise Doskey.exe :

**test Doskey = CD \\ ** ** \\ test** <em>de \_ \_ \_ chemin d’accès très long</em>

L’appel suivant à [**AddConsoleAlias**](addconsolealias.md) crée le même alias de console :

``` syntax
AddConsoleAlias( TEXT("test"), 
                 TEXT("cd \\<a_very_long_path>\\test"), 
                 TEXT("cmd.exe"));
```

Pour ajouter des paramètres à une macro alias de la console à l’aide de Doskey.exe, utilisez les paramètres de lot $1 à $9. Pour plus d’informations sur les codes spéciaux qui peuvent être utilisés dans les définitions de macros Doskey, consultez l’aide de la ligne de commande pour Doskey.exe ou [doskey](https://go.microsoft.com/fwlink/p/?linkid=196265) sur TechNet.

Toutes les instances d’un fichier exécutable s’exécutant dans la même fenêtre de console partagent tous les alias de console définis. Plusieurs instances du même fichier exécutable s’exécutant dans différentes fenêtres de console ne partagent pas les alias de la console. Les différents fichiers exécutables qui s’exécutent dans la même fenêtre de console ne partagent pas les alias de la console.

Pour récupérer la chaîne cible pour une chaîne source et un fichier exécutable spécifiés, utilisez la fonction [**GetConsoleAlias**](getconsolealias.md) . Pour récupérer tous les alias d’un fichier exécutable spécifié, utilisez la fonction [**GetConsoleAliases**](getconsolealiases.md) . Pour récupérer les noms de tous les alias pour lesquels des alias de console ont été définis, utilisez la fonction [**GetConsoleAliasExes**](getconsolealiasexes.md) .

 

 




