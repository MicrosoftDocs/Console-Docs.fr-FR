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
# <a name="high-level-console-modes"></a>Modes de console de haut niveau


Le comportement des fonctions de console de haut niveau est affecté par les modes d’entrée et de sortie de la console. Tous les modes d’entrée de la console suivants sont activés pour la mémoire tampon d’entrée d’une console lors de la création d’une console :

- Mode de saisie de ligne
- Mode de saisie traité
- Mode de saisie d’écho

Les deux modes de sortie de console suivants sont activés pour une mémoire tampon d’écran de console lors de sa création :

- Mode de sortie traité
- Retour en mode de sortie de EOL

Les trois modes d’entrée, ainsi que le mode de sortie traité, sont conçus pour fonctionner ensemble. Il est préférable d’activer ou de désactiver tous ces modes en tant que groupe. Lorsque toutes les sont activées, l’application est dite en mode « cuit », ce qui signifie que la majeure partie du traitement est gérée pour l’application. Lorsque tous les sont désactivés, l’application est en mode « brut », ce qui signifie que l’entrée n’est pas filtrée et que le traitement est laissé à l’application.

Une application peut utiliser la fonction [**GetConsoleMode**](getconsolemode.md) pour déterminer le mode actuel de la mémoire tampon d’entrée ou de mémoire tampon d’entrée d’une console. Vous pouvez activer ou désactiver l’un de ces modes en utilisant les valeurs suivantes dans la fonction [**SetConsoleMode**](setconsolemode.md) . Notez que la définition du mode de sortie d’une mémoire tampon d’écran n’affecte pas le mode de sortie des autres mémoires tampons d’écran.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Mode</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>ENABLE_PROCESSED_INPUT</strong></td>
<td>Utilisé avec un handle d’entrée de console pour obliger le système à traiter toute entrée de modification ou de clé de contrôle du système au lieu de la retourner comme entrée dans l’opération de lecture&#39;tampon s. Si l’entrée de ligne est également activée, les retours arrière et les retours chariot sont correctement gérés. Un retour arrière fait avancer le curseur d’un espace sans affecter le caractère à la position du curseur. Un retour chariot est converti en combinaison retour chariot-saut de ligne. Si le mode d’entrée ECHO est activé et que la sortie doit refléter la modification du système, la sortie traitée doit être activée pour la mémoire tampon d’écran active. Si l’entrée traitée est activée, la combinaison de touches CTRL + C est transmise au gestionnaire approprié, que l’entrée de ligne soit activée ou non. Pour plus d’informations sur les gestionnaires de contrôles, consultez <a href="console-control-handlers.md" data-raw-source="[Console Control Handlers](console-control-handlers.md)">gestionnaires de contrôle de console</a>.</td>
</tr>
<tr class="even">
<td><strong>ENABLE_LINE_INPUT</strong></td>
<td>Utilisé avec un handle d’entrée de console pour provoquer le retour des fonctions <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> et <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> lorsque la touche entrée est enfoncée. Si le mode de saisie de ligne est désactivé, les fonctions retournent lorsqu’un ou plusieurs caractères sont disponibles dans la mémoire tampon d’entrée.</td>
</tr>
<tr class="odd">
<td><strong>ENABLE_ECHO_INPUT</strong></td>
<td>Utilisé avec un handle d’entrée de console pour que l’entrée au clavier lue par la fonction <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> ou <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> soit répercutée dans la mémoire tampon d’écran active. Les caractères sont répercutés uniquement si le processus qui appelle <strong>ReadFile</strong> ou <strong>ReadConsole</strong> a un handle ouvert à la mémoire tampon d’écran active. Le mode ECHO ne peut pas être activé, sauf si l’entrée de ligne est également activée. Le mode de sortie de la mémoire tampon d’écran active affecte la façon dont les entrées en écho sont affichées.</td>
</tr>
<tr class="even">
<td><strong>ENABLE_PROCESSED_OUTPUT</strong></td>
<td>Utilisé avec un handle de mémoire tampon d’écran de la console pour obliger le système à exécuter l’action appropriée pour les caractères de contrôle ANSI écrits dans une mémoire tampon d’écran. Les caractères retour arrière, tabulation, cloche, retour chariot et saut de ligne sont traités. Un caractère de tabulation déplace le curseur sur le taquet de tabulation suivant, qui se produit tous les huit caractères. Un caractère de cloche émet un bref instant.</td>
</tr>
<tr class="odd">
<td><strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong></td>
<td>Utilisé avec un handle de mémoire tampon d’écran de la console pour faire passer la position de sortie actuelle (position du curseur) à la première colonne de la ligne suivante (ligne) lorsque la fin de la ligne actuelle est atteinte. Si le bas de la zone de fenêtre est atteint, l’origine de la fenêtre est déplacée d’une ligne vers le bas. Ce déplacement a pour effet de faire défiler le contenu de la fenêtre vers le haut d’une ligne. Si le bas de la mémoire tampon de l’écran de la console est atteint, le contenu de la mémoire tampon de l’écran de la console fait défiler d’une ligne vers le haut et la ligne supérieure de la mémoire tampon de l’écran de la console est ignorée.
<p>Si ce mode est désactivé, le dernier caractère de la ligne est remplacé par les caractères suivants.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

 

 




