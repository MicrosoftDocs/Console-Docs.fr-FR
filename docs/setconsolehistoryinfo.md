---
title: SetConsoleHistoryInfo fonction)
description: Définit les paramètres de l’historique pour la console Windows du processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/SetConsoleHistoryInfo
- wincon/SetConsoleHistoryInfo
- SetConsoleHistoryInfo
MS-HAID:
- base.setconsolehistoryinfo
- consoles.setconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: db180f53-aa3c-4a91-bc3e-9f3f0bb7ab01
topic_type:
- apiref
api_name:
- SetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: bf194e154a06efc32510fe811ab89877e283e142
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059100"
---
# <a name="setconsolehistoryinfo-function"></a><span data-ttu-id="3129f-104">SetConsoleHistoryInfo fonction)</span><span class="sxs-lookup"><span data-stu-id="3129f-104">SetConsoleHistoryInfo function</span></span>


<span data-ttu-id="3129f-105">Définit les paramètres de l’historique pour la console du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="3129f-105">Sets the history settings for the calling process's console.</span></span>

<a name="syntax"></a><span data-ttu-id="3129f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3129f-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleHistoryInfo(
  _In_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

<a name="parameters"></a><span data-ttu-id="3129f-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3129f-107">Parameters</span></span>
----------

<span data-ttu-id="3129f-108">*lpConsoleHistoryInfo* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="3129f-108">*lpConsoleHistoryInfo* \[in\]</span></span>  
<span data-ttu-id="3129f-109">Pointeur vers une structure [**d' \_ \_ informations d’historique**](console-history-info.md) de la console qui contient les paramètres d’historique de la console du processus.</span><span class="sxs-lookup"><span data-stu-id="3129f-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that contains the history settings for the process's console.</span></span>

<a name="return-value"></a><span data-ttu-id="3129f-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="3129f-110">Return value</span></span>
------------

<span data-ttu-id="3129f-111">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="3129f-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="3129f-112">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="3129f-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="3129f-113">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="3129f-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="3129f-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="3129f-114">Remarks</span></span>
-------

<span data-ttu-id="3129f-115">Si le processus appelant n’est pas un processus de console, la fonction échoue et définit le dernier code d’erreur sur **erreur \_ accès \_ refusé**.</span><span class="sxs-lookup"><span data-stu-id="3129f-115">If the calling process is not a console process, the function fails and sets the last error code to **ERROR\_ACCESS\_DENIED**.</span></span>

<a name="requirements"></a><span data-ttu-id="3129f-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3129f-116">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="3129f-117">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="3129f-117">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="3129f-118">Windows Vista [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="3129f-118">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3129f-119">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="3129f-119">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="3129f-120">Windows Server 2008 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="3129f-120">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3129f-121">En-tête</span><span class="sxs-lookup"><span data-stu-id="3129f-121">Header</span></span></p></td>
<td><span data-ttu-id="3129f-122">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="3129f-122">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3129f-123">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="3129f-123">Library</span></span></p></td>
<td><span data-ttu-id="3129f-124">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="3129f-124">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3129f-125">DLL</span><span class="sxs-lookup"><span data-stu-id="3129f-125">DLL</span></span></p></td>
<td><span data-ttu-id="3129f-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3129f-126">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="3129f-127"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3129f-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="3129f-128">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="3129f-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3129f-129">**\_informations sur l’historique de la console \_**</span><span class="sxs-lookup"><span data-stu-id="3129f-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="3129f-130">**GetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="3129f-130">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)

 

 




