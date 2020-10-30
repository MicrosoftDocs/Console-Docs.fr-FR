---
title: Définitions de console Windows et de terminal
description: Fournit les définitions des mots et des expressions couramment utilisés dans cet espace et l’ensemble de documents associés à la console et au système Terminal Server.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, terminal, terminal virtuel, hôte de la console, ligne de commande, sous-système, définitions
ms.prod: console
ms.openlocfilehash: 763421a25d5ecaa2291b68b0370644af152622a9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039590"
---
# <a name="definitions"></a>Définitions

Ce document fournit les définitions de mots et d’expressions spécifiques dans cet espace et sert de référence dans cet ensemble de documents.

## <a name="command-line-applications"></a>Applications en ligne de commande

Les applications en ligne de commande, ou parfois appelées « applications console » et/ou appelées « clients » du sous-système de la console, sont des programmes qui fonctionnent principalement sur un flux de texte ou des informations de caractères. Elles ne contiennent généralement aucun élément d’interface utilisateur propre et délèguent à la fois les rôles de sortie/d’affichage et d’entrée/d’interaction à une application d’hébergement. Les applications en ligne de commande reçoivent un flux de texte sur leur handle d’entrée standard `STDIN` qui représente l’entrée de clavier d’un utilisateur, traite ces informations, puis répond avec un flux de texte sur leur sortie standard `STDOUT` pour l’afficher à l’écran de l’utilisateur. Bien entendu, cela a évolué au fil du temps pour les périphériques d’entrée supplémentaires et les scénarios distants, mais la même philosophie de base reste la même : les clients de ligne de commande opèrent sur du texte et quelqu’un d’autre gère l’affichage/l’entrée.

## <a name="standard-handles"></a>Handles standard

Les handles standard sont une série,, `STDIN` `STDOUT` et `STDERR` , introduite dans le cadre d’un espace de processus au démarrage. Ils représentent un emplacement dans lequel les informations doivent être acceptées et renvoyées en retour (y compris un emplacement spécial pour signaler les erreurs). Pour les applications en ligne de commande, celles-ci doivent toujours exister au démarrage de l’application. Elles sont héritées automatiquement du parent, définies explicitement par le parent, ou créées automatiquement par le système d’exploitation si aucune des deux n’est spécifiée/autorisée. Pour les applications Windows classiques, celles-ci peuvent être vides au démarrage. Toutefois, ils peuvent être hérités implicitement ou explicitement à partir du parent ou alloués, attachés et libérés pendant l’exécution par l’application elle-même.

Les handles standard n’impliquent pas un type spécifique d’appareil attaché. Toutefois, dans le cas d’applications en ligne de commande, l’appareil est le plus souvent un périphérique de console, un fichier (de redirection dans un Shell) ou un canal (à partir d’un shell qui connecte la sortie d’un utilitaire à l’entrée du suivant). Il peut également s’agir d’un socket ou d’un autre type d’appareil.

## <a name="ttypty"></a>TTY/PTY

Sur les plateformes non-Windows, les appareils TTY et PTY représentent respectivement un véritable appareil physique ou un Pseudo-appareil créé par logiciel qui est le même concept qu’une session de console Windows : un canal dans lequel la communication entre une application cliente de ligne de commande et une application d’interactivité de l’hôte du serveur ou un périphérique clavier/écran physique peut échanger des informations textuelles.

## <a name="clients-and-servers"></a>Clients et serveurs

Dans cet espace, nous faisons référence aux « clients » comme des applications qui effectuent le travail de traitement d’informations et d’exécution de commandes. Les applications « serveur » sont celles qui sont responsables de l’interface utilisateur et sont des Workers qui peuvent traduire les entrées et les sorties en formulaires standard pour le compte des clients.

## <a name="console-subsystem"></a>Sous-système de la console

Il s’agit d’un terme de rattrapage qui représente tous les modules affectant les opérations de console et de ligne de commande. Il fait spécifiquement référence à un indicateur qui fait partie de l’en-tête de l’exécutable portable qui spécifie si l’application de démarrage est une application de ligne de commande/console (et doit avoir des handles standard pour démarrer) ou une application Windows (et n’en a pas besoin).

L’hôte de la console, les applications clientes de ligne de commande, le pilote de la console, la surface de l’API de la console, l’infrastructure pseudoconsole, les terminaux, les feuilles de propriétés de configuration, les mécanismes et les stubs à l’intérieur du chargeur de processus et tous les utilitaires liés au fonctionnement de ces types d’applications sont considérés comme appartenant à ce groupe.

## <a name="console-host"></a>Hôte de console

L’hôte de console Windows, ou `conhost.exe` , est à la fois l’application serveur pour toutes les API de console Windows et l’interface utilisateur Windows classique pour travailler avec des applications en ligne de commande. Le contenu complet de ce fichier binaire, à la fois le serveur d’API et l’interface utilisateur, appartenait à Windows `csrss.exe` , à un processus système critique et a été divergent à des fins de sécurité et d’isolation. À l’avenir, `conhost.exe` continuera à être responsable de la traduction et de la maintenance des appels d’API, mais les composants de l’interface utilisateur sont destinés à être délégués via un pseudoconsole à un terminal.

## <a name="pseudoconsole"></a>Pseudoconsole

Il s’agit de la simulation Windows d’un pseudoterminal ou « PTY » à partir d’autres plateformes. Il tente de faire correspondre la philosophie d’interface générale de PTYs, en fournissant un canal bidirectionnel simple de communication basée sur le texte, mais il le complète sur Windows avec une couche de compatibilité importante pour traduire la largeur des applications Windows écrites avant cette philosophie de conception à partir de la surface de l’API de la console classique dans le format de communication de la chaîne de texte simple. Les terminaux peuvent utiliser le pseudoconsole pour prendre possession des éléments de l’interface utilisateur en dehors de l’hôte de la console, `conhost.exe` , tout en le laissant responsable des efforts de maintenance, de traduction et de compatibilité des API.

## <a name="terminal"></a>Terminal

Un terminal est le module interface utilisateur et interaction pour une application en ligne de commande. Aujourd’hui, il s’agit d’une représentation logicielle de ce qui était historiquement un appareil physique avec un moniteur d’affichage, un clavier et un canal de communication en série bidirectionnel. Il est responsable de la collecte des entrées de l’utilisateur dans diverses formes, de sa traduction et de son encodage, ainsi que de toutes les informations de commande spéciales en un seul flux de texte, et de sa soumission au PTY en vue de sa transmission vers le `STDIN` canal de l’application cliente de ligne de commande. Il est également chargé de recevoir des informations, par le biais du PTY, qui proviennent du canal d’une application cliente `STDOUT` , de décoder toutes les informations spéciales dans la charge utile, de disposer tout le texte et les commandes supplémentaires, et de les présenter sous forme de graphique à l’utilisateur final.
