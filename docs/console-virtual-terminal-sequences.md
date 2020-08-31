---
title: Séquences de terminaux virtuels de la console
description: Les séquences de terminaux virtuels sont des séquences de caractères de contrôle qui peuvent contrôler le mouvement du curseur, le mode couleur/police et d’autres opérations lors de l’écriture dans le flux de sortie.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: A5C553A5-FD84-4D16-A814-EDB3B8699B91
ms.openlocfilehash: d05aa6f44cc97478d4eb2aba25587b2506e84a98
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059253"
---
# <a name="console-virtual-terminal-sequences"></a><span data-ttu-id="de10e-104">Séquences de terminaux virtuels de la console</span><span class="sxs-lookup"><span data-stu-id="de10e-104">Console Virtual Terminal Sequences</span></span>


<span data-ttu-id="de10e-105">Les séquences de terminaux virtuels sont des séquences de caractères de contrôle qui peuvent contrôler le mouvement du curseur, le mode couleur/police et d’autres opérations lors de l’écriture dans le flux de sortie.</span><span class="sxs-lookup"><span data-stu-id="de10e-105">Virtual terminal sequences are control character sequences that can control cursor movement, color/font mode, and other operations when written to the output stream.</span></span> <span data-ttu-id="de10e-106">Les séquences peuvent également être reçues sur le flux d’entrée en réponse à une séquence d’informations de requête de flux de sortie ou en tant qu’encodage d’entrée d’utilisateur lorsque le mode approprié est défini.</span><span class="sxs-lookup"><span data-stu-id="de10e-106">Sequences may also be received on the input stream in response to an output stream query information sequence or as an encoding of user input when the appropriate mode is set.</span></span>

<span data-ttu-id="de10e-107">Vous pouvez utiliser les fonctions [**GetConsoleMode**](getconsolemode.md) et [**SetConsoleMode**](setconsolemode.md) pour configurer ce comportement.</span><span class="sxs-lookup"><span data-stu-id="de10e-107">You can use [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions to configure this behavior.</span></span> <span data-ttu-id="de10e-108">Vous trouverez un exemple de la méthode suggérée pour activer les comportements des terminaux virtuels à la fin de ce document.</span><span class="sxs-lookup"><span data-stu-id="de10e-108">A sample of the suggested way to enable virtual terminal behaviors is included at the end of this document.</span></span>

<span data-ttu-id="de10e-109">Le comportement des séquences suivantes est basé sur les technologies d’émulateur de terminal VT100 et dérivées, le plus spécifiquement l’émulateur de terminal xterm.</span><span class="sxs-lookup"><span data-stu-id="de10e-109">The behavior of the following sequences is based on the VT100 and derived terminal emulator technologies, most specifically the xterm terminal emulator.</span></span> <span data-ttu-id="de10e-110">Vous trouverez plus d’informations sur les séquences de terminaux à l’adresse <http://vt100.net> et à <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html> .</span><span class="sxs-lookup"><span data-stu-id="de10e-110">More information about terminal sequences can be found at <http://vt100.net> and at <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span></span>

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span data-ttu-id="de10e-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Séquences de sortie</span><span class="sxs-lookup"><span data-stu-id="de10e-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Output Sequences</span></span>


<span data-ttu-id="de10e-112">Les séquences de terminaux suivantes sont interceptées par l’hôte de la console lorsqu’elles sont écrites dans le flux de sortie, si l’indicateur activer le \_ \_ \_ traitement des terminaux virtuels est défini sur le descripteur de la mémoire tampon d’écran à l’aide de la fonction [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="de10e-112">The following terminal sequences are intercepted by the console host when written into the output stream, if the ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING flag is set on the screen buffer handle using the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="de10e-113">Notez que l’indicateur désactiver le \_ retour automatique à la ligne \_ \_ peut également être utile pour émuler la position du curseur et le comportement du défilement des autres émulateurs de terminal en ce qui concerne les caractères écrits dans la dernière colonne de n’importe quelle ligne.</span><span class="sxs-lookup"><span data-stu-id="de10e-113">Note that the DISABLE\_NEWLINE\_AUTO\_RETURN flag may also be useful in emulating the cursor positioning and scrolling behavior of other terminal emulators in relation to characters written to the final column in any row.</span></span>

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span data-ttu-id="de10e-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Positionnement de curseur simple</span><span class="sxs-lookup"><span data-stu-id="de10e-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Simple Cursor Positioning</span></span>


<span data-ttu-id="de10e-115">Dans toutes les descriptions suivantes, ESC est toujours la valeur hexadécimale 0x1B.</span><span class="sxs-lookup"><span data-stu-id="de10e-115">In all of the following descriptions, ESC is always the hexadecimal value 0x1B.</span></span> <span data-ttu-id="de10e-116">Aucun espace ne doit être inclus dans les séquences de terminal.</span><span class="sxs-lookup"><span data-stu-id="de10e-116">No spaces are to be included in terminal sequences.</span></span> <span data-ttu-id="de10e-117">Pour obtenir un exemple de l’utilisation de ces séquences dans la pratique, consultez l' [exemple](#example) à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="de10e-117">For an example of how these sequences are used in practice, please see the [example](#example) at the end of this topic.</span></span>

<span data-ttu-id="de10e-118">Le tableau suivant décrit les séquences d’échappement simples avec une seule commande d’action directement après le caractère ESC.</span><span class="sxs-lookup"><span data-stu-id="de10e-118">The following table describes simple escape sequences with a single action command directly after the ESC character.</span></span> <span data-ttu-id="de10e-119">Ces séquences n’ont pas de paramètres et prennent effet immédiatement.</span><span class="sxs-lookup"><span data-stu-id="de10e-119">These sequences have no parameters and take effect immediately.</span></span>

<span data-ttu-id="de10e-120">Toutes les commandes de ce tableau sont généralement équivalentes à l’appel de l’API de la console [**SetConsoleCursorPosition**](setconsolecursorposition.md) pour placer le curseur.</span><span class="sxs-lookup"><span data-stu-id="de10e-120">All commands in this table are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API to place the cursor.</span></span>

<span data-ttu-id="de10e-121">Le déplacement du curseur est limité par la fenêtre d’affichage actuelle dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="de10e-121">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="de10e-122">Le défilement (si disponible) ne se produit pas.</span><span class="sxs-lookup"><span data-stu-id="de10e-122">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="de10e-123">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-123">Sequence</span></span> | <span data-ttu-id="de10e-124">Pratique</span><span class="sxs-lookup"><span data-stu-id="de10e-124">Shorthand</span></span> | <span data-ttu-id="de10e-125">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-125">Behavior</span></span>                                                                                                                                      |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="de10e-126">ÉCHAP A</span><span class="sxs-lookup"><span data-stu-id="de10e-126">ESC A</span></span>    | <span data-ttu-id="de10e-127">CUU</span><span class="sxs-lookup"><span data-stu-id="de10e-127">CUU</span></span>       | <span data-ttu-id="de10e-128">Curseur vers le haut de 1</span><span class="sxs-lookup"><span data-stu-id="de10e-128">Cursor Up by 1</span></span>                                                                                                                                |
| <span data-ttu-id="de10e-129">ESC B</span><span class="sxs-lookup"><span data-stu-id="de10e-129">ESC B</span></span>    | <span data-ttu-id="de10e-130">CUD</span><span class="sxs-lookup"><span data-stu-id="de10e-130">CUD</span></span>       | <span data-ttu-id="de10e-131">Curseur en dessous de 1</span><span class="sxs-lookup"><span data-stu-id="de10e-131">Cursor Down by 1</span></span>                                                                                                                              |
| <span data-ttu-id="de10e-132">ESC C</span><span class="sxs-lookup"><span data-stu-id="de10e-132">ESC C</span></span>    | <span data-ttu-id="de10e-133">CUF</span><span class="sxs-lookup"><span data-stu-id="de10e-133">CUF</span></span>       | <span data-ttu-id="de10e-134">Curseur vers l’avant (à droite) de 1</span><span class="sxs-lookup"><span data-stu-id="de10e-134">Cursor Forward (Right) by 1</span></span>                                                                                                                   |
| <span data-ttu-id="de10e-135">ECHAP D</span><span class="sxs-lookup"><span data-stu-id="de10e-135">ESC D</span></span>    | <span data-ttu-id="de10e-136">CUB</span><span class="sxs-lookup"><span data-stu-id="de10e-136">CUB</span></span>       | <span data-ttu-id="de10e-137">Curseur vers l’arrière (à gauche) de 1</span><span class="sxs-lookup"><span data-stu-id="de10e-137">Cursor Backward (Left) by 1</span></span>                                                                                                                   |
| <span data-ttu-id="de10e-138">ESC M</span><span class="sxs-lookup"><span data-stu-id="de10e-138">ESC M</span></span>    | <span data-ttu-id="de10e-139">Instance réservée</span><span class="sxs-lookup"><span data-stu-id="de10e-139">RI</span></span>        | <span data-ttu-id="de10e-140">Inverser l’index : effectue l’opération inverse de \\ n, déplace le curseur d’une ligne vers le haut, conserve la position horizontale, fait défiler le tampon si nécessaire.\*</span><span class="sxs-lookup"><span data-stu-id="de10e-140">Reverse Index – Performs the reverse operation of \\n, moves cursor up one line, maintains horizontal position, scrolls buffer if necessary\*</span></span> |
| <span data-ttu-id="de10e-141">ESC 7</span><span class="sxs-lookup"><span data-stu-id="de10e-141">ESC 7</span></span>    | <span data-ttu-id="de10e-142">DECSC</span><span class="sxs-lookup"><span data-stu-id="de10e-142">DECSC</span></span>     | <span data-ttu-id="de10e-143">Enregistrer la position du curseur en mémoire\*\*</span><span class="sxs-lookup"><span data-stu-id="de10e-143">Save Cursor Position in Memory\*\*</span></span>                                                                                                            |
| <span data-ttu-id="de10e-144">ESC 8</span><span class="sxs-lookup"><span data-stu-id="de10e-144">ESC 8</span></span>    | <span data-ttu-id="de10e-145">DECSR</span><span class="sxs-lookup"><span data-stu-id="de10e-145">DECSR</span></span>     | <span data-ttu-id="de10e-146">Restaurer la position du curseur à partir de la mémoire\*\*</span><span class="sxs-lookup"><span data-stu-id="de10e-146">Restore Cursor Position from Memory\*\*</span></span>                                                                                                       |



<span data-ttu-id="de10e-147">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="de10e-147">**Note**</span></span>  
<span data-ttu-id="de10e-148">\* Si des marges de défilement sont définies, l’RI à l’intérieur des marges défile uniquement le contenu des marges et laisse la fenêtre d’affichage inchangée.</span><span class="sxs-lookup"><span data-stu-id="de10e-148">\* If there are scroll margins set, RI inside the margins will scroll only the contents of the margins, and leave the viewport unchanged.</span></span> <span data-ttu-id="de10e-149">(Voir les marges de défilement)</span><span class="sxs-lookup"><span data-stu-id="de10e-149">(See Scrolling Margins)</span></span>

<span data-ttu-id="de10e-150">\*\*Aucune valeur n’est enregistrée en mémoire tant que la première utilisation de la commande Save n’est pas utilisée.</span><span class="sxs-lookup"><span data-stu-id="de10e-150">\*\*There will be no value saved in memory until the first use of the save command.</span></span> <span data-ttu-id="de10e-151">La seule façon d’accéder à la valeur enregistrée est la commande Restore.</span><span class="sxs-lookup"><span data-stu-id="de10e-151">The only way to access the saved value is with the restore command.</span></span>



## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span data-ttu-id="de10e-152"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Positionnement du curseur</span><span class="sxs-lookup"><span data-stu-id="de10e-152"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursor Positioning</span></span>


<span data-ttu-id="de10e-153">Les tableaux suivants englobent les séquences de types de séquences de contrôle (CSI).</span><span class="sxs-lookup"><span data-stu-id="de10e-153">The following tables encompass Control Sequence Introducer (CSI) type sequences.</span></span> <span data-ttu-id="de10e-154">Toutes les séquences CSI commencent par ESC (0x1B) suivies de \[ (crochet gauche, 0x5B) et peuvent contenir des paramètres de longueur variable pour spécifier plus d’informations pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="de10e-154">All CSI sequences start with ESC (0x1B) followed by \[ (left bracket, 0x5B) and may contain parameters of variable length to specify more information for each operation.</span></span> <span data-ttu-id="de10e-155">Ce sera représenté par le raccourci &lt; n &gt; .</span><span class="sxs-lookup"><span data-stu-id="de10e-155">This will be represented by the shorthand &lt;n&gt;.</span></span> <span data-ttu-id="de10e-156">Chaque tableau ci-dessous est regroupé par fonctionnalité avec les notes ci-dessous de chaque tableau expliquant le fonctionnement du groupe.</span><span class="sxs-lookup"><span data-stu-id="de10e-156">Each table below is grouped by functionality with notes below each table explaining how the group works.</span></span>

<span data-ttu-id="de10e-157">Pour tous les paramètres, les règles suivantes s’appliquent, sauf indication contraire :</span><span class="sxs-lookup"><span data-stu-id="de10e-157">For all parameters, the following rules apply unless otherwise noted:</span></span>

- <span data-ttu-id="de10e-158">&lt;n &gt; représente la distance à déplacer et est un paramètre facultatif</span><span class="sxs-lookup"><span data-stu-id="de10e-158">&lt;n&gt; represents the distance to move and is an optional parameter</span></span>
- <span data-ttu-id="de10e-159">Si &lt; n &gt; est omis ou est égal à 0, il est traité comme un 1</span><span class="sxs-lookup"><span data-stu-id="de10e-159">If &lt;n&gt; is omitted or equals 0, it will be treated as a 1</span></span>
- <span data-ttu-id="de10e-160">&lt;n &gt; ne peut pas être supérieur à 32 767 (valeur minimale)</span><span class="sxs-lookup"><span data-stu-id="de10e-160">&lt;n&gt; cannot be larger than 32,767 (maximum short value)</span></span>
- <span data-ttu-id="de10e-161">&lt;n &gt; ne peut pas être négatif</span><span class="sxs-lookup"><span data-stu-id="de10e-161">&lt;n&gt; cannot be negative</span></span>

<span data-ttu-id="de10e-162">Toutes les commandes de cette section sont généralement équivalentes à l’appel de l’API de la console [**SetConsoleCursorPosition**](setconsolecursorposition.md) .</span><span class="sxs-lookup"><span data-stu-id="de10e-162">All commands in this section are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API.</span></span>

<span data-ttu-id="de10e-163">Le déplacement du curseur est limité par la fenêtre d’affichage actuelle dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="de10e-163">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="de10e-164">Le défilement (si disponible) ne se produit pas.</span><span class="sxs-lookup"><span data-stu-id="de10e-164">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="de10e-165">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-165">Sequence</span></span>                       | <span data-ttu-id="de10e-166">Code</span><span class="sxs-lookup"><span data-stu-id="de10e-166">Code</span></span>      | <span data-ttu-id="de10e-167">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-167">Description</span></span>                         | <span data-ttu-id="de10e-168">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-168">Behavior</span></span>                                                                                                                   |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="de10e-169">ECHAP \[ &lt; n &gt; A</span><span class="sxs-lookup"><span data-stu-id="de10e-169">ESC \[ &lt;n&gt; A</span></span>             | <span data-ttu-id="de10e-170">CUU</span><span class="sxs-lookup"><span data-stu-id="de10e-170">CUU</span></span>       | <span data-ttu-id="de10e-171">Curseur vers le haut</span><span class="sxs-lookup"><span data-stu-id="de10e-171">Cursor Up</span></span>                           | <span data-ttu-id="de10e-172">Curseur jusqu’à &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="de10e-172">Cursor up by &lt;n&gt;</span></span>                                                                                                     |
| <span data-ttu-id="de10e-173">ECHAP \[ &lt; n &gt; B</span><span class="sxs-lookup"><span data-stu-id="de10e-173">ESC \[ &lt;n&gt; B</span></span>             | <span data-ttu-id="de10e-174">CUD</span><span class="sxs-lookup"><span data-stu-id="de10e-174">CUD</span></span>       | <span data-ttu-id="de10e-175">Curseur en dessous</span><span class="sxs-lookup"><span data-stu-id="de10e-175">Cursor Down</span></span>                         | <span data-ttu-id="de10e-176">Curseur en dessous de &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="de10e-176">Cursor down by &lt;n&gt;</span></span>                                                                                                   |
| <span data-ttu-id="de10e-177">ECHAP \[ &lt; n &gt; C</span><span class="sxs-lookup"><span data-stu-id="de10e-177">ESC \[ &lt;n&gt; C</span></span>             | <span data-ttu-id="de10e-178">CUF</span><span class="sxs-lookup"><span data-stu-id="de10e-178">CUF</span></span>       | <span data-ttu-id="de10e-179">Curseur vers l’avant</span><span class="sxs-lookup"><span data-stu-id="de10e-179">Cursor Forward</span></span>                      | <span data-ttu-id="de10e-180">Curseur vers l’avant (à droite) de &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="de10e-180">Cursor forward (Right) by &lt;n&gt;</span></span>                                                                                        |
| <span data-ttu-id="de10e-181">ECHAP \[ &lt; n &gt; D</span><span class="sxs-lookup"><span data-stu-id="de10e-181">ESC \[ &lt;n&gt; D</span></span>             | <span data-ttu-id="de10e-182">CUB</span><span class="sxs-lookup"><span data-stu-id="de10e-182">CUB</span></span>       | <span data-ttu-id="de10e-183">Curseur vers l’arrière</span><span class="sxs-lookup"><span data-stu-id="de10e-183">Cursor Backward</span></span>                     | <span data-ttu-id="de10e-184">Curseur vers l’arrière (à gauche) de &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="de10e-184">Cursor backward (Left) by &lt;n&gt;</span></span>                                                                                        |
| <span data-ttu-id="de10e-185">ECHAP \[ &lt; n &gt; E</span><span class="sxs-lookup"><span data-stu-id="de10e-185">ESC \[ &lt;n&gt; E</span></span>             | <span data-ttu-id="de10e-186">CNL</span><span class="sxs-lookup"><span data-stu-id="de10e-186">CNL</span></span>       | <span data-ttu-id="de10e-187">Ligne suivante du curseur</span><span class="sxs-lookup"><span data-stu-id="de10e-187">Cursor Next Line</span></span>                    | <span data-ttu-id="de10e-188">Curseur vers le début du &lt; n &gt; ième trait dans la fenêtre d’affichage</span><span class="sxs-lookup"><span data-stu-id="de10e-188">Cursor down to beginning of &lt;n&gt;th line in the viewport</span></span>                                                               |
| <span data-ttu-id="de10e-189">ECHAP \[ &lt; n &gt; F</span><span class="sxs-lookup"><span data-stu-id="de10e-189">ESC \[ &lt;n&gt; F</span></span>             | <span data-ttu-id="de10e-190">PERSONNALISATION</span><span class="sxs-lookup"><span data-stu-id="de10e-190">CPL</span></span>       | <span data-ttu-id="de10e-191">Ligne précédente du curseur</span><span class="sxs-lookup"><span data-stu-id="de10e-191">Cursor Previous Line</span></span>                | <span data-ttu-id="de10e-192">Curseur jusqu’au début de &lt; &gt; la n ième ligne dans la fenêtre d’affichage</span><span class="sxs-lookup"><span data-stu-id="de10e-192">Cursor up to beginning of &lt;n&gt;th line in the viewport</span></span>                                                                 |
| <span data-ttu-id="de10e-193">ECHAP \[ &lt; n &gt; G</span><span class="sxs-lookup"><span data-stu-id="de10e-193">ESC \[ &lt;n&gt; G</span></span>             | <span data-ttu-id="de10e-194">CHA</span><span class="sxs-lookup"><span data-stu-id="de10e-194">CHA</span></span>       | <span data-ttu-id="de10e-195">Curseur horizontal absolu</span><span class="sxs-lookup"><span data-stu-id="de10e-195">Cursor Horizontal Absolute</span></span>          | <span data-ttu-id="de10e-196">Le curseur se déplace d’une position à une &lt; &gt; position horizontale dans la ligne active</span><span class="sxs-lookup"><span data-stu-id="de10e-196">Cursor moves to &lt;n&gt;th position horizontally in the current line</span></span>                                                      |
| <span data-ttu-id="de10e-197">ECHAP \[ &lt; n &gt; d</span><span class="sxs-lookup"><span data-stu-id="de10e-197">ESC \[ &lt;n&gt; d</span></span>             | <span data-ttu-id="de10e-198">VPA</span><span class="sxs-lookup"><span data-stu-id="de10e-198">VPA</span></span>       | <span data-ttu-id="de10e-199">Position de ligne verticale absolue</span><span class="sxs-lookup"><span data-stu-id="de10e-199">Vertical Line Position Absolute</span></span>     | <span data-ttu-id="de10e-200">Le curseur se déplace vers la &lt; n &gt; ième position verticale dans la colonne actuelle</span><span class="sxs-lookup"><span data-stu-id="de10e-200">Cursor moves to the &lt;n&gt;th position vertically in the current column</span></span>                                                  |
| <span data-ttu-id="de10e-201">ESC \[ &lt; y &gt; ; &lt; x &gt; H</span><span class="sxs-lookup"><span data-stu-id="de10e-201">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span></span> | <span data-ttu-id="de10e-202">FOOTBALL</span><span class="sxs-lookup"><span data-stu-id="de10e-202">CUP</span></span>       | <span data-ttu-id="de10e-203">Position du curseur</span><span class="sxs-lookup"><span data-stu-id="de10e-203">Cursor Position</span></span>                     | <span data-ttu-id="de10e-204">\*Le curseur est déplacé vers &lt; x &gt; ; &lt; &gt; coordonnée y dans la fenêtre d’affichage, où &lt; x &gt; est la colonne de la &lt; &gt; ligne y</span><span class="sxs-lookup"><span data-stu-id="de10e-204">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="de10e-205">ESC \[ &lt; y &gt; ; &lt; x &gt; f</span><span class="sxs-lookup"><span data-stu-id="de10e-205">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span></span> | <span data-ttu-id="de10e-206">HVP</span><span class="sxs-lookup"><span data-stu-id="de10e-206">HVP</span></span>       | <span data-ttu-id="de10e-207">Position verticale horizontale</span><span class="sxs-lookup"><span data-stu-id="de10e-207">Horizontal Vertical Position</span></span>        | <span data-ttu-id="de10e-208">\*Le curseur est déplacé vers &lt; x &gt; ; &lt; &gt; coordonnée y dans la fenêtre d’affichage, où &lt; x &gt; est la colonne de la &lt; &gt; ligne y</span><span class="sxs-lookup"><span data-stu-id="de10e-208">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="de10e-209">ESC \[ s</span><span class="sxs-lookup"><span data-stu-id="de10e-209">ESC \[ s</span></span>                       | <span data-ttu-id="de10e-210">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="de10e-210">ANSISYSSC</span></span> | <span data-ttu-id="de10e-211">Enregistrer le curseur – Ansi.sys l’émulation</span><span class="sxs-lookup"><span data-stu-id="de10e-211">Save Cursor – Ansi.sys emulation</span></span>    | <span data-ttu-id="de10e-212">\*\*Sans paramètre, effectue une opération enregistrer le curseur comme DECSC</span><span class="sxs-lookup"><span data-stu-id="de10e-212">\*\*With no parameters, performs a save cursor operation like DECSC</span></span>                                                        |
| <span data-ttu-id="de10e-213">ESC \[ u</span><span class="sxs-lookup"><span data-stu-id="de10e-213">ESC \[ u</span></span>                       | <span data-ttu-id="de10e-214">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="de10e-214">ANSISYSSC</span></span> | <span data-ttu-id="de10e-215">Curseur de restauration – émulation de Ansi.sys</span><span class="sxs-lookup"><span data-stu-id="de10e-215">Restore Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="de10e-216">\*\*Sans paramètre, effectue une opération de restauration de curseur comme DECRC</span><span class="sxs-lookup"><span data-stu-id="de10e-216">\*\*With no parameters, performs a restore cursor operation like DECRC</span></span>                                                     |



<span data-ttu-id="de10e-217">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="de10e-217">**Note**</span></span>  
<span data-ttu-id="de10e-218">\*&lt;&gt; &lt; les paramètres x et y &gt; ont les mêmes limitations que &lt; n &gt; ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="de10e-218">\*&lt;x&gt; and &lt;y&gt; parameters have the same limitations as &lt;n&gt; above.</span></span> <span data-ttu-id="de10e-219">Si &lt; x &gt; et &lt; y &gt; sont omis, ils sont définis sur 1 ; 1.</span><span class="sxs-lookup"><span data-stu-id="de10e-219">If &lt;x&gt; and &lt;y&gt; are omitted, they will be set to 1;1.</span></span>

<span data-ttu-id="de10e-220">\*\*ANSI.sys documentation historique se trouve dans <https://msdn.microsoft.com/library/cc722862.aspx> et est implémentée pour des raisons pratiques/de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="de10e-220">\*\*ANSI.sys historical documentation can be found at <https://msdn.microsoft.com/library/cc722862.aspx> and is implemented for convenience/compatibility.</span></span>



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span data-ttu-id="de10e-221"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Visibilité du curseur</span><span class="sxs-lookup"><span data-stu-id="de10e-221"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursor Visibility</span></span>


<span data-ttu-id="de10e-222">Les commandes suivantes contrôlent la visibilité du curseur et son état de clignotement.</span><span class="sxs-lookup"><span data-stu-id="de10e-222">The following commands control the visibility of the cursor and its blinking state.</span></span> <span data-ttu-id="de10e-223">Les séquences DECTCEM sont généralement équivalentes à l’appel de l’API de console [**SetConsoleCursorInfo**](setconsolecursorinfo.md) pour basculer la visibilité du curseur.</span><span class="sxs-lookup"><span data-stu-id="de10e-223">The DECTCEM sequences are generally equivalent to calling [**SetConsoleCursorInfo**](setconsolecursorinfo.md) console API to toggle cursor visibility.</span></span>


| <span data-ttu-id="de10e-224">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-224">Sequence</span></span>      | <span data-ttu-id="de10e-225">Code</span><span class="sxs-lookup"><span data-stu-id="de10e-225">Code</span></span>    | <span data-ttu-id="de10e-226">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-226">Description</span></span>                  | <span data-ttu-id="de10e-227">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-227">Behavior</span></span>                  |
|---------------|---------|------------------------------|---------------------------|
| <span data-ttu-id="de10e-228">Échap \[ ?</span><span class="sxs-lookup"><span data-stu-id="de10e-228">ESC \[ ?</span></span> <span data-ttu-id="de10e-229">12 h</span><span class="sxs-lookup"><span data-stu-id="de10e-229">12 h</span></span> | <span data-ttu-id="de10e-230">ATT160</span><span class="sxs-lookup"><span data-stu-id="de10e-230">ATT160</span></span>  | <span data-ttu-id="de10e-231">Curseur de texte activer le clignotement</span><span class="sxs-lookup"><span data-stu-id="de10e-231">Text Cursor Enable Blinking</span></span>  | <span data-ttu-id="de10e-232">Démarrer le clignotement du curseur</span><span class="sxs-lookup"><span data-stu-id="de10e-232">Start the cursor blinking</span></span> |
| <span data-ttu-id="de10e-233">Échap \[ ?</span><span class="sxs-lookup"><span data-stu-id="de10e-233">ESC \[ ?</span></span> <span data-ttu-id="de10e-234">12 l</span><span class="sxs-lookup"><span data-stu-id="de10e-234">12 l</span></span> | <span data-ttu-id="de10e-235">ATT160</span><span class="sxs-lookup"><span data-stu-id="de10e-235">ATT160</span></span>  | <span data-ttu-id="de10e-236">Curseur de texte désactiver le clignotement</span><span class="sxs-lookup"><span data-stu-id="de10e-236">Text Cursor Disable Blinking</span></span>  | <span data-ttu-id="de10e-237">Arrêter le clignotement du curseur</span><span class="sxs-lookup"><span data-stu-id="de10e-237">Stop blinking the cursor</span></span>  |
| <span data-ttu-id="de10e-238">Échap \[ ?</span><span class="sxs-lookup"><span data-stu-id="de10e-238">ESC \[ ?</span></span> <span data-ttu-id="de10e-239">25 h</span><span class="sxs-lookup"><span data-stu-id="de10e-239">25 h</span></span> | <span data-ttu-id="de10e-240">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="de10e-240">DECTCEM</span></span> | <span data-ttu-id="de10e-241">Affichage du mode d’activation du curseur de texte</span><span class="sxs-lookup"><span data-stu-id="de10e-241">Text Cursor Enable Mode Show</span></span> | <span data-ttu-id="de10e-242">Afficher le curseur</span><span class="sxs-lookup"><span data-stu-id="de10e-242">Show the cursor</span></span>           |
| <span data-ttu-id="de10e-243">Échap \[ ?</span><span class="sxs-lookup"><span data-stu-id="de10e-243">ESC \[ ?</span></span> <span data-ttu-id="de10e-244">25 l</span><span class="sxs-lookup"><span data-stu-id="de10e-244">25 l</span></span> | <span data-ttu-id="de10e-245">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="de10e-245">DECTCEM</span></span> | <span data-ttu-id="de10e-246">Masquage du mode d’activation du curseur de texte</span><span class="sxs-lookup"><span data-stu-id="de10e-246">Text Cursor Enable Mode Hide</span></span> | <span data-ttu-id="de10e-247">Masquer le curseur</span><span class="sxs-lookup"><span data-stu-id="de10e-247">Hide the cursor</span></span>           |



## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span data-ttu-id="de10e-248"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Positionnement de la fenêtre d’affichage</span><span class="sxs-lookup"><span data-stu-id="de10e-248"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Viewport Positioning</span></span>


<span data-ttu-id="de10e-249">Toutes les commandes de cette section sont généralement équivalentes à l’appel de l’API de console [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) pour déplacer le contenu de la mémoire tampon de la console.</span><span class="sxs-lookup"><span data-stu-id="de10e-249">All commands in this section are generally equivalent to calling [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console API to move the contents of the console buffer.</span></span>

<span data-ttu-id="de10e-250">**Attention**  Les noms de commande sont trompeurs.</span><span class="sxs-lookup"><span data-stu-id="de10e-250">**Caution**  The command names are misleading.</span></span> <span data-ttu-id="de10e-251">Le défilement fait référence à la direction vers laquelle le texte se déplace au cours de l’opération, et non à la façon dont la fenêtre d’affichage semble bouger.</span><span class="sxs-lookup"><span data-stu-id="de10e-251">Scroll refers to which direction the text moves during the operation, not which way the viewport would seem to move.</span></span>




| <span data-ttu-id="de10e-252">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-252">Sequence</span></span>           | <span data-ttu-id="de10e-253">Code</span><span class="sxs-lookup"><span data-stu-id="de10e-253">Code</span></span> | <span data-ttu-id="de10e-254">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-254">Description</span></span> | <span data-ttu-id="de10e-255">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-255">Behavior</span></span>                                                                                             |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="de10e-256">ECHAP \[ &lt; n &gt; S</span><span class="sxs-lookup"><span data-stu-id="de10e-256">ESC \[ &lt;n&gt; S</span></span> | <span data-ttu-id="de10e-257">Unités de diffusion en continu</span><span class="sxs-lookup"><span data-stu-id="de10e-257">SU</span></span>   | <span data-ttu-id="de10e-258">Faire défiler vers le haut</span><span class="sxs-lookup"><span data-stu-id="de10e-258">Scroll Up</span></span>   | <span data-ttu-id="de10e-259">Faire défiler le texte de &lt; n &gt; .</span><span class="sxs-lookup"><span data-stu-id="de10e-259">Scroll text up by &lt;n&gt;.</span></span> <span data-ttu-id="de10e-260">Également appelée panoramique, les nouvelles lignes remplissent à partir du bas de l’écran</span><span class="sxs-lookup"><span data-stu-id="de10e-260">Also known as pan down, new lines fill in from the bottom of the screen</span></span> |
| <span data-ttu-id="de10e-261">ECHAP \[ &lt; n &gt; T</span><span class="sxs-lookup"><span data-stu-id="de10e-261">ESC \[ &lt;n&gt; T</span></span> | <span data-ttu-id="de10e-262">SD</span><span class="sxs-lookup"><span data-stu-id="de10e-262">SD</span></span>   | <span data-ttu-id="de10e-263">Faire défiler vers le bas</span><span class="sxs-lookup"><span data-stu-id="de10e-263">Scroll Down</span></span> | <span data-ttu-id="de10e-264">Faites défiler la liste de &lt; n &gt; .</span><span class="sxs-lookup"><span data-stu-id="de10e-264">Scroll down by &lt;n&gt;.</span></span> <span data-ttu-id="de10e-265">Également appelée panoramique, les nouvelles lignes remplissent à partir du haut de l’écran</span><span class="sxs-lookup"><span data-stu-id="de10e-265">Also known as pan up, new lines fill in from the top of the screen</span></span>         |



<span data-ttu-id="de10e-266">Le texte est déplacé à partir de la ligne sur laquelle se trouve le curseur.</span><span class="sxs-lookup"><span data-stu-id="de10e-266">The text is moved starting with the line the cursor is on.</span></span> <span data-ttu-id="de10e-267">Si le curseur se trouve sur la ligne du milieu de la fenêtre d’affichage, le défilement vers le haut déplace la moitié inférieure de la fenêtre d’affichage et insère des lignes vides en bas.</span><span class="sxs-lookup"><span data-stu-id="de10e-267">If the cursor is on the middle row of the viewport, then scroll up would move the bottom half of the viewport, and insert blank lines at the bottom.</span></span> <span data-ttu-id="de10e-268">Faire défiler vers le haut déplace la moitié supérieure des lignes de la fenêtre d’affichage et insère de nouvelles lignes en haut.</span><span class="sxs-lookup"><span data-stu-id="de10e-268">Scroll down would move the top half of the viewport’s rows, and insert new lines at the top.</span></span>

<span data-ttu-id="de10e-269">Il est également important de noter que le défilement vers le haut et vers le haut est également affecté par les marges de défilement.</span><span class="sxs-lookup"><span data-stu-id="de10e-269">Also important to note is scroll up and down are also affected by the scrolling margins.</span></span> <span data-ttu-id="de10e-270">Le défilement vers le haut et vers le haut n’affecte pas les lignes situées en dehors des marges de défilement.</span><span class="sxs-lookup"><span data-stu-id="de10e-270">Scroll up and down won’t affect any lines outside the scrolling margins.</span></span>

<span data-ttu-id="de10e-271">La valeur par défaut de &lt; n &gt; est 1 et la valeur peut éventuellement être omise.</span><span class="sxs-lookup"><span data-stu-id="de10e-271">The default value for &lt;n&gt; is 1, and the value can be optionally omitted.</span></span>

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span data-ttu-id="de10e-272"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Modification du texte</span><span class="sxs-lookup"><span data-stu-id="de10e-272"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Text Modification</span></span>


<span data-ttu-id="de10e-273">Toutes les commandes de cette section sont généralement équivalentes à l’appel d’API de console [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)et [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) pour modifier le contenu de la mémoire tampon de texte.</span><span class="sxs-lookup"><span data-stu-id="de10e-273">All commands in this section are generally equivalent to calling [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md), and [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console APIs to modify the text buffer contents.</span></span>


| <span data-ttu-id="de10e-274">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-274">Sequence</span></span>           | <span data-ttu-id="de10e-275">Code</span><span class="sxs-lookup"><span data-stu-id="de10e-275">Code</span></span> | <span data-ttu-id="de10e-276">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-276">Description</span></span>      | <span data-ttu-id="de10e-277">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-277">Behavior</span></span>                                                                                                                                          |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="de10e-278">ECHAP \[ &lt; n&gt; @</span><span class="sxs-lookup"><span data-stu-id="de10e-278">ESC \[ &lt;n&gt; @</span></span> | <span data-ttu-id="de10e-279">Centr</span><span class="sxs-lookup"><span data-stu-id="de10e-279">ICH</span></span>  | <span data-ttu-id="de10e-280">Insérer un caractère</span><span class="sxs-lookup"><span data-stu-id="de10e-280">Insert Character</span></span> | <span data-ttu-id="de10e-281">Insérer &lt; n &gt; espaces à la position actuelle du curseur, en décalant tout le texte existant vers la droite.</span><span class="sxs-lookup"><span data-stu-id="de10e-281">Insert &lt;n&gt; spaces at the current cursor position, shifting all existing text to the right.</span></span> <span data-ttu-id="de10e-282">Le texte qui quitte l’écran à droite est supprimé.</span><span class="sxs-lookup"><span data-stu-id="de10e-282">Text exiting the screen to the right is removed.</span></span> |
| <span data-ttu-id="de10e-283">ECHAP \[ &lt; n &gt; P</span><span class="sxs-lookup"><span data-stu-id="de10e-283">ESC \[ &lt;n&gt; P</span></span> | <span data-ttu-id="de10e-284">DCH</span><span class="sxs-lookup"><span data-stu-id="de10e-284">DCH</span></span>  | <span data-ttu-id="de10e-285">Supprimer le caractère</span><span class="sxs-lookup"><span data-stu-id="de10e-285">Delete Character</span></span> | <span data-ttu-id="de10e-286">Supprime &lt; &gt; les n caractères à la position actuelle du curseur, en les décalant dans les espaces à partir du bord droit de l’écran.</span><span class="sxs-lookup"><span data-stu-id="de10e-286">Delete &lt;n&gt; characters at the current cursor position, shifting in space characters from the right edge of the screen.</span></span>                       |
| <span data-ttu-id="de10e-287">ECHAP \[ &lt; n &gt; X</span><span class="sxs-lookup"><span data-stu-id="de10e-287">ESC \[ &lt;n&gt; X</span></span> | <span data-ttu-id="de10e-288">YÈTCH</span><span class="sxs-lookup"><span data-stu-id="de10e-288">ECH</span></span>  | <span data-ttu-id="de10e-289">Effacer le caractère</span><span class="sxs-lookup"><span data-stu-id="de10e-289">Erase Character</span></span>  | <span data-ttu-id="de10e-290">Efface les &lt; n &gt; caractères de la position actuelle du curseur en les remplaçant par un espace.</span><span class="sxs-lookup"><span data-stu-id="de10e-290">Erase &lt;n&gt; characters from the current cursor position by overwriting them with a space character.</span></span>                                           |
| <span data-ttu-id="de10e-291">ECHAP \[ &lt; n &gt; L</span><span class="sxs-lookup"><span data-stu-id="de10e-291">ESC \[ &lt;n&gt; L</span></span> | <span data-ttu-id="de10e-292">IL</span><span class="sxs-lookup"><span data-stu-id="de10e-292">IL</span></span>   | <span data-ttu-id="de10e-293">Insérer une ligne</span><span class="sxs-lookup"><span data-stu-id="de10e-293">Insert Line</span></span>      | <span data-ttu-id="de10e-294">Insère &lt; n &gt; lignes dans la mémoire tampon à la position du curseur.</span><span class="sxs-lookup"><span data-stu-id="de10e-294">Inserts &lt;n&gt; lines into the buffer at the cursor position.</span></span> <span data-ttu-id="de10e-295">La ligne sur laquelle se trouve le curseur et les lignes au-dessous de celle-ci sont décalées vers le bas.</span><span class="sxs-lookup"><span data-stu-id="de10e-295">The line the cursor is on, and lines below it, will be shifted downwards.</span></span>         |
| <span data-ttu-id="de10e-296">ECHAP \[ &lt; n &gt; M</span><span class="sxs-lookup"><span data-stu-id="de10e-296">ESC \[ &lt;n&gt; M</span></span> | <span data-ttu-id="de10e-297">DL</span><span class="sxs-lookup"><span data-stu-id="de10e-297">DL</span></span>   | <span data-ttu-id="de10e-298">Supprimer la ligne</span><span class="sxs-lookup"><span data-stu-id="de10e-298">Delete Line</span></span>      | <span data-ttu-id="de10e-299">Supprime &lt; n &gt; lignes de la mémoire tampon, en commençant par la ligne sur laquelle se trouve le curseur.</span><span class="sxs-lookup"><span data-stu-id="de10e-299">Deletes &lt;n&gt; lines from the buffer, starting with the row the cursor is on.</span></span>                                                                  |



<span data-ttu-id="de10e-300">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="de10e-300">**Note**</span></span>  
<span data-ttu-id="de10e-301">Pour IL et DL, seules les lignes des marges de défilement (voir marges de défilement) sont affectées.</span><span class="sxs-lookup"><span data-stu-id="de10e-301">For IL and DL, only the lines in the scrolling margins (see Scrolling Margins) are affected.</span></span> <span data-ttu-id="de10e-302">Si aucune marge n’est définie, les bordures de marge par défaut sont la fenêtre d’affichage actuelle.</span><span class="sxs-lookup"><span data-stu-id="de10e-302">If no margins are set, the default margin borders are the current viewport.</span></span> <span data-ttu-id="de10e-303">Si les lignes sont décalées en dessous des marges, elles sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="de10e-303">If lines would be shifted below the margins, they are discarded.</span></span> <span data-ttu-id="de10e-304">Lorsque des lignes sont supprimées, des lignes vides sont insérées en bas des marges, les lignes extérieures à la fenêtre d’affichage ne sont jamais affectées.</span><span class="sxs-lookup"><span data-stu-id="de10e-304">When lines are deleted, blank lines are inserted at the bottom of the margins, lines from outside the viewport are never affected.</span></span>

<span data-ttu-id="de10e-305">Pour chacune des séquences, la valeur par défaut pour &lt; n &gt; s’il est omis est 0.</span><span class="sxs-lookup"><span data-stu-id="de10e-305">For each of the sequences, the default value for &lt;n&gt; if it is omitted is 0.</span></span>



<span data-ttu-id="de10e-306">Pour les commandes suivantes, le paramètre &lt; n &gt; a 3 valeurs valides :</span><span class="sxs-lookup"><span data-stu-id="de10e-306">For the following commands, the parameter &lt;n&gt; has 3 valid values:</span></span>

- <span data-ttu-id="de10e-307">0 efface de la position actuelle du curseur jusqu’à la fin de la ligne/de l’affichage</span><span class="sxs-lookup"><span data-stu-id="de10e-307">0 erases from the current cursor position (inclusive) to the end of the line/display</span></span>
- <span data-ttu-id="de10e-308">1 efface à partir du début de la ligne/s’affiche jusqu’à la position actuelle du curseur et y compris</span><span class="sxs-lookup"><span data-stu-id="de10e-308">1 erases from the beginning of the line/display up to and including the current cursor position</span></span>
- <span data-ttu-id="de10e-309">2 efface l’intégralité de la ligne/de l’affichage</span><span class="sxs-lookup"><span data-stu-id="de10e-309">2 erases the entire line/display</span></span>


| <span data-ttu-id="de10e-310">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-310">Sequence</span></span>           | <span data-ttu-id="de10e-311">Code</span><span class="sxs-lookup"><span data-stu-id="de10e-311">Code</span></span> | <span data-ttu-id="de10e-312">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-312">Description</span></span>      | <span data-ttu-id="de10e-313">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-313">Behavior</span></span>                                                                                     |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="de10e-314">ECHAP \[ &lt; n &gt; J</span><span class="sxs-lookup"><span data-stu-id="de10e-314">ESC \[ &lt;n&gt; J</span></span> | <span data-ttu-id="de10e-315">ED</span><span class="sxs-lookup"><span data-stu-id="de10e-315">ED</span></span>   | <span data-ttu-id="de10e-316">Effacer dans l’affichage</span><span class="sxs-lookup"><span data-stu-id="de10e-316">Erase in Display</span></span> | <span data-ttu-id="de10e-317">Remplacer tout le texte de la fenêtre d’affichage ou de l’écran en cours spécifié par &lt; n &gt; espaces</span><span class="sxs-lookup"><span data-stu-id="de10e-317">Replace all text in the current viewport/screen specified by &lt;n&gt; with space characters</span></span> |
| <span data-ttu-id="de10e-318">ECHAP \[ &lt; n &gt; K</span><span class="sxs-lookup"><span data-stu-id="de10e-318">ESC \[ &lt;n&gt; K</span></span> | <span data-ttu-id="de10e-319">CYRILLIQUE</span><span class="sxs-lookup"><span data-stu-id="de10e-319">EL</span></span>   | <span data-ttu-id="de10e-320">Effacer à la ligne</span><span class="sxs-lookup"><span data-stu-id="de10e-320">Erase in Line</span></span>    | <span data-ttu-id="de10e-321">Remplacer tout le texte de la ligne par le curseur spécifié par &lt; n &gt; espaces</span><span class="sxs-lookup"><span data-stu-id="de10e-321">Replace all text on the line with the cursor specified by &lt;n&gt; with space characters</span></span>    |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span data-ttu-id="de10e-322"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Mise en forme du texte</span><span class="sxs-lookup"><span data-stu-id="de10e-322"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Text Formatting</span></span>


<span data-ttu-id="de10e-323">Toutes les commandes de cette section sont généralement équivalentes à l’appel des API de console [**SetConsoleTextAttribute**](setconsoletextattribute.md) pour ajuster la mise en forme de toutes les écritures futures dans la mémoire tampon de texte de sortie de la console.</span><span class="sxs-lookup"><span data-stu-id="de10e-323">All commands in this section are generally equivalent to calling [**SetConsoleTextAttribute**](setconsoletextattribute.md) console APIs to adjust the formatting of all future writes to the console output text buffer.</span></span>

<span data-ttu-id="de10e-324">Cette commande est spéciale dans la mesure où la &lt; &gt; position n ci-dessous peut accepter entre 0 et 16 paramètres séparés par des points-virgules.</span><span class="sxs-lookup"><span data-stu-id="de10e-324">This command is special in that the &lt;n&gt; position below can accept between 0 and 16 parameters separated by semicolons.</span></span>

<span data-ttu-id="de10e-325">Quand aucun paramètre n’est spécifié, il est traité de la même manière qu’un seul paramètre 0.</span><span class="sxs-lookup"><span data-stu-id="de10e-325">When no parameters are specified, it is treated the same as a single 0 parameter.</span></span>


| <span data-ttu-id="de10e-326">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-326">Sequence</span></span>           | <span data-ttu-id="de10e-327">Code</span><span class="sxs-lookup"><span data-stu-id="de10e-327">Code</span></span> | <span data-ttu-id="de10e-328">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-328">Description</span></span>            | <span data-ttu-id="de10e-329">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-329">Behavior</span></span>                                                        |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| <span data-ttu-id="de10e-330">ECHAP \[ &lt; n &gt; m</span><span class="sxs-lookup"><span data-stu-id="de10e-330">ESC \[ &lt;n&gt; m</span></span> | <span data-ttu-id="de10e-331">SGR</span><span class="sxs-lookup"><span data-stu-id="de10e-331">SGR</span></span>  | <span data-ttu-id="de10e-332">Définir un rendu graphique</span><span class="sxs-lookup"><span data-stu-id="de10e-332">Set Graphics Rendition</span></span> | <span data-ttu-id="de10e-333">Définir le format de l’écran et du texte comme spécifié par &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="de10e-333">Set the format of the screen and text as specified by &lt;n&gt;</span></span> |



<span data-ttu-id="de10e-334">Le tableau de valeurs suivant peut être utilisé dans &lt; n &gt; pour représenter différents modes de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="de10e-334">The following table of values can be used in &lt;n&gt; to represent different formatting modes.</span></span>

<span data-ttu-id="de10e-335">Les modes de mise en forme s’appliquent de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="de10e-335">Formatting modes are applied from left to right.</span></span> <span data-ttu-id="de10e-336">L’application d’options de mise en forme concurrentes entraînera la précédence de l’option la plus à droite.</span><span class="sxs-lookup"><span data-stu-id="de10e-336">Applying competing formatting options will result in the right-most option taking precedence.</span></span>

<span data-ttu-id="de10e-337">Pour les options qui spécifient des couleurs, les couleurs sont utilisées comme défini dans la table des couleurs de la console, qui peut être modifiée à l’aide de l’API [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) .</span><span class="sxs-lookup"><span data-stu-id="de10e-337">For options that specify colors, the colors will be used as defined in the console color table which can be modified using the [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) API.</span></span> <span data-ttu-id="de10e-338">Si la table est modifiée pour que la position « bleu » dans la table affiche un ombrage RVB rouge, tous les appels au **premier plan bleu** affichent cette couleur rouge jusqu’à ce qu’ils soient modifiés.</span><span class="sxs-lookup"><span data-stu-id="de10e-338">If the table is modified to make the “blue” position in the table display an RGB shade of red, then all calls to **Foreground Blue** will display that red color until otherwise changed.</span></span>


| <span data-ttu-id="de10e-339">Value</span><span class="sxs-lookup"><span data-stu-id="de10e-339">Value</span></span> | <span data-ttu-id="de10e-340">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-340">Description</span></span>               | <span data-ttu-id="de10e-341">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-341">Behavior</span></span>                                                           |
|-------|---------------------------|--------------------------------------------------------------------|
| <span data-ttu-id="de10e-342">0</span><span class="sxs-lookup"><span data-stu-id="de10e-342">0</span></span>     | <span data-ttu-id="de10e-343">Default</span><span class="sxs-lookup"><span data-stu-id="de10e-343">Default</span></span>                   | <span data-ttu-id="de10e-344">Retourne tous les attributs à l’État par défaut avant la modification</span><span class="sxs-lookup"><span data-stu-id="de10e-344">Returns all attributes to the default state prior to modification</span></span>  |
| <span data-ttu-id="de10e-345">1</span><span class="sxs-lookup"><span data-stu-id="de10e-345">1</span></span>     | <span data-ttu-id="de10e-346">Gras/vif</span><span class="sxs-lookup"><span data-stu-id="de10e-346">Bold/Bright</span></span>               | <span data-ttu-id="de10e-347">Applique l’indicateur de luminosité/intensité à la couleur de premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-347">Applies brightness/intensity flag to foreground color</span></span>              |
| <span data-ttu-id="de10e-348">4</span><span class="sxs-lookup"><span data-stu-id="de10e-348">4</span></span>     | <span data-ttu-id="de10e-349">Souligner</span><span class="sxs-lookup"><span data-stu-id="de10e-349">Underline</span></span>                 | <span data-ttu-id="de10e-350">Ajoute un soulignement</span><span class="sxs-lookup"><span data-stu-id="de10e-350">Adds underline</span></span>                                                     |
| <span data-ttu-id="de10e-351">24</span><span class="sxs-lookup"><span data-stu-id="de10e-351">24</span></span>    | <span data-ttu-id="de10e-352">Pas de soulignement</span><span class="sxs-lookup"><span data-stu-id="de10e-352">No underline</span></span>              | <span data-ttu-id="de10e-353">Supprime le soulignement</span><span class="sxs-lookup"><span data-stu-id="de10e-353">Removes underline</span></span>                                                  |
| <span data-ttu-id="de10e-354">7</span><span class="sxs-lookup"><span data-stu-id="de10e-354">7</span></span>     | <span data-ttu-id="de10e-355">Négatif</span><span class="sxs-lookup"><span data-stu-id="de10e-355">Negative</span></span>                  | <span data-ttu-id="de10e-356">Permute les couleurs de premier plan et d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-356">Swaps foreground and background colors</span></span>                             |
| <span data-ttu-id="de10e-357">27</span><span class="sxs-lookup"><span data-stu-id="de10e-357">27</span></span>    | <span data-ttu-id="de10e-358">Positif (pas de négatif)</span><span class="sxs-lookup"><span data-stu-id="de10e-358">Positive (No negative)</span></span>    | <span data-ttu-id="de10e-359">Retourne le premier plan/l’arrière-plan à normal</span><span class="sxs-lookup"><span data-stu-id="de10e-359">Returns foreground/background to normal</span></span>                            |
| <span data-ttu-id="de10e-360">30</span><span class="sxs-lookup"><span data-stu-id="de10e-360">30</span></span>    | <span data-ttu-id="de10e-361">Noir de premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-361">Foreground Black</span></span>          | <span data-ttu-id="de10e-362">Applique un noir clair ou non gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-362">Applies non-bold/bright black to foreground</span></span>                        |
| <span data-ttu-id="de10e-363">31</span><span class="sxs-lookup"><span data-stu-id="de10e-363">31</span></span>    | <span data-ttu-id="de10e-364">Premier plan rouge</span><span class="sxs-lookup"><span data-stu-id="de10e-364">Foreground Red</span></span>            | <span data-ttu-id="de10e-365">Applique un rouge vif ou non gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-365">Applies non-bold/bright red to foreground</span></span>                          |
| <span data-ttu-id="de10e-366">32</span><span class="sxs-lookup"><span data-stu-id="de10e-366">32</span></span>    | <span data-ttu-id="de10e-367">Vert de premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-367">Foreground Green</span></span>          | <span data-ttu-id="de10e-368">Applique un vert clair ou non gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-368">Applies non-bold/bright green to foreground</span></span>                        |
| <span data-ttu-id="de10e-369">33</span><span class="sxs-lookup"><span data-stu-id="de10e-369">33</span></span>    | <span data-ttu-id="de10e-370">Premier plan jaune</span><span class="sxs-lookup"><span data-stu-id="de10e-370">Foreground Yellow</span></span>         | <span data-ttu-id="de10e-371">Applique le jaune clair ou non gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-371">Applies non-bold/bright yellow to foreground</span></span>                       |
| <span data-ttu-id="de10e-372">34</span><span class="sxs-lookup"><span data-stu-id="de10e-372">34</span></span>    | <span data-ttu-id="de10e-373">Bleu de premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-373">Foreground Blue</span></span>           | <span data-ttu-id="de10e-374">Applique le bleu clair ou non gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-374">Applies non-bold/bright blue to foreground</span></span>                         |
| <span data-ttu-id="de10e-375">35</span><span class="sxs-lookup"><span data-stu-id="de10e-375">35</span></span>    | <span data-ttu-id="de10e-376">Magenta de premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-376">Foreground Magenta</span></span>        | <span data-ttu-id="de10e-377">Applique le magenta non gras/clair au premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-377">Applies non-bold/bright magenta to foreground</span></span>                      |
| <span data-ttu-id="de10e-378">36</span><span class="sxs-lookup"><span data-stu-id="de10e-378">36</span></span>    | <span data-ttu-id="de10e-379">Cyan de premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-379">Foreground Cyan</span></span>           | <span data-ttu-id="de10e-380">Applique un cyan clair ou non gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-380">Applies non-bold/bright cyan to foreground</span></span>                         |
| <span data-ttu-id="de10e-381">37</span><span class="sxs-lookup"><span data-stu-id="de10e-381">37</span></span>    | <span data-ttu-id="de10e-382">Blanc de premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-382">Foreground White</span></span>          | <span data-ttu-id="de10e-383">Applique un blanc clair ou non gras au premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-383">Applies non-bold/bright white to foreground</span></span>                        |
| <span data-ttu-id="de10e-384">38</span><span class="sxs-lookup"><span data-stu-id="de10e-384">38</span></span>    | <span data-ttu-id="de10e-385">Premier plan étendu</span><span class="sxs-lookup"><span data-stu-id="de10e-385">Foreground Extended</span></span>       | <span data-ttu-id="de10e-386">Applique la valeur de couleur étendue au premier plan (voir les détails ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="de10e-386">Applies extended color value to the foreground (see details below)</span></span> |
| <span data-ttu-id="de10e-387">39</span><span class="sxs-lookup"><span data-stu-id="de10e-387">39</span></span>    | <span data-ttu-id="de10e-388">Premier plan par défaut</span><span class="sxs-lookup"><span data-stu-id="de10e-388">Foreground Default</span></span>        | <span data-ttu-id="de10e-389">Applique uniquement la partie de premier plan des valeurs par défaut (voir 0).</span><span class="sxs-lookup"><span data-stu-id="de10e-389">Applies only the foreground portion of the defaults (see 0)</span></span>        |
| <span data-ttu-id="de10e-390">40</span><span class="sxs-lookup"><span data-stu-id="de10e-390">40</span></span>    | <span data-ttu-id="de10e-391">Arrière-plan noir</span><span class="sxs-lookup"><span data-stu-id="de10e-391">Background Black</span></span>          | <span data-ttu-id="de10e-392">Applique un noir non gras/clair à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-392">Applies non-bold/bright black to background</span></span>                        |
| <span data-ttu-id="de10e-393">41</span><span class="sxs-lookup"><span data-stu-id="de10e-393">41</span></span>    | <span data-ttu-id="de10e-394">Arrière-plan rouge</span><span class="sxs-lookup"><span data-stu-id="de10e-394">Background Red</span></span>            | <span data-ttu-id="de10e-395">Applique le rouge non gras/clair à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-395">Applies non-bold/bright red to background</span></span>                          |
| <span data-ttu-id="de10e-396">42</span><span class="sxs-lookup"><span data-stu-id="de10e-396">42</span></span>    | <span data-ttu-id="de10e-397">Arrière-plan vert</span><span class="sxs-lookup"><span data-stu-id="de10e-397">Background Green</span></span>          | <span data-ttu-id="de10e-398">Applique un vert clair ou non gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-398">Applies non-bold/bright green to background</span></span>                        |
| <span data-ttu-id="de10e-399">43</span><span class="sxs-lookup"><span data-stu-id="de10e-399">43</span></span>    | <span data-ttu-id="de10e-400">Arrière-plan jaune</span><span class="sxs-lookup"><span data-stu-id="de10e-400">Background Yellow</span></span>         | <span data-ttu-id="de10e-401">Applique le jaune non gras/clair à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-401">Applies non-bold/bright yellow to background</span></span>                       |
| <span data-ttu-id="de10e-402">44</span><span class="sxs-lookup"><span data-stu-id="de10e-402">44</span></span>    | <span data-ttu-id="de10e-403">Arrière-plan bleu</span><span class="sxs-lookup"><span data-stu-id="de10e-403">Background Blue</span></span>           | <span data-ttu-id="de10e-404">Applique le bleu clair ou non gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-404">Applies non-bold/bright blue to background</span></span>                         |
| <span data-ttu-id="de10e-405">45</span><span class="sxs-lookup"><span data-stu-id="de10e-405">45</span></span>    | <span data-ttu-id="de10e-406">Arrière-plan magenta</span><span class="sxs-lookup"><span data-stu-id="de10e-406">Background Magenta</span></span>        | <span data-ttu-id="de10e-407">Applique le magenta non gras/clair à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-407">Applies non-bold/bright magenta to background</span></span>                      |
| <span data-ttu-id="de10e-408">46</span><span class="sxs-lookup"><span data-stu-id="de10e-408">46</span></span>    | <span data-ttu-id="de10e-409">Arrière-plan cyan</span><span class="sxs-lookup"><span data-stu-id="de10e-409">Background Cyan</span></span>           | <span data-ttu-id="de10e-410">Applique un cyan clair ou non gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-410">Applies non-bold/bright cyan to background</span></span>                         |
| <span data-ttu-id="de10e-411">47</span><span class="sxs-lookup"><span data-stu-id="de10e-411">47</span></span>    | <span data-ttu-id="de10e-412">Arrière-plan blanc</span><span class="sxs-lookup"><span data-stu-id="de10e-412">Background White</span></span>          | <span data-ttu-id="de10e-413">Applique un blanc clair ou non gras à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-413">Applies non-bold/bright white to background</span></span>                        |
| <span data-ttu-id="de10e-414">48</span><span class="sxs-lookup"><span data-stu-id="de10e-414">48</span></span>    | <span data-ttu-id="de10e-415">Arrière-plan étendu</span><span class="sxs-lookup"><span data-stu-id="de10e-415">Background Extended</span></span>       | <span data-ttu-id="de10e-416">Applique la valeur de couleur étendue à l’arrière-plan (voir les détails ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="de10e-416">Applies extended color value to the background (see details below)</span></span> |
| <span data-ttu-id="de10e-417">49</span><span class="sxs-lookup"><span data-stu-id="de10e-417">49</span></span>    | <span data-ttu-id="de10e-418">Arrière-plan par défaut</span><span class="sxs-lookup"><span data-stu-id="de10e-418">Background Default</span></span>        | <span data-ttu-id="de10e-419">Applique uniquement la partie d’arrière-plan des valeurs par défaut (voir 0).</span><span class="sxs-lookup"><span data-stu-id="de10e-419">Applies only the background portion of the defaults (see 0)</span></span>        |
| <span data-ttu-id="de10e-420">90</span><span class="sxs-lookup"><span data-stu-id="de10e-420">90</span></span>    | <span data-ttu-id="de10e-421">Noir de premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-421">Bright Foreground Black</span></span>   | <span data-ttu-id="de10e-422">Applique le noir gras/clair au premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-422">Applies bold/bright black to foreground</span></span>                            |
| <span data-ttu-id="de10e-423">91</span><span class="sxs-lookup"><span data-stu-id="de10e-423">91</span></span>    | <span data-ttu-id="de10e-424">Rouge de premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-424">Bright Foreground Red</span></span>     | <span data-ttu-id="de10e-425">Applique le rouge gras/vif au premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-425">Applies bold/bright red to foreground</span></span>                              |
| <span data-ttu-id="de10e-426">92</span><span class="sxs-lookup"><span data-stu-id="de10e-426">92</span></span>    | <span data-ttu-id="de10e-427">Vert de premier plan brillant</span><span class="sxs-lookup"><span data-stu-id="de10e-427">Bright Foreground Green</span></span>   | <span data-ttu-id="de10e-428">Applique le vert gras/vif au premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-428">Applies bold/bright green to foreground</span></span>                            |
| <span data-ttu-id="de10e-429">93</span><span class="sxs-lookup"><span data-stu-id="de10e-429">93</span></span>    | <span data-ttu-id="de10e-430">Clair de premier plan jaune</span><span class="sxs-lookup"><span data-stu-id="de10e-430">Bright Foreground Yellow</span></span>  | <span data-ttu-id="de10e-431">Applique le jaune gras/clair au premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-431">Applies bold/bright yellow to foreground</span></span>                           |
| <span data-ttu-id="de10e-432">94</span><span class="sxs-lookup"><span data-stu-id="de10e-432">94</span></span>    | <span data-ttu-id="de10e-433">Bleu de premier plan brillant</span><span class="sxs-lookup"><span data-stu-id="de10e-433">Bright Foreground Blue</span></span>    | <span data-ttu-id="de10e-434">Applique le bleu gras/clair au premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-434">Applies bold/bright blue to foreground</span></span>                             |
| <span data-ttu-id="de10e-435">95</span><span class="sxs-lookup"><span data-stu-id="de10e-435">95</span></span>    | <span data-ttu-id="de10e-436">Magenta de premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-436">Bright Foreground Magenta</span></span> | <span data-ttu-id="de10e-437">Applique le magenta gras/vif au premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-437">Applies bold/bright magenta to foreground</span></span>                          |
| <span data-ttu-id="de10e-438">96</span><span class="sxs-lookup"><span data-stu-id="de10e-438">96</span></span>    | <span data-ttu-id="de10e-439">Cyan de premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-439">Bright Foreground Cyan</span></span>    | <span data-ttu-id="de10e-440">Applique le cyan gras/vif au premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-440">Applies bold/bright cyan to foreground</span></span>                             |
| <span data-ttu-id="de10e-441">97</span><span class="sxs-lookup"><span data-stu-id="de10e-441">97</span></span>    | <span data-ttu-id="de10e-442">Blanc de premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-442">Bright Foreground White</span></span>   | <span data-ttu-id="de10e-443">Applique le gras/blanc brillant au premier plan</span><span class="sxs-lookup"><span data-stu-id="de10e-443">Applies bold/bright white to foreground</span></span>                            |
| <span data-ttu-id="de10e-444">100</span><span class="sxs-lookup"><span data-stu-id="de10e-444">100</span></span>   | <span data-ttu-id="de10e-445">Arrière-plan lumineux noir</span><span class="sxs-lookup"><span data-stu-id="de10e-445">Bright Background Black</span></span>   | <span data-ttu-id="de10e-446">Applique un noir gras/vif à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-446">Applies bold/bright black to background</span></span>                            |
| <span data-ttu-id="de10e-447">101</span><span class="sxs-lookup"><span data-stu-id="de10e-447">101</span></span>   | <span data-ttu-id="de10e-448">Arrière-plan lumineux rouge</span><span class="sxs-lookup"><span data-stu-id="de10e-448">Bright Background Red</span></span>     | <span data-ttu-id="de10e-449">Applique le rouge gras/vif à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-449">Applies bold/bright red to background</span></span>                              |
| <span data-ttu-id="de10e-450">102</span><span class="sxs-lookup"><span data-stu-id="de10e-450">102</span></span>   | <span data-ttu-id="de10e-451">Arrière-plan brillant vert</span><span class="sxs-lookup"><span data-stu-id="de10e-451">Bright Background Green</span></span>   | <span data-ttu-id="de10e-452">Applique le vert gras/vif à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-452">Applies bold/bright green to background</span></span>                            |
| <span data-ttu-id="de10e-453">103</span><span class="sxs-lookup"><span data-stu-id="de10e-453">103</span></span>   | <span data-ttu-id="de10e-454">Arrière-plan lumineux jaune</span><span class="sxs-lookup"><span data-stu-id="de10e-454">Bright Background Yellow</span></span>  | <span data-ttu-id="de10e-455">Applique le jaune gras/vif à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-455">Applies bold/bright yellow to background</span></span>                           |
| <span data-ttu-id="de10e-456">104</span><span class="sxs-lookup"><span data-stu-id="de10e-456">104</span></span>   | <span data-ttu-id="de10e-457">Arrière-plan bleu vif</span><span class="sxs-lookup"><span data-stu-id="de10e-457">Bright Background Blue</span></span>    | <span data-ttu-id="de10e-458">Applique le bleu gras/clair à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-458">Applies bold/bright blue to background</span></span>                             |
| <span data-ttu-id="de10e-459">105</span><span class="sxs-lookup"><span data-stu-id="de10e-459">105</span></span>   | <span data-ttu-id="de10e-460">Arrière-plan magenta clair</span><span class="sxs-lookup"><span data-stu-id="de10e-460">Bright Background Magenta</span></span> | <span data-ttu-id="de10e-461">Applique le magenta gras/vif à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-461">Applies bold/bright magenta to background</span></span>                          |
| <span data-ttu-id="de10e-462">106</span><span class="sxs-lookup"><span data-stu-id="de10e-462">106</span></span>   | <span data-ttu-id="de10e-463">Arrière-plan lumineux cyan</span><span class="sxs-lookup"><span data-stu-id="de10e-463">Bright Background Cyan</span></span>    | <span data-ttu-id="de10e-464">Applique le cyan gras/vif à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-464">Applies bold/bright cyan to background</span></span>                             |
| <span data-ttu-id="de10e-465">107</span><span class="sxs-lookup"><span data-stu-id="de10e-465">107</span></span>   | <span data-ttu-id="de10e-466">Blanc d’arrière-plan brillant</span><span class="sxs-lookup"><span data-stu-id="de10e-466">Bright Background White</span></span>   | <span data-ttu-id="de10e-467">Applique le blanc gras/clair à l’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="de10e-467">Applies bold/bright white to background</span></span>                            |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span data-ttu-id="de10e-468"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Couleurs étendues</span><span class="sxs-lookup"><span data-stu-id="de10e-468"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Extended Colors</span></span>

<span data-ttu-id="de10e-469">Certains émulateurs de terminaux virtuels prennent en charge une palette de couleurs supérieure aux 16 couleurs fournies par la console Windows.</span><span class="sxs-lookup"><span data-stu-id="de10e-469">Some virtual terminal emulators support a palette of colors greater than the 16 colors provided by the Windows Console.</span></span> <span data-ttu-id="de10e-470">Pour ces couleurs étendues, la console Windows choisit la couleur appropriée la plus proche de la table 16 couleurs existante pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="de10e-470">For these extended colors, the Windows Console will choose the nearest appropriate color from the existing 16 color table for display.</span></span> <span data-ttu-id="de10e-471">Contrairement aux valeurs SGR classiques ci-dessus, les valeurs étendues consomment des paramètres supplémentaires après l’indicateur initial, conformément au tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="de10e-471">Unlike typical SGR values above, the extended values will consume additional parameters after the initial indicator according to the table below.</span></span>


| <span data-ttu-id="de10e-472">Sous-séquence SGR</span><span class="sxs-lookup"><span data-stu-id="de10e-472">SGR Subsequence</span></span>                            | <span data-ttu-id="de10e-473">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-473">Description</span></span>                                                                                 |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="de10e-474">38 ; 2 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="de10e-474">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="de10e-475">Définir la couleur de premier plan sur la valeur RVB spécifiée dans les &lt; &gt; paramètres r, &lt; g &gt; , &lt; b &gt;\*</span><span class="sxs-lookup"><span data-stu-id="de10e-475">Set foreground color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="de10e-476">48 ; 2 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="de10e-476">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="de10e-477">Définir la couleur d’arrière-plan sur la valeur RVB spécifiée dans les &lt; &gt; paramètres r, &lt; g &gt; , &lt; b &gt;\*</span><span class="sxs-lookup"><span data-stu-id="de10e-477">Set background color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="de10e-478">38 ; 5,5 &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="de10e-478">38 ; 5 ; &lt;s&gt;</span></span>                         | <span data-ttu-id="de10e-479">Définir la couleur de premier plan sur &lt; &gt; l’index s dans la table de couleurs 88 ou 256\*</span><span class="sxs-lookup"><span data-stu-id="de10e-479">Set foreground color to &lt;s&gt; index in 88 or 256 color table\*</span></span>                          |
| <span data-ttu-id="de10e-480">48 ; 5,5 &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="de10e-480">48 ; 5 ; &lt;s&gt;</span></span>                         | <span data-ttu-id="de10e-481">Définir la couleur d’arrière-plan sur &lt; &gt; l’index s dans le tableau de couleurs 88 ou 256\*</span><span class="sxs-lookup"><span data-stu-id="de10e-481">Set background color to &lt;s&gt; index in 88 or 256 color table\*</span></span>                          |



<span data-ttu-id="de10e-482">\*Les palettes de couleurs 88 et 256 gérées en interne pour la comparaison sont basées sur l’émulateur de terminal xterm.</span><span class="sxs-lookup"><span data-stu-id="de10e-482">\*The 88 and 256 color palettes maintained internally for comparison are based from the xterm terminal emulator.</span></span> <span data-ttu-id="de10e-483">Les tables de comparaison et d’arrondi ne peuvent pas être modifiées pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="de10e-483">The comparison/rounding tables cannot be modified at this time.</span></span>


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span data-ttu-id="de10e-484"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Couleurs de l’écran</span><span class="sxs-lookup"><span data-stu-id="de10e-484"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Screen Colors</span></span>


<span data-ttu-id="de10e-485">La commande suivante permet à l’application de définir les valeurs de la palette de couleurs d’écran sur n’importe quelle valeur RVB.</span><span class="sxs-lookup"><span data-stu-id="de10e-485">The following command allows the application to set the screen colors palette values to any RGB value.</span></span>

<span data-ttu-id="de10e-486">Les valeurs RVB doivent être des valeurs hexadécimales comprises entre `0` et `ff` , et séparées par le caractère de barre oblique inverse (par exemple, `rgb:1/24/86` ).</span><span class="sxs-lookup"><span data-stu-id="de10e-486">The RGB values should be hexadecimal values between `0` and `ff`, and separated by the forward-slash character (e.g. `rgb:1/24/86`).</span></span>

<span data-ttu-id="de10e-487">Notez que cette séquence est une séquence de « commande du système d’exploitation » OSC, et non un CSI comme un grand nombre des autres séquences listées, et qu’elles commencent par « \\ X1B \] », et non pas par « \\ X1B \[ ».</span><span class="sxs-lookup"><span data-stu-id="de10e-487">Note that this sequence is an OSC “Operating system command” sequence, and not a CSI like many of the other sequences listed, and as such start with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="de10e-488">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-488">Sequence</span></span>                                                           | <span data-ttu-id="de10e-489">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-489">Description</span></span>          | <span data-ttu-id="de10e-490">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-490">Behavior</span></span>                                                                                                     |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="de10e-491">ESC \] 4 ; &lt; i &gt; ; RVB : &lt; r &gt;  /  &lt; g &gt;  /  &lt; b &gt; ESC</span><span class="sxs-lookup"><span data-stu-id="de10e-491">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span></span> | <span data-ttu-id="de10e-492">Modifier les couleurs de l’écran</span><span class="sxs-lookup"><span data-stu-id="de10e-492">Modify Screen Colors</span></span> | <span data-ttu-id="de10e-493">Définit l’index de la palette &lt; de couleurs de l’écran &gt; sur les valeurs RVB spécifiées dans &lt; r &gt; , &lt; g &gt; , &lt; b&gt;</span><span class="sxs-lookup"><span data-stu-id="de10e-493">Sets the screen color palette index &lt;i&gt; to the RGB values specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt;</span></span> |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span data-ttu-id="de10e-494"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Modifications du mode</span><span class="sxs-lookup"><span data-stu-id="de10e-494"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Mode Changes</span></span>


<span data-ttu-id="de10e-495">Il s’agit de séquences qui contrôlent les modes d’entrée.</span><span class="sxs-lookup"><span data-stu-id="de10e-495">These are sequences that control the input modes.</span></span> <span data-ttu-id="de10e-496">Il existe deux ensembles différents de modes de saisie : le mode touches de curseur et le mode touches du pavé numérique.</span><span class="sxs-lookup"><span data-stu-id="de10e-496">There are two different sets of input modes, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="de10e-497">Le mode touches de curseur contrôle les séquences émises par les touches de direction, ainsi que le mode de démarrage et de fin, tandis que le mode touches de clavier contrôle les séquences émises par les touches sur le pavé numérique, ainsi que les touches de fonction.</span><span class="sxs-lookup"><span data-stu-id="de10e-497">The Cursor Keys Mode controls the sequences that are emitted by the arrow keys as well as Home and End, while the Keypad Keys Mode controls the sequences emitted by the keys on the numpad primarily, as well as the function keys.</span></span>

<span data-ttu-id="de10e-498">Chacun de ces modes est un simple paramètre booléen : le mode touches de curseur est normal (valeur par défaut) ou application, et le mode touches du clavier est soit numérique (valeur par défaut), soit application.</span><span class="sxs-lookup"><span data-stu-id="de10e-498">Each of these modes are simple boolean settings – the Cursor Keys Mode is either Normal (default) or Application, and the Keypad Keys Mode is either Numeric (default) or Application.</span></span>

<span data-ttu-id="de10e-499">Consultez les sections touches de curseur et touches de fonction & pavé numérique pour les séquences émises dans ces modes.</span><span class="sxs-lookup"><span data-stu-id="de10e-499">See the Cursor Keys and Numpad & Function Keys sections for the sequences emitted in these modes.</span></span>


| <span data-ttu-id="de10e-500">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-500">Sequence</span></span>     | <span data-ttu-id="de10e-501">Code</span><span class="sxs-lookup"><span data-stu-id="de10e-501">Code</span></span>    | <span data-ttu-id="de10e-502">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-502">Description</span></span>                                            | <span data-ttu-id="de10e-503">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-503">Behavior</span></span>                                                |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| <span data-ttu-id="de10e-504">ECHAP =</span><span class="sxs-lookup"><span data-stu-id="de10e-504">ESC =</span></span>        | <span data-ttu-id="de10e-505">DECKPAM</span><span class="sxs-lookup"><span data-stu-id="de10e-505">DECKPAM</span></span> | <span data-ttu-id="de10e-506">Activer le mode d’application du clavier</span><span class="sxs-lookup"><span data-stu-id="de10e-506">Enable Keypad Application Mode</span></span>                         | <span data-ttu-id="de10e-507">Les touches du pavé numérique émettent leurs séquences en mode application.</span><span class="sxs-lookup"><span data-stu-id="de10e-507">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="de10e-508">Escudo &gt;</span><span class="sxs-lookup"><span data-stu-id="de10e-508">ESC &gt;</span></span>     | <span data-ttu-id="de10e-509">DECKPNM</span><span class="sxs-lookup"><span data-stu-id="de10e-509">DECKPNM</span></span> | <span data-ttu-id="de10e-510">Activer le mode numérique du pavé numérique</span><span class="sxs-lookup"><span data-stu-id="de10e-510">Enable Keypad Numeric Mode</span></span>                             | <span data-ttu-id="de10e-511">Les touches du pavé numérique émettent leurs séquences de mode numérique.</span><span class="sxs-lookup"><span data-stu-id="de10e-511">Keypad keys will emit their Numeric Mode sequences.</span></span>     |
| <span data-ttu-id="de10e-512">Échap \[ ?</span><span class="sxs-lookup"><span data-stu-id="de10e-512">ESC \[ ?</span></span> <span data-ttu-id="de10e-513">1 h</span><span class="sxs-lookup"><span data-stu-id="de10e-513">1 h</span></span> | <span data-ttu-id="de10e-514">DECCKM</span><span class="sxs-lookup"><span data-stu-id="de10e-514">DECCKM</span></span>  | <span data-ttu-id="de10e-515">Activer le mode d’application des touches de curseur</span><span class="sxs-lookup"><span data-stu-id="de10e-515">Enable Cursor Keys Application Mode</span></span>                    | <span data-ttu-id="de10e-516">Les touches du pavé numérique émettent leurs séquences en mode application.</span><span class="sxs-lookup"><span data-stu-id="de10e-516">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="de10e-517">Échap \[ ?</span><span class="sxs-lookup"><span data-stu-id="de10e-517">ESC \[ ?</span></span> <span data-ttu-id="de10e-518">1 l</span><span class="sxs-lookup"><span data-stu-id="de10e-518">1 l</span></span> | <span data-ttu-id="de10e-519">DECCKM</span><span class="sxs-lookup"><span data-stu-id="de10e-519">DECCKM</span></span>  | <span data-ttu-id="de10e-520">Désactiver le mode d’application des touches de curseur (utiliser le mode normal)</span><span class="sxs-lookup"><span data-stu-id="de10e-520">Disable Cursor Keys Application Mode (use Normal Mode)</span></span> | <span data-ttu-id="de10e-521">Les touches du pavé numérique émettent leurs séquences de mode numérique.</span><span class="sxs-lookup"><span data-stu-id="de10e-521">Keypad keys will emit their Numeric Mode sequences.</span></span>     |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span data-ttu-id="de10e-522"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>État de la requête</span><span class="sxs-lookup"><span data-stu-id="de10e-522"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Query State</span></span>


<span data-ttu-id="de10e-523">Toutes les commandes de cette section sont généralement équivalentes à l’appel de la commande obtenir des \* API de console pour récupérer des informations d’État sur l’état actuel de la mémoire tampon de la console.</span><span class="sxs-lookup"><span data-stu-id="de10e-523">All commands in this section are generally equivalent to calling Get\* console APIs to retrieve status information about the current console buffer state.</span></span>

<span data-ttu-id="de10e-524">**Remarque**  Ces requêtes émettent leurs réponses dans le flux d’entrée de la console immédiatement après leur reconnaissance sur le flux de sortie pendant que l’activation du \_ \_ traitement des terminaux virtuels \_ est définie.</span><span class="sxs-lookup"><span data-stu-id="de10e-524">**Note**  These queries will emit their responses into the console input stream immediately after being recognized on the output stream while ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING is set.</span></span> <span data-ttu-id="de10e-525">L' \_ \_ indicateur d’entrée activer le terminal virtuel \_ ne s’applique pas aux commandes de requête, car il est supposé qu’une application qui effectue la requête doit toujours recevoir la réponse.</span><span class="sxs-lookup"><span data-stu-id="de10e-525">The ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag does not apply to query commands as it is assumed that an application making the query will always want to receive the reply.</span></span>




| <span data-ttu-id="de10e-526">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-526">Sequence</span></span>   | <span data-ttu-id="de10e-527">Code</span><span class="sxs-lookup"><span data-stu-id="de10e-527">Code</span></span>    | <span data-ttu-id="de10e-528">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-528">Description</span></span>            | <span data-ttu-id="de10e-529">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-529">Behavior</span></span>                                                                                                               |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="de10e-530">ESC \[ 6 n</span><span class="sxs-lookup"><span data-stu-id="de10e-530">ESC \[ 6 n</span></span> | <span data-ttu-id="de10e-531">DECXCPR</span><span class="sxs-lookup"><span data-stu-id="de10e-531">DECXCPR</span></span> | <span data-ttu-id="de10e-532">Position du curseur de rapport</span><span class="sxs-lookup"><span data-stu-id="de10e-532">Report Cursor Position</span></span> | <span data-ttu-id="de10e-533">Émettez la position du curseur en tant que : ESC \[ &lt; r &gt; ; &lt; c &gt; r où &lt; R &gt; = ligne de curseur et &lt; c &gt; = colonne de curseur</span><span class="sxs-lookup"><span data-stu-id="de10e-533">Emit the cursor position as: ESC \[ &lt;r&gt; ; &lt;c&gt; R Where &lt;r&gt; = cursor row and &lt;c&gt; = cursor column</span></span> |
| <span data-ttu-id="de10e-534">ESC \[ 0 c</span><span class="sxs-lookup"><span data-stu-id="de10e-534">ESC \[ 0 c</span></span> | <span data-ttu-id="de10e-535">DA</span><span class="sxs-lookup"><span data-stu-id="de10e-535">DA</span></span>      | <span data-ttu-id="de10e-536">Attributs de l’appareil</span><span class="sxs-lookup"><span data-stu-id="de10e-536">Device Attributes</span></span>      | <span data-ttu-id="de10e-537">Signalez l’identité du terminal.</span><span class="sxs-lookup"><span data-stu-id="de10e-537">Report the terminal identity.</span></span> <span data-ttu-id="de10e-538">Émettra « \\ X1B \[ ? 1 ; 0C », indiquant « VT101 sans options ».</span><span class="sxs-lookup"><span data-stu-id="de10e-538">Will emit “\\x1b\[?1;0c”, indicating "VT101 with No Options".</span></span>                            |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span data-ttu-id="de10e-539"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Quitte</span><span class="sxs-lookup"><span data-stu-id="de10e-539"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabs</span></span>


<span data-ttu-id="de10e-540">Alors que la console Windows s’attend traditionnellement à ce que les onglets soient exclusivement dotés de huit caractères, \* nix les applications utilisant certaines séquences peuvent manipuler l’emplacement où les taquets de tabulation se trouvent dans les fenêtres de la console pour optimiser le déplacement des curseurs par l’application.</span><span class="sxs-lookup"><span data-stu-id="de10e-540">While the windows console traditionally expects tabs to be exclusively eight characters wide, \*nix applications utilizing certain sequences can manipulate where the tab stops are within the console windows to optimize cursor movement by the application.</span></span>

<span data-ttu-id="de10e-541">Les séquences suivantes permettent à une application de définir les emplacements de taquet de tabulation dans la fenêtre de console, de les supprimer et de naviguer entre elles.</span><span class="sxs-lookup"><span data-stu-id="de10e-541">The following sequences allow an application to set the tab stop locations within the console window, remove them, and navigate between them.</span></span>


| <span data-ttu-id="de10e-542">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-542">Sequence</span></span>           | <span data-ttu-id="de10e-543">Code</span><span class="sxs-lookup"><span data-stu-id="de10e-543">Code</span></span> | <span data-ttu-id="de10e-544">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-544">Description</span></span>                     | <span data-ttu-id="de10e-545">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-545">Behavior</span></span>                                                                                                                                                                                                                    |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="de10e-546">ESC H</span><span class="sxs-lookup"><span data-stu-id="de10e-546">ESC H</span></span>              | <span data-ttu-id="de10e-547">HTS</span><span class="sxs-lookup"><span data-stu-id="de10e-547">HTS</span></span>  | <span data-ttu-id="de10e-548">Ensemble de tabulations horizontales</span><span class="sxs-lookup"><span data-stu-id="de10e-548">Horizontal Tab Set</span></span>              | <span data-ttu-id="de10e-549">Définit un taquet de tabulation dans la colonne actuelle dans laquelle se trouve le curseur.</span><span class="sxs-lookup"><span data-stu-id="de10e-549">Sets a tab stop in the current column the cursor is in.</span></span>                                                                                                                                                                     |
| <span data-ttu-id="de10e-550">ECHAP \[ &lt; n &gt; I</span><span class="sxs-lookup"><span data-stu-id="de10e-550">ESC \[ &lt;n&gt; I</span></span> | <span data-ttu-id="de10e-551">CHT</span><span class="sxs-lookup"><span data-stu-id="de10e-551">CHT</span></span>  | <span data-ttu-id="de10e-552">Onglet curseur horizontal (suivant)</span><span class="sxs-lookup"><span data-stu-id="de10e-552">Cursor Horizontal (Forward) Tab</span></span> | <span data-ttu-id="de10e-553">Avancer le curseur jusqu’à la colonne suivante (sur la même ligne) avec un taquet de tabulation.</span><span class="sxs-lookup"><span data-stu-id="de10e-553">Advance the cursor to the next column (in the same row) with a tab stop.</span></span> <span data-ttu-id="de10e-554">S’il n’y a plus de taquets de tabulation, passez à la dernière colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="de10e-554">If there are no more tab stops, move to the last column in the row.</span></span> <span data-ttu-id="de10e-555">Si le curseur se trouve dans la dernière colonne, passez à la première colonne de la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="de10e-555">If the cursor is in the last column, move to the first column of the next row.</span></span> |
| <span data-ttu-id="de10e-556">ECHAP \[ &lt; n &gt; Z</span><span class="sxs-lookup"><span data-stu-id="de10e-556">ESC \[ &lt;n&gt; Z</span></span> | <span data-ttu-id="de10e-557">CBT</span><span class="sxs-lookup"><span data-stu-id="de10e-557">CBT</span></span>  | <span data-ttu-id="de10e-558">Onglet de curseur vers l’arrière</span><span class="sxs-lookup"><span data-stu-id="de10e-558">Cursor Backwards Tab</span></span>            | <span data-ttu-id="de10e-559">Déplacez le curseur vers la colonne précédente (sur la même ligne) avec un taquet de tabulation.</span><span class="sxs-lookup"><span data-stu-id="de10e-559">Move the cursor to the previous column (in the same row) with a tab stop.</span></span> <span data-ttu-id="de10e-560">S’il n’y a plus de taquets de tabulation, déplace le curseur vers la première colonne.</span><span class="sxs-lookup"><span data-stu-id="de10e-560">If there are no more tab stops, moves the cursor to the first column.</span></span> <span data-ttu-id="de10e-561">Si le curseur se trouve dans la première colonne, ne déplace pas le curseur.</span><span class="sxs-lookup"><span data-stu-id="de10e-561">If the cursor is in the first column, doesn’t move the cursor.</span></span>              |
| <span data-ttu-id="de10e-562">ESC \[ 0 g</span><span class="sxs-lookup"><span data-stu-id="de10e-562">ESC \[ 0 g</span></span>         | <span data-ttu-id="de10e-563">TBC</span><span class="sxs-lookup"><span data-stu-id="de10e-563">TBC</span></span>  | <span data-ttu-id="de10e-564">Tabulation effacer (colonne actuelle)</span><span class="sxs-lookup"><span data-stu-id="de10e-564">Tab Clear (current column)</span></span>      | <span data-ttu-id="de10e-565">Efface le taquet de tabulation dans la colonne actuelle, s’il en existe un.</span><span class="sxs-lookup"><span data-stu-id="de10e-565">Clears the tab stop in the current column, if there is one.</span></span> <span data-ttu-id="de10e-566">Sinon, ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="de10e-566">Otherwise does nothing.</span></span>                                                                                                                                         |
| <span data-ttu-id="de10e-567">ESC \[ 3 g</span><span class="sxs-lookup"><span data-stu-id="de10e-567">ESC \[ 3 g</span></span>         | <span data-ttu-id="de10e-568">TBC</span><span class="sxs-lookup"><span data-stu-id="de10e-568">TBC</span></span>  | <span data-ttu-id="de10e-569">Onglet effacer (toutes les colonnes)</span><span class="sxs-lookup"><span data-stu-id="de10e-569">Tab Clear (all columns)</span></span>         | <span data-ttu-id="de10e-570">Efface tous les taquets de tabulation actuellement définis.</span><span class="sxs-lookup"><span data-stu-id="de10e-570">Clears all currently set tab stops.</span></span>                                                                                                                                                                                         |



- <span data-ttu-id="de10e-571">Pour CHT et CBT, &lt; n &gt; est un paramètre facultatif qui (valeur par défaut = 1) indique le nombre d’incréments du curseur dans la direction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="de10e-571">For both CHT and CBT, &lt;n&gt; is an optional parameter that (default=1) indicating how many times to advance the cursor in the specified direction.</span></span>
- <span data-ttu-id="de10e-572">Si aucun taquet de tabulation n’est défini via HTS, CHT et CBT traiteront la première et la dernière colonnes de la fenêtre, car les deux seuls taquets de tabulation.</span><span class="sxs-lookup"><span data-stu-id="de10e-572">If there are no tab stops set via HTS, CHT and CBT will treat the first and last columns of the window as the only two tab stops.</span></span>
- <span data-ttu-id="de10e-573">L’utilisation de HTS pour définir un taquet de tabulation entraîne également l’accès de la console au taquet de tabulation suivant sur la sortie d’un caractère de tabulation (0x09, ' \\ t'), de la même manière que CHT.</span><span class="sxs-lookup"><span data-stu-id="de10e-573">Using HTS to set a tab stop will also cause the console to navigate to the next tab stop on the output of a TAB (0x09, ‘\\t’) character, in the same manner as CHT.</span></span>

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span data-ttu-id="de10e-574"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Désigner le jeu de caractères</span><span class="sxs-lookup"><span data-stu-id="de10e-574"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designate Character Set</span></span>


<span data-ttu-id="de10e-575">Les séquences suivantes permettent à un programme de modifier le mappage du jeu de caractères actif.</span><span class="sxs-lookup"><span data-stu-id="de10e-575">The following sequences allow a program to change the active character set mapping.</span></span> <span data-ttu-id="de10e-576">Cela permet à un programme d’émettre des caractères ASCII de 7 bits, mais de les afficher sous la forme d’autres glyphes sur l’écran de terminal lui-même.</span><span class="sxs-lookup"><span data-stu-id="de10e-576">This allows a program to emit 7-bit ASCII characters, but have them displayed as other glyphs on the terminal screen itself.</span></span> <span data-ttu-id="de10e-577">Actuellement, les deux seuls jeux de caractères pris en charge sont ASCII (par défaut) et le jeu de caractères graphiques spéciaux DEC.</span><span class="sxs-lookup"><span data-stu-id="de10e-577">Currently, the only two supported character sets are ASCII (default) and the DEC Special Graphics Character Set.</span></span> <span data-ttu-id="de10e-578">Consultez <http://vt100.net/docs/vt220-rm/table2-4.html> pour obtenir la liste de tous les caractères représentés par le jeu de caractères spéciaux du DEC.</span><span class="sxs-lookup"><span data-stu-id="de10e-578">See <http://vt100.net/docs/vt220-rm/table2-4.html> for a listing of all of the characters represented by the DEC Special Graphics Character Set.</span></span>


| <span data-ttu-id="de10e-579">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-579">Sequence</span></span> | <span data-ttu-id="de10e-580">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-580">Description</span></span>                                | <span data-ttu-id="de10e-581">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-581">Behavior</span></span>                      |
|----------|--------------------------------------------|-------------------------------|
| <span data-ttu-id="de10e-582">ÉCHAP (0</span><span class="sxs-lookup"><span data-stu-id="de10e-582">ESC ( 0</span></span>  | <span data-ttu-id="de10e-583">Désigner le jeu de caractères – dessin de ligne DEC</span><span class="sxs-lookup"><span data-stu-id="de10e-583">Designate Character Set – DEC Line Drawing</span></span> | <span data-ttu-id="de10e-584">Active le mode de dessin de la ligne DEC</span><span class="sxs-lookup"><span data-stu-id="de10e-584">Enables DEC Line Drawing Mode</span></span> |
| <span data-ttu-id="de10e-585">ÉCHAP (B</span><span class="sxs-lookup"><span data-stu-id="de10e-585">ESC ( B</span></span>  | <span data-ttu-id="de10e-586">Désigner le jeu de caractères – ASCII US</span><span class="sxs-lookup"><span data-stu-id="de10e-586">Designate Character Set – US ASCII</span></span>         | <span data-ttu-id="de10e-587">Active le mode ASCII (par défaut)</span><span class="sxs-lookup"><span data-stu-id="de10e-587">Enables ASCII Mode (Default)</span></span>  |



<span data-ttu-id="de10e-588">En particulier, le mode de dessin de la ligne DEC est utilisé pour dessiner les bordures dans les applications console.</span><span class="sxs-lookup"><span data-stu-id="de10e-588">Notably, the DEC Line Drawing mode is used for drawing borders in console applications.</span></span> <span data-ttu-id="de10e-589">Le tableau suivant répertorie les correspondances de caractères ASCII avec le caractère de dessin de ligne.</span><span class="sxs-lookup"><span data-stu-id="de10e-589">The following table shows what ASCII character maps to which line drawing character.</span></span>


| <span data-ttu-id="de10e-590">Hex</span><span class="sxs-lookup"><span data-stu-id="de10e-590">Hex</span></span>  | <span data-ttu-id="de10e-591">ASCII</span><span class="sxs-lookup"><span data-stu-id="de10e-591">ASCII</span></span> | <span data-ttu-id="de10e-592">Dessin de ligne DEC</span><span class="sxs-lookup"><span data-stu-id="de10e-592">DEC Line Drawing</span></span> |
|------|-------|------------------|
| <span data-ttu-id="de10e-593">0x6a</span><span class="sxs-lookup"><span data-stu-id="de10e-593">0x6a</span></span> | <span data-ttu-id="de10e-594">j</span><span class="sxs-lookup"><span data-stu-id="de10e-594">j</span></span>     | <span data-ttu-id="de10e-595">┘</span><span class="sxs-lookup"><span data-stu-id="de10e-595">┘</span></span>                |
| <span data-ttu-id="de10e-596">0x6b</span><span class="sxs-lookup"><span data-stu-id="de10e-596">0x6b</span></span> | <span data-ttu-id="de10e-597">k</span><span class="sxs-lookup"><span data-stu-id="de10e-597">k</span></span>     | <span data-ttu-id="de10e-598">┐</span><span class="sxs-lookup"><span data-stu-id="de10e-598">┐</span></span>                |
| <span data-ttu-id="de10e-599">0x6C</span><span class="sxs-lookup"><span data-stu-id="de10e-599">0x6c</span></span> | <span data-ttu-id="de10e-600">l</span><span class="sxs-lookup"><span data-stu-id="de10e-600">l</span></span>     | <span data-ttu-id="de10e-601">┌</span><span class="sxs-lookup"><span data-stu-id="de10e-601">┌</span></span>                |
| <span data-ttu-id="de10e-602">0x6d</span><span class="sxs-lookup"><span data-stu-id="de10e-602">0x6d</span></span> | <span data-ttu-id="de10e-603">m</span><span class="sxs-lookup"><span data-stu-id="de10e-603">m</span></span>     | <span data-ttu-id="de10e-604">└</span><span class="sxs-lookup"><span data-stu-id="de10e-604">└</span></span>                |
| <span data-ttu-id="de10e-605">0x6e</span><span class="sxs-lookup"><span data-stu-id="de10e-605">0x6e</span></span> | <span data-ttu-id="de10e-606">n</span><span class="sxs-lookup"><span data-stu-id="de10e-606">n</span></span>     | <span data-ttu-id="de10e-607">┼</span><span class="sxs-lookup"><span data-stu-id="de10e-607">┼</span></span>                |
| <span data-ttu-id="de10e-608">0x71</span><span class="sxs-lookup"><span data-stu-id="de10e-608">0x71</span></span> | <span data-ttu-id="de10e-609">q</span><span class="sxs-lookup"><span data-stu-id="de10e-609">q</span></span>     | <span data-ttu-id="de10e-610">─</span><span class="sxs-lookup"><span data-stu-id="de10e-610">─</span></span>                |
| <span data-ttu-id="de10e-611">0x74</span><span class="sxs-lookup"><span data-stu-id="de10e-611">0x74</span></span> | <span data-ttu-id="de10e-612">t</span><span class="sxs-lookup"><span data-stu-id="de10e-612">t</span></span>     | <span data-ttu-id="de10e-613">├</span><span class="sxs-lookup"><span data-stu-id="de10e-613">├</span></span>                |
| <span data-ttu-id="de10e-614">0x75</span><span class="sxs-lookup"><span data-stu-id="de10e-614">0x75</span></span> | <span data-ttu-id="de10e-615">u</span><span class="sxs-lookup"><span data-stu-id="de10e-615">u</span></span>     | <span data-ttu-id="de10e-616">┤</span><span class="sxs-lookup"><span data-stu-id="de10e-616">┤</span></span>                |
| <span data-ttu-id="de10e-617">0x76</span><span class="sxs-lookup"><span data-stu-id="de10e-617">0x76</span></span> | <span data-ttu-id="de10e-618">v</span><span class="sxs-lookup"><span data-stu-id="de10e-618">v</span></span>     | <span data-ttu-id="de10e-619">┴</span><span class="sxs-lookup"><span data-stu-id="de10e-619">┴</span></span>                |
| <span data-ttu-id="de10e-620">0x77</span><span class="sxs-lookup"><span data-stu-id="de10e-620">0x77</span></span> | <span data-ttu-id="de10e-621">w</span><span class="sxs-lookup"><span data-stu-id="de10e-621">w</span></span>     | <span data-ttu-id="de10e-622">┬</span><span class="sxs-lookup"><span data-stu-id="de10e-622">┬</span></span>                |
| <span data-ttu-id="de10e-623">0x78</span><span class="sxs-lookup"><span data-stu-id="de10e-623">0x78</span></span> | <span data-ttu-id="de10e-624">x</span><span class="sxs-lookup"><span data-stu-id="de10e-624">x</span></span>     | <span data-ttu-id="de10e-625">│</span><span class="sxs-lookup"><span data-stu-id="de10e-625">│</span></span>                |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span data-ttu-id="de10e-626"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Marges de défilement</span><span class="sxs-lookup"><span data-stu-id="de10e-626"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scrolling Margins</span></span>


<span data-ttu-id="de10e-627">Les séquences suivantes permettent à un programme de configurer la « zone de défilement » de l’écran qui est affectée par les opérations de défilement.</span><span class="sxs-lookup"><span data-stu-id="de10e-627">The following sequences allow a program to configure the “scrolling region” of the screen that is affected by scrolling operations.</span></span> <span data-ttu-id="de10e-628">Il s’agit d’un sous-ensemble des lignes qui sont ajustées lorsque l’écran défilerait, par exemple, sur un' \\ n’ou un RI.</span><span class="sxs-lookup"><span data-stu-id="de10e-628">This is a subset of the rows that are adjusted when the screen would otherwise scroll, for example, on a ‘\\n’ or RI.</span></span> <span data-ttu-id="de10e-629">Ces marges affectent également les lignes modifiées par la ligne d’insertion (IL) et la ligne de suppression (DL), le défilement vers le haut (SU) et le défilement vers le haut (SD).</span><span class="sxs-lookup"><span data-stu-id="de10e-629">These margins also affect the rows modified by Insert Line (IL) and Delete Line (DL), Scroll Up (SU) and Scroll Down (SD).</span></span>

<span data-ttu-id="de10e-630">Les marges de défilement peuvent être particulièrement utiles pour disposer d’une partie de l’écran qui ne défile pas lorsque le reste de l’écran est rempli, par exemple avec une barre de titre en haut ou une barre d’État au bas de votre application.</span><span class="sxs-lookup"><span data-stu-id="de10e-630">The scrolling margins can be especially useful for having a portion of the screen that doesn’t scroll when the rest of the screen is filled, such as having a title bar at the top or a status bar at the bottom of your application.</span></span>

<span data-ttu-id="de10e-631">Pour DECSTBM, il existe deux paramètres facultatifs, &lt; t &gt; et &lt; b &gt; , qui sont utilisés pour spécifier les lignes qui représentent les lignes supérieure et inférieure de la zone de défilement, inclusivement.</span><span class="sxs-lookup"><span data-stu-id="de10e-631">For DECSTBM, there are two optional parameters, &lt;t&gt; and &lt;b&gt;, which are used to specify the rows that represent the top and bottom lines of the scroll region, inclusive.</span></span> <span data-ttu-id="de10e-632">Si les paramètres sont omis, &lt; t est &gt; défini par défaut sur 1 et &lt; b &gt; sur la hauteur de la fenêtre d’affichage actuelle.</span><span class="sxs-lookup"><span data-stu-id="de10e-632">If the parameters are omitted, &lt;t&gt; defaults to 1 and &lt;b&gt; defaults to the current viewport height.</span></span>

<span data-ttu-id="de10e-633">Les marges de défilement sont par mémoire tampon. il est donc important que l’autre mémoire tampon et la mémoire tampon principale maintiennent des paramètres de marges de défilement distincts (de sorte qu’une application en plein écran dans l’autre mémoire tampon n’incorrompra pas les marges de la mémoire tampon principale).</span><span class="sxs-lookup"><span data-stu-id="de10e-633">Scrolling margins are per-buffer, so importantly, the Alternate Buffer and Main Buffer maintain separate scrolling margins settings (so a full screen application in the alternate buffer will not poison the main buffer’s margins).</span></span>


| <span data-ttu-id="de10e-634">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-634">Sequence</span></span>                       | <span data-ttu-id="de10e-635">Code</span><span class="sxs-lookup"><span data-stu-id="de10e-635">Code</span></span>    | <span data-ttu-id="de10e-636">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-636">Description</span></span>          | <span data-ttu-id="de10e-637">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-637">Behavior</span></span>                                       |
|--------------------------------|---------|----------------------|------------------------------------------------|
| <span data-ttu-id="de10e-638">ESC \[ &lt; t &gt; ; &lt; b &gt; r</span><span class="sxs-lookup"><span data-stu-id="de10e-638">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span></span> | <span data-ttu-id="de10e-639">DECSTBM</span><span class="sxs-lookup"><span data-stu-id="de10e-639">DECSTBM</span></span> | <span data-ttu-id="de10e-640">Définir la zone de défilement</span><span class="sxs-lookup"><span data-stu-id="de10e-640">Set Scrolling Region</span></span> | <span data-ttu-id="de10e-641">Définit les marges de défilement VT de la fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="de10e-641">Sets the VT scrolling margins of the viewport.</span></span> |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span data-ttu-id="de10e-642"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Titre de la fenêtre</span><span class="sxs-lookup"><span data-stu-id="de10e-642"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Window Title</span></span>


<span data-ttu-id="de10e-643">Les commandes suivantes permettent à l’application de définir le titre de la fenêtre de console sur le &lt; paramètre de chaîne donné &gt; .</span><span class="sxs-lookup"><span data-stu-id="de10e-643">The following commands allows the application to set the title of the console window to the given &lt;string&gt; parameter.</span></span> <span data-ttu-id="de10e-644">La chaîne doit contenir moins de 255 caractères à accepter.</span><span class="sxs-lookup"><span data-stu-id="de10e-644">The string must be less than 255 characters to be accepted.</span></span> <span data-ttu-id="de10e-645">Cela équivaut à appeler SetConsoleTitle avec la chaîne donnée.</span><span class="sxs-lookup"><span data-stu-id="de10e-645">This is equivalent to calling SetConsoleTitle with the given string.</span></span>

<span data-ttu-id="de10e-646">Notez que ces séquences sont des séquences de « commande du système d’exploitation », et non d’un CSI comme nombre des autres séquences répertoriées. par conséquent, commence par « \\ X1B \] », et non pas par « \\ X1B \[ ».</span><span class="sxs-lookup"><span data-stu-id="de10e-646">Note that these sequences are OSC “Operating system command” sequences, and not a CSI like many of the other sequences listed, and as such starts with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="de10e-647">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-647">Sequence</span></span>                      | <span data-ttu-id="de10e-648">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-648">Description</span></span>               | <span data-ttu-id="de10e-649">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-649">Behavior</span></span>                                           |
|-------------------------------|---------------------------|----------------------------------------------------|
| <span data-ttu-id="de10e-650">ECHAP \] 0 ; &lt; chaîne &gt; bel</span><span class="sxs-lookup"><span data-stu-id="de10e-650">ESC \] 0 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="de10e-651">Définir l’icône et le titre de la fenêtre</span><span class="sxs-lookup"><span data-stu-id="de10e-651">Set Icon and Window Title</span></span> | <span data-ttu-id="de10e-652">Définit le titre de la fenêtre de la console sur &lt; String &gt; .</span><span class="sxs-lookup"><span data-stu-id="de10e-652">Sets the console window’s title to &lt;string&gt;.</span></span> |
| <span data-ttu-id="de10e-653">ESC \] 2 ; &lt; chaîne &gt; bel</span><span class="sxs-lookup"><span data-stu-id="de10e-653">ESC \] 2 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="de10e-654">Définir le titre de la fenêtre</span><span class="sxs-lookup"><span data-stu-id="de10e-654">Set Window Title</span></span>          | <span data-ttu-id="de10e-655">Définit le titre de la fenêtre de la console sur &lt; String &gt; .</span><span class="sxs-lookup"><span data-stu-id="de10e-655">Sets the console window’s title to &lt;string&gt;.</span></span> |



<span data-ttu-id="de10e-656">Le caractère de fin ici est le caractère « cloche », « \\ x07 »</span><span class="sxs-lookup"><span data-stu-id="de10e-656">The terminating character here is the “Bell” character, ‘\\x07’</span></span>

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span data-ttu-id="de10e-657"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Mémoire tampon d’écran de remplacement</span><span class="sxs-lookup"><span data-stu-id="de10e-657"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternate Screen Buffer</span></span>


<span data-ttu-id="de10e-658">\*Les applications de style nix utilisent souvent une mémoire tampon d’écran de remplacement, afin qu’elles puissent modifier l’ensemble du contenu de la mémoire tampon, sans affecter l’application qui les a démarrées.</span><span class="sxs-lookup"><span data-stu-id="de10e-658">\*Nix style applications often utilize an alternate screen buffer, so that they can modify the entire contents of the buffer, without affecting the application that started them.</span></span> <span data-ttu-id="de10e-659">La mémoire tampon de remplacement est exactement celle des dimensions de la fenêtre, sans aucune région scrollback.</span><span class="sxs-lookup"><span data-stu-id="de10e-659">The alternate buffer is exactly the dimensions of the window, without any scrollback region.</span></span>

<span data-ttu-id="de10e-660">Pour obtenir un exemple de ce comportement, pensez à la façon dont vim est lancé à partir de bash.</span><span class="sxs-lookup"><span data-stu-id="de10e-660">For an example of this behavior, consider when vim is launched from bash.</span></span> <span data-ttu-id="de10e-661">Vim utilise l’intégralité de l’écran pour modifier le fichier, puis le retour à bash laisse la mémoire tampon d’origine inchangée.</span><span class="sxs-lookup"><span data-stu-id="de10e-661">Vim uses the entirety of the screen to edit the file, then returning to bash leaves the original buffer unchanged.</span></span>


| <span data-ttu-id="de10e-662">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-662">Sequence</span></span>           | <span data-ttu-id="de10e-663">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-663">Description</span></span>                 | <span data-ttu-id="de10e-664">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-664">Behavior</span></span>                                   |
|--------------------|-----------------------------|--------------------------------------------|
| <span data-ttu-id="de10e-665">Échap \[ ?</span><span class="sxs-lookup"><span data-stu-id="de10e-665">ESC \[ ?</span></span> <span data-ttu-id="de10e-666">1 0 4 9 h</span><span class="sxs-lookup"><span data-stu-id="de10e-666">1 0 4 9 h</span></span> | <span data-ttu-id="de10e-667">Utiliser une autre mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="de10e-667">Use Alternate Screen Buffer</span></span> | <span data-ttu-id="de10e-668">Bascule vers une nouvelle mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="de10e-668">Switches to a new alternate screen buffer.</span></span> |
| <span data-ttu-id="de10e-669">Échap \[ ?</span><span class="sxs-lookup"><span data-stu-id="de10e-669">ESC \[ ?</span></span> <span data-ttu-id="de10e-670">1 0 4 9 l</span><span class="sxs-lookup"><span data-stu-id="de10e-670">1 0 4 9 l</span></span> | <span data-ttu-id="de10e-671">Utiliser la mémoire tampon de l’écran principal</span><span class="sxs-lookup"><span data-stu-id="de10e-671">Use Main Screen Buffer</span></span>      | <span data-ttu-id="de10e-672">Bascule vers la mémoire tampon principale.</span><span class="sxs-lookup"><span data-stu-id="de10e-672">Switches to the main buffer.</span></span>               |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span data-ttu-id="de10e-673"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Largeur de la fenêtre</span><span class="sxs-lookup"><span data-stu-id="de10e-673"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Window Width</span></span>


<span data-ttu-id="de10e-674">Les séquences suivantes peuvent être utilisées pour contrôler la largeur de la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="de10e-674">The following sequences can be used to control the width of the console window.</span></span> <span data-ttu-id="de10e-675">Ils sont à peu près équivalents à l’appel de l’API de la console SetConsoleScreenBufferInfoEx pour définir la largeur de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="de10e-675">They are roughly equivalent to the calling the SetConsoleScreenBufferInfoEx console API to set the window width.</span></span>


| <span data-ttu-id="de10e-676">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-676">Sequence</span></span>     | <span data-ttu-id="de10e-677">Code</span><span class="sxs-lookup"><span data-stu-id="de10e-677">Code</span></span>    | <span data-ttu-id="de10e-678">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-678">Description</span></span>                  | <span data-ttu-id="de10e-679">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-679">Behavior</span></span>                                    |
|--------------|---------|------------------------------|---------------------------------------------|
| <span data-ttu-id="de10e-680">Échap \[ ?</span><span class="sxs-lookup"><span data-stu-id="de10e-680">ESC \[ ?</span></span> <span data-ttu-id="de10e-681">3 h</span><span class="sxs-lookup"><span data-stu-id="de10e-681">3 h</span></span> | <span data-ttu-id="de10e-682">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="de10e-682">DECCOLM</span></span> | <span data-ttu-id="de10e-683">Définir le nombre de colonnes sur 132</span><span class="sxs-lookup"><span data-stu-id="de10e-683">Set Number of Columns to 132</span></span> | <span data-ttu-id="de10e-684">Définit la largeur de la console sur 132 colonnes en largeur.</span><span class="sxs-lookup"><span data-stu-id="de10e-684">Sets the console width to 132 columns wide.</span></span> |
| <span data-ttu-id="de10e-685">Échap \[ ?</span><span class="sxs-lookup"><span data-stu-id="de10e-685">ESC \[ ?</span></span> <span data-ttu-id="de10e-686">3 l</span><span class="sxs-lookup"><span data-stu-id="de10e-686">3 l</span></span> | <span data-ttu-id="de10e-687">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="de10e-687">DECCOLM</span></span> | <span data-ttu-id="de10e-688">Définir le nombre de colonnes sur 80</span><span class="sxs-lookup"><span data-stu-id="de10e-688">Set Number of Columns to 80</span></span>  | <span data-ttu-id="de10e-689">Définit la largeur de la console sur 80 colonnes en largeur.</span><span class="sxs-lookup"><span data-stu-id="de10e-689">Sets the console width to 80 columns wide.</span></span>  |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span data-ttu-id="de10e-690"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Réinitialisation logicielle</span><span class="sxs-lookup"><span data-stu-id="de10e-690"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Soft Reset</span></span>


<span data-ttu-id="de10e-691">La séquence suivante peut être utilisée pour réinitialiser certaines propriétés à leurs valeurs par défaut. Les propriétés suivantes sont réinitialisées aux valeurs par défaut suivantes (elles sont également répertoriées dans les séquences qui contrôlent ces propriétés) :</span><span class="sxs-lookup"><span data-stu-id="de10e-691">The following sequence can be used to reset certain properties to their default values.The following properties are reset to the following default values (also listed are the sequences that control those properties):</span></span>

- <span data-ttu-id="de10e-692">Visibilité du curseur : visible (DECTEM)</span><span class="sxs-lookup"><span data-stu-id="de10e-692">Cursor visibility: visible (DECTEM)</span></span>
- <span data-ttu-id="de10e-693">Pavé numérique : mode numérique (DECNKM)</span><span class="sxs-lookup"><span data-stu-id="de10e-693">Numeric Keypad: Numeric Mode (DECNKM)</span></span>
- <span data-ttu-id="de10e-694">Mode touches de curseur : mode normal (DECCKM)</span><span class="sxs-lookup"><span data-stu-id="de10e-694">Cursor Keys Mode: Normal Mode (DECCKM)</span></span>
- <span data-ttu-id="de10e-695">Marges supérieure et inférieure : haut = 1, bas = hauteur de la console (DECSTBM)</span><span class="sxs-lookup"><span data-stu-id="de10e-695">Top and Bottom Margins: Top=1, Bottom=Console height (DECSTBM)</span></span>
- <span data-ttu-id="de10e-696">Jeu de caractères : ASCII US</span><span class="sxs-lookup"><span data-stu-id="de10e-696">Character Set: US ASCII</span></span>
- <span data-ttu-id="de10e-697">Rendu graphique : par défaut/désactivé (SGR)</span><span class="sxs-lookup"><span data-stu-id="de10e-697">Graphics Rendition: Default/Off (SGR)</span></span>
- <span data-ttu-id="de10e-698">Enregistrer l’état du curseur : position de départ (0, 0) (DECSC)</span><span class="sxs-lookup"><span data-stu-id="de10e-698">Save cursor state: Home position (0,0) (DECSC)</span></span>


| <span data-ttu-id="de10e-699">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-699">Sequence</span></span>   | <span data-ttu-id="de10e-700">Code</span><span class="sxs-lookup"><span data-stu-id="de10e-700">Code</span></span>   | <span data-ttu-id="de10e-701">Description</span><span class="sxs-lookup"><span data-stu-id="de10e-701">Description</span></span> | <span data-ttu-id="de10e-702">Comportement</span><span class="sxs-lookup"><span data-stu-id="de10e-702">Behavior</span></span>                                           |
|------------|--------|-------------|----------------------------------------------------|
| <span data-ttu-id="de10e-703">Échap \[ !</span><span class="sxs-lookup"><span data-stu-id="de10e-703">ESC \[ !</span></span> <span data-ttu-id="de10e-704">p</span><span class="sxs-lookup"><span data-stu-id="de10e-704">p</span></span> | <span data-ttu-id="de10e-705">DECSTR</span><span class="sxs-lookup"><span data-stu-id="de10e-705">DECSTR</span></span> | <span data-ttu-id="de10e-706">Réinitialisation logicielle</span><span class="sxs-lookup"><span data-stu-id="de10e-706">Soft Reset</span></span>  | <span data-ttu-id="de10e-707">Réinitialiser certains paramètres de terminal à leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="de10e-707">Reset certain terminal settings to their defaults.</span></span> |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span data-ttu-id="de10e-708"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Séquences d’entrée</span><span class="sxs-lookup"><span data-stu-id="de10e-708"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Input Sequences</span></span>


<span data-ttu-id="de10e-709">Les séquences de terminaux suivantes sont émises par l’hôte de la console sur le flux d’entrée si l' \_ \_ indicateur d’entrée activer le terminal virtuel \_ est défini sur le descripteur de la mémoire tampon d’entrée à l’aide de l’indicateur SetConsoleMode.</span><span class="sxs-lookup"><span data-stu-id="de10e-709">The following terminal sequences are emitted by the console host on the input stream if the ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag is set on the input buffer handle using the SetConsoleMode flag.</span></span>

<span data-ttu-id="de10e-710">Il existe deux modes internes qui contrôlent les séquences émises pour les touches d’entrée données, le mode des touches de curseur et le mode touches du pavé numérique.</span><span class="sxs-lookup"><span data-stu-id="de10e-710">There are two internal modes that control which sequences are emitted for the given input keys, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="de10e-711">Celles-ci sont décrites dans la section modifications de mode.</span><span class="sxs-lookup"><span data-stu-id="de10e-711">These are described in the Mode Changes section.</span></span>

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span data-ttu-id="de10e-712"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Touches de curseur</span><span class="sxs-lookup"><span data-stu-id="de10e-712"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Cursor Keys</span></span>


| <span data-ttu-id="de10e-713">Clé</span><span class="sxs-lookup"><span data-stu-id="de10e-713">Key</span></span>         | <span data-ttu-id="de10e-714">Mode Normal</span><span class="sxs-lookup"><span data-stu-id="de10e-714">Normal Mode</span></span> | <span data-ttu-id="de10e-715">Mode d’application</span><span class="sxs-lookup"><span data-stu-id="de10e-715">Application Mode</span></span> |
|-------------|-------------|------------------|
| <span data-ttu-id="de10e-716">Flèche haut</span><span class="sxs-lookup"><span data-stu-id="de10e-716">Up Arrow</span></span>    | <span data-ttu-id="de10e-717">Échap \[ A</span><span class="sxs-lookup"><span data-stu-id="de10e-717">ESC \[ A</span></span>    | <span data-ttu-id="de10e-718">ECHAP O A</span><span class="sxs-lookup"><span data-stu-id="de10e-718">ESC O A</span></span>          |
| <span data-ttu-id="de10e-719">Flèche Bas</span><span class="sxs-lookup"><span data-stu-id="de10e-719">Down Arrow</span></span>  | <span data-ttu-id="de10e-720">ESC \[ B</span><span class="sxs-lookup"><span data-stu-id="de10e-720">ESC \[ B</span></span>    | <span data-ttu-id="de10e-721">ECHAP O B</span><span class="sxs-lookup"><span data-stu-id="de10e-721">ESC O B</span></span>          |
| <span data-ttu-id="de10e-722">Flèche droite</span><span class="sxs-lookup"><span data-stu-id="de10e-722">Right Arrow</span></span> | <span data-ttu-id="de10e-723">ESC \[ C</span><span class="sxs-lookup"><span data-stu-id="de10e-723">ESC \[ C</span></span>    | <span data-ttu-id="de10e-724">ECHAP O C</span><span class="sxs-lookup"><span data-stu-id="de10e-724">ESC O C</span></span>          |
| <span data-ttu-id="de10e-725">Gauche</span><span class="sxs-lookup"><span data-stu-id="de10e-725">Left Arrow</span></span>  | <span data-ttu-id="de10e-726">ECHAP \[ D</span><span class="sxs-lookup"><span data-stu-id="de10e-726">ESC \[ D</span></span>    | <span data-ttu-id="de10e-727">ECHAP O D</span><span class="sxs-lookup"><span data-stu-id="de10e-727">ESC O D</span></span>          |
| <span data-ttu-id="de10e-728">Accueil</span><span class="sxs-lookup"><span data-stu-id="de10e-728">Home</span></span>        | <span data-ttu-id="de10e-729">ESC \[ H</span><span class="sxs-lookup"><span data-stu-id="de10e-729">ESC \[ H</span></span>    | <span data-ttu-id="de10e-730">ECHAP O H</span><span class="sxs-lookup"><span data-stu-id="de10e-730">ESC O H</span></span>          |
| <span data-ttu-id="de10e-731">End</span><span class="sxs-lookup"><span data-stu-id="de10e-731">End</span></span>         | <span data-ttu-id="de10e-732">ESC \[ F</span><span class="sxs-lookup"><span data-stu-id="de10e-732">ESC \[ F</span></span>    | <span data-ttu-id="de10e-733">ECHAP O F</span><span class="sxs-lookup"><span data-stu-id="de10e-733">ESC O F</span></span>          |



<span data-ttu-id="de10e-734">En outre, si la touche CTRL est enfoncée avec l’une de ces clés, les séquences suivantes sont émises à la place, quel que soit le mode des touches de curseur :</span><span class="sxs-lookup"><span data-stu-id="de10e-734">Additionally, if Ctrl is pressed with any of these keys, the following sequences are emitted instead, regardless of the Cursor Keys Mode:</span></span>


| <span data-ttu-id="de10e-735">Clé</span><span class="sxs-lookup"><span data-stu-id="de10e-735">Key</span></span>                | <span data-ttu-id="de10e-736">N’importe quel mode</span><span class="sxs-lookup"><span data-stu-id="de10e-736">Any Mode</span></span>       |
|--------------------|----------------|
| <span data-ttu-id="de10e-737">Ctrl + flèche haut</span><span class="sxs-lookup"><span data-stu-id="de10e-737">Ctrl + Up Arrow</span></span>    | <span data-ttu-id="de10e-738">ESC \[ 1 ; 5 A</span><span class="sxs-lookup"><span data-stu-id="de10e-738">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="de10e-739">Ctrl + flèche bas</span><span class="sxs-lookup"><span data-stu-id="de10e-739">Ctrl + Down Arrow</span></span>  | <span data-ttu-id="de10e-740">ESC \[ 1 ; 5 B</span><span class="sxs-lookup"><span data-stu-id="de10e-740">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="de10e-741">Ctrl + flèche droite</span><span class="sxs-lookup"><span data-stu-id="de10e-741">Ctrl + Right Arrow</span></span> | <span data-ttu-id="de10e-742">ESC \[ 1 ; 5 C</span><span class="sxs-lookup"><span data-stu-id="de10e-742">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="de10e-743">Ctrl + flèche gauche</span><span class="sxs-lookup"><span data-stu-id="de10e-743">Ctrl + Left Arrow</span></span>  | <span data-ttu-id="de10e-744">ESC \[ 1 ; 5 D</span><span class="sxs-lookup"><span data-stu-id="de10e-744">ESC \[ 1 ; 5 D</span></span> |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span data-ttu-id="de10e-745"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Touches de fonction & pavé numérique</span><span class="sxs-lookup"><span data-stu-id="de10e-745"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad & Function Keys</span></span>


| <span data-ttu-id="de10e-746">Clé</span><span class="sxs-lookup"><span data-stu-id="de10e-746">Key</span></span>       | <span data-ttu-id="de10e-747">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-747">Sequence</span></span>     |
|-----------|--------------|
| <span data-ttu-id="de10e-748">Retour arrière</span><span class="sxs-lookup"><span data-stu-id="de10e-748">Backspace</span></span> | <span data-ttu-id="de10e-749">0x7F (DEL)</span><span class="sxs-lookup"><span data-stu-id="de10e-749">0x7f (DEL)</span></span>   |
| <span data-ttu-id="de10e-750">Suspendre</span><span class="sxs-lookup"><span data-stu-id="de10e-750">Pause</span></span>     | <span data-ttu-id="de10e-751">0x1A (SUB)</span><span class="sxs-lookup"><span data-stu-id="de10e-751">0x1a (SUB)</span></span>   |
| <span data-ttu-id="de10e-752">Caractère d'échappement</span><span class="sxs-lookup"><span data-stu-id="de10e-752">Escape</span></span>    | <span data-ttu-id="de10e-753">0x1B (ESC)</span><span class="sxs-lookup"><span data-stu-id="de10e-753">0x1b (ESC)</span></span>   |
| <span data-ttu-id="de10e-754">Insérer</span><span class="sxs-lookup"><span data-stu-id="de10e-754">Insert</span></span>    | <span data-ttu-id="de10e-755">ESC \[ 2 ~</span><span class="sxs-lookup"><span data-stu-id="de10e-755">ESC \[ 2 ~</span></span>   |
| <span data-ttu-id="de10e-756">Supprimer</span><span class="sxs-lookup"><span data-stu-id="de10e-756">Delete</span></span>    | <span data-ttu-id="de10e-757">ESC \[ 3 ~</span><span class="sxs-lookup"><span data-stu-id="de10e-757">ESC \[ 3 ~</span></span>   |
| <span data-ttu-id="de10e-758">Page précédente</span><span class="sxs-lookup"><span data-stu-id="de10e-758">Page Up</span></span>   | <span data-ttu-id="de10e-759">ESC \[ 5 ~</span><span class="sxs-lookup"><span data-stu-id="de10e-759">ESC \[ 5 ~</span></span>   |
| <span data-ttu-id="de10e-760">Page suivante</span><span class="sxs-lookup"><span data-stu-id="de10e-760">Page Down</span></span> | <span data-ttu-id="de10e-761">ESC \[ 6 ~</span><span class="sxs-lookup"><span data-stu-id="de10e-761">ESC \[ 6 ~</span></span>   |
| <span data-ttu-id="de10e-762">F1</span><span class="sxs-lookup"><span data-stu-id="de10e-762">F1</span></span>        | <span data-ttu-id="de10e-763">ECHAP O P</span><span class="sxs-lookup"><span data-stu-id="de10e-763">ESC O P</span></span>      |
| <span data-ttu-id="de10e-764">F2</span><span class="sxs-lookup"><span data-stu-id="de10e-764">F2</span></span>        | <span data-ttu-id="de10e-765">ECHAP O Q</span><span class="sxs-lookup"><span data-stu-id="de10e-765">ESC O Q</span></span>      |
| <span data-ttu-id="de10e-766">F3</span><span class="sxs-lookup"><span data-stu-id="de10e-766">F3</span></span>        | <span data-ttu-id="de10e-767">ECHAP O R</span><span class="sxs-lookup"><span data-stu-id="de10e-767">ESC O R</span></span>      |
| <span data-ttu-id="de10e-768">F4</span><span class="sxs-lookup"><span data-stu-id="de10e-768">F4</span></span>        | <span data-ttu-id="de10e-769">ECHAP O S</span><span class="sxs-lookup"><span data-stu-id="de10e-769">ESC O S</span></span>      |
| <span data-ttu-id="de10e-770">F5</span><span class="sxs-lookup"><span data-stu-id="de10e-770">F5</span></span>        | <span data-ttu-id="de10e-771">ECHAP \[ 1 5 ~</span><span class="sxs-lookup"><span data-stu-id="de10e-771">ESC \[ 1 5 ~</span></span> |
| <span data-ttu-id="de10e-772">F6</span><span class="sxs-lookup"><span data-stu-id="de10e-772">F6</span></span>        | <span data-ttu-id="de10e-773">ECHAP \[ 1 7 ~</span><span class="sxs-lookup"><span data-stu-id="de10e-773">ESC \[ 1 7 ~</span></span> |
| <span data-ttu-id="de10e-774">F7</span><span class="sxs-lookup"><span data-stu-id="de10e-774">F7</span></span>        | <span data-ttu-id="de10e-775">ECHAP \[ 1 8 ~</span><span class="sxs-lookup"><span data-stu-id="de10e-775">ESC \[ 1 8 ~</span></span> |
| <span data-ttu-id="de10e-776">F8</span><span class="sxs-lookup"><span data-stu-id="de10e-776">F8</span></span>        | <span data-ttu-id="de10e-777">ECHAP \[ 1 9 ~</span><span class="sxs-lookup"><span data-stu-id="de10e-777">ESC \[ 1 9 ~</span></span> |
| <span data-ttu-id="de10e-778">F9</span><span class="sxs-lookup"><span data-stu-id="de10e-778">F9</span></span>        | <span data-ttu-id="de10e-779">ECHAP \[ 2 0 ~</span><span class="sxs-lookup"><span data-stu-id="de10e-779">ESC \[ 2 0 ~</span></span> |
| <span data-ttu-id="de10e-780">F10</span><span class="sxs-lookup"><span data-stu-id="de10e-780">F10</span></span>       | <span data-ttu-id="de10e-781">ECHAP \[ 2 1 ~</span><span class="sxs-lookup"><span data-stu-id="de10e-781">ESC \[ 2 1 ~</span></span> |
| <span data-ttu-id="de10e-782">F11</span><span class="sxs-lookup"><span data-stu-id="de10e-782">F11</span></span>       | <span data-ttu-id="de10e-783">ECHAP \[ 2 3 ~</span><span class="sxs-lookup"><span data-stu-id="de10e-783">ESC \[ 2 3 ~</span></span> |
| <span data-ttu-id="de10e-784">F12</span><span class="sxs-lookup"><span data-stu-id="de10e-784">F12</span></span>       | <span data-ttu-id="de10e-785">ECHAP \[ 2 4 ~</span><span class="sxs-lookup"><span data-stu-id="de10e-785">ESC \[ 2 4 ~</span></span> |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span data-ttu-id="de10e-786"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modificateurs</span><span class="sxs-lookup"><span data-stu-id="de10e-786"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifiers</span></span>

<span data-ttu-id="de10e-787">La touche Alt est traitée en préfixant la séquence par un caractère d’échappement : Échap &lt; c &gt; où &lt; c &gt; est le caractère passé par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="de10e-787">Alt is treated by prefixing the sequence with an escape: ESC &lt;c&gt; where &lt;c&gt; is the character passed by the operating system.</span></span> <span data-ttu-id="de10e-788">ALT + CTRL est gérée de la même façon, à ceci près que le système d’exploitation aura au préalable déplacé la &lt; &gt; clé c vers le caractère de contrôle approprié, qui sera relayé à l’application.</span><span class="sxs-lookup"><span data-stu-id="de10e-788">Alt+Ctrl is handled the same way except that the operating system will have pre-shifted the &lt;c&gt; key to the appropriate control character which will be relayed to the application.</span></span>

<span data-ttu-id="de10e-789">La touche CTRL est généralement transmise à partir du système.</span><span class="sxs-lookup"><span data-stu-id="de10e-789">Ctrl is generally passed through exactly as received from the system.</span></span> <span data-ttu-id="de10e-790">Il s’agit généralement d’un caractère unique déplacé vers le bout dans l’espace réservé du caractère de contrôle (0x0-0x1F).</span><span class="sxs-lookup"><span data-stu-id="de10e-790">This is typically a single character shifted down into the control character reserved space (0x0-0x1f).</span></span> <span data-ttu-id="de10e-791">Par exemple, Ctrl + @ (0x40) devient NUL (0x00), CTRL + \[ (0x5B) devient ESC (0x1B), etc. Quelques combinaisons de touches Ctrl sont traitées de façon spéciale selon le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="de10e-791">For example, Ctrl+@ (0x40) becomes NUL (0x00), Ctrl+\[ (0x5b) becomes ESC (0x1b), etc. A few Ctrl key combinations are treated specially according to the following table:</span></span>


| <span data-ttu-id="de10e-792">Clé</span><span class="sxs-lookup"><span data-stu-id="de10e-792">Key</span></span>                | <span data-ttu-id="de10e-793">Séquence</span><span class="sxs-lookup"><span data-stu-id="de10e-793">Sequence</span></span>       |
|--------------------|----------------|
| <span data-ttu-id="de10e-794">Ctrl + espace</span><span class="sxs-lookup"><span data-stu-id="de10e-794">Ctrl + Space</span></span>       | <span data-ttu-id="de10e-795">0x00 (NUL)</span><span class="sxs-lookup"><span data-stu-id="de10e-795">0x00 (NUL)</span></span>     |
| <span data-ttu-id="de10e-796">Ctrl + flèche haut</span><span class="sxs-lookup"><span data-stu-id="de10e-796">Ctrl + Up Arrow</span></span>    | <span data-ttu-id="de10e-797">ESC \[ 1 ; 5 A</span><span class="sxs-lookup"><span data-stu-id="de10e-797">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="de10e-798">Ctrl + flèche bas</span><span class="sxs-lookup"><span data-stu-id="de10e-798">Ctrl + Down Arrow</span></span>  | <span data-ttu-id="de10e-799">ESC \[ 1 ; 5 B</span><span class="sxs-lookup"><span data-stu-id="de10e-799">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="de10e-800">Ctrl + flèche droite</span><span class="sxs-lookup"><span data-stu-id="de10e-800">Ctrl + Right Arrow</span></span> | <span data-ttu-id="de10e-801">ESC \[ 1 ; 5 C</span><span class="sxs-lookup"><span data-stu-id="de10e-801">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="de10e-802">Ctrl + flèche gauche</span><span class="sxs-lookup"><span data-stu-id="de10e-802">Ctrl + Left Arrow</span></span>  | <span data-ttu-id="de10e-803">ESC \[ 1 ; 5 D</span><span class="sxs-lookup"><span data-stu-id="de10e-803">ESC \[ 1 ; 5 D</span></span> |



<span data-ttu-id="de10e-804">**Remarque**  CTRL gauche + droite Alt est traité comme AltGr.</span><span class="sxs-lookup"><span data-stu-id="de10e-804">**Note**  Left Ctrl + Right Alt is treated as AltGr.</span></span> <span data-ttu-id="de10e-805">Lorsqu’ils sont affichés ensemble, ils sont supprimés et la valeur Unicode du caractère présenté par le système est transmise à la cible.</span><span class="sxs-lookup"><span data-stu-id="de10e-805">When both are seen together, they will be stripped and the Unicode value of the character presented by the system will be passed into the target.</span></span> <span data-ttu-id="de10e-806">Le système convertit les valeurs AltGr en fonction des paramètres d’entrée système actuels.</span><span class="sxs-lookup"><span data-stu-id="de10e-806">The system will pre-translate AltGr values according to the current system input settings.</span></span>



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span data-ttu-id="de10e-807"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Extraits</span><span class="sxs-lookup"><span data-stu-id="de10e-807"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Samples</span></span>


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span data-ttu-id="de10e-808"><span id="example"></span><span id="EXAMPLE"></span>Exemple de séquences de terminaux SGR</span><span class="sxs-lookup"><span data-stu-id="de10e-808"><span id="example"></span><span id="EXAMPLE"></span>Example of SGR terminal sequences</span></span>

<span data-ttu-id="de10e-809">Le code suivant fournit plusieurs exemples de mise en forme du texte.</span><span class="sxs-lookup"><span data-stu-id="de10e-809">The following code provides several examples of text formatting.</span></span>

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

<span data-ttu-id="de10e-810">**Remarque**  Dans l’exemple précédent, la chaîne' `\x1b[31m` 'correspond à l’implémentation de **ESC \[ &lt; n &gt; m** avec &lt; n &gt; étant 31.</span><span class="sxs-lookup"><span data-stu-id="de10e-810">**Note**  In the previous example, the string '`\x1b[31m`' is the implementation of **ESC \[ &lt;n&gt; m** with &lt;n&gt; being 31.</span></span>



<span data-ttu-id="de10e-811">Le graphique suivant montre la sortie de l’exemple de code précédent.</span><span class="sxs-lookup"><span data-stu-id="de10e-811">The following graphic shows the output of the previous code example.</span></span>

![sortie de la console à l’aide de la commande SGR](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span data-ttu-id="de10e-813"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Exemple d’activation du traitement des terminaux virtuels</span><span class="sxs-lookup"><span data-stu-id="de10e-813"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Example of Enabling Virtual Terminal Processing</span></span>

<span data-ttu-id="de10e-814">Le code suivant fournit un exemple de la méthode recommandée pour activer le traitement des terminaux virtuels pour une application.</span><span class="sxs-lookup"><span data-stu-id="de10e-814">The following code provides an example of the recommended way to enable virtual terminal processing for an application.</span></span> <span data-ttu-id="de10e-815">L’objectif de l’exemple est de démontrer les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="de10e-815">The intent of the sample is to demonstrate:</span></span>

1. <span data-ttu-id="de10e-816">Le mode existant doit toujours être récupéré via GetConsoleMode et analysé avant d’être défini avec SetConsoleMode.</span><span class="sxs-lookup"><span data-stu-id="de10e-816">The existing mode should always be retrieved via GetConsoleMode and analyzed before being set with SetConsoleMode.</span></span>

2. <span data-ttu-id="de10e-817">Vérification de la valeur retournée `0` par SetConsoleMode et GetLastError retourne \_ le paramètre de l’état non valide \_ est le mécanisme actuel à déterminer lors de l’exécution sur un système de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="de10e-817">Checking whether SetConsoleMode returns `0` and GetLastError returns STATUS\_INVALID\_PARAMETER is the current mechanism to determine when running on a down-level system.</span></span> <span data-ttu-id="de10e-818">Une application recevant un paramètre d’état \_ non valide \_ avec l’un des nouveaux indicateurs de mode de console dans le champ de bits doit dégrader le comportement de manière appropriée, puis réessayer.</span><span class="sxs-lookup"><span data-stu-id="de10e-818">An application receiving STATUS\_INVALID\_PARAMETER with one of the newer console mode flags in the bit field should gracefully degrade behavior and try again.</span></span>

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

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span data-ttu-id="de10e-819"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Exemple de sélection de fonctionnalités de mise à jour anniversaire</span><span class="sxs-lookup"><span data-stu-id="de10e-819"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Example of Select Anniversary Update Features</span></span>

<span data-ttu-id="de10e-820">L’exemple suivant est destiné à être un exemple plus robuste de code utilisant une variété de séquences d’échappement pour manipuler la mémoire tampon, en mettant l’accent sur les fonctionnalités ajoutées dans la mise à jour anniversaire pour Windows 10.</span><span class="sxs-lookup"><span data-stu-id="de10e-820">The following example is intended to be a more robust example of code using a variety of escape sequences to manipulate the buffer, with an emphasis on the features added in the Anniversary Update for Windows 10.</span></span>

<span data-ttu-id="de10e-821">Cet exemple utilise l’autre mémoire tampon d’écran, la manipulation des taquets de tabulation, la définition des marges de défilement et la modification du jeu de caractères.</span><span class="sxs-lookup"><span data-stu-id="de10e-821">This example makes use of the alternate screen buffer, manipulating tab stops, setting scrolling margins, and changing the character set.</span></span>

```C
//
//    Copyright (C) Microsoft.  All rights reserved.
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
    printf(ESC "(0");       // Enter Line drawing mode
    printf(CSI "104;93m");   // bright yellow on bright blue
    printf("x");            // in line drawing mode, \x78 -> \u2502 "Vertical Bar"
    printf(CSI "0m");       // restore color
    printf(ESC "(B");       // exit line drawing mode
}

void PrintHorizontalBorder(COORD const Size, bool fIsTop)
{
    printf(ESC "(0");       // Enter Line drawing mode
    printf(CSI "104;93m");  // Make the border bright yellow on bright blue
    printf(fIsTop? "l" : "m"); // print left corner 

    for (int i = 1; i < Size.X - 1; i++) 
        printf("q"); // in line drawing mode, \x71 -> \u2500 "HORIZONTAL SCAN LINE-5"

    printf(fIsTop? "k" : "j"); // print right corner
    printf(CSI "0m");
    printf(ESC "(B");       // exit line drawing mode
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
    Size.Y = ScreenBufferInfo.srWindow.Bottom -  ScreenBufferInfo.srWindow.Top + 1;

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








