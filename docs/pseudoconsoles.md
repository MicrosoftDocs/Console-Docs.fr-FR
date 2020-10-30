---
title: Pseudoconsoles – Bureau Windows
description: Un pseudoconsole est un concept utilisé pour fournir l’aspect d’hébergement ou de maintenance d’une application en mode caractère.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API console, conpty, pseudoconsole
ms.openlocfilehash: 2b2d28065ec4f0e4121decb906e76b34ac1871fc
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039477"
---
# <a name="pseudoconsoles"></a>Pseudoconsoles

Un *pseudoconsole* est un type d’appareil qui permet aux applications de devenir l’hôte des applications en mode caractère.

Contrairement à une session de console classique, le système d’exploitation crée une fenêtre d’hébergement pour le compte de l’application en mode caractères pour gérer la sortie graphique et l’entrée utilisateur.

Avec un pseudoconsole, la fenêtre d’hébergement n’est pas créée. L’application qui rend le pseudoconsole doit être responsable de l’affichage de la sortie graphique et de la collecte de l’entrée d’utilisateur. Les informations peuvent également être relayées plus en détail vers une autre application responsable de ces activités à un point ultérieur de la chaîne.

Cette fonctionnalité est conçue pour les applications tierces de « fenêtre de terminal » qui existent sur la plateforme ou pour la redirection des activités en mode caractère vers une session « fenêtre de terminal » distante sur un autre ordinateur, voire sur une autre plateforme.

Notez que la session de console sous-jacente sera toujours créée pour le compte de l’application demandant le pseudoconsole. Toutes les règles des [sessions de console](consoles.md) s’appliquent toujours, y compris la possibilité pour plusieurs applications en mode caractères client de se connecter à la session.

Pour assurer une compatibilité maximale avec le monde existant de la fonctionnalité pseudoterminal, les informations fournies sur le canal pseudoconsole seront toujours encodées au format UTF-8. Cela n’affecte pas la page de codes ou l’encodage des applications clientes qui sont attachées. La traduction se produit à l’intérieur du système pseudoconsole si nécessaire.

Vous trouverez un exemple de mise en route dans [la rubrique Création d’une session Pseudoconsole](creating-a-pseudoconsole-session.md).

Vous trouverez des informations générales supplémentaires sur pseudoconsoles dans le billet de blog d’annonce : [Windows Command-Line : présentation de la console Windows (ConPTY)](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).
