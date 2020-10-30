---
title: Problèmes des applications d’une console
description: Examinez les problèmes de l’application console, tels que les fonctions qui acceptent ou retournent des chaînes de jeu de caractères OEM et les fonctions qui acceptent ou retournent des chaînes de jeu de caractères ANSI.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_console\_application\_issues'
- base.console\_application\_issues
- consoles.console\_application\_issues
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a561fbdd-b50d-4687-92d7-735377a7991d
ms.openlocfilehash: a1e49e605d1379984ebff7d1737db5ef96c4ff0f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038457"
---
# <a name="console-application-issues"></a>Problèmes des applications d’une console

Les fonctions de console de 8 bits utilisent la page de codes OEM. Toutes les autres fonctions utilisent la page de codes ANSI par défaut. Cela signifie que les chaînes retournées par les fonctions de la console peuvent ne pas être traitées correctement par les autres fonctions et vice versa. Par exemple, si **FindFirstFileA** retourne une chaîne qui contient certains caractères ANSI étendus, **WriteConsoleA** n’affichera pas correctement la chaîne.

La meilleure solution à long terme pour une application console consiste à utiliser **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** . La console accepte l’encodage UTF-16 sur la variante W des API ou l’encodage UTF-8 sur la variante A des API après avoir utilisé **[SetConsoleCP](setconsolecp.md)** et **[SetConsoleOutputCP](setconsoleoutputcp.md)** sur `65001` ( `CP_UTF8` constante) pour la page de codes UTF-8.

En excluant cette solution, une application console doit utiliser la fonction [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) . Cette fonction modifie les fonctions de fichier pertinentes afin qu’elles produisent des chaînes de jeu de caractères OEM plutôt que des chaînes de jeu de caractères ANSI.

Les fonctions de fichiers sont les suivantes :

:::row:::
    :::column:::
        [CopyFile](https://msdn.microsoft.com/library/windows/desktop/aa363851)  
        [CreateDirectory](https://msdn.microsoft.com/library/windows/desktop/aa363855)  
        [CreateFile](https://msdn.microsoft.com/library/windows/desktop/aa363858)  
        [CreateProcess](https://msdn.microsoft.com/library/windows/desktop/ms682425)  
        [DeleteFile](https://msdn.microsoft.com/library/windows/desktop/aa363915)  
        [FindFirstFile](https://msdn.microsoft.com/library/windows/desktop/aa364418)  
        [FindNextFile](https://msdn.microsoft.com/library/windows/desktop/aa364428)  
        [GetCurrentDirectory](https://msdn.microsoft.com/library/windows/desktop/aa364934)  
        [GetDiskFreeSpace](https://msdn.microsoft.com/library/windows/desktop/aa364935)  
        [GetDriveType](https://msdn.microsoft.com/library/windows/desktop/aa364939)  
    :::column-end:::
    :::column:::
        [GetFileAttributes](https://msdn.microsoft.com/library/windows/desktop/aa364944)  
        [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963)  
        [GetModuleFileName](https://msdn.microsoft.com/library/windows/desktop/ms683197)  
        [Échec GetModuleHandle](https://msdn.microsoft.com/library/windows/desktop/ms683199)  
        [GetSystemDirectory](https://msdn.microsoft.com/library/windows/desktop/ms724373)  
        [GetTempFileName](https://msdn.microsoft.com/library/windows/desktop/aa364991)  
        [GetTempPath](https://msdn.microsoft.com/library/windows/desktop/aa364992)  
        [GetVolumeInformation](https://msdn.microsoft.com/library/windows/desktop/aa364993)  
        [GetWindowsDirectory](https://msdn.microsoft.com/library/windows/desktop/ms724454)  
        [LoadLibrary](https://msdn.microsoft.com/library/windows/desktop/ms684175)  
    :::column-end:::
    :::column:::
        [LoadLibraryEx](https://msdn.microsoft.com/library/windows/desktop/ms684179)  
        [MoveFile](https://msdn.microsoft.com/library/windows/desktop/aa365239)  
        [MoveFileEx](https://msdn.microsoft.com/library/windows/desktop/aa365240)  
        [OpenFile](https://msdn.microsoft.com/library/windows/desktop/aa365430)  
        [RemoveDirectory](https://msdn.microsoft.com/library/windows/desktop/aa365488)  
        [SearchPath](https://msdn.microsoft.com/library/windows/desktop/aa365527)  
        [SetCurrentDirectory](https://msdn.microsoft.com/library/windows/desktop/aa365530)  
        [SetFileAttributes](https://msdn.microsoft.com/library/windows/desktop/aa365535)  
    :::column-end:::
:::row-end:::

Lors du traitement des lignes de commande, une application console doit obtenir la ligne de commande au format Unicode et la convertir au format OEM, à l’aide des fonctions de conversion de caractères en OEM appropriées. Notez également que *argv* utilise le jeu de caractères ANSI.
