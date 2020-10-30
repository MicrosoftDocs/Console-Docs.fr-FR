---
title: Handles de console
description: Un processus de console utilise des handles pour accéder aux mémoires tampons d’entrée et d’écran de sa console, y compris les fonctions GetStdHandle, CreateFile ou CreateConsoleScreenBuffer.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_console\_handles'
- base.console\_handles
- consoles.console\_handles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: dc723046-b3e9-418a-b386-79be411e5ac8
ms.openlocfilehash: 29d25e83281c7c98c74ae4a0da03eea06dbf0077
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039227"
---
# <a name="console-handles"></a>Handles de console

Un processus de console utilise des handles pour accéder aux mémoires tampons d’entrée et d’écran de sa console. Un processus peut utiliser la fonction [**GetStdHandle**](getstdhandle.md), [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)ou [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) pour ouvrir l’un de ces handles.

La fonction [**GetStdHandle**](getstdhandle.md) fournit un mécanisme permettant de récupérer les handles d’entrée standard ( `STDIN` ), de sortie standard ( `STDOUT` ) et d’erreur standard ( `STDERR` ) associés à un processus. Pendant la création de la console, le système crée ces descripteurs. Initialement, `STDIN` est un handle vers la mémoire tampon d’entrée de la console et `STDOUT` et `STDERR` sont des handles de la mémoire tampon d’écran active de la console. Toutefois, la fonction [**SetStdHandle**](setstdhandle.md) peut rediriger les handles standard en modifiant le handle associé à `STDIN` , `STDOUT` ou `STDERR` . Étant donné que les handles standard du parent sont hérités par n’importe quel processus enfant, les appels suivants à **GetStdHandle** retournent le handle Redirigé. Un handle retourné par **GetStdHandle** peut, par conséquent, faire référence à autre chose que l’e/s de la console. Par exemple, avant de créer un processus enfant, un processus parent peut utiliser **SetStdHandle** pour définir un handle de canal comme `STDIN` handle hérité par le processus enfant. Lorsque le processus enfant appelle **GetStdHandle** , il obtient le handle du canal. Cela signifie que le processus parent peut contrôler les handles standard du processus enfant. Les handles retournés par **GetStdHandle** ont `GENERIC_READ | GENERIC_WRITE` accès, sauf si **SetStdHandle** a été utilisé pour définir le handle standard comme ayant un accès plus faible.

La valeur des handles retournées par [**GetStdHandle**](getstdhandle.md) n’est pas 0, 1 et 2. par conséquent, les constantes de flux prédéfinies standard dans stdio. h ( `STDIN` , `STDOUT` et `STDERR` ) ne peuvent pas être utilisées dans les fonctions qui requièrent un handle de console.

La fonction [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) permet à un processus d’obtenir un handle vers la mémoire tampon d’entrée et la mémoire tampon d’écran active de la console, même si `STDIN` et `STDOUT` ont été redirigés. Pour ouvrir un handle vers la mémoire tampon d’entrée d’une console, spécifiez la `CONIN$` valeur dans un appel à **CreateFile** . Spécifiez la `CONOUT$` valeur dans un appel à **CreateFile** pour ouvrir un handle vers la mémoire tampon d’écran active d’une console. **CreateFile** vous permet de spécifier l’accès en lecture/écriture du handle qu’il retourne.

La fonction [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) crée une mémoire tampon d’écran et retourne un descripteur. Ce handle peut être utilisé dans toute fonction qui accepte un handle vers la sortie de la console. La nouvelle mémoire tampon d’écran n’est pas active (affichée) tant que son handle n’est pas spécifié dans un appel à la fonction [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) . Notez que la modification de la mémoire tampon d’écran active n’affecte pas le handle retourné par [**GetStdHandle**](getstdhandle.md). De même, l’utilisation de [**SetStdHandle**](setstdhandle.md) pour modifier le `STDOUT` descripteur n’affecte pas la mémoire tampon d’écran active.

Les handles de console retournés par [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) et [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) peuvent être utilisés dans n’importe quelle fonction de console qui requiert un handle vers la mémoire tampon d’entrée d’une console ou d’une mémoire tampon d’écran de la console. Les handles retournés par [**GetStdHandle**](getstdhandle.md) peuvent être utilisés par les fonctions de la console s’ils n’ont pas été redirigés pour faire référence à autre chose que les e/s de la console. Toutefois, si un handle standard a été redirigé pour faire référence à un fichier ou à un canal, le handle ne peut être utilisé que par les fonctions [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) . [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype) peut vous aider à déterminer le type d’appareil auquel le descripteur fait référence. Un descripteur de console présente comme `FILE_TYPE_CHAR` .

Un processus peut utiliser la fonction [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) pour créer un handle de console en double qui a un accès ou une héritage différent du handle d’origine. Notez, toutefois, qu’un processus peut créer un handle de console dupliqué uniquement pour sa propre utilisation. Cela diffère des autres types de handles (tels que les objets de fichier, de canal ou mutex), pour lesquels **DuplicateHandle** peut créer un doublon valide pour un processus différent.
L’accès à une console doit être partagé lors de la [création](creation-of-a-console.md) de l’autre processus ou peut être demandé par l’autre processus par le biais du mécanisme [**AttachConsole**](attachconsole.md) .

Pour fermer un handle de console, un processus peut utiliser la fonction [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) .
