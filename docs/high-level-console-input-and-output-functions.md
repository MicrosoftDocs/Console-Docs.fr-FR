---
title: Fonctions d’entrée et de sortie de la console de haut niveau
description: Les fonctions ReadFile et WriteFile, ou les fonctions ReadConsole et WriteConsole, permettent à une application de lire l’entrée de la console et d’écrire la sortie de la console sous forme de flux de caractères.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_high\_level\_console\_input\_and\_output\_functions'
- base.high\_level\_console\_input\_and\_output\_functions
- consoles.high\_level\_console\_input\_and\_output\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 086b1bec-85f8-4e31-848d-7cb2d2703a3d
ms.openlocfilehash: d6e13edf9350fcff812ad02b2d9116c3fe132154
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059089"
---
# <a name="high-level-console-input-and-output-functions"></a>Fonctions d’entrée et de sortie de la console de haut niveau


Les fonctions [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) , ou les fonctions [**ReadConsole**](readconsole.md) et [**WriteConsole**](writeconsole.md) , permettent à une application de lire l’entrée de la console et d’écrire la sortie de la console sous forme de flux de caractères. **ReadConsole** et **WriteConsole** se comportent exactement comme **ReadFile** et **WriteFile** , sauf qu’ils peuvent être utilisés comme fonctions à caractères larges (dans lesquelles les arguments Text doivent utiliser Unicode) ou comme fonctions ANSI (dans lesquelles les arguments Text doivent utiliser des caractères du jeu de caractères Windows). Les applications qui doivent gérer un seul ensemble de sources pour prendre en charge Unicode ou le jeu de caractères ANSI doivent utiliser **ReadConsole** et **WriteConsole**.

[**ReadConsole**](readconsole.md) et [**WriteConsole**](writeconsole.md) peuvent uniquement être utilisés avec des handles de console ; [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) peuvent être utilisés avec d’autres Handles (tels que des fichiers ou des canaux). **ReadConsole** et **WriteConsole** échouent s’ils sont utilisés avec un handle standard qui a été redirigé et n’est plus un handle de console.

Pour obtenir une entrée au clavier, un processus peut utiliser [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ou [**ReadConsole**](readconsole.md) avec un handle vers la mémoire tampon d’entrée de la console, ou il peut utiliser **ReadFile** pour lire l’entrée à partir d’un fichier ou d’un canal si stdin a été redirigé. Ces fonctions retournent uniquement les événements de clavier qui peuvent être traduits en caractères ANSI (ou en caractères Unicode dans le cas de **ReadConsole**). L’entrée qui peut être retournée comprend des combinaisons de touches de contrôle. Les fonctions ne retournent pas d’événements de clavier impliquant les touches de fonction ou les touches de direction. Les événements d’entrée générés par la souris, la fenêtre, le focus ou l’entrée de menu sont ignorés.

Si le mode de saisie de ligne est activé (mode par défaut), [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**ReadConsole**](readconsole.md) ne retournent pas à l’application appelante tant que la touche entrée n’est pas enfoncée. Si le mode de saisie de ligne est désactivé, les fonctions ne retournent pas de données tant qu’au moins un caractère n’est pas disponible. Dans l’un ou l’autre mode, tous les caractères disponibles sont lus jusqu’à ce que plus aucune clé soit disponible ou que le nombre spécifié de caractères ait été lu. Les caractères non lus sont mis en mémoire tampon jusqu’à la prochaine opération de lecture. Les fonctions indiquent le nombre total de caractères réellement lus. Si le mode d’entrée ECHO est activé, les caractères lus par ces fonctions sont écrits dans la mémoire tampon d’écran active à la position actuelle du curseur.

Un processus peut utiliser [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ou **WriteConsole** pour écrire dans une mémoire tampon d’écran active ou inactive, ou il peut utiliser **WriteFile** pour écrire dans un fichier ou un canal si stdout a été redirigé. Le mode de sortie traité et le retour à la ligne en mode de sortie EOL contrôlent la façon dont les caractères sont écrits ou répercutés dans une mémoire tampon d’écran.

Les caractères écrits par [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ou [**WriteConsole**](writeconsole.md), ou en écho par [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ou [**ReadConsole**](readconsole.md), sont insérés dans une mémoire tampon d’écran à la position actuelle du curseur. À mesure que chaque caractère est écrit, la position du curseur passe à la cellule de caractère suivante ; Toutefois, le comportement à la fin d’une ligne dépend du retour à la ligne de la mémoire tampon de l’écran de la console en mode de sortie EOL. Une application peut utiliser la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) pour déterminer la position actuelle du curseur et la fonction [**SetConsoleCursorPosition**](setconsolecursorposition.md) pour définir la position du curseur.

Pour obtenir un exemple qui utilise les fonctions d’e/s de console de haut niveau, consultez [utilisation des fonctions d’entrée et de sortie de haut niveau](using-the-high-level-input-and-output-functions.md).

 

 




