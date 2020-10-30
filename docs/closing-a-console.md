---
title: Fermeture d’une console
description: Un processus peut utiliser la fonction FreeConsole pour se détacher de sa console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_closing\_a\_console'
- base.closing\_a\_console
- consoles.closing\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 254b7cfc-4dee-452f-a409-4fc90d20d4c1
ms.openlocfilehash: db424e6d9fc91a7a3b6cff3b5fc5028833d208f9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037317"
---
# <a name="closing-a-console"></a>Fermeture d’une console

Un processus peut utiliser la fonction [**FreeConsole**](freeconsole.md) pour se détacher de sa console. Si d’autres processus partagent la console, la console n’est pas détruite, mais le processus qui a appelé **FreeConsole** ne peut pas y faire référence. Après l’appel de **FreeConsole** , le processus peut utiliser [**AllocConsole**](allocconsole.md) pour créer une nouvelle console ou [**AttachConsole**](attachconsole.md) à attacher à une autre console.

Une console est fermée lorsque le dernier processus qui lui est associé se termine ou appelle [**FreeConsole**](freeconsole.md).
