---
ms.openlocfilehash: eaaaa3487e8f2aa95915f6f10724bf4c26784622
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038871"
---
Une console se compose d’une mémoire tampon d’entrée et d’une ou plusieurs mémoires tampons d’écran. Le mode d’une mémoire tampon de console détermine le comportement de la console lors des opérations d’entrée ou de sortie (e/s). Un jeu de constantes d’indicateur est utilisé avec les handles d’entrée, et un autre jeu est utilisé avec les descripteurs de mémoire tampon d’écran (sortie). La définition des modes de sortie d’une mémoire tampon d’écran n’affecte pas les modes de sortie des autres mémoires tampons d’écran.

Les modes **activer l' \_ \_ entrée** de la ligne et **activer l' \_ \_ entrée** de l’écho affectent uniquement les processus qui utilisent [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ou [**ReadConsole**](../readconsole.md) pour lire à partir de la mémoire tampon d’entrée de la console. De même, l' **activation du mode \_ \_ d’entrée traité** affecte principalement les utilisateurs de **ReadFile** et **ReadConsole** , à ceci près qu’elle détermine également si l’entrée Ctrl + C est signalée dans la mémoire tampon d’entrée (pour être lue par la fonction [**ReadConsoleInput**](../readconsoleinput.md) ) ou si elle est passée à une fonction définie par l’application.

Les modes **activer l' \_ \_ entrée** de la fenêtre et **activer \_ la souris \_** déterminent si les interactions de l’utilisateur impliquant le redimensionnement de fenêtre et les actions de la souris sont signalées dans la mémoire tampon d’entrée ou ignorées. Ces événements peuvent être lus par [**ReadConsoleInput**](../readconsoleinput.md), mais ils sont toujours filtrés par [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**ReadConsole**](../readconsole.md).

Les modes de sortie **activer le \_ \_ résultat traité** et **activer le \_ Retour à la ligne \_ en fin de \_ \_ vie** affectent uniquement les processus utilisant [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) , [**ReadConsole**](../readconsole.md) et [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ou [**WriteConsole**](../writeconsole.md).
