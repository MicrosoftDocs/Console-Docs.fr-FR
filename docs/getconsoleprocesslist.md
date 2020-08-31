---
title: GetConsoleProcessList fonction)
description: Consultez les informations de référence sur la fonction GetConsoleProcessList, qui récupère une liste des processus attachés à la console actuelle.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetConsoleProcessList
- wincon/GetConsoleProcessList
- GetConsoleProcessList
MS-HAID:
- '\_win32\_getconsoleprocesslist'
- base.getconsoleprocesslist
- consoles.getconsoleprocesslist
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3d21103b-662d-4393-ae3f-773cd9e4a930
topic_type:
- apiref
api_name:
- GetConsoleProcessList
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 5b032754172886fd83a8152caeb5e2228b917930
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059157"
---
# <a name="getconsoleprocesslist-function"></a><span data-ttu-id="bc738-104">GetConsoleProcessList fonction)</span><span class="sxs-lookup"><span data-stu-id="bc738-104">GetConsoleProcessList function</span></span>


<span data-ttu-id="bc738-105">Récupère une liste des processus attachés à la console actuelle.</span><span class="sxs-lookup"><span data-stu-id="bc738-105">Retrieves a list of the processes attached to the current console.</span></span>

<a name="syntax"></a><span data-ttu-id="bc738-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc738-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleProcessList(
  _Out_ LPDWORD lpdwProcessList,
  _In_  DWORD   dwProcessCount
);
```

<a name="parameters"></a><span data-ttu-id="bc738-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bc738-107">Parameters</span></span>
----------

<span data-ttu-id="bc738-108">*lpdwProcessList* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="bc738-108">*lpdwProcessList* \[out\]</span></span>  
<span data-ttu-id="bc738-109">Pointeur vers une mémoire tampon qui reçoit un tableau d’identificateurs de processus en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="bc738-109">A pointer to a buffer that receives an array of process identifiers upon success.</span></span> <span data-ttu-id="bc738-110">Il doit s’agir d’une mémoire tampon valide qui ne peut pas être `NULL` .</span><span class="sxs-lookup"><span data-stu-id="bc738-110">This must be a valid buffer and cannot be `NULL`.</span></span> <span data-ttu-id="bc738-111">La mémoire tampon doit avoir un espace pour recevoir au moins 1 ID de processus retourné.</span><span class="sxs-lookup"><span data-stu-id="bc738-111">The buffer must have space to receive at least 1 returned process id.</span></span>

<span data-ttu-id="bc738-112">*dwProcessCount* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="bc738-112">*dwProcessCount* \[in\]</span></span>  
<span data-ttu-id="bc738-113">Nombre maximal d’identificateurs de processus qui peuvent être stockés dans la mémoire tampon *lpdwProcessList* .</span><span class="sxs-lookup"><span data-stu-id="bc738-113">The maximum number of process identifiers that can be stored in the *lpdwProcessList* buffer.</span></span> <span data-ttu-id="bc738-114">La valeur doit être supérieure à 0.</span><span class="sxs-lookup"><span data-stu-id="bc738-114">This must be greater than 0.</span></span>

<a name="return-value"></a><span data-ttu-id="bc738-115">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="bc738-115">Return value</span></span>
------------

<span data-ttu-id="bc738-116">Si la fonction est réussie, la valeur de retour est inférieure ou égale à *dwProcessCount* et représente le nombre d’identificateurs de processus stockés dans la mémoire tampon *lpdwProcessList* .</span><span class="sxs-lookup"><span data-stu-id="bc738-116">If the function succeeds, the return value is less than or equal to *dwProcessCount* and represents the number of process identifiers stored in the *lpdwProcessList* buffer.</span></span>

<span data-ttu-id="bc738-117">Si la mémoire tampon est trop petite pour contenir tous les identificateurs de processus valides, la valeur de retour est le nombre requis d’éléments de tableau.</span><span class="sxs-lookup"><span data-stu-id="bc738-117">If the buffer is too small to hold all the valid process identifiers, the return value is the required number of array elements.</span></span> <span data-ttu-id="bc738-118">La fonction n’a stocké aucun identificateur dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="bc738-118">The function will have stored no identifiers in the buffer.</span></span> <span data-ttu-id="bc738-119">Dans ce cas, utilisez la valeur de retour pour allouer une mémoire tampon suffisamment grande pour stocker la liste entière et appeler à nouveau la fonction.</span><span class="sxs-lookup"><span data-stu-id="bc738-119">In this situation, use the return value to allocate a buffer that is large enough to store the entire list and call the function again.</span></span>

<span data-ttu-id="bc738-120">Si la valeur de retour est égale à zéro, la fonction a échoué, car chaque console a au moins un processus associé.</span><span class="sxs-lookup"><span data-stu-id="bc738-120">If the return value is zero, the function has failed, because every console has at least one process associated with it.</span></span> <span data-ttu-id="bc738-121">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="bc738-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="bc738-122">Si une `NULL` liste de processus a été fournie ou si le nombre de processus est égal à 0, l’appel retourne 0 et `GetLastError` retourne `ERROR_INVALID_PARAMETER` .</span><span class="sxs-lookup"><span data-stu-id="bc738-122">If a `NULL` process list was provided or the process count was 0, the call will return 0 and `GetLastError` will return `ERROR_INVALID_PARAMETER`.</span></span> <span data-ttu-id="bc738-123">Indiquez une mémoire tampon d’au moins un élément pour appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="bc738-123">Please provide a buffer of at least one element to call this function.</span></span> <span data-ttu-id="bc738-124">Allouez une mémoire tampon plus grande et rappelez si le code de retour est plus grand que la longueur de la mémoire tampon fournie.</span><span class="sxs-lookup"><span data-stu-id="bc738-124">Allocate a larger buffer and call again if the return code is larger than the length of the provided buffer.</span></span>

<a name="remarks"></a><span data-ttu-id="bc738-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="bc738-125">Remarks</span></span>
-------

<span data-ttu-id="bc738-126">Pour compiler une application qui utilise cette fonction, définissez \*\* \_ Win32 \_ winnt\*\* comme 0x0501 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="bc738-126">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="bc738-127">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="bc738-127">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="bc738-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bc738-128">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="bc738-129">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="bc738-129">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="bc738-130">Windows XP [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="bc738-130">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bc738-131">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="bc738-131">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="bc738-132">Windows Server 2003 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="bc738-132">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bc738-133">En-tête</span><span class="sxs-lookup"><span data-stu-id="bc738-133">Header</span></span></p></td>
<td><span data-ttu-id="bc738-134">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="bc738-134">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bc738-135">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="bc738-135">Library</span></span></p></td>
<td><span data-ttu-id="bc738-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="bc738-136">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bc738-137">DLL</span><span class="sxs-lookup"><span data-stu-id="bc738-137">DLL</span></span></p></td>
<td><span data-ttu-id="bc738-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="bc738-138">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="bc738-139"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc738-139"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="bc738-140">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="bc738-140">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="bc738-141">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="bc738-141">Console Functions</span></span>](console-functions.md)

 

 




