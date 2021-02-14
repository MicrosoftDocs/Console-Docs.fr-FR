---
title: Handles de console
description: Un processus de console utilise des handles pour accéder à la mémoire tampon d’entrée et à la mémoire tampon d’écran de sa console, notamment des fonctions GetStdHandle, CreateFile et CreateConsoleScreenBuffer.
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
ms.localizationpriority: high
ms.openlocfilehash: 817c902426ac09fdd246f8d1281528ee5dfcab06
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358069"
---
# <a name="console-handles"></a>Handles de console

Un processus de console utilise des handles pour accéder à la mémoire tampon d’entrée et à la mémoire tampon d’écran de sa console. Un processus peut utiliser la fonction [**GetStdHandle**](getstdhandle.md), [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) ou [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) pour ouvrir l’un de ces handles.

La fonction [**GetStdHandle**](getstdhandle.md) fournit un mécanisme permettant de récupérer les handles d’entrée standard (`STDIN`), de sortie standard (`STDOUT`) et d’erreur standard (`STDERR`) qui sont associés à un processus. Ces handles sont créés par le système pendant la création de la console. À la base, `STDIN` est un handle vers la mémoire tampon d’entrée de la console, et `STDOUT` et `STDERR` sont des handles vers la mémoire tampon d’écran active de la console. Toutefois, la fonction [**SetStdHandle**](setstdhandle.md) peut rediriger les handles standard en modifiant le handle associé à `STDIN`, `STDOUT` ou `STDERR`. Étant donné que les handles standard du parent sont hérités par tous les processus enfants, les appels suivants à **GetStdHandle** retourneront le handle redirigé. Un handle retourné par **GetStdHandle** peut, par conséquent, référencer autre chose que les E/S de la console. Par exemple, avant de créer un processus enfant, un processus parent peut utiliser **SetStdHandle** pour définir un handle de canal comme étant le handle `STDIN` hérité par le processus enfant. Lorsque le processus enfant appelle **GetStdHandle**, il obtient le handle du canal. Cela signifie que le processus parent peut contrôler les handles standard du processus enfant. Les handles retournés par **GetStdHandle** disposent d’un accès `GENERIC_READ | GENERIC_WRITE`, sauf si **SetStdHandle** a été utilisé dans le but de configurer un accès moindre pour le handle standard.

Les valeurs des handles retournées par [**GetStdHandle**](getstdhandle.md) ne sont pas 0, 1 et 2. Par conséquent, les constantes de flux prédéfinies standard contenues dans Stdio.h (`STDIN`, `STDOUT` et `STDERR`) ne peuvent pas être utilisées dans les fonctions qui nécessitent un handle de console.

La fonction [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) permet à un processus d’obtenir un handle vers la mémoire tampon d’entrée et la mémoire tampon d’écran active de la console, même si `STDIN` et `STDOUT` ont été redirigés. Pour ouvrir le handle vers la mémoire tampon d’entrée d’une console, spécifiez la valeur `CONIN$` dans un appel à **CreateFile**. Spécifiez la valeur `CONOUT$` dans un appel à **CreateFile** pour ouvrir le handle vers la mémoire tampon d’écran active de la console. **CreateFile** vous permet de spécifier l’accès en lecture/écriture du handle qu’il retourne.

La fonction [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) crée une mémoire tampon d’écran et retourne un handle. Ce handle peut être utilisé dans toutes les fonctions qui acceptent un handle vers la sortie de la console. La nouvelle mémoire tampon d’écran n’est pas active (affichée) tant que son handle n’est pas spécifié dans un appel à la fonction [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md). Notez que le fait de changer la mémoire tampon d’écran active n’affecte pas le handle retourné par [**GetStdHandle**](getstdhandle.md). De même, l’utilisation de [**SetStdHandle**](setstdhandle.md) pour modifier le handle `STDOUT` n’affecte pas la mémoire tampon d’écran active.

Les handles de console retournés par [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) et [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) peuvent être utilisés dans toutes les fonctions de console qui nécessitent un handle vers la mémoire tampon d’entrée ou la mémoire tampon d’écran d’une console. Les handles retournés par [**GetStdHandle**](getstdhandle.md) peuvent être utilisés par les fonctions de la console s’ils n’ont pas été redirigés pour référencer autre chose que les E/S de la console. Toutefois, si un handle standard a été redirigé pour référencer un fichier ou un canal, ce handle ne pourra être utilisé que par les fonctions [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) et [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile). [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype) peut aider à déterminer le type d’appareil que le handle référence. Un handle de console se présente ainsi : `FILE_TYPE_CHAR`.

Un processus peut utiliser la fonction [**DuplicateHandle**](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle) pour créer un handle de console dupliqué avec un accès ou un héritage différents de ceux du handle d’origine. Notez, toutefois, qu’un processus ne peut créer un handle de console dupliqué que pour sa propre utilisation. Cela diffère donc des autres types de handles (tels que les objets de fichier, de canal ou mutex), pour lesquels **DuplicateHandle** peut créer un doublon valide pour un processus différent.
L’accès à une console doit être partagé lors de la [création](creation-of-a-console.md) de l’autre processus, ou peut être demandé par l’autre processus par le biais du mécanisme [**AttachConsole**](attachconsole.md).

Pour fermer un handle de console, un processus peut utiliser la fonction [**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle).