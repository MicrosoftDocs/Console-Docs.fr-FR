---
ms.openlocfilehash: 2e5222bba5878d98c6f703b8aa25dfd1a22197db
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037030"
---
Cette fonction utilise des caractères Unicode ou 8 bits à partir de la page de codes actuelle de la console. La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système. Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](../setconsolecp.md) ou [**SetConsoleOutputCP**](../setconsoleoutputcp.md) . Les consommateurs hérités peuvent également utiliser les commandes **chcp** ou **con # Select =** , mais cela n’est pas recommandé pour un nouveau développement.