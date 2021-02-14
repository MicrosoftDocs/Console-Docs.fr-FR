---
title: Signal CTRL + fermer
description: Le système génère un signal CTRL + fermer lorsque l’utilisateur ferme une console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_ctrl\_close\_signal'
- base.ctrl\_close\_signal
- consoles.ctrl\_close\_signal
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a327dd55-3250-40ee-b1c4-6ba3b80984a8
ms.openlocfilehash: be237eac7649ad76615aea341a555a8a7af6445c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357889"
---
# <a name="ctrlclose-signal"></a>Signal CTRL + fermer

Le système génère un signal CTRL + fermer lorsque l’utilisateur ferme une console. Tous les processus attachés à la console reçoivent le signal, donnant à chaque processus la possibilité de le nettoyer avant son arrêt. Lorsqu’un processus reçoit ce signal, la fonction de gestionnaire peut effectuer l’une des actions suivantes après avoir effectué des opérations de nettoyage :

- Appelez [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) pour terminer le processus.
- Retourne **false**. Si aucune des fonctions de gestionnaire inscrites ne retourne la **valeur true**, le gestionnaire par défaut arrête le processus.
- Retourne la **valeur true**. Dans ce cas, aucune autre fonction de gestionnaire n’est appelée et le processus se termine.