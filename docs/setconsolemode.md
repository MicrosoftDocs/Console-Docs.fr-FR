---
title: SetConsoleMode fonction)
description: Définit le mode d’entrée de la mémoire tampon d’entrée d’une console ou le mode de sortie d’une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi/SetConsoleMode
- wincon/SetConsoleMode
- SetConsoleMode
MS-HAID:
- '\_win32\_setconsolemode'
- base.setconsolemode
- consoles.setconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 77508d58-8a7a-4c47-9ec5-dc61e5c4beac
topic_type:
- apiref
api_name:
- SetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a524a9f730d53efd331a70693aadfeddeaad4cc0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060518"
---
# <a name="setconsolemode-function"></a><span data-ttu-id="03a0b-104">SetConsoleMode fonction)</span><span class="sxs-lookup"><span data-stu-id="03a0b-104">SetConsoleMode function</span></span>


<span data-ttu-id="03a0b-105">Définit le mode d’entrée de la mémoire tampon d’entrée d’une console ou le mode de sortie d’une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="03a0b-105">Sets the input mode of a console's input buffer or the output mode of a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="03a0b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03a0b-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

<a name="parameters"></a><span data-ttu-id="03a0b-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="03a0b-107">Parameters</span></span>
----------

<span data-ttu-id="03a0b-108">*hConsoleHandle* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="03a0b-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="03a0b-109">Handle vers la mémoire tampon d’entrée de la console ou une mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="03a0b-109">A handle to the console input buffer or a console screen buffer.</span></span> <span data-ttu-id="03a0b-110">Le handle doit avoir le droit d’accès \*\* \_ en lecture générique\*\* .</span><span class="sxs-lookup"><span data-stu-id="03a0b-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="03a0b-111">Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="03a0b-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="03a0b-112">*dwMode* \[ dans\]</span><span class="sxs-lookup"><span data-stu-id="03a0b-112">*dwMode* \[in\]</span></span>  
<span data-ttu-id="03a0b-113">Mode d’entrée ou de sortie à définir.</span><span class="sxs-lookup"><span data-stu-id="03a0b-113">The input or output mode to be set.</span></span> <span data-ttu-id="03a0b-114">Si le paramètre *hConsoleHandle* est un handle d’entrée, le mode peut être une ou plusieurs des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="03a0b-114">If the *hConsoleHandle* parameter is an input handle, the mode can be one or more of the following values.</span></span> <span data-ttu-id="03a0b-115">Quand une console est créée, tous les modes d’entrée à l’exception de l’option **activer l' \_ \_ entrée de fenêtre** sont activés par défaut.</span><span class="sxs-lookup"><span data-stu-id="03a0b-115">When a console is created, all input modes except **ENABLE\_WINDOW\_INPUT** are enabled by default.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="03a0b-116">Value</span><span class="sxs-lookup"><span data-stu-id="03a0b-116">Value</span></span></th>
<th><span data-ttu-id="03a0b-117">Signification</span><span class="sxs-lookup"><span data-stu-id="03a0b-117">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="03a0b-118"><span id="ENABLE_ECHO_INPUT"></span><span id="enable_echo_input"></span>
<strong>ENABLE_ECHO_INPUT</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="03a0b-118"><span id="ENABLE_ECHO_INPUT"></span><span id="enable_echo_input"></span>
<strong>ENABLE_ECHO_INPUT</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="03a0b-119">Les caractères lus par la fonction <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> ou <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> sont écrits dans la mémoire tampon d’écran active au fur et à mesure de leur lecture.</span><span class="sxs-lookup"><span data-stu-id="03a0b-119">Characters read by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function are written to the active screen buffer as they are read.</span></span> <span data-ttu-id="03a0b-120">Ce mode peut être utilisé uniquement si le mode de <strong>ENABLE_LINE_INPUT</strong> est également activé.</span><span class="sxs-lookup"><span data-stu-id="03a0b-120">This mode can be used only if the <strong>ENABLE_LINE_INPUT</strong> mode is also enabled.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="03a0b-121"><span id="ENABLE_EXTENDED_FLAGS"></span><span id="enable_extended_flags"></span>
<strong>ENABLE_EXTENDED_FLAGS</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="03a0b-121"><span id="ENABLE_EXTENDED_FLAGS"></span><span id="enable_extended_flags"></span>
<strong>ENABLE_EXTENDED_FLAGS</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="03a0b-122">Requis pour activer ou désactiver les indicateurs étendus.</span><span class="sxs-lookup"><span data-stu-id="03a0b-122">Required to enable or disable extended flags.</span></span> <span data-ttu-id="03a0b-123">Consultez <strong>ENABLE_INSERT_MODE</strong> et <strong>ENABLE_QUICK_EDIT_MODE</strong>.</span><span class="sxs-lookup"><span data-stu-id="03a0b-123">See <strong>ENABLE_INSERT_MODE</strong> and <strong>ENABLE_QUICK_EDIT_MODE</strong>.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="03a0b-124"><span id="ENABLE_INSERT_MODE"></span><span id="enable_insert_mode"></span>
<strong>ENABLE_INSERT_MODE</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="03a0b-124"><span id="ENABLE_INSERT_MODE"></span><span id="enable_insert_mode"></span>
<strong>ENABLE_INSERT_MODE</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="03a0b-125">Lorsque cette option est activée, le texte entré dans une fenêtre de console est inséré à l’emplacement du curseur actuel et tout le texte qui suit cet emplacement n’est pas remplacé.</span><span class="sxs-lookup"><span data-stu-id="03a0b-125">When enabled, text entered in a console window will be inserted at the current cursor location and all text following that location will not be overwritten.</span></span> <span data-ttu-id="03a0b-126">Quand elle est désactivée, tout le texte suivant est remplacé.</span><span class="sxs-lookup"><span data-stu-id="03a0b-126">When disabled, all following text will be overwritten.</span></span></p>
<p><span data-ttu-id="03a0b-127">Pour activer ce mode, utilisez <code>ENABLE_INSERT_MODE | ENABLE_EXTENDED_FLAGS</code> .</span><span class="sxs-lookup"><span data-stu-id="03a0b-127">To enable this mode, use <code>ENABLE_INSERT_MODE | ENABLE_EXTENDED_FLAGS</code>.</span></span> <span data-ttu-id="03a0b-128">Pour désactiver ce mode, utilisez <strong>ENABLE_EXTENDED_FLAGS</strong> sans cet indicateur.</span><span class="sxs-lookup"><span data-stu-id="03a0b-128">To disable this mode, use <strong>ENABLE_EXTENDED_FLAGS</strong> without this flag.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="03a0b-129"><span id="ENABLE_LINE_INPUT"></span><span id="enable_line_input"></span>
<strong>ENABLE_LINE_INPUT</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="03a0b-129"><span id="ENABLE_LINE_INPUT"></span><span id="enable_line_input"></span>
<strong>ENABLE_LINE_INPUT</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="03a0b-130">La fonction <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> ou <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> retourne uniquement lorsqu’un caractère de retour chariot est lu.</span><span class="sxs-lookup"><span data-stu-id="03a0b-130">The <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function returns only when a carriage return character is read.</span></span> <span data-ttu-id="03a0b-131">Si ce mode est désactivé, les fonctions retournent lorsqu’un ou plusieurs caractères sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="03a0b-131">If this mode is disabled, the functions return when one or more characters are available.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="03a0b-132"><span id="ENABLE_MOUSE_INPUT"></span><span id="enable_mouse_input"></span>
<strong>ENABLE_MOUSE_INPUT</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="03a0b-132"><span id="ENABLE_MOUSE_INPUT"></span><span id="enable_mouse_input"></span>
<strong>ENABLE_MOUSE_INPUT</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="03a0b-133">Si le pointeur de la souris se trouve dans les limites de la fenêtre de console et que la fenêtre a le focus clavier, les événements de souris générés par le déplacement de la souris et les enfoncements de bouton sont placés dans la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="03a0b-133">If the mouse pointer is within the borders of the console window and the window has the keyboard focus, mouse events generated by mouse movement and button presses are placed in the input buffer.</span></span> <span data-ttu-id="03a0b-134">Ces événements sont ignorés par <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> ou <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, même quand ce mode est activé.</span><span class="sxs-lookup"><span data-stu-id="03a0b-134">These events are discarded by <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, even when this mode is enabled.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="03a0b-135"><span id="ENABLE_PROCESSED_INPUT"></span><span id="enable_processed_input"></span>
<strong>ENABLE_PROCESSED_INPUT</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="03a0b-135"><span id="ENABLE_PROCESSED_INPUT"></span><span id="enable_processed_input"></span>
<strong>ENABLE_PROCESSED_INPUT</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="03a0b-136">CTRL + C est traité par le système et n’est pas placé dans la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="03a0b-136">CTRL+C is processed by the system and is not placed in the input buffer.</span></span> <span data-ttu-id="03a0b-137">Si la mémoire tampon d’entrée est lue par <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> ou <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, d’autres clés de contrôle sont traitées par le système et ne sont pas retournées dans la mémoire tampon <strong>ReadFile</strong> ou <strong>ReadConsole</strong> .</span><span class="sxs-lookup"><span data-stu-id="03a0b-137">If the input buffer is being read by <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, other control keys are processed by the system and are not returned in the <strong>ReadFile</strong> or <strong>ReadConsole</strong> buffer.</span></span> <span data-ttu-id="03a0b-138">Si le mode de <strong>ENABLE_LINE_INPUT</strong> est également activé, les caractères de retour arrière, de retour chariot et de saut de ligne sont gérés par le système.</span><span class="sxs-lookup"><span data-stu-id="03a0b-138">If the <strong>ENABLE_LINE_INPUT</strong> mode is also enabled, backspace, carriage return, and line feed characters are handled by the system.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="03a0b-139"><span id="ENABLE_QUICK_EDIT_MODE"></span><span id="enable_quick_edit_mode"></span>
<strong>ENABLE_QUICK_EDIT_MODE</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="03a0b-139"><span id="ENABLE_QUICK_EDIT_MODE"></span><span id="enable_quick_edit_mode"></span>
<strong>ENABLE_QUICK_EDIT_MODE</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="03a0b-140">Cet indicateur permet à l’utilisateur de sélectionner et de modifier du texte à l’aide de la souris.</span><span class="sxs-lookup"><span data-stu-id="03a0b-140">This flag enables the user to use the mouse to select and edit text.</span></span></p>
<p><span data-ttu-id="03a0b-141">Pour activer ce mode, utilisez <code>ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS</code> .</span><span class="sxs-lookup"><span data-stu-id="03a0b-141">To enable this mode, use <code>ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS</code>.</span></span> <span data-ttu-id="03a0b-142">Pour désactiver ce mode, utilisez <strong>ENABLE_EXTENDED_FLAGS</strong> sans cet indicateur.</span><span class="sxs-lookup"><span data-stu-id="03a0b-142">To disable this mode, use <strong>ENABLE_EXTENDED_FLAGS</strong> without this flag.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="03a0b-143"><span id="ENABLE_WINDOW_INPUT"></span><span id="enable_window_input"></span>
<strong>ENABLE_WINDOW_INPUT</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="03a0b-143"><span id="ENABLE_WINDOW_INPUT"></span><span id="enable_window_input"></span>
<strong>ENABLE_WINDOW_INPUT</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="03a0b-144">Les interactions utilisateur qui modifient la taille de la mémoire tampon de l’écran de la console sont signalées dans la mémoire tampon d’entrée de la console&#39;s.</span><span class="sxs-lookup"><span data-stu-id="03a0b-144">User interactions that change the size of the console screen buffer are reported in the console&#39;s input buffer.</span></span> <span data-ttu-id="03a0b-145">Les informations relatives à ces événements peuvent être lues à partir de la mémoire tampon d’entrée par les applications à l’aide de la fonction <a href="readconsoleinput.md" data-raw-source="[&lt;strong&gt;ReadConsoleInput&lt;/strong&gt;](readconsoleinput.md)"><strong>ReadConsoleInput</strong></a> , mais pas par celles utilisant <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> ou <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>.</span><span class="sxs-lookup"><span data-stu-id="03a0b-145">Information about these events can be read from the input buffer by applications using the <a href="readconsoleinput.md" data-raw-source="[&lt;strong&gt;ReadConsoleInput&lt;/strong&gt;](readconsoleinput.md)"><strong>ReadConsoleInput</strong></a> function, but not by those using <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="03a0b-146"><span id="ENABLE_VIRTUAL_TERMINAL_INPUT"></span><span id="enable_virtual_terminal_input"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_INPUT</strong> 0x0200</span><span class="sxs-lookup"><span data-stu-id="03a0b-146"><span id="ENABLE_VIRTUAL_TERMINAL_INPUT"></span><span id="enable_virtual_terminal_input"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_INPUT</strong> 0x0200</span></span></td>
<td><p><span data-ttu-id="03a0b-147">La définition de cet indicateur indique au moteur de traitement des terminaux virtuels de convertir les entrées utilisateur reçues par la fenêtre de console en séquences de terminaux virtuels de la console qui peuvent être récupérées par une application de prise en charge via les fonctions ReadFile ou ReadConsole.</span><span class="sxs-lookup"><span data-stu-id="03a0b-147">Setting this flag directs the Virtual Terminal processing engine to convert user input received by the console window into Console Virtual Terminal Sequences that can be retrieved by a supporting application through ReadFile or ReadConsole functions.</span></span></p>
<p><span data-ttu-id="03a0b-148">L’utilisation classique de cet indicateur est conçue conjointement avec ENABLE_VIRTUAL_TERMINAL_PROCESSING sur le handle de sortie pour se connecter à une application qui communique exclusivement par le biais de séquences de terminaux virtuels.</span><span class="sxs-lookup"><span data-stu-id="03a0b-148">The typical usage of this flag is intended in conjunction with ENABLE_VIRTUAL_TERMINAL_PROCESSING on the output handle to connect to an application that communicates exclusively via virtual terminal sequences.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
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

 

<span data-ttu-id="03a0b-149">Si le paramètre *hConsoleHandle* est un descripteur de mémoire tampon d’écran, le mode peut être une ou plusieurs des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="03a0b-149">If the *hConsoleHandle* parameter is a screen buffer handle, the mode can be one or more of the following values.</span></span> <span data-ttu-id="03a0b-150">Quand une mémoire tampon d’écran est créée, les deux modes de sortie sont activés par défaut.</span><span class="sxs-lookup"><span data-stu-id="03a0b-150">When a screen buffer is created, both output modes are enabled by default.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="03a0b-151">Value</span><span class="sxs-lookup"><span data-stu-id="03a0b-151">Value</span></span></th>
<th><span data-ttu-id="03a0b-152">Signification</span><span class="sxs-lookup"><span data-stu-id="03a0b-152">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="03a0b-153"><span id="ENABLE_PROCESSED_OUTPUT"></span><span id="enable_processed_output"></span>
<strong>ENABLE_PROCESSED_OUTPUT</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="03a0b-153"><span id="ENABLE_PROCESSED_OUTPUT"></span><span id="enable_processed_output"></span>
<strong>ENABLE_PROCESSED_OUTPUT</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="03a0b-154">Les caractères écrits par la fonction <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> ou <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> ou renvoyés par la fonction <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> ou <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> sont examinés pour les séquences de contrôle ASCII et l’action correcte est effectuée.</span><span class="sxs-lookup"><span data-stu-id="03a0b-154">Characters written by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> function or echoed by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function are examined for ASCII control sequences and the correct action is performed.</span></span> <span data-ttu-id="03a0b-155">Les caractères retour arrière, tabulation, cloche, retour chariot et saut de ligne sont traités.</span><span class="sxs-lookup"><span data-stu-id="03a0b-155">Backspace, tab, bell, carriage return, and line feed characters are processed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="03a0b-156"><span id="ENABLE_WRAP_AT_EOL_OUTPUT"></span><span id="enable_wrap_at_eol_output"></span>
<strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="03a0b-156"><span id="ENABLE_WRAP_AT_EOL_OUTPUT"></span><span id="enable_wrap_at_eol_output"></span>
<strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="03a0b-157">Lors de l’écriture avec <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> ou <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> ou l’écho avec <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> ou <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, le curseur se déplace au début de la ligne suivante lorsqu’il atteint la fin de la ligne actuelle.</span><span class="sxs-lookup"><span data-stu-id="03a0b-157">When writing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> or echoing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, the cursor moves to the beginning of the next row when it reaches the end of the current row.</span></span> <span data-ttu-id="03a0b-158">Cela entraîne le défilement automatique des lignes affichées dans la fenêtre de la console lorsque le curseur avance au-delà de la dernière ligne de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="03a0b-158">This causes the rows displayed in the console window to scroll up automatically when the cursor advances beyond the last row in the window.</span></span> <span data-ttu-id="03a0b-159">Cela permet également de faire défiler le contenu de la mémoire tampon d’écran de la console vers le haut (en ignorant la ligne supérieure de la mémoire tampon d’écran de la console) lorsque le curseur avance au-delà de la dernière ligne dans la mémoire tampon de l’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="03a0b-159">It also causes the contents of the console screen buffer to scroll up (discarding the top row of the console screen buffer) when the cursor advances beyond the last row in the console screen buffer.</span></span> <span data-ttu-id="03a0b-160">Si ce mode est désactivé, le dernier caractère de la ligne est remplacé par les caractères suivants.</span><span class="sxs-lookup"><span data-stu-id="03a0b-160">If this mode is disabled, the last character in the row is overwritten with any subsequent characters.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="03a0b-161"><span id="ENABLE_VIRTUAL_TERMINAL_PROCESSING"></span><span id="enable_virtual_terminal_processing"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_PROCESSING</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="03a0b-161"><span id="ENABLE_VIRTUAL_TERMINAL_PROCESSING"></span><span id="enable_virtual_terminal_processing"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_PROCESSING</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="03a0b-162">Lors de l’écriture avec <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> ou <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, les caractères sont analysés pour VT100 et les séquences de caractères de contrôle similaires qui contrôlent le mouvement du curseur, le mode couleur/police et d’autres opérations qui peuvent également être effectuées via les API de console existantes.</span><span class="sxs-lookup"><span data-stu-id="03a0b-162">When writing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, characters are parsed for VT100 and similar control character sequences that control cursor movement, color/font mode, and other operations that can also be performed via the existing Console APIs.</span></span> <span data-ttu-id="03a0b-163">Pour plus d’informations, consultez <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">séquences de terminaux virtuels de la console</a>.</span><span class="sxs-lookup"><span data-stu-id="03a0b-163">For more information, see <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">Console Virtual Terminal Sequences</a>.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="03a0b-164"><span id="DISABLE_NEWLINE_AUTO_RETURN"></span><span id="disable_newline_auto_return"></span>
<strong>DISABLE_NEWLINE_AUTO_RETURN</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="03a0b-164"><span id="DISABLE_NEWLINE_AUTO_RETURN"></span><span id="disable_newline_auto_return"></span>
<strong>DISABLE_NEWLINE_AUTO_RETURN</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="03a0b-165">Lors de l’écriture avec <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> ou <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, cela ajoute un État supplémentaire à l’encapsulation de fin de ligne qui peut retarder le déplacement du curseur et les opérations de défilement de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="03a0b-165">When writing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, this adds an additional state to end-of-line wrapping that can delay the cursor move and buffer scroll operations.</span></span></p>
<p><span data-ttu-id="03a0b-166">Normalement, lorsque ENABLE_WRAP_AT_EOL_OUTPUT est définie et que le texte atteint la fin de la ligne, le curseur passe immédiatement à la ligne suivante et le contenu de la mémoire tampon défile d’une ligne vers le haut.</span><span class="sxs-lookup"><span data-stu-id="03a0b-166">Normally when ENABLE_WRAP_AT_EOL_OUTPUT is set and text reaches the end of the line, the cursor will immediately move to the next line and the contents of the buffer will scroll up by one line.</span></span> <span data-ttu-id="03a0b-167">Contrairement à cet indicateur, l’opération de défilement et le déplacement de curseur sont retardés jusqu’à ce que le caractère suivant arrive.</span><span class="sxs-lookup"><span data-stu-id="03a0b-167">In contrast with this flag set, the scroll operation and cursor move is delayed until the next character arrives.</span></span> <span data-ttu-id="03a0b-168">Le caractère écrit est imprimé à la position finale sur la ligne et le curseur se trouve au-dessus de ce caractère comme si ENABLE_WRAP_AT_EOL_OUTPUT était désactivé, mais le prochain caractère imprimable sera imprimé comme si ENABLE_WRAP_AT_EOL_OUTPUT était activé.</span><span class="sxs-lookup"><span data-stu-id="03a0b-168">The written character will be printed in the final position on the line and the cursor will remain above this character as if ENABLE_WRAP_AT_EOL_OUTPUT was off, but the next printable character will be printed as if ENABLE_WRAP_AT_EOL_OUTPUT is on.</span></span> <span data-ttu-id="03a0b-169">Aucun remplacement ne se produit.</span><span class="sxs-lookup"><span data-stu-id="03a0b-169">No overwrite will occur.</span></span> <span data-ttu-id="03a0b-170">Plus précisément, le curseur avance rapidement jusqu’à la ligne suivante, un défilement est effectué si nécessaire, le caractère est imprimé et le curseur avance d’une position.</span><span class="sxs-lookup"><span data-stu-id="03a0b-170">Specifically, the cursor quickly advances down to the following line, a scroll is performed if necessary, the character is printed, and the cursor advances one more position.</span></span></p>
<p><span data-ttu-id="03a0b-171">L’utilisation classique de cet indicateur est conçue conjointement avec la définition de ENABLE_VIRTUAL_TERMINAL_PROCESSING pour mieux émuler un émulateur de terminal dans lequel l’écriture du dernier caractère sur l’écran (dans le coin inférieur droit) sans déclencher de défilement immédiat est le comportement souhaité.</span><span class="sxs-lookup"><span data-stu-id="03a0b-171">The typical usage of this flag is intended in conjunction with setting ENABLE_VIRTUAL_TERMINAL_PROCESSING to better emulate a terminal emulator where writing the final character on the screen (in the bottom right corner) without triggering an immediate scroll is the desired behavior.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="03a0b-172"><span id="ENABLE_LVB_GRID_WORLDWIDE"></span><span id="enable_lvb_grid_worldwide"></span>
<strong>ENABLE_LVB_GRID_WORLDWIDE</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="03a0b-172"><span id="ENABLE_LVB_GRID_WORLDWIDE"></span><span id="enable_lvb_grid_worldwide"></span>
<strong>ENABLE_LVB_GRID_WORLDWIDE</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="03a0b-173">Les API permettant d’écrire des attributs de caractères, y compris <a href="writeconsoleoutput.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutput&lt;/strong&gt;](writeconsoleoutput.md)"><strong>WriteConsoleOutput</strong></a> et <a href="writeconsoleoutputattribute.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutputAttribute&lt;/strong&gt;](writeconsoleoutputattribute.md)"><strong>WriteConsoleOutputAttribute</strong></a> , permettent d’utiliser des indicateurs d' <a href="https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes" data-raw-source="[character attributes](https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes)">attributs de caractères</a> pour ajuster la couleur du premier plan et de l’arrière-plan du texte.</span><span class="sxs-lookup"><span data-stu-id="03a0b-173">The APIs for writing character attributes including <a href="writeconsoleoutput.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutput&lt;/strong&gt;](writeconsoleoutput.md)"><strong>WriteConsoleOutput</strong></a> and <a href="writeconsoleoutputattribute.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutputAttribute&lt;/strong&gt;](writeconsoleoutputattribute.md)"><strong>WriteConsoleOutputAttribute</strong></a> allow the usage of flags from <a href="https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes" data-raw-source="[character attributes](https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes)">character attributes</a> to adjust the color of the foreground and background of text.</span></span> <span data-ttu-id="03a0b-174">En outre, une plage d’indicateurs DBCS a été spécifiée avec le préfixe COMMON_LVB.</span><span class="sxs-lookup"><span data-stu-id="03a0b-174">Additionally, a range of DBCS flags was specified with the COMMON_LVB prefix.</span></span> <span data-ttu-id="03a0b-175">Historiquement, ces indicateurs ne fonctionnent que dans les pages de codes DBCS pour les langues chinoises, japonaises et coréennes.</span><span class="sxs-lookup"><span data-stu-id="03a0b-175">Historically, these flags only functioned in DBCS code pages for Chinese, Japanese, and Korean languages.</span></span></p>
<p><span data-ttu-id="03a0b-176">À l’exception des indicateurs d’octet de début et d’octet de fin, les indicateurs restants qui décrivent le dessin de lignes et la vidéo inverse (swap Foreground et Background Colors) peuvent être utiles pour d’autres langages afin de mettre en évidence certaines parties de la sortie.</span><span class="sxs-lookup"><span data-stu-id="03a0b-176">With exception of the leading byte and trailing byte flags, the remaining flags describing line drawing and reverse video (swap foreground and background colors) can be useful for other languages to emphasize portions of output.</span></span></p>
<p><span data-ttu-id="03a0b-177">La définition de cet indicateur de mode de la console permet d’utiliser ces attributs dans chaque page de codes de chaque langue.</span><span class="sxs-lookup"><span data-stu-id="03a0b-177">Setting this console mode flag will allow these attributes to be used in every code page on every language.</span></span></p>
<p><span data-ttu-id="03a0b-178">Elle est désactivée par défaut pour assurer la compatibilité avec les applications connues qui ont historiquement pris l’avantage de la console en ignorant ces indicateurs sur les ordinateurs non-CJK pour stocker les bits dans ces champs à des fins ou par accident.</span><span class="sxs-lookup"><span data-stu-id="03a0b-178">It is off by default to maintain compatibility with known applications that have historically taken advantage of the console ignoring these flags on non-CJK machines to store bits in these fields for their own purposes or by accident.</span></span></p>
<p><span data-ttu-id="03a0b-179">Notez que l’utilisation du mode de ENABLE_VIRTUAL_TERMINAL_PROCESSING peut entraîner la définition de la grille LVB et des indicateurs de vidéo inversée, alors que cet indicateur est toujours désactivé si l’application attachée demande la soulignement ou l’inverse de la vidéo via des <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">séquences de terminaux virtuels</a>de la console.</span><span class="sxs-lookup"><span data-stu-id="03a0b-179">Note that using the ENABLE_VIRTUAL_TERMINAL_PROCESSING mode can result in LVB grid and reverse video flags being set while this flag is still off if the attached application requests underlining or inverse video via <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">Console Virtual Terminal Sequences</a>.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="03a0b-180">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="03a0b-180">Return value</span></span>
------------

<span data-ttu-id="03a0b-181">Si la fonction est réussie, la valeur de retour est différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="03a0b-181">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="03a0b-182">Si la fonction échoue, la valeur de retour est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="03a0b-182">If the function fails, the return value is zero.</span></span> <span data-ttu-id="03a0b-183">Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="03a0b-183">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="03a0b-184">Remarques</span><span class="sxs-lookup"><span data-stu-id="03a0b-184">Remarks</span></span>
-------

<span data-ttu-id="03a0b-185">Une console se compose d’une mémoire tampon d’entrée et d’une ou plusieurs mémoires tampons d’écran.</span><span class="sxs-lookup"><span data-stu-id="03a0b-185">A console consists of an input buffer and one or more screen buffers.</span></span> <span data-ttu-id="03a0b-186">Le mode d’une mémoire tampon de console détermine le comportement de la console pendant les opérations d’entrée et de sortie (e/s).</span><span class="sxs-lookup"><span data-stu-id="03a0b-186">The mode of a console buffer determines how the console behaves during input and output (I/O) operations.</span></span> <span data-ttu-id="03a0b-187">Un jeu de constantes d’indicateur est utilisé avec les handles d’entrée, et un autre jeu est utilisé avec les descripteurs de mémoire tampon d’écran (sortie).</span><span class="sxs-lookup"><span data-stu-id="03a0b-187">One set of flag constants is used with input handles, and another set is used with screen buffer (output) handles.</span></span> <span data-ttu-id="03a0b-188">La définition des modes de sortie d’une mémoire tampon d’écran n’affecte pas les modes de sortie des autres mémoires tampons d’écran.</span><span class="sxs-lookup"><span data-stu-id="03a0b-188">Setting the output modes of one screen buffer does not affect the output modes of other screen buffers.</span></span>

<span data-ttu-id="03a0b-189">Les modes **activer l' \_ \_ entrée** de la ligne et **activer l' \_ \_ entrée** de l’écho affectent uniquement les processus qui utilisent [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ou [**ReadConsole**](readconsole.md) pour lire à partir de la mémoire tampon d’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="03a0b-189">The **ENABLE\_LINE\_INPUT** and **ENABLE\_ECHO\_INPUT** modes only affect processes that use [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) to read from the console's input buffer.</span></span> <span data-ttu-id="03a0b-190">De même, l' **activation du mode \_ \_ d’entrée traité** affecte principalement les utilisateurs de **ReadFile** et **ReadConsole** , à ceci près qu’elle détermine également si l’entrée Ctrl + C est signalée dans la mémoire tampon d’entrée (pour être lue par la fonction [**ReadConsoleInput**](readconsoleinput.md) ) ou si elle est transmise à une fonction [**HandlerRoutine**](handlerroutine.md) définie par l’application.</span><span class="sxs-lookup"><span data-stu-id="03a0b-190">Similarly, the **ENABLE\_PROCESSED\_INPUT** mode primarily affects **ReadFile** and **ReadConsole** users, except that it also determines whether Ctrl+C input is reported in the input buffer (to be read by the [**ReadConsoleInput**](readconsoleinput.md) function) or is passed to a [**HandlerRoutine**](handlerroutine.md) function defined by the application.</span></span>

<span data-ttu-id="03a0b-191">Les modes **activer l' \_ \_ entrée** de la fenêtre et \*\*activer \_ la souris \_ \*\* déterminent si les interactions de l’utilisateur impliquant le redimensionnement de fenêtre et les actions de la souris sont signalées dans la mémoire tampon d’entrée ou ignorées.</span><span class="sxs-lookup"><span data-stu-id="03a0b-191">The **ENABLE\_WINDOW\_INPUT** and **ENABLE\_MOUSE\_INPUT** modes determine whether user interactions involving window resizing and mouse actions are reported in the input buffer or discarded.</span></span> <span data-ttu-id="03a0b-192">Ces événements peuvent être lus par [**ReadConsoleInput**](readconsoleinput.md), mais ils sont toujours filtrés par [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**ReadConsole**](readconsole.md).</span><span class="sxs-lookup"><span data-stu-id="03a0b-192">These events can be read by [**ReadConsoleInput**](readconsoleinput.md), but they are always filtered by [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md).</span></span>

<span data-ttu-id="03a0b-193">Les modes de sortie **activer le \_ \_ résultat traité** et **activer le \_ Retour à la ligne \_ en fin de \_ \_ vie** affectent uniquement les processus utilisant [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) , [**ReadConsole**](readconsole.md) et [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ou [**WriteConsole**](writeconsole.md).</span><span class="sxs-lookup"><span data-stu-id="03a0b-193">The **ENABLE\_PROCESSED\_OUTPUT** and **ENABLE\_WRAP\_AT\_EOL\_OUTPUT** modes only affect processes using [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md).</span></span>

<span data-ttu-id="03a0b-194">Pour déterminer le mode actuel d’une mémoire tampon d’entrée de console ou d’une mémoire tampon d’écran, utilisez la fonction [**GetConsoleMode**](getconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="03a0b-194">To determine the current mode of a console input buffer or a screen buffer, use the [**GetConsoleMode**](getconsolemode.md) function.</span></span>

<a name="examples"></a><span data-ttu-id="03a0b-195">Exemples</span><span class="sxs-lookup"><span data-stu-id="03a0b-195">Examples</span></span>
--------

<span data-ttu-id="03a0b-196">Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="03a0b-196">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="03a0b-197">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="03a0b-197">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="03a0b-198">Client minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="03a0b-198">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="03a0b-199">Windows 2000 professionnel [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="03a0b-199">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="03a0b-200">Serveur minimal pris en charge</span><span class="sxs-lookup"><span data-stu-id="03a0b-200">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="03a0b-201">Serveur Windows 2000 [applications de bureau uniquement]</span><span class="sxs-lookup"><span data-stu-id="03a0b-201">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="03a0b-202">En-tête</span><span class="sxs-lookup"><span data-stu-id="03a0b-202">Header</span></span></p></td>
<td><span data-ttu-id="03a0b-203">ConsoleApi. h (via wincon. h, incluez Windows. h)</span><span class="sxs-lookup"><span data-stu-id="03a0b-203">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="03a0b-204">Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="03a0b-204">Library</span></span></p></td>
<td><span data-ttu-id="03a0b-205">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="03a0b-205">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="03a0b-206">DLL</span><span class="sxs-lookup"><span data-stu-id="03a0b-206">DLL</span></span></p></td>
<td><span data-ttu-id="03a0b-207">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="03a0b-207">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="03a0b-208"><span id="see_also"></span>Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03a0b-208"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="03a0b-209">Fonctions de la console</span><span class="sxs-lookup"><span data-stu-id="03a0b-209">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="03a0b-210">Modes de la console</span><span class="sxs-lookup"><span data-stu-id="03a0b-210">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="03a0b-211">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="03a0b-211">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="03a0b-212">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="03a0b-212">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="03a0b-213">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="03a0b-213">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="03a0b-214">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="03a0b-214">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="03a0b-215">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="03a0b-215">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="03a0b-216">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="03a0b-216">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="03a0b-217">**Appel**</span><span class="sxs-lookup"><span data-stu-id="03a0b-217">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




