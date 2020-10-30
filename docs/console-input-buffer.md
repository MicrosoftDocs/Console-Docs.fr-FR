---
title: Mémoire tampon d’entrée d’une console
description: Chaque console possède une mémoire tampon d’entrée qui contient une file d’attente d’enregistrements d’événements d’entrée.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_console\_input\_buffer'
- base.console\_input\_buffer
- consoles.console\_input\_buffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6e536658-8a27-478e-82ee-d1e11f351301
ms.openlocfilehash: 9b210e07fd2531b2f58130f4b96ad31a374923f4
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039207"
---
# <a name="console-input-buffer"></a>Mémoire tampon d’entrée d’une console

Chaque console possède une mémoire tampon d’entrée qui contient une file d’attente d’enregistrements d’événements d’entrée. Lorsque la fenêtre d’une console a le focus clavier, une console met en forme chaque événement d’entrée (par exemple, une frappe de touche, un mouvement de la souris ou un clic sur le bouton de la souris) comme un enregistrement d’entrée qu’il place dans la mémoire tampon d’entrée de la console.

Les applications peuvent accéder indirectement à la mémoire tampon d’entrée d’une console à l’aide des [fonctions d’e/s de console de haut niveau](high-level-console-input-and-output-functions.md), ou directement à l’aide des [fonctions d’entrée de la console de bas niveau](low-level-console-input-functions.md). Les fonctions d’entrée de haut niveau filtrent et traitent les données dans la mémoire tampon d’entrée, en retournant uniquement un flux de caractères d’entrée. Les fonctions d’entrée de bas niveau permettent aux applications de lire des enregistrements d’entrée directement à partir de la mémoire tampon d’entrée d’une console, ou de placer des enregistrements d’entrée dans la mémoire tampon d’entrée. Pour ouvrir un handle vers la mémoire tampon d’entrée d’une console, spécifiez la valeur **CONIN $** dans un appel à la fonction [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) .

Un enregistrement d’entrée est une structure contenant des informations sur le type d’événement qui s’est produit (clavier, souris, redimensionnement de fenêtre, focus ou événement de menu), ainsi que des détails spécifiques sur l’événement. Le membre **eventType** dans une structure [**d' \_ enregistrement d’entrée**](input-record-str.md) indique quel type d’événement est contenu dans l’enregistrement.

Les événements de focus et de menu sont placés dans la mémoire tampon d’entrée d’une console pour une utilisation interne par le système et doivent être ignorés par les applications.

## <a name="keyboard-events"></a>Événements de clavier

Les événements de clavier sont générés lorsqu’une touche est enfoncée ou libérée. Cela comprend les clés de contrôle. Toutefois, la touche ALT a une signification particulière pour le système lorsqu’elle est appuyée et libérée sans être associée à un autre caractère, et elle n’est pas transmise à l’application. En outre, la combinaison de touches CTRL + C n’est pas transmise si le handle d’entrée est en mode traité.

Si l’événement d’entrée est une séquence de touches, le membre d' **événement** dans l' [**\_ enregistrement d’entrée**](input-record-str.md) est une structure d' [**\_ \_ enregistrement d’événement clé**](key-event-record-str.md) contenant les informations suivantes :

- Valeur booléenne indiquant si la touche a été enfoncée ou libérée.
- Nombre de répétitions qui peut être supérieur à un lorsqu’une touche est maintenue enfoncée.
- Code de la touche virtuelle, identifiant la clé donnée de façon indépendante du périphérique.
- Code d’analyse virtuelle, indiquant la valeur dépendante du périphérique générée par le matériel clavier.
- ™ Unicode ou caractère ANSI traduit.
- Variable d’indicateur qui indique l’état des touches de contrôle (ALT, CTRL, Maj, Verr. NUM, verrou de défilement et touches de verrouillage en MAJUSCULEs) et indique si une touche améliorée a été enfoncée. Les clés améliorées pour les claviers IBM® 101-Key et 102-Key sont les touches Inser, DEL, début, fin, PAGE précédente, PAGE suivante et flèche dans les clusters à gauche du pavé numérique et les touches Division (/) et entrée du pavé numérique.

## <a name="mouse-events"></a>Événements de souris

Les événements de souris sont générés lorsque l’utilisateur déplace la souris ou appuie sur ou relâche l’un des boutons de la souris. Les événements de souris ne sont placés dans la mémoire tampon d’entrée que si les conditions suivantes sont remplies :

- Le mode d’entrée de la console est défini pour **activer l' \_ \_ entrée de la souris** (mode par défaut).
- La fenêtre de console a le focus clavier.
- Le pointeur de la souris se trouve dans les limites de la fenêtre de la console.

Si l’événement d’entrée est un événement de souris, le membre d' **événement** dans l' [**\_ enregistrement d’entrée**](input-record-str.md) est une structure d' [**enregistrement d' \_ événement \_ de souris**](mouse-event-record-str.md) contenant les informations suivantes :

- Coordonnées du pointeur de la souris en termes de la ligne et de la colonne de cellule de caractère dans le système de coordonnées de la mémoire tampon de l’écran de la console.
- Variable d’indicateur qui indique l’état des boutons de la souris.
- Variable d’indicateur qui indique l’état des touches de contrôle (ALT, CTRL, Maj, Verr. NUM, verrou de défilement et Verr. Maj) et indique si une touche améliorée a été enfoncée. Les clés améliorées pour les claviers IBM 101-Key et 102-Key sont les touches Inser, DEL, début, fin, PAGE précédente, PAGE suivante et flèche dans les clusters à gauche du pavé numérique et les touches de division (/) et de saisie dans le pavé numérique.
- Variable d’indicateur qui indique si l’événement est un événement de bouton ou de libération de bouton normal, un événement de déplacement de la souris ou un deuxième clic sur un événement de double-clic.

> [!NOTE]
>Les coordonnées de position de la souris sont en termes de mémoire tampon d’écran de la console, et non de la fenêtre de console. La mémoire tampon d’écran a peut-être été défilée par rapport à la fenêtre. par conséquent, le coin supérieur gauche de la fenêtre n’est pas nécessairement la coordonnée (0,0) de la mémoire tampon d’écran de la console. Pour déterminer les coordonnées de la souris par rapport au système de coordonnées de la fenêtre, soustraire les coordonnées d’origine de la fenêtre des coordonnées de position de la souris. Utilisez la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) pour déterminer les coordonnées d’origine de la fenêtre.

Le membre **dwButtonState** de la structure de l’enregistrement de l' [**\_ événement \_ de souris**](mouse-event-record-str.md) a un bit correspondant à chaque bouton de la souris. Le bit est 1 si le bouton est enfoncé et 0 si le bouton est actif. Un événement de libération de bouton est détecté par une valeur 0 pour le membre **dwEventFlags** de l' **enregistrement d' \_ événement \_ de souris** et une modification du bit d’un bouton de 1 à 0. La fonction [**GetNumberOfConsoleMouseButtons**](getnumberofconsolemousebuttons.md) récupère le nombre de boutons sur la souris.

## <a name="buffer-resizing-events"></a>Événements de Buffer-Resizing

Le menu d’une fenêtre de console permet à l’utilisateur de modifier la taille de la mémoire tampon d’écran active ; Cette modification génère un événement de redimensionnement de mémoire tampon. Les événements de redimensionnement de mémoire tampon sont placés dans la mémoire tampon d’entrée si le mode d’entrée de la console est défini pour **activer l' \_ \_ entrée** de la fenêtre (autrement dit, le mode par défaut est désactivé).

Si l’événement d’entrée est un événement de redimensionnement de la mémoire tampon, le membre de l' **événement** de l' [**\_ enregistrement d’entrée**](input-record-str.md) est une structure d’enregistrement de taille de la [**\_ mémoire tampon \_ \_ de fenêtre**](window-buffer-size-record-str.md) contenant la nouvelle taille de la mémoire tampon de l’écran de la console, exprimée en colonnes et lignes de cellule de caractères.

Si l’utilisateur réduit la taille de la mémoire tampon d’écran de la console, toutes les données contenues dans la partie ignorée du tampon sont perdues.

Les modifications apportées à la taille de la mémoire tampon d’écran de la console suite à des appels d’application à la fonction [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) ne sont pas générées en tant qu’événements de redimensionnement de mémoire tampon.
