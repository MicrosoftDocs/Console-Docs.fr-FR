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
# <a name="console-application-issues"></a><span data-ttu-id="a6660-104">Problèmes des applications d’une console</span><span class="sxs-lookup"><span data-stu-id="a6660-104">Console Application Issues</span></span>

<span data-ttu-id="a6660-105">Les fonctions de console de 8 bits utilisent la page de codes OEM.</span><span class="sxs-lookup"><span data-stu-id="a6660-105">The 8-bit console functions use the OEM code page.</span></span> <span data-ttu-id="a6660-106">Toutes les autres fonctions utilisent la page de codes ANSI par défaut.</span><span class="sxs-lookup"><span data-stu-id="a6660-106">All other functions use the ANSI code page by default.</span></span> <span data-ttu-id="a6660-107">Cela signifie que les chaînes retournées par les fonctions de la console peuvent ne pas être traitées correctement par les autres fonctions et vice versa.</span><span class="sxs-lookup"><span data-stu-id="a6660-107">This means that strings returned by the console functions may not be processed correctly by the other functions and vice versa.</span></span> <span data-ttu-id="a6660-108">Par exemple, si **FindFirstFileA** retourne une chaîne qui contient certains caractères ANSI étendus, **WriteConsoleA** n’affichera pas correctement la chaîne.</span><span class="sxs-lookup"><span data-stu-id="a6660-108">For example, if **FindFirstFileA** returns a string that contains certain extended ANSI characters, **WriteConsoleA** will not display the string properly.</span></span>

<span data-ttu-id="a6660-109">La meilleure solution à long terme pour une application console consiste à utiliser **[Unicode](/windows/win32/intl/unicode)**.</span><span class="sxs-lookup"><span data-stu-id="a6660-109">The best long-term solution for a console application is to use **[Unicode](/windows/win32/intl/unicode)**.</span></span> <span data-ttu-id="a6660-110">La console accepte l’encodage UTF-16 sur la variante W des API ou l’encodage UTF-8 sur la variante A des API après avoir utilisé **[SetConsoleCP](setconsolecp.md)** et **[SetConsoleOutputCP](setconsoleoutputcp.md)** sur `65001` ( `CP_UTF8` constante) pour la page de codes UTF-8.</span><span class="sxs-lookup"><span data-stu-id="a6660-110">The console will accept UTF-16 encoding on the W variant of the APIs or UTF-8 encoding on the A variant of the APIs after using **[SetConsoleCP](setconsolecp.md)** and **[SetConsoleOutputCP](setconsoleoutputcp.md)** to `65001` (`CP_UTF8` constant) for the UTF-8 code page.</span></span>

<span data-ttu-id="a6660-111">En excluant cette solution, une application console doit utiliser la fonction [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) .</span><span class="sxs-lookup"><span data-stu-id="a6660-111">Barring that solution, a console application should use the [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) function.</span></span> <span data-ttu-id="a6660-112">Cette fonction modifie les fonctions de fichier pertinentes afin qu’elles produisent des chaînes de jeu de caractères OEM plutôt que des chaînes de jeu de caractères ANSI.</span><span class="sxs-lookup"><span data-stu-id="a6660-112">That function changes relevant file functions so that they produce OEM character set strings rather than ANSI character set strings.</span></span>

<span data-ttu-id="a6660-113">Les fonctions de fichiers sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a6660-113">The following are file functions:</span></span>

:::row:::
    :::column:::
        [<span data-ttu-id="a6660-114">CopyFile</span><span class="sxs-lookup"><span data-stu-id="a6660-114">CopyFile</span></span>](/windows/win32/api/winbase/nf-winbase-copyfile)  
        [<span data-ttu-id="a6660-115">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="a6660-115">CreateDirectory</span></span>](/windows/win32/api/fileapi/nf-fileapi-createdirectorya)  
        [<span data-ttu-id="a6660-116">CreateFile</span><span class="sxs-lookup"><span data-stu-id="a6660-116">CreateFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-createfilea)  
        [<span data-ttu-id="a6660-117">CreateProcess</span><span class="sxs-lookup"><span data-stu-id="a6660-117">CreateProcess</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)  
        [<span data-ttu-id="a6660-118">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="a6660-118">DeleteFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-deletefilea)  
        [<span data-ttu-id="a6660-119">FindFirstFile</span><span class="sxs-lookup"><span data-stu-id="a6660-119">FindFirstFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-findfirstfilea)  
        [<span data-ttu-id="a6660-120">FindNextFile</span><span class="sxs-lookup"><span data-stu-id="a6660-120">FindNextFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-findnextfilea)  
        [<span data-ttu-id="a6660-121">GetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="a6660-121">GetCurrentDirectory</span></span>](/windows/win32/api/winbase/nf-winbase-getcurrentdirectory)  
        [<span data-ttu-id="a6660-122">GetDiskFreeSpace</span><span class="sxs-lookup"><span data-stu-id="a6660-122">GetDiskFreeSpace</span></span>](/windows/win32/api/fileapi/nf-fileapi-getdiskfreespacea)  
        [<span data-ttu-id="a6660-123">GetDriveType</span><span class="sxs-lookup"><span data-stu-id="a6660-123">GetDriveType</span></span>](/windows/win32/api/fileapi/nf-fileapi-getdrivetypea)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="a6660-124">GetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="a6660-124">GetFileAttributes</span></span>](/windows/win32/api/fileapi/nf-fileapi-getfileattributesa)  
        [<span data-ttu-id="a6660-125">GetFullPathName</span><span class="sxs-lookup"><span data-stu-id="a6660-125">GetFullPathName</span></span>](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamea)  
        [<span data-ttu-id="a6660-126">GetModuleFileName</span><span class="sxs-lookup"><span data-stu-id="a6660-126">GetModuleFileName</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamea)  
        [<span data-ttu-id="a6660-127">Échec GetModuleHandle</span><span class="sxs-lookup"><span data-stu-id="a6660-127">GetModuleHandle</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulehandlea)  
        [<span data-ttu-id="a6660-128">GetSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="a6660-128">GetSystemDirectory</span></span>](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemdirectorya)  
        [<span data-ttu-id="a6660-129">GetTempFileName</span><span class="sxs-lookup"><span data-stu-id="a6660-129">GetTempFileName</span></span>](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamea)  
        [<span data-ttu-id="a6660-130">GetTempPath</span><span class="sxs-lookup"><span data-stu-id="a6660-130">GetTempPath</span></span>](/windows/win32/api/fileapi/nf-fileapi-gettemppatha)  
        [<span data-ttu-id="a6660-131">GetVolumeInformation</span><span class="sxs-lookup"><span data-stu-id="a6660-131">GetVolumeInformation</span></span>](/windows/win32/api/fileapi/nf-fileapi-getvolumeinformationa)  
        [<span data-ttu-id="a6660-132">GetWindowsDirectory</span><span class="sxs-lookup"><span data-stu-id="a6660-132">GetWindowsDirectory</span></span>](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getwindowsdirectorya)  
        [<span data-ttu-id="a6660-133">LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="a6660-133">LoadLibrary</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibrarya)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="a6660-134">LoadLibraryEx</span><span class="sxs-lookup"><span data-stu-id="a6660-134">LoadLibraryEx</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa)  
        [<span data-ttu-id="a6660-135">MoveFile</span><span class="sxs-lookup"><span data-stu-id="a6660-135">MoveFile</span></span>](/windows/win32/api/winbase/nf-winbase-movefile)  
        [<span data-ttu-id="a6660-136">MoveFileEx</span><span class="sxs-lookup"><span data-stu-id="a6660-136">MoveFileEx</span></span>](/windows/win32/api/winbase/nf-winbase-movefileexa)  
        [<span data-ttu-id="a6660-137">OpenFile</span><span class="sxs-lookup"><span data-stu-id="a6660-137">OpenFile</span></span>](/windows/win32/api/winbase/nf-winbase-openfile)  
        [<span data-ttu-id="a6660-138">RemoveDirectory</span><span class="sxs-lookup"><span data-stu-id="a6660-138">RemoveDirectory</span></span>](/windows/win32/api/fileapi/nf-fileapi-removedirectorya)  
        [<span data-ttu-id="a6660-139">SearchPath</span><span class="sxs-lookup"><span data-stu-id="a6660-139">SearchPath</span></span>](/windows/win32/api/processenv/nf-processenv-searchpatha)  
        [<span data-ttu-id="a6660-140">SetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="a6660-140">SetCurrentDirectory</span></span>](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory)  
        [<span data-ttu-id="a6660-141">SetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="a6660-141">SetFileAttributes</span></span>](/windows/win32/api/fileapi/nf-fileapi-setfileattributesa)  
    :::column-end:::
:::row-end:::

<span data-ttu-id="a6660-142">Lors du traitement des lignes de commande, une application console doit obtenir la ligne de commande au format Unicode et la convertir au format OEM, à l’aide des fonctions de conversion de caractères en OEM appropriées.</span><span class="sxs-lookup"><span data-stu-id="a6660-142">When dealing with command lines, a console application should obtain the command line in Unicode form and convert it to OEM form, using the relevant character-to-OEM functions.</span></span> <span data-ttu-id="a6660-143">Notez également que *argv* utilise le jeu de caractères ANSI.</span><span class="sxs-lookup"><span data-stu-id="a6660-143">Note, also, that *argv* uses the ANSI character set.</span></span>