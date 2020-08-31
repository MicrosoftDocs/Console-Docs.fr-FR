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
# <a name="console-code-pages"></a>Pages de codes de la console


Une *page de codes* est un mappage de 256 codes de caractères à des caractères individuels. Les différentes pages de code incluent des caractères spéciaux différents, généralement personnalisés pour une langue ou un groupe de langues.

Deux pages de codes sont associées à chaque console : une pour l’entrée et une pour la sortie. Une console utilise sa page de codes d’entrée pour convertir l’entrée au clavier en valeur de caractère correspondante. Elle utilise sa page de codes de sortie pour convertir les valeurs de caractères écrites par les différentes fonctions de sortie dans les images affichées dans la fenêtre de la console. Une application peut utiliser les fonctions [**SetConsoleCP**](setconsolecp.md) et [**GetConsoleCP**](getconsolecp.md) pour définir et récupérer les pages de codes d’entrée d’une console, ainsi que les fonctions [**SetConsoleOutputCP**](setconsoleoutputcp.md) et [**GetConsoleOutputCP**](getconsoleoutputcp.md) pour définir et récupérer les pages de codes de sortie.

Les identificateurs des pages de codes disponibles sur l’ordinateur local sont stockés dans le Registre sous la clé suivante.

**HKEY \_ local \_ machine \\ System \\ CurrentControlSet \\ contrôler \\ la \\ page de codes nls**

Pour plus d’informations sur l’utilisation des fonctions de Registre pour déterminer les pages de codes disponibles, consultez [**Registry**](https://msdn.microsoft.com/library/windows/desktop/ms724871).

 

 




