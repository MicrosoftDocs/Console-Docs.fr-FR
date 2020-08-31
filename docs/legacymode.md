---
title: Mode console héritée – Bureau Windows
description: Le mode console héritée est un outil de compatibilité qui permet d’exécuter des applications en ligne de commande qui peuvent ne pas fonctionner avec l’hôte de la console Windows 10.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console, compatibilité
ms.openlocfilehash: a69e192426cc178ae98565db07c49f9ff2ce4961
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059288"
---
# <a name="legacy-console-mode"></a>Mode console hérité

Le mode de console hérité est un outil de compatibilité conçu pour aider les utilisateurs d’outils de ligne de commande plus anciens sur Windows 10. Pour tous les outils en ligne de commande qui ne s’affichent pas ou ne fonctionnent pas correctement dans l’expérience de la console Windows 10 par défaut, ce mode fournit une solution à granularité grossière pour revenir au système à une version antérieure de l’expérience d’hébergement de la console.

## <a name="using-legacy-console-mode"></a>Utilisation du mode console hérité

Pour utiliser le mode console hérité, commencez par ouvrir une fenêtre d’hébergement de console. Cela s’effectue généralement en lançant l’un des interpréteurs de commandes [cmd](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd) ou [PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-windows-powershell).

Cliquez avec le bouton droit sur la barre de titre de l’application et choisissez l' `Properties` option de menu. Choisissez le premier onglet, `Options` . Activez ensuite la case à cocher en bas de la page décrivant `Use legacy console` . Appuyez sur le `OK` bouton pour appliquer.

Le paramètre peut être rétabli en revenant au même menu de la feuille de propriétés et en désactivez la case, puis en appuyant sur `OK` .

**Remarque :** Ce paramètre est appliqué globalement à toutes les sessions qui démarrent après la modification de la préférence. Les sessions déjà ouvertes ne seront pas modifiées.

## <a name="differences-between-modes"></a>Différences entre les modes

L’équipe hôte de la console s’efforce de réduire les différences entre les modes hérité et actuel de la console pour s’assurer que le nombre de clients le plus récent possible peut exécuter la version la plus à jour. Si vous rencontrez un problème qui nécessite que vous utilisiez la console héritée qui n’est pas documentée ici, veuillez contacter l’équipe sur le référentiel [Microsoft/Terminal](https://github.com/microsoft/terminal/) GitHub ou via le [Hub de commentaires](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) pour obtenir de l’aide.

### <a name="16-bit-applications-on-32-bit-windows"></a>applications 16 bits sur Windows 32 bits

Certaines applications 16 bits sur Windows 32 bits utilisent une technologie de machine virtuelle pour fonctionner sous le nom [NTVDM](https://docs.microsoft.com/windows/compatibility/ntvdm-and-16-bit-app-support). Ces applications utilisent souvent un mode de mise en mémoire tampon d’écran graphique conjointement avec l’environnement d’hébergement de la console pour fonctionner. Seule l’expérience de la console héritée prend en charge ces modes de mise en mémoire tampon graphiques et la prise en charge d’API de console supplémentaire requise pour alimenter ces applications. Le système sélectionne automatiquement l’environnement de la console héritée quand l’une de ces applications est lancée.

### <a name="ime-embedding"></a>Incorporation IME

L’hôte de console hérité incorporait la partie suggestion de l’IME à l’intérieur de la fenêtre d’hébergement en réservant une ligne en bas de l’écran pour obtenir des suggestions. L’environnement actuel de l’hôte de la console délègue cette activité au sous-système IME pour afficher une fenêtre superposée au-dessus de l’hôte de la console avec des suggestions. Dans un environnement où les fenêtres de superposition ne sont pas possibles (comme avec certains outils de communication à distance), l’hôte de console hérité peut être nécessaire.

### <a name="api-differences"></a>Différences d’API

La principale différence connue entre les versions héritées et actuelles est l’implémentation d’UTF-8. L’hôte hérité a une prise en charge extrêmement rudimentaire et souvent incorrecte d’UTF-8 avec la [page de codes 65001](https://docs.microsoft.com/windows/win32/intl/code-pages). L’hôte de console actuel contient des améliorations incrémentielles de la version préliminaire de Windows 10 pour améliorer cette prise en charge. Les applications qui tentent de s’appuyer sur la prédiction des interprétations « incorrectes connues » d’UTF-8 à partir de la console héritée peuvent recevoir des réponses différentes à mesure que la prise en charge est améliorée. 

Les autres différences rencontrées avec les API doivent être signalées au référentiel [Microsoft/Terminal](https://github.com/microsoft/terminal/) GitHub ou via le [Hub de commentaires](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) pour le triage et la correction possible.