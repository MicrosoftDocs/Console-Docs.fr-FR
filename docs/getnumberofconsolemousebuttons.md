---
title: GetNumberOfConsoleMouseButtons fonction)
description: Récupère le nombre de boutons de la souris utilisés par la console actuelle.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
ms.openlocfilehash: 4a2f936ac778b13985aa0c1d237c59e9f993d995
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358849"
---
# <a name="getnumberofconsolemousebuttons-function"></a><span data-ttu-id="6622e-104">GetNumberOfConsoleMouseButtons fonction)</span><span class="sxs-lookup"><span data-stu-id="6622e-104">GetNumberOfConsoleMouseButtons function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="6622e-105">Récupère le nombre de boutons de la souris utilisés par la console actuelle.</span><span class="sxs-lookup"><span data-stu-id="6622e-105">Retrieves the number of buttons on the mouse used by the current console.</span></span>

## <a name="syntax"></a><span data-ttu-id="6622e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6622e-106">Syntax</span></span>

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

## <a name="parameters"></a><span data-ttu-id="6622e-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6622e-107">Parameters</span></span>

<span data-ttu-id="6622e-108">*lpNumberOfMouseButtons* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="6622e-108">*lpNumberOfMouseButtons* \[out\]</span></span>  
<span data-ttu-id="6622e-109">Pointeur vers une variable qui reçoit le nombre de boutons de la souris.</span><span class="sxs-lookup"><span data-stu-id="6622e-109">A pointer to a variable that receives the number of mouse buttons.</span></span>

## <a name="return-value"></a><span data-ttu-id="6622e-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="6622e-110">Return value</span></span>

<span data-ttu-id="6622e-111">Si la fonction réussit, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="6622e-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="6622e-112">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="6622e-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="6622e-113">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="6622e-113">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="6622e-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="6622e-114">Remarks</span></span>

<span data-ttu-id="6622e-115">Quand une console reçoit une entrée de souris, une structure [**d' \_ enregistrement d’entrée**](input-record-str.md) contenant une structure d' [**\_ \_ enregistrement d’événement de souris**](mouse-event-record-str.md) est placée dans la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="6622e-115">When a console receives mouse input, an [**INPUT\_RECORD**](input-record-str.md) structure containing a [**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md) structure is placed in the console's input buffer.</span></span> <span data-ttu-id="6622e-116">Le membre **dwButtonState** de **l' \_ \_ enregistrement d’événement de souris** a un bit qui indique l’état de chaque bouton de la souris.</span><span class="sxs-lookup"><span data-stu-id="6622e-116">The **dwButtonState** member of **MOUSE\_EVENT\_RECORD** has a bit indicating the state of each mouse button.</span></span> <span data-ttu-id="6622e-117">Le bit est 1 si le bouton est enfoncé et 0 si le bouton est actif.</span><span class="sxs-lookup"><span data-stu-id="6622e-117">The bit is 1 if the button is down and 0 if the button is up.</span></span> <span data-ttu-id="6622e-118">Pour déterminer le nombre de bits significatifs, utilisez **GetNumberOfConsoleMouseButtons**.</span><span class="sxs-lookup"><span data-stu-id="6622e-118">To determine the number of bits that are significant, use **GetNumberOfConsoleMouseButtons**.</span></span>

> [!TIP]
> <span data-ttu-id="6622e-119">Cette API n’est pas recommandée et n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="6622e-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="6622e-120">Cette décision aligne intentionnellement la plateforme Windows avec d’autres systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="6622e-120">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="6622e-121">Cet État s’applique uniquement à l’utilisateur local, à la session et au contexte de privilège.</span><span class="sxs-lookup"><span data-stu-id="6622e-121">This state is only relevant to the local user, session, and privilege context.</span></span> <span data-ttu-id="6622e-122">La communication à distance des applications via des utilitaires multiplateforme et des transports comme SSH peut ne pas fonctionner comme prévu si vous utilisez cette API.</span><span class="sxs-lookup"><span data-stu-id="6622e-122">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="6622e-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6622e-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="6622e-124">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="6622e-124">Minimum supported client</span></span> | <span data-ttu-id="6622e-125">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="6622e-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="6622e-126">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="6622e-126">Minimum supported server</span></span> | <span data-ttu-id="6622e-127">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="6622e-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="6622e-128">En-tête</span><span class="sxs-lookup"><span data-stu-id="6622e-128">Header</span></span> | <span data-ttu-id="6622e-129">ConsoleApi3. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6622e-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="6622e-130">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="6622e-130">Library</span></span> | <span data-ttu-id="6622e-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="6622e-131">Kernel32.lib</span></span> |
| <span data-ttu-id="6622e-132">DLL</span><span class="sxs-lookup"><span data-stu-id="6622e-132">DLL</span></span> | <span data-ttu-id="6622e-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6622e-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="6622e-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6622e-134">See also</span></span>

[<span data-ttu-id="6622e-135">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="6622e-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="6622e-136">Mémoire tampon d’entrée d’une console</span><span class="sxs-lookup"><span data-stu-id="6622e-136">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="6622e-137">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="6622e-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="6622e-138">**enregistrement d’entrée \_**</span><span class="sxs-lookup"><span data-stu-id="6622e-138">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="6622e-139">**\_enregistrement d’événement de souris \_**</span><span class="sxs-lookup"><span data-stu-id="6622e-139">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)