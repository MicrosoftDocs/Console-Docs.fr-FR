---
title: À propos des consoles
description: Les consoles fournissent une prise en charge de haut niveau pour les applications en mode caractères simples qui interagissent avec l’utilisateur à l’aide des fonctions qui lisent les entrées standard et écrivent dans une sortie standard ou une erreur standard.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: e20fa54434b4121abd3f77ee530945bf9aa590f2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037527"
---
# <a name="about-character-mode-applications"></a>À propos des applications en mode caractère

Applications en mode caractère (ou « ligne de commande ») :

1. \[Éventuellement \] , lire des données à partir d’une entrée standard (stdin)
2. Faire « travail »
3. \[Vous pouvez \] écrire des données dans une sortie standard (stdout) ou une erreur standard (stderr).

Les applications en mode caractère communiquent avec l’utilisateur final par le biais d’une application « console » (ou « terminal »). Une console convertit l’entrée utilisateur à partir du clavier, de la souris, de l’écran tactile, du stylet, etc., et l’envoie au stdin d’une application en mode caractère. Une console peut également afficher une sortie de texte d’une application en mode caractère sur l’écran de l’utilisateur.

Dans Windows, la console est intégrée et fournit une API riche par le biais de laquelle les applications en mode caractère peuvent interagir avec l’utilisateur. Toutefois, dans l’ère récente, l’équipe de la console encourage toutes les applications en mode caractère à être développées avec des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) sur les appels d’API classiques pour une compatibilité maximale entre Windows et d’autres systèmes d’exploitation. Pour plus d’informations sur cette transition et les interruptions de service impliquées, consultez notre discussion sur les [API classiques et les séquences de terminaux virtuels](classic-vs-vt.md).

- [Consoles](consoles.md)
- [Méthodes d’entrée et de sortie](input-and-output-methods.md)
- [Pages de code d’une console](console-code-pages.md)
- [Gestionnaires de contrôle d’une console](console-control-handlers.md)
- [Alias d’une console](console-aliases.md)
- [Sécurité de la mémoire tampon et droits d’accès d’une console](console-buffer-security-and-access-rights.md)
- [Problèmes des applications d’une console](console-application-issues.md)
