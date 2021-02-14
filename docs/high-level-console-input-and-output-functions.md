---
title: Fonctions d’entrée et de sortie de la console High-Level
description: Les fonctions ReadFile et WriteFile, ou les fonctions ReadConsole et WriteConsole, permettent à une application de lire l’entrée de la console et d’écrire la sortie de la console sous forme de flux de caractères.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_high\_level\_console\_input\_and\_output\_functions'
- base.high\_level\_console\_input\_and\_output\_functions
- consoles.high\_level\_console\_input\_and\_output\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 086b1bec-85f8-4e31-848d-7cb2d2703a3d
ms.openlocfilehash: 4da8845e4e35170980d306930c182ff6e5fb6cbf
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358299"
---
# <a name="high-level-console-input-and-output-functions"></a>Fonctions d’entrée et de sortie de la console High-Level

Les fonctions [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) et [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) , ou les fonctions [**ReadConsole**](readconsole.md) et [**WriteConsole**](writeconsole.md) , permettent à une application de lire l’entrée de la console et d’écrire la sortie de la console sous forme de flux de caractères. **ReadConsole** et **WriteConsole** se comportent exactement comme **ReadFile** et **WriteFile** , sauf qu’ils peuvent être utilisés comme fonctions à caractères larges (dans lesquelles les arguments Text doivent utiliser Unicode) ou comme fonctions ANSI (dans lesquelles les arguments Text doivent utiliser des caractères du jeu de caractères Windows). Les applications qui doivent gérer un seul ensemble de sources pour prendre en charge Unicode ou le jeu de caractères ANSI doivent utiliser **ReadConsole** et **WriteConsole**.

[**ReadConsole**](readconsole.md) et [**WriteConsole**](writeconsole.md) peuvent uniquement être utilisés avec des handles de console ; [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) et [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) peuvent être utilisés avec d’autres Handles (tels que des fichiers ou des canaux). **ReadConsole** et **WriteConsole** échouent s’ils sont utilisés avec un handle standard qui a été redirigé et n’est plus un handle de console.

Pour obtenir une entrée au clavier, un processus peut utiliser [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) ou [**ReadConsole**](readconsole.md) avec un handle vers la mémoire tampon d’entrée de la console, ou il peut utiliser **ReadFile** pour lire l’entrée à partir d’un fichier ou d’un canal si `STDIN` a été redirigé. Ces fonctions retournent uniquement les événements de clavier qui peuvent être traduits en caractères ANSI ou Unicode. L’entrée qui peut être retournée comprend des combinaisons de touches de contrôle. Les fonctions ne retournent pas d’événements de clavier impliquant les touches de fonction ou les touches de direction. Les événements d’entrée générés par la souris, la fenêtre, le focus ou l’entrée de menu sont ignorés.

Si le mode de saisie de ligne est activé (mode par défaut), [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) et [**ReadConsole**](readconsole.md) ne retournent pas à l’application appelante tant que la touche entrée n’est pas enfoncée. Si le mode de saisie de ligne est désactivé, les fonctions ne retournent pas de données tant qu’au moins un caractère n’est pas disponible. Dans l’un ou l’autre mode, tous les caractères disponibles sont lus jusqu’à ce que plus aucune clé soit disponible ou que le nombre spécifié de caractères ait été lu. Les caractères non lus sont mis en mémoire tampon jusqu’à la prochaine opération de lecture. Les fonctions indiquent le nombre total de caractères réellement lus. Si le mode d’entrée ECHO est activé, les caractères lus par ces fonctions sont écrits dans la mémoire tampon d’écran active à la position actuelle du curseur.

Un processus peut utiliser [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) ou **WriteConsole** pour écrire dans une mémoire tampon d’écran active ou inactive, ou il peut utiliser **WriteFile** pour écrire dans un fichier ou un canal si stdout a été redirigé. Le mode de sortie traité et le retour à la ligne en mode de sortie EOL contrôlent la façon dont les caractères sont écrits ou répercutés dans une mémoire tampon d’écran.

Les caractères écrits par [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) ou [**WriteConsole**](writeconsole.md), ou en écho par [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) ou [**ReadConsole**](readconsole.md), sont insérés dans une mémoire tampon d’écran à la position actuelle du curseur. À mesure que chaque caractère est écrit, la position du curseur passe à la cellule de caractère suivante ; Toutefois, le comportement à la fin d’une ligne dépend du retour à la ligne de la mémoire tampon de l’écran de la console en mode de sortie EOL.

Vous trouverez plus d’informations sur la position du curseur par le biais de **[séquences de terminaux virtuels](console-virtual-terminal-sequences.md)**, en particulier dans la catégorie état de la **[requête](console-virtual-terminal-sequences.md#query-state)** pour trouver la position actuelle et la catégorie de **[positionnement du curseur](console-virtual-terminal-sequences.md#cursor-positioning)** pour définir la position actuelle. Une application peut également utiliser la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) pour déterminer la position actuelle du curseur et la fonction [**SetConsoleCursorPosition**](setconsolecursorposition.md) pour définir la position du curseur. Toutefois, le mécanisme de **séquences de terminaux virtuels** est préféré pour tout développement nouveau et en cours. Pour plus d’informations sur la stratégie qui sous-tend cette décision, consultez la documentation sur les **[fonctions classiques par rapport aux terminaux virtuels](classic-vs-vt.md)** et aux plans de l' **[écosystème](ecosystem-roadmap.md)** .

Pour obtenir un exemple qui utilise les fonctions d’e/s de console de haut niveau, consultez [utilisation des fonctions d’entrée et de sortie High-Level](using-the-high-level-input-and-output-functions.md).