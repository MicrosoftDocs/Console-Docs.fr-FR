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
# <a name="console-code-pages"></a>Pages de code d’une console

Une *page de codes* est un mappage de 256 codes de caractères à des caractères individuels. Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.

Deux pages de codes sont associées à chaque console : une pour l’entrée et une pour la sortie. Une console utilise sa page de codes d’entrée pour convertir l’entrée au clavier en valeur de caractère correspondante. Elle utilise sa page de codes de sortie pour convertir les valeurs de caractères écrites par les différentes fonctions de sortie dans les images affichées dans la fenêtre de la console. Une application peut utiliser les fonctions [**SetConsoleCP**](setconsolecp.md) et [**GetConsoleCP**](getconsolecp.md) pour définir et récupérer les pages de codes d’entrée d’une console, ainsi que les fonctions [**SetConsoleOutputCP**](setconsoleoutputcp.md) et [**GetConsoleOutputCP**](getconsoleoutputcp.md) pour définir et récupérer les pages de codes de sortie.

Les identificateurs des pages de codes disponibles sur l’ordinateur local sont stockés dans le Registre sous la clé suivante : `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

Pour plus d’informations sur l’utilisation des fonctions de Registre pour déterminer les pages de codes disponibles, consultez [**Registry**](/windows/win32/sysinfo/registry).

> [!TIP]
> Il est recommandé pour toutes les applications de ligne de commande nouvelles et mises à jour d’éviter les pages de codes et d’utiliser **[Unicode](/windows/win32/intl/unicode)**. Le texte au format UTF-16 peut être envoyé à la famille *W* d’API de console. Le texte au format UTF-8 peut être envoyé à *une* famille d’API de console après avoir vérifié que la page de codes est d’abord définie sur **[65001 (CP_UTF8)](/windows/win32/intl/code-page-identifiers)** avec les fonctions [**SetConsoleCP**](setconsolecp.md) et [**SetConsoleOutputCP**](setconsoleoutputcp.md) .