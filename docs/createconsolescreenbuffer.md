---
title: CreateConsoleScreenBuffer fonction)
description: La fonction CreateConsoleScreenBuffer crée une mémoire tampon d’écran pour la console Windows.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi2/CreateConsoleScreenBuffer
- wincon/CreateConsoleScreenBuffer
- CreateConsoleScreenBuffer
MS-HAID:
- '\_win32\_createconsolescreenbuffer'
- base.createconsolescreenbuffer
- consoles.createconsolescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98bb74e4-dad2-4615-9263-48ba778a06ff
topic_type:
- apiref
api_name:
- CreateConsoleScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0e7e4606e561454a2037650cc8d1f3b685ff2d5d
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357959"
---
# <a name="createconsolescreenbuffer-function"></a><span data-ttu-id="0d558-104">CreateConsoleScreenBuffer fonction)</span><span class="sxs-lookup"><span data-stu-id="0d558-104">CreateConsoleScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="0d558-105">Crée une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="0d558-105">Creates a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d558-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d558-106">Syntax</span></span>

```C
HANDLE WINAPI CreateConsoleScreenBuffer(
  _In_             DWORD               dwDesiredAccess,
  _In_             DWORD               dwShareMode,
  _In_opt_   const SECURITY_ATTRIBUTES *lpSecurityAttributes,
  _In_             DWORD               dwFlags,
  _Reserved_       LPVOID              lpScreenBufferData
);
```

## <a name="parameters"></a><span data-ttu-id="0d558-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0d558-107">Parameters</span></span>

<span data-ttu-id="0d558-108">*dwDesiredAccess* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="0d558-108">*dwDesiredAccess* \[in\]</span></span>  
<span data-ttu-id="0d558-109">Accès à la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="0d558-109">The access to the console screen buffer.</span></span> <span data-ttu-id="0d558-110">Pour obtenir la liste des droits d’accès, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="0d558-110">For a list of access rights, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="0d558-111">*dwShareMode* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="0d558-111">*dwShareMode* \[in\]</span></span>  
<span data-ttu-id="0d558-112">Ce paramètre peut être égal à zéro, ce qui indique que la mémoire tampon ne peut pas être partagée ou qu’il peut s’agir d’une ou plusieurs des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="0d558-112">This parameter can be zero, indicating that the buffer cannot be shared, or it can be one or more of the following values.</span></span>

| <span data-ttu-id="0d558-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="0d558-113">Value</span></span> | <span data-ttu-id="0d558-114">Signification</span><span class="sxs-lookup"><span data-stu-id="0d558-114">Meaning</span></span> |
|-|-|
| <span data-ttu-id="0d558-115">**FILE_SHARE_READ** 0x00000001</span><span class="sxs-lookup"><span data-stu-id="0d558-115">**FILE_SHARE_READ** 0x00000001</span></span> | <span data-ttu-id="0d558-116">D’autres opérations ouvertes peuvent être effectuées dans la mémoire tampon d’écran de la console pour l’accès en lecture.</span><span class="sxs-lookup"><span data-stu-id="0d558-116">Other open operations can be performed on the console screen buffer for read access.</span></span> |
| <span data-ttu-id="0d558-117">**FILE_SHARE_WRITE** 0x00000002</span><span class="sxs-lookup"><span data-stu-id="0d558-117">**FILE_SHARE_WRITE** 0x00000002</span></span> | <span data-ttu-id="0d558-118">D’autres opérations ouvertes peuvent être effectuées dans la mémoire tampon d’écran de la console pour l’accès en écriture.</span><span class="sxs-lookup"><span data-stu-id="0d558-118">Other open operations can be performed on the console screen buffer for write access.</span></span> |

<span data-ttu-id="0d558-119">*lpSecurityAttributes* \[ dans, facultatif\]</span><span class="sxs-lookup"><span data-stu-id="0d558-119">*lpSecurityAttributes* \[in, optional\]</span></span>  
<span data-ttu-id="0d558-120">Pointeur vers une structure [**d' \_ attributs de sécurité**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85)) qui détermine si le handle retourné peut être hérité par les processus enfants.</span><span class="sxs-lookup"><span data-stu-id="0d558-120">A pointer to a [**SECURITY\_ATTRIBUTES**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85)) structure that determines whether the returned handle can be inherited by child processes.</span></span> <span data-ttu-id="0d558-121">Si *lpSecurityAttributes* a la **valeur null**, le handle ne peut pas être hérité.</span><span class="sxs-lookup"><span data-stu-id="0d558-121">If *lpSecurityAttributes* is **NULL**, the handle cannot be inherited.</span></span> <span data-ttu-id="0d558-122">Le membre **lpSecurityDescriptor** de la structure spécifie un descripteur de sécurité pour la nouvelle mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="0d558-122">The **lpSecurityDescriptor** member of the structure specifies a security descriptor for the new console screen buffer.</span></span> <span data-ttu-id="0d558-123">Si *lpSecurityAttributes* a la **valeur null**, la mémoire tampon d’écran de la console obtient un descripteur de sécurité par défaut.</span><span class="sxs-lookup"><span data-stu-id="0d558-123">If *lpSecurityAttributes* is **NULL**, the console screen buffer gets a default security descriptor.</span></span> <span data-ttu-id="0d558-124">Les listes de contrôle d’accès dans le descripteur de sécurité par défaut pour une mémoire tampon d’écran de console proviennent du jeton principal ou d’emprunt d’identité du créateur.</span><span class="sxs-lookup"><span data-stu-id="0d558-124">The ACLs in the default security descriptor for a console screen buffer come from the primary or impersonation token of the creator.</span></span>

<span data-ttu-id="0d558-125">*dwFlags* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="0d558-125">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="0d558-126">Type de mémoire tampon d’écran de console à créer.</span><span class="sxs-lookup"><span data-stu-id="0d558-126">The type of console screen buffer to create.</span></span> <span data-ttu-id="0d558-127">Le seul type de mémoire tampon d’écran pris en charge est la **\_ \_ mémoire tampon** de la console.</span><span class="sxs-lookup"><span data-stu-id="0d558-127">The only supported screen buffer type is **CONSOLE\_TEXTMODE\_BUFFER**.</span></span>

<span data-ttu-id="0d558-128">*lpScreenBufferData*</span><span class="sxs-lookup"><span data-stu-id="0d558-128">*lpScreenBufferData*</span></span>  
<span data-ttu-id="0d558-129">Réservé doit avoir la **valeur null**.</span><span class="sxs-lookup"><span data-stu-id="0d558-129">Reserved; should be **NULL**.</span></span>

## <a name="return-value"></a><span data-ttu-id="0d558-130">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0d558-130">Return value</span></span>

<span data-ttu-id="0d558-131">Si la fonction est réussie, la valeur de retour est un handle vers la nouvelle mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="0d558-131">If the function succeeds, the return value is a handle to the new console screen buffer.</span></span>

<span data-ttu-id="0d558-132">Si la fonction échoue, la valeur de retour est **INVALID\_HANDLE\_VALUE**.</span><span class="sxs-lookup"><span data-stu-id="0d558-132">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="0d558-133">Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="0d558-133">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="0d558-134">Remarques</span><span class="sxs-lookup"><span data-stu-id="0d558-134">Remarks</span></span>

<span data-ttu-id="0d558-135">Une console peut avoir plusieurs mémoires tampons d’écran, mais une seule mémoire tampon d’écran active.</span><span class="sxs-lookup"><span data-stu-id="0d558-135">A console can have multiple screen buffers but only one active screen buffer.</span></span> <span data-ttu-id="0d558-136">La lecture et l’écriture de tampons d’écran inactifs sont accessibles en lecture et en écriture, mais seule la mémoire tampon d’écran active s’affiche.</span><span class="sxs-lookup"><span data-stu-id="0d558-136">Inactive screen buffers can be accessed for reading and writing, but only the active screen buffer is displayed.</span></span> <span data-ttu-id="0d558-137">Pour faire du nouvel écran la mémoire tampon d’écran active, utilisez la fonction [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="0d558-137">To make the new screen buffer the active screen buffer, use the [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) function.</span></span>

<span data-ttu-id="0d558-138">La mémoire tampon d’écran nouvellement créée copie des propriétés à partir de la mémoire tampon d’écran active au moment où cette fonction est appelée.</span><span class="sxs-lookup"><span data-stu-id="0d558-138">The newly created screen buffer will copy some properties from the active screen buffer at the time that this function is called.</span></span> <span data-ttu-id="0d558-139">Le comportement est le suivant :</span><span class="sxs-lookup"><span data-stu-id="0d558-139">The behavior is as follows:</span></span>

- <span data-ttu-id="0d558-140">`Font` -copié à partir de la mémoire tampon d’écran active</span><span class="sxs-lookup"><span data-stu-id="0d558-140">`Font` - copied from active screen buffer</span></span>
- <span data-ttu-id="0d558-141">`Display Window Size` -copié à partir de la mémoire tampon d’écran active</span><span class="sxs-lookup"><span data-stu-id="0d558-141">`Display Window Size` - copied from active screen buffer</span></span>
- <span data-ttu-id="0d558-142">`Buffer Size` -correspond à `Display Window Size` (**non** copié)</span><span class="sxs-lookup"><span data-stu-id="0d558-142">`Buffer Size` - matched to `Display Window Size` (**NOT** copied)</span></span>
- <span data-ttu-id="0d558-143">`Default Attributes` (couleurs)-copié à partir de la mémoire tampon d’écran active</span><span class="sxs-lookup"><span data-stu-id="0d558-143">`Default Attributes` (colors) - copied from active screen buffer</span></span>
- <span data-ttu-id="0d558-144">`Default Popup Attributes` (couleurs)-copié à partir de la mémoire tampon d’écran active</span><span class="sxs-lookup"><span data-stu-id="0d558-144">`Default Popup Attributes` (colors) - copied from active screen buffer</span></span>

<span data-ttu-id="0d558-145">Le processus appelant peut utiliser le handle retourné dans toute fonction qui requiert un handle vers une mémoire tampon d’écran de la console, selon les limitations d’accès spécifiées par le paramètre *dwDesiredAccess* .</span><span class="sxs-lookup"><span data-stu-id="0d558-145">The calling process can use the returned handle in any function that requires a handle to a console screen buffer, subject to the limitations of access specified by the *dwDesiredAccess* parameter.</span></span>

<span data-ttu-id="0d558-146">Le processus appelant peut utiliser la fonction [**DuplicateHandle**](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle) pour créer un handle de mémoire tampon d’écran en double qui a un accès ou une héritage différent du handle d’origine.</span><span class="sxs-lookup"><span data-stu-id="0d558-146">The calling process can use the [**DuplicateHandle**](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle) function to create a duplicate screen buffer handle that has different access or inheritability from the original handle.</span></span> <span data-ttu-id="0d558-147">Toutefois, vous ne pouvez pas utiliser **DuplicateHandle** pour créer un doublon valide pour un autre processus (sauf par héritage).</span><span class="sxs-lookup"><span data-stu-id="0d558-147">However, **DuplicateHandle** cannot be used to create a duplicate that is valid for a different process (except through inheritance).</span></span>

<span data-ttu-id="0d558-148">Pour fermer le descripteur de la mémoire tampon de l’écran de la console, utilisez la fonction [**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle) .</span><span class="sxs-lookup"><span data-stu-id="0d558-148">To close the console screen buffer handle, use the [**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle) function.</span></span>

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a><span data-ttu-id="0d558-149">Exemples</span><span class="sxs-lookup"><span data-stu-id="0d558-149">Examples</span></span>

<span data-ttu-id="0d558-150">Pour obtenir un exemple, consultez [lecture et écriture de blocs de caractères et d’attributs](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="0d558-150">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="0d558-151">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0d558-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="0d558-152">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="0d558-152">Minimum supported client</span></span> | <span data-ttu-id="0d558-153">Windows 2000 Professionnel - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="0d558-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="0d558-154">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="0d558-154">Minimum supported server</span></span> | <span data-ttu-id="0d558-155">Windows 2000 Server - \[Applications de bureau uniquement\]</span><span class="sxs-lookup"><span data-stu-id="0d558-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="0d558-156">En-tête</span><span class="sxs-lookup"><span data-stu-id="0d558-156">Header</span></span> | <span data-ttu-id="0d558-157">ConsoleApi2. h (via WinCon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0d558-157">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="0d558-158">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="0d558-158">Library</span></span> | <span data-ttu-id="0d558-159">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="0d558-159">Kernel32.lib</span></span> |
| <span data-ttu-id="0d558-160">DLL</span><span class="sxs-lookup"><span data-stu-id="0d558-160">DLL</span></span> | <span data-ttu-id="0d558-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0d558-161">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="0d558-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d558-162">See also</span></span>

[<span data-ttu-id="0d558-163">Fonctions de console</span><span class="sxs-lookup"><span data-stu-id="0d558-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0d558-164">Mémoires tampons d’écran d’une console</span><span class="sxs-lookup"><span data-stu-id="0d558-164">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="0d558-165">**CloseHandle**</span><span class="sxs-lookup"><span data-stu-id="0d558-165">**CloseHandle**</span></span>](/windows/win32/api/handleapi/nf-handleapi-closehandle)

[<span data-ttu-id="0d558-166">**DuplicateHandle**</span><span class="sxs-lookup"><span data-stu-id="0d558-166">**DuplicateHandle**</span></span>](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle)

[<span data-ttu-id="0d558-167">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="0d558-167">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

<span data-ttu-id="0d558-168">[**attributs de sécurité \_**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="0d558-168">[**SECURITY\_ATTRIBUTES**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85))</span></span>

[<span data-ttu-id="0d558-169">**SetConsoleActiveScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="0d558-169">**SetConsoleActiveScreenBuffer**</span></span>](setconsoleactivescreenbuffer.md)

[<span data-ttu-id="0d558-170">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="0d558-170">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)