---
title: Problèmes liés aux applications console
description: Examinez les problèmes de l’application console, tels que les fonctions qui acceptent ou retournent des chaînes de jeu de caractères OEM et les fonctions qui acceptent ou retournent des chaînes de jeu de caractères ANSI.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_console\_application\_issues'
- base.console\_application\_issues
- consoles.console\_application\_issues
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a561fbdd-b50d-4687-92d7-735377a7991d
ms.openlocfilehash: 4bf0d6792a991d8ae141ec0b1b9c940311e00ab9
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059353"
---
# <a name="console-application-issues"></a><span data-ttu-id="6dd48-104">Problèmes liés aux applications console</span><span class="sxs-lookup"><span data-stu-id="6dd48-104">Console Application Issues</span></span>

<span data-ttu-id="6dd48-105">Les fonctions de console de 8 bits utilisent la page de codes OEM.</span><span class="sxs-lookup"><span data-stu-id="6dd48-105">The 8-bit console functions use the OEM code page.</span></span> <span data-ttu-id="6dd48-106">Toutes les autres fonctions utilisent la page de codes ANSI par défaut.</span><span class="sxs-lookup"><span data-stu-id="6dd48-106">All other functions use the ANSI code page by default.</span></span> <span data-ttu-id="6dd48-107">Cela signifie que les chaînes retournées par les fonctions de la console peuvent ne pas être traitées correctement par les autres fonctions et vice versa.</span><span class="sxs-lookup"><span data-stu-id="6dd48-107">This means that strings returned by the console functions may not be processed correctly by the other functions and vice versa.</span></span> <span data-ttu-id="6dd48-108">Par exemple, si **FindFirstFileA** retourne une chaîne qui contient certains caractères ANSI étendus, **WriteConsoleA** n’affichera pas correctement la chaîne.</span><span class="sxs-lookup"><span data-stu-id="6dd48-108">For example, if **FindFirstFileA** returns a string that contains certain extended ANSI characters, **WriteConsoleA** will not display the string properly.</span></span>

<span data-ttu-id="6dd48-109">La meilleure solution à long terme pour une application console consiste à utiliser Unicode.</span><span class="sxs-lookup"><span data-stu-id="6dd48-109">The best long-term solution for a console application is to use Unicode.</span></span> <span data-ttu-id="6dd48-110">En excluant cette solution, une application console doit utiliser la fonction [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) .</span><span class="sxs-lookup"><span data-stu-id="6dd48-110">Barring that solution, a console application should use the [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) function.</span></span> <span data-ttu-id="6dd48-111">Cette fonction modifie les fonctions de fichier pertinentes afin qu’elles produisent des chaînes de jeu de caractères OEM plutôt que des chaînes de jeu de caractères ANSI.</span><span class="sxs-lookup"><span data-stu-id="6dd48-111">That function changes relevant file functions so that they produce OEM character set strings rather than ANSI character set strings.</span></span>

<span data-ttu-id="6dd48-112">Les fonctions de fichiers sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6dd48-112">The following are file functions:</span></span>

:::row:::
    :::column:::
        [<span data-ttu-id="6dd48-113">CopyFile</span><span class="sxs-lookup"><span data-stu-id="6dd48-113">CopyFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363851)  
        [<span data-ttu-id="6dd48-114">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="6dd48-114">CreateDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363855)  
        [<span data-ttu-id="6dd48-115">CreateFile</span><span class="sxs-lookup"><span data-stu-id="6dd48-115">CreateFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)  
        [<span data-ttu-id="6dd48-116">CreateProcess</span><span class="sxs-lookup"><span data-stu-id="6dd48-116">CreateProcess</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)  
        [<span data-ttu-id="6dd48-117">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="6dd48-117">DeleteFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363915)  
        [<span data-ttu-id="6dd48-118">FindFirstFile</span><span class="sxs-lookup"><span data-stu-id="6dd48-118">FindFirstFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364418)  
        [<span data-ttu-id="6dd48-119">FindNextFile</span><span class="sxs-lookup"><span data-stu-id="6dd48-119">FindNextFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364428)  
        [<span data-ttu-id="6dd48-120">GetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="6dd48-120">GetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364934)  
        [<span data-ttu-id="6dd48-121">GetDiskFreeSpace</span><span class="sxs-lookup"><span data-stu-id="6dd48-121">GetDiskFreeSpace</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364935)  
        [<span data-ttu-id="6dd48-122">GetDriveType</span><span class="sxs-lookup"><span data-stu-id="6dd48-122">GetDriveType</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364939)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="6dd48-123">GetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="6dd48-123">GetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364944)  
        [<span data-ttu-id="6dd48-124">GetFullPathName</span><span class="sxs-lookup"><span data-stu-id="6dd48-124">GetFullPathName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364963)  
        [<span data-ttu-id="6dd48-125">GetModuleFileName</span><span class="sxs-lookup"><span data-stu-id="6dd48-125">GetModuleFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683197)  
        [<span data-ttu-id="6dd48-126">Échec GetModuleHandle</span><span class="sxs-lookup"><span data-stu-id="6dd48-126">GetModuleHandle</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683199)  
        [<span data-ttu-id="6dd48-127">GetSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="6dd48-127">GetSystemDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724373)  
        [<span data-ttu-id="6dd48-128">GetTempFileName</span><span class="sxs-lookup"><span data-stu-id="6dd48-128">GetTempFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364991)  
        [<span data-ttu-id="6dd48-129">GetTempPath</span><span class="sxs-lookup"><span data-stu-id="6dd48-129">GetTempPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364992)  
        [<span data-ttu-id="6dd48-130">GetVolumeInformation</span><span class="sxs-lookup"><span data-stu-id="6dd48-130">GetVolumeInformation</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364993)  
        [<span data-ttu-id="6dd48-131">GetWindowsDirectory</span><span class="sxs-lookup"><span data-stu-id="6dd48-131">GetWindowsDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724454)  
        [<span data-ttu-id="6dd48-132">LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="6dd48-132">LoadLibrary</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684175)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="6dd48-133">LoadLibraryEx</span><span class="sxs-lookup"><span data-stu-id="6dd48-133">LoadLibraryEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684179)  
        [<span data-ttu-id="6dd48-134">MoveFile</span><span class="sxs-lookup"><span data-stu-id="6dd48-134">MoveFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365239)  
        [<span data-ttu-id="6dd48-135">MoveFileEx</span><span class="sxs-lookup"><span data-stu-id="6dd48-135">MoveFileEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365240)  
        [<span data-ttu-id="6dd48-136">OpenFile</span><span class="sxs-lookup"><span data-stu-id="6dd48-136">OpenFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365430)  
        [<span data-ttu-id="6dd48-137">RemoveDirectory</span><span class="sxs-lookup"><span data-stu-id="6dd48-137">RemoveDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365488)  
        [<span data-ttu-id="6dd48-138">SearchPath</span><span class="sxs-lookup"><span data-stu-id="6dd48-138">SearchPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365527)  
        [<span data-ttu-id="6dd48-139">SetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="6dd48-139">SetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365530)  
        [<span data-ttu-id="6dd48-140">SetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="6dd48-140">SetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365535)  
    :::column-end:::
:::row-end:::

<span data-ttu-id="6dd48-141">Lors du traitement des lignes de commande, une application console doit obtenir la ligne de commande au format Unicode et la convertir au format OEM, à l’aide des fonctions de conversion de caractères en OEM appropriées.</span><span class="sxs-lookup"><span data-stu-id="6dd48-141">When dealing with command lines, a console application should obtain the command line in Unicode form and convert it to OEM form, using the relevant character-to-OEM functions.</span></span> <span data-ttu-id="6dd48-142">Notez également que *argv* utilise le jeu de caractères ANSI.</span><span class="sxs-lookup"><span data-stu-id="6dd48-142">Note, also, that *argv* uses the ANSI character set.</span></span>
