---
title: Signal CTRL + fermer
description: Le système génère un signal CTRL + fermer lorsque l’utilisateur ferme une console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_ctrl\_close\_signal'
- base.ctrl\_close\_signal
- consoles.ctrl\_close\_signal
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a327dd55-3250-40ee-b1c4-6ba3b80984a8
ms.openlocfilehash: a44f54e5c73c77155d4aa1d8307375c176463a49
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059213"
---
# <a name="ctrlclose-signal"></a>Signal CTRL + fermer


Le système génère un signal CTRL + fermer lorsque l’utilisateur ferme une console. Tous les processus attachés à la console reçoivent le signal, donnant à chaque processus la possibilité de le nettoyer avant son arrêt. Lorsqu’un processus reçoit ce signal, la fonction de gestionnaire peut effectuer l’une des actions suivantes après avoir effectué des opérations de nettoyage :

- Appelez [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) pour terminer le processus.
- Retourne **false**. Si aucune des fonctions de gestionnaire inscrites ne retourne la **valeur true**, le gestionnaire par défaut arrête le processus.
- Retourne la **valeur true**. Dans ce cas, aucune autre fonction de gestionnaire n’est appelée et le processus se termine.

 

 




