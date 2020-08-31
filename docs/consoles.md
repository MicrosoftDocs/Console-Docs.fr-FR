---
title: Consoles – Windows Desktop
description: Une console est une application qui fournit des e/s à des applications en ligne de commande.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: 7b447e3c1d6d72c58890797177f6668f5d835d35
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059241"
---
# <a name="consoles"></a>Consoles

Une *console* (ou un *Terminal*) est une application qui fournit des e/s à des applications en mode caractère. Ce mécanisme indépendant du processeur facilite le portage des applications en mode caractère existantes ou la création d’outils et d’applications en mode caractères.

Une console se compose d’une mémoire tampon d’entrée et d’une ou plusieurs mémoires tampons d’écran. La *mémoire tampon d’entrée* contient une file d’attente d’enregistrements d’entrée, chacun contenant des informations sur un événement d’entrée. La file d’attente d’entrée comprend toujours des événements touche-pression et clé-version. Il peut également inclure des événements de souris (mouvements de pointeurs et presses de bouton et mises en production) et des événements au cours desquels les actions de l’utilisateur affectent la taille de la mémoire tampon d’écran active. Une *mémoire tampon d’écran* est un tableau à deux dimensions de données de caractères et de couleur pour la sortie dans une fenêtre de console. Un nombre quelconque de processus peuvent partager une console.

- [Création d’une console](creation-of-a-console.md)
- [Attachement à une console](attaching-to-a-console.md)
- [Fermeture d’une console](closing-a-console.md)
- [Handles de la console](console-handles.md)
- [Mémoire tampon d’entrée de la console](console-input-buffer.md)
- [Mémoires tampons d’écran de la console](console-screen-buffers.md)
- [Taille de la mémoire tampon de la fenêtre et de l’écran](window-and-screen-buffer-size.md)
- [Sélection de la console](console-selection.md)
- [Défilement de la mémoire tampon d’écran](scrolling-the-screen-buffer.md)
