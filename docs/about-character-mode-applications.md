---
title: À propos des consoles
description: Les consoles fournissent une prise en charge de haut niveau pour les applications en mode caractères simples qui interagissent avec l’utilisateur à l’aide des fonctions qui lisent les entrées standard et écrivent dans une sortie standard ou une erreur standard.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: 0a738c72ec45a68817fae6dbfa9d6b3e45beb53e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059393"
---
# <a name="about-character-mode-applications"></a>À propos des applications en mode caractère

Applications en mode caractère (ou « ligne de commande ») :

1. Éventuellement Lire des données à partir d’une entrée standard (stdin)
2. Faire « travail »
3. Éventuellement Écrire des données dans une sortie standard (stdout) ou une erreur standard (stderr)

Les applications en mode caractère communiquent avec l’utilisateur final par le biais d’une application « console » (ou « terminal »). Une console convertit l’entrée utilisateur à partir du clavier, de la souris, de l’écran tactile, du stylet, etc., et l’envoie au stdin d’une application en mode caractère. Une console peut également afficher une sortie de texte d’une application en mode caractère sur l’écran de l’utilisateur.

Dans Windows, la console est intégrée et fournit une API riche par le biais de laquelle les applications en mode caractère peuvent interagir avec l’utilisateur.

- [Consoles](consoles.md)
- [Méthodes d’entrée et de sortie](input-and-output-methods.md)
- [Pages de codes de la console](console-code-pages.md)
- [Gestionnaires de contrôle de console](console-control-handlers.md)
- [Alias de console](console-aliases.md)
- [Sécurité de la mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md)
- [Problèmes liés aux applications console](console-application-issues.md)

 

 




