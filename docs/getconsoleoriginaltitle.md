---
title: GetConsoleOriginalTitle fonction)
description: Consultez les informations de référence sur la fonction GetConsoleOriginalTitle, qui récupère le titre d’origine de la fenêtre de console active.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
ms.openlocfilehash: 3c4fc202601cec9257b6cf95efdd460c64122b80
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358999"
---
# <a name="getconsoleoriginaltitle-function"></a><span data-ttu-id="0f613-104">GetConsoleOriginalTitle fonction)</span><span class="sxs-lookup"><span data-stu-id="0f613-104">GetConsoleOriginalTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="0f613-105">Récupère le titre d’origine de la fenêtre de console active.</span><span class="sxs-lookup"><span data-stu-id="0f613-105">Retrieves the original title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f613-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f613-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a><span data-ttu-id="0f613-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0f613-107">Parameters</span></span>

<span data-ttu-id="0f613-108">*lpConsoleTitle* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="0f613-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="0f613-109">Pointeur vers une mémoire tampon qui reçoit une chaîne se terminant par null et contenant le titre d’origine.</span><span class="sxs-lookup"><span data-stu-id="0f613-109">A pointer to a buffer that receives a null-terminated string containing the original title.</span></span>

<span data-ttu-id="0f613-110">*nSize* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="0f613-110">*nSize* \[in\]</span></span>  
<span data-ttu-id="0f613-111">Taille de la mémoire tampon *lpConsoleTitle* , en caractères.</span><span class="sxs-lookup"><span data-stu-id="0f613-111">The size of the *lpConsoleTitle* buffer, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="0f613-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0f613-112">Return value</span></span>

<span data-ttu-id="0f613-113">Si la fonction est réussie, la valeur de retour est la longueur de la chaîne copiée dans la mémoire tampon, en caractères.</span><span class="sxs-lookup"><span data-stu-id="0f613-113">If the function succeeds, the return value is the length of the string copied to the buffer, in characters.</span></span>

<span data-ttu-id="0f613-114">Si la mémoire tampon n’est pas assez grande pour stocker le titre, la valeur de retour est zéro et [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) retourne une **erreur de \_ réussite**.</span><span class="sxs-lookup"><span data-stu-id="0f613-114">If the buffer is not large enough to store the title, the return value is zero and [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) returns **ERROR\_SUCCESS**.</span></span>

<span data-ttu-id="0f613-115">Si la fonction échoue, la valeur de retour est zéro et [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) retourne le code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0f613-115">If the function fails, the return value is zero and [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) returns the error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f613-116">Notes</span><span class="sxs-lookup"><span data-stu-id="0f613-116">Remarks</span></span>

<span data-ttu-id="0f613-117">Pour définir le titre d’une fenêtre de console, utilisez la fonction [**SetConsoleTitle**](setconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="0f613-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="0f613-118">Pour récupérer la chaîne de titre actuelle, utilisez la fonction [**GetConsoleTitle**](getconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="0f613-118">To retrieve the current title string, use the [**GetConsoleTitle**](getconsoletitle.md) function.</span></span>

<span data-ttu-id="0f613-119">Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0600 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="0f613-119">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0600 or later.</span></span> <span data-ttu-id="0f613-120">Pour plus d’informations, consultez [utilisation des en-têtes Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="0f613-120">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

> [!TIP]
> <span data-ttu-id="0f613-121">Cette API n’est pas recommandée et n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="0f613-121">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="0f613-122">Cette décision aligne intentionnellement la plateforme Windows avec d’autres systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="0f613-122">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="0f613-123">La communication à distance des applications via des utilitaires multiplateforme et des transports comme SSH peut ne pas fonctionner comme prévu si vous utilisez cette API.</span><span class="sxs-lookup"><span data-stu-id="0f613-123">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="0f613-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0f613-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="0f613-125">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="0f613-125">Minimum supported client</span></span> | <span data-ttu-id="0f613-126">Applications de \[ Bureau Windows Vista uniquement\]</span><span class="sxs-lookup"><span data-stu-id="0f613-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="0f613-127">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="0f613-127">Minimum supported server</span></span> | <span data-ttu-id="0f613-128">Applications de bureau Windows Server 2008 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="0f613-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="0f613-129">En-tête</span><span class="sxs-lookup"><span data-stu-id="0f613-129">Header</span></span> | <span data-ttu-id="0f613-130">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0f613-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="0f613-131">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="0f613-131">Library</span></span> | <span data-ttu-id="0f613-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="0f613-132">Kernel32.lib</span></span> |
| <span data-ttu-id="0f613-133">DLL</span><span class="sxs-lookup"><span data-stu-id="0f613-133">DLL</span></span> | <span data-ttu-id="0f613-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0f613-134">Kernel32.dll</span></span> |
| <span data-ttu-id="0f613-135">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="0f613-135">Unicode and ANSI names</span></span> | <span data-ttu-id="0f613-136">**GetConsoleOriginalTitleW** (Unicode) et **GetConsoleOriginalTitleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="0f613-136">**GetConsoleOriginalTitleW** (Unicode) and **GetConsoleOriginalTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="0f613-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f613-137">See also</span></span>

[<span data-ttu-id="0f613-138">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="0f613-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0f613-139">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="0f613-139">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="0f613-140">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="0f613-140">**SetConsoleTitle**</span></span>](setconsoletitle.md)