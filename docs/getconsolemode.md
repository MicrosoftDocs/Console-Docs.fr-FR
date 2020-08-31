---
title: GetConsoleMode fonction)
description: Récupère le mode de saisie actuel de la mémoire tampon d’entrée d’une console ou le mode de sortie actuel d’une mémoire tampon d’écran de la console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- consoleapi/GetConsoleMode
- wincon/GetConsoleMode
- GetConsoleMode
MS-HAID:
- '\_win32\_getconsolemode'
- base.getconsolemode
- consoles.getconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 49adf618-196d-4490-93ca-cd177807f58e
topic_type:
- apiref
api_name:
- GetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a2d18ed191d1d82cc54c3277aa38badb0aedb630
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059140"
---
# <a name="getconsolemode-function"></a>GetConsoleMode fonction)


Récupère le mode de saisie actuel de la mémoire tampon d’entrée d’une console ou le mode de sortie actuel d’une mémoire tampon d’écran de la console.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI GetConsoleMode(
  _In_  HANDLE  hConsoleHandle,
  _Out_ LPDWORD lpMode
);
```

<a name="parameters"></a>Paramètres
----------

*hConsoleHandle* \[ dans\]  
Handle vers la mémoire tampon d’entrée de la console ou la mémoire tampon d’écran de la console. Le handle doit avoir le droit d’accès ** \_ en lecture générique** . Pour plus d’informations, consultez sécurité de la [mémoire tampon de la console et droits d’accès](console-buffer-security-and-access-rights.md).

*lpMode* \[ à\]  
Pointeur vers une variable qui reçoit le mode actuel de la mémoire tampon spécifiée.

Si le paramètre *hConsoleHandle* est un handle d’entrée, le mode peut être une ou plusieurs des valeurs suivantes. Quand une console est créée, tous les modes d’entrée à l’exception de l’option **activer l' \_ \_ entrée de fenêtre** sont activés par défaut.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Value</th>
<th>Signification</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="ENABLE_ECHO_INPUT"></span><span id="enable_echo_input"></span>
<strong>ENABLE_ECHO_INPUT</strong> 0x0004</td>
<td><p>Les caractères lus par la fonction <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> ou <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> sont écrits dans la mémoire tampon d’écran active au fur et à mesure de leur lecture. Ce mode peut être utilisé uniquement si le mode de <strong>ENABLE_LINE_INPUT</strong> est également activé.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_INSERT_MODE"></span><span id="enable_insert_mode"></span>
<strong>ENABLE_INSERT_MODE</strong> 0x0020</td>
<td><p>Lorsque cette option est activée, le texte entré dans une fenêtre de console est inséré à l’emplacement du curseur actuel et tout le texte qui suit cet emplacement n’est pas remplacé. Quand elle est désactivée, tout le texte suivant est remplacé.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_LINE_INPUT"></span><span id="enable_line_input"></span>
<strong>ENABLE_LINE_INPUT</strong> 0x0002</td>
<td><p>La fonction <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> ou <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> retourne uniquement lorsqu’un caractère de retour chariot est lu. Si ce mode est désactivé, les fonctions retournent lorsqu’un ou plusieurs caractères sont disponibles.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_MOUSE_INPUT"></span><span id="enable_mouse_input"></span>
<strong>ENABLE_MOUSE_INPUT</strong> 0x0010</td>
<td><p>Si le pointeur de la souris se trouve dans les limites de la fenêtre de console et que la fenêtre a le focus clavier, les événements de souris générés par le déplacement de la souris et les enfoncements de bouton sont placés dans la mémoire tampon d’entrée. Ces événements sont ignorés par <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> ou <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, même quand ce mode est activé.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_PROCESSED_INPUT"></span><span id="enable_processed_input"></span>
<strong>ENABLE_PROCESSED_INPUT</strong> 0x0001</td>
<td><p>CTRL + C est traité par le système et n’est pas placé dans la mémoire tampon d’entrée. Si la mémoire tampon d’entrée est lue par <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> ou <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, d’autres clés de contrôle sont traitées par le système et ne sont pas retournées dans la mémoire tampon <strong>ReadFile</strong> ou <strong>ReadConsole</strong> . Si le mode de <strong>ENABLE_LINE_INPUT</strong> est également activé, les caractères de retour arrière, de retour chariot et de saut de ligne sont gérés par le système.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_QUICK_EDIT_MODE"></span><span id="enable_quick_edit_mode"></span>
<strong>ENABLE_QUICK_EDIT_MODE</strong> 0x0040</td>
<td><p>Cet indicateur permet à l’utilisateur de sélectionner et de modifier du texte à l’aide de la souris.</p>
<p>Pour activer ce mode, utilisez <code>ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS</code> . Pour désactiver ce mode, utilisez <strong>ENABLE_EXTENDED_FLAGS</strong> sans cet indicateur.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_WINDOW_INPUT"></span><span id="enable_window_input"></span>
<strong>ENABLE_WINDOW_INPUT</strong> 0x0008</td>
<td><p>Les interactions utilisateur qui modifient la taille de la mémoire tampon de l’écran de la console sont signalées dans la mémoire tampon d’entrée de la console&#39;s. Les informations relatives à ces événements peuvent être lues à partir de la mémoire tampon d’entrée par les applications à l’aide de la fonction <a href="readconsoleinput.md" data-raw-source="[&lt;strong&gt;ReadConsoleInput&lt;/strong&gt;](readconsoleinput.md)"><strong>ReadConsoleInput</strong></a> , mais pas par celles utilisant <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> ou <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_VIRTUAL_TERMINAL_INPUT"></span><span id="enable_virtual_terminal_input"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_INPUT</strong> 0x0200</td>
<td><p>La définition de cet indicateur indique au moteur de traitement des terminaux virtuels de convertir les entrées utilisateur reçues par la fenêtre de console en <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">séquences de terminaux virtuels de la console</a> qui peuvent être récupérées par une application de prise en charge via les fonctions <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> ou <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> .</p>
<p>L’utilisation classique de cet indicateur est conçue conjointement avec ENABLE_VIRTUAL_TERMINAL_PROCESSING sur le handle de sortie pour se connecter à une application qui communique exclusivement par le biais de séquences de terminaux virtuels.</p></td>
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

 

Si le paramètre *hConsoleHandle* est un descripteur de mémoire tampon d’écran, le mode peut être une ou plusieurs des valeurs suivantes. Quand une mémoire tampon d’écran est créée, les deux modes de sortie sont activés par défaut.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Value</th>
<th>Signification</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="ENABLE_PROCESSED_OUTPUT"></span><span id="enable_processed_output"></span>
<strong>ENABLE_PROCESSED_OUTPUT</strong> 0x0001</td>
<td><p>Les caractères écrits par la fonction <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> ou <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> ou répercutés par la fonction <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> ou <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> sont analysés pour les séquences de contrôle ASCII, et l’action correcte est effectuée. Les caractères retour arrière, tabulation, cloche, retour chariot et saut de ligne sont traités.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_WRAP_AT_EOL_OUTPUT"></span><span id="enable_wrap_at_eol_output"></span>
<strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong> 0x0002</td>
<td><p>Lors de l’écriture avec <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> ou <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> ou l’écho avec <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> ou <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, le curseur se déplace au début de la ligne suivante lorsqu’il atteint la fin de la ligne actuelle. Cela entraîne le défilement automatique des lignes affichées dans la fenêtre de la console lorsque le curseur avance au-delà de la dernière ligne de la fenêtre. Cela permet également de faire défiler le contenu de la mémoire tampon d’écran de la console vers le haut (en ignorant la ligne supérieure de la mémoire tampon d’écran de la console) lorsque le curseur avance au-delà de la dernière ligne dans la mémoire tampon de l’écran de la console. Si ce mode est désactivé, le dernier caractère de la ligne est remplacé par les caractères suivants.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_VIRTUAL_TERMINAL_PROCESSING"></span><span id="enable_virtual_terminal_processing"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_PROCESSING</strong> 0x0004</td>
<td><p>Lors de l’écriture avec <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> ou <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, les caractères sont analysés pour VT100 et les séquences de caractères de contrôle similaires qui contrôlent le mouvement du curseur, le mode couleur/police et d’autres opérations qui peuvent également être effectuées via les API de console existantes. Pour plus d’informations, consultez <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">séquences de terminaux virtuels de la console</a>.</p></td>
</tr>
<tr class="even">
<td><span id="DISABLE_NEWLINE_AUTO_RETURN"></span><span id="disable_newline_auto_return"></span>
<strong>DISABLE_NEWLINE_AUTO_RETURN</strong> 0x0008</td>
<td><p>Lors de l’écriture avec <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> ou <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, cela ajoute un État supplémentaire à l’encapsulation de fin de ligne qui peut retarder le déplacement du curseur et les opérations de défilement de la mémoire tampon.</p>
<p>Normalement, lorsque ENABLE_WRAP_AT_EOL_OUTPUT est définie et que le texte atteint la fin de la ligne, le curseur passe immédiatement à la ligne suivante et le contenu de la mémoire tampon défile d’une ligne vers le haut. Contrairement à cet indicateur, l’opération de défilement et le déplacement de curseur sont retardés jusqu’à ce que le caractère suivant arrive. Le caractère écrit est imprimé à la position finale sur la ligne et le curseur se trouve au-dessus de ce caractère comme si ENABLE_WRAP_AT_EOL_OUTPUT était désactivé, mais le prochain caractère imprimable sera imprimé comme si ENABLE_WRAP_AT_EOL_OUTPUT était activé. Aucun remplacement ne se produit. Plus précisément, le curseur avance rapidement jusqu’à la ligne suivante, un défilement est effectué si nécessaire, le caractère est imprimé et le curseur avance d’une position.</p>
<p>L’utilisation classique de cet indicateur est conçue conjointement avec la définition de ENABLE_VIRTUAL_TERMINAL_PROCESSING pour mieux émuler un émulateur de terminal dans lequel l’écriture du dernier caractère sur l’écran (dans le coin inférieur droit) sans déclencher de défilement immédiat est le comportement souhaité.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_LVB_GRID_WORLDWIDE"></span><span id="enable_lvb_grid_worldwide"></span>
<strong>ENABLE_LVB_GRID_WORLDWIDE</strong> 0x0010</td>
<td><p>Les API permettant d’écrire des attributs de caractères, y compris <a href="writeconsoleoutput.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutput&lt;/strong&gt;](writeconsoleoutput.md)"><strong>WriteConsoleOutput</strong></a> et <a href="writeconsoleoutputattribute.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutputAttribute&lt;/strong&gt;](writeconsoleoutputattribute.md)"><strong>WriteConsoleOutputAttribute</strong></a> , permettent d’utiliser des indicateurs d' <a href="https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes" data-raw-source="[character attributes](https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes)">attributs de caractères</a> pour ajuster la couleur du premier plan et de l’arrière-plan du texte. En outre, une plage d’indicateurs DBCS a été spécifiée avec le préfixe COMMON_LVB. Historiquement, ces indicateurs ne fonctionnent que dans les pages de codes DBCS pour les langues chinoises, japonaises et coréennes.</p>
<p>À l’exception des indicateurs d’octet de début et d’octet de fin, les indicateurs restants qui décrivent le dessin de lignes et la vidéo inverse (swap Foreground et Background Colors) peuvent être utiles pour d’autres langages afin de mettre en évidence certaines parties de la sortie.</p>
<p>La définition de cet indicateur de mode de la console permet d’utiliser ces attributs dans chaque page de codes de chaque langue.</p>
<p>Elle est désactivée par défaut pour assurer la compatibilité avec les applications connues qui ont historiquement pris l’avantage de la console en ignorant ces indicateurs sur les ordinateurs non-CJK pour stocker les bits dans ces champs à des fins ou par accident.</p>
<p>Notez que l’utilisation du mode de ENABLE_VIRTUAL_TERMINAL_PROCESSING peut entraîner la définition de la grille LVB et des indicateurs de vidéo inversée, alors que cet indicateur est toujours désactivé si l’application attachée demande la soulignement ou l’inverse de la vidéo via des <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">séquences de terminaux virtuels</a>de la console.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

Une console se compose d’une mémoire tampon d’entrée et d’une ou plusieurs mémoires tampons d’écran. Le mode d’une mémoire tampon de console détermine le comportement de la console lors des opérations d’entrée ou de sortie (e/s). Un jeu de constantes d’indicateur est utilisé avec les handles d’entrée, et un autre jeu est utilisé avec les descripteurs de mémoire tampon d’écran (sortie). La définition des modes de sortie d’une mémoire tampon d’écran n’affecte pas les modes de sortie des autres mémoires tampons d’écran.

Les modes **activer l' \_ \_ entrée** de la ligne et **activer l' \_ \_ entrée** de l’écho affectent uniquement les processus qui utilisent [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ou [**ReadConsole**](readconsole.md) pour lire à partir de la mémoire tampon d’entrée de la console. De même, l' **activation du mode \_ \_ d’entrée traité** affecte principalement les utilisateurs de **ReadFile** et **ReadConsole** , à ceci près qu’elle détermine également si l’entrée Ctrl + C est signalée dans la mémoire tampon d’entrée (pour être lue par la fonction [**ReadConsoleInput**](readconsoleinput.md) ) ou si elle est passée à une fonction définie par l’application.

Les modes **activer l' \_ \_ entrée** de la fenêtre et **activer \_ la souris \_ ** déterminent si les interactions de l’utilisateur impliquant le redimensionnement de fenêtre et les actions de la souris sont signalées dans la mémoire tampon d’entrée ou ignorées. Ces événements peuvent être lus par [**ReadConsoleInput**](readconsoleinput.md), mais ils sont toujours filtrés par [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**ReadConsole**](readconsole.md).

Les modes de sortie **activer le \_ \_ résultat traité** et **activer le \_ Retour à la ligne \_ en fin de \_ \_ vie** affectent uniquement les processus utilisant [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) , [**ReadConsole**](readconsole.md) et [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) ou [**WriteConsole**](writeconsole.md).

Pour modifier les modes d’e/s d’une console, appelez la fonction [**SetConsoleMode**](setconsolemode.md) .

<a name="examples"></a>Exemples
--------

Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).

<a name="requirements"></a>Configuration requise
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Client minimal pris en charge</p></td>
<td><p>Windows 2000 professionnel [applications de bureau uniquement]</p></td>
</tr>
<tr class="even">
<td><p>Serveur minimal pris en charge</p></td>
<td><p>Serveur Windows 2000 [applications de bureau uniquement]</p></td>
</tr>
<tr class="odd">
<td><p>En-tête</p></td>
<td>ConsoleApi. h (via wincon. h, incluez Windows. h)</td>
</tr>
<tr class="even">
<td><p>Bibliothèque</p></td>
<td>Kernel32. lib</td>
</tr>
<tr class="odd">
<td><p>DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Voir aussi


[Fonctions de la console](console-functions.md)

[Modes de la console](console-modes.md)

[**ReadConsole**](readconsole.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetConsoleMode**](setconsolemode.md)

[**WriteConsole**](writeconsole.md)

[**Appel**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




