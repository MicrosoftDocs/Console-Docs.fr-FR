---
title: Séquences de terminal virtuel de console
description: Les séquences de terminal virtuel sont des séquences de caractères de contrôle qui peuvent contrôler le déplacement du curseur, le mode couleur/police et d’autres opérations lors de leur écriture dans le flux de sortie.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: A5C553A5-FD84-4D16-A814-EDB3B8699B91
ms.openlocfilehash: 45ee5518ec8ea2da840d2a4442efd9e0d4346526
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "93039147"
---
# <a name="console-virtual-terminal-sequences"></a><span data-ttu-id="63d69-104">Séquences de terminal virtuel de console</span><span class="sxs-lookup"><span data-stu-id="63d69-104">Console Virtual Terminal Sequences</span></span>


<span data-ttu-id="63d69-105">Les séquences de terminal virtuel sont des séquences de caractères de contrôle qui peuvent contrôler le déplacement du curseur, le mode couleur/police et d’autres opérations lors de leur écriture dans le flux de sortie.</span><span class="sxs-lookup"><span data-stu-id="63d69-105">Virtual terminal sequences are control character sequences that can control cursor movement, color/font mode, and other operations when written to the output stream.</span></span> <span data-ttu-id="63d69-106">Les séquences peuvent également être reçues sur le flux d’entrée en réponse à une séquence d’informations de requête de flux de sortie ou en tant qu’encodage d’entrée d’utilisateur quand le mode approprié est défini.</span><span class="sxs-lookup"><span data-stu-id="63d69-106">Sequences may also be received on the input stream in response to an output stream query information sequence or as an encoding of user input when the appropriate mode is set.</span></span>

<span data-ttu-id="63d69-107">Pour configurer ce comportement, vous pouvez utiliser les fonctions [**GetConsoleMode**](getconsolemode.md) et [**SetConsoleMode**](setconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="63d69-107">You can use [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions to configure this behavior.</span></span> <span data-ttu-id="63d69-108">Vous trouverez un exemple de la méthode suggérée pour activer les comportements des terminaux virtuels à la fin de ce document.</span><span class="sxs-lookup"><span data-stu-id="63d69-108">A sample of the suggested way to enable virtual terminal behaviors is included at the end of this document.</span></span>

<span data-ttu-id="63d69-109">Le comportement des séquences suivantes est basé sur les technologies d’émulateur de terminal VT100 et dérivés, plus spécifiquement l’émulateur de terminal xterm.</span><span class="sxs-lookup"><span data-stu-id="63d69-109">The behavior of the following sequences is based on the VT100 and derived terminal emulator technologies, most specifically the xterm terminal emulator.</span></span> <span data-ttu-id="63d69-110">Pour plus d’informations sur les séquences de terminal, consultez <http://vt100.net> et <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span><span class="sxs-lookup"><span data-stu-id="63d69-110">More information about terminal sequences can be found at <http://vt100.net> and at <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span></span>

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span data-ttu-id="63d69-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Séquences de sortie</span><span class="sxs-lookup"><span data-stu-id="63d69-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Output Sequences</span></span>


<span data-ttu-id="63d69-112">Les séquences de terminal suivantes sont interceptées par l’hôte de la console quand elles sont écrites dans le flux de sortie, si l’indicateur ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING est défini sur le descripteur de mémoire tampon d’écran à l’aide de la fonction [**SetConsoleMode**](setconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="63d69-112">The following terminal sequences are intercepted by the console host when written into the output stream, if the ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING flag is set on the screen buffer handle using the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="63d69-113">Notez que l’indicateur DISABLE\_NEWLINE\_AUTO\_RETURN peut également être utile pour émuler le comportement de défilement et de positionnement de curseur d’autres émulateurs de terminal par rapport aux caractères écrits dans la dernière colonne de n’importe quelle ligne.</span><span class="sxs-lookup"><span data-stu-id="63d69-113">Note that the DISABLE\_NEWLINE\_AUTO\_RETURN flag may also be useful in emulating the cursor positioning and scrolling behavior of other terminal emulators in relation to characters written to the final column in any row.</span></span>

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span data-ttu-id="63d69-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Positionnement de curseur simple</span><span class="sxs-lookup"><span data-stu-id="63d69-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Simple Cursor Positioning</span></span>


<span data-ttu-id="63d69-115">Dans toutes les descriptions suivantes, le caractère d’échappement (ESC) est toujours la valeur hexadécimale 0x1B.</span><span class="sxs-lookup"><span data-stu-id="63d69-115">In all of the following descriptions, ESC is always the hexadecimal value 0x1B.</span></span> <span data-ttu-id="63d69-116">Aucun espace ne doit être inclus dans les séquences de terminal.</span><span class="sxs-lookup"><span data-stu-id="63d69-116">No spaces are to be included in terminal sequences.</span></span> <span data-ttu-id="63d69-117">Pour obtenir un exemple d’utilisation pratique de ces séquences, consultez l’[exemple ](#example) à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="63d69-117">For an example of how these sequences are used in practice, please see the [example](#example) at the end of this topic.</span></span>

<span data-ttu-id="63d69-118">Le tableau suivant décrit des séquences d’échappement simples avec une commande d’action unique directement après le caractère d’échappement (ESC).</span><span class="sxs-lookup"><span data-stu-id="63d69-118">The following table describes simple escape sequences with a single action command directly after the ESC character.</span></span> <span data-ttu-id="63d69-119">Ces séquences n’ont pas de paramètres et prennent effet immédiatement.</span><span class="sxs-lookup"><span data-stu-id="63d69-119">These sequences have no parameters and take effect immediately.</span></span>

<span data-ttu-id="63d69-120">Toutes les commandes de ce tableau équivalent généralement à appeler l’API de console [**SetConsoleCursorPosition**](setconsolecursorposition.md) pour placer le curseur.</span><span class="sxs-lookup"><span data-stu-id="63d69-120">All commands in this table are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API to place the cursor.</span></span>

<span data-ttu-id="63d69-121">Le déplacement du curseur est limité par la fenêtre d’affichage actuelle dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="63d69-121">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="63d69-122">Le défilement (si disponible) ne se produit pas.</span><span class="sxs-lookup"><span data-stu-id="63d69-122">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="63d69-123">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-123">Sequence</span></span> | <span data-ttu-id="63d69-124">Forme abrégée</span><span class="sxs-lookup"><span data-stu-id="63d69-124">Shorthand</span></span> | <span data-ttu-id="63d69-125">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-125">Behavior</span></span> |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="63d69-126">ESC A</span><span class="sxs-lookup"><span data-stu-id="63d69-126">ESC A</span></span> | <span data-ttu-id="63d69-127">CUU</span><span class="sxs-lookup"><span data-stu-id="63d69-127">CUU</span></span> | <span data-ttu-id="63d69-128">Déplacement du curseur vers le haut de 1 ligne</span><span class="sxs-lookup"><span data-stu-id="63d69-128">Cursor Up by 1</span></span> |
| <span data-ttu-id="63d69-129">ESC B</span><span class="sxs-lookup"><span data-stu-id="63d69-129">ESC B</span></span> | <span data-ttu-id="63d69-130">CUD</span><span class="sxs-lookup"><span data-stu-id="63d69-130">CUD</span></span> | <span data-ttu-id="63d69-131">Déplacement du curseur vers le bas de 1 ligne</span><span class="sxs-lookup"><span data-stu-id="63d69-131">Cursor Down by 1</span></span> |
| <span data-ttu-id="63d69-132">ESC C</span><span class="sxs-lookup"><span data-stu-id="63d69-132">ESC C</span></span> | <span data-ttu-id="63d69-133">CUF</span><span class="sxs-lookup"><span data-stu-id="63d69-133">CUF</span></span> | <span data-ttu-id="63d69-134">Déplacement du curseur vers l’avant (à droite) de 1 colonne</span><span class="sxs-lookup"><span data-stu-id="63d69-134">Cursor Forward (Right) by 1</span></span> |
| <span data-ttu-id="63d69-135">ESC D</span><span class="sxs-lookup"><span data-stu-id="63d69-135">ESC D</span></span> | <span data-ttu-id="63d69-136">CUB</span><span class="sxs-lookup"><span data-stu-id="63d69-136">CUB</span></span> | <span data-ttu-id="63d69-137">Déplacement du curseur vers l’arrière (à gauche) de 1 colonne</span><span class="sxs-lookup"><span data-stu-id="63d69-137">Cursor Backward (Left) by 1</span></span> |
| <span data-ttu-id="63d69-138">ESC M</span><span class="sxs-lookup"><span data-stu-id="63d69-138">ESC M</span></span> | <span data-ttu-id="63d69-139">Instance réservée</span><span class="sxs-lookup"><span data-stu-id="63d69-139">RI</span></span> | <span data-ttu-id="63d69-140">Index inverse : effectue l’opération inverse de \\n, déplace le curseur d’une ligne vers le haut, conserve la position horizontale, fait défiler le tampon si nécessaire\*</span><span class="sxs-lookup"><span data-stu-id="63d69-140">Reverse Index – Performs the reverse operation of \\n, moves cursor up one line, maintains horizontal position, scrolls buffer if necessary\*</span></span> |
| <span data-ttu-id="63d69-141">ESC 7</span><span class="sxs-lookup"><span data-stu-id="63d69-141">ESC 7</span></span> | <span data-ttu-id="63d69-142">DECSC</span><span class="sxs-lookup"><span data-stu-id="63d69-142">DECSC</span></span> | <span data-ttu-id="63d69-143">Enregistrer la position du curseur en mémoire\*\*</span><span class="sxs-lookup"><span data-stu-id="63d69-143">Save Cursor Position in Memory\*\*</span></span> |
| <span data-ttu-id="63d69-144">ESC 8</span><span class="sxs-lookup"><span data-stu-id="63d69-144">ESC 8</span></span> | <span data-ttu-id="63d69-145">DECSR</span><span class="sxs-lookup"><span data-stu-id="63d69-145">DECSR</span></span> | <span data-ttu-id="63d69-146">Restaurer la position du curseur à partir de la mémoire\*\*</span><span class="sxs-lookup"><span data-stu-id="63d69-146">Restore Cursor Position from Memory\*\*</span></span> |



> [!NOTE]
><span data-ttu-id="63d69-147">\* Si des marges de défilement sont définies, l’index inverse (RI) à l’intérieur des marges fait défiler uniquement le contenu des marges et laisse la fenêtre d’affichage inchangée.</span><span class="sxs-lookup"><span data-stu-id="63d69-147">\* If there are scroll margins set, RI inside the margins will scroll only the contents of the margins, and leave the viewport unchanged.</span></span> <span data-ttu-id="63d69-148">(Voir Marges de défilement)</span><span class="sxs-lookup"><span data-stu-id="63d69-148">(See Scrolling Margins)</span></span>
>
><span data-ttu-id="63d69-149">\*\*Aucune valeur n’est enregistrée en mémoire tant que la commande d’enregistrement n’a pas été utilisée une première fois.</span><span class="sxs-lookup"><span data-stu-id="63d69-149">\*\*There will be no value saved in memory until the first use of the save command.</span></span> <span data-ttu-id="63d69-150">La seule façon d’accéder à la valeur enregistrée consiste à utiliser la commande de restauration.</span><span class="sxs-lookup"><span data-stu-id="63d69-150">The only way to access the saved value is with the restore command.</span></span>

## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span data-ttu-id="63d69-151"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Positionnement du curseur</span><span class="sxs-lookup"><span data-stu-id="63d69-151"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursor Positioning</span></span>


<span data-ttu-id="63d69-152">Les tableaux suivants englobent les séquences de types CSI (Control Sequence Introducer, Introducteur de séquence de commandes).</span><span class="sxs-lookup"><span data-stu-id="63d69-152">The following tables encompass Control Sequence Introducer (CSI) type sequences.</span></span> <span data-ttu-id="63d69-153">Toutes les séquences CSI commencent par ESC (0x1B) suivi de \[ (crochet gauche, 0x5B) et peuvent contenir des paramètres de longueur variable afin de spécifier plus d’informations pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="63d69-153">All CSI sequences start with ESC (0x1B) followed by \[ (left bracket, 0x5B) and may contain parameters of variable length to specify more information for each operation.</span></span> <span data-ttu-id="63d69-154">Cela est représenté par la forme abrégée &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="63d69-154">This will be represented by the shorthand &lt;n&gt;.</span></span> <span data-ttu-id="63d69-155">Chaque tableau ci-dessous est regroupé par fonctionnalité et est suivi de notes expliquant le fonctionnement du groupe.</span><span class="sxs-lookup"><span data-stu-id="63d69-155">Each table below is grouped by functionality with notes below each table explaining how the group works.</span></span>

<span data-ttu-id="63d69-156">Pour tous les paramètres, les règles suivantes s’appliquent, sauf indication contraire :</span><span class="sxs-lookup"><span data-stu-id="63d69-156">For all parameters, the following rules apply unless otherwise noted:</span></span>

- <span data-ttu-id="63d69-157">&lt;n&gt; représente la distance de déplacement et est un paramètre facultatif</span><span class="sxs-lookup"><span data-stu-id="63d69-157">&lt;n&gt; represents the distance to move and is an optional parameter</span></span>
- <span data-ttu-id="63d69-158">Si &lt;n&gt; est omis ou est égal à 0, il est traité comme un 1</span><span class="sxs-lookup"><span data-stu-id="63d69-158">If &lt;n&gt; is omitted or equals 0, it will be treated as a 1</span></span>
- <span data-ttu-id="63d69-159">&lt;n&gt; ne peut pas être supérieur à 32 767 (valeur courte maximale)</span><span class="sxs-lookup"><span data-stu-id="63d69-159">&lt;n&gt; cannot be larger than 32,767 (maximum short value)</span></span>
- <span data-ttu-id="63d69-160">&lt;n&gt; ne peut pas être négatif</span><span class="sxs-lookup"><span data-stu-id="63d69-160">&lt;n&gt; cannot be negative</span></span>

<span data-ttu-id="63d69-161">Toutes les commandes de cette section équivalent généralement à appeler l’API de console [**SetConsoleCursorPosition**](setconsolecursorposition.md).</span><span class="sxs-lookup"><span data-stu-id="63d69-161">All commands in this section are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API.</span></span>

<span data-ttu-id="63d69-162">Le déplacement du curseur est limité par la fenêtre d’affichage actuelle dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="63d69-162">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="63d69-163">Le défilement (si disponible) ne se produit pas.</span><span class="sxs-lookup"><span data-stu-id="63d69-163">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="63d69-164">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-164">Sequence</span></span> | <span data-ttu-id="63d69-165">Code</span><span class="sxs-lookup"><span data-stu-id="63d69-165">Code</span></span> | <span data-ttu-id="63d69-166">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-166">Description</span></span> | <span data-ttu-id="63d69-167">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-167">Behavior</span></span> |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="63d69-168">ESC \[ &lt;n&gt; A</span><span class="sxs-lookup"><span data-stu-id="63d69-168">ESC \[ &lt;n&gt; A</span></span> | <span data-ttu-id="63d69-169">CUU</span><span class="sxs-lookup"><span data-stu-id="63d69-169">CUU</span></span> | <span data-ttu-id="63d69-170">Déplacement du curseur vers le haut</span><span class="sxs-lookup"><span data-stu-id="63d69-170">Cursor Up</span></span> | <span data-ttu-id="63d69-171">Déplacement du curseur vers le haut de &lt;n&gt; ligne(s)</span><span class="sxs-lookup"><span data-stu-id="63d69-171">Cursor up by &lt;n&gt;</span></span> |
| <span data-ttu-id="63d69-172">ESC \[ &lt;n&gt; B</span><span class="sxs-lookup"><span data-stu-id="63d69-172">ESC \[ &lt;n&gt; B</span></span> | <span data-ttu-id="63d69-173">CUD</span><span class="sxs-lookup"><span data-stu-id="63d69-173">CUD</span></span> | <span data-ttu-id="63d69-174">Déplacement du curseur vers le bas</span><span class="sxs-lookup"><span data-stu-id="63d69-174">Cursor Down</span></span> | <span data-ttu-id="63d69-175">Déplacement du curseur vers le bas de &lt;n&gt; ligne(s)</span><span class="sxs-lookup"><span data-stu-id="63d69-175">Cursor down by &lt;n&gt;</span></span> |
| <span data-ttu-id="63d69-176">ESC \[ &lt;n&gt; C</span><span class="sxs-lookup"><span data-stu-id="63d69-176">ESC \[ &lt;n&gt; C</span></span> | <span data-ttu-id="63d69-177">CUF</span><span class="sxs-lookup"><span data-stu-id="63d69-177">CUF</span></span> | <span data-ttu-id="63d69-178">Déplacement du curseur vers l’avant</span><span class="sxs-lookup"><span data-stu-id="63d69-178">Cursor Forward</span></span> | <span data-ttu-id="63d69-179">Déplacement du curseur vers l’avant (à droite) de &lt;n&gt; colonne(s)</span><span class="sxs-lookup"><span data-stu-id="63d69-179">Cursor forward (Right) by &lt;n&gt;</span></span> |
| <span data-ttu-id="63d69-180">ESC \[ &lt;n&gt; D</span><span class="sxs-lookup"><span data-stu-id="63d69-180">ESC \[ &lt;n&gt; D</span></span> | <span data-ttu-id="63d69-181">CUB</span><span class="sxs-lookup"><span data-stu-id="63d69-181">CUB</span></span> | <span data-ttu-id="63d69-182">Déplacement du curseur vers l’arrière</span><span class="sxs-lookup"><span data-stu-id="63d69-182">Cursor Backward</span></span> | <span data-ttu-id="63d69-183">Déplacement du curseur vers l’arrière (à gauche) de &lt;n&gt; colonne(s)</span><span class="sxs-lookup"><span data-stu-id="63d69-183">Cursor backward (Left) by &lt;n&gt;</span></span> |
| <span data-ttu-id="63d69-184">ESC \[ &lt;n&gt; E</span><span class="sxs-lookup"><span data-stu-id="63d69-184">ESC \[ &lt;n&gt; E</span></span> | <span data-ttu-id="63d69-185">CNL</span><span class="sxs-lookup"><span data-stu-id="63d69-185">CNL</span></span> | <span data-ttu-id="63d69-186">Déplacement du curseur vers la ligne suivante</span><span class="sxs-lookup"><span data-stu-id="63d69-186">Cursor Next Line</span></span> | <span data-ttu-id="63d69-187">Déplacement du curseur vers le bas de &lt;n&gt; lignes à partir de la position actuelle</span><span class="sxs-lookup"><span data-stu-id="63d69-187">Cursor down &lt;n&gt; lines from current position</span></span> |
| <span data-ttu-id="63d69-188">ESC \[ &lt;n&gt; F</span><span class="sxs-lookup"><span data-stu-id="63d69-188">ESC \[ &lt;n&gt; F</span></span> | <span data-ttu-id="63d69-189">CPL</span><span class="sxs-lookup"><span data-stu-id="63d69-189">CPL</span></span> | <span data-ttu-id="63d69-190">Déplacement du curseur vers la ligne précédente</span><span class="sxs-lookup"><span data-stu-id="63d69-190">Cursor Previous Line</span></span> | <span data-ttu-id="63d69-191">Déplacement du curseur vers le haut de &lt;n&gt; lignes à partir de la position actuelle</span><span class="sxs-lookup"><span data-stu-id="63d69-191">Cursor up &lt;n&gt; lines from current position</span></span> |
| <span data-ttu-id="63d69-192">ESC \[ &lt;n&gt; G</span><span class="sxs-lookup"><span data-stu-id="63d69-192">ESC \[ &lt;n&gt; G</span></span> | <span data-ttu-id="63d69-193">CHA</span><span class="sxs-lookup"><span data-stu-id="63d69-193">CHA</span></span> | <span data-ttu-id="63d69-194">Déplacement horizontal absolu du curseur</span><span class="sxs-lookup"><span data-stu-id="63d69-194">Cursor Horizontal Absolute</span></span> | <span data-ttu-id="63d69-195">Le curseur se déplace horizontalement jusqu’à la &lt;n&gt;ième position dans la ligne actuelle</span><span class="sxs-lookup"><span data-stu-id="63d69-195">Cursor moves to &lt;n&gt;th position horizontally in the current line</span></span> |
| <span data-ttu-id="63d69-196">ESC \[ &lt;n&gt; d</span><span class="sxs-lookup"><span data-stu-id="63d69-196">ESC \[ &lt;n&gt; d</span></span> | <span data-ttu-id="63d69-197">VPA</span><span class="sxs-lookup"><span data-stu-id="63d69-197">VPA</span></span> | <span data-ttu-id="63d69-198">Déplacement vertical absolu jusqu’à une ligne</span><span class="sxs-lookup"><span data-stu-id="63d69-198">Vertical Line Position Absolute</span></span> | <span data-ttu-id="63d69-199">Le curseur se déplace verticalement jusqu’à la &lt;n&gt;ième position dans la colonne actuelle</span><span class="sxs-lookup"><span data-stu-id="63d69-199">Cursor moves to the &lt;n&gt;th position vertically in the current column</span></span> |
| <span data-ttu-id="63d69-200">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span><span class="sxs-lookup"><span data-stu-id="63d69-200">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span></span> | <span data-ttu-id="63d69-201">CUP</span><span class="sxs-lookup"><span data-stu-id="63d69-201">CUP</span></span> | <span data-ttu-id="63d69-202">Position du curseur</span><span class="sxs-lookup"><span data-stu-id="63d69-202">Cursor Position</span></span> | <span data-ttu-id="63d69-203">\*Le curseur se déplace jusqu’à la position &lt;x&gt;; &lt;y&gt; dans la fenêtre d’affichage, où &lt;x&gt; correspond à la colonne de la ligne &lt;y&gt;</span><span class="sxs-lookup"><span data-stu-id="63d69-203">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="63d69-204">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span><span class="sxs-lookup"><span data-stu-id="63d69-204">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span></span> | <span data-ttu-id="63d69-205">HVP</span><span class="sxs-lookup"><span data-stu-id="63d69-205">HVP</span></span> | <span data-ttu-id="63d69-206">Position verticale horizontale</span><span class="sxs-lookup"><span data-stu-id="63d69-206">Horizontal Vertical Position</span></span> | <span data-ttu-id="63d69-207">\*Le curseur se déplace jusqu’à la position &lt;x&gt;; &lt;y&gt; dans la fenêtre d’affichage, où &lt;x&gt; correspond à la colonne de la ligne &lt;y&gt;</span><span class="sxs-lookup"><span data-stu-id="63d69-207">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="63d69-208">ESC \[ s</span><span class="sxs-lookup"><span data-stu-id="63d69-208">ESC \[ s</span></span> | <span data-ttu-id="63d69-209">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="63d69-209">ANSISYSSC</span></span> | <span data-ttu-id="63d69-210">Enregistrer le curseur – émulation Ansi.sys</span><span class="sxs-lookup"><span data-stu-id="63d69-210">Save Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="63d69-211">\*\*Sans paramètre, effectue une opération d’enregistrement du curseur comme DECSC</span><span class="sxs-lookup"><span data-stu-id="63d69-211">\*\*With no parameters, performs a save cursor operation like DECSC</span></span> |
| <span data-ttu-id="63d69-212">ESC \[ u</span><span class="sxs-lookup"><span data-stu-id="63d69-212">ESC \[ u</span></span> | <span data-ttu-id="63d69-213">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="63d69-213">ANSISYSSC</span></span> | <span data-ttu-id="63d69-214">Restaurer le curseur – émulation Ansi.sys</span><span class="sxs-lookup"><span data-stu-id="63d69-214">Restore Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="63d69-215">\*\*Sans paramètre, effectue une opération de restauration du curseur comme DECRC</span><span class="sxs-lookup"><span data-stu-id="63d69-215">\*\*With no parameters, performs a restore cursor operation like DECRC</span></span> |



> [!NOTE]
><span data-ttu-id="63d69-216">Les paramètres \*&lt;x&gt; et &lt;y&gt; présentent les mêmes limitations que &lt;n&gt; ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="63d69-216">\*&lt;x&gt; and &lt;y&gt; parameters have the same limitations as &lt;n&gt; above.</span></span> <span data-ttu-id="63d69-217">Si &lt;x&gt; et &lt;y&gt; sont omis, ils sont définis sur 1;1.</span><span class="sxs-lookup"><span data-stu-id="63d69-217">If &lt;x&gt; and &lt;y&gt; are omitted, they will be set to 1;1.</span></span>
>
><span data-ttu-id="63d69-218">\*\*La documentation historique sur ANSI.sys est disponible à l’adresse <https://msdn.microsoft.com/library/cc722862.aspx> et est implémentée pour des raisons pratiques et de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="63d69-218">\*\*ANSI.sys historical documentation can be found at <https://msdn.microsoft.com/library/cc722862.aspx> and is implemented for convenience/compatibility.</span></span>



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span data-ttu-id="63d69-219"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Visibilité du curseur</span><span class="sxs-lookup"><span data-stu-id="63d69-219"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursor Visibility</span></span>


<span data-ttu-id="63d69-220">Les commandes suivantes contrôlent la visibilité du curseur et son état de clignotement.</span><span class="sxs-lookup"><span data-stu-id="63d69-220">The following commands control the visibility of the cursor and its blinking state.</span></span> <span data-ttu-id="63d69-221">Les séquences DECTCEM équivalent généralement à appeler l’API de console [**SetConsoleCursorInfo**](setconsolecursorinfo.md) pour changer l’état de la visibilité du curseur.</span><span class="sxs-lookup"><span data-stu-id="63d69-221">The DECTCEM sequences are generally equivalent to calling [**SetConsoleCursorInfo**](setconsolecursorinfo.md) console API to toggle cursor visibility.</span></span>


| <span data-ttu-id="63d69-222">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-222">Sequence</span></span> | <span data-ttu-id="63d69-223">Code</span><span class="sxs-lookup"><span data-stu-id="63d69-223">Code</span></span> | <span data-ttu-id="63d69-224">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-224">Description</span></span> | <span data-ttu-id="63d69-225">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-225">Behavior</span></span> |
|---------------|---------|------------------------------|---------------------------|
| <span data-ttu-id="63d69-226">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="63d69-226">ESC \[ ?</span></span> <span data-ttu-id="63d69-227">12 h</span><span class="sxs-lookup"><span data-stu-id="63d69-227">12 h</span></span> | <span data-ttu-id="63d69-228">ATT160</span><span class="sxs-lookup"><span data-stu-id="63d69-228">ATT160</span></span> | <span data-ttu-id="63d69-229">Curseur de texte - Activer le clignotement</span><span class="sxs-lookup"><span data-stu-id="63d69-229">Text Cursor Enable Blinking</span></span> | <span data-ttu-id="63d69-230">Démarrer le clignotement du curseur</span><span class="sxs-lookup"><span data-stu-id="63d69-230">Start the cursor blinking</span></span> |
| <span data-ttu-id="63d69-231">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="63d69-231">ESC \[ ?</span></span> <span data-ttu-id="63d69-232">12 l</span><span class="sxs-lookup"><span data-stu-id="63d69-232">12 l</span></span> | <span data-ttu-id="63d69-233">ATT160</span><span class="sxs-lookup"><span data-stu-id="63d69-233">ATT160</span></span> | <span data-ttu-id="63d69-234">Curseur de texte - Désactiver le clignotement</span><span class="sxs-lookup"><span data-stu-id="63d69-234">Text Cursor Disable Blinking</span></span> | <span data-ttu-id="63d69-235">Arrêter le clignotement du curseur</span><span class="sxs-lookup"><span data-stu-id="63d69-235">Stop blinking the cursor</span></span> |
| <span data-ttu-id="63d69-236">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="63d69-236">ESC \[ ?</span></span> <span data-ttu-id="63d69-237">25 h</span><span class="sxs-lookup"><span data-stu-id="63d69-237">25 h</span></span> | <span data-ttu-id="63d69-238">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="63d69-238">DECTCEM</span></span> | <span data-ttu-id="63d69-239">Curseur de texte - Activer le mode affichage</span><span class="sxs-lookup"><span data-stu-id="63d69-239">Text Cursor Enable Mode Show</span></span> | <span data-ttu-id="63d69-240">Afficher le curseur</span><span class="sxs-lookup"><span data-stu-id="63d69-240">Show the cursor</span></span> |
| <span data-ttu-id="63d69-241">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="63d69-241">ESC \[ ?</span></span> <span data-ttu-id="63d69-242">25 l</span><span class="sxs-lookup"><span data-stu-id="63d69-242">25 l</span></span> | <span data-ttu-id="63d69-243">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="63d69-243">DECTCEM</span></span> | <span data-ttu-id="63d69-244">Curseur de texte - Activer le mode masquage</span><span class="sxs-lookup"><span data-stu-id="63d69-244">Text Cursor Enable Mode Hide</span></span> | <span data-ttu-id="63d69-245">Masquer le curseur</span><span class="sxs-lookup"><span data-stu-id="63d69-245">Hide the cursor</span></span> |

> [!TIP]
> <span data-ttu-id="63d69-246">Les séquences d’activation se terminent par un caractère H minuscule (`h`), tandis que les séquences de désactivation se terminent par un caractère L minuscule (`l`).</span><span class="sxs-lookup"><span data-stu-id="63d69-246">The enable sequences end in a lowercase H character (`h`) and the disable sequences end in a lowercase L character (`l`).</span></span>

## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span data-ttu-id="63d69-247"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Positionnement de la fenêtre d’affichage</span><span class="sxs-lookup"><span data-stu-id="63d69-247"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Viewport Positioning</span></span>


<span data-ttu-id="63d69-248">Toutes les commandes de cette section équivalent généralement à appeler l’API de console [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) pour déplacer le contenu de la mémoire tampon de la console.</span><span class="sxs-lookup"><span data-stu-id="63d69-248">All commands in this section are generally equivalent to calling [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console API to move the contents of the console buffer.</span></span>

<span data-ttu-id="63d69-249">**Attention** Les noms des commandes sont trompeurs.</span><span class="sxs-lookup"><span data-stu-id="63d69-249">**Caution** The command names are misleading.</span></span> <span data-ttu-id="63d69-250">Le défilement fait référence à la direction dans laquelle le texte se déplace au cours de l’opération, et non à celle que semblerait emprunter la fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="63d69-250">Scroll refers to which direction the text moves during the operation, not which way the viewport would seem to move.</span></span>




| <span data-ttu-id="63d69-251">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-251">Sequence</span></span> | <span data-ttu-id="63d69-252">Code</span><span class="sxs-lookup"><span data-stu-id="63d69-252">Code</span></span> | <span data-ttu-id="63d69-253">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-253">Description</span></span> | <span data-ttu-id="63d69-254">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-254">Behavior</span></span> |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="63d69-255">ESC \[ &lt;n&gt; S</span><span class="sxs-lookup"><span data-stu-id="63d69-255">ESC \[ &lt;n&gt; S</span></span> | <span data-ttu-id="63d69-256">Unités de diffusion en continu</span><span class="sxs-lookup"><span data-stu-id="63d69-256">SU</span></span> | <span data-ttu-id="63d69-257">Faire défiler vers le haut</span><span class="sxs-lookup"><span data-stu-id="63d69-257">Scroll Up</span></span> | <span data-ttu-id="63d69-258">Faire défiler le texte vers le haut de &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="63d69-258">Scroll text up by &lt;n&gt;.</span></span> <span data-ttu-id="63d69-259">Opération également appelée « panoramique vers le bas » ; les nouvelles lignes se remplissent à partir du bas de l’écran</span><span class="sxs-lookup"><span data-stu-id="63d69-259">Also known as pan down, new lines fill in from the bottom of the screen</span></span> |
| <span data-ttu-id="63d69-260">ESC \[ &lt;n&gt; T</span><span class="sxs-lookup"><span data-stu-id="63d69-260">ESC \[ &lt;n&gt; T</span></span> | <span data-ttu-id="63d69-261">SD</span><span class="sxs-lookup"><span data-stu-id="63d69-261">SD</span></span> | <span data-ttu-id="63d69-262">Faire défiler vers le bas</span><span class="sxs-lookup"><span data-stu-id="63d69-262">Scroll Down</span></span> | <span data-ttu-id="63d69-263">Faire défiler vers le bas de &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="63d69-263">Scroll down by &lt;n&gt;.</span></span> <span data-ttu-id="63d69-264">Opération également appelée « panoramique vers le haut » ; les nouvelles lignes se remplissent à partir du haut de l’écran</span><span class="sxs-lookup"><span data-stu-id="63d69-264">Also known as pan up, new lines fill in from the top of the screen</span></span> |



<span data-ttu-id="63d69-265">Le texte est déplacé à partir de la ligne sur laquelle se trouve le curseur.</span><span class="sxs-lookup"><span data-stu-id="63d69-265">The text is moved starting with the line the cursor is on.</span></span> <span data-ttu-id="63d69-266">Si le curseur se trouve sur la ligne du milieu de la fenêtre d’affichage, le défilement vers le haut déplace la moitié inférieure de la fenêtre d’affichage et insère des lignes vides en bas.</span><span class="sxs-lookup"><span data-stu-id="63d69-266">If the cursor is on the middle row of the viewport, then scroll up would move the bottom half of the viewport, and insert blank lines at the bottom.</span></span> <span data-ttu-id="63d69-267">Le défilement vers le bas déplace la moitié supérieure des lignes de la fenêtre d’affichage et insère de nouvelles lignes en haut.</span><span class="sxs-lookup"><span data-stu-id="63d69-267">Scroll down would move the top half of the viewport’s rows, and insert new lines at the top.</span></span>

<span data-ttu-id="63d69-268">En outre, il est important de noter que le défilement vers le haut et vers le bas est également affecté par les marges de défilement.</span><span class="sxs-lookup"><span data-stu-id="63d69-268">Also important to note is scroll up and down are also affected by the scrolling margins.</span></span> <span data-ttu-id="63d69-269">Le défilement vers le haut et vers le bas n’affecte pas les lignes situées en dehors des marges de défilement.</span><span class="sxs-lookup"><span data-stu-id="63d69-269">Scroll up and down won’t affect any lines outside the scrolling margins.</span></span>

<span data-ttu-id="63d69-270">La valeur par défaut de &lt;n&gt; est 1 et la valeur peut éventuellement être omise.</span><span class="sxs-lookup"><span data-stu-id="63d69-270">The default value for &lt;n&gt; is 1, and the value can be optionally omitted.</span></span>

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span data-ttu-id="63d69-271"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Modification du texte</span><span class="sxs-lookup"><span data-stu-id="63d69-271"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Text Modification</span></span>


<span data-ttu-id="63d69-272">Toutes les commandes de cette section équivalent généralement à appeler les API de console [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) et [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) pour modifier le contenu de la mémoire tampon de texte.</span><span class="sxs-lookup"><span data-stu-id="63d69-272">All commands in this section are generally equivalent to calling [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md), and [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console APIs to modify the text buffer contents.</span></span>


| <span data-ttu-id="63d69-273">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-273">Sequence</span></span> | <span data-ttu-id="63d69-274">Code</span><span class="sxs-lookup"><span data-stu-id="63d69-274">Code</span></span> | <span data-ttu-id="63d69-275">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-275">Description</span></span> | <span data-ttu-id="63d69-276">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-276">Behavior</span></span> |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="63d69-277">ESC \[ &lt;n&gt; @</span><span class="sxs-lookup"><span data-stu-id="63d69-277">ESC \[ &lt;n&gt; @</span></span> | <span data-ttu-id="63d69-278">ICH</span><span class="sxs-lookup"><span data-stu-id="63d69-278">ICH</span></span> | <span data-ttu-id="63d69-279">Insérer un caractère</span><span class="sxs-lookup"><span data-stu-id="63d69-279">Insert Character</span></span> | <span data-ttu-id="63d69-280">Insérer &lt;n&gt; espaces à la position actuelle du curseur, en décalant tout le texte existant vers la droite.</span><span class="sxs-lookup"><span data-stu-id="63d69-280">Insert &lt;n&gt; spaces at the current cursor position, shifting all existing text to the right.</span></span> <span data-ttu-id="63d69-281">Le texte qui quitte l’écran à droite est supprimé.</span><span class="sxs-lookup"><span data-stu-id="63d69-281">Text exiting the screen to the right is removed.</span></span> |
| <span data-ttu-id="63d69-282">ESC \[ &lt;n&gt; P</span><span class="sxs-lookup"><span data-stu-id="63d69-282">ESC \[ &lt;n&gt; P</span></span> | <span data-ttu-id="63d69-283">DCH</span><span class="sxs-lookup"><span data-stu-id="63d69-283">DCH</span></span> | <span data-ttu-id="63d69-284">Supprimer un caractère</span><span class="sxs-lookup"><span data-stu-id="63d69-284">Delete Character</span></span> | <span data-ttu-id="63d69-285">Supprimer &lt;n&gt; caractères à la position actuelle du curseur, entraînant par effet de décalage la création d’autant de caractères d’espace à partir du bord droit de l’écran.</span><span class="sxs-lookup"><span data-stu-id="63d69-285">Delete &lt;n&gt; characters at the current cursor position, shifting in space characters from the right edge of the screen.</span></span> |
| <span data-ttu-id="63d69-286">ESC \[ &lt;n&gt; X</span><span class="sxs-lookup"><span data-stu-id="63d69-286">ESC \[ &lt;n&gt; X</span></span> | <span data-ttu-id="63d69-287">ECH</span><span class="sxs-lookup"><span data-stu-id="63d69-287">ECH</span></span> | <span data-ttu-id="63d69-288">Effacer un caractère</span><span class="sxs-lookup"><span data-stu-id="63d69-288">Erase Character</span></span> | <span data-ttu-id="63d69-289">Effacer &lt;n&gt; caractères de la position actuelle du curseur en les remplaçant par un espace.</span><span class="sxs-lookup"><span data-stu-id="63d69-289">Erase &lt;n&gt; characters from the current cursor position by overwriting them with a space character.</span></span> |
| <span data-ttu-id="63d69-290">ESC \[ &lt;n&gt; L</span><span class="sxs-lookup"><span data-stu-id="63d69-290">ESC \[ &lt;n&gt; L</span></span> | <span data-ttu-id="63d69-291">IL</span><span class="sxs-lookup"><span data-stu-id="63d69-291">IL</span></span> | <span data-ttu-id="63d69-292">Insérer une ligne</span><span class="sxs-lookup"><span data-stu-id="63d69-292">Insert Line</span></span> | <span data-ttu-id="63d69-293">Insérer &lt;n&gt; lignes dans la mémoire tampon à la position du curseur.</span><span class="sxs-lookup"><span data-stu-id="63d69-293">Inserts &lt;n&gt; lines into the buffer at the cursor position.</span></span> <span data-ttu-id="63d69-294">La ligne sur laquelle se trouve le curseur et les lignes au-dessous de celle-ci sont décalées vers le bas.</span><span class="sxs-lookup"><span data-stu-id="63d69-294">The line the cursor is on, and lines below it, will be shifted downwards.</span></span> |
| <span data-ttu-id="63d69-295">ESC \[ &lt;n&gt; M</span><span class="sxs-lookup"><span data-stu-id="63d69-295">ESC \[ &lt;n&gt; M</span></span> | <span data-ttu-id="63d69-296">DL</span><span class="sxs-lookup"><span data-stu-id="63d69-296">DL</span></span> | <span data-ttu-id="63d69-297">Supprimer la ligne</span><span class="sxs-lookup"><span data-stu-id="63d69-297">Delete Line</span></span> | <span data-ttu-id="63d69-298">Supprime &lt;n&gt; lignes de la mémoire tampon, en commençant par la ligne sur laquelle se trouve le curseur.</span><span class="sxs-lookup"><span data-stu-id="63d69-298">Deletes &lt;n&gt; lines from the buffer, starting with the row the cursor is on.</span></span> |



> [!NOTE]
><span data-ttu-id="63d69-299">Pour IL et DL, seules les lignes dans les marges de défilement (voir Marges de défilement) sont affectées.</span><span class="sxs-lookup"><span data-stu-id="63d69-299">For IL and DL, only the lines in the scrolling margins (see Scrolling Margins) are affected.</span></span> <span data-ttu-id="63d69-300">Si aucune marge n’est définie, les bordures de marge par défaut sont la fenêtre d’affichage actuelle.</span><span class="sxs-lookup"><span data-stu-id="63d69-300">If no margins are set, the default margin borders are the current viewport.</span></span> <span data-ttu-id="63d69-301">Si des lignes sont décalées en dessous des marges, elles sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="63d69-301">If lines would be shifted below the margins, they are discarded.</span></span> <span data-ttu-id="63d69-302">Quand des lignes sont supprimées, des lignes vides sont insérées en bas des marges et les lignes en dehors de la fenêtre d’affichage ne sont jamais affectées.</span><span class="sxs-lookup"><span data-stu-id="63d69-302">When lines are deleted, blank lines are inserted at the bottom of the margins, lines from outside the viewport are never affected.</span></span>

<span data-ttu-id="63d69-303">Pour chacune des séquences, la valeur par défaut de &lt;n&gt; s’il est omis est 0.</span><span class="sxs-lookup"><span data-stu-id="63d69-303">For each of the sequences, the default value for &lt;n&gt; if it is omitted is 0.</span></span>



<span data-ttu-id="63d69-304">Pour les commandes suivantes, le paramètre &lt;n&gt; a 3 valeurs valides :</span><span class="sxs-lookup"><span data-stu-id="63d69-304">For the following commands, the parameter &lt;n&gt; has 3 valid values:</span></span>

- <span data-ttu-id="63d69-305">0 efface de la position actuelle du curseur (comprise) jusqu’à la fin de la ligne/de l’affichage</span><span class="sxs-lookup"><span data-stu-id="63d69-305">0 erases from the current cursor position (inclusive) to the end of the line/display</span></span>
- <span data-ttu-id="63d69-306">1 efface du début de la ligne/de l’affichage jusqu’à la position actuelle du curseur comprise</span><span class="sxs-lookup"><span data-stu-id="63d69-306">1 erases from the beginning of the line/display up to and including the current cursor position</span></span>
- <span data-ttu-id="63d69-307">2 efface l’intégralité de la ligne/de l’affichage</span><span class="sxs-lookup"><span data-stu-id="63d69-307">2 erases the entire line/display</span></span>


| <span data-ttu-id="63d69-308">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-308">Sequence</span></span> | <span data-ttu-id="63d69-309">Code</span><span class="sxs-lookup"><span data-stu-id="63d69-309">Code</span></span> | <span data-ttu-id="63d69-310">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-310">Description</span></span> | <span data-ttu-id="63d69-311">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-311">Behavior</span></span> |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="63d69-312">ESC \[ &lt;n&gt; J</span><span class="sxs-lookup"><span data-stu-id="63d69-312">ESC \[ &lt;n&gt; J</span></span> | <span data-ttu-id="63d69-313">ED</span><span class="sxs-lookup"><span data-stu-id="63d69-313">ED</span></span> | <span data-ttu-id="63d69-314">Effacer dans l’affichage</span><span class="sxs-lookup"><span data-stu-id="63d69-314">Erase in Display</span></span> | <span data-ttu-id="63d69-315">En fonction de la valeur de &lt;n&gt;, remplacer par des espaces tout le texte de la fenêtre d’affichage ou de l’écran actuel</span><span class="sxs-lookup"><span data-stu-id="63d69-315">Replace all text in the current viewport/screen specified by &lt;n&gt; with space characters</span></span> |
| <span data-ttu-id="63d69-316">ESC \[ &lt;n&gt; K</span><span class="sxs-lookup"><span data-stu-id="63d69-316">ESC \[ &lt;n&gt; K</span></span> | <span data-ttu-id="63d69-317">EL</span><span class="sxs-lookup"><span data-stu-id="63d69-317">EL</span></span> | <span data-ttu-id="63d69-318">Effacer dans la ligne</span><span class="sxs-lookup"><span data-stu-id="63d69-318">Erase in Line</span></span> | <span data-ttu-id="63d69-319">En fonction de la valeur de &lt;n&gt;, remplacer par des espaces tout le texte de la ligne contenant le curseur</span><span class="sxs-lookup"><span data-stu-id="63d69-319">Replace all text on the line with the cursor specified by &lt;n&gt; with space characters</span></span> |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span data-ttu-id="63d69-320"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Mise en forme du texte</span><span class="sxs-lookup"><span data-stu-id="63d69-320"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Text Formatting</span></span>


<span data-ttu-id="63d69-321">Toutes les commandes de cette section équivalent généralement à appeler les API de console [**SetConsoleTextAttribute**](setconsoletextattribute.md) pour ajuster la mise en forme de toutes les écritures futures dans la mémoire tampon de texte de sortie de la console.</span><span class="sxs-lookup"><span data-stu-id="63d69-321">All commands in this section are generally equivalent to calling [**SetConsoleTextAttribute**](setconsoletextattribute.md) console APIs to adjust the formatting of all future writes to the console output text buffer.</span></span>

<span data-ttu-id="63d69-322">Cette commande est spéciale dans la mesure où la position &lt;n&gt; ci-dessous peut accepter entre 0 et 16 paramètres séparés par des points-virgules.</span><span class="sxs-lookup"><span data-stu-id="63d69-322">This command is special in that the &lt;n&gt; position below can accept between 0 and 16 parameters separated by semicolons.</span></span>

<span data-ttu-id="63d69-323">L’absence de paramètre équivaut à la présence d’un paramètre 0 unique.</span><span class="sxs-lookup"><span data-stu-id="63d69-323">When no parameters are specified, it is treated the same as a single 0 parameter.</span></span>


| <span data-ttu-id="63d69-324">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-324">Sequence</span></span> | <span data-ttu-id="63d69-325">Code</span><span class="sxs-lookup"><span data-stu-id="63d69-325">Code</span></span> | <span data-ttu-id="63d69-326">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-326">Description</span></span> | <span data-ttu-id="63d69-327">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-327">Behavior</span></span> |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| <span data-ttu-id="63d69-328">ESC \[ &lt;n&gt; m</span><span class="sxs-lookup"><span data-stu-id="63d69-328">ESC \[ &lt;n&gt; m</span></span> | <span data-ttu-id="63d69-329">SGR</span><span class="sxs-lookup"><span data-stu-id="63d69-329">SGR</span></span> | <span data-ttu-id="63d69-330">Définir un rendu graphique</span><span class="sxs-lookup"><span data-stu-id="63d69-330">Set Graphics Rendition</span></span> | <span data-ttu-id="63d69-331">Définir le format de l’écran et du texte tel que spécifié par &lt;n&gt;</span><span class="sxs-lookup"><span data-stu-id="63d69-331">Set the format of the screen and text as specified by &lt;n&gt;</span></span> |



<span data-ttu-id="63d69-332">Le tableau de valeurs suivant peut être utilisé dans &lt;n&gt; pour représenter différents modes de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="63d69-332">The following table of values can be used in &lt;n&gt; to represent different formatting modes.</span></span>

<span data-ttu-id="63d69-333">Les modes de mise en forme s’appliquent de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="63d69-333">Formatting modes are applied from left to right.</span></span> <span data-ttu-id="63d69-334">Si des options de mise en forme concurrentes sont appliquées, l’option la plus à droite est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="63d69-334">Applying competing formatting options will result in the right-most option taking precedence.</span></span>

<span data-ttu-id="63d69-335">Pour les options qui spécifient des couleurs, celles-ci sont utilisées comme défini dans la table de couleurs de la console, qui peut être modifiée à l’aide de l’API [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md).</span><span class="sxs-lookup"><span data-stu-id="63d69-335">For options that specify colors, the colors will be used as defined in the console color table which can be modified using the [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) API.</span></span> <span data-ttu-id="63d69-336">Si la table est modifiée afin que la position « bleu » dans la table affiche une nuance RVB rouge, tous les appels à **Premier plan en bleu** affichent cette couleur rouge jusqu’à ce qu’une nouvelle modification soit effectuée.</span><span class="sxs-lookup"><span data-stu-id="63d69-336">If the table is modified to make the “blue” position in the table display an RGB shade of red, then all calls to **Foreground Blue** will display that red color until otherwise changed.</span></span>


| <span data-ttu-id="63d69-337">Valeur</span><span class="sxs-lookup"><span data-stu-id="63d69-337">Value</span></span> | <span data-ttu-id="63d69-338">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-338">Description</span></span> | <span data-ttu-id="63d69-339">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-339">Behavior</span></span> |
|-------|---------------------------|--------------------------------------------------------------------|
| <span data-ttu-id="63d69-340">0</span><span class="sxs-lookup"><span data-stu-id="63d69-340">0</span></span> | <span data-ttu-id="63d69-341">Default</span><span class="sxs-lookup"><span data-stu-id="63d69-341">Default</span></span> | <span data-ttu-id="63d69-342">Retourne tous les attributs à l’état par défaut avant la modification</span><span class="sxs-lookup"><span data-stu-id="63d69-342">Returns all attributes to the default state prior to modification</span></span> |
| <span data-ttu-id="63d69-343">1</span><span class="sxs-lookup"><span data-stu-id="63d69-343">1</span></span> | <span data-ttu-id="63d69-344">Mise en gras/couleur brillante</span><span class="sxs-lookup"><span data-stu-id="63d69-344">Bold/Bright</span></span> | <span data-ttu-id="63d69-345">Applique l’indicateur de luminosité/intensité à la couleur de premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-345">Applies brightness/intensity flag to foreground color</span></span> |
| <span data-ttu-id="63d69-346">4</span><span class="sxs-lookup"><span data-stu-id="63d69-346">4</span></span> | <span data-ttu-id="63d69-347">Souligner</span><span class="sxs-lookup"><span data-stu-id="63d69-347">Underline</span></span> | <span data-ttu-id="63d69-348">Ajoute un soulignement</span><span class="sxs-lookup"><span data-stu-id="63d69-348">Adds underline</span></span> |
| <span data-ttu-id="63d69-349">24</span><span class="sxs-lookup"><span data-stu-id="63d69-349">24</span></span> | <span data-ttu-id="63d69-350">Pas de soulignement</span><span class="sxs-lookup"><span data-stu-id="63d69-350">No underline</span></span> | <span data-ttu-id="63d69-351">Supprime le soulignement</span><span class="sxs-lookup"><span data-stu-id="63d69-351">Removes underline</span></span> |
| <span data-ttu-id="63d69-352">7</span><span class="sxs-lookup"><span data-stu-id="63d69-352">7</span></span> | <span data-ttu-id="63d69-353">Négatif</span><span class="sxs-lookup"><span data-stu-id="63d69-353">Negative</span></span> | <span data-ttu-id="63d69-354">Permute les couleurs de premier plan et d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-354">Swaps foreground and background colors</span></span> |
| <span data-ttu-id="63d69-355">27</span><span class="sxs-lookup"><span data-stu-id="63d69-355">27</span></span> | <span data-ttu-id="63d69-356">Image positive (non négative)</span><span class="sxs-lookup"><span data-stu-id="63d69-356">Positive (No negative)</span></span> | <span data-ttu-id="63d69-357">Rétablit le premier plan et l’arrière-plan à l’état normal</span><span class="sxs-lookup"><span data-stu-id="63d69-357">Returns foreground/background to normal</span></span> |
| <span data-ttu-id="63d69-358">30</span><span class="sxs-lookup"><span data-stu-id="63d69-358">30</span></span> | <span data-ttu-id="63d69-359">Premier plan en noir</span><span class="sxs-lookup"><span data-stu-id="63d69-359">Foreground Black</span></span> | <span data-ttu-id="63d69-360">Applique la couleur noir brillant sans mise en gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-360">Applies non-bold/bright black to foreground</span></span> |
| <span data-ttu-id="63d69-361">31</span><span class="sxs-lookup"><span data-stu-id="63d69-361">31</span></span> | <span data-ttu-id="63d69-362">Premier plan en rouge</span><span class="sxs-lookup"><span data-stu-id="63d69-362">Foreground Red</span></span> | <span data-ttu-id="63d69-363">Applique la couleur rouge vif sans mise en gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-363">Applies non-bold/bright red to foreground</span></span> |
| <span data-ttu-id="63d69-364">32</span><span class="sxs-lookup"><span data-stu-id="63d69-364">32</span></span> | <span data-ttu-id="63d69-365">Premier plan en vert</span><span class="sxs-lookup"><span data-stu-id="63d69-365">Foreground Green</span></span> | <span data-ttu-id="63d69-366">Applique la couleur vert clair sans mise en gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-366">Applies non-bold/bright green to foreground</span></span> |
| <span data-ttu-id="63d69-367">33</span><span class="sxs-lookup"><span data-stu-id="63d69-367">33</span></span> | <span data-ttu-id="63d69-368">Premier plan en jaune</span><span class="sxs-lookup"><span data-stu-id="63d69-368">Foreground Yellow</span></span> | <span data-ttu-id="63d69-369">Applique la couleur jaune vif sans mise en gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-369">Applies non-bold/bright yellow to foreground</span></span> |
| <span data-ttu-id="63d69-370">34</span><span class="sxs-lookup"><span data-stu-id="63d69-370">34</span></span> | <span data-ttu-id="63d69-371">Premier plan en bleu</span><span class="sxs-lookup"><span data-stu-id="63d69-371">Foreground Blue</span></span> | <span data-ttu-id="63d69-372">Applique la couleur bleu brillant sans mise en gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-372">Applies non-bold/bright blue to foreground</span></span> |
| <span data-ttu-id="63d69-373">35</span><span class="sxs-lookup"><span data-stu-id="63d69-373">35</span></span> | <span data-ttu-id="63d69-374">Premier plan en magenta</span><span class="sxs-lookup"><span data-stu-id="63d69-374">Foreground Magenta</span></span> | <span data-ttu-id="63d69-375">Applique la couleur magenta brillant sans mise en gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-375">Applies non-bold/bright magenta to foreground</span></span> |
| <span data-ttu-id="63d69-376">36</span><span class="sxs-lookup"><span data-stu-id="63d69-376">36</span></span> | <span data-ttu-id="63d69-377">Premier plan en cyan</span><span class="sxs-lookup"><span data-stu-id="63d69-377">Foreground Cyan</span></span> | <span data-ttu-id="63d69-378">Applique la couleur cyan brillant sans mise en gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-378">Applies non-bold/bright cyan to foreground</span></span> |
| <span data-ttu-id="63d69-379">37</span><span class="sxs-lookup"><span data-stu-id="63d69-379">37</span></span> | <span data-ttu-id="63d69-380">Premier plan en blanc</span><span class="sxs-lookup"><span data-stu-id="63d69-380">Foreground White</span></span> | <span data-ttu-id="63d69-381">Applique la couleur blanc brillant sans mise en gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-381">Applies non-bold/bright white to foreground</span></span> |
| <span data-ttu-id="63d69-382">38</span><span class="sxs-lookup"><span data-stu-id="63d69-382">38</span></span> | <span data-ttu-id="63d69-383">Premier plan avec valeur de couleur étendue</span><span class="sxs-lookup"><span data-stu-id="63d69-383">Foreground Extended</span></span> | <span data-ttu-id="63d69-384">Applique la valeur de couleur étendue au premier plan (voir les détails ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="63d69-384">Applies extended color value to the foreground (see details below)</span></span> |
| <span data-ttu-id="63d69-385">39</span><span class="sxs-lookup"><span data-stu-id="63d69-385">39</span></span> | <span data-ttu-id="63d69-386">Définition par défaut du premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-386">Foreground Default</span></span> | <span data-ttu-id="63d69-387">Applique uniquement la partie du premier plan des valeurs par défaut (voir 0).</span><span class="sxs-lookup"><span data-stu-id="63d69-387">Applies only the foreground portion of the defaults (see 0)</span></span> |
| <span data-ttu-id="63d69-388">40</span><span class="sxs-lookup"><span data-stu-id="63d69-388">40</span></span> | <span data-ttu-id="63d69-389">Arrière-plan en noir</span><span class="sxs-lookup"><span data-stu-id="63d69-389">Background Black</span></span> | <span data-ttu-id="63d69-390">Applique la couleur noir brillant sans mise en gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-390">Applies non-bold/bright black to background</span></span> |
| <span data-ttu-id="63d69-391">41</span><span class="sxs-lookup"><span data-stu-id="63d69-391">41</span></span> | <span data-ttu-id="63d69-392">Arrière-plan en rouge</span><span class="sxs-lookup"><span data-stu-id="63d69-392">Background Red</span></span> | <span data-ttu-id="63d69-393">Applique la couleur rouge vif sans mise en gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-393">Applies non-bold/bright red to background</span></span> |
| <span data-ttu-id="63d69-394">42</span><span class="sxs-lookup"><span data-stu-id="63d69-394">42</span></span> | <span data-ttu-id="63d69-395">Arrière-plan en vert</span><span class="sxs-lookup"><span data-stu-id="63d69-395">Background Green</span></span> | <span data-ttu-id="63d69-396">Applique la couleur vert clair sans mise en gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-396">Applies non-bold/bright green to background</span></span> |
| <span data-ttu-id="63d69-397">43</span><span class="sxs-lookup"><span data-stu-id="63d69-397">43</span></span> | <span data-ttu-id="63d69-398">Arrière-plan en jaune</span><span class="sxs-lookup"><span data-stu-id="63d69-398">Background Yellow</span></span> | <span data-ttu-id="63d69-399">Applique la couleur jaune vif sans mise en gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-399">Applies non-bold/bright yellow to background</span></span> |
| <span data-ttu-id="63d69-400">44</span><span class="sxs-lookup"><span data-stu-id="63d69-400">44</span></span> | <span data-ttu-id="63d69-401">Arrière-plan en bleu</span><span class="sxs-lookup"><span data-stu-id="63d69-401">Background Blue</span></span> | <span data-ttu-id="63d69-402">Applique la couleur bleu brillant sans mise en gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-402">Applies non-bold/bright blue to background</span></span> |
| <span data-ttu-id="63d69-403">45</span><span class="sxs-lookup"><span data-stu-id="63d69-403">45</span></span> | <span data-ttu-id="63d69-404">Arrière-plan en magenta</span><span class="sxs-lookup"><span data-stu-id="63d69-404">Background Magenta</span></span> | <span data-ttu-id="63d69-405">Applique la couleur magenta brillant sans mise en gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-405">Applies non-bold/bright magenta to background</span></span> |
| <span data-ttu-id="63d69-406">46</span><span class="sxs-lookup"><span data-stu-id="63d69-406">46</span></span> | <span data-ttu-id="63d69-407">Arrière-plan en cyan</span><span class="sxs-lookup"><span data-stu-id="63d69-407">Background Cyan</span></span> | <span data-ttu-id="63d69-408">Applique la couleur cyan brillant sans mise en gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-408">Applies non-bold/bright cyan to background</span></span> |
| <span data-ttu-id="63d69-409">47</span><span class="sxs-lookup"><span data-stu-id="63d69-409">47</span></span> | <span data-ttu-id="63d69-410">Arrière-plan en blanc</span><span class="sxs-lookup"><span data-stu-id="63d69-410">Background White</span></span> | <span data-ttu-id="63d69-411">Applique la couleur blanc brillant sans mise en gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-411">Applies non-bold/bright white to background</span></span> |
| <span data-ttu-id="63d69-412">48</span><span class="sxs-lookup"><span data-stu-id="63d69-412">48</span></span> | <span data-ttu-id="63d69-413">Arrière-plan avec valeur de couleur étendue</span><span class="sxs-lookup"><span data-stu-id="63d69-413">Background Extended</span></span> | <span data-ttu-id="63d69-414">Applique une valeur de couleur étendue à l’arrière-plan (voir les détails ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="63d69-414">Applies extended color value to the background (see details below)</span></span> |
| <span data-ttu-id="63d69-415">49</span><span class="sxs-lookup"><span data-stu-id="63d69-415">49</span></span> | <span data-ttu-id="63d69-416">Définition par défaut de l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-416">Background Default</span></span> | <span data-ttu-id="63d69-417">Applique uniquement la partie de l’arrière-plan des valeurs par défaut (voir 0).</span><span class="sxs-lookup"><span data-stu-id="63d69-417">Applies only the background portion of the defaults (see 0)</span></span> |
| <span data-ttu-id="63d69-418">90</span><span class="sxs-lookup"><span data-stu-id="63d69-418">90</span></span> | <span data-ttu-id="63d69-419">Premier plan en noir brillant</span><span class="sxs-lookup"><span data-stu-id="63d69-419">Bright Foreground Black</span></span> | <span data-ttu-id="63d69-420">Applique la couleur noir brillant avec mise en gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-420">Applies bold/bright black to foreground</span></span> |
| <span data-ttu-id="63d69-421">91</span><span class="sxs-lookup"><span data-stu-id="63d69-421">91</span></span> | <span data-ttu-id="63d69-422">Premier plan en rouge vif</span><span class="sxs-lookup"><span data-stu-id="63d69-422">Bright Foreground Red</span></span> | <span data-ttu-id="63d69-423">Applique la couleur rouge vif avec mise en gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-423">Applies bold/bright red to foreground</span></span> |
| <span data-ttu-id="63d69-424">92</span><span class="sxs-lookup"><span data-stu-id="63d69-424">92</span></span> | <span data-ttu-id="63d69-425">Premier plan en vert clair</span><span class="sxs-lookup"><span data-stu-id="63d69-425">Bright Foreground Green</span></span> | <span data-ttu-id="63d69-426">Applique la couleur vert clair avec mise en gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-426">Applies bold/bright green to foreground</span></span> |
| <span data-ttu-id="63d69-427">93</span><span class="sxs-lookup"><span data-stu-id="63d69-427">93</span></span> | <span data-ttu-id="63d69-428">Premier plan en jaune vif</span><span class="sxs-lookup"><span data-stu-id="63d69-428">Bright Foreground Yellow</span></span> | <span data-ttu-id="63d69-429">Applique la couleur jaune vif avec mise en gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-429">Applies bold/bright yellow to foreground</span></span> |
| <span data-ttu-id="63d69-430">94</span><span class="sxs-lookup"><span data-stu-id="63d69-430">94</span></span> | <span data-ttu-id="63d69-431">Premier plan en bleu brillant</span><span class="sxs-lookup"><span data-stu-id="63d69-431">Bright Foreground Blue</span></span> | <span data-ttu-id="63d69-432">Applique la couleur bleu brillant avec mise en gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-432">Applies bold/bright blue to foreground</span></span> |
| <span data-ttu-id="63d69-433">95</span><span class="sxs-lookup"><span data-stu-id="63d69-433">95</span></span> | <span data-ttu-id="63d69-434">Premier plan en magenta brillant</span><span class="sxs-lookup"><span data-stu-id="63d69-434">Bright Foreground Magenta</span></span> | <span data-ttu-id="63d69-435">Applique la couleur magenta brillant avec mise en gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-435">Applies bold/bright magenta to foreground</span></span> |
| <span data-ttu-id="63d69-436">96</span><span class="sxs-lookup"><span data-stu-id="63d69-436">96</span></span> | <span data-ttu-id="63d69-437">Premier plan en cyan brillant</span><span class="sxs-lookup"><span data-stu-id="63d69-437">Bright Foreground Cyan</span></span> | <span data-ttu-id="63d69-438">Applique la couleur cyan brillant avec mise en gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-438">Applies bold/bright cyan to foreground</span></span> |
| <span data-ttu-id="63d69-439">97</span><span class="sxs-lookup"><span data-stu-id="63d69-439">97</span></span> | <span data-ttu-id="63d69-440">Premier plan en blanc brillant</span><span class="sxs-lookup"><span data-stu-id="63d69-440">Bright Foreground White</span></span> | <span data-ttu-id="63d69-441">Applique la couleur blanc brillant avec mise en gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="63d69-441">Applies bold/bright white to foreground</span></span> |
| <span data-ttu-id="63d69-442">100</span><span class="sxs-lookup"><span data-stu-id="63d69-442">100</span></span> | <span data-ttu-id="63d69-443">Arrière-plan en noir brillant</span><span class="sxs-lookup"><span data-stu-id="63d69-443">Bright Background Black</span></span> | <span data-ttu-id="63d69-444">Applique la couleur noir brillant avec mise en gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-444">Applies bold/bright black to background</span></span> |
| <span data-ttu-id="63d69-445">101</span><span class="sxs-lookup"><span data-stu-id="63d69-445">101</span></span> | <span data-ttu-id="63d69-446">Arrière-plan en rouge vif</span><span class="sxs-lookup"><span data-stu-id="63d69-446">Bright Background Red</span></span> | <span data-ttu-id="63d69-447">Applique la couleur rouge vif avec mise en gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-447">Applies bold/bright red to background</span></span> |
| <span data-ttu-id="63d69-448">102</span><span class="sxs-lookup"><span data-stu-id="63d69-448">102</span></span> | <span data-ttu-id="63d69-449">Arrière-plan en vert clair</span><span class="sxs-lookup"><span data-stu-id="63d69-449">Bright Background Green</span></span> | <span data-ttu-id="63d69-450">Applique la couleur vert clair avec mise en gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-450">Applies bold/bright green to background</span></span> |
| <span data-ttu-id="63d69-451">103</span><span class="sxs-lookup"><span data-stu-id="63d69-451">103</span></span> | <span data-ttu-id="63d69-452">Arrière-plan en jaune vif</span><span class="sxs-lookup"><span data-stu-id="63d69-452">Bright Background Yellow</span></span> | <span data-ttu-id="63d69-453">Applique la couleur jaune vif avec mise en gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-453">Applies bold/bright yellow to background</span></span> |
| <span data-ttu-id="63d69-454">104</span><span class="sxs-lookup"><span data-stu-id="63d69-454">104</span></span> | <span data-ttu-id="63d69-455">Arrière-plan en bleu brillant</span><span class="sxs-lookup"><span data-stu-id="63d69-455">Bright Background Blue</span></span> | <span data-ttu-id="63d69-456">Applique la couleur bleu brillant avec mise en gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-456">Applies bold/bright blue to background</span></span> |
| <span data-ttu-id="63d69-457">105</span><span class="sxs-lookup"><span data-stu-id="63d69-457">105</span></span> | <span data-ttu-id="63d69-458">Arrière-plan en magenta brillant</span><span class="sxs-lookup"><span data-stu-id="63d69-458">Bright Background Magenta</span></span> | <span data-ttu-id="63d69-459">Applique la couleur magenta brillant avec mise en gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-459">Applies bold/bright magenta to background</span></span> |
| <span data-ttu-id="63d69-460">106</span><span class="sxs-lookup"><span data-stu-id="63d69-460">106</span></span> | <span data-ttu-id="63d69-461">Arrière-plan en cyan brillant</span><span class="sxs-lookup"><span data-stu-id="63d69-461">Bright Background Cyan</span></span> | <span data-ttu-id="63d69-462">Applique la couleur cyan brillant avec mise en gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-462">Applies bold/bright cyan to background</span></span> |
| <span data-ttu-id="63d69-463">107</span><span class="sxs-lookup"><span data-stu-id="63d69-463">107</span></span> | <span data-ttu-id="63d69-464">Arrière-plan en blanc brillant</span><span class="sxs-lookup"><span data-stu-id="63d69-464">Bright Background White</span></span> | <span data-ttu-id="63d69-465">Applique la couleur blanc brillant avec mise en gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="63d69-465">Applies bold/bright white to background</span></span> |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span data-ttu-id="63d69-466"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Couleurs étendues</span><span class="sxs-lookup"><span data-stu-id="63d69-466"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Extended Colors</span></span>

<span data-ttu-id="63d69-467">Certains émulateurs de terminaux virtuels prennent en charge une palette de couleurs supérieure aux 16 couleurs fournies par la console Windows.</span><span class="sxs-lookup"><span data-stu-id="63d69-467">Some virtual terminal emulators support a palette of colors greater than the 16 colors provided by the Windows Console.</span></span> <span data-ttu-id="63d69-468">Pour ces couleurs étendues, la console Windows choisit la couleur appropriée la plus proche dans la table de 16 couleurs existante pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="63d69-468">For these extended colors, the Windows Console will choose the nearest appropriate color from the existing 16 color table for display.</span></span> <span data-ttu-id="63d69-469">Contrairement aux valeurs SGR classiques ci-dessus, les valeurs étendues consomment des paramètres supplémentaires après l’indicateur initial, conformément au tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="63d69-469">Unlike typical SGR values above, the extended values will consume additional parameters after the initial indicator according to the table below.</span></span>


| <span data-ttu-id="63d69-470">Sous-séquence SGR</span><span class="sxs-lookup"><span data-stu-id="63d69-470">SGR Subsequence</span></span> | <span data-ttu-id="63d69-471">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-471">Description</span></span> |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="63d69-472">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="63d69-472">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="63d69-473">Définir la couleur de premier plan sur la valeur RVB spécifiée dans les paramètres &lt;r&gt;, &lt;g&gt;, &lt;b&gt; \*</span><span class="sxs-lookup"><span data-stu-id="63d69-473">Set foreground color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="63d69-474">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="63d69-474">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="63d69-475">Définir la couleur d’arrière-plan sur la valeur RVB spécifiée dans les paramètres &lt;r&gt;, &lt;g&gt;, &lt;b&gt; \*</span><span class="sxs-lookup"><span data-stu-id="63d69-475">Set background color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="63d69-476">38 ; 5 ; &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="63d69-476">38 ; 5 ; &lt;s&gt;</span></span> | <span data-ttu-id="63d69-477">Définir la couleur de premier plan sur l’index &lt;s&gt; dans la table de 88 ou 256 couleurs\*</span><span class="sxs-lookup"><span data-stu-id="63d69-477">Set foreground color to &lt;s&gt; index in 88 or 256 color table\*</span></span> |
| <span data-ttu-id="63d69-478">48 ; 5 ; &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="63d69-478">48 ; 5 ; &lt;s&gt;</span></span> | <span data-ttu-id="63d69-479">Définir la couleur d’arrière-plan sur l’index &lt;s&gt; dans la table de 88 ou 256 couleurs\*</span><span class="sxs-lookup"><span data-stu-id="63d69-479">Set background color to &lt;s&gt; index in 88 or 256 color table\*</span></span> |



<span data-ttu-id="63d69-480">\*Les palettes de 88 et 256 couleurs gérées en interne pour la comparaison sont basées sur l’émulateur de terminal xterm.</span><span class="sxs-lookup"><span data-stu-id="63d69-480">\*The 88 and 256 color palettes maintained internally for comparison are based from the xterm terminal emulator.</span></span> <span data-ttu-id="63d69-481">Les tables de comparaison et d’arrondi ne peuvent pas être modifiées pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="63d69-481">The comparison/rounding tables cannot be modified at this time.</span></span>


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span data-ttu-id="63d69-482"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Couleurs d’écran</span><span class="sxs-lookup"><span data-stu-id="63d69-482"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Screen Colors</span></span>


<span data-ttu-id="63d69-483">La commande suivante permet à l’application de définir les valeurs de la palette de couleurs d’écran sur n’importe quelle valeur RVB.</span><span class="sxs-lookup"><span data-stu-id="63d69-483">The following command allows the application to set the screen colors palette values to any RGB value.</span></span>

<span data-ttu-id="63d69-484">Les valeurs RVB doivent être des valeurs hexadécimales comprises entre `0` et `ff` séparées par le caractère barre oblique (par exemple, `rgb:1/24/86`).</span><span class="sxs-lookup"><span data-stu-id="63d69-484">The RGB values should be hexadecimal values between `0` and `ff`, and separated by the forward-slash character (e.g. `rgb:1/24/86`).</span></span>

<span data-ttu-id="63d69-485">Notez que cette séquence est une séquence OSC (Operating System Command, commande de système d’exploitation), et non une séquence CSI telle que la plupart des autres séquences listées. Ainsi, elle commence par « \\x1b\] », et non pas par « \\x1b\[ ».</span><span class="sxs-lookup"><span data-stu-id="63d69-485">Note that this sequence is an OSC “Operating system command” sequence, and not a CSI like many of the other sequences listed, and as such start with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="63d69-486">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-486">Sequence</span></span> | <span data-ttu-id="63d69-487">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-487">Description</span></span> | <span data-ttu-id="63d69-488">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-488">Behavior</span></span> |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="63d69-489">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span><span class="sxs-lookup"><span data-stu-id="63d69-489">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span></span> | <span data-ttu-id="63d69-490">Modifier les couleurs d’écran</span><span class="sxs-lookup"><span data-stu-id="63d69-490">Modify Screen Colors</span></span> | <span data-ttu-id="63d69-491">Définit l’index &lt;i&gt; de la palette de couleurs d’écran sur les valeurs RVB spécifiées dans &lt;r&gt;, &lt;g&gt;, &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="63d69-491">Sets the screen color palette index &lt;i&gt; to the RGB values specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt;</span></span> |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span data-ttu-id="63d69-492"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Changements de mode</span><span class="sxs-lookup"><span data-stu-id="63d69-492"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Mode Changes</span></span>


<span data-ttu-id="63d69-493">Il s’agit de séquences qui contrôlent les modes d’entrée.</span><span class="sxs-lookup"><span data-stu-id="63d69-493">These are sequences that control the input modes.</span></span> <span data-ttu-id="63d69-494">Il existe deux ensembles différents de modes d’entrée : le mode touches de direction et le mode touches du pavé numérique.</span><span class="sxs-lookup"><span data-stu-id="63d69-494">There are two different sets of input modes, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="63d69-495">Le mode touches de direction contrôle les séquences émises par les touches de direction, Début et Fin, tandis que le mode touches du pavé numérique contrôle les séquences émises par les touches du pavé numérique, essentiellement, ainsi que par les touches de fonction.</span><span class="sxs-lookup"><span data-stu-id="63d69-495">The Cursor Keys Mode controls the sequences that are emitted by the arrow keys as well as Home and End, while the Keypad Keys Mode controls the sequences emitted by the keys on the numpad primarily, as well as the function keys.</span></span>

<span data-ttu-id="63d69-496">Chacun de ces modes est constitué de paramètres booléens simples : le mode touches de direction est Normal (valeur par défaut) ou Application, tandis que le mode touches du pavé numérique est soit Numérique (valeur par défaut), soit Application.</span><span class="sxs-lookup"><span data-stu-id="63d69-496">Each of these modes are simple boolean settings – the Cursor Keys Mode is either Normal (default) or Application, and the Keypad Keys Mode is either Numeric (default) or Application.</span></span>

<span data-ttu-id="63d69-497">Consultez les sections Touches de direction et Touches de fonction et pavé numérique pour connaître les séquences émises dans ces modes.</span><span class="sxs-lookup"><span data-stu-id="63d69-497">See the Cursor Keys and Numpad & Function Keys sections for the sequences emitted in these modes.</span></span>


| <span data-ttu-id="63d69-498">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-498">Sequence</span></span> | <span data-ttu-id="63d69-499">Code</span><span class="sxs-lookup"><span data-stu-id="63d69-499">Code</span></span> | <span data-ttu-id="63d69-500">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-500">Description</span></span> | <span data-ttu-id="63d69-501">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-501">Behavior</span></span> |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| <span data-ttu-id="63d69-502">ESC =</span><span class="sxs-lookup"><span data-stu-id="63d69-502">ESC =</span></span> | <span data-ttu-id="63d69-503">DECKPAM</span><span class="sxs-lookup"><span data-stu-id="63d69-503">DECKPAM</span></span> | <span data-ttu-id="63d69-504">Activer le mode Application du pavé numérique</span><span class="sxs-lookup"><span data-stu-id="63d69-504">Enable Keypad Application Mode</span></span> | <span data-ttu-id="63d69-505">Les touches du pavé numérique émettent leurs séquences en mode Application.</span><span class="sxs-lookup"><span data-stu-id="63d69-505">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="63d69-506">ESC &gt;</span><span class="sxs-lookup"><span data-stu-id="63d69-506">ESC &gt;</span></span> | <span data-ttu-id="63d69-507">DECKPNM</span><span class="sxs-lookup"><span data-stu-id="63d69-507">DECKPNM</span></span> | <span data-ttu-id="63d69-508">Activer le mode Numérique du pavé numérique</span><span class="sxs-lookup"><span data-stu-id="63d69-508">Enable Keypad Numeric Mode</span></span> | <span data-ttu-id="63d69-509">Les touches du pavé numérique émettent leurs séquences en mode Numérique.</span><span class="sxs-lookup"><span data-stu-id="63d69-509">Keypad keys will emit their Numeric Mode sequences.</span></span> |
| <span data-ttu-id="63d69-510">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="63d69-510">ESC \[ ?</span></span> <span data-ttu-id="63d69-511">1 h</span><span class="sxs-lookup"><span data-stu-id="63d69-511">1 h</span></span> | <span data-ttu-id="63d69-512">DECCKM</span><span class="sxs-lookup"><span data-stu-id="63d69-512">DECCKM</span></span> | <span data-ttu-id="63d69-513">Activer le mode Application de touches de direction</span><span class="sxs-lookup"><span data-stu-id="63d69-513">Enable Cursor Keys Application Mode</span></span> | <span data-ttu-id="63d69-514">Les touches du pavé numérique émettent leurs séquences en mode Application.</span><span class="sxs-lookup"><span data-stu-id="63d69-514">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="63d69-515">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="63d69-515">ESC \[ ?</span></span> <span data-ttu-id="63d69-516">1 l</span><span class="sxs-lookup"><span data-stu-id="63d69-516">1 l</span></span> | <span data-ttu-id="63d69-517">DECCKM</span><span class="sxs-lookup"><span data-stu-id="63d69-517">DECCKM</span></span> | <span data-ttu-id="63d69-518">Désactiver le mode Application de touches de direction (utiliser le mode Normal)</span><span class="sxs-lookup"><span data-stu-id="63d69-518">Disable Cursor Keys Application Mode (use Normal Mode)</span></span> | <span data-ttu-id="63d69-519">Les touches du pavé numérique émettent leurs séquences en mode Numérique.</span><span class="sxs-lookup"><span data-stu-id="63d69-519">Keypad keys will emit their Numeric Mode sequences.</span></span> |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span data-ttu-id="63d69-520"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>État de requête</span><span class="sxs-lookup"><span data-stu-id="63d69-520"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Query State</span></span>


<span data-ttu-id="63d69-521">Toutes les commandes de cette section équivalent généralement à appeler les API de console \* pour récupérer les informations sur l’état actuel de la mémoire tampon de la console.</span><span class="sxs-lookup"><span data-stu-id="63d69-521">All commands in this section are generally equivalent to calling Get\* console APIs to retrieve status information about the current console buffer state.</span></span>

> [!NOTE]
><span data-ttu-id="63d69-522">Ces requêtes émettent leurs réponses dans le flux d’entrée de la console immédiatement après avoir été reconnues sur le flux de sortie si l’indicateur ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING est défini.</span><span class="sxs-lookup"><span data-stu-id="63d69-522">These queries will emit their responses into the console input stream immediately after being recognized on the output stream while ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING is set.</span></span> <span data-ttu-id="63d69-523">L’indicateur ENABLE\_VIRTUAL\_TERMINAL\_INPUT ne s’applique pas aux commandes de requête, car il est supposé qu’une application qui effectue la requête doit toujours recevoir la réponse.</span><span class="sxs-lookup"><span data-stu-id="63d69-523">The ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag does not apply to query commands as it is assumed that an application making the query will always want to receive the reply.</span></span>




| <span data-ttu-id="63d69-524">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-524">Sequence</span></span> | <span data-ttu-id="63d69-525">Code</span><span class="sxs-lookup"><span data-stu-id="63d69-525">Code</span></span> | <span data-ttu-id="63d69-526">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-526">Description</span></span> | <span data-ttu-id="63d69-527">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-527">Behavior</span></span> |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="63d69-528">ESC \[ 6 n</span><span class="sxs-lookup"><span data-stu-id="63d69-528">ESC \[ 6 n</span></span> | <span data-ttu-id="63d69-529">DECXCPR</span><span class="sxs-lookup"><span data-stu-id="63d69-529">DECXCPR</span></span> | <span data-ttu-id="63d69-530">Signaler la position du curseur</span><span class="sxs-lookup"><span data-stu-id="63d69-530">Report Cursor Position</span></span> | <span data-ttu-id="63d69-531">Émet la position du curseur comme suit : ESC \[ &lt;r&gt; ; &lt;c&gt; R où &lt;r&gt; = ligne du curseur et &lt;c&gt; = colonne du curseur</span><span class="sxs-lookup"><span data-stu-id="63d69-531">Emit the cursor position as: ESC \[ &lt;r&gt; ; &lt;c&gt; R Where &lt;r&gt; = cursor row and &lt;c&gt; = cursor column</span></span> |
| <span data-ttu-id="63d69-532">ESC \[ 0 c</span><span class="sxs-lookup"><span data-stu-id="63d69-532">ESC \[ 0 c</span></span> | <span data-ttu-id="63d69-533">DA</span><span class="sxs-lookup"><span data-stu-id="63d69-533">DA</span></span> | <span data-ttu-id="63d69-534">Attributs de l’appareil</span><span class="sxs-lookup"><span data-stu-id="63d69-534">Device Attributes</span></span> | <span data-ttu-id="63d69-535">Signaler l’identité du terminal.</span><span class="sxs-lookup"><span data-stu-id="63d69-535">Report the terminal identity.</span></span> <span data-ttu-id="63d69-536">Émet « \\x1b\[?1;0c », en indiquant « VT101 with No Options » (VT101 sans options).</span><span class="sxs-lookup"><span data-stu-id="63d69-536">Will emit “\\x1b\[?1;0c”, indicating "VT101 with No Options".</span></span> |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span data-ttu-id="63d69-537"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabulations</span><span class="sxs-lookup"><span data-stu-id="63d69-537"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabs</span></span>


<span data-ttu-id="63d69-538">Alors que la console Windows s’attend traditionnellement à ce que les tabulations aient exclusivement une largeur de huit caractères, les applications \*nix utilisant certaines séquences peuvent manipuler la position des taquets de tabulation dans les fenêtres de console pour optimiser le déplacement du curseur par l’application.</span><span class="sxs-lookup"><span data-stu-id="63d69-538">While the windows console traditionally expects tabs to be exclusively eight characters wide, \*nix applications utilizing certain sequences can manipulate where the tab stops are within the console windows to optimize cursor movement by the application.</span></span>

<span data-ttu-id="63d69-539">Les séquences suivantes permettent à une application de définir les positions des taquets de tabulation dans la fenêtre de console, de supprimer ces derniers et de passer de l’un à l’autre.</span><span class="sxs-lookup"><span data-stu-id="63d69-539">The following sequences allow an application to set the tab stop locations within the console window, remove them, and navigate between them.</span></span>


| <span data-ttu-id="63d69-540">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-540">Sequence</span></span> | <span data-ttu-id="63d69-541">Code</span><span class="sxs-lookup"><span data-stu-id="63d69-541">Code</span></span> | <span data-ttu-id="63d69-542">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-542">Description</span></span> | <span data-ttu-id="63d69-543">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-543">Behavior</span></span> |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="63d69-544">ESC H</span><span class="sxs-lookup"><span data-stu-id="63d69-544">ESC H</span></span> | <span data-ttu-id="63d69-545">HTS</span><span class="sxs-lookup"><span data-stu-id="63d69-545">HTS</span></span> | <span data-ttu-id="63d69-546">Définir une tabulation horizontale</span><span class="sxs-lookup"><span data-stu-id="63d69-546">Horizontal Tab Set</span></span> | <span data-ttu-id="63d69-547">Définit un taquet de tabulation au niveau de la colonne à laquelle se trouve actuellement le curseur.</span><span class="sxs-lookup"><span data-stu-id="63d69-547">Sets a tab stop in the current column the cursor is in.</span></span> |
| <span data-ttu-id="63d69-548">ESC \[ &lt;n&gt; I</span><span class="sxs-lookup"><span data-stu-id="63d69-548">ESC \[ &lt;n&gt; I</span></span> | <span data-ttu-id="63d69-549">CHT</span><span class="sxs-lookup"><span data-stu-id="63d69-549">CHT</span></span> | <span data-ttu-id="63d69-550">Déplacer le curseur vers un taquet de tabulation horizontale (vers l’avant)</span><span class="sxs-lookup"><span data-stu-id="63d69-550">Cursor Horizontal (Forward) Tab</span></span> | <span data-ttu-id="63d69-551">Avance le curseur jusqu’à la colonne suivante (sur la même ligne) ayant un taquet de tabulation.</span><span class="sxs-lookup"><span data-stu-id="63d69-551">Advance the cursor to the next column (in the same row) with a tab stop.</span></span> <span data-ttu-id="63d69-552">S’il n’y a plus de taquets de tabulation, passe à la dernière colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="63d69-552">If there are no more tab stops, move to the last column in the row.</span></span> <span data-ttu-id="63d69-553">Si le curseur se trouve à la dernière colonne, passe à la première colonne de la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="63d69-553">If the cursor is in the last column, move to the first column of the next row.</span></span> |
| <span data-ttu-id="63d69-554">ESC \[ &lt;n&gt; Z</span><span class="sxs-lookup"><span data-stu-id="63d69-554">ESC \[ &lt;n&gt; Z</span></span> | <span data-ttu-id="63d69-555">CBT</span><span class="sxs-lookup"><span data-stu-id="63d69-555">CBT</span></span> | <span data-ttu-id="63d69-556">Déplacer le curseur vers un taquet de tabulation vers l’arrière</span><span class="sxs-lookup"><span data-stu-id="63d69-556">Cursor Backwards Tab</span></span> | <span data-ttu-id="63d69-557">Déplace le curseur jusqu’à la colonne précédente (sur la même ligne) ayant un taquet de tabulation.</span><span class="sxs-lookup"><span data-stu-id="63d69-557">Move the cursor to the previous column (in the same row) with a tab stop.</span></span> <span data-ttu-id="63d69-558">S’il n’y a plus de taquets de tabulation, déplace le curseur jusqu’à la première colonne.</span><span class="sxs-lookup"><span data-stu-id="63d69-558">If there are no more tab stops, moves the cursor to the first column.</span></span> <span data-ttu-id="63d69-559">Si le curseur se trouve à la première colonne, ne déplace pas le curseur.</span><span class="sxs-lookup"><span data-stu-id="63d69-559">If the cursor is in the first column, doesn’t move the cursor.</span></span> |
| <span data-ttu-id="63d69-560">ESC \[ 0 g</span><span class="sxs-lookup"><span data-stu-id="63d69-560">ESC \[ 0 g</span></span> | <span data-ttu-id="63d69-561">À confirmer</span><span class="sxs-lookup"><span data-stu-id="63d69-561">TBC</span></span> | <span data-ttu-id="63d69-562">Effacer un taquet de tabulation (colonne actuelle)</span><span class="sxs-lookup"><span data-stu-id="63d69-562">Tab Clear (current column)</span></span> | <span data-ttu-id="63d69-563">Efface le taquet de tabulation à la colonne actuelle, s’il en existe un.</span><span class="sxs-lookup"><span data-stu-id="63d69-563">Clears the tab stop in the current column, if there is one.</span></span> <span data-ttu-id="63d69-564">Sinon, ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="63d69-564">Otherwise does nothing.</span></span> |
| <span data-ttu-id="63d69-565">ESC \[ 3 g</span><span class="sxs-lookup"><span data-stu-id="63d69-565">ESC \[ 3 g</span></span> | <span data-ttu-id="63d69-566">À confirmer</span><span class="sxs-lookup"><span data-stu-id="63d69-566">TBC</span></span> | <span data-ttu-id="63d69-567">Effacer les taquets de tabulation (toutes les colonnes)</span><span class="sxs-lookup"><span data-stu-id="63d69-567">Tab Clear (all columns)</span></span> | <span data-ttu-id="63d69-568">Efface tous les taquets de tabulation actuellement définis.</span><span class="sxs-lookup"><span data-stu-id="63d69-568">Clears all currently set tab stops.</span></span> |



- <span data-ttu-id="63d69-569">Pour CHT et CBT, &lt;n&gt; est un paramètre facultatif (valeur par défaut = 1) qui indique combien de fois il faut avancer le curseur dans la direction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="63d69-569">For both CHT and CBT, &lt;n&gt; is an optional parameter that (default=1) indicating how many times to advance the cursor in the specified direction.</span></span>
- <span data-ttu-id="63d69-570">Si aucun taquet de tabulation n’est défini par le biais de HTS, CHT et CBT traitent les première et dernière colonnes de la fenêtre comme étant les deux seuls taquets de tabulation.</span><span class="sxs-lookup"><span data-stu-id="63d69-570">If there are no tab stops set via HTS, CHT and CBT will treat the first and last columns of the window as the only two tab stops.</span></span>
- <span data-ttu-id="63d69-571">En outre, quand HTS est utilisé pour définir un taquet de tabulation, la console accède au taquet de tabulation suivant sur la sortie d’un caractère de tabulation (0x09, '\\t'), de la même manière que CHT.</span><span class="sxs-lookup"><span data-stu-id="63d69-571">Using HTS to set a tab stop will also cause the console to navigate to the next tab stop on the output of a TAB (0x09, ‘\\t’) character, in the same manner as CHT.</span></span>

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span data-ttu-id="63d69-572"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Désigner le jeu de caractères</span><span class="sxs-lookup"><span data-stu-id="63d69-572"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designate Character Set</span></span>


<span data-ttu-id="63d69-573">Les séquences suivantes permettent à un programme de changer le mappage du jeu de caractères actif.</span><span class="sxs-lookup"><span data-stu-id="63d69-573">The following sequences allow a program to change the active character set mapping.</span></span> <span data-ttu-id="63d69-574">Ainsi, un programme peut émettre des caractères ASCII de 7 bits, mais les faire s’afficher sous la forme d’autres glyphes sur l’écran de terminal lui-même.</span><span class="sxs-lookup"><span data-stu-id="63d69-574">This allows a program to emit 7-bit ASCII characters, but have them displayed as other glyphs on the terminal screen itself.</span></span> <span data-ttu-id="63d69-575">Les deux seuls jeux de caractères pris en charge sont ASCII (par défaut) et le jeu de caractères DEC Special Graphics.</span><span class="sxs-lookup"><span data-stu-id="63d69-575">Currently, the only two supported character sets are ASCII (default) and the DEC Special Graphics Character Set.</span></span> <span data-ttu-id="63d69-576">Consultez <http://vt100.net/docs/vt220-rm/table2-4.html> pour obtenir la liste de tous les caractères représentés par le jeu de caractères DEC Special Graphics.</span><span class="sxs-lookup"><span data-stu-id="63d69-576">See <http://vt100.net/docs/vt220-rm/table2-4.html> for a listing of all of the characters represented by the DEC Special Graphics Character Set.</span></span>


| <span data-ttu-id="63d69-577">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-577">Sequence</span></span> | <span data-ttu-id="63d69-578">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-578">Description</span></span> | <span data-ttu-id="63d69-579">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-579">Behavior</span></span> |
|----------|--------------------------------------------|-------------------------------|
| <span data-ttu-id="63d69-580">ESC ( 0</span><span class="sxs-lookup"><span data-stu-id="63d69-580">ESC ( 0</span></span> | <span data-ttu-id="63d69-581">Désigner le jeu de caractères – Dessin de ligne DEC</span><span class="sxs-lookup"><span data-stu-id="63d69-581">Designate Character Set – DEC Line Drawing</span></span> | <span data-ttu-id="63d69-582">Active le mode de dessin de la ligne DEC</span><span class="sxs-lookup"><span data-stu-id="63d69-582">Enables DEC Line Drawing Mode</span></span> |
| <span data-ttu-id="63d69-583">ESC ( B</span><span class="sxs-lookup"><span data-stu-id="63d69-583">ESC ( B</span></span> | <span data-ttu-id="63d69-584">Désigner le jeu de caractères – ASCII des États-Unis</span><span class="sxs-lookup"><span data-stu-id="63d69-584">Designate Character Set – US ASCII</span></span> | <span data-ttu-id="63d69-585">Active le mode ASCII (par défaut)</span><span class="sxs-lookup"><span data-stu-id="63d69-585">Enables ASCII Mode (Default)</span></span> |



<span data-ttu-id="63d69-586">En particulier, le mode de dessin de ligne DEC est utilisé pour dessiner les bordures dans les applications console.</span><span class="sxs-lookup"><span data-stu-id="63d69-586">Notably, the DEC Line Drawing mode is used for drawing borders in console applications.</span></span> <span data-ttu-id="63d69-587">Le tableau suivant indique les correspondances entre les caractères ASCII et les caractères de dessin de ligne.</span><span class="sxs-lookup"><span data-stu-id="63d69-587">The following table shows what ASCII character maps to which line drawing character.</span></span>


| <span data-ttu-id="63d69-588">Hex</span><span class="sxs-lookup"><span data-stu-id="63d69-588">Hex</span></span> | <span data-ttu-id="63d69-589">ASCII</span><span class="sxs-lookup"><span data-stu-id="63d69-589">ASCII</span></span> | <span data-ttu-id="63d69-590">Dessin de ligne DEC</span><span class="sxs-lookup"><span data-stu-id="63d69-590">DEC Line Drawing</span></span> |
|------|-------|------------------|
| <span data-ttu-id="63d69-591">0x6a</span><span class="sxs-lookup"><span data-stu-id="63d69-591">0x6a</span></span> | <span data-ttu-id="63d69-592">j</span><span class="sxs-lookup"><span data-stu-id="63d69-592">j</span></span> | <span data-ttu-id="63d69-593">┘</span><span class="sxs-lookup"><span data-stu-id="63d69-593">┘</span></span> |
| <span data-ttu-id="63d69-594">0x6b</span><span class="sxs-lookup"><span data-stu-id="63d69-594">0x6b</span></span> | <span data-ttu-id="63d69-595">k</span><span class="sxs-lookup"><span data-stu-id="63d69-595">k</span></span> | <span data-ttu-id="63d69-596">┐</span><span class="sxs-lookup"><span data-stu-id="63d69-596">┐</span></span> |
| <span data-ttu-id="63d69-597">0x6c</span><span class="sxs-lookup"><span data-stu-id="63d69-597">0x6c</span></span> | <span data-ttu-id="63d69-598">l</span><span class="sxs-lookup"><span data-stu-id="63d69-598">l</span></span> | <span data-ttu-id="63d69-599">┌</span><span class="sxs-lookup"><span data-stu-id="63d69-599">┌</span></span> |
| <span data-ttu-id="63d69-600">0x6d</span><span class="sxs-lookup"><span data-stu-id="63d69-600">0x6d</span></span> | <span data-ttu-id="63d69-601">m</span><span class="sxs-lookup"><span data-stu-id="63d69-601">m</span></span> | <span data-ttu-id="63d69-602">└</span><span class="sxs-lookup"><span data-stu-id="63d69-602">└</span></span> |
| <span data-ttu-id="63d69-603">0x6e</span><span class="sxs-lookup"><span data-stu-id="63d69-603">0x6e</span></span> | <span data-ttu-id="63d69-604">n</span><span class="sxs-lookup"><span data-stu-id="63d69-604">n</span></span> | <span data-ttu-id="63d69-605">┼</span><span class="sxs-lookup"><span data-stu-id="63d69-605">┼</span></span> |
| <span data-ttu-id="63d69-606">0x71</span><span class="sxs-lookup"><span data-stu-id="63d69-606">0x71</span></span> | <span data-ttu-id="63d69-607">q</span><span class="sxs-lookup"><span data-stu-id="63d69-607">q</span></span> | <span data-ttu-id="63d69-608">─</span><span class="sxs-lookup"><span data-stu-id="63d69-608">─</span></span> |
| <span data-ttu-id="63d69-609">0x74</span><span class="sxs-lookup"><span data-stu-id="63d69-609">0x74</span></span> | <span data-ttu-id="63d69-610">t</span><span class="sxs-lookup"><span data-stu-id="63d69-610">t</span></span> | <span data-ttu-id="63d69-611">├</span><span class="sxs-lookup"><span data-stu-id="63d69-611">├</span></span> |
| <span data-ttu-id="63d69-612">0x75</span><span class="sxs-lookup"><span data-stu-id="63d69-612">0x75</span></span> | <span data-ttu-id="63d69-613">u</span><span class="sxs-lookup"><span data-stu-id="63d69-613">u</span></span> | <span data-ttu-id="63d69-614">┤</span><span class="sxs-lookup"><span data-stu-id="63d69-614">┤</span></span> |
| <span data-ttu-id="63d69-615">0x76</span><span class="sxs-lookup"><span data-stu-id="63d69-615">0x76</span></span> | <span data-ttu-id="63d69-616">v</span><span class="sxs-lookup"><span data-stu-id="63d69-616">v</span></span> | <span data-ttu-id="63d69-617">┴</span><span class="sxs-lookup"><span data-stu-id="63d69-617">┴</span></span> |
| <span data-ttu-id="63d69-618">0x77</span><span class="sxs-lookup"><span data-stu-id="63d69-618">0x77</span></span> | <span data-ttu-id="63d69-619">w</span><span class="sxs-lookup"><span data-stu-id="63d69-619">w</span></span> | <span data-ttu-id="63d69-620">┬</span><span class="sxs-lookup"><span data-stu-id="63d69-620">┬</span></span> |
| <span data-ttu-id="63d69-621">0x78</span><span class="sxs-lookup"><span data-stu-id="63d69-621">0x78</span></span> | <span data-ttu-id="63d69-622">x</span><span class="sxs-lookup"><span data-stu-id="63d69-622">x</span></span> | <span data-ttu-id="63d69-623">│</span><span class="sxs-lookup"><span data-stu-id="63d69-623">│</span></span> |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span data-ttu-id="63d69-624"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Marges de défilement</span><span class="sxs-lookup"><span data-stu-id="63d69-624"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scrolling Margins</span></span>


<span data-ttu-id="63d69-625">Les séquences suivantes permettent à un programme de configurer la « zone de défilement » de l’écran qui est affectée par les opérations de défilement.</span><span class="sxs-lookup"><span data-stu-id="63d69-625">The following sequences allow a program to configure the “scrolling region” of the screen that is affected by scrolling operations.</span></span> <span data-ttu-id="63d69-626">Il s’agit d’un sous-ensemble des lignes qui sont ajustées en cas de défilement de l’écran, par exemple, sur une commande « \\n » ou RI.</span><span class="sxs-lookup"><span data-stu-id="63d69-626">This is a subset of the rows that are adjusted when the screen would otherwise scroll, for example, on a ‘\\n’ or RI.</span></span> <span data-ttu-id="63d69-627">Ces marges affectent également les lignes modifiées par les commandes d’insertion de ligne (IL), de suppression de ligne (DL), de défilement vers le haut (SU) et de défilement vers le bas (SD).</span><span class="sxs-lookup"><span data-stu-id="63d69-627">These margins also affect the rows modified by Insert Line (IL) and Delete Line (DL), Scroll Up (SU) and Scroll Down (SD).</span></span>

<span data-ttu-id="63d69-628">Les marges de défilement peuvent être particulièrement utiles pour disposer d’une partie de l’écran qui ne défile pas quand le reste de l’écran est rempli, par exemple une barre de titre en haut ou une barre d’état en bas de votre application.</span><span class="sxs-lookup"><span data-stu-id="63d69-628">The scrolling margins can be especially useful for having a portion of the screen that doesn’t scroll when the rest of the screen is filled, such as having a title bar at the top or a status bar at the bottom of your application.</span></span>

<span data-ttu-id="63d69-629">Pour DECSTBM, il existe deux paramètres facultatifs, &lt;t&gt; et &lt;b&gt;, qui servent à spécifier les lignes qui représentent les lignes supérieure et inférieure de la zone de défilement, celles-ci incluses.</span><span class="sxs-lookup"><span data-stu-id="63d69-629">For DECSTBM, there are two optional parameters, &lt;t&gt; and &lt;b&gt;, which are used to specify the rows that represent the top and bottom lines of the scroll region, inclusive.</span></span> <span data-ttu-id="63d69-630">Si les paramètres sont omis, &lt;t&gt; a la valeur par défaut 1 et &lt;b&gt; est défini par défaut sur la hauteur de la fenêtre d’affichage actuelle.</span><span class="sxs-lookup"><span data-stu-id="63d69-630">If the parameters are omitted, &lt;t&gt; defaults to 1 and &lt;b&gt; defaults to the current viewport height.</span></span>

<span data-ttu-id="63d69-631">Les marges de défilement sont définies par mémoire tampon. Il est donc important que la mémoire tampon secondaire et la mémoire tampon principale aient constamment des paramètres de marges de défilement distincts (afin qu’une application en plein écran dans la mémoire tampon secondaire n’altère pas les marges de la mémoire tampon principale).</span><span class="sxs-lookup"><span data-stu-id="63d69-631">Scrolling margins are per-buffer, so importantly, the Alternate Buffer and Main Buffer maintain separate scrolling margins settings (so a full screen application in the alternate buffer will not poison the main buffer’s margins).</span></span>


| <span data-ttu-id="63d69-632">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-632">Sequence</span></span> | <span data-ttu-id="63d69-633">Code</span><span class="sxs-lookup"><span data-stu-id="63d69-633">Code</span></span> | <span data-ttu-id="63d69-634">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-634">Description</span></span> | <span data-ttu-id="63d69-635">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-635">Behavior</span></span> |
|--------------------------------|---------|----------------------|------------------------------------------------|
| <span data-ttu-id="63d69-636">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span><span class="sxs-lookup"><span data-stu-id="63d69-636">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span></span> | <span data-ttu-id="63d69-637">DECSTBM</span><span class="sxs-lookup"><span data-stu-id="63d69-637">DECSTBM</span></span> | <span data-ttu-id="63d69-638">Définir la zone de défilement</span><span class="sxs-lookup"><span data-stu-id="63d69-638">Set Scrolling Region</span></span> | <span data-ttu-id="63d69-639">Définit les marges de défilement des tabulations verticales de la fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="63d69-639">Sets the VT scrolling margins of the viewport.</span></span> |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span data-ttu-id="63d69-640"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Titre de fenêtre</span><span class="sxs-lookup"><span data-stu-id="63d69-640"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Window Title</span></span>


<span data-ttu-id="63d69-641">Les commandes suivantes permettent à l’application de définir le titre de la fenêtre de console sur le paramètre &lt;chaîne&gt; donné.</span><span class="sxs-lookup"><span data-stu-id="63d69-641">The following commands allows the application to set the title of the console window to the given &lt;string&gt; parameter.</span></span> <span data-ttu-id="63d69-642">La chaîne doit contenir moins de 255 caractères pour être acceptée.</span><span class="sxs-lookup"><span data-stu-id="63d69-642">The string must be less than 255 characters to be accepted.</span></span> <span data-ttu-id="63d69-643">Cela équivaut à appeler SetConsoleTitle avec la chaîne donnée.</span><span class="sxs-lookup"><span data-stu-id="63d69-643">This is equivalent to calling SetConsoleTitle with the given string.</span></span>

<span data-ttu-id="63d69-644">Notez que ces séquences sont des séquences OSC, et non des séquence CSI telles que la plupart des autres séquences listées. Ainsi, elle commence par « \\x1b\] », et non pas par « \\x1b\[ ».</span><span class="sxs-lookup"><span data-stu-id="63d69-644">Note that these sequences are OSC “Operating system command” sequences, and not a CSI like many of the other sequences listed, and as such starts with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="63d69-645">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-645">Sequence</span></span> | <span data-ttu-id="63d69-646">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-646">Description</span></span> | <span data-ttu-id="63d69-647">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-647">Behavior</span></span> |
|-------------------------------|---------------------------|----------------------------------------------------|
| <span data-ttu-id="63d69-648">ESC \] 0 ; &lt;chaîne&gt; BEL</span><span class="sxs-lookup"><span data-stu-id="63d69-648">ESC \] 0 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="63d69-649">Définir l’icône et le titre de la fenêtre</span><span class="sxs-lookup"><span data-stu-id="63d69-649">Set Icon and Window Title</span></span> | <span data-ttu-id="63d69-650">Définit le titre de la fenêtre de console sur &lt;chaîne&gt;.</span><span class="sxs-lookup"><span data-stu-id="63d69-650">Sets the console window’s title to &lt;string&gt;.</span></span> |
| <span data-ttu-id="63d69-651">ESC \] 2 ; &lt;chaîne&gt; BEL</span><span class="sxs-lookup"><span data-stu-id="63d69-651">ESC \] 2 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="63d69-652">Définir le titre de la fenêtre</span><span class="sxs-lookup"><span data-stu-id="63d69-652">Set Window Title</span></span> | <span data-ttu-id="63d69-653">Définit le titre de la fenêtre de console sur &lt;chaîne&gt;.</span><span class="sxs-lookup"><span data-stu-id="63d69-653">Sets the console window’s title to &lt;string&gt;.</span></span> |



<span data-ttu-id="63d69-654">En l’occurrence, le caractère de fin est le caractère « sonnerie », « \\x07 »</span><span class="sxs-lookup"><span data-stu-id="63d69-654">The terminating character here is the “Bell” character, ‘\\x07’</span></span>

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span data-ttu-id="63d69-655"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Mémoire tampon d’écran secondaire</span><span class="sxs-lookup"><span data-stu-id="63d69-655"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternate Screen Buffer</span></span>


<span data-ttu-id="63d69-656">Les applications de style \*nix utilisent souvent une mémoire tampon d’écran secondaire, afin de pouvoir modifier l’ensemble du contenu de la mémoire tampon, sans affecter l’application qui les a démarrées.</span><span class="sxs-lookup"><span data-stu-id="63d69-656">\*Nix style applications often utilize an alternate screen buffer, so that they can modify the entire contents of the buffer, without affecting the application that started them.</span></span> <span data-ttu-id="63d69-657">La mémoire tampon secondaire épouse les dimensions de la fenêtre, sans aucune zone de défilement.</span><span class="sxs-lookup"><span data-stu-id="63d69-657">The alternate buffer is exactly the dimensions of the window, without any scrollback region.</span></span>

<span data-ttu-id="63d69-658">À titre d’exemple de ce comportement, pensez à la façon dont vim est lancé à partir de bash.</span><span class="sxs-lookup"><span data-stu-id="63d69-658">For an example of this behavior, consider when vim is launched from bash.</span></span> <span data-ttu-id="63d69-659">Vim utilise l’intégralité de l’écran pour modifier le fichier, puis le retour à bash laisse la mémoire tampon d’origine inchangée.</span><span class="sxs-lookup"><span data-stu-id="63d69-659">Vim uses the entirety of the screen to edit the file, then returning to bash leaves the original buffer unchanged.</span></span>


| <span data-ttu-id="63d69-660">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-660">Sequence</span></span> | <span data-ttu-id="63d69-661">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-661">Description</span></span> | <span data-ttu-id="63d69-662">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-662">Behavior</span></span> |
|--------------------|-----------------------------|--------------------------------------------|
| <span data-ttu-id="63d69-663">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="63d69-663">ESC \[ ?</span></span> <span data-ttu-id="63d69-664">1 0 4 9 h</span><span class="sxs-lookup"><span data-stu-id="63d69-664">1 0 4 9 h</span></span> | <span data-ttu-id="63d69-665">Utiliser une mémoire tampon d’écran secondaire</span><span class="sxs-lookup"><span data-stu-id="63d69-665">Use Alternate Screen Buffer</span></span> | <span data-ttu-id="63d69-666">Bascule vers une nouvelle mémoire tampon d’écran secondaire.</span><span class="sxs-lookup"><span data-stu-id="63d69-666">Switches to a new alternate screen buffer.</span></span> |
| <span data-ttu-id="63d69-667">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="63d69-667">ESC \[ ?</span></span> <span data-ttu-id="63d69-668">1 0 4 9 l</span><span class="sxs-lookup"><span data-stu-id="63d69-668">1 0 4 9 l</span></span> | <span data-ttu-id="63d69-669">Utiliser la mémoire tampon d’écran principale</span><span class="sxs-lookup"><span data-stu-id="63d69-669">Use Main Screen Buffer</span></span> | <span data-ttu-id="63d69-670">Bascule vers la mémoire tampon principale.</span><span class="sxs-lookup"><span data-stu-id="63d69-670">Switches to the main buffer.</span></span> |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span data-ttu-id="63d69-671"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Largeur de la fenêtre</span><span class="sxs-lookup"><span data-stu-id="63d69-671"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Window Width</span></span>


<span data-ttu-id="63d69-672">Les séquences suivantes peuvent être utilisées pour contrôler la largeur de la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="63d69-672">The following sequences can be used to control the width of the console window.</span></span> <span data-ttu-id="63d69-673">Elles équivalent plus ou moins à appeler l’API de console SetConsoleScreenBufferInfoEx pour définir la largeur de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="63d69-673">They are roughly equivalent to the calling the SetConsoleScreenBufferInfoEx console API to set the window width.</span></span>


| <span data-ttu-id="63d69-674">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-674">Sequence</span></span> | <span data-ttu-id="63d69-675">Code</span><span class="sxs-lookup"><span data-stu-id="63d69-675">Code</span></span> | <span data-ttu-id="63d69-676">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-676">Description</span></span> | <span data-ttu-id="63d69-677">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-677">Behavior</span></span> |
|--------------|---------|------------------------------|---------------------------------------------|
| <span data-ttu-id="63d69-678">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="63d69-678">ESC \[ ?</span></span> <span data-ttu-id="63d69-679">3 h</span><span class="sxs-lookup"><span data-stu-id="63d69-679">3 h</span></span> | <span data-ttu-id="63d69-680">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="63d69-680">DECCOLM</span></span> | <span data-ttu-id="63d69-681">Définir le nombre de colonnes sur 132</span><span class="sxs-lookup"><span data-stu-id="63d69-681">Set Number of Columns to 132</span></span> | <span data-ttu-id="63d69-682">Définit la largeur de la console sur une largeur de 132 colonnes.</span><span class="sxs-lookup"><span data-stu-id="63d69-682">Sets the console width to 132 columns wide.</span></span> |
| <span data-ttu-id="63d69-683">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="63d69-683">ESC \[ ?</span></span> <span data-ttu-id="63d69-684">3 l</span><span class="sxs-lookup"><span data-stu-id="63d69-684">3 l</span></span> | <span data-ttu-id="63d69-685">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="63d69-685">DECCOLM</span></span> | <span data-ttu-id="63d69-686">Définir le nombre de colonnes sur 80</span><span class="sxs-lookup"><span data-stu-id="63d69-686">Set Number of Columns to 80</span></span> | <span data-ttu-id="63d69-687">Définit la largeur de la console sur une largeur de 80 colonnes.</span><span class="sxs-lookup"><span data-stu-id="63d69-687">Sets the console width to 80 columns wide.</span></span> |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span data-ttu-id="63d69-688"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Réinitialisation à chaud</span><span class="sxs-lookup"><span data-stu-id="63d69-688"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Soft Reset</span></span>


<span data-ttu-id="63d69-689">La séquence suivante peut être utilisée pour réinitialiser certaines propriétés à leurs valeurs par défaut. Les propriétés suivantes sont réinitialisées aux valeurs par défaut indiquées (les séquences qui contrôlent ces propriétés sont également listées) :</span><span class="sxs-lookup"><span data-stu-id="63d69-689">The following sequence can be used to reset certain properties to their default values.The following properties are reset to the following default values (also listed are the sequences that control those properties):</span></span>

- <span data-ttu-id="63d69-690">Visibilité du curseur : visible (DECTEM)</span><span class="sxs-lookup"><span data-stu-id="63d69-690">Cursor visibility: visible (DECTEM)</span></span>
- <span data-ttu-id="63d69-691">Pavé numérique : mode Numérique (DECNKM)</span><span class="sxs-lookup"><span data-stu-id="63d69-691">Numeric Keypad: Numeric Mode (DECNKM)</span></span>
- <span data-ttu-id="63d69-692">Mode touches de direction : mode Normal (DECCKM)</span><span class="sxs-lookup"><span data-stu-id="63d69-692">Cursor Keys Mode: Normal Mode (DECCKM)</span></span>
- <span data-ttu-id="63d69-693">Marges supérieure et inférieure : supérieure= 1, inférieure = hauteur de la console (DECSTBM)</span><span class="sxs-lookup"><span data-stu-id="63d69-693">Top and Bottom Margins: Top=1, Bottom=Console height (DECSTBM)</span></span>
- <span data-ttu-id="63d69-694">Jeu de caractères : ASCII des États-Unis</span><span class="sxs-lookup"><span data-stu-id="63d69-694">Character Set: US ASCII</span></span>
- <span data-ttu-id="63d69-695">Rendu graphique : Par défaut/désactivé (SGR)</span><span class="sxs-lookup"><span data-stu-id="63d69-695">Graphics Rendition: Default/Off (SGR)</span></span>
- <span data-ttu-id="63d69-696">Enregistrer l’état du curseur : Position de début (0,0) (DECSC)</span><span class="sxs-lookup"><span data-stu-id="63d69-696">Save cursor state: Home position (0,0) (DECSC)</span></span>


| <span data-ttu-id="63d69-697">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-697">Sequence</span></span> | <span data-ttu-id="63d69-698">Code</span><span class="sxs-lookup"><span data-stu-id="63d69-698">Code</span></span> | <span data-ttu-id="63d69-699">Description</span><span class="sxs-lookup"><span data-stu-id="63d69-699">Description</span></span> | <span data-ttu-id="63d69-700">Comportement</span><span class="sxs-lookup"><span data-stu-id="63d69-700">Behavior</span></span> |
|------------|--------|-------------|----------------------------------------------------|
| <span data-ttu-id="63d69-701">ESC \[ !</span><span class="sxs-lookup"><span data-stu-id="63d69-701">ESC \[ !</span></span> <span data-ttu-id="63d69-702">p</span><span class="sxs-lookup"><span data-stu-id="63d69-702">p</span></span> | <span data-ttu-id="63d69-703">DECSTR</span><span class="sxs-lookup"><span data-stu-id="63d69-703">DECSTR</span></span> | <span data-ttu-id="63d69-704">Réinitialisation à chaud</span><span class="sxs-lookup"><span data-stu-id="63d69-704">Soft Reset</span></span> | <span data-ttu-id="63d69-705">Réinitialiser certains paramètres de terminal à leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="63d69-705">Reset certain terminal settings to their defaults.</span></span> |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span data-ttu-id="63d69-706"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Séquences d’entrée</span><span class="sxs-lookup"><span data-stu-id="63d69-706"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Input Sequences</span></span>


<span data-ttu-id="63d69-707">Les séquences de terminal suivantes sont émises par l’hôte de la console sur le flux d’entrée si l’indicateur ENABLE\_VIRTUAL\_TERMINAL\_INPUT est défini sur le descripteur de mémoire tampon d’entrée à l’aide de l’indicateur SetConsoleMode.</span><span class="sxs-lookup"><span data-stu-id="63d69-707">The following terminal sequences are emitted by the console host on the input stream if the ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag is set on the input buffer handle using the SetConsoleMode flag.</span></span>

<span data-ttu-id="63d69-708">Il existe deux modes internes qui déterminent les séquences émises pour les touches d’entrée données : le mode touches de direction et le mode touches du pavé numérique.</span><span class="sxs-lookup"><span data-stu-id="63d69-708">There are two internal modes that control which sequences are emitted for the given input keys, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="63d69-709">Ces modes sont décrits dans la section Changements de mode.</span><span class="sxs-lookup"><span data-stu-id="63d69-709">These are described in the Mode Changes section.</span></span>

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span data-ttu-id="63d69-710"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Touches de direction</span><span class="sxs-lookup"><span data-stu-id="63d69-710"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Cursor Keys</span></span>


| <span data-ttu-id="63d69-711">Clé</span><span class="sxs-lookup"><span data-stu-id="63d69-711">Key</span></span> | <span data-ttu-id="63d69-712">Mode Normal</span><span class="sxs-lookup"><span data-stu-id="63d69-712">Normal Mode</span></span> | <span data-ttu-id="63d69-713">Mode Application</span><span class="sxs-lookup"><span data-stu-id="63d69-713">Application Mode</span></span> |
|-------------|-------------|------------------|
| <span data-ttu-id="63d69-714">Flèche haut</span><span class="sxs-lookup"><span data-stu-id="63d69-714">Up Arrow</span></span> | <span data-ttu-id="63d69-715">ESC \[ A</span><span class="sxs-lookup"><span data-stu-id="63d69-715">ESC \[ A</span></span> | <span data-ttu-id="63d69-716">ESC O A</span><span class="sxs-lookup"><span data-stu-id="63d69-716">ESC O A</span></span> |
| <span data-ttu-id="63d69-717">Flèche Bas</span><span class="sxs-lookup"><span data-stu-id="63d69-717">Down Arrow</span></span> | <span data-ttu-id="63d69-718">ESC \[ B</span><span class="sxs-lookup"><span data-stu-id="63d69-718">ESC \[ B</span></span> | <span data-ttu-id="63d69-719">ESC O B</span><span class="sxs-lookup"><span data-stu-id="63d69-719">ESC O B</span></span> |
| <span data-ttu-id="63d69-720">Flèche droite</span><span class="sxs-lookup"><span data-stu-id="63d69-720">Right Arrow</span></span> | <span data-ttu-id="63d69-721">ESC \[ C</span><span class="sxs-lookup"><span data-stu-id="63d69-721">ESC \[ C</span></span> | <span data-ttu-id="63d69-722">ESC O C</span><span class="sxs-lookup"><span data-stu-id="63d69-722">ESC O C</span></span> |
| <span data-ttu-id="63d69-723">Gauche</span><span class="sxs-lookup"><span data-stu-id="63d69-723">Left Arrow</span></span> | <span data-ttu-id="63d69-724">ESC \[ D</span><span class="sxs-lookup"><span data-stu-id="63d69-724">ESC \[ D</span></span> | <span data-ttu-id="63d69-725">ESC O D</span><span class="sxs-lookup"><span data-stu-id="63d69-725">ESC O D</span></span> |
| <span data-ttu-id="63d69-726">Accueil</span><span class="sxs-lookup"><span data-stu-id="63d69-726">Home</span></span> | <span data-ttu-id="63d69-727">ESC \[ H</span><span class="sxs-lookup"><span data-stu-id="63d69-727">ESC \[ H</span></span> | <span data-ttu-id="63d69-728">ESC O H</span><span class="sxs-lookup"><span data-stu-id="63d69-728">ESC O H</span></span> |
| <span data-ttu-id="63d69-729">End</span><span class="sxs-lookup"><span data-stu-id="63d69-729">End</span></span> | <span data-ttu-id="63d69-730">ESC \[ F</span><span class="sxs-lookup"><span data-stu-id="63d69-730">ESC \[ F</span></span> | <span data-ttu-id="63d69-731">ESC O F</span><span class="sxs-lookup"><span data-stu-id="63d69-731">ESC O F</span></span> |



<span data-ttu-id="63d69-732">En outre, si la touche CTRL est enfoncée avec l’une de ces touches, les séquences suivantes sont émises à la place, indépendamment du mode touches de direction :</span><span class="sxs-lookup"><span data-stu-id="63d69-732">Additionally, if Ctrl is pressed with any of these keys, the following sequences are emitted instead, regardless of the Cursor Keys Mode:</span></span>


| <span data-ttu-id="63d69-733">Clé</span><span class="sxs-lookup"><span data-stu-id="63d69-733">Key</span></span> | <span data-ttu-id="63d69-734">N’importe quel mode</span><span class="sxs-lookup"><span data-stu-id="63d69-734">Any Mode</span></span> |
|--------------------|----------------|
| <span data-ttu-id="63d69-735">Ctrl + flèche haut</span><span class="sxs-lookup"><span data-stu-id="63d69-735">Ctrl + Up Arrow</span></span> | <span data-ttu-id="63d69-736">ESC \[ 1 ; 5 A</span><span class="sxs-lookup"><span data-stu-id="63d69-736">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="63d69-737">Ctrl + flèche bas</span><span class="sxs-lookup"><span data-stu-id="63d69-737">Ctrl + Down Arrow</span></span> | <span data-ttu-id="63d69-738">ESC \[ 1 ; 5 B</span><span class="sxs-lookup"><span data-stu-id="63d69-738">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="63d69-739">Ctrl + flèche droite</span><span class="sxs-lookup"><span data-stu-id="63d69-739">Ctrl + Right Arrow</span></span> | <span data-ttu-id="63d69-740">ESC \[ 1 ; 5 C</span><span class="sxs-lookup"><span data-stu-id="63d69-740">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="63d69-741">Ctrl + flèche gauche</span><span class="sxs-lookup"><span data-stu-id="63d69-741">Ctrl + Left Arrow</span></span> | <span data-ttu-id="63d69-742">ESC \[ 1 ; 5 D</span><span class="sxs-lookup"><span data-stu-id="63d69-742">ESC \[ 1 ; 5 D</span></span> |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span data-ttu-id="63d69-743"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Touches de fonction et pavé numérique</span><span class="sxs-lookup"><span data-stu-id="63d69-743"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad & Function Keys</span></span>


| <span data-ttu-id="63d69-744">Clé</span><span class="sxs-lookup"><span data-stu-id="63d69-744">Key</span></span> | <span data-ttu-id="63d69-745">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-745">Sequence</span></span> |
|-----------|--------------|
| <span data-ttu-id="63d69-746">Retour arrière</span><span class="sxs-lookup"><span data-stu-id="63d69-746">Backspace</span></span> | <span data-ttu-id="63d69-747">0x7f (DEL)</span><span class="sxs-lookup"><span data-stu-id="63d69-747">0x7f (DEL)</span></span> |
| <span data-ttu-id="63d69-748">Suspendre</span><span class="sxs-lookup"><span data-stu-id="63d69-748">Pause</span></span> | <span data-ttu-id="63d69-749">0x1a (SUB)</span><span class="sxs-lookup"><span data-stu-id="63d69-749">0x1a (SUB)</span></span> |
| <span data-ttu-id="63d69-750">Caractère d'échappement</span><span class="sxs-lookup"><span data-stu-id="63d69-750">Escape</span></span> | <span data-ttu-id="63d69-751">0x1b (ESC)</span><span class="sxs-lookup"><span data-stu-id="63d69-751">0x1b (ESC)</span></span> |
| <span data-ttu-id="63d69-752">Insérer</span><span class="sxs-lookup"><span data-stu-id="63d69-752">Insert</span></span> | <span data-ttu-id="63d69-753">ESC \[ 2 ~</span><span class="sxs-lookup"><span data-stu-id="63d69-753">ESC \[ 2 ~</span></span> |
| <span data-ttu-id="63d69-754">Supprimer</span><span class="sxs-lookup"><span data-stu-id="63d69-754">Delete</span></span> | <span data-ttu-id="63d69-755">ESC \[ 3 ~</span><span class="sxs-lookup"><span data-stu-id="63d69-755">ESC \[ 3 ~</span></span> |
| <span data-ttu-id="63d69-756">Page précédente</span><span class="sxs-lookup"><span data-stu-id="63d69-756">Page Up</span></span> | <span data-ttu-id="63d69-757">ESC \[ 5 ~</span><span class="sxs-lookup"><span data-stu-id="63d69-757">ESC \[ 5 ~</span></span> |
| <span data-ttu-id="63d69-758">Page suivante</span><span class="sxs-lookup"><span data-stu-id="63d69-758">Page Down</span></span> | <span data-ttu-id="63d69-759">ESC \[ 6 ~</span><span class="sxs-lookup"><span data-stu-id="63d69-759">ESC \[ 6 ~</span></span> |
| <span data-ttu-id="63d69-760">F1</span><span class="sxs-lookup"><span data-stu-id="63d69-760">F1</span></span> | <span data-ttu-id="63d69-761">ESC O P</span><span class="sxs-lookup"><span data-stu-id="63d69-761">ESC O P</span></span> |
| <span data-ttu-id="63d69-762">F2</span><span class="sxs-lookup"><span data-stu-id="63d69-762">F2</span></span> | <span data-ttu-id="63d69-763">ESC O Q</span><span class="sxs-lookup"><span data-stu-id="63d69-763">ESC O Q</span></span> |
| <span data-ttu-id="63d69-764">F3</span><span class="sxs-lookup"><span data-stu-id="63d69-764">F3</span></span> | <span data-ttu-id="63d69-765">ESC O R</span><span class="sxs-lookup"><span data-stu-id="63d69-765">ESC O R</span></span> |
| <span data-ttu-id="63d69-766">F4</span><span class="sxs-lookup"><span data-stu-id="63d69-766">F4</span></span> | <span data-ttu-id="63d69-767">ESC O S</span><span class="sxs-lookup"><span data-stu-id="63d69-767">ESC O S</span></span> |
| <span data-ttu-id="63d69-768">F5</span><span class="sxs-lookup"><span data-stu-id="63d69-768">F5</span></span> | <span data-ttu-id="63d69-769">ESC \[ 1 5 ~</span><span class="sxs-lookup"><span data-stu-id="63d69-769">ESC \[ 1 5 ~</span></span> |
| <span data-ttu-id="63d69-770">F6</span><span class="sxs-lookup"><span data-stu-id="63d69-770">F6</span></span> | <span data-ttu-id="63d69-771">ESC \[ 1 7 ~</span><span class="sxs-lookup"><span data-stu-id="63d69-771">ESC \[ 1 7 ~</span></span> |
| <span data-ttu-id="63d69-772">F7</span><span class="sxs-lookup"><span data-stu-id="63d69-772">F7</span></span> | <span data-ttu-id="63d69-773">ESC \[ 1 8 ~</span><span class="sxs-lookup"><span data-stu-id="63d69-773">ESC \[ 1 8 ~</span></span> |
| <span data-ttu-id="63d69-774">F8</span><span class="sxs-lookup"><span data-stu-id="63d69-774">F8</span></span> | <span data-ttu-id="63d69-775">ESC \[ 1 9 ~</span><span class="sxs-lookup"><span data-stu-id="63d69-775">ESC \[ 1 9 ~</span></span> |
| <span data-ttu-id="63d69-776">F9</span><span class="sxs-lookup"><span data-stu-id="63d69-776">F9</span></span> | <span data-ttu-id="63d69-777">ESC \[ 2 0 ~</span><span class="sxs-lookup"><span data-stu-id="63d69-777">ESC \[ 2 0 ~</span></span> |
| <span data-ttu-id="63d69-778">F10</span><span class="sxs-lookup"><span data-stu-id="63d69-778">F10</span></span> | <span data-ttu-id="63d69-779">ESC \[ 2 1 ~</span><span class="sxs-lookup"><span data-stu-id="63d69-779">ESC \[ 2 1 ~</span></span> |
| <span data-ttu-id="63d69-780">F11</span><span class="sxs-lookup"><span data-stu-id="63d69-780">F11</span></span> | <span data-ttu-id="63d69-781">ESC \[ 2 3 ~</span><span class="sxs-lookup"><span data-stu-id="63d69-781">ESC \[ 2 3 ~</span></span> |
| <span data-ttu-id="63d69-782">F12</span><span class="sxs-lookup"><span data-stu-id="63d69-782">F12</span></span> | <span data-ttu-id="63d69-783">ESC \[ 2 4 ~</span><span class="sxs-lookup"><span data-stu-id="63d69-783">ESC \[ 2 4 ~</span></span> |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span data-ttu-id="63d69-784"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modificateurs</span><span class="sxs-lookup"><span data-stu-id="63d69-784"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifiers</span></span>

<span data-ttu-id="63d69-785">La touche Alt est traitée en préfixant la séquence par un caractère d’échappement : ESC &lt;c&gt; où &lt;c&gt; est le caractère passé par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="63d69-785">Alt is treated by prefixing the sequence with an escape: ESC &lt;c&gt; where &lt;c&gt; is the character passed by the operating system.</span></span> <span data-ttu-id="63d69-786">La séquence Alt+Ctrl est gérée de la même façon, à la différence que le système d’exploitation aura préalablement décalé la touche &lt;c&gt; vers le caractère de contrôle approprié qui sera relayé à l’application.</span><span class="sxs-lookup"><span data-stu-id="63d69-786">Alt+Ctrl is handled the same way except that the operating system will have pre-shifted the &lt;c&gt; key to the appropriate control character which will be relayed to the application.</span></span>

<span data-ttu-id="63d69-787">La touche Ctrl est généralement transmise telle qu’elle est reçue du système.</span><span class="sxs-lookup"><span data-stu-id="63d69-787">Ctrl is generally passed through exactly as received from the system.</span></span> <span data-ttu-id="63d69-788">Il s’agit généralement d’un caractère unique baissé dans l’espace réservé de caractères de contrôle (0x0-0x1f).</span><span class="sxs-lookup"><span data-stu-id="63d69-788">This is typically a single character shifted down into the control character reserved space (0x0-0x1f).</span></span> <span data-ttu-id="63d69-789">Par exemple, Ctrl+@ (0x40) devient NUL (0x00), Ctrl+\[ (0x5b) devient ESC (0x1b), etc. Quelques combinaisons de touches impliquant Ctrl sont traitées de façon spéciale selon le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="63d69-789">For example, Ctrl+@ (0x40) becomes NUL (0x00), Ctrl+\[ (0x5b) becomes ESC (0x1b), etc. A few Ctrl key combinations are treated specially according to the following table:</span></span>


| <span data-ttu-id="63d69-790">Clé</span><span class="sxs-lookup"><span data-stu-id="63d69-790">Key</span></span> | <span data-ttu-id="63d69-791">Séquence</span><span class="sxs-lookup"><span data-stu-id="63d69-791">Sequence</span></span> |
|--------------------|----------------|
| <span data-ttu-id="63d69-792">Ctrl + espace</span><span class="sxs-lookup"><span data-stu-id="63d69-792">Ctrl + Space</span></span> | <span data-ttu-id="63d69-793">0x00 (NUL)</span><span class="sxs-lookup"><span data-stu-id="63d69-793">0x00 (NUL)</span></span> |
| <span data-ttu-id="63d69-794">Ctrl + flèche haut</span><span class="sxs-lookup"><span data-stu-id="63d69-794">Ctrl + Up Arrow</span></span> | <span data-ttu-id="63d69-795">ESC \[ 1 ; 5 A</span><span class="sxs-lookup"><span data-stu-id="63d69-795">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="63d69-796">Ctrl + flèche bas</span><span class="sxs-lookup"><span data-stu-id="63d69-796">Ctrl + Down Arrow</span></span> | <span data-ttu-id="63d69-797">ESC \[ 1 ; 5 B</span><span class="sxs-lookup"><span data-stu-id="63d69-797">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="63d69-798">Ctrl + flèche droite</span><span class="sxs-lookup"><span data-stu-id="63d69-798">Ctrl + Right Arrow</span></span> | <span data-ttu-id="63d69-799">ESC \[ 1 ; 5 C</span><span class="sxs-lookup"><span data-stu-id="63d69-799">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="63d69-800">Ctrl + flèche gauche</span><span class="sxs-lookup"><span data-stu-id="63d69-800">Ctrl + Left Arrow</span></span> | <span data-ttu-id="63d69-801">ESC \[ 1 ; 5 D</span><span class="sxs-lookup"><span data-stu-id="63d69-801">ESC \[ 1 ; 5 D</span></span> |



> [!NOTE]
><span data-ttu-id="63d69-802"><kbd>Ctrl</kbd> gauche + <kbd>Alt</kbd> droite est traité comme AltGr.</span><span class="sxs-lookup"><span data-stu-id="63d69-802">Left <kbd>Ctrl</kbd> + Right <kbd>Alt</kbd> is treated as AltGr.</span></span> <span data-ttu-id="63d69-803">Quand ils apparaissent ensemble, ils sont supprimés et la valeur Unicode du caractère présenté par le système est transmise à la cible.</span><span class="sxs-lookup"><span data-stu-id="63d69-803">When both are seen together, they will be stripped and the Unicode value of the character presented by the system will be passed into the target.</span></span> <span data-ttu-id="63d69-804">Le système pré-convertit les valeurs AltGr en fonction des paramètres d’entrée système actuels.</span><span class="sxs-lookup"><span data-stu-id="63d69-804">The system will pre-translate AltGr values according to the current system input settings.</span></span>



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span data-ttu-id="63d69-805"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Exemples</span><span class="sxs-lookup"><span data-stu-id="63d69-805"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Samples</span></span>


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span data-ttu-id="63d69-806"><span id="example"></span><span id="EXAMPLE"></span>Exemple de séquences de terminal SGR</span><span class="sxs-lookup"><span data-stu-id="63d69-806"><span id="example"></span><span id="EXAMPLE"></span>Example of SGR terminal sequences</span></span>

<span data-ttu-id="63d69-807">Le code suivant fournit plusieurs exemples de mise en forme de texte.</span><span class="sxs-lookup"><span data-stu-id="63d69-807">The following code provides several examples of text formatting.</span></span>

```C
#include <stdio.h>
#include <wchar.h>
#include <windows.h>

int main()
{
 // Set output mode to handle virtual terminal sequences
 HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
 if (hOut == INVALID_HANDLE_VALUE)
 {
 return GetLastError();
 }

 DWORD dwMode = 0;
 if (!GetConsoleMode(hOut, &dwMode))
 {
 return GetLastError();
 }

 dwMode |= ENABLE_VIRTUAL_TERMINAL_PROCESSING;
 if (!SetConsoleMode(hOut, dwMode))
 {
 return GetLastError();
 }

 // Try some Set Graphics Rendition (SGR) terminal escape sequences
 wprintf(L"\x1b[31mThis text has a red foreground using SGR.31.\r\n");
 wprintf(L"\x1b[1mThis text has a bright (bold) red foreground using SGR.1 to affect the previous color setting.\r\n");
 wprintf(L"\x1b[mThis text has returned to default colors using SGR.0 implicitly.\r\n");
 wprintf(L"\x1b[34;46mThis text shows the foreground and background change at the same time.\r\n");
 wprintf(L"\x1b[0mThis text has returned to default colors using SGR.0 explicitly.\r\n");
 wprintf(L"\x1b[31;32;33;34;35;36;101;102;103;104;105;106;107mThis text attempts to apply many colors in the same command. Note the colors are applied from left to right so only the right-most option of foreground cyan (SGR.36) and background bright white (SGR.107) is effective.\r\n");
 wprintf(L"\x1b[39mThis text has restored the foreground color only.\r\n");
 wprintf(L"\x1b[49mThis text has restored the background color only.\r\n");

 return 0;
}
```

> [!NOTE]
><span data-ttu-id="63d69-808">Dans l’exemple précédent, la chaîne « `\x1b[31m` » correspond à l’implémentation de **ESC \[ &lt;n&gt; m** où &lt;n&gt; a pour valeur 31.</span><span class="sxs-lookup"><span data-stu-id="63d69-808">In the previous example, the string '`\x1b[31m`' is the implementation of **ESC \[ &lt;n&gt; m** with &lt;n&gt; being 31.</span></span>



<span data-ttu-id="63d69-809">Le graphique suivant montre la sortie de l’exemple de code précédent.</span><span class="sxs-lookup"><span data-stu-id="63d69-809">The following graphic shows the output of the previous code example.</span></span>

![Sortie de la console illustrant l’utilisation de la commande sgr](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span data-ttu-id="63d69-811"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Exemple d’activation de traitement de terminal virtuel</span><span class="sxs-lookup"><span data-stu-id="63d69-811"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Example of Enabling Virtual Terminal Processing</span></span>

<span data-ttu-id="63d69-812">Le code suivant fournit un exemple de la méthode recommandée pour activer le traitement de terminal virtuel pour une application.</span><span class="sxs-lookup"><span data-stu-id="63d69-812">The following code provides an example of the recommended way to enable virtual terminal processing for an application.</span></span> <span data-ttu-id="63d69-813">L’exemple vise à illustrer les points suivants :</span><span class="sxs-lookup"><span data-stu-id="63d69-813">The intent of the sample is to demonstrate:</span></span>

1. <span data-ttu-id="63d69-814">Le mode existant doit toujours être récupéré par le biais de GetConsoleMode et analysé avant d’être défini avec SetConsoleMode.</span><span class="sxs-lookup"><span data-stu-id="63d69-814">The existing mode should always be retrieved via GetConsoleMode and analyzed before being set with SetConsoleMode.</span></span>

2. <span data-ttu-id="63d69-815">Le fait de vérifier si SetConsoleMode retourne `0` et GetLastError retourne STATUS\_INVALID\_PARAMETER est le mécanisme actuel pour déterminer si l’exécution a lieu sur un système de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="63d69-815">Checking whether SetConsoleMode returns `0` and GetLastError returns STATUS\_INVALID\_PARAMETER is the current mechanism to determine when running on a down-level system.</span></span> <span data-ttu-id="63d69-816">Une application qui reçoit STATUS\_INVALID\_PARAMETER avec l’un des nouveaux indicateurs de mode de console dans le champ de bit doit progressivement dégrader le comportement, puis réessayer.</span><span class="sxs-lookup"><span data-stu-id="63d69-816">An application receiving STATUS\_INVALID\_PARAMETER with one of the newer console mode flags in the bit field should gracefully degrade behavior and try again.</span></span>

```C
#include <stdio.h>
#include <wchar.h>
#include <windows.h>

int main()
{
 // Set output mode to handle virtual terminal sequences
 HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
 if (hOut == INVALID_HANDLE_VALUE)
 {
 return false;
 }
 HANDLE hIn = GetStdHandle(STD_INPUT_HANDLE);
 if (hIn == INVALID_HANDLE_VALUE)
 {
 return false;
 }

 DWORD dwOriginalOutMode = 0;
 DWORD dwOriginalInMode = 0;
 if (!GetConsoleMode(hOut, &dwOriginalOutMode))
 {
 return false;
 }
 if (!GetConsoleMode(hIn, &dwOriginalInMode))
 {
 return false;
 }

 DWORD dwRequestedOutModes = ENABLE_VIRTUAL_TERMINAL_PROCESSING | DISABLE_NEWLINE_AUTO_RETURN;
 DWORD dwRequestedInModes = ENABLE_VIRTUAL_TERMINAL_INPUT;

 DWORD dwOutMode = dwOriginalOutMode | dwRequestedOutModes;
 if (!SetConsoleMode(hOut, dwOutMode))
 {
 // we failed to set both modes, try to step down mode gracefully.
 dwRequestedOutModes = ENABLE_VIRTUAL_TERMINAL_PROCESSING;
 dwOutMode = dwOriginalOutMode | dwRequestedOutModes;
 if (!SetConsoleMode(hOut, dwOutMode))
 {
 // Failed to set any VT mode, can't do anything here.
 return -1;
 }
 }

 DWORD dwInMode = dwOriginalInMode | ENABLE_VIRTUAL_TERMINAL_INPUT;
 if (!SetConsoleMode(hIn, dwInMode))
 {
 // Failed to set VT input mode, can't do anything here.
 return -1;
 }

 return 0;
}
```

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span data-ttu-id="63d69-817"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Exemple de certaines fonctionnalités de mise à jour anniversaire</span><span class="sxs-lookup"><span data-stu-id="63d69-817"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Example of Select Anniversary Update Features</span></span>

<span data-ttu-id="63d69-818">L’exemple suivant se veut un exemple plus robuste de code utilisant une variété de séquences d’échappement pour manipuler la mémoire tampon et met l’accent sur les fonctionnalités ajoutées dans la mise à jour anniversaire pour Windows 10.</span><span class="sxs-lookup"><span data-stu-id="63d69-818">The following example is intended to be a more robust example of code using a variety of escape sequences to manipulate the buffer, with an emphasis on the features added in the Anniversary Update for Windows 10.</span></span>

<span data-ttu-id="63d69-819">Cet exemple utilise la mémoire tampon d’écran secondaire et illustre la manipulation des taquets de tabulation, la définition des marges de défilement et le changement du jeu de caractères.</span><span class="sxs-lookup"><span data-stu-id="63d69-819">This example makes use of the alternate screen buffer, manipulating tab stops, setting scrolling margins, and changing the character set.</span></span>

```C
//
// Copyright (C) Microsoft. All rights reserved.
//
#define DEFINE_CONSOLEV2_PROPERTIES

// System headers
#include <windows.h>

// Standard library C-style
#include <wchar.h>
#include <stdlib.h>
#include <stdio.h>

#define ESC "\x1b"
#define CSI "\x1b["

bool EnableVTMode()
{
 // Set output mode to handle virtual terminal sequences
 HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
 if (hOut == INVALID_HANDLE_VALUE)
 {
 return false;
 }

 DWORD dwMode = 0;
 if (!GetConsoleMode(hOut, &dwMode))
 {
 return false;
 }

 dwMode |= ENABLE_VIRTUAL_TERMINAL_PROCESSING;
 if (!SetConsoleMode(hOut, dwMode))
 {
 return false;
 }
 return true;
}

void PrintVerticalBorder()
{
 printf(ESC "(0"); // Enter Line drawing mode
 printf(CSI "104;93m"); // bright yellow on bright blue
 printf("x"); // in line drawing mode, \x78 -> \u2502 "Vertical Bar"
 printf(CSI "0m"); // restore color
 printf(ESC "(B"); // exit line drawing mode
}

void PrintHorizontalBorder(COORD const Size, bool fIsTop)
{
 printf(ESC "(0"); // Enter Line drawing mode
 printf(CSI "104;93m"); // Make the border bright yellow on bright blue
 printf(fIsTop? "l" : "m"); // print left corner 

 for (int i = 1; i < Size.X - 1; i++) 
 printf("q"); // in line drawing mode, \x71 -> \u2500 "HORIZONTAL SCAN LINE-5"

 printf(fIsTop? "k" : "j"); // print right corner
 printf(CSI "0m");
 printf(ESC "(B"); // exit line drawing mode
}

void PrintStatusLine(char* const pszMessage, COORD const Size)
{
 printf(CSI "%d;1H", Size.Y);
 printf(CSI "K"); // clear the line
 printf(pszMessage); 
}

int __cdecl wmain(int argc, WCHAR* argv[])
{ 
 argc; // unused
 argv; // unused
 //First, enable VT mode
 bool fSuccess = EnableVTMode();
 if (!fSuccess)
 {
 printf("Unable to enter VT processing mode. Quitting.\n");
 return -1;
 }
 HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
 if (hOut == INVALID_HANDLE_VALUE)
 {
 printf("Couldn't get the console handle. Quitting.\n");
 return -1;
 }

 CONSOLE_SCREEN_BUFFER_INFO ScreenBufferInfo;
 GetConsoleScreenBufferInfo(hOut, &ScreenBufferInfo);
 COORD Size;
 Size.X = ScreenBufferInfo.srWindow.Right - ScreenBufferInfo.srWindow.Left + 1;
 Size.Y = ScreenBufferInfo.srWindow.Bottom - ScreenBufferInfo.srWindow.Top + 1;

 // Enter the alternate buffer
 printf(CSI "?1049h");

 // Clear screen, tab stops, set, stop at columns 16, 32
 printf(CSI "1;1H");
 printf(CSI "2J"); // Clear screen

 int iNumTabStops = 4; // (0, 20, 40, width)
 printf(CSI "3g"); // clear all tab stops
 printf(CSI "1;20H"); // Move to column 20
 printf(ESC "H"); // set a tab stop

 printf(CSI "1;40H"); // Move to column 40
 printf(ESC "H"); // set a tab stop

 // Set scrolling margins to 3, h-2
 printf(CSI "3;%dr", Size.Y-2);
 int iNumLines = Size.Y - 4;

 printf(CSI "1;1H");
 printf(CSI "102;30m");
 printf("Windows 10 Anniversary Update - VT Example"); 
 printf(CSI "0m");

 // Print a top border - Yellow
 printf(CSI "2;1H");
 PrintHorizontalBorder(Size, true);

 // // Print a bottom border
 printf(CSI "%d;1H", Size.Y-1);
 PrintHorizontalBorder(Size, false);

 wchar_t wch;

 // draw columns
 printf(CSI "3;1H"); 
 int line = 0;
 for (line = 0; line < iNumLines * iNumTabStops; line++)
 {
 PrintVerticalBorder();
 if (line + 1 != iNumLines * iNumTabStops) // don't advance to next line if this is the last line
 printf("\t"); // advance to next tab stop

 }

 PrintStatusLine("Press any key to see text printed between tab stops.", Size);
 wch = _getwch();

 // Fill columns with output
 printf(CSI "3;1H"); 
 for (line = 0; line < iNumLines; line++)
 {
 int tab = 0;
 for (tab = 0; tab < iNumTabStops-1; tab++)
 {
 PrintVerticalBorder();
 printf("line=%d", line);
 printf("\t"); // advance to next tab stop
 }
 PrintVerticalBorder();// print border at right side
 if (line+1 != iNumLines)
 printf("\t"); // advance to next tab stop, (on the next line)
 }

 PrintStatusLine("Press any key to demonstrate scroll margins", Size);
 wch = _getwch();

 printf(CSI "3;1H"); 
 for (line = 0; line < iNumLines * 2; line++)
 {
 printf(CSI "K"); // clear the line
 int tab = 0;
 for (tab = 0; tab < iNumTabStops-1; tab++)
 {
 PrintVerticalBorder();
 printf("line=%d", line);
 printf("\t"); // advance to next tab stop
 }
 PrintVerticalBorder(); // print border at right side
 if (line+1 != iNumLines * 2)
 {
 printf("\n"); //Advance to next line. If we're at the bottom of the margins, the text will scroll.
 printf("\r"); //return to first col in buffer
 }
 }

 PrintStatusLine("Press any key to exit", Size);
 wch = _getwch();

 // Exit the alternate buffer
 printf(CSI "?1049l");

}
```








