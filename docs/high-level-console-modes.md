---
title: Modes de console de haut niveau
description: Le comportement des fonctions de console de haut niveau est affecté par les modes d’entrée et de sortie de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_high\_level\_console\_modes'
- base.high\_level\_console\_modes
- consoles.high\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3ec915eb-333d-484d-a14d-46377b503ecc
ms.openlocfilehash: b5b24056a1283d46cbfe21737bd930318042c039
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059084"
---
# <a name="high-level-console-modes"></a><span data-ttu-id="2c476-104">Modes de console de haut niveau</span><span class="sxs-lookup"><span data-stu-id="2c476-104">High-Level Console Modes</span></span>


<span data-ttu-id="2c476-105">Le comportement des fonctions de console de haut niveau est affecté par les modes d’entrée et de sortie de la console.</span><span class="sxs-lookup"><span data-stu-id="2c476-105">The behavior of the high-level console functions is affected by the console input and output modes.</span></span> <span data-ttu-id="2c476-106">Tous les modes d’entrée de la console suivants sont activés pour la mémoire tampon d’entrée d’une console lors de la création d’une console :</span><span class="sxs-lookup"><span data-stu-id="2c476-106">All of the following console input modes are enabled for a console's input buffer when a console is created:</span></span>

- <span data-ttu-id="2c476-107">Mode de saisie de ligne</span><span class="sxs-lookup"><span data-stu-id="2c476-107">Line input mode</span></span>
- <span data-ttu-id="2c476-108">Mode de saisie traité</span><span class="sxs-lookup"><span data-stu-id="2c476-108">Processed input mode</span></span>
- <span data-ttu-id="2c476-109">Mode de saisie d’écho</span><span class="sxs-lookup"><span data-stu-id="2c476-109">Echo input mode</span></span>

<span data-ttu-id="2c476-110">Les deux modes de sortie de console suivants sont activés pour une mémoire tampon d’écran de console lors de sa création :</span><span class="sxs-lookup"><span data-stu-id="2c476-110">Both of the following console output modes are enabled for a console screen buffer when it is created:</span></span>

- <span data-ttu-id="2c476-111">Mode de sortie traité</span><span class="sxs-lookup"><span data-stu-id="2c476-111">Processed output mode</span></span>
- <span data-ttu-id="2c476-112">Retour en mode de sortie de EOL</span><span class="sxs-lookup"><span data-stu-id="2c476-112">Wrapping at EOL output mode</span></span>

<span data-ttu-id="2c476-113">Les trois modes d’entrée, ainsi que le mode de sortie traité, sont conçus pour fonctionner ensemble.</span><span class="sxs-lookup"><span data-stu-id="2c476-113">All three input modes, along with processed output mode, are designed to work together.</span></span> <span data-ttu-id="2c476-114">Il est préférable d’activer ou de désactiver tous ces modes en tant que groupe.</span><span class="sxs-lookup"><span data-stu-id="2c476-114">It is best to either enable or disable all of these modes as a group.</span></span> <span data-ttu-id="2c476-115">Lorsque toutes les sont activées, l’application est dite en mode « cuit », ce qui signifie que la majeure partie du traitement est gérée pour l’application.</span><span class="sxs-lookup"><span data-stu-id="2c476-115">When all are enabled, the application is said to be in "cooked" mode, which means that most of the processing is handled for the application.</span></span> <span data-ttu-id="2c476-116">Lorsque tous les sont désactivés, l’application est en mode « brut », ce qui signifie que l’entrée n’est pas filtrée et que le traitement est laissé à l’application.</span><span class="sxs-lookup"><span data-stu-id="2c476-116">When all are disabled, the application is in "raw" mode, which means that input is unfiltered and any processing is left to the application.</span></span>

<span data-ttu-id="2c476-117">Une application peut utiliser la fonction [**GetConsoleMode**](getconsolemode.md) pour déterminer le mode actuel de la mémoire tampon d’entrée ou de mémoire tampon d’entrée d’une console.</span><span class="sxs-lookup"><span data-stu-id="2c476-117">An application can use the [**GetConsoleMode**](getconsolemode.md) function to determine the current mode of a console's input buffer or screen buffer.</span></span> <span data-ttu-id="2c476-118">Vous pouvez activer ou désactiver l’un de ces modes en utilisant les valeurs suivantes dans la fonction [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="2c476-118">You can enable or disable any of these modes by using the following values in the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="2c476-119">Notez que la définition du mode de sortie d’une mémoire tampon d’écran n’affecte pas le mode de sortie des autres mémoires tampons d’écran.</span><span class="sxs-lookup"><span data-stu-id="2c476-119">Note that setting the output mode of one screen buffer does not affect the output mode of other screen buffers.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="2c476-120">Mode</span><span class="sxs-lookup"><span data-stu-id="2c476-120">Mode</span></span></th>
<th><span data-ttu-id="2c476-121">Description</span><span class="sxs-lookup"><span data-stu-id="2c476-121">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="2c476-122"><strong>ENABLE_PROCESSED_INPUT</strong></span><span class="sxs-lookup"><span data-stu-id="2c476-122"><strong>ENABLE_PROCESSED_INPUT</strong></span></span></td>
<td><span data-ttu-id="2c476-123">Utilisé avec un handle d’entrée de console pour obliger le système à traiter toute entrée de modification ou de clé de contrôle du système au lieu de la retourner comme entrée dans l’opération de lecture&#39;tampon s.</span><span class="sxs-lookup"><span data-stu-id="2c476-123">Used with a console input handle to cause the system to process any system editing or control key input rather than returning it as input in the read operation&#39;s buffer.</span></span> <span data-ttu-id="2c476-124">Si l’entrée de ligne est également activée, les retours arrière et les retours chariot sont correctement gérés.</span><span class="sxs-lookup"><span data-stu-id="2c476-124">If line input is also enabled, backspaces and carriage returns are handled correctly.</span></span> <span data-ttu-id="2c476-125">Un retour arrière fait avancer le curseur d’un espace sans affecter le caractère à la position du curseur.</span><span class="sxs-lookup"><span data-stu-id="2c476-125">A backspace causes the cursor to move back one space without affecting the character at the cursor position.</span></span> <span data-ttu-id="2c476-126">Un retour chariot est converti en combinaison retour chariot-saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="2c476-126">A carriage return is converted to carriage return – line feed character combination.</span></span> <span data-ttu-id="2c476-127">Si le mode d’entrée ECHO est activé et que la sortie doit refléter la modification du système, la sortie traitée doit être activée pour la mémoire tampon d’écran active.</span><span class="sxs-lookup"><span data-stu-id="2c476-127">If echo input mode is enabled and the output should reflect system editing, processed output must be enabled for the active screen buffer.</span></span> <span data-ttu-id="2c476-128">Si l’entrée traitée est activée, la combinaison de touches CTRL + C est transmise au gestionnaire approprié, que l’entrée de ligne soit activée ou non.</span><span class="sxs-lookup"><span data-stu-id="2c476-128">If processed input is enabled, the CTRL+C key combination is passed on to the appropriate handler regardless of whether line input is enabled.</span></span> <span data-ttu-id="2c476-129">Pour plus d’informations sur les gestionnaires de contrôles, consultez <a href="console-control-handlers.md" data-raw-source="[Console Control Handlers](console-control-handlers.md)">gestionnaires de contrôle de console</a>.</span><span class="sxs-lookup"><span data-stu-id="2c476-129">For more information about control handlers, see <a href="console-control-handlers.md" data-raw-source="[Console Control Handlers](console-control-handlers.md)">Console Control Handlers</a>.</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="2c476-130"><strong>ENABLE_LINE_INPUT</strong></span><span class="sxs-lookup"><span data-stu-id="2c476-130"><strong>ENABLE_LINE_INPUT</strong></span></span></td>
<td><span data-ttu-id="2c476-131">Utilisé avec un handle d’entrée de console pour provoquer le retour des fonctions <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> et <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> lorsque la touche entrée est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="2c476-131">Used with a console input handle to cause the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> and <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> functions to return when the ENTER key is pressed.</span></span> <span data-ttu-id="2c476-132">Si le mode de saisie de ligne est désactivé, les fonctions retournent lorsqu’un ou plusieurs caractères sont disponibles dans la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="2c476-132">If line input mode is disabled, the functions return when one or more characters are available in the input buffer.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="2c476-133"><strong>ENABLE_ECHO_INPUT</strong></span><span class="sxs-lookup"><span data-stu-id="2c476-133"><strong>ENABLE_ECHO_INPUT</strong></span></span></td>
<td><span data-ttu-id="2c476-134">Utilisé avec un handle d’entrée de console pour que l’entrée au clavier lue par la fonction <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> ou <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> soit répercutée dans la mémoire tampon d’écran active.</span><span class="sxs-lookup"><span data-stu-id="2c476-134">Used with a console input handle to cause keyboard input read by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function to be echoed to the active screen buffer.</span></span> <span data-ttu-id="2c476-135">Les caractères sont répercutés uniquement si le processus qui appelle <strong>ReadFile</strong> ou <strong>ReadConsole</strong> a un handle ouvert à la mémoire tampon d’écran active.</span><span class="sxs-lookup"><span data-stu-id="2c476-135">Characters are echoed only if the process that calls <strong>ReadFile</strong> or <strong>ReadConsole</strong> has an open handle to the active screen buffer.</span></span> <span data-ttu-id="2c476-136">Le mode ECHO ne peut pas être activé, sauf si l’entrée de ligne est également activée.</span><span class="sxs-lookup"><span data-stu-id="2c476-136">Echo mode cannot be enabled unless line input is also enabled.</span></span> <span data-ttu-id="2c476-137">Le mode de sortie de la mémoire tampon d’écran active affecte la façon dont les entrées en écho sont affichées.</span><span class="sxs-lookup"><span data-stu-id="2c476-137">The output mode of the active screen buffer affects the way echoed input is displayed.</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="2c476-138"><strong>ENABLE_PROCESSED_OUTPUT</strong></span><span class="sxs-lookup"><span data-stu-id="2c476-138"><strong>ENABLE_PROCESSED_OUTPUT</strong></span></span></td>
<td><span data-ttu-id="2c476-139">Utilisé avec un handle de mémoire tampon d’écran de la console pour obliger le système à exécuter l’action appropriée pour les caractères de contrôle ANSI écrits dans une mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="2c476-139">Used with a console screen buffer handle to cause the system to perform the appropriate action for ANSI control characters that are written to a screen buffer.</span></span> <span data-ttu-id="2c476-140">Les caractères retour arrière, tabulation, cloche, retour chariot et saut de ligne sont traités.</span><span class="sxs-lookup"><span data-stu-id="2c476-140">The backspace, tab, bell, carriage return, and line feed characters are processed.</span></span> <span data-ttu-id="2c476-141">Un caractère de tabulation déplace le curseur sur le taquet de tabulation suivant, qui se produit tous les huit caractères.</span><span class="sxs-lookup"><span data-stu-id="2c476-141">A tab character moves the cursor to the next tab stop, which occurs every eight characters.</span></span> <span data-ttu-id="2c476-142">Un caractère de cloche émet un bref instant.</span><span class="sxs-lookup"><span data-stu-id="2c476-142">A bell character sounds a short tone.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="2c476-143"><strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong></span><span class="sxs-lookup"><span data-stu-id="2c476-143"><strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong></span></span></td>
<td><span data-ttu-id="2c476-144">Utilisé avec un handle de mémoire tampon d’écran de la console pour faire passer la position de sortie actuelle (position du curseur) à la première colonne de la ligne suivante (ligne) lorsque la fin de la ligne actuelle est atteinte.</span><span class="sxs-lookup"><span data-stu-id="2c476-144">Used with a console screen buffer handle to cause the current output position (cursor position) to move to the first column in the next row (line) when the end of the current row is reached.</span></span> <span data-ttu-id="2c476-145">Si le bas de la zone de fenêtre est atteint, l’origine de la fenêtre est déplacée d’une ligne vers le bas.</span><span class="sxs-lookup"><span data-stu-id="2c476-145">If the bottom of the window region is reached, the window origin is moved down one row.</span></span> <span data-ttu-id="2c476-146">Ce déplacement a pour effet de faire défiler le contenu de la fenêtre vers le haut d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="2c476-146">This movement has the effect of scrolling the contents of the window up one row.</span></span> <span data-ttu-id="2c476-147">Si le bas de la mémoire tampon de l’écran de la console est atteint, le contenu de la mémoire tampon de l’écran de la console fait défiler d’une ligne vers le haut et la ligne supérieure de la mémoire tampon de l’écran de la console est ignorée.</span><span class="sxs-lookup"><span data-stu-id="2c476-147">If the bottom of the console screen buffer is reached, the contents of the console screen buffer are scrolled up one row, and the top row of the console screen buffer is discarded.</span></span>
<p><span data-ttu-id="2c476-148">Si ce mode est désactivé, le dernier caractère de la ligne est remplacé par les caractères suivants.</span><span class="sxs-lookup"><span data-stu-id="2c476-148">If this mode is disabled, the last character in the row is overwritten with any subsequent characters.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

 

 




