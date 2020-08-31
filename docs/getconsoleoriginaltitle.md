---
title: GetConsoleOriginalTitle fonction)
description: Consultez les informations de référence sur la fonction GetConsoleOriginalTitle, qui récupère le titre d’origine de la fenêtre de console active.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 109d41a141083fc4691ebaf2546ec8f412f7b861
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059137"
---
# <a name="getconsoleoriginaltitle-function"></a><span data-ttu-id="cff93-104">GetConsoleOriginalTitle fonction)</span><span class="sxs-lookup"><span data-stu-id="cff93-104">GetConsoleOriginalTitle function</span></span>


<span data-ttu-id="cff93-105">Récupère le titre d’origine de la fenêtre de console active.</span><span class="sxs-lookup"><span data-stu-id="cff93-105">Retrieves the original title for the current console window.</span></span>

<a name="syntax"></a><span data-ttu-id="cff93-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cff93-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a><span data-ttu-id="cff93-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cff93-107">Parameters</span></span>
----------

<span data-ttu-id="cff93-108">*lpConsoleTitle* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="cff93-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="cff93-109">Pointeur vers une mémoire tampon qui reçoit une chaîne se terminant par null et contenant le titre d’origine.</span><span class="sxs-lookup"><span data-stu-id="cff93-109">A pointer to a buffer that receives a null-terminated string containing the original title.</span></span>

<span data-ttu-id="cff93-110">*nSize* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="cff93-110">*nSize* \[in\]</span></span>  
<span data-ttu-id="cff93-111">Taille de la mémoire tampon *lpConsoleTitle* , en caractères.</span><span class="sxs-lookup"><span data-stu-id="cff93-111">The size of the *lpConsoleTitle* buffer, in characters.</span></span>

<a name="return-value"></a><span data-ttu-id="cff93-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="cff93-112">Return value</span></span>
------------

<span data-ttu-id="cff93-113">Si la fonction est réussie, la valeur de retour est la longueur de la chaîne copiée dans la mémoire tampon, en caractères.</span><span class="sxs-lookup"><span data-stu-id="cff93-113">If the function succeeds, the return value is the length of the string copied to the buffer, in characters.</span></span>

<span data-ttu-id="cff93-114">Si la mémoire tampon n’est pas assez grande pour stocker le titre, la valeur de retour est zéro et [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) retourne une **erreur de \_ réussite**.</span><span class="sxs-lookup"><span data-stu-id="cff93-114">If the buffer is not large enough to store the title, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns **ERROR\_SUCCESS**.</span></span>

<span data-ttu-id="cff93-115">Si la fonction échoue, la valeur de retour est zéro et [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) retourne le code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="cff93-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

<a name="remarks"></a><span data-ttu-id="cff93-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="cff93-116">Remarks</span></span>
-------

<span data-ttu-id="cff93-117">Pour définir le titre d’une fenêtre de console, utilisez la fonction [**SetConsoleTitle**](setconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="cff93-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="cff93-118">Pour récupérer la chaîne de titre actuelle, utilisez la fonction [**GetConsoleTitle**](getconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="cff93-118">To retrieve the current title string, use the [**GetConsoleTitle**](getconsoletitle.md) function.</span></span>

<span data-ttu-id="cff93-119">Pour compiler une application qui utilise cette fonction, définissez \*\* \_ Win32 \_ winnt\*\* comme 0x0600 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="cff93-119">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0600 or later.</span></span> <span data-ttu-id="cff93-120">Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="cff93-120">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="cff93-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cff93-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="cff93-122">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="cff93-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="cff93-123">Windows Vista [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="cff93-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="cff93-124">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="cff93-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="cff93-125">Windows Server 2008 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="cff93-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="cff93-126">En-tête</span><span class="sxs-lookup"><span data-stu-id="cff93-126">Header</span></span></p></td>
<td><span data-ttu-id="cff93-127">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="cff93-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="cff93-128">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="cff93-128">Library</span></span></p></td>
<td><span data-ttu-id="cff93-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="cff93-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="cff93-130">DLL</span><span class="sxs-lookup"><span data-stu-id="cff93-130">DLL</span></span></p></td>
<td><span data-ttu-id="cff93-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="cff93-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="cff93-132">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="cff93-132">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="cff93-133"><strong>GetConsoleOriginalTitleW</strong> (Unicode) et <strong>GetConsoleOriginalTitleA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="cff93-133"><strong>GetConsoleOriginalTitleW</strong> (Unicode) and <strong>GetConsoleOriginalTitleA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="cff93-134"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cff93-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="cff93-135">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="cff93-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="cff93-136">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="cff93-136">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="cff93-137">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="cff93-137">**SetConsoleTitle**</span></span>](setconsoletitle.md)

 

 




