---
title: GetNumberOfConsoleMouseButtons fonction)
description: Récupère le nombre de boutons de la souris utilisés par la console actuelle.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi3/GetNumberOfConsoleMouseButtons
- wincon/GetNumberOfConsoleMouseButtons
- GetNumberOfConsoleMouseButtons
MS-HAID:
- '\_win32\_getnumberofconsolemousebuttons'
- base.getnumberofconsolemousebuttons
- consoles.getnumberofconsolemousebuttons
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2
topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 67089bd301ac2632f9a99ca24cc2042789f6a3e8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059492"
---
# <a name="getnumberofconsolemousebuttons-function"></a><span data-ttu-id="490a1-104">GetNumberOfConsoleMouseButtons fonction)</span><span class="sxs-lookup"><span data-stu-id="490a1-104">GetNumberOfConsoleMouseButtons function</span></span>


<span data-ttu-id="490a1-105">Récupère le nombre de boutons de la souris utilisés par la console actuelle.</span><span class="sxs-lookup"><span data-stu-id="490a1-105">Retrieves the number of buttons on the mouse used by the current console.</span></span>

<a name="syntax"></a><span data-ttu-id="490a1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="490a1-106">Syntax</span></span>
------

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

<a name="parameters"></a><span data-ttu-id="490a1-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="490a1-107">Parameters</span></span>
----------

<span data-ttu-id="490a1-108">*lpNumberOfMouseButtons* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="490a1-108">*lpNumberOfMouseButtons* \[out\]</span></span>  
<span data-ttu-id="490a1-109">Pointeur vers une variable qui reçoit le nombre de boutons de la souris.</span><span class="sxs-lookup"><span data-stu-id="490a1-109">A pointer to a variable that receives the number of mouse buttons.</span></span>

<a name="return-value"></a><span data-ttu-id="490a1-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="490a1-110">Return value</span></span>
------------

<span data-ttu-id="490a1-111">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="490a1-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="490a1-112">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="490a1-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="490a1-113">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="490a1-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="490a1-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="490a1-114">Remarks</span></span>
-------

<span data-ttu-id="490a1-115">Quand une console reçoit une entrée de souris, une structure [**d' \_ enregistrement d’entrée**](input-record-str.md) contenant une structure d' [\*\* \_ \_ enregistrement d’événement de souris\*\*](mouse-event-record-str.md) est placée dans la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="490a1-115">When a console receives mouse input, an [**INPUT\_RECORD**](input-record-str.md) structure containing a [**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md) structure is placed in the console's input buffer.</span></span> <span data-ttu-id="490a1-116">Le membre **dwButtonState** de **l' \_ \_ enregistrement d’événement de souris** a un bit qui indique l’état de chaque bouton de la souris.</span><span class="sxs-lookup"><span data-stu-id="490a1-116">The **dwButtonState** member of **MOUSE\_EVENT\_RECORD** has a bit indicating the state of each mouse button.</span></span> <span data-ttu-id="490a1-117">Le bit est 1 si le bouton est enfoncé et 0 si le bouton est actif.</span><span class="sxs-lookup"><span data-stu-id="490a1-117">The bit is 1 if the button is down and 0 if the button is up.</span></span> <span data-ttu-id="490a1-118">Pour déterminer le nombre de bits significatifs, utilisez **GetNumberOfConsoleMouseButtons**.</span><span class="sxs-lookup"><span data-stu-id="490a1-118">To determine the number of bits that are significant, use **GetNumberOfConsoleMouseButtons**.</span></span>

<a name="requirements"></a><span data-ttu-id="490a1-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="490a1-119">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="490a1-120">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="490a1-120">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="490a1-121">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="490a1-121">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="490a1-122">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="490a1-122">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="490a1-123">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="490a1-123">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="490a1-124">En-tête</span><span class="sxs-lookup"><span data-stu-id="490a1-124">Header</span></span></p></td>
<td><span data-ttu-id="490a1-125">ConsoleApi3. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="490a1-125">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="490a1-126">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="490a1-126">Library</span></span></p></td>
<td><span data-ttu-id="490a1-127">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="490a1-127">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="490a1-128">DLL</span><span class="sxs-lookup"><span data-stu-id="490a1-128">DLL</span></span></p></td>
<td><span data-ttu-id="490a1-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="490a1-129">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="490a1-130"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="490a1-130"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="490a1-131">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="490a1-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="490a1-132">Mémoire tampon d’entrée de la console</span><span class="sxs-lookup"><span data-stu-id="490a1-132">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="490a1-133">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="490a1-133">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="490a1-134">**enregistrement d’entrée \_**</span><span class="sxs-lookup"><span data-stu-id="490a1-134">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="490a1-135">**\_enregistrement d’événement de souris \_**</span><span class="sxs-lookup"><span data-stu-id="490a1-135">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

 

 




