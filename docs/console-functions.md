---
title: Fonctions de la console
description: Décrit la liste complète de toutes les fonctions utilisées pour accéder à une console.
author: miniksa
ms.author: miniksa
ms.topic: hub-page
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_console\_functions'
- base.console\_functions
- consoles.console\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2a0e5dcc-be48-42ab-a05a-96f68d012a67
ms.openlocfilehash: 0ee2dde2c14a3d827aa2bc5e14f3cc65cf5fdc0f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039237"
---
# <a name="console-functions"></a>Fonctions de la console

Les fonctions suivantes sont utilisées pour accéder à une console.

| Fonction | Description |
|-|-|
| [**AddConsoleAlias**](addconsolealias.md) | Définit un alias de console pour l’exécutable spécifié. |
| [**AllocConsole**](allocconsole.md) | Alloue une nouvelle console pour le processus appelant. |
| [**AttachConsole**](attachconsole.md) | Joint le processus appelant à la console du processus spécifié. |
| [**ClosePseudoConsole**](closepseudoconsole.md) | Ferme un pseudoconsole à partir du handle donné. |
| [**CreatePseudoConsole**](createpseudoconsole.md) | Alloue un nouveau pseudoconsole pour le processus appelant. |
| [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) | Crée une mémoire tampon d’écran de la console. |
| [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) | Définit les attributs de couleur de texte et d’arrière-plan pour un nombre spécifié de cellules de caractères. |
| [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md) | Écrit un caractère dans la mémoire tampon de l’écran de la console un nombre spécifié de fois. |
| [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) | Vide la mémoire tampon d’entrée de la console. |
| [**FreeConsole**](freeconsole.md) | Détache le processus appelant de sa console. |
| [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) | Envoie un signal spécifié à un groupe de processus de console qui partage la console associée au processus appelant. |
| [**GetConsoleAlias**](getconsolealias.md) | Récupère l’alias spécifié pour l’exécutable spécifié. |
| [**GetConsoleAliases**](getconsolealiases.md) | Récupère tous les alias de console définis pour l’exécutable spécifié. |
| [**GetConsoleAliasesLength**](getconsolealiaseslength.md) | Retourne la taille, en octets, de la mémoire tampon nécessaire pour stocker tous les alias de console pour l’exécutable spécifié. |
| [**GetConsoleAliasExes**](getconsolealiasexes.md) | Récupère les noms de tous les exécutables avec des alias de console définis. |
| [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) | Retourne la taille, en octets, de la mémoire tampon nécessaire pour stocker les noms de tous les exécutables qui ont des alias de console définis. |
| [**GetConsoleCP**](getconsolecp.md) | Récupère la page de codes d’entrée utilisée par la console associée au processus appelant. |
| [**GetConsoleCursorInfo**](getconsolecursorinfo.md) | Récupère des informations sur la taille et la visibilité du curseur pour la mémoire tampon d’écran de console spécifiée. |
| [**GetConsoleDisplayMode**](getconsoledisplaymode.md) | Récupère le mode d’affichage de la console actuelle. |
| [**GetConsoleFontSize**](getconsolefontsize.md) | Récupère la taille de la police utilisée par la mémoire tampon d’écran de console spécifiée. |
| [**GetConsoleHistoryInfo**](getconsolehistoryinfo.md) | Récupère les paramètres d’historique pour la console du processus appelant. |
| [**GetConsoleMode**](getconsolemode.md) | Récupère le mode de saisie actuel de la mémoire tampon d’entrée d’une console ou le mode de sortie actuel d’une mémoire tampon d’écran de la console. |
| [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) | Récupère le titre d’origine de la fenêtre de console active. |
| [**GetConsoleOutputCP**](getconsoleoutputcp.md) | Récupère la page de codes de sortie utilisée par la console associée au processus appelant. |
| [**GetConsoleProcessList**](getconsoleprocesslist.md) | Récupère une liste des processus attachés à la console actuelle. |
| [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) | Récupère des informations sur la mémoire tampon d’écran de console spécifiée. |
| [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) | Récupère des informations étendues sur la mémoire tampon d’écran de console spécifiée. |
| [**GetConsoleSelectionInfo**](getconsoleselectioninfo.md) | Récupère des informations sur la sélection de la console actuelle. |
| [**GetConsoleTitle**](getconsoletitle.md) | Récupère le titre de la fenêtre de console active. |
| [**GetConsoleWindow**](getconsolewindow.md) | Récupère le handle de fenêtre utilisé par la console associée au processus appelant. |
| [**GetCurrentConsoleFont**](getcurrentconsolefont.md) | Récupère des informations sur la police de la console actuelle. |
| [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) | Récupère des informations étendues sur la police de la console actuelle. |
| [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) | Récupère la taille de la plus grande fenêtre de console possible. |
| [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) | Récupère le nombre d’enregistrements d’entrée non lus dans la mémoire tampon d’entrée de la console. |
| [**GetNumberOfConsoleMouseButtons**](getnumberofconsolemousebuttons.md) | Récupère le nombre de boutons de la souris utilisés par la console actuelle. |
| [**GetStdHandle**](getstdhandle.md) | Récupère un handle pour l’entrée standard, la sortie standard ou le périphérique d’erreur standard. |
| [**HandlerRoutine**](handlerroutine.md) | Fonction définie par l’application utilisée avec la fonction [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) . |
| [**PeekConsoleInput**](peekconsoleinput.md) | Lit les données de la mémoire tampon d’entrée de la console spécifiée sans les supprimer de la mémoire tampon. |
| [**ReadConsole**](readconsole.md) | Lit les entrées de caractères à partir de la mémoire tampon d’entrée de la console et les supprime de la mémoire tampon. |
| [**ReadConsoleInput**](readconsoleinput.md) | Lit les données à partir d’une mémoire tampon d’entrée de la console et les supprime de la mémoire tampon. |
| [**ReadConsoleOutput**](readconsoleoutput.md) | Lit les données d’attribut de caractère et de couleur à partir d’un bloc rectangulaire de cellules de caractères dans une mémoire tampon d’écran de la console. |
| [**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md) | Copie un nombre spécifié d’attributs de couleur de premier plan et d’arrière-plan à partir des cellules consécutives d’une mémoire tampon d’écran de la console. |
| [**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md) | Copie un nombre de caractères à partir de cellules consécutives dans une mémoire tampon d’écran de la console. |
| [**ResizePseudoConsole**](resizepseudoconsole.md) | Redimensionne les mémoires tampons internes pour un pseudoconsole à la taille donnée. |
| [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) | Déplace un bloc de données dans une mémoire tampon d’écran. |
| [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) | Définit la mémoire tampon d’écran spécifiée comme étant la mémoire tampon d’écran de la console actuellement affichée. |
| [**SetConsoleCP**](setconsolecp.md) | Définit la page de codes d’entrée utilisée par la console associée au processus appelant. |
| [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) | Ajoute ou supprime un [**HandlerRoutine**](handlerroutine.md) défini par l’application dans la liste des fonctions de gestionnaire pour le processus appelant. |
| [**SetConsoleCursorInfo**](setconsolecursorinfo.md) | Définit la taille et la visibilité du curseur pour la mémoire tampon d’écran de la console spécifiée. |
| [**SetConsoleCursorPosition**](setconsolecursorposition.md) | Définit la position du curseur dans la mémoire tampon d’écran de console spécifiée. |
| [**SetConsoleDisplayMode**](setconsoledisplaymode.md) | Définit le mode d’affichage de la mémoire tampon d’écran de console spécifiée. |
| [**SetConsoleHistoryInfo**](setconsolehistoryinfo.md) | Définit les paramètres de l’historique pour la console du processus appelant. |
| [**SetConsoleMode**](setconsolemode.md) | Définit le mode d’entrée de la mémoire tampon d’entrée d’une console ou le mode de sortie d’une mémoire tampon d’écran de la console. |
| [**SetConsoleOutputCP**](setconsoleoutputcp.md) | Définit la page de codes de sortie utilisée par la console associée au processus appelant. |
| [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) | Définit des informations étendues sur la mémoire tampon d’écran de console spécifiée. |
| [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) | Modifie la taille de la mémoire tampon d’écran de la console spécifiée. |
| [**SetConsoleTextAttribute**](setconsoletextattribute.md) | Définit les attributs de couleur de premier plan (texte) et d’arrière-plan des caractères écrits dans la mémoire tampon d’écran de la console. |
| [**SetConsoleTitle**](setconsoletitle.md) | Définit le titre de la fenêtre de console active. |
| [**SetConsoleWindowInfo**](setconsolewindowinfo.md) | Définit la taille actuelle et la position de la fenêtre d’une mémoire tampon d’écran de la console. |
| [**SetCurrentConsoleFontEx**](setcurrentconsolefontex.md) | Définit des informations étendues sur la police de la console actuelle. |
| [**SetStdHandle**](setstdhandle.md) | Définit le handle pour l’entrée standard, la sortie standard ou le périphérique d’erreur standard. |
| [**WriteConsole**](writeconsole.md) | Écrit une chaîne de caractères dans une mémoire tampon d’écran de console en commençant à l’emplacement actuel du curseur. |
| [**WriteConsoleInput**](writeconsoleinput.md) | Écrit les données directement dans la mémoire tampon d’entrée de la console. |
| [**WriteConsoleOutput**](writeconsoleoutput.md) | Écrit des données d’attribut de caractère et de couleur dans un bloc rectangulaire spécifié de cellules de caractères dans une mémoire tampon d’écran de la console. |
| [**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md) | Copie un certain nombre d’attributs de couleur de premier plan et d’arrière-plan dans les cellules consécutives d’une mémoire tampon d’écran de la console. |
| [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md) | Copie un nombre de caractères dans les cellules consécutives d’une mémoire tampon d’écran de la console. |
