---
title: Attachement à une console
description: Un processus peut utiliser la fonction AttachConsole pour s’attacher à une console. Un processus peut être attaché à une console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_attaching\_to\_a\_console'
- base.attaching\_to\_a\_console
- consoles.attaching\_to\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 348e572f-2448-4384-9822-fab01d4ba255
ms.openlocfilehash: 793cc83c0af1f8b0ae4be026f966a79dd034250e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037457"
---
# <a name="attaching-to-a-console"></a>Attachement à une console

Un processus peut utiliser la fonction [**AttachConsole**](attachconsole.md) pour attacher une console en tant que client. Un processus peut être attaché à une console.

Un grand nombre de processus peuvent être attachés à une console. Pour récupérer une liste des processus attachés à une console, appelez la fonction [**GetConsoleProcessList**](getconsoleprocesslist.md) .

Pour attacher en tant que serveur, consultez les informations relatives à [**Pseudoconsoles**](pseudoconsoles.md).
