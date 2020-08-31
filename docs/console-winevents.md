---
title: WinEvents de la console
description: Les constantes d’événement suivantes sont utilisées dans le paramètre Event de la fonction de rappel WinEventProc. Pour plus d’informations, consultez WinEvents.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
f1_keywords:
- winuser/EVENT_CONSOLE_CARET
- winuser/EVENT_CONSOLE_END_APPLICATION
- winuser/EVENT_CONSOLE_LAYOUT
- winuser/EVENT_CONSOLE_START_APPLICATION
- winuser/EVENT_CONSOLE_UPDATE_REGION
- winuser/EVENT_CONSOLE_UPDATE_SCROLL
- winuser/EVENT_CONSOLE_UPDATE_SIMPLE
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
MS-HAID:
- '\_win32\_console\_winevents'
- base.console\_winevents
- consoles.console\_winevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b7078b2d-5508-4e42-bac2-34b70f1856e2
topic_type:
- apiref
api_name:
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
api_location:
- Winuser.h
api_type:
- HeaderDef
ms.openlocfilehash: ab58df01b3fb29e6efea3ecd0aab145fe2f298c2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059244"
---
# <a name="console-winevents"></a>WinEvents de la console


Les constantes d’événement suivantes sont utilisées dans le paramètre *Event* de la fonction de rappel [*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) . Pour plus d’informations, consultez [winEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Constante/valeur</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="EVENT_CONSOLE_CARET"></span><span id="event_console_caret"></span>
<strong>EVENT_CONSOLE_CARET</strong> 0x4001</td>
<td><p>Le signe insertion de la console a été déplacé. Le paramètre <em>idObject</em> est une ou plusieurs des valeurs suivantes : <strong>CONSOLE_CARET_SELECTION</strong> ou <strong>CONSOLE_CARET_VISIBLE</strong>.</p>
<p>Le paramètre <em>idChild</em> est une structure de <strong><a href="https://docs.microsoft.com/windows/console/coord-str">repère</a></strong> qui spécifie la position actuelle du curseur.</p></td>
</tr>
<tr class="even">
<td><span id="EVENT_CONSOLE_END_APPLICATION"></span><span id="event_console_end_application"></span>
<strong>EVENT_CONSOLE_END_APPLICATION</strong> 0x4007</td>
<td><p>Un processus de console s’est terminé. Le paramètre <em>idObject</em> contient l’identificateur de processus du processus terminé.</p></td>
</tr>
<tr class="odd">
<td><span id="EVENT_CONSOLE_LAYOUT"></span><span id="event_console_layout"></span>
<strong>EVENT_CONSOLE_LAYOUT</strong> 0x4005</td>
<td><p>La disposition de la console a changé.</p></td>
</tr>
<tr class="even">
<td><span id="EVENT_CONSOLE_START_APPLICATION"></span><span id="event_console_start_application"></span>
<strong>EVENT_CONSOLE_START_APPLICATION</strong> 0x4006</td>
<td><p>Un nouveau processus de console a démarré. Le paramètre <em>idObject</em> contient l’identificateur de processus du processus nouvellement créé. Si l’application est une application 16 bits, le paramètre <em>idChild</em> est <strong>CONSOLE_APPLICATION_16BIT</strong> et <em>idObject</em> est l’identificateur de processus de la session NTVDM associée à la console.</p></td>
</tr>
<tr class="odd">
<td><span id="EVENT_CONSOLE_UPDATE_REGION"></span><span id="event_console_update_region"></span>
<strong>EVENT_CONSOLE_UPDATE_REGION</strong> 0x4002</td>
<td><p>Plus d’un caractère a été modifié. Le paramètre <em>idObject</em> est une structure de <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>repère</strong></a> qui spécifie le début de la région modifiée. Le paramètre <em>idChild</em> est une structure de <strong>repère</strong> qui spécifie la fin de la région modifiée.</p></td>
</tr>
<tr class="even">
<td><span id="EVENT_CONSOLE_UPDATE_SCROLL"></span><span id="event_console_update_scroll"></span>
<strong>EVENT_CONSOLE_UPDATE_SCROLL</strong> 0x4004</td>
<td><p>La console a défilé. Le paramètre <em>idObject</em> est la distance horizontale à laquelle la console a défilé. Le paramètre <em>idChild</em> est la distance verticale à laquelle la console a défilé.</p></td>
</tr>
<tr class="odd">
<td><span id="EVENT_CONSOLE_UPDATE_SIMPLE"></span><span id="event_console_update_simple"></span>
<strong>EVENT_CONSOLE_UPDATE_SIMPLE</strong> 0x4003</td>
<td><p>Un caractère unique a changé. Le paramètre <em>idObject</em> est une structure de <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>repère</strong></a> qui spécifie le caractère qui a changé. Le paramètre <em>idChild</em> spécifie le caractère dans le mot de poids faible et les <a href="console-screen-buffers.md#_win32_font_attributes" data-raw-source="[character attributes](console-screen-buffers.md#_win32_font_attributes)">attributs de caractère</a> dans le mot de poids fort.</p></td>
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
<td>Winuser. h</td>
</tr>
</tbody>
</table>
