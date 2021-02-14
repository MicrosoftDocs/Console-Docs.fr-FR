---
title: WinEvents de la console
description: Les constantes d’événement suivantes sont utilisées dans le paramètre Event de la fonction de rappel WinEventProc. Pour plus d’informations, consultez WinEvents.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
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
ms.openlocfilehash: 2cd48537ef79f09024a55b32a98e2aa85fe76f62
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358049"
---
# <a name="console-winevents"></a>WinEvents de la console

> [!IMPORTANT]
> Les WinEvents font partie de l’infrastructure de **[Active Accessibility Microsoft](/windows/win32/winauto/microsoft-active-accessibility)** héritée. Le développement à l’aide de ces événements est fortement déconseillé en faveur de l’infrastructure d' **[automatisation d’interface utilisateur de Microsoft](/windows/win32/winauto/entry-uiauto-win32)** , qui fournit une suite plus robuste et plus complète d’interfaces permettant aux applications d’accessibilité et d’automatisation d’interagir avec la console. 

> [!WARNING]
> L’inscription à ces événements est une activité globale qui aura un impact considérable sur les performances de toutes les applications de ligne de commande exécutées sur un système en même temps, y compris les services et les utilitaires d’arrière-plan. L’infrastructure d’automatisation de l' **interface utilisateur de Microsoft** est spécifique à la session de console et survient à cette limitation.

Les constantes d’événement suivantes sont utilisées dans le paramètre *Event* de la fonction de rappel [*WinEventProc*](/windows/win32/api/winuser/nc-winuser-wineventproc) . Pour plus d’informations, consultez [winEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).

| Constante/valeur | Description |
|-|-|
| **EVENT_CONSOLE_CARET** 0x4001 | Le signe insertion de la console a été déplacé. Le paramètre *idObject* est une ou plusieurs des valeurs suivantes : **CONSOLE_CARET_SELECTION** ou **CONSOLE_CARET_VISIBLE**. Le paramètre *idChild* est une structure de **[repère](coord-str.md)** qui spécifie la position actuelle du curseur. |
| **EVENT_CONSOLE_END_APPLICATION** 0x4007 | Un processus de console s’est terminé. Le paramètre *idObject* contient l’identificateur de processus du processus terminé. |
| **EVENT_CONSOLE_LAYOUT** 0x4005 | La disposition de la console a changé. |
| **EVENT_CONSOLE_START_APPLICATION** 0x4006 | Un nouveau processus de console a démarré. Le paramètre *idObject* contient l’identificateur de processus du processus nouvellement créé. Si l’application est une application 16 bits, le paramètre *idChild* est **CONSOLE_APPLICATION_16BIT** et *idObject* est l’identificateur de processus de la session NTVDM associée à la console. |
|**EVENT_CONSOLE_UPDATE_REGION** 0x4002 | Plus d’un caractère a été modifié. Le paramètre  *idObject* est une structure de **[repère](coord-str.md)** qui spécifie le début de la région modifiée. Le paramètre *idChild* est une structure de **repère** qui spécifie la fin de la région modifiée. |
|**EVENT_CONSOLE_UPDATE_SCROLL** 0x4004 | La console a défilé. Le paramètre *idObject* est la distance horizontale à laquelle la console a défilé. Le paramètre *idChild* est la distance verticale à laquelle la console a défilé. |
|**EVENT_CONSOLE_UPDATE_SIMPLE** 0x4003 | Un caractère unique a changé. Le paramètre *idObject* est une structure de **[repère](coord-str.md)** qui spécifie le caractère qui a changé. Le paramètre *idChild* spécifie le caractère dans le mot de poids faible et les **[attributs de caractère](console-screen-buffers.md#character-attributes)** dans le mot de poids fort. |

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 2000 Professionnel - \[Applications de bureau uniquement\] |
| Serveur minimal pris en charge | Windows 2000 Server - \[Applications de bureau uniquement\] |
| En-tête | Winuser. h |