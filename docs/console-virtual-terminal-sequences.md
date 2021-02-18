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
ms.openlocfilehash: 29c1cc65db5e20c35ca0aaf6dc58c6e485d0edc6
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358129"
---
# <a name="console-virtual-terminal-sequences"></a>Séquences de terminal virtuel de console


Les séquences de terminal virtuel sont des séquences de caractères de contrôle qui peuvent contrôler le déplacement du curseur, le mode couleur/police et d’autres opérations lors de leur écriture dans le flux de sortie. Les séquences peuvent également être reçues sur le flux d’entrée en réponse à une séquence d’informations de requête de flux de sortie ou en tant qu’encodage d’entrée d’utilisateur quand le mode approprié est défini.

Pour configurer ce comportement, vous pouvez utiliser les fonctions [**GetConsoleMode**](getconsolemode.md) et [**SetConsoleMode**](setconsolemode.md). Vous trouverez un exemple de la méthode suggérée pour activer les comportements des terminaux virtuels à la fin de ce document.

Le comportement des séquences suivantes est basé sur les technologies d’émulateur de terminal VT100 et dérivés, plus spécifiquement l’émulateur de terminal xterm. Pour plus d’informations sur les séquences de terminal, consultez <http://vt100.net> et <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Séquences de sortie


Les séquences de terminal suivantes sont interceptées par l’hôte de la console quand elles sont écrites dans le flux de sortie, si l’indicateur ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING est défini sur le descripteur de mémoire tampon d’écran à l’aide de la fonction [**SetConsoleMode**](setconsolemode.md). Notez que l’indicateur DISABLE\_NEWLINE\_AUTO\_RETURN peut également être utile pour émuler le comportement de défilement et de positionnement de curseur d’autres émulateurs de terminal par rapport aux caractères écrits dans la dernière colonne de n’importe quelle ligne.

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Positionnement de curseur simple


Dans toutes les descriptions suivantes, le caractère d’échappement (ESC) est toujours la valeur hexadécimale 0x1B. Aucun espace ne doit être inclus dans les séquences de terminal. Pour obtenir un exemple d’utilisation pratique de ces séquences, consultez l’[exemple ](#example) à la fin de cette rubrique.

Le tableau suivant décrit des séquences d’échappement simples avec une commande d’action unique directement après le caractère d’échappement (ESC). Ces séquences n’ont pas de paramètres et prennent effet immédiatement.

Toutes les commandes de ce tableau équivalent généralement à appeler l’API de console [**SetConsoleCursorPosition**](setconsolecursorposition.md) pour placer le curseur.

Le déplacement du curseur est limité par la fenêtre d’affichage actuelle dans la mémoire tampon. Le défilement (si disponible) ne se produit pas.


| Séquence | Forme abrégée | Comportement |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| ESC A | CUU | Déplacement du curseur vers le haut de 1 ligne |
| ESC B | CUD | Déplacement du curseur vers le bas de 1 ligne |
| ESC C | CUF | Déplacement du curseur vers l’avant (à droite) de 1 colonne |
| ESC D | CUB | Déplacement du curseur vers l’arrière (à gauche) de 1 colonne |
| ESC M | Instance réservée | Index inverse : effectue l’opération inverse de \\n, déplace le curseur d’une ligne vers le haut, conserve la position horizontale, fait défiler le tampon si nécessaire\* |
| ESC 7 | DECSC | Enregistrer la position du curseur en mémoire\*\* |
| ESC 8 | DECSR | Restaurer la position du curseur à partir de la mémoire\*\* |



> [!NOTE]
>\* Si des marges de défilement sont définies, l’index inverse (RI) à l’intérieur des marges fait défiler uniquement le contenu des marges et laisse la fenêtre d’affichage inchangée. (Voir Marges de défilement)
>
>\*\*Aucune valeur n’est enregistrée en mémoire tant que la commande d’enregistrement n’a pas été utilisée une première fois. La seule façon d’accéder à la valeur enregistrée consiste à utiliser la commande de restauration.

## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Positionnement du curseur


Les tableaux suivants englobent les séquences de types CSI (Control Sequence Introducer, Introducteur de séquence de commandes). Toutes les séquences CSI commencent par ESC (0x1B) suivi de \[ (crochet gauche, 0x5B) et peuvent contenir des paramètres de longueur variable afin de spécifier plus d’informations pour chaque opération. Cela est représenté par la forme abrégée &lt;n&gt;. Chaque tableau ci-dessous est regroupé par fonctionnalité et est suivi de notes expliquant le fonctionnement du groupe.

Pour tous les paramètres, les règles suivantes s’appliquent, sauf indication contraire :

- &lt;n&gt; représente la distance de déplacement et est un paramètre facultatif
- Si &lt;n&gt; est omis ou est égal à 0, il est traité comme un 1
- &lt;n&gt; ne peut pas être supérieur à 32 767 (valeur courte maximale)
- &lt;n&gt; ne peut pas être négatif

Toutes les commandes de cette section équivalent généralement à appeler l’API de console [**SetConsoleCursorPosition**](setconsolecursorposition.md).

Le déplacement du curseur est limité par la fenêtre d’affichage actuelle dans la mémoire tampon. Le défilement (si disponible) ne se produit pas.


| Séquence | Code | Description | Comportement |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; A | CUU | Déplacement du curseur vers le haut | Déplacement du curseur vers le haut de &lt;n&gt; ligne(s) |
| ESC \[ &lt;n&gt; B | CUD | Déplacement du curseur vers le bas | Déplacement du curseur vers le bas de &lt;n&gt; ligne(s) |
| ESC \[ &lt;n&gt; C | CUF | Déplacement du curseur vers l’avant | Déplacement du curseur vers l’avant (à droite) de &lt;n&gt; colonne(s) |
| ESC \[ &lt;n&gt; D | CUB | Déplacement du curseur vers l’arrière | Déplacement du curseur vers l’arrière (à gauche) de &lt;n&gt; colonne(s) |
| ESC \[ &lt;n&gt; E | CNL | Déplacement du curseur vers la ligne suivante | Déplacement du curseur vers le bas de &lt;n&gt; lignes à partir de la position actuelle |
| ESC \[ &lt;n&gt; F | CPL | Déplacement du curseur vers la ligne précédente | Déplacement du curseur vers le haut de &lt;n&gt; lignes à partir de la position actuelle |
| ESC \[ &lt;n&gt; G | CHA | Déplacement horizontal absolu du curseur | Le curseur se déplace horizontalement jusqu’à la &lt;n&gt;ième position dans la ligne actuelle |
| ESC \[ &lt;n&gt; d | VPA | Déplacement vertical absolu jusqu’à une ligne | Le curseur se déplace verticalement jusqu’à la &lt;n&gt;ième position dans la colonne actuelle |
| ESC \[ &lt;y&gt; ; &lt;x&gt; H | CUP | Position du curseur | \*Le curseur se déplace jusqu’à la position &lt;x&gt;; &lt;y&gt; dans la fenêtre d’affichage, où &lt;x&gt; correspond à la colonne de la ligne &lt;y&gt; |
| ESC \[ &lt;y&gt; ; &lt;x&gt; f | HVP | Position verticale horizontale | \*Le curseur se déplace jusqu’à la position &lt;x&gt;; &lt;y&gt; dans la fenêtre d’affichage, où &lt;x&gt; correspond à la colonne de la ligne &lt;y&gt; |
| ESC \[ s | ANSISYSSC | Enregistrer le curseur – émulation Ansi.sys | \*\*Sans paramètre, effectue une opération d’enregistrement du curseur comme DECSC |
| ESC \[ u | ANSISYSSC | Restaurer le curseur – émulation Ansi.sys | \*\*Sans paramètre, effectue une opération de restauration du curseur comme DECRC |



> [!NOTE]
>Les paramètres \*&lt;x&gt; et &lt;y&gt; présentent les mêmes limitations que &lt;n&gt; ci-dessus. Si &lt;x&gt; et &lt;y&gt; sont omis, ils sont définis sur 1;1.
>
>\*\*La documentation historique sur ANSI.sys est disponible à l’adresse <https://msdn.microsoft.com/library/cc722862.aspx> et est implémentée pour des raisons pratiques et de compatibilité.



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Visibilité du curseur


Les commandes suivantes contrôlent la visibilité du curseur et son état de clignotement. Les séquences DECTCEM équivalent généralement à appeler l’API de console [**SetConsoleCursorInfo**](setconsolecursorinfo.md) pour changer l’état de la visibilité du curseur.


| Séquence | Code | Description | Comportement |
|---------------|---------|------------------------------|---------------------------|
| ESC \[ ? 12 h | ATT160 | Curseur de texte - Activer le clignotement | Démarrer le clignotement du curseur |
| ESC \[ ? 12 l | ATT160 | Curseur de texte - Désactiver le clignotement | Arrêter le clignotement du curseur |
| ESC \[ ? 25 h | DECTCEM | Curseur de texte - Activer le mode affichage | Afficher le curseur |
| ESC \[ ? 25 l | DECTCEM | Curseur de texte - Activer le mode masquage | Masquer le curseur |

> [!TIP]
> Les séquences d’activation se terminent par un caractère H minuscule (`h`), tandis que les séquences de désactivation se terminent par un caractère L minuscule (`l`).

## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Positionnement de la fenêtre d’affichage


Toutes les commandes de cette section équivalent généralement à appeler l’API de console [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) pour déplacer le contenu de la mémoire tampon de la console.

**Attention** Les noms des commandes sont trompeurs. Le défilement fait référence à la direction dans laquelle le texte se déplace au cours de l’opération, et non à celle que semblerait emprunter la fenêtre d’affichage.




| Séquence | Code | Description | Comportement |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; S | Unités de diffusion en continu | Faire défiler vers le haut | Faire défiler le texte vers le haut de &lt;n&gt;. Opération également appelée « panoramique vers le bas » ; les nouvelles lignes se remplissent à partir du bas de l’écran |
| ESC \[ &lt;n&gt; T | SD | Faire défiler vers le bas | Faire défiler vers le bas de &lt;n&gt;. Opération également appelée « panoramique vers le haut » ; les nouvelles lignes se remplissent à partir du haut de l’écran |



Le texte est déplacé à partir de la ligne sur laquelle se trouve le curseur. Si le curseur se trouve sur la ligne du milieu de la fenêtre d’affichage, le défilement vers le haut déplace la moitié inférieure de la fenêtre d’affichage et insère des lignes vides en bas. Le défilement vers le bas déplace la moitié supérieure des lignes de la fenêtre d’affichage et insère de nouvelles lignes en haut.

En outre, il est important de noter que le défilement vers le haut et vers le bas est également affecté par les marges de défilement. Le défilement vers le haut et vers le bas n’affecte pas les lignes situées en dehors des marges de défilement.

La valeur par défaut de &lt;n&gt; est 1 et la valeur peut éventuellement être omise.

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Modification du texte


Toutes les commandes de cette section équivalent généralement à appeler les API de console [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) et [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) pour modifier le contenu de la mémoire tampon de texte.


| Séquence | Code | Description | Comportement |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; @ | ICH | Insérer un caractère | Insérer &lt;n&gt; espaces à la position actuelle du curseur, en décalant tout le texte existant vers la droite. Le texte qui quitte l’écran à droite est supprimé. |
| ESC \[ &lt;n&gt; P | DCH | Supprimer un caractère | Supprimer &lt;n&gt; caractères à la position actuelle du curseur, entraînant par effet de décalage la création d’autant de caractères d’espace à partir du bord droit de l’écran. |
| ESC \[ &lt;n&gt; X | ECH | Effacer un caractère | Effacer &lt;n&gt; caractères de la position actuelle du curseur en les remplaçant par un espace. |
| ESC \[ &lt;n&gt; L | IL | Insérer une ligne | Insérer &lt;n&gt; lignes dans la mémoire tampon à la position du curseur. La ligne sur laquelle se trouve le curseur et les lignes au-dessous de celle-ci sont décalées vers le bas. |
| ESC \[ &lt;n&gt; M | DL | Supprimer la ligne | Supprime &lt;n&gt; lignes de la mémoire tampon, en commençant par la ligne sur laquelle se trouve le curseur. |



> [!NOTE]
>Pour IL et DL, seules les lignes dans les marges de défilement (voir Marges de défilement) sont affectées. Si aucune marge n’est définie, les bordures de marge par défaut sont la fenêtre d’affichage actuelle. Si des lignes sont décalées en dessous des marges, elles sont ignorées. Quand des lignes sont supprimées, des lignes vides sont insérées en bas des marges et les lignes en dehors de la fenêtre d’affichage ne sont jamais affectées.

Pour chacune des séquences, la valeur par défaut de &lt;n&gt; s’il est omis est 0.



Pour les commandes suivantes, le paramètre &lt;n&gt; a 3 valeurs valides :

- 0 efface de la position actuelle du curseur (comprise) jusqu’à la fin de la ligne/de l’affichage
- 1 efface du début de la ligne/de l’affichage jusqu’à la position actuelle du curseur comprise
- 2 efface l’intégralité de la ligne/de l’affichage


| Séquence | Code | Description | Comportement |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; J | ED | Effacer dans l’affichage | En fonction de la valeur de &lt;n&gt;, remplacer par des espaces tout le texte de la fenêtre d’affichage ou de l’écran actuel |
| ESC \[ &lt;n&gt; K | EL | Effacer dans la ligne | En fonction de la valeur de &lt;n&gt;, remplacer par des espaces tout le texte de la ligne contenant le curseur |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Mise en forme du texte


Toutes les commandes de cette section équivalent généralement à appeler les API de console [**SetConsoleTextAttribute**](setconsoletextattribute.md) pour ajuster la mise en forme de toutes les écritures futures dans la mémoire tampon de texte de sortie de la console.

Cette commande est spéciale dans la mesure où la position &lt;n&gt; ci-dessous peut accepter entre 0 et 16 paramètres séparés par des points-virgules.

L’absence de paramètre équivaut à la présence d’un paramètre 0 unique.


| Séquence | Code | Description | Comportement |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| ESC \[ &lt;n&gt; m | SGR | Définir un rendu graphique | Définir le format de l’écran et du texte tel que spécifié par &lt;n&gt; |



Le tableau de valeurs suivant peut être utilisé dans &lt;n&gt; pour représenter différents modes de mise en forme.

Les modes de mise en forme s’appliquent de gauche à droite. Si des options de mise en forme concurrentes sont appliquées, l’option la plus à droite est prioritaire.

Pour les options qui spécifient des couleurs, celles-ci sont utilisées comme défini dans la table de couleurs de la console, qui peut être modifiée à l’aide de l’API [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md). Si la table est modifiée afin que la position « bleu » dans la table affiche une nuance RVB rouge, tous les appels à **Premier plan en bleu** affichent cette couleur rouge jusqu’à ce qu’une nouvelle modification soit effectuée.


| Valeur | Description | Comportement |
|-------|---------------------------|--------------------------------------------------------------------|
| 0 | Default | Retourne tous les attributs à l’état par défaut avant la modification |
| 1 | Mise en gras/couleur brillante | Applique l’indicateur de luminosité/intensité à la couleur de premier plan |
| 22 | Aucune mise en gras/couleur brillante | Supprime l’indicateur de luminosité/intensité de la couleur de premier plan |
| 4 | Souligner | Ajoute un soulignement |
| 24 | Pas de soulignement | Supprime le soulignement |
| 7 | Négatif | Permute les couleurs de premier plan et d’arrière-plan |
| 27 | Image positive (non négative) | Rétablit le premier plan et l’arrière-plan à l’état normal |
| 30 | Premier plan en noir | Applique la couleur noir brillant sans mise en gras au premier plan |
| 31 | Premier plan en rouge | Applique la couleur rouge vif sans mise en gras au premier plan |
| 32 | Premier plan en vert | Applique la couleur vert clair sans mise en gras au premier plan |
| 33 | Premier plan en jaune | Applique la couleur jaune vif sans mise en gras au premier plan |
| 34 | Premier plan en bleu | Applique la couleur bleu brillant sans mise en gras au premier plan |
| 35 | Premier plan en magenta | Applique la couleur magenta brillant sans mise en gras au premier plan |
| 36 | Premier plan en cyan | Applique la couleur cyan brillant sans mise en gras au premier plan |
| 37 | Premier plan en blanc | Applique la couleur blanc brillant sans mise en gras au premier plan |
| 38 | Premier plan avec valeur de couleur étendue | Applique la valeur de couleur étendue au premier plan (voir les détails ci-dessous). |
| 39 | Définition par défaut du premier plan | Applique uniquement la partie du premier plan des valeurs par défaut (voir 0). |
| 40 | Arrière-plan en noir | Applique la couleur noir brillant sans mise en gras à l’arrière-plan |
| 41 | Arrière-plan en rouge | Applique la couleur rouge vif sans mise en gras à l’arrière-plan |
| 42 | Arrière-plan en vert | Applique la couleur vert clair sans mise en gras à l’arrière-plan |
| 43 | Arrière-plan en jaune | Applique la couleur jaune vif sans mise en gras à l’arrière-plan |
| 44 | Arrière-plan en bleu | Applique la couleur bleu brillant sans mise en gras à l’arrière-plan |
| 45 | Arrière-plan en magenta | Applique la couleur magenta brillant sans mise en gras à l’arrière-plan |
| 46 | Arrière-plan en cyan | Applique la couleur cyan brillant sans mise en gras à l’arrière-plan |
| 47 | Arrière-plan en blanc | Applique la couleur blanc brillant sans mise en gras à l’arrière-plan |
| 48 | Arrière-plan avec valeur de couleur étendue | Applique une valeur de couleur étendue à l’arrière-plan (voir les détails ci-dessous). |
| 49 | Définition par défaut de l’arrière-plan | Applique uniquement la partie de l’arrière-plan des valeurs par défaut (voir 0). |
| 90 | Premier plan en noir brillant | Applique la couleur noir brillant avec mise en gras au premier plan |
| 91 | Premier plan en rouge vif | Applique la couleur rouge vif avec mise en gras au premier plan |
| 92 | Premier plan en vert clair | Applique la couleur vert clair avec mise en gras au premier plan |
| 93 | Premier plan en jaune vif | Applique la couleur jaune vif avec mise en gras au premier plan |
| 94 | Premier plan en bleu brillant | Applique la couleur bleu brillant avec mise en gras au premier plan |
| 95 | Premier plan en magenta brillant | Applique la couleur magenta brillant avec mise en gras au premier plan |
| 96 | Premier plan en cyan brillant | Applique la couleur cyan brillant avec mise en gras au premier plan |
| 97 | Premier plan en blanc brillant | Applique la couleur blanc brillant avec mise en gras au premier plan |
| 100 | Arrière-plan en noir brillant | Applique la couleur noir brillant avec mise en gras à l’arrière-plan |
| 101 | Arrière-plan en rouge vif | Applique la couleur rouge vif avec mise en gras à l’arrière-plan |
| 102 | Arrière-plan en vert clair | Applique la couleur vert clair avec mise en gras à l’arrière-plan |
| 103 | Arrière-plan en jaune vif | Applique la couleur jaune vif avec mise en gras à l’arrière-plan |
| 104 | Arrière-plan en bleu brillant | Applique la couleur bleu brillant avec mise en gras à l’arrière-plan |
| 105 | Arrière-plan en magenta brillant | Applique la couleur magenta brillant avec mise en gras à l’arrière-plan |
| 106 | Arrière-plan en cyan brillant | Applique la couleur cyan brillant avec mise en gras à l’arrière-plan |
| 107 | Arrière-plan en blanc brillant | Applique la couleur blanc brillant avec mise en gras à l’arrière-plan |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Couleurs étendues

Certains émulateurs de terminaux virtuels prennent en charge une palette de couleurs supérieure aux 16 couleurs fournies par la console Windows. Pour ces couleurs étendues, la console Windows choisit la couleur appropriée la plus proche dans la table de 16 couleurs existante pour l’affichage. Contrairement aux valeurs SGR classiques ci-dessus, les valeurs étendues consomment des paramètres supplémentaires après l’indicateur initial, conformément au tableau ci-dessous.


| Sous-séquence SGR | Description |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| 38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt; | Définir la couleur de premier plan sur la valeur RVB spécifiée dans les paramètres &lt;r&gt;, &lt;g&gt;, &lt;b&gt; \* |
| 48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt; | Définir la couleur d’arrière-plan sur la valeur RVB spécifiée dans les paramètres &lt;r&gt;, &lt;g&gt;, &lt;b&gt; \* |
| 38 ; 5 ; &lt;s&gt; | Définir la couleur de premier plan sur l’index &lt;s&gt; dans la table de 88 ou 256 couleurs\* |
| 48 ; 5 ; &lt;s&gt; | Définir la couleur d’arrière-plan sur l’index &lt;s&gt; dans la table de 88 ou 256 couleurs\* |



\*Les palettes de 88 et 256 couleurs gérées en interne pour la comparaison sont basées sur l’émulateur de terminal xterm. Les tables de comparaison et d’arrondi ne peuvent pas être modifiées pour l’instant.


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Couleurs d’écran


La commande suivante permet à l’application de définir les valeurs de la palette de couleurs d’écran sur n’importe quelle valeur RVB.

Les valeurs RVB doivent être des valeurs hexadécimales comprises entre `0` et `ff` séparées par le caractère barre oblique (par exemple, `rgb:1/24/86`).

Notez que cette séquence est une séquence OSC (Operating System Command, commande de système d’exploitation), et non une séquence CSI telle que la plupart des autres séquences listées. Ainsi, elle commence par « \\x1b\] », et non pas par « \\x1b\[ ».


| Séquence | Description | Comportement |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC | Modifier les couleurs d’écran | Définit l’index &lt;i&gt; de la palette de couleurs d’écran sur les valeurs RVB spécifiées dans &lt;r&gt;, &lt;g&gt;, &lt;b&gt; |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Changements de mode


Il s’agit de séquences qui contrôlent les modes d’entrée. Il existe deux ensembles différents de modes d’entrée : le mode touches de direction et le mode touches du pavé numérique. Le mode touches de direction contrôle les séquences émises par les touches de direction, Début et Fin, tandis que le mode touches du pavé numérique contrôle les séquences émises par les touches du pavé numérique, essentiellement, ainsi que par les touches de fonction.

Chacun de ces modes est constitué de paramètres booléens simples : le mode touches de direction est Normal (valeur par défaut) ou Application, tandis que le mode touches du pavé numérique est soit Numérique (valeur par défaut), soit Application.

Consultez les sections Touches de direction et Touches de fonction et pavé numérique pour connaître les séquences émises dans ces modes.


| Séquence | Code | Description | Comportement |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| ESC = | DECKPAM | Activer le mode Application du pavé numérique | Les touches du pavé numérique émettent leurs séquences en mode Application. |
| ESC &gt; | DECKPNM | Activer le mode Numérique du pavé numérique | Les touches du pavé numérique émettent leurs séquences en mode Numérique. |
| ESC \[ ? 1 h | DECCKM | Activer le mode Application de touches de direction | Les touches du pavé numérique émettent leurs séquences en mode Application. |
| ESC \[ ? 1 l | DECCKM | Désactiver le mode Application de touches de direction (utiliser le mode Normal) | Les touches du pavé numérique émettent leurs séquences en mode Numérique. |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>État de requête


Toutes les commandes de cette section équivalent généralement à appeler les API de console \* pour récupérer les informations sur l’état actuel de la mémoire tampon de la console.

> [!NOTE]
>Ces requêtes émettent leurs réponses dans le flux d’entrée de la console immédiatement après avoir été reconnues sur le flux de sortie si l’indicateur ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING est défini. L’indicateur ENABLE\_VIRTUAL\_TERMINAL\_INPUT ne s’applique pas aux commandes de requête, car il est supposé qu’une application qui effectue la requête doit toujours recevoir la réponse.




| Séquence | Code | Description | Comportement |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| ESC \[ 6 n | DECXCPR | Signaler la position du curseur | Émet la position du curseur comme suit : ESC \[ &lt;r&gt; ; &lt;c&gt; R où &lt;r&gt; = ligne du curseur et &lt;c&gt; = colonne du curseur |
| ESC \[ 0 c | DA | Attributs de l’appareil | Signaler l’identité du terminal. Émet « \\x1b\[?1;0c », en indiquant « VT101 with No Options » (VT101 sans options). |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabulations


Alors que la console Windows s’attend traditionnellement à ce que les tabulations aient exclusivement une largeur de huit caractères, les applications \*nix utilisant certaines séquences peuvent manipuler la position des taquets de tabulation dans les fenêtres de console pour optimiser le déplacement du curseur par l’application.

Les séquences suivantes permettent à une application de définir les positions des taquets de tabulation dans la fenêtre de console, de supprimer ces derniers et de passer de l’un à l’autre.


| Séquence | Code | Description | Comportement |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC H | HTS | Définir une tabulation horizontale | Définit un taquet de tabulation au niveau de la colonne à laquelle se trouve actuellement le curseur. |
| ESC \[ &lt;n&gt; I | CHT | Déplacer le curseur vers un taquet de tabulation horizontale (vers l’avant) | Avance le curseur jusqu’à la colonne suivante (sur la même ligne) ayant un taquet de tabulation. S’il n’y a plus de taquets de tabulation, passe à la dernière colonne de la ligne. Si le curseur se trouve à la dernière colonne, passe à la première colonne de la ligne suivante. |
| ESC \[ &lt;n&gt; Z | CBT | Déplacer le curseur vers un taquet de tabulation vers l’arrière | Déplace le curseur jusqu’à la colonne précédente (sur la même ligne) ayant un taquet de tabulation. S’il n’y a plus de taquets de tabulation, déplace le curseur jusqu’à la première colonne. Si le curseur se trouve à la première colonne, ne déplace pas le curseur. |
| ESC \[ 0 g | À confirmer | Effacer un taquet de tabulation (colonne actuelle) | Efface le taquet de tabulation à la colonne actuelle, s’il en existe un. Sinon, ne fait rien. |
| ESC \[ 3 g | À confirmer | Effacer les taquets de tabulation (toutes les colonnes) | Efface tous les taquets de tabulation actuellement définis. |



- Pour CHT et CBT, &lt;n&gt; est un paramètre facultatif (valeur par défaut = 1) qui indique combien de fois il faut avancer le curseur dans la direction spécifiée.
- Si aucun taquet de tabulation n’est défini par le biais de HTS, CHT et CBT traitent les première et dernière colonnes de la fenêtre comme étant les deux seuls taquets de tabulation.
- En outre, quand HTS est utilisé pour définir un taquet de tabulation, la console accède au taquet de tabulation suivant sur la sortie d’un caractère de tabulation (0x09, '\\t'), de la même manière que CHT.

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Désigner le jeu de caractères


Les séquences suivantes permettent à un programme de changer le mappage du jeu de caractères actif. Ainsi, un programme peut émettre des caractères ASCII de 7 bits, mais les faire s’afficher sous la forme d’autres glyphes sur l’écran de terminal lui-même. Les deux seuls jeux de caractères pris en charge sont ASCII (par défaut) et le jeu de caractères DEC Special Graphics. Consultez <http://vt100.net/docs/vt220-rm/table2-4.html> pour obtenir la liste de tous les caractères représentés par le jeu de caractères DEC Special Graphics.


| Séquence | Description | Comportement |
|----------|--------------------------------------------|-------------------------------|
| ESC ( 0 | Désigner le jeu de caractères – Dessin de ligne DEC | Active le mode de dessin de la ligne DEC |
| ESC ( B | Désigner le jeu de caractères – ASCII des États-Unis | Active le mode ASCII (par défaut) |



En particulier, le mode de dessin de ligne DEC est utilisé pour dessiner les bordures dans les applications console. Le tableau suivant indique les correspondances entre les caractères ASCII et les caractères de dessin de ligne.


| Hex | ASCII | Dessin de ligne DEC |
|------|-------|------------------|
| 0x6a | j | ┘ |
| 0x6b | k | ┐ |
| 0x6c | l | ┌ |
| 0x6d | m | └ |
| 0x6e | n | ┼ |
| 0x71 | q | ─ |
| 0x74 | t | ├ |
| 0x75 | u | ┤ |
| 0x76 | v | ┴ |
| 0x77 | w | ┬ |
| 0x78 | x | │ |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Marges de défilement


Les séquences suivantes permettent à un programme de configurer la « zone de défilement » de l’écran qui est affectée par les opérations de défilement. Il s’agit d’un sous-ensemble des lignes qui sont ajustées en cas de défilement de l’écran, par exemple, sur une commande « \\n » ou RI. Ces marges affectent également les lignes modifiées par les commandes d’insertion de ligne (IL), de suppression de ligne (DL), de défilement vers le haut (SU) et de défilement vers le bas (SD).

Les marges de défilement peuvent être particulièrement utiles pour disposer d’une partie de l’écran qui ne défile pas quand le reste de l’écran est rempli, par exemple une barre de titre en haut ou une barre d’état en bas de votre application.

Pour DECSTBM, il existe deux paramètres facultatifs, &lt;t&gt; et &lt;b&gt;, qui servent à spécifier les lignes qui représentent les lignes supérieure et inférieure de la zone de défilement, celles-ci incluses. Si les paramètres sont omis, &lt;t&gt; a la valeur par défaut 1 et &lt;b&gt; est défini par défaut sur la hauteur de la fenêtre d’affichage actuelle.

Les marges de défilement sont définies par mémoire tampon. Il est donc important que la mémoire tampon secondaire et la mémoire tampon principale aient constamment des paramètres de marges de défilement distincts (afin qu’une application en plein écran dans la mémoire tampon secondaire n’altère pas les marges de la mémoire tampon principale).


| Séquence | Code | Description | Comportement |
|--------------------------------|---------|----------------------|------------------------------------------------|
| ESC \[ &lt;t&gt; ; &lt;b&gt; r | DECSTBM | Définir la zone de défilement | Définit les marges de défilement des tabulations verticales de la fenêtre d’affichage. |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Titre de fenêtre


Les commandes suivantes permettent à l’application de définir le titre de la fenêtre de console sur le paramètre &lt;chaîne&gt; donné. La chaîne doit contenir moins de 255 caractères pour être acceptée. Cela équivaut à appeler SetConsoleTitle avec la chaîne donnée.

Notez que ces séquences sont des séquences OSC, et non des séquence CSI telles que la plupart des autres séquences listées. Ainsi, elle commence par « \\x1b\] », et non pas par « \\x1b\[ ».


| Séquence | Description | Comportement |
|-------------------------------|---------------------------|----------------------------------------------------|
| ESC \] 0 ; &lt;chaîne&gt; BEL | Définir l’icône et le titre de la fenêtre | Définit le titre de la fenêtre de console sur &lt;chaîne&gt;. |
| ESC \] 2 ; &lt;chaîne&gt; BEL | Définir le titre de la fenêtre | Définit le titre de la fenêtre de console sur &lt;chaîne&gt;. |



En l’occurrence, le caractère de fin est le caractère « sonnerie », « \\x07 »

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Mémoire tampon d’écran secondaire


Les applications de style \*nix utilisent souvent une mémoire tampon d’écran secondaire, afin de pouvoir modifier l’ensemble du contenu de la mémoire tampon, sans affecter l’application qui les a démarrées. La mémoire tampon secondaire épouse les dimensions de la fenêtre, sans aucune zone de défilement.

À titre d’exemple de ce comportement, pensez à la façon dont vim est lancé à partir de bash. Vim utilise l’intégralité de l’écran pour modifier le fichier, puis le retour à bash laisse la mémoire tampon d’origine inchangée.


| Séquence | Description | Comportement |
|--------------------|-----------------------------|--------------------------------------------|
| ESC \[ ? 1 0 4 9 h | Utiliser une mémoire tampon d’écran secondaire | Bascule vers une nouvelle mémoire tampon d’écran secondaire. |
| ESC \[ ? 1 0 4 9 l | Utiliser la mémoire tampon d’écran principale | Bascule vers la mémoire tampon principale. |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Largeur de la fenêtre


Les séquences suivantes peuvent être utilisées pour contrôler la largeur de la fenêtre de console. Elles équivalent plus ou moins à appeler l’API de console SetConsoleScreenBufferInfoEx pour définir la largeur de la fenêtre.


| Séquence | Code | Description | Comportement |
|--------------|---------|------------------------------|---------------------------------------------|
| ESC \[ ? 3 h | DECCOLM | Définir le nombre de colonnes sur 132 | Définit la largeur de la console sur une largeur de 132 colonnes. |
| ESC \[ ? 3 l | DECCOLM | Définir le nombre de colonnes sur 80 | Définit la largeur de la console sur une largeur de 80 colonnes. |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Réinitialisation à chaud


La séquence suivante peut être utilisée pour réinitialiser certaines propriétés à leurs valeurs par défaut. Les propriétés suivantes sont réinitialisées aux valeurs par défaut indiquées (les séquences qui contrôlent ces propriétés sont également listées) :

- Visibilité du curseur : visible (DECTEM)
- Pavé numérique : mode Numérique (DECNKM)
- Mode touches de direction : mode Normal (DECCKM)
- Marges supérieure et inférieure : supérieure= 1, inférieure = hauteur de la console (DECSTBM)
- Jeu de caractères : ASCII des États-Unis
- Rendu graphique : Par défaut/désactivé (SGR)
- Enregistrer l’état du curseur : Position de début (0,0) (DECSC)


| Séquence | Code | Description | Comportement |
|------------|--------|-------------|----------------------------------------------------|
| ESC \[ ! p | DECSTR | Réinitialisation à chaud | Réinitialiser certains paramètres de terminal à leurs valeurs par défaut. |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Séquences d’entrée


Les séquences de terminal suivantes sont émises par l’hôte de la console sur le flux d’entrée si l’indicateur ENABLE\_VIRTUAL\_TERMINAL\_INPUT est défini sur le descripteur de mémoire tampon d’entrée à l’aide de l’indicateur SetConsoleMode.

Il existe deux modes internes qui déterminent les séquences émises pour les touches d’entrée données : le mode touches de direction et le mode touches du pavé numérique. Ces modes sont décrits dans la section Changements de mode.

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Touches de direction


| Clé | Mode Normal | Mode Application |
|-------------|-------------|------------------|
| Flèche haut | ESC \[ A | ESC O A |
| Flèche Bas | ESC \[ B | ESC O B |
| Flèche droite | ESC \[ C | ESC O C |
| Gauche | ESC \[ D | ESC O D |
| Accueil | ESC \[ H | ESC O H |
| End | ESC \[ F | ESC O F |



En outre, si la touche CTRL est enfoncée avec l’une de ces touches, les séquences suivantes sont émises à la place, indépendamment du mode touches de direction :


| Clé | N’importe quel mode |
|--------------------|----------------|
| Ctrl + flèche haut | ESC \[ 1 ; 5 A |
| Ctrl + flèche bas | ESC \[ 1 ; 5 B |
| Ctrl + flèche droite | ESC \[ 1 ; 5 C |
| Ctrl + flèche gauche | ESC \[ 1 ; 5 D |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Touches de fonction et pavé numérique


| Clé | Séquence |
|-----------|--------------|
| Retour arrière | 0x7f (DEL) |
| Suspendre | 0x1a (SUB) |
| Caractère d'échappement | 0x1b (ESC) |
| Insérer | ESC \[ 2 ~ |
| Supprimer | ESC \[ 3 ~ |
| Page précédente | ESC \[ 5 ~ |
| Page suivante | ESC \[ 6 ~ |
| F1 | ESC O P |
| F2 | ESC O Q |
| F3 | ESC O R |
| F4 | ESC O S |
| F5 | ESC \[ 1 5 ~ |
| F6 | ESC \[ 1 7 ~ |
| F7 | ESC \[ 1 8 ~ |
| F8 | ESC \[ 1 9 ~ |
| F9 | ESC \[ 2 0 ~ |
| F10 | ESC \[ 2 1 ~ |
| F11 | ESC \[ 2 3 ~ |
| F12 | ESC \[ 2 4 ~ |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modificateurs

La touche Alt est traitée en préfixant la séquence par un caractère d’échappement : ESC &lt;c&gt; où &lt;c&gt; est le caractère passé par le système d’exploitation. La séquence Alt+Ctrl est gérée de la même façon, à la différence que le système d’exploitation aura préalablement décalé la touche &lt;c&gt; vers le caractère de contrôle approprié qui sera relayé à l’application.

La touche Ctrl est généralement transmise telle qu’elle est reçue du système. Il s’agit généralement d’un caractère unique baissé dans l’espace réservé de caractères de contrôle (0x0-0x1f). Par exemple, Ctrl+@ (0x40) devient NUL (0x00), Ctrl+\[ (0x5b) devient ESC (0x1b), etc. Quelques combinaisons de touches impliquant Ctrl sont traitées de façon spéciale selon le tableau suivant :


| Clé | Séquence |
|--------------------|----------------|
| Ctrl + espace | 0x00 (NUL) |
| Ctrl + flèche haut | ESC \[ 1 ; 5 A |
| Ctrl + flèche bas | ESC \[ 1 ; 5 B |
| Ctrl + flèche droite | ESC \[ 1 ; 5 C |
| Ctrl + flèche gauche | ESC \[ 1 ; 5 D |



> [!NOTE]
><kbd>Ctrl</kbd> gauche + <kbd>Alt</kbd> droite est traité comme AltGr. Quand ils apparaissent ensemble, ils sont supprimés et la valeur Unicode du caractère présenté par le système est transmise à la cible. Le système pré-convertit les valeurs AltGr en fonction des paramètres d’entrée système actuels.



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Exemples


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span id="example"></span><span id="EXAMPLE"></span>Exemple de séquences de terminal SGR

Le code suivant fournit plusieurs exemples de mise en forme de texte.

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
>Dans l’exemple précédent, la chaîne « `\x1b[31m` » correspond à l’implémentation de **ESC \[ &lt;n&gt; m** où &lt;n&gt; a pour valeur 31.



Le graphique suivant montre la sortie de l’exemple de code précédent.

![Sortie de la console illustrant l’utilisation de la commande sgr](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Exemple d’activation de traitement de terminal virtuel

Le code suivant fournit un exemple de la méthode recommandée pour activer le traitement de terminal virtuel pour une application. L’exemple vise à illustrer les points suivants :

1. Le mode existant doit toujours être récupéré par le biais de GetConsoleMode et analysé avant d’être défini avec SetConsoleMode.

2. Le fait de vérifier si SetConsoleMode retourne `0` et GetLastError retourne STATUS\_INVALID\_PARAMETER est le mécanisme actuel pour déterminer si l’exécution a lieu sur un système de niveau inférieur. Une application qui reçoit STATUS\_INVALID\_PARAMETER avec l’un des nouveaux indicateurs de mode de console dans le champ de bit doit progressivement dégrader le comportement, puis réessayer.

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

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Exemple de certaines fonctionnalités de mise à jour anniversaire

L’exemple suivant se veut un exemple plus robuste de code utilisant une variété de séquences d’échappement pour manipuler la mémoire tampon et met l’accent sur les fonctionnalités ajoutées dans la mise à jour anniversaire pour Windows 10.

Cet exemple utilise la mémoire tampon d’écran secondaire et illustre la manipulation des taquets de tabulation, la définition des marges de défilement et le changement du jeu de caractères.

```C
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
    printf(fIsTop ? "l" : "m"); // print left corner 

    for (int i = 1; i < Size.X - 1; i++)
        printf("q"); // in line drawing mode, \x71 -> \u2500 "HORIZONTAL SCAN LINE-5"

    printf(fIsTop ? "k" : "j"); // print right corner
    printf(CSI "0m");
    printf(ESC "(B"); // exit line drawing mode
}

void PrintStatusLine(const char* const pszMessage, COORD const Size)
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
    printf(CSI "3;%dr", Size.Y - 2);
    int iNumLines = Size.Y - 4;

    printf(CSI "1;1H");
    printf(CSI "102;30m");
    printf("Windows 10 Anniversary Update - VT Example");
    printf(CSI "0m");

    // Print a top border - Yellow
    printf(CSI "2;1H");
    PrintHorizontalBorder(Size, true);

    // // Print a bottom border
    printf(CSI "%d;1H", Size.Y - 1);
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
        for (tab = 0; tab < iNumTabStops - 1; tab++)
        {
            PrintVerticalBorder();
            printf("line=%d", line);
            printf("\t"); // advance to next tab stop
        }
        PrintVerticalBorder();// print border at right side
        if (line + 1 != iNumLines)
            printf("\t"); // advance to next tab stop, (on the next line)
    }

    PrintStatusLine("Press any key to demonstrate scroll margins", Size);
    wch = _getwch();

    printf(CSI "3;1H");
    for (line = 0; line < iNumLines * 2; line++)
    {
        printf(CSI "K"); // clear the line
        int tab = 0;
        for (tab = 0; tab < iNumTabStops - 1; tab++)
        {
            PrintVerticalBorder();
            printf("line=%d", line);
            printf("\t"); // advance to next tab stop
        }
        PrintVerticalBorder(); // print border at right side
        if (line + 1 != iNumLines * 2)
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
