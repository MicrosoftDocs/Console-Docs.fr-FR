---
title: Consoles – Windows Desktop
description: Une console est une application qui fournit des e/s à des applications en ligne de commande.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: b50ccd3d38b70ce67498451c8272b832c59fcef9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039117"
---
# <a name="consoles"></a>Consoles

Une *console* est une application qui fournit des services d’e/s aux applications en mode caractère.

Une console se compose d’une mémoire tampon d’entrée et d’une ou plusieurs mémoires tampons d’écran. La *mémoire tampon d’entrée* contient une file d’attente d’enregistrements d’entrée, chacun contenant des informations sur un événement d’entrée. La file d’attente d’entrée comprend toujours des événements touche-pression et clé-version. Il peut également inclure des événements de souris (mouvements de pointeurs et presses de bouton et mises en production) et des événements au cours desquels les actions de l’utilisateur affectent la taille de la mémoire tampon d’écran active. Une *mémoire tampon d’écran* est un tableau à deux dimensions de données de caractères et de couleur pour la sortie dans une fenêtre de console. Un nombre quelconque de processus peuvent partager une console.

> [!TIP]
>Une idée plus large des consoles et de la façon dont elles sont liées aux terminaux et aux applications clientes de ligne de commande est disponible dans la feuille de route de l' **[écosystème](ecosystem-roadmap.md)** .

- [Création d’une console](creation-of-a-console.md)
- [Attachement à une console](attaching-to-a-console.md)
- [Fermeture d’une console](closing-a-console.md)
- [Handles de console](console-handles.md)
- [Mémoire tampon d’entrée d’une console](console-input-buffer.md)
- [Mémoires tampons d’écran d’une console](console-screen-buffers.md)
- [Taille de la mémoire tampon de la fenêtre et de l’écran](window-and-screen-buffer-size.md)
- [Sélection de consoles](console-selection.md)
- [Défilement de la mémoire tampon d’écran](scrolling-the-screen-buffer.md)
