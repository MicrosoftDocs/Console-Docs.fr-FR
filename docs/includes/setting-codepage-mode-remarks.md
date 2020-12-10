---
ms.openlocfilehash: 2e5222bba5878d98c6f703b8aa25dfd1a22197db
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "93037030"
---
Cette fonction utilise des caractères Unicode ou des caractères 8 bits de la page de codes actuelle de la console. Par défaut, la page de codes de la console est initialement définie sur la page de codes OEM du système. Pour changer la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](../setconsolecp.md) ou [**SetConsoleOutputCP**](../setconsoleoutputcp.md). Les consommateurs existants peuvent également utiliser les commandes **chcp** ou **mode con cp select=** , mais ce n’est pas recommandé pour un nouveau développement.