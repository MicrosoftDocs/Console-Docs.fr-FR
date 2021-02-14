---
title: Groupes de processus de la console
description: Lorsqu’un processus utilise la fonction CreateProcess pour créer un nouveau processus de console, il peut spécifier l' \_ indicateur de création d’un nouveau \_ \_ groupe de processus pour faire du nouveau processus le processus racine d’un groupe de processus de la console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_console\_process\_groups'
- base.console\_process\_groups
- consoles.console\_process\_groups
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6cfe5b4b-d677-4747-bbf2-c7243db2346e
ms.openlocfilehash: 8df877eca9a52ef9072685c673461723dda78a0b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358099"
---
# <a name="console-process-groups"></a>Groupes de processus de la console

Lorsqu’un processus utilise la fonction [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) pour créer un nouveau processus de console, il peut spécifier l’indicateur de création d’un **\_ nouveau \_ \_ groupe de processus** pour faire du nouveau processus le processus racine d’un groupe de processus de la console. Le groupe de processus comprend tous les processus qui sont des descendants du processus racine.

Un processus peut utiliser la fonction [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) pour envoyer un signal Ctrl + C ou Ctrl + Pause à tous les processus d’un groupe de processus de la console. Le signal est reçu uniquement par les processus du groupe qui sont attachés à la même console que le processus qui a appelé **GenerateConsoleCtrlEvent**.