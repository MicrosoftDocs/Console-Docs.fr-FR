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
# <a name="console-virtual-terminal-sequences"></a>Séquences de terminaux virtuels de la console


Les séquences de terminaux virtuels sont des séquences de caractères de contrôle qui peuvent contrôler le mouvement du curseur, le mode couleur/police et d’autres opérations lors de l’écriture dans le flux de sortie. Les séquences peuvent également être reçues sur le flux d’entrée en réponse à une séquence d’informations de requête de flux de sortie ou en tant qu’encodage d’entrée d’utilisateur lorsque le mode approprié est défini.

Vous pouvez utiliser les fonctions [**GetConsoleMode**](getconsolemode.md) et [**SetConsoleMode**](setconsolemode.md) pour configurer ce comportement. Vous trouverez un exemple de la méthode suggérée pour activer les comportements des terminaux virtuels à la fin de ce document.

Le comportement des séquences suivantes est basé sur les technologies d’émulateur de terminal VT100 et dérivées, le plus spécifiquement l’émulateur de terminal xterm. Vous trouverez plus d’informations sur les séquences de terminaux à l’adresse <http://vt100.net> et à <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html> .

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Séquences de sortie


Les séquences de terminaux suivantes sont interceptées par l’hôte de la console lorsqu’elles sont écrites dans le flux de sortie, si l’indicateur activer le \_ \_ \_ traitement des terminaux virtuels est défini sur le descripteur de la mémoire tampon d’écran à l’aide de la fonction [**SetConsoleMode**](setconsolemode.md) . Notez que l’indicateur désactiver le \_ retour automatique à la ligne \_ \_ peut également être utile pour émuler la position du curseur et le comportement du défilement des autres émulateurs de terminal en ce qui concerne les caractères écrits dans la dernière colonne de n’importe quelle ligne.

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Positionnement de curseur simple


Dans toutes les descriptions suivantes, ESC est toujours la valeur hexadécimale 0x1B. Aucun espace ne doit être inclus dans les séquences de terminal. Pour obtenir un exemple de l’utilisation de ces séquences dans la pratique, consultez l' [exemple](#example) à la fin de cette rubrique.

Le tableau suivant décrit les séquences d’échappement simples avec une seule commande d’action directement après le caractère ESC. Ces séquences n’ont pas de paramètres et prennent effet immédiatement.

Toutes les commandes de ce tableau sont généralement équivalentes à l’appel de l’API de la console [**SetConsoleCursorPosition**](setconsolecursorposition.md) pour placer le curseur.

Le déplacement du curseur est limité par la fenêtre d’affichage actuelle dans la mémoire tampon. Le défilement (si disponible) ne se produit pas.


| Séquence | Pratique | Comportement                                                                                                                                      |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| ÉCHAP A    | CUU       | Curseur vers le haut de 1                                                                                                                                |
| ESC B    | CUD       | Curseur en dessous de 1                                                                                                                              |
| ESC C    | CUF       | Curseur vers l’avant (à droite) de 1                                                                                                                   |
| ECHAP D    | CUB       | Curseur vers l’arrière (à gauche) de 1                                                                                                                   |
| ESC M    | Instance réservée        | Inverser l’index : effectue l’opération inverse de \\ n, déplace le curseur d’une ligne vers le haut, conserve la position horizontale, fait défiler le tampon si nécessaire.\* |
| ESC 7    | DECSC     | Enregistrer la position du curseur en mémoire\*\*                                                                                                            |
| ESC 8    | DECSR     | Restaurer la position du curseur à partir de la mémoire\*\*                                                                                                       |



**Remarque**  
\* Si des marges de défilement sont définies, l’RI à l’intérieur des marges défile uniquement le contenu des marges et laisse la fenêtre d’affichage inchangée. (Voir les marges de défilement)

\*\*Aucune valeur n’est enregistrée en mémoire tant que la première utilisation de la commande Save n’est pas utilisée. La seule façon d’accéder à la valeur enregistrée est la commande Restore.



## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Positionnement du curseur


Les tableaux suivants englobent les séquences de types de séquences de contrôle (CSI). Toutes les séquences CSI commencent par ESC (0x1B) suivies de \[ (crochet gauche, 0x5B) et peuvent contenir des paramètres de longueur variable pour spécifier plus d’informations pour chaque opération. Ce sera représenté par le raccourci &lt; n &gt; . Chaque tableau ci-dessous est regroupé par fonctionnalité avec les notes ci-dessous de chaque tableau expliquant le fonctionnement du groupe.

Pour tous les paramètres, les règles suivantes s’appliquent, sauf indication contraire :

- &lt;n &gt; représente la distance à déplacer et est un paramètre facultatif
- Si &lt; n &gt; est omis ou est égal à 0, il est traité comme un 1
- &lt;n &gt; ne peut pas être supérieur à 32 767 (valeur minimale)
- &lt;n &gt; ne peut pas être négatif

Toutes les commandes de cette section sont généralement équivalentes à l’appel de l’API de la console [**SetConsoleCursorPosition**](setconsolecursorposition.md) .

Le déplacement du curseur est limité par la fenêtre d’affichage actuelle dans la mémoire tampon. Le défilement (si disponible) ne se produit pas.


| Séquence                       | Code      | Description                         | Comportement                                                                                                                   |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| ECHAP \[ &lt; n &gt; A             | CUU       | Curseur vers le haut                           | Curseur jusqu’à &lt; n&gt;                                                                                                     |
| ECHAP \[ &lt; n &gt; B             | CUD       | Curseur en dessous                         | Curseur en dessous de &lt; n&gt;                                                                                                   |
| ECHAP \[ &lt; n &gt; C             | CUF       | Curseur vers l’avant                      | Curseur vers l’avant (à droite) de &lt; n&gt;                                                                                        |
| ECHAP \[ &lt; n &gt; D             | CUB       | Curseur vers l’arrière                     | Curseur vers l’arrière (à gauche) de &lt; n&gt;                                                                                        |
| ECHAP \[ &lt; n &gt; E             | CNL       | Ligne suivante du curseur                    | Curseur vers le début du &lt; n &gt; ième trait dans la fenêtre d’affichage                                                               |
| ECHAP \[ &lt; n &gt; F             | PERSONNALISATION       | Ligne précédente du curseur                | Curseur jusqu’au début de &lt; &gt; la n ième ligne dans la fenêtre d’affichage                                                                 |
| ECHAP \[ &lt; n &gt; G             | CHA       | Curseur horizontal absolu          | Le curseur se déplace d’une position à une &lt; &gt; position horizontale dans la ligne active                                                      |
| ECHAP \[ &lt; n &gt; d             | VPA       | Position de ligne verticale absolue     | Le curseur se déplace vers la &lt; n &gt; ième position verticale dans la colonne actuelle                                                  |
| ESC \[ &lt; y &gt; ; &lt; x &gt; H | FOOTBALL       | Position du curseur                     | \*Le curseur est déplacé vers &lt; x &gt; ; &lt; &gt; coordonnée y dans la fenêtre d’affichage, où &lt; x &gt; est la colonne de la &lt; &gt; ligne y |
| ESC \[ &lt; y &gt; ; &lt; x &gt; f | HVP       | Position verticale horizontale        | \*Le curseur est déplacé vers &lt; x &gt; ; &lt; &gt; coordonnée y dans la fenêtre d’affichage, où &lt; x &gt; est la colonne de la &lt; &gt; ligne y |
| ESC \[ s                       | ANSISYSSC | Enregistrer le curseur – Ansi.sys l’émulation    | \*\*Sans paramètre, effectue une opération enregistrer le curseur comme DECSC                                                        |
| ESC \[ u                       | ANSISYSSC | Curseur de restauration – émulation de Ansi.sys | \*\*Sans paramètre, effectue une opération de restauration de curseur comme DECRC                                                     |



**Remarque**  
\*&lt;&gt; &lt; les paramètres x et y &gt; ont les mêmes limitations que &lt; n &gt; ci-dessus. Si &lt; x &gt; et &lt; y &gt; sont omis, ils sont définis sur 1 ; 1.

\*\*ANSI.sys documentation historique se trouve dans <https://msdn.microsoft.com/library/cc722862.aspx> et est implémentée pour des raisons pratiques/de compatibilité.



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Visibilité du curseur


Les commandes suivantes contrôlent la visibilité du curseur et son état de clignotement. Les séquences DECTCEM sont généralement équivalentes à l’appel de l’API de console [**SetConsoleCursorInfo**](setconsolecursorinfo.md) pour basculer la visibilité du curseur.


| Séquence      | Code    | Description                  | Comportement                  |
|---------------|---------|------------------------------|---------------------------|
| Échap \[ ? 12 h | ATT160  | Curseur de texte activer le clignotement  | Démarrer le clignotement du curseur |
| Échap \[ ? 12 l | ATT160  | Curseur de texte désactiver le clignotement  | Arrêter le clignotement du curseur  |
| Échap \[ ? 25 h | DECTCEM | Affichage du mode d’activation du curseur de texte | Afficher le curseur           |
| Échap \[ ? 25 l | DECTCEM | Masquage du mode d’activation du curseur de texte | Masquer le curseur           |



## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Positionnement de la fenêtre d’affichage


Toutes les commandes de cette section sont généralement équivalentes à l’appel de l’API de console [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) pour déplacer le contenu de la mémoire tampon de la console.

**Attention**  Les noms de commande sont trompeurs. Le défilement fait référence à la direction vers laquelle le texte se déplace au cours de l’opération, et non à la façon dont la fenêtre d’affichage semble bouger.




| Séquence           | Code | Description | Comportement                                                                                             |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| ECHAP \[ &lt; n &gt; S | Unités de diffusion en continu   | Faire défiler vers le haut   | Faire défiler le texte de &lt; n &gt; . Également appelée panoramique, les nouvelles lignes remplissent à partir du bas de l’écran |
| ECHAP \[ &lt; n &gt; T | SD   | Faire défiler vers le bas | Faites défiler la liste de &lt; n &gt; . Également appelée panoramique, les nouvelles lignes remplissent à partir du haut de l’écran         |



Le texte est déplacé à partir de la ligne sur laquelle se trouve le curseur. Si le curseur se trouve sur la ligne du milieu de la fenêtre d’affichage, le défilement vers le haut déplace la moitié inférieure de la fenêtre d’affichage et insère des lignes vides en bas. Faire défiler vers le haut déplace la moitié supérieure des lignes de la fenêtre d’affichage et insère de nouvelles lignes en haut.

Il est également important de noter que le défilement vers le haut et vers le haut est également affecté par les marges de défilement. Le défilement vers le haut et vers le haut n’affecte pas les lignes situées en dehors des marges de défilement.

La valeur par défaut de &lt; n &gt; est 1 et la valeur peut éventuellement être omise.

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Modification du texte


Toutes les commandes de cette section sont généralement équivalentes à l’appel d’API de console [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)et [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) pour modifier le contenu de la mémoire tampon de texte.


| Séquence           | Code | Description      | Comportement                                                                                                                                          |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| ECHAP \[ &lt; n&gt; @ | Centr  | Insérer un caractère | Insérer &lt; n &gt; espaces à la position actuelle du curseur, en décalant tout le texte existant vers la droite. Le texte qui quitte l’écran à droite est supprimé. |
| ECHAP \[ &lt; n &gt; P | DCH  | Supprimer le caractère | Supprime &lt; &gt; les n caractères à la position actuelle du curseur, en les décalant dans les espaces à partir du bord droit de l’écran.                       |
| ECHAP \[ &lt; n &gt; X | YÈTCH  | Effacer le caractère  | Efface les &lt; n &gt; caractères de la position actuelle du curseur en les remplaçant par un espace.                                           |
| ECHAP \[ &lt; n &gt; L | IL   | Insérer une ligne      | Insère &lt; n &gt; lignes dans la mémoire tampon à la position du curseur. La ligne sur laquelle se trouve le curseur et les lignes au-dessous de celle-ci sont décalées vers le bas.         |
| ECHAP \[ &lt; n &gt; M | DL   | Supprimer la ligne      | Supprime &lt; n &gt; lignes de la mémoire tampon, en commençant par la ligne sur laquelle se trouve le curseur.                                                                  |



**Remarque**  
Pour IL et DL, seules les lignes des marges de défilement (voir marges de défilement) sont affectées. Si aucune marge n’est définie, les bordures de marge par défaut sont la fenêtre d’affichage actuelle. Si les lignes sont décalées en dessous des marges, elles sont ignorées. Lorsque des lignes sont supprimées, des lignes vides sont insérées en bas des marges, les lignes extérieures à la fenêtre d’affichage ne sont jamais affectées.

Pour chacune des séquences, la valeur par défaut pour &lt; n &gt; s’il est omis est 0.



Pour les commandes suivantes, le paramètre &lt; n &gt; a 3 valeurs valides :

- 0 efface de la position actuelle du curseur jusqu’à la fin de la ligne/de l’affichage
- 1 efface à partir du début de la ligne/s’affiche jusqu’à la position actuelle du curseur et y compris
- 2 efface l’intégralité de la ligne/de l’affichage


| Séquence           | Code | Description      | Comportement                                                                                     |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| ECHAP \[ &lt; n &gt; J | ED   | Effacer dans l’affichage | Remplacer tout le texte de la fenêtre d’affichage ou de l’écran en cours spécifié par &lt; n &gt; espaces |
| ECHAP \[ &lt; n &gt; K | CYRILLIQUE   | Effacer à la ligne    | Remplacer tout le texte de la ligne par le curseur spécifié par &lt; n &gt; espaces    |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Mise en forme du texte


Toutes les commandes de cette section sont généralement équivalentes à l’appel des API de console [**SetConsoleTextAttribute**](setconsoletextattribute.md) pour ajuster la mise en forme de toutes les écritures futures dans la mémoire tampon de texte de sortie de la console.

Cette commande est spéciale dans la mesure où la &lt; &gt; position n ci-dessous peut accepter entre 0 et 16 paramètres séparés par des points-virgules.

Quand aucun paramètre n’est spécifié, il est traité de la même manière qu’un seul paramètre 0.


| Séquence           | Code | Description            | Comportement                                                        |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| ECHAP \[ &lt; n &gt; m | SGR  | Définir un rendu graphique | Définir le format de l’écran et du texte comme spécifié par &lt; n&gt; |



Le tableau de valeurs suivant peut être utilisé dans &lt; n &gt; pour représenter différents modes de mise en forme.

Les modes de mise en forme s’appliquent de gauche à droite. L’application d’options de mise en forme concurrentes entraînera la précédence de l’option la plus à droite.

Pour les options qui spécifient des couleurs, les couleurs sont utilisées comme défini dans la table des couleurs de la console, qui peut être modifiée à l’aide de l’API [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) . Si la table est modifiée pour que la position « bleu » dans la table affiche un ombrage RVB rouge, tous les appels au **premier plan bleu** affichent cette couleur rouge jusqu’à ce qu’ils soient modifiés.


| Value | Description               | Comportement                                                           |
|-------|---------------------------|--------------------------------------------------------------------|
| 0     | Default                   | Retourne tous les attributs à l’État par défaut avant la modification  |
| 1     | Gras/vif               | Applique l’indicateur de luminosité/intensité à la couleur de premier plan              |
| 4     | Souligner                 | Ajoute un soulignement                                                     |
| 24    | Pas de soulignement              | Supprime le soulignement                                                  |
| 7     | Négatif                  | Permute les couleurs de premier plan et d’arrière-plan                             |
| 27    | Positif (pas de négatif)    | Retourne le premier plan/l’arrière-plan à normal                            |
| 30    | Noir de premier plan          | Applique un noir clair ou non gras au premier plan                        |
| 31    | Premier plan rouge            | Applique un rouge vif ou non gras au premier plan                          |
| 32    | Vert de premier plan          | Applique un vert clair ou non gras au premier plan                        |
| 33    | Premier plan jaune         | Applique le jaune clair ou non gras au premier plan                       |
| 34    | Bleu de premier plan           | Applique le bleu clair ou non gras au premier plan                         |
| 35    | Magenta de premier plan        | Applique le magenta non gras/clair au premier plan                      |
| 36    | Cyan de premier plan           | Applique un cyan clair ou non gras au premier plan                         |
| 37    | Blanc de premier plan          | Applique un blanc clair ou non gras au premier plan                        |
| 38    | Premier plan étendu       | Applique la valeur de couleur étendue au premier plan (voir les détails ci-dessous). |
| 39    | Premier plan par défaut        | Applique uniquement la partie de premier plan des valeurs par défaut (voir 0).        |
| 40    | Arrière-plan noir          | Applique un noir non gras/clair à l’arrière-plan                        |
| 41    | Arrière-plan rouge            | Applique le rouge non gras/clair à l’arrière-plan                          |
| 42    | Arrière-plan vert          | Applique un vert clair ou non gras à l’arrière-plan                        |
| 43    | Arrière-plan jaune         | Applique le jaune non gras/clair à l’arrière-plan                       |
| 44    | Arrière-plan bleu           | Applique le bleu clair ou non gras à l’arrière-plan                         |
| 45    | Arrière-plan magenta        | Applique le magenta non gras/clair à l’arrière-plan                      |
| 46    | Arrière-plan cyan           | Applique un cyan clair ou non gras à l’arrière-plan                         |
| 47    | Arrière-plan blanc          | Applique un blanc clair ou non gras à l’arrière-plan                        |
| 48    | Arrière-plan étendu       | Applique la valeur de couleur étendue à l’arrière-plan (voir les détails ci-dessous). |
| 49    | Arrière-plan par défaut        | Applique uniquement la partie d’arrière-plan des valeurs par défaut (voir 0).        |
| 90    | Noir de premier plan   | Applique le noir gras/clair au premier plan                            |
| 91    | Rouge de premier plan     | Applique le rouge gras/vif au premier plan                              |
| 92    | Vert de premier plan brillant   | Applique le vert gras/vif au premier plan                            |
| 93    | Clair de premier plan jaune  | Applique le jaune gras/clair au premier plan                           |
| 94    | Bleu de premier plan brillant    | Applique le bleu gras/clair au premier plan                             |
| 95    | Magenta de premier plan | Applique le magenta gras/vif au premier plan                          |
| 96    | Cyan de premier plan    | Applique le cyan gras/vif au premier plan                             |
| 97    | Blanc de premier plan   | Applique le gras/blanc brillant au premier plan                            |
| 100   | Arrière-plan lumineux noir   | Applique un noir gras/vif à l’arrière-plan                            |
| 101   | Arrière-plan lumineux rouge     | Applique le rouge gras/vif à l’arrière-plan                              |
| 102   | Arrière-plan brillant vert   | Applique le vert gras/vif à l’arrière-plan                            |
| 103   | Arrière-plan lumineux jaune  | Applique le jaune gras/vif à l’arrière-plan                           |
| 104   | Arrière-plan bleu vif    | Applique le bleu gras/clair à l’arrière-plan                             |
| 105   | Arrière-plan magenta clair | Applique le magenta gras/vif à l’arrière-plan                          |
| 106   | Arrière-plan lumineux cyan    | Applique le cyan gras/vif à l’arrière-plan                             |
| 107   | Blanc d’arrière-plan brillant   | Applique le blanc gras/clair à l’arrière-plan                            |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Couleurs étendues

Certains émulateurs de terminaux virtuels prennent en charge une palette de couleurs supérieure aux 16 couleurs fournies par la console Windows. Pour ces couleurs étendues, la console Windows choisit la couleur appropriée la plus proche de la table 16 couleurs existante pour l’affichage. Contrairement aux valeurs SGR classiques ci-dessus, les valeurs étendues consomment des paramètres supplémentaires après l’indicateur initial, conformément au tableau ci-dessous.


| Sous-séquence SGR                            | Description                                                                                 |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| 38 ; 2 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt; | Définir la couleur de premier plan sur la valeur RVB spécifiée dans les &lt; &gt; paramètres r, &lt; g &gt; , &lt; b &gt;\* |
| 48 ; 2 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt; | Définir la couleur d’arrière-plan sur la valeur RVB spécifiée dans les &lt; &gt; paramètres r, &lt; g &gt; , &lt; b &gt;\* |
| 38 ; 5,5 &lt;s&gt;                         | Définir la couleur de premier plan sur &lt; &gt; l’index s dans la table de couleurs 88 ou 256\*                          |
| 48 ; 5,5 &lt;s&gt;                         | Définir la couleur d’arrière-plan sur &lt; &gt; l’index s dans le tableau de couleurs 88 ou 256\*                          |



\*Les palettes de couleurs 88 et 256 gérées en interne pour la comparaison sont basées sur l’émulateur de terminal xterm. Les tables de comparaison et d’arrondi ne peuvent pas être modifiées pour l’instant.


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Couleurs de l’écran


La commande suivante permet à l’application de définir les valeurs de la palette de couleurs d’écran sur n’importe quelle valeur RVB.

Les valeurs RVB doivent être des valeurs hexadécimales comprises entre `0` et `ff` , et séparées par le caractère de barre oblique inverse (par exemple, `rgb:1/24/86` ).

Notez que cette séquence est une séquence de « commande du système d’exploitation » OSC, et non un CSI comme un grand nombre des autres séquences listées, et qu’elles commencent par « \\ X1B \] », et non pas par « \\ X1B \[ ».


| Séquence                                                           | Description          | Comportement                                                                                                     |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| ESC \] 4 ; &lt; i &gt; ; RVB : &lt; r &gt;  /  &lt; g &gt;  /  &lt; b &gt; ESC | Modifier les couleurs de l’écran | Définit l’index de la palette &lt; de couleurs de l’écran &gt; sur les valeurs RVB spécifiées dans &lt; r &gt; , &lt; g &gt; , &lt; b&gt; |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Modifications du mode


Il s’agit de séquences qui contrôlent les modes d’entrée. Il existe deux ensembles différents de modes de saisie : le mode touches de curseur et le mode touches du pavé numérique. Le mode touches de curseur contrôle les séquences émises par les touches de direction, ainsi que le mode de démarrage et de fin, tandis que le mode touches de clavier contrôle les séquences émises par les touches sur le pavé numérique, ainsi que les touches de fonction.

Chacun de ces modes est un simple paramètre booléen : le mode touches de curseur est normal (valeur par défaut) ou application, et le mode touches du clavier est soit numérique (valeur par défaut), soit application.

Consultez les sections touches de curseur et touches de fonction & pavé numérique pour les séquences émises dans ces modes.


| Séquence     | Code    | Description                                            | Comportement                                                |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| ECHAP =        | DECKPAM | Activer le mode d’application du clavier                         | Les touches du pavé numérique émettent leurs séquences en mode application. |
| Escudo &gt;     | DECKPNM | Activer le mode numérique du pavé numérique                             | Les touches du pavé numérique émettent leurs séquences de mode numérique.     |
| Échap \[ ? 1 h | DECCKM  | Activer le mode d’application des touches de curseur                    | Les touches du pavé numérique émettent leurs séquences en mode application. |
| Échap \[ ? 1 l | DECCKM  | Désactiver le mode d’application des touches de curseur (utiliser le mode normal) | Les touches du pavé numérique émettent leurs séquences de mode numérique.     |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>État de la requête


Toutes les commandes de cette section sont généralement équivalentes à l’appel de la commande obtenir des \* API de console pour récupérer des informations d’État sur l’état actuel de la mémoire tampon de la console.

**Remarque**  Ces requêtes émettent leurs réponses dans le flux d’entrée de la console immédiatement après leur reconnaissance sur le flux de sortie pendant que l’activation du \_ \_ traitement des terminaux virtuels \_ est définie. L' \_ \_ indicateur d’entrée activer le terminal virtuel \_ ne s’applique pas aux commandes de requête, car il est supposé qu’une application qui effectue la requête doit toujours recevoir la réponse.




| Séquence   | Code    | Description            | Comportement                                                                                                               |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| ESC \[ 6 n | DECXCPR | Position du curseur de rapport | Émettez la position du curseur en tant que : ESC \[ &lt; r &gt; ; &lt; c &gt; r où &lt; R &gt; = ligne de curseur et &lt; c &gt; = colonne de curseur |
| ESC \[ 0 c | DA      | Attributs de l’appareil      | Signalez l’identité du terminal. Émettra « \\ X1B \[ ? 1 ; 0C », indiquant « VT101 sans options ».                            |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Quitte


Alors que la console Windows s’attend traditionnellement à ce que les onglets soient exclusivement dotés de huit caractères, \* nix les applications utilisant certaines séquences peuvent manipuler l’emplacement où les taquets de tabulation se trouvent dans les fenêtres de la console pour optimiser le déplacement des curseurs par l’application.

Les séquences suivantes permettent à une application de définir les emplacements de taquet de tabulation dans la fenêtre de console, de les supprimer et de naviguer entre elles.


| Séquence           | Code | Description                     | Comportement                                                                                                                                                                                                                    |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC H              | HTS  | Ensemble de tabulations horizontales              | Définit un taquet de tabulation dans la colonne actuelle dans laquelle se trouve le curseur.                                                                                                                                                                     |
| ECHAP \[ &lt; n &gt; I | CHT  | Onglet curseur horizontal (suivant) | Avancer le curseur jusqu’à la colonne suivante (sur la même ligne) avec un taquet de tabulation. S’il n’y a plus de taquets de tabulation, passez à la dernière colonne de la ligne. Si le curseur se trouve dans la dernière colonne, passez à la première colonne de la ligne suivante. |
| ECHAP \[ &lt; n &gt; Z | CBT  | Onglet de curseur vers l’arrière            | Déplacez le curseur vers la colonne précédente (sur la même ligne) avec un taquet de tabulation. S’il n’y a plus de taquets de tabulation, déplace le curseur vers la première colonne. Si le curseur se trouve dans la première colonne, ne déplace pas le curseur.              |
| ESC \[ 0 g         | TBC  | Tabulation effacer (colonne actuelle)      | Efface le taquet de tabulation dans la colonne actuelle, s’il en existe un. Sinon, ne fait rien.                                                                                                                                         |
| ESC \[ 3 g         | TBC  | Onglet effacer (toutes les colonnes)         | Efface tous les taquets de tabulation actuellement définis.                                                                                                                                                                                         |



- Pour CHT et CBT, &lt; n &gt; est un paramètre facultatif qui (valeur par défaut = 1) indique le nombre d’incréments du curseur dans la direction spécifiée.
- Si aucun taquet de tabulation n’est défini via HTS, CHT et CBT traiteront la première et la dernière colonnes de la fenêtre, car les deux seuls taquets de tabulation.
- L’utilisation de HTS pour définir un taquet de tabulation entraîne également l’accès de la console au taquet de tabulation suivant sur la sortie d’un caractère de tabulation (0x09, ' \\ t'), de la même manière que CHT.

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Désigner le jeu de caractères


Les séquences suivantes permettent à un programme de modifier le mappage du jeu de caractères actif. Cela permet à un programme d’émettre des caractères ASCII de 7 bits, mais de les afficher sous la forme d’autres glyphes sur l’écran de terminal lui-même. Actuellement, les deux seuls jeux de caractères pris en charge sont ASCII (par défaut) et le jeu de caractères graphiques spéciaux DEC. Consultez <http://vt100.net/docs/vt220-rm/table2-4.html> pour obtenir la liste de tous les caractères représentés par le jeu de caractères spéciaux du DEC.


| Séquence | Description                                | Comportement                      |
|----------|--------------------------------------------|-------------------------------|
| ÉCHAP (0  | Désigner le jeu de caractères – dessin de ligne DEC | Active le mode de dessin de la ligne DEC |
| ÉCHAP (B  | Désigner le jeu de caractères – ASCII US         | Active le mode ASCII (par défaut)  |



En particulier, le mode de dessin de la ligne DEC est utilisé pour dessiner les bordures dans les applications console. Le tableau suivant répertorie les correspondances de caractères ASCII avec le caractère de dessin de ligne.


| Hex  | ASCII | Dessin de ligne DEC |
|------|-------|------------------|
| 0x6a | j     | ┘                |
| 0x6b | k     | ┐                |
| 0x6C | l     | ┌                |
| 0x6d | m     | └                |
| 0x6e | n     | ┼                |
| 0x71 | q     | ─                |
| 0x74 | t     | ├                |
| 0x75 | u     | ┤                |
| 0x76 | v     | ┴                |
| 0x77 | w     | ┬                |
| 0x78 | x     | │                |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Marges de défilement


Les séquences suivantes permettent à un programme de configurer la « zone de défilement » de l’écran qui est affectée par les opérations de défilement. Il s’agit d’un sous-ensemble des lignes qui sont ajustées lorsque l’écran défilerait, par exemple, sur un' \\ n’ou un RI. Ces marges affectent également les lignes modifiées par la ligne d’insertion (IL) et la ligne de suppression (DL), le défilement vers le haut (SU) et le défilement vers le haut (SD).

Les marges de défilement peuvent être particulièrement utiles pour disposer d’une partie de l’écran qui ne défile pas lorsque le reste de l’écran est rempli, par exemple avec une barre de titre en haut ou une barre d’État au bas de votre application.

Pour DECSTBM, il existe deux paramètres facultatifs, &lt; t &gt; et &lt; b &gt; , qui sont utilisés pour spécifier les lignes qui représentent les lignes supérieure et inférieure de la zone de défilement, inclusivement. Si les paramètres sont omis, &lt; t est &gt; défini par défaut sur 1 et &lt; b &gt; sur la hauteur de la fenêtre d’affichage actuelle.

Les marges de défilement sont par mémoire tampon. il est donc important que l’autre mémoire tampon et la mémoire tampon principale maintiennent des paramètres de marges de défilement distincts (de sorte qu’une application en plein écran dans l’autre mémoire tampon n’incorrompra pas les marges de la mémoire tampon principale).


| Séquence                       | Code    | Description          | Comportement                                       |
|--------------------------------|---------|----------------------|------------------------------------------------|
| ESC \[ &lt; t &gt; ; &lt; b &gt; r | DECSTBM | Définir la zone de défilement | Définit les marges de défilement VT de la fenêtre d’affichage. |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Titre de la fenêtre


Les commandes suivantes permettent à l’application de définir le titre de la fenêtre de console sur le &lt; paramètre de chaîne donné &gt; . La chaîne doit contenir moins de 255 caractères à accepter. Cela équivaut à appeler SetConsoleTitle avec la chaîne donnée.

Notez que ces séquences sont des séquences de « commande du système d’exploitation », et non d’un CSI comme nombre des autres séquences répertoriées. par conséquent, commence par « \\ X1B \] », et non pas par « \\ X1B \[ ».


| Séquence                      | Description               | Comportement                                           |
|-------------------------------|---------------------------|----------------------------------------------------|
| ECHAP \] 0 ; &lt; chaîne &gt; bel | Définir l’icône et le titre de la fenêtre | Définit le titre de la fenêtre de la console sur &lt; String &gt; . |
| ESC \] 2 ; &lt; chaîne &gt; bel | Définir le titre de la fenêtre          | Définit le titre de la fenêtre de la console sur &lt; String &gt; . |



Le caractère de fin ici est le caractère « cloche », « \\ x07 »

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Mémoire tampon d’écran de remplacement


\*Les applications de style nix utilisent souvent une mémoire tampon d’écran de remplacement, afin qu’elles puissent modifier l’ensemble du contenu de la mémoire tampon, sans affecter l’application qui les a démarrées. La mémoire tampon de remplacement est exactement celle des dimensions de la fenêtre, sans aucune région scrollback.

Pour obtenir un exemple de ce comportement, pensez à la façon dont vim est lancé à partir de bash. Vim utilise l’intégralité de l’écran pour modifier le fichier, puis le retour à bash laisse la mémoire tampon d’origine inchangée.


| Séquence           | Description                 | Comportement                                   |
|--------------------|-----------------------------|--------------------------------------------|
| Échap \[ ? 1 0 4 9 h | Utiliser une autre mémoire tampon d’écran | Bascule vers une nouvelle mémoire tampon d’écran. |
| Échap \[ ? 1 0 4 9 l | Utiliser la mémoire tampon de l’écran principal      | Bascule vers la mémoire tampon principale.               |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Largeur de la fenêtre


Les séquences suivantes peuvent être utilisées pour contrôler la largeur de la fenêtre de console. Ils sont à peu près équivalents à l’appel de l’API de la console SetConsoleScreenBufferInfoEx pour définir la largeur de la fenêtre.


| Séquence     | Code    | Description                  | Comportement                                    |
|--------------|---------|------------------------------|---------------------------------------------|
| Échap \[ ? 3 h | DECCOLM | Définir le nombre de colonnes sur 132 | Définit la largeur de la console sur 132 colonnes en largeur. |
| Échap \[ ? 3 l | DECCOLM | Définir le nombre de colonnes sur 80  | Définit la largeur de la console sur 80 colonnes en largeur.  |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Réinitialisation logicielle


La séquence suivante peut être utilisée pour réinitialiser certaines propriétés à leurs valeurs par défaut. Les propriétés suivantes sont réinitialisées aux valeurs par défaut suivantes (elles sont également répertoriées dans les séquences qui contrôlent ces propriétés) :

- Visibilité du curseur : visible (DECTEM)
- Pavé numérique : mode numérique (DECNKM)
- Mode touches de curseur : mode normal (DECCKM)
- Marges supérieure et inférieure : haut = 1, bas = hauteur de la console (DECSTBM)
- Jeu de caractères : ASCII US
- Rendu graphique : par défaut/désactivé (SGR)
- Enregistrer l’état du curseur : position de départ (0, 0) (DECSC)


| Séquence   | Code   | Description | Comportement                                           |
|------------|--------|-------------|----------------------------------------------------|
| Échap \[ ! p | DECSTR | Réinitialisation logicielle  | Réinitialiser certains paramètres de terminal à leurs valeurs par défaut. |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Séquences d’entrée


Les séquences de terminaux suivantes sont émises par l’hôte de la console sur le flux d’entrée si l' \_ \_ indicateur d’entrée activer le terminal virtuel \_ est défini sur le descripteur de la mémoire tampon d’entrée à l’aide de l’indicateur SetConsoleMode.

Il existe deux modes internes qui contrôlent les séquences émises pour les touches d’entrée données, le mode des touches de curseur et le mode touches du pavé numérique. Celles-ci sont décrites dans la section modifications de mode.

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Touches de curseur


| Clé         | Mode Normal | Mode d’application |
|-------------|-------------|------------------|
| Flèche haut    | Échap \[ A    | ECHAP O A          |
| Flèche Bas  | ESC \[ B    | ECHAP O B          |
| Flèche droite | ESC \[ C    | ECHAP O C          |
| Gauche  | ECHAP \[ D    | ECHAP O D          |
| Accueil        | ESC \[ H    | ECHAP O H          |
| End         | ESC \[ F    | ECHAP O F          |



En outre, si la touche CTRL est enfoncée avec l’une de ces clés, les séquences suivantes sont émises à la place, quel que soit le mode des touches de curseur :


| Clé                | N’importe quel mode       |
|--------------------|----------------|
| Ctrl + flèche haut    | ESC \[ 1 ; 5 A |
| Ctrl + flèche bas  | ESC \[ 1 ; 5 B |
| Ctrl + flèche droite | ESC \[ 1 ; 5 C |
| Ctrl + flèche gauche  | ESC \[ 1 ; 5 D |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Touches de fonction & pavé numérique


| Clé       | Séquence     |
|-----------|--------------|
| Retour arrière | 0x7F (DEL)   |
| Suspendre     | 0x1A (SUB)   |
| Caractère d'échappement    | 0x1B (ESC)   |
| Insérer    | ESC \[ 2 ~   |
| Supprimer    | ESC \[ 3 ~   |
| Page précédente   | ESC \[ 5 ~   |
| Page suivante | ESC \[ 6 ~   |
| F1        | ECHAP O P      |
| F2        | ECHAP O Q      |
| F3        | ECHAP O R      |
| F4        | ECHAP O S      |
| F5        | ECHAP \[ 1 5 ~ |
| F6        | ECHAP \[ 1 7 ~ |
| F7        | ECHAP \[ 1 8 ~ |
| F8        | ECHAP \[ 1 9 ~ |
| F9        | ECHAP \[ 2 0 ~ |
| F10       | ECHAP \[ 2 1 ~ |
| F11       | ECHAP \[ 2 3 ~ |
| F12       | ECHAP \[ 2 4 ~ |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modificateurs

La touche Alt est traitée en préfixant la séquence par un caractère d’échappement : Échap &lt; c &gt; où &lt; c &gt; est le caractère passé par le système d’exploitation. ALT + CTRL est gérée de la même façon, à ceci près que le système d’exploitation aura au préalable déplacé la &lt; &gt; clé c vers le caractère de contrôle approprié, qui sera relayé à l’application.

La touche CTRL est généralement transmise à partir du système. Il s’agit généralement d’un caractère unique déplacé vers le bout dans l’espace réservé du caractère de contrôle (0x0-0x1F). Par exemple, Ctrl + @ (0x40) devient NUL (0x00), CTRL + \[ (0x5B) devient ESC (0x1B), etc. Quelques combinaisons de touches Ctrl sont traitées de façon spéciale selon le tableau suivant :


| Clé                | Séquence       |
|--------------------|----------------|
| Ctrl + espace       | 0x00 (NUL)     |
| Ctrl + flèche haut    | ESC \[ 1 ; 5 A |
| Ctrl + flèche bas  | ESC \[ 1 ; 5 B |
| Ctrl + flèche droite | ESC \[ 1 ; 5 C |
| Ctrl + flèche gauche  | ESC \[ 1 ; 5 D |



**Remarque**  CTRL gauche + droite Alt est traité comme AltGr. Lorsqu’ils sont affichés ensemble, ils sont supprimés et la valeur Unicode du caractère présenté par le système est transmise à la cible. Le système convertit les valeurs AltGr en fonction des paramètres d’entrée système actuels.



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Extraits


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span id="example"></span><span id="EXAMPLE"></span>Exemple de séquences de terminaux SGR

Le code suivant fournit plusieurs exemples de mise en forme du texte.

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

**Remarque**  Dans l’exemple précédent, la chaîne' `\x1b[31m` 'correspond à l’implémentation de **ESC \[ &lt; n &gt; m** avec &lt; n &gt; étant 31.



Le graphique suivant montre la sortie de l’exemple de code précédent.

![sortie de la console à l’aide de la commande SGR](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Exemple d’activation du traitement des terminaux virtuels

Le code suivant fournit un exemple de la méthode recommandée pour activer le traitement des terminaux virtuels pour une application. L’objectif de l’exemple est de démontrer les éléments suivants :

1. Le mode existant doit toujours être récupéré via GetConsoleMode et analysé avant d’être défini avec SetConsoleMode.

2. Vérification de la valeur retournée `0` par SetConsoleMode et GetLastError retourne \_ le paramètre de l’état non valide \_ est le mécanisme actuel à déterminer lors de l’exécution sur un système de niveau supérieur. Une application recevant un paramètre d’état \_ non valide \_ avec l’un des nouveaux indicateurs de mode de console dans le champ de bits doit dégrader le comportement de manière appropriée, puis réessayer.

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

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Exemple de sélection de fonctionnalités de mise à jour anniversaire

L’exemple suivant est destiné à être un exemple plus robuste de code utilisant une variété de séquences d’échappement pour manipuler la mémoire tampon, en mettant l’accent sur les fonctionnalités ajoutées dans la mise à jour anniversaire pour Windows 10.

Cet exemple utilise l’autre mémoire tampon d’écran, la manipulation des taquets de tabulation, la définition des marges de défilement et la modification du jeu de caractères.

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








