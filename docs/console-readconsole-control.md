---
title: CONSOLE_READCONSOLE_CONTROL, structure
description: Consultez les informations de référence sur la structure CONSOLE_READCONSOLE_CONTROL, qui contient des informations relatives à une opération de lecture de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/CONSOLE_READCONSOLE_CONTROL
- wincon/CONSOLE_READCONSOLE_CONTROL
- CONSOLE_READCONSOLE_CONTROL
- consoleapi/PCONSOLE_READCONSOLE_CONTROL
- wincon/PCONSOLE_READCONSOLE_CONTROL
- PCONSOLE_READCONSOLE_CONTROL
MS-HAID:
- base.console\_readconsole\_control
- consoles.console\_readconsole\_control
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a8451a6-d692-43af-88c4-972c4dc5e07c
topic_type:
- apiref
api_name:
- CONSOLE_READCONSOLE_CONTROL
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8a703a1eaa370e16095e1b10eb146a0718f332e9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039187"
---
# <a name="console_readconsole_control-structure"></a><span data-ttu-id="19b17-104">\_Structure de contrôle READCONSOLE de la console \_</span><span class="sxs-lookup"><span data-stu-id="19b17-104">CONSOLE\_READCONSOLE\_CONTROL structure</span></span>

<span data-ttu-id="19b17-105">Contient des informations relatives à une opération de lecture de console.</span><span class="sxs-lookup"><span data-stu-id="19b17-105">Contains information for a console read operation.</span></span>

## <a name="syntax"></a><span data-ttu-id="19b17-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19b17-106">Syntax</span></span>

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

## <a name="members"></a><span data-ttu-id="19b17-107">Membres</span><span class="sxs-lookup"><span data-stu-id="19b17-107">Members</span></span>

<span data-ttu-id="19b17-108">**nLength**</span><span class="sxs-lookup"><span data-stu-id="19b17-108">**nLength**</span></span>  
<span data-ttu-id="19b17-109">Taille de la structure.</span><span class="sxs-lookup"><span data-stu-id="19b17-109">The size of the structure.</span></span> <span data-ttu-id="19b17-110">Affectez à ce membre la valeur `sizeof(CONSOLE_READCONSOLE_CONTROL)` .</span><span class="sxs-lookup"><span data-stu-id="19b17-110">Set this member to `sizeof(CONSOLE_READCONSOLE_CONTROL)`.</span></span>

<span data-ttu-id="19b17-111">**nInitialChars**</span><span class="sxs-lookup"><span data-stu-id="19b17-111">**nInitialChars**</span></span>  
<span data-ttu-id="19b17-112">Nombre de caractères à ignorer (et donc conserver) avant l’écriture de l’entrée récemment lue dans la mémoire tampon transmise à la fonction [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="19b17-112">The number of characters to skip (and thus preserve) before writing newly read input in the buffer passed to the [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="19b17-113">Cette valeur doit être inférieure au paramètre *nNumberOfCharsToRead* de la fonction **ReadConsole** .</span><span class="sxs-lookup"><span data-stu-id="19b17-113">This value must be less than the *nNumberOfCharsToRead* parameter of the **ReadConsole** function.</span></span>

<span data-ttu-id="19b17-114">**dwCtrlWakeupMask**</span><span class="sxs-lookup"><span data-stu-id="19b17-114">**dwCtrlWakeupMask**</span></span>  
<span data-ttu-id="19b17-115">Masque spécifiant quels caractères de contrôle entre `0x00` et `0x1F` doivent être utilisés pour signaler que la lecture est terminée.</span><span class="sxs-lookup"><span data-stu-id="19b17-115">A mask specifying which control characters between `0x00` and `0x1F` should be used to signal that the read is complete.</span></span> <span data-ttu-id="19b17-116">Chaque bit correspond à un caractère avec le bit le moins significatif correspondant à `0x00` ou `NUL` et le bit le plus significatif correspondant à `0x1F` ou à `US` .</span><span class="sxs-lookup"><span data-stu-id="19b17-116">Each bit corresponds to a character with the least significant bit corresponding to `0x00` or `NUL` and the most significant bit corresponding to `0x1F` or `US`.</span></span> <span data-ttu-id="19b17-117">Plusieurs bits (caractères de contrôle) peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="19b17-117">Multiple bits (control characters) can be specified.</span></span>

<span data-ttu-id="19b17-118">**dwControlKeyState**</span><span class="sxs-lookup"><span data-stu-id="19b17-118">**dwControlKeyState**</span></span>  
<span data-ttu-id="19b17-119">État des touches de contrôle.</span><span class="sxs-lookup"><span data-stu-id="19b17-119">The state of the control keys.</span></span> <span data-ttu-id="19b17-120">Ce membre peut être une ou plusieurs des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="19b17-120">This member can be one or more of the following values.</span></span>

| <span data-ttu-id="19b17-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="19b17-121">Value</span></span> | <span data-ttu-id="19b17-122">Signification</span><span class="sxs-lookup"><span data-stu-id="19b17-122">Meaning</span></span> |
|-|-|
| <span data-ttu-id="19b17-123">**CAPSLOCK_ON** 0x0080</span><span class="sxs-lookup"><span data-stu-id="19b17-123">**CAPSLOCK_ON** 0x0080</span></span> | <span data-ttu-id="19b17-124">Le voyant Verr. MAJ est activé.</span><span class="sxs-lookup"><span data-stu-id="19b17-124">The CAPS LOCK light is on.</span></span> |
| <span data-ttu-id="19b17-125">**ENHANCED_KEY** 0x0100</span><span class="sxs-lookup"><span data-stu-id="19b17-125">**ENHANCED_KEY** 0x0100</span></span> | <span data-ttu-id="19b17-126">La clé est améliorée.</span><span class="sxs-lookup"><span data-stu-id="19b17-126">The key is enhanced.</span></span> <span data-ttu-id="19b17-127">Consultez la [section Notes](key-event-record-str.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="19b17-127">See [remarks](key-event-record-str.md#remarks).</span></span> |
| <span data-ttu-id="19b17-128">**LEFT_ALT_PRESSED** 0x0002</span><span class="sxs-lookup"><span data-stu-id="19b17-128">**LEFT_ALT_PRESSED** 0x0002</span></span> | <span data-ttu-id="19b17-129">La touche ALT de gauche est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="19b17-129">The left ALT key is pressed.</span></span> |
| <span data-ttu-id="19b17-130">**LEFT_CTRL_PRESSED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="19b17-130">**LEFT_CTRL_PRESSED** 0x0008</span></span> | <span data-ttu-id="19b17-131">La touche CTRL de gauche est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="19b17-131">The left CTRL key is pressed.</span></span> |
| <span data-ttu-id="19b17-132">**NUMLOCK_ON** 0x0020</span><span class="sxs-lookup"><span data-stu-id="19b17-132">**NUMLOCK_ON** 0x0020</span></span> | <span data-ttu-id="19b17-133">La diode Verr. NUM est activée.</span><span class="sxs-lookup"><span data-stu-id="19b17-133">The NUM LOCK light is on.</span></span> |
| <span data-ttu-id="19b17-134">**RIGHT_ALT_PRESSED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="19b17-134">**RIGHT_ALT_PRESSED** 0x0001</span></span> | <span data-ttu-id="19b17-135">La touche ALT de droite est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="19b17-135">The right ALT key is pressed.</span></span> |
| <span data-ttu-id="19b17-136">**RIGHT_CTRL_PRESSED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="19b17-136">**RIGHT_CTRL_PRESSED** 0x0004</span></span> | <span data-ttu-id="19b17-137">La touche CTRL de droite est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="19b17-137">The right CTRL key is pressed.</span></span> |
| <span data-ttu-id="19b17-138">**SCROLLLOCK_ON** 0x0040</span><span class="sxs-lookup"><span data-stu-id="19b17-138">**SCROLLLOCK_ON** 0x0040</span></span> | <span data-ttu-id="19b17-139">Le voyant du verrou de défilement est activé.</span><span class="sxs-lookup"><span data-stu-id="19b17-139">The SCROLL LOCK light is on.</span></span> |
| <span data-ttu-id="19b17-140">**SHIFT_PRESSED** 0x0010</span><span class="sxs-lookup"><span data-stu-id="19b17-140">**SHIFT_PRESSED** 0x0010</span></span> | <span data-ttu-id="19b17-141">La touche Maj est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="19b17-141">The SHIFT key is pressed.</span></span> |

## <a name="requirements"></a><span data-ttu-id="19b17-142">Spécifications</span><span class="sxs-lookup"><span data-stu-id="19b17-142">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="19b17-143">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="19b17-143">Minimum supported client</span></span> | <span data-ttu-id="19b17-144">Applications de \[ Bureau Windows Vista uniquement\]</span><span class="sxs-lookup"><span data-stu-id="19b17-144">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="19b17-145">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="19b17-145">Minimum supported server</span></span> | <span data-ttu-id="19b17-146">Applications de bureau Windows Server 2008 \[ uniquement\]</span><span class="sxs-lookup"><span data-stu-id="19b17-146">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="19b17-147">En-tête</span><span class="sxs-lookup"><span data-stu-id="19b17-147">Header</span></span> | <span data-ttu-id="19b17-148">ConsoleApi. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="19b17-148">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="19b17-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19b17-149">See also</span></span>

[<span data-ttu-id="19b17-150">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="19b17-150">**ReadConsole**</span></span>](readconsole.md)
