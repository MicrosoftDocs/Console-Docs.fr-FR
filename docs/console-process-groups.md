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
ms.openlocfilehash: 26a1b0b9001f64ea2dc7465fa298b1383f30aa61
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038447"
---
# <a name="console-process-groups"></a>Groupes de processus de la console

Lorsqu’un processus utilise la fonction [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) pour créer un nouveau processus de console, il peut spécifier l’indicateur de création d’un **\_ nouveau \_ \_ groupe de processus** pour faire du nouveau processus le processus racine d’un groupe de processus de la console. Le groupe de processus comprend tous les processus qui sont des descendants du processus racine.

Un processus peut utiliser la fonction [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) pour envoyer un signal Ctrl + C ou Ctrl + Pause à tous les processus d’un groupe de processus de la console. Le signal est reçu uniquement par les processus du groupe qui sont attachés à la même console que le processus qui a appelé **GenerateConsoleCtrlEvent** .
