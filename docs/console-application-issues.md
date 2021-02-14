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
ms.openlocfilehash: e81a2b8f6e3b7ba17a7fd704aac868425c86d52c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358269"
---
# <a name="console-application-issues"></a>Problèmes des applications d’une console

Les fonctions de console de 8 bits utilisent la page de codes OEM. Toutes les autres fonctions utilisent la page de codes ANSI par défaut. Cela signifie que les chaînes retournées par les fonctions de la console peuvent ne pas être traitées correctement par les autres fonctions et vice versa. Par exemple, si **FindFirstFileA** retourne une chaîne qui contient certains caractères ANSI étendus, **WriteConsoleA** n’affichera pas correctement la chaîne.

La meilleure solution à long terme pour une application console consiste à utiliser **[Unicode](/windows/win32/intl/unicode)**. La console accepte l’encodage UTF-16 sur la variante W des API ou l’encodage UTF-8 sur la variante A des API après avoir utilisé **[SetConsoleCP](setconsolecp.md)** et **[SetConsoleOutputCP](setconsoleoutputcp.md)** sur `65001` ( `CP_UTF8` constante) pour la page de codes UTF-8.

En excluant cette solution, une application console doit utiliser la fonction [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) . Cette fonction modifie les fonctions de fichier pertinentes afin qu’elles produisent des chaînes de jeu de caractères OEM plutôt que des chaînes de jeu de caractères ANSI.

Les fonctions de fichiers sont les suivantes :

:::row:::
    :::column:::
        [CopyFile](/windows/win32/api/winbase/nf-winbase-copyfile)  
        [CreateDirectory](/windows/win32/api/fileapi/nf-fileapi-createdirectorya)  
        [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilea)  
        [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)  
        [DeleteFile](/windows/win32/api/fileapi/nf-fileapi-deletefilea)  
        [FindFirstFile](/windows/win32/api/fileapi/nf-fileapi-findfirstfilea)  
        [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilea)  
        [GetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-getcurrentdirectory)  
        [GetDiskFreeSpace](/windows/win32/api/fileapi/nf-fileapi-getdiskfreespacea)  
        [GetDriveType](/windows/win32/api/fileapi/nf-fileapi-getdrivetypea)  
    :::column-end:::
    :::column:::
        [GetFileAttributes](/windows/win32/api/fileapi/nf-fileapi-getfileattributesa)  
        [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamea)  
        [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamea)  
        [Échec GetModuleHandle](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulehandlea)  
        [GetSystemDirectory](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemdirectorya)  
        [GetTempFileName](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamea)  
        [GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppatha)  
        [GetVolumeInformation](/windows/win32/api/fileapi/nf-fileapi-getvolumeinformationa)  
        [GetWindowsDirectory](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getwindowsdirectorya)  
        [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibrarya)  
    :::column-end:::
    :::column:::
        [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa)  
        [MoveFile](/windows/win32/api/winbase/nf-winbase-movefile)  
        [MoveFileEx](/windows/win32/api/winbase/nf-winbase-movefileexa)  
        [OpenFile](/windows/win32/api/winbase/nf-winbase-openfile)  
        [RemoveDirectory](/windows/win32/api/fileapi/nf-fileapi-removedirectorya)  
        [SearchPath](/windows/win32/api/processenv/nf-processenv-searchpatha)  
        [SetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory)  
        [SetFileAttributes](/windows/win32/api/fileapi/nf-fileapi-setfileattributesa)  
    :::column-end:::
:::row-end:::

Lors du traitement des lignes de commande, une application console doit obtenir la ligne de commande au format Unicode et la convertir au format OEM, à l’aide des fonctions de conversion de caractères en OEM appropriées. Notez également que *argv* utilise le jeu de caractères ANSI.