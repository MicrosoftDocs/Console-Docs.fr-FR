---
title: Sélection de consoles
description: Une application d’accessibilité a besoin d’informations sur la sélection de l’utilisateur dans la console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_console\_selection'
- base.console\_selection
- consoles.console\_selection
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f631e1b-d502-45b7-9c15-34c01e913738
ms.openlocfilehash: afc2d0a7615381b394df7f496aaf1b2a6002d04f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039157"
---
# <a name="console-selection"></a>Sélection de consoles

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Une application d’accessibilité a besoin d’informations sur la sélection de l’utilisateur dans la console. Pour récupérer la sélection de la console actuelle, appelez la fonction [**GetConsoleSelectionInfo**](getconsoleselectioninfo.md) . La structure d’informations sur la [**\_ sélection \_**](console-selection-info-str.md) de la console contient des informations sur la sélection, telles que l’ancre, les coordonnées et l’État.
