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
# <a name="console-selection"></a><span data-ttu-id="ca515-104">Sélection de consoles</span><span class="sxs-lookup"><span data-stu-id="ca515-104">Console Selection</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="ca515-105">Une application d’accessibilité a besoin d’informations sur la sélection de l’utilisateur dans la console.</span><span class="sxs-lookup"><span data-stu-id="ca515-105">An accessibility application needs information about the user's selection in the console.</span></span> <span data-ttu-id="ca515-106">Pour récupérer la sélection de la console actuelle, appelez la fonction [**GetConsoleSelectionInfo**](getconsoleselectioninfo.md) .</span><span class="sxs-lookup"><span data-stu-id="ca515-106">To retrieve the current console selection, call the [**GetConsoleSelectionInfo**](getconsoleselectioninfo.md) function.</span></span> <span data-ttu-id="ca515-107">La structure d’informations sur la [**\_ sélection \_**](console-selection-info-str.md) de la console contient des informations sur la sélection, telles que l’ancre, les coordonnées et l’État.</span><span class="sxs-lookup"><span data-stu-id="ca515-107">The [**CONSOLE\_SELECTION\_INFO**](console-selection-info-str.md) structure contains information about the selection, such as the anchor, coordinates, and status.</span></span>
