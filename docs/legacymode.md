---
title: Mode Console héritée - Bureau Windows
description: Le mode Console héritée est un outil de compatibilité permettant d’exécuter des applications en ligne de commande qui risquent de ne pas fonctionner avec l’hôte de console Windows 10
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, api console, compatibilité
ms.openlocfilehash: eeddfd00ffa8c3ad9d99583b89e4b3be7959f445
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "93037707"
---
# <a name="legacy-console-mode"></a>Mode Console héritée

Le mode Console hérité est un outil de compatibilité conçu pour aider les utilisateurs d’anciens outils en ligne de commande sur Windows 10. Pour tous les outils en ligne de commande qui ne s’affichent pas ou ne fonctionnent pas correctement dans l’expérience par défaut de la console Windows 10, ce mode fournit une solution grossière pour rétablir, dans le système, une version antérieure de l’expérience d’hébergement de console.

## <a name="using-legacy-console-mode"></a>Utilisation du mode Console héritée

Pour utiliser le mode Console hérité, commencez par ouvrir une fenêtre d’hébergement de console. Cette opération s’effectue généralement en lançant l’un des interpréteurs de commandes [CMD](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd) ou [PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-windows-powershell).

Cliquez avec le bouton droit sur la barre de titre de l’application, puis choisissez l’option de menu `Properties`. Choisissez le premier onglet, `Options`. Cochez ensuite la case en bas de la page décrivant `Use legacy console`. Appuyez sur le bouton `OK` pour appliquer vos sélections.

Le paramètre peut être rétabli en revenant au même menu de feuille de propriétés, en décochant la case, puis en appuyant sur `OK`.

> [!NOTE]
>Ce paramètre est appliqué globalement à toutes les sessions qui démarrent après le changement de la préférence. Les sessions déjà ouvertes ne sont pas modifiées.

## <a name="differences-between-modes"></a>Différences entre les modes

L’équipe Hôte de la console s’efforce de réduire les différences entre le mode Hérité et le mode actuel de la console pour garantir que le plus grand nombre de clients possible peuvent exécuter la version la plus à jour. Si vous rencontrez un problème qui vous oblige à utiliser la console héritée qui n’est pas documentée ici, contactez l’équipe sur le dépôt GitHub [microsoft/terminal](https://github.com/microsoft/terminal/) ou par le biais du [Hub de commentaires](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) pour obtenir de l’aide.

### <a name="16-bit-applications-on-32-bit-windows"></a>Applications 16 bits sur Windows 32 bits

Pour fonctionner, certaines applications 16 bits sur Windows 32 bits utilisent une technologie de machine virtuelle appelée [NTVDM](https://docs.microsoft.com/windows/compatibility/ntvdm-and-16-bit-app-support). Ces applications utilisent souvent un mode de mise en mémoire tampon d’écran graphique conjointement avec l’environnement d’hébergement de console pour fonctionner. Seule l’expérience de console héritée prend en charge ces modes de mise en mémoire tampon graphiques et les API de console supplémentaires nécessaires pour alimenter ces applications. Le système sélectionne automatiquement l’environnement de console héritée quand l’une de ces applications est lancée.

### <a name="ime-embedding"></a>Incorporation d’IME

L’hôte de console héritée incorporait la partie suggestion de l’IME à l’intérieur de la fenêtre d’hébergement en réservant une ligne en bas de l’écran pour les suggestions. Au lieu de cela, l’environnement d’hôte de console actuel délègue cette activité au sous-système IME pour afficher une fenêtre superposée au-dessus de l’hôte de console avec des suggestions. Dans un environnement où les fenêtres superposées ne sont pas possibles (comme avec certains outils de communication à distance), l’hôte de console héritée peut être nécessaire.

### <a name="api-differences"></a>Différences d’API

La principale différence connue entre l’hôte hérité et l’hôte actuel est l’implémentation d’UTF-8. L’hôte hérité a une prise en charge extrêmement rudimentaire et souvent incorrecte d’UTF-8 avec la [page de codes 65001](https://docs.microsoft.com/windows/win32/intl/code-pages). L’hôte de console actuel bénéficie d’améliorations progressives de Windows 10, version après version, visant à perfectionner cette prise en charge. Les applications qui tentent de s’appuyer sur la prédiction d’interprétations « connues comme étant incorrectes » d’UTF-8 à partir de la console héritée peuvent se retrouver à recevoir des réponses différentes à mesure que la prise en charge est améliorée.

Les autres différences rencontrées avec les API doivent être signalées dans le [dépôt GitHub microsoft/terminal](https://github.com/microsoft/terminal/) ou le [Hub de commentaires](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) en vue de les trier et d’y apporter des solutions.
