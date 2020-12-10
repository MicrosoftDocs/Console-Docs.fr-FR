---
ms.openlocfilehash: eaaaa3487e8f2aa95915f6f10724bf4c26784622
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "93038871"
---
Une console se compose d’une mémoire tampon d’entrée et d’une ou de plusieurs mémoires tampons d’écran. Le mode d’une mémoire tampon de console détermine le comportement de la console lors des opérations d’entrée ou de sortie (E/S). Un ensemble de constantes d’indicateur est utilisé avec les handles d’entrée, et un autre ensemble est utilisé avec les handles (de sortie) de mémoire tampon d’écran. La définition des modes de sortie d’une mémoire tampon d’écran n’affecte pas les modes de sortie des autres mémoires tampons d’écran.

Les modes **ENABLE\_LINE\_INPUT** et **ENABLE\_ECHO\_INPUT** affectent uniquement les processus qui utilisent [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ou [**ReadConsole**](../readconsole.md) pour lire à partir de la mémoire tampon d’entrée de la console. De même, le mode **ENABLE\_PROCESSED\_INPUT** affecte principalement les utilisateurs de **ReadFile** et de **ReadConsole**, sauf qu’il détermine également si l’entrée CTRL+C est signalée dans la mémoire tampon d’entrée (pour être lue par la fonction [**ReadConsoleInput**](../readconsoleinput.md)) ou si elle est passée à une fonction définie par l’application.

Les modes **ENABLE\_WINDOW\_INPUT** et **ENABLE\_MOUSE\_INPUT** déterminent si les interactions utilisateur impliquant un redimensionnement de fenêtre et des actions de la souris sont signalées dans la mémoire tampon d’entrée ou si elles sont ignorées. Ces événements peuvent être lus par [**ReadConsoleInput**](../readconsoleinput.md), mais ils sont toujours filtrés par [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**ReadConsole**](../readconsole.md).

Les modes **ENABLE\_PROCESSED\_OUTPUT** et **ENABLE\_WRAP\_AT\_EOL\_OUTPUT** affectent uniquement les processus qui utilisent [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ou [**ReadConsole**](../readconsole.md) et [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ou [**WriteConsole**](../writeconsole.md).
