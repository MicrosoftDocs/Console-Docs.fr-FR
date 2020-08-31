---
title: Fonctions d’entrée de la console de bas niveau
description: Une mémoire tampon de fonctions d’entrée de console de bas niveau contient des enregistrements d’entrée qui peuvent inclure des informations sur le clavier, la souris, le redimensionnement de mémoire tampon, le redimensionnement, le focus et les événements de menu.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_low\_level\_console\_input\_functions'
- base.low\_level\_console\_input\_functions
- consoles.low\_level\_console\_input\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 41488614-ca7c-4207-b706-f7776423c7ba
ms.openlocfilehash: 9e9e576b244e978dad1dd2018a194e7a05fbce85
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059285"
---
# <a name="low-level-console-input-functions"></a>Fonctions d’entrée de la console de bas niveau


Une mémoire tampon de fonctions d’entrée de console de bas niveau contient des enregistrements d’entrée qui peuvent inclure des informations sur le clavier, la souris, le redimensionnement de mémoire tampon, le redimensionnement, le focus et les événements de menu. Les fonctions de bas niveau fournissent un accès direct à la mémoire tampon d’entrée, contrairement aux fonctions de haut niveau qui filtrent et traitent les données de la mémoire tampon d’entrée, en ignorant toutes les entrées à l’exception du clavier.

Il existe cinq fonctions de bas niveau pour accéder à la mémoire tampon d’entrée d’une console :

- [**ReadConsoleInput**](readconsoleinput.md)
- [**PeekConsoleInput**](peekconsoleinput.md)
- [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)
- [**WriteConsoleInput**](writeconsoleinput.md)
- [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

Les fonctions [**ReadConsoleInput**](readconsoleinput.md), [**PeekConsoleInput**](peekconsoleinput.md)et [**WriteConsoleInput**](writeconsoleinput.md) utilisent la structure [**d' \_ enregistrement d’entrée**](input-record-str.md) pour lire ou écrire dans une mémoire tampon d’entrée.

Voici les descriptions des fonctions d’entrée de la console de bas niveau.


| Fonction                                                               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [**ReadConsoleInput**](readconsoleinput.md)                           | Lit et supprime les enregistrements d’entrée d’une mémoire tampon d’entrée. La fonction ne retourne pas de valeur tant qu’au moins un enregistrement n’est pas disponible pour être lu. Tous les enregistrements disponibles sont ensuite transférés vers la mémoire tampon du processus appelant jusqu’à ce qu’aucun autre enregistrement soit disponible ou que le nombre spécifié d’enregistrements ait été lu. Les enregistrements non lus restent dans la mémoire tampon d’entrée pour l’opération de lecture suivante. La fonction indique le nombre total d’enregistrements qui ont été lus. Pour obtenir un exemple qui utilise [**ReadConsoleInput**](readconsoleinput.md), consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md). |
| [**PeekConsoleInput**](peekconsoleinput.md)                           | Lectures sans supprimer les enregistrements d’entrée en attente dans une mémoire tampon d’entrée. Tous les enregistrements disponibles jusqu’au nombre spécifié sont copiés dans la mémoire tampon du processus appelant. Si aucun enregistrement n’est disponible, la fonction est immédiatement retournée. La fonction indique le nombre total d’enregistrements qui ont été lus.                                                                                                                                                                                                                                                                                              |
| [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) | Détermine le nombre d’enregistrements d’entrée non lus dans une mémoire tampon d’entrée.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [**WriteConsoleInput**](writeconsoleinput.md)                         | Place les enregistrements d’entrée dans la mémoire tampon d’entrée derrière les enregistrements en attente dans la mémoire tampon. Le tampon d’entrée augmente de manière dynamique, si nécessaire, pour conserver autant d’enregistrements que le nombre écrit. Pour utiliser cette fonction, le handle de mémoire tampon d’entrée spécifié doit disposer du \_ droit d’accès en lecture générique.                                                                                                                                                                                                                                                                                                                           |
| [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)             | Ignore tous les événements non lus dans la mémoire tampon d’entrée. Pour utiliser cette fonction, le handle de mémoire tampon d’entrée spécifié doit disposer du \_ droit d’accès en lecture générique.                                                                                                                                                                                                                                                                                                                                                                                                                                                          |




Un thread du processus d’une application peut effectuer une opération d’attente pour attendre que l’entrée soit disponible dans une mémoire tampon d’entrée. Pour initier une opération d’attente, spécifiez un handle vers la mémoire tampon d’entrée dans un appel à l’une des [fonctions d’attente](https://msdn.microsoft.com/library/windows/desktop/ms687069). Ces fonctions peuvent retourner lorsque l’état d’un ou plusieurs objets est signalé. L’état d’un descripteur d’entrée de la console devient signalé lorsqu’il y a des enregistrements non lus dans sa mémoire tampon d’entrée. L’État est réinitialisé à l’état non signalé lorsque la mémoire tampon d’entrée est vide. Si aucune entrée n’est disponible, le thread appelant passe à un état d’attente efficace, ce qui consomme très peu de temps processeur en attendant que les conditions de l’opération d’attente soient satisfaites.








