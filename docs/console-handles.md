---
title: Handles de la console
description: Un processus de console utilise des handles pour accéder aux mémoires tampons d’entrée et d’écran de sa console, y compris les fonctions GetStdHandle, CreateFile ou CreateConsoleScreenBuffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_console\_handles'
- base.console\_handles
- consoles.console\_handles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: dc723046-b3e9-418a-b386-79be411e5ac8
ms.openlocfilehash: 50b1ca460818080461116df85bf51387c024df89
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059072"
---
# <a name="console-handles"></a>Handles de la console


Un processus de console utilise des handles pour accéder aux mémoires tampons d’entrée et d’écran de sa console. Un processus peut utiliser la fonction [**GetStdHandle**](getstdhandle.md), [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)ou [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) pour ouvrir l’un de ces handles.

La fonction [**GetStdHandle**](getstdhandle.md) fournit un mécanisme permettant de récupérer les handles d’entrée standard (stdin), de sortie standard (stdout) et d’erreur standard (stderr) associés à un processus. Pendant la création de la console, le système crée ces descripteurs. Initialement, STDIN est un handle vers la mémoire tampon d’entrée de la console, et STDOUT et STDERR sont des handles de la mémoire tampon d’écran active de la console. Toutefois, la fonction [**SetStdHandle**](setstdhandle.md) peut rediriger les handles standard en modifiant le descripteur associé à stdin, stdout ou stderr. Étant donné que les handles standard du parent sont hérités par n’importe quel processus enfant, les appels suivants à **GetStdHandle** retournent le handle Redirigé. Un handle retourné par **GetStdHandle** peut, par conséquent, faire référence à autre chose que l’e/s de la console. Par exemple, avant de créer un processus enfant, un processus parent peut utiliser **SetStdHandle** pour définir un handle de canal comme handle stdin hérité par le processus enfant. Lorsque le processus enfant appelle **GetStdHandle**, il obtient le handle du canal. Cela signifie que le processus parent peut contrôler les handles standard du processus enfant. Les handles retournés par **GetStdHandle** ont une \_ lecture générique | \_Accès en écriture générique, sauf si **SetStdHandle** a été utilisé pour définir le handle standard de manière à avoir un accès moindre.

La valeur des handles renvoyés par [**GetStdHandle**](getstdhandle.md) n’est pas 0, 1 et 2. par conséquent, les constantes de flux prédéfinies standard dans stdio. h (stdin, stdout et stderr) ne peuvent pas être utilisées dans les fonctions qui requièrent un handle de console.

La fonction [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) permet à un processus d’obtenir un handle vers la mémoire tampon d’entrée et la mémoire tampon d’écran active de la console, même si stdin et stdout ont été redirigés. Pour ouvrir un handle vers la mémoire tampon d’entrée d’une console, spécifiez la valeur CONIN $ dans un appel à **CreateFile**. Spécifiez la valeur CONOUT $ dans un appel à **CreateFile** pour ouvrir un handle vers la mémoire tampon d’écran active d’une console. **CreateFile** vous permet de spécifier l’accès en lecture/écriture du handle qu’il retourne.

La fonction [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) crée une mémoire tampon d’écran et retourne un descripteur. Ce handle peut être utilisé dans toute fonction qui accepte un handle vers la sortie de la console. La nouvelle mémoire tampon d’écran n’est pas active tant que son handle n’est pas spécifié dans un appel à la fonction [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) . Notez que la modification de la mémoire tampon d’écran active n’affecte pas le handle retourné par [**GetStdHandle**](getstdhandle.md). De même, l’utilisation de [**SetStdHandle**](setstdhandle.md) pour modifier le descripteur stdout n’affecte pas la mémoire tampon d’écran active.

Les handles de console retournés par [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) et [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) peuvent être utilisés dans n’importe quelle fonction de console qui requiert un handle vers la mémoire tampon d’entrée d’une console ou d’une mémoire tampon d’écran de la console. Les handles retournés par [**GetStdHandle**](getstdhandle.md) peuvent être utilisés par les fonctions de la console s’ils n’ont pas été redirigés pour faire référence à autre chose que les e/s de la console. Toutefois, si un handle standard a été redirigé pour faire référence à un fichier ou à un canal, le handle ne peut être utilisé que par les fonctions [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) .

Un processus peut utiliser la fonction [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) pour créer un handle de console en double qui a un accès ou une héritage différent du handle d’origine. Notez, toutefois, qu’un processus peut créer un handle de console dupliqué uniquement pour sa propre utilisation. Cela diffère des autres types de handles (tels que les objets de fichier, de canal ou mutex), pour lesquels **DuplicateHandle** peut créer un doublon valide pour un processus différent.

Pour fermer un handle de console, un processus peut utiliser la fonction [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) .

 

 




