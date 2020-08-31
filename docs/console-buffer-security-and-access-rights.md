---
title: Sécurité de la mémoire tampon de la console et droits d’accès
description: Le modèle de sécurité Windows vous permet de contrôler l’accès aux mémoires tampons d’entrée de la console et aux mémoires tampons d’écran de la console. Pour plus d’informations sur la sécurité, consultez modèle de contrôle d’accès.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_console\_buffer\_security\_and\_access\_rights'
- base.console\_buffer\_security\_and\_access\_rights
- consoles.console\_buffer\_security\_and\_access\_rights
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f9a50063-8fc8-4cd1-8f24-9ae3946d3119
ms.openlocfilehash: 63cfdb91f4ab9696ade81c7a15bc62e1c93ab6e3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059349"
---
# <a name="console-buffer-security-and-access-rights"></a><span data-ttu-id="feef3-105">Sécurité de la mémoire tampon de la console et droits d’accès</span><span class="sxs-lookup"><span data-stu-id="feef3-105">Console Buffer Security and Access Rights</span></span>


<span data-ttu-id="feef3-106">Le modèle de sécurité Windows vous permet de contrôler l’accès aux mémoires tampons d’entrée de la console et aux mémoires tampons d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="feef3-106">The Windows security model enables you to control access to console input buffers and console screen buffers.</span></span> <span data-ttu-id="feef3-107">Pour plus d’informations sur la sécurité, consultez [modèle de contrôle d’accès](https://msdn.microsoft.com/library/windows/desktop/aa374876).</span><span class="sxs-lookup"><span data-stu-id="feef3-107">For more information about security, see [Access-Control Model](https://msdn.microsoft.com/library/windows/desktop/aa374876).</span></span>

<span data-ttu-id="feef3-108">Vous pouvez spécifier un [descripteur de sécurité](https://msdn.microsoft.com/library/windows/desktop/aa379563) pour l’entrée de la console et des mémoires tampons d’écran de console lorsque vous appelez la fonction [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) ou [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="feef3-108">You can specify a [security descriptor](https://msdn.microsoft.com/library/windows/desktop/aa379563) for the console input and console screen buffers when you call the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) or [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) function.</span></span> <span data-ttu-id="feef3-109">Si vous spécifiez **null**, l’objet obtient un descripteur de sécurité par défaut.</span><span class="sxs-lookup"><span data-stu-id="feef3-109">If you specify **NULL**, the object gets a default security descriptor.</span></span> <span data-ttu-id="feef3-110">Les listes de contrôle d’accès dans le descripteur de sécurité par défaut pour une mémoire tampon de la console proviennent du jeton principal ou d’emprunt d’identité du créateur.</span><span class="sxs-lookup"><span data-stu-id="feef3-110">The ACLs in the default security descriptor for a console buffer come from the primary or impersonation token of the creator.</span></span>

<span data-ttu-id="feef3-111">Les handles retournés par [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)et [**GetStdHandle**](getstdhandle.md) ont les droits d’accès en \*\* \_ écriture\*\* **génériques et \_ en lecture** .</span><span class="sxs-lookup"><span data-stu-id="feef3-111">The handles returned by [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md), and [**GetStdHandle**](getstdhandle.md) have the **GENERIC\_READ** and **GENERIC\_WRITE** access rights.</span></span>

<span data-ttu-id="feef3-112">Les droits d’accès valides incluent les [droits d’accès](https://msdn.microsoft.com/library/windows/desktop/aa446632)génériques \*\* \_ en lecture et en\*\* \*\* \_ écriture\*\* génériques.</span><span class="sxs-lookup"><span data-stu-id="feef3-112">The valid access rights include the **GENERIC\_READ** and **GENERIC\_WRITE** [generic access rights](https://msdn.microsoft.com/library/windows/desktop/aa446632).</span></span>


| <span data-ttu-id="feef3-113">Value</span><span class="sxs-lookup"><span data-stu-id="feef3-113">Value</span></span>                            | <span data-ttu-id="feef3-114">Signification</span><span class="sxs-lookup"><span data-stu-id="feef3-114">Meaning</span></span>                                                                                               |
|----------------------------------|-------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="feef3-115">**Générique \_ LECTURE** (0x80000000L)</span><span class="sxs-lookup"><span data-stu-id="feef3-115">**GENERIC\_READ** (0x80000000L)</span></span>  | <span data-ttu-id="feef3-116">Demande l’accès en lecture à la mémoire tampon d’écran de la console, ce qui permet au processus de lire des données à partir de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="feef3-116">Requests read access to the console screen buffer, enabling the process to read data from the buffer.</span></span> |
| <span data-ttu-id="feef3-117">**Générique \_ ÉCRITURE** (0x40000000L)</span><span class="sxs-lookup"><span data-stu-id="feef3-117">**GENERIC\_WRITE** (0x40000000L)</span></span> | <span data-ttu-id="feef3-118">Demande l’accès en écriture à la mémoire tampon de l’écran de la console, ce qui permet au processus d’écrire des données dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="feef3-118">Requests write access to the console screen buffer, enabling the process to write data to the buffer.</span></span> |










