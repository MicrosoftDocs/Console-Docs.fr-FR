---
title: GetConsoleTitle fonction)
description: Récupère le titre et la taille du titre pour la fenêtre de console active.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi2/GetConsoleTitle
- wincon/GetConsoleTitle
- GetConsoleTitle
- consoleapi2/GetConsoleTitleA
- wincon/GetConsoleTitleA
- GetConsoleTitleA
- consoleapi2/GetConsoleTitleW
- wincon/GetConsoleTitleW
- GetConsoleTitleW
MS-HAID:
- '\_win32\_getconsoletitle'
- base.getconsoletitle
- consoles.getconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c58bba36-9813-4bdc-83bf-30d55f8d7d79
topic_type:
- apiref
api_name:
- GetConsoleTitle
- GetConsoleTitleA
- GetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-Ms-Win-Core-Console-Ansi-L2-1-0.dll
- Kernel32Legacy.dll
api_type:
- DllExport
ms.openlocfilehash: 5b8e78e65e52c3f10be14afa6a122fa12609a2eb
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059120"
---
# <a name="getconsoletitle-function"></a><span data-ttu-id="deb65-104">GetConsoleTitle fonction)</span><span class="sxs-lookup"><span data-stu-id="deb65-104">GetConsoleTitle function</span></span>


<span data-ttu-id="deb65-105">Récupère le titre de la fenêtre de console active.</span><span class="sxs-lookup"><span data-stu-id="deb65-105">Retrieves the title for the current console window.</span></span>

<a name="syntax"></a><span data-ttu-id="deb65-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="deb65-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a><span data-ttu-id="deb65-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="deb65-107">Parameters</span></span>
----------

<span data-ttu-id="deb65-108">*lpConsoleTitle* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="deb65-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="deb65-109">Pointeur vers une mémoire tampon qui reçoit une chaîne se terminant par null et contenant le titre.</span><span class="sxs-lookup"><span data-stu-id="deb65-109">A pointer to a buffer that receives a null-terminated string containing the title.</span></span> <span data-ttu-id="deb65-110">Si la mémoire tampon est trop petite pour stocker le titre, la fonction stocke autant de caractères du titre que ceux qui sont contenus dans la mémoire tampon, se terminant par une marque de fin null.</span><span class="sxs-lookup"><span data-stu-id="deb65-110">If the buffer is too small to store the title, the function stores as many characters of the title as will fit in the buffer, ending with a null terminator.</span></span>

<span data-ttu-id="deb65-111">*nSize* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="deb65-111">*nSize* \[in\]</span></span>  
<span data-ttu-id="deb65-112">Taille de la mémoire tampon vers laquelle pointe le paramètre *lpConsoleTitle* , en caractères.</span><span class="sxs-lookup"><span data-stu-id="deb65-112">The size of the buffer pointed to by the *lpConsoleTitle* parameter, in characters.</span></span>

<a name="return-value"></a><span data-ttu-id="deb65-113">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="deb65-113">Return value</span></span>
------------

<span data-ttu-id="deb65-114">Si la fonction est réussie, la valeur de retour est la longueur du titre de la fenêtre de console, en caractères.</span><span class="sxs-lookup"><span data-stu-id="deb65-114">If the function succeeds, the return value is the length of the console window's title, in characters.</span></span>

<span data-ttu-id="deb65-115">Si la fonction échoue, la valeur de retour est zéro et [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) retourne le code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="deb65-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

<a name="remarks"></a><span data-ttu-id="deb65-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="deb65-116">Remarks</span></span>
-------

<span data-ttu-id="deb65-117">Pour définir le titre d’une fenêtre de console, utilisez la fonction [**SetConsoleTitle**](setconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="deb65-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="deb65-118">Pour récupérer la chaîne de titre d’origine, utilisez la fonction [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) .</span><span class="sxs-lookup"><span data-stu-id="deb65-118">To retrieve the original title string, use the [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) function.</span></span>

<span data-ttu-id="deb65-119">Cette fonction utilise des caractères Unicode ou 8 bits à partir de la page de codes actuelle de la console.</span><span class="sxs-lookup"><span data-stu-id="deb65-119">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="deb65-120">La page de codes de la console est initialement définie par défaut sur la page de codes OEM du système.</span><span class="sxs-lookup"><span data-stu-id="deb65-120">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="deb65-121">Pour modifier la page de codes de la console, utilisez les fonctions [**SetConsoleCP**](setconsolecp.md) ou [**SetConsoleOutputCP**](setconsoleoutputcp.md) , ou utilisez les commandes **chcp** ou **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="deb65-121">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="deb65-122">Exemples</span><span class="sxs-lookup"><span data-stu-id="deb65-122">Examples</span></span>
--------

<span data-ttu-id="deb65-123">Pour obtenir un exemple, consultez [**SetConsoleTitle**](setconsoletitle.md).</span><span class="sxs-lookup"><span data-stu-id="deb65-123">For an example, see [**SetConsoleTitle**](setconsoletitle.md).</span></span>

<a name="requirements"></a><span data-ttu-id="deb65-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="deb65-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="deb65-125">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="deb65-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="deb65-126">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="deb65-126">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="deb65-127">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="deb65-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="deb65-128">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="deb65-128">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="deb65-129">En-tête</span><span class="sxs-lookup"><span data-stu-id="deb65-129">Header</span></span></p></td>
<td><span data-ttu-id="deb65-130">ConsoleApi2. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="deb65-130">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="deb65-131">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="deb65-131">Library</span></span></p></td>
<td><span data-ttu-id="deb65-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="deb65-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="deb65-133">DLL</span><span class="sxs-lookup"><span data-stu-id="deb65-133">DLL</span></span></p></td>
<td><span data-ttu-id="deb65-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="deb65-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="deb65-135">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="deb65-135">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="deb65-136"><strong>GetConsoleTitleW</strong> (Unicode) et <strong>GetConsoleTitleA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="deb65-136"><strong>GetConsoleTitleW</strong> (Unicode) and <strong>GetConsoleTitleA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="deb65-137"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="deb65-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="deb65-138">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="deb65-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="deb65-139">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="deb65-139">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="deb65-140">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="deb65-140">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="deb65-141">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="deb65-141">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="deb65-142">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="deb65-142">**SetConsoleTitle**</span></span>](setconsoletitle.md)

 

 




