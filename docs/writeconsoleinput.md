---
title: WriteConsoleInput fonction)
description: Consultez les informations de référence sur la fonction WriteConsoleInput, qui écrit les données directement dans la mémoire tampon d’entrée de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/WriteConsoleInput
- wincon/WriteConsoleInput
- WriteConsoleInput
- consoleapi2/WriteConsoleInputA
- wincon/WriteConsoleInputA
- WriteConsoleInputA
- consoleapi2/WriteConsoleInputW
- wincon/WriteConsoleInputW
- WriteConsoleInputW
MS-HAID:
- '\_win32\_writeconsoleinput'
- base.writeconsoleinput
- consoles.writeconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad06231f-5063-4aff-b14d-8df5e6e42430
topic_type:
- apiref
api_name:
- WriteConsoleInput
- WriteConsoleInputA
- WriteConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: dc2c7930ab76587edc9ae1991d4493c858b0ec30
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039287"
---
# <a name="writeconsoleinput-function"></a><span data-ttu-id="7880f-104">WriteConsoleInput fonction)</span><span class="sxs-lookup"><span data-stu-id="7880f-104">WriteConsoleInput function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="7880f-105">Écrit les données directement dans la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="7880f-105">Writes data directly to the console input buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="7880f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7880f-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="7880f-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7880f-107">Parameters</span></span>

<span data-ttu-id="7880f-108">*hConsoleInput* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="7880f-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="7880f-109">Handle vers la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="7880f-109">A handle to the console input buffer.</span></span> <span data-ttu-id="7880f-110">Le descripteur doit avoir le droit d’accès en **\_ écriture générique** .</span><span class="sxs-lookup"><span data-stu-id="7880f-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="7880f-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="7880f-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="7880f-112">*lpBuffer* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="7880f-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="7880f-113">Pointeur vers un tableau de structures [**d' \_ enregistrements d’entrée**](input-record-str.md) qui contiennent les données à écrire dans la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7880f-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that contain data to be written to the input buffer.</span></span>

<span data-ttu-id="7880f-114">*nLength* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="7880f-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="7880f-115">Nombre d’enregistrements d’entrée à écrire.</span><span class="sxs-lookup"><span data-stu-id="7880f-115">The number of input records to be written.</span></span>

<span data-ttu-id="7880f-116">*lpNumberOfEventsWritten* \[ à\]</span><span class="sxs-lookup"><span data-stu-id="7880f-116">*lpNumberOfEventsWritten* \[out\]</span></span>  
<span data-ttu-id="7880f-117">Pointeur vers une variable qui reçoit le nombre d’enregistrements d’entrée réellement écrits.</span><span class="sxs-lookup"><span data-stu-id="7880f-117">A pointer to a variable that receives the number of input records actually written.</span></span>

## <a name="return-value"></a><span data-ttu-id="7880f-118">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="7880f-118">Return value</span></span>

<span data-ttu-id="7880f-119">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="7880f-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="7880f-120">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="7880f-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="7880f-121">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="7880f-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="7880f-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="7880f-122">Remarks</span></span>

<span data-ttu-id="7880f-123">**WriteConsoleInput** place les enregistrements d’entrée dans la mémoire tampon d’entrée derrière les événements en attente dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="7880f-123">**WriteConsoleInput** places input records into the input buffer behind any pending events in the buffer.</span></span> <span data-ttu-id="7880f-124">Le tampon d’entrée augmente de manière dynamique, si nécessaire, pour contenir autant d’événements que ceux écrits.</span><span class="sxs-lookup"><span data-stu-id="7880f-124">The input buffer grows dynamically, if necessary, to hold as many events as are written.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="7880f-125">Cette API n’est pas recommandée et n’a pas d’équivalent de **[terminal virtuel](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="7880f-125">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="7880f-126">Cette décision aligne intentionnellement la plateforme Windows avec d’autres systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="7880f-126">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="7880f-127">Cette opération est considérée comme un **[verbe incorrect](console-buffer-security-and-access-rights.md#wrong-way-verbs)** pour cette mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="7880f-127">This operation is considered the **[wrong-way verb](console-buffer-security-and-access-rights.md#wrong-way-verbs)** for this buffer.</span></span> <span data-ttu-id="7880f-128">La communication à distance des applications via des utilitaires multiplateforme et des transports comme SSH peut ne pas fonctionner comme prévu si vous utilisez cette API.</span><span class="sxs-lookup"><span data-stu-id="7880f-128">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="7880f-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7880f-129">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="7880f-130">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7880f-130">Minimum supported client</span></span> | <span data-ttu-id="7880f-131">Applications de bureau Windows 2000 professionnel \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="7880f-131">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="7880f-132">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="7880f-132">Minimum supported server</span></span> | <span data-ttu-id="7880f-133">Applications de bureau Windows 2000 Server \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="7880f-133">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="7880f-134">En-tête</span><span class="sxs-lookup"><span data-stu-id="7880f-134">Header</span></span> | <span data-ttu-id="7880f-135">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="7880f-135">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="7880f-136">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="7880f-136">Library</span></span> | <span data-ttu-id="7880f-137">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="7880f-137">Kernel32.lib</span></span> |
| <span data-ttu-id="7880f-138">DLL</span><span class="sxs-lookup"><span data-stu-id="7880f-138">DLL</span></span> | <span data-ttu-id="7880f-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7880f-139">Kernel32.dll</span></span> |
| <span data-ttu-id="7880f-140">Noms Unicode et ANSI</span><span class="sxs-lookup"><span data-stu-id="7880f-140">Unicode and ANSI names</span></span> | <span data-ttu-id="7880f-141">**WriteConsoleInputW** (Unicode) et **WriteConsoleInputA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="7880f-141">**WriteConsoleInputW** (Unicode) and **WriteConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="7880f-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7880f-142">See also</span></span>

[<span data-ttu-id="7880f-143">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="7880f-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="7880f-144">**enregistrement d’entrée \_**</span><span class="sxs-lookup"><span data-stu-id="7880f-144">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="7880f-145">Fonctions d’entrée de la console de bas niveau</span><span class="sxs-lookup"><span data-stu-id="7880f-145">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="7880f-146">**MapVirtualKey**</span><span class="sxs-lookup"><span data-stu-id="7880f-146">**MapVirtualKey**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646306)

[<span data-ttu-id="7880f-147">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="7880f-147">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="7880f-148">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="7880f-148">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="7880f-149">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="7880f-149">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="7880f-150">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="7880f-150">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="7880f-151">**VkKeyScan**</span><span class="sxs-lookup"><span data-stu-id="7880f-151">**VkKeyScan**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646329)
