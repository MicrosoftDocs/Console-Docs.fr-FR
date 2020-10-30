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
# <a name="console-application-issues"></a><span data-ttu-id="18841-104">Problèmes des applications d’une console</span><span class="sxs-lookup"><span data-stu-id="18841-104">Console Application Issues</span></span>

<span data-ttu-id="18841-105">Les fonctions de console de 8 bits utilisent la page de codes OEM.</span><span class="sxs-lookup"><span data-stu-id="18841-105">The 8-bit console functions use the OEM code page.</span></span> <span data-ttu-id="18841-106">Toutes les autres fonctions utilisent la page de codes ANSI par défaut.</span><span class="sxs-lookup"><span data-stu-id="18841-106">All other functions use the ANSI code page by default.</span></span> <span data-ttu-id="18841-107">Cela signifie que les chaînes retournées par les fonctions de la console peuvent ne pas être traitées correctement par les autres fonctions et vice versa.</span><span class="sxs-lookup"><span data-stu-id="18841-107">This means that strings returned by the console functions may not be processed correctly by the other functions and vice versa.</span></span> <span data-ttu-id="18841-108">Par exemple, si **FindFirstFileA** retourne une chaîne qui contient certains caractères ANSI étendus, **WriteConsoleA** n’affichera pas correctement la chaîne.</span><span class="sxs-lookup"><span data-stu-id="18841-108">For example, if **FindFirstFileA** returns a string that contains certain extended ANSI characters, **WriteConsoleA** will not display the string properly.</span></span>

<span data-ttu-id="18841-109">La meilleure solution à long terme pour une application console consiste à utiliser **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** .</span><span class="sxs-lookup"><span data-stu-id="18841-109">The best long-term solution for a console application is to use **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** .</span></span> <span data-ttu-id="18841-110">La console accepte l’encodage UTF-16 sur la variante W des API ou l’encodage UTF-8 sur la variante A des API après avoir utilisé **[SetConsoleCP](setconsolecp.md)** et **[SetConsoleOutputCP](setconsoleoutputcp.md)** sur `65001` ( `CP_UTF8` constante) pour la page de codes UTF-8.</span><span class="sxs-lookup"><span data-stu-id="18841-110">The console will accept UTF-16 encoding on the W variant of the APIs or UTF-8 encoding on the A variant of the APIs after using **[SetConsoleCP](setconsolecp.md)** and **[SetConsoleOutputCP](setconsoleoutputcp.md)** to `65001` (`CP_UTF8` constant) for the UTF-8 code page.</span></span>

<span data-ttu-id="18841-111">En excluant cette solution, une application console doit utiliser la fonction [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) .</span><span class="sxs-lookup"><span data-stu-id="18841-111">Barring that solution, a console application should use the [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) function.</span></span> <span data-ttu-id="18841-112">Cette fonction modifie les fonctions de fichier pertinentes afin qu’elles produisent des chaînes de jeu de caractères OEM plutôt que des chaînes de jeu de caractères ANSI.</span><span class="sxs-lookup"><span data-stu-id="18841-112">That function changes relevant file functions so that they produce OEM character set strings rather than ANSI character set strings.</span></span>

<span data-ttu-id="18841-113">Les fonctions de fichiers sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="18841-113">The following are file functions:</span></span>

:::row:::
    :::column:::
        [<span data-ttu-id="18841-114">CopyFile</span><span class="sxs-lookup"><span data-stu-id="18841-114">CopyFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363851)  
        [<span data-ttu-id="18841-115">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="18841-115">CreateDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363855)  
        [<span data-ttu-id="18841-116">CreateFile</span><span class="sxs-lookup"><span data-stu-id="18841-116">CreateFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)  
        [<span data-ttu-id="18841-117">CreateProcess</span><span class="sxs-lookup"><span data-stu-id="18841-117">CreateProcess</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)  
        [<span data-ttu-id="18841-118">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="18841-118">DeleteFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363915)  
        [<span data-ttu-id="18841-119">FindFirstFile</span><span class="sxs-lookup"><span data-stu-id="18841-119">FindFirstFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364418)  
        [<span data-ttu-id="18841-120">FindNextFile</span><span class="sxs-lookup"><span data-stu-id="18841-120">FindNextFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364428)  
        [<span data-ttu-id="18841-121">GetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="18841-121">GetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364934)  
        [<span data-ttu-id="18841-122">GetDiskFreeSpace</span><span class="sxs-lookup"><span data-stu-id="18841-122">GetDiskFreeSpace</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364935)  
        [<span data-ttu-id="18841-123">GetDriveType</span><span class="sxs-lookup"><span data-stu-id="18841-123">GetDriveType</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364939)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="18841-124">GetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="18841-124">GetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364944)  
        [<span data-ttu-id="18841-125">GetFullPathName</span><span class="sxs-lookup"><span data-stu-id="18841-125">GetFullPathName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364963)  
        [<span data-ttu-id="18841-126">GetModuleFileName</span><span class="sxs-lookup"><span data-stu-id="18841-126">GetModuleFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683197)  
        [<span data-ttu-id="18841-127">Échec GetModuleHandle</span><span class="sxs-lookup"><span data-stu-id="18841-127">GetModuleHandle</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683199)  
        [<span data-ttu-id="18841-128">GetSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="18841-128">GetSystemDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724373)  
        [<span data-ttu-id="18841-129">GetTempFileName</span><span class="sxs-lookup"><span data-stu-id="18841-129">GetTempFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364991)  
        [<span data-ttu-id="18841-130">GetTempPath</span><span class="sxs-lookup"><span data-stu-id="18841-130">GetTempPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364992)  
        [<span data-ttu-id="18841-131">GetVolumeInformation</span><span class="sxs-lookup"><span data-stu-id="18841-131">GetVolumeInformation</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364993)  
        [<span data-ttu-id="18841-132">GetWindowsDirectory</span><span class="sxs-lookup"><span data-stu-id="18841-132">GetWindowsDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724454)  
        [<span data-ttu-id="18841-133">LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="18841-133">LoadLibrary</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684175)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="18841-134">LoadLibraryEx</span><span class="sxs-lookup"><span data-stu-id="18841-134">LoadLibraryEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684179)  
        [<span data-ttu-id="18841-135">MoveFile</span><span class="sxs-lookup"><span data-stu-id="18841-135">MoveFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365239)  
        [<span data-ttu-id="18841-136">MoveFileEx</span><span class="sxs-lookup"><span data-stu-id="18841-136">MoveFileEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365240)  
        [<span data-ttu-id="18841-137">OpenFile</span><span class="sxs-lookup"><span data-stu-id="18841-137">OpenFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365430)  
        [<span data-ttu-id="18841-138">RemoveDirectory</span><span class="sxs-lookup"><span data-stu-id="18841-138">RemoveDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365488)  
        [<span data-ttu-id="18841-139">SearchPath</span><span class="sxs-lookup"><span data-stu-id="18841-139">SearchPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365527)  
        [<span data-ttu-id="18841-140">SetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="18841-140">SetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365530)  
        [<span data-ttu-id="18841-141">SetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="18841-141">SetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365535)  
    :::column-end:::
:::row-end:::

<span data-ttu-id="18841-142">Lors du traitement des lignes de commande, une application console doit obtenir la ligne de commande au format Unicode et la convertir au format OEM, à l’aide des fonctions de conversion de caractères en OEM appropriées.</span><span class="sxs-lookup"><span data-stu-id="18841-142">When dealing with command lines, a console application should obtain the command line in Unicode form and convert it to OEM form, using the relevant character-to-OEM functions.</span></span> <span data-ttu-id="18841-143">Notez également que *argv* utilise le jeu de caractères ANSI.</span><span class="sxs-lookup"><span data-stu-id="18841-143">Note, also, that *argv* uses the ANSI character set.</span></span>
