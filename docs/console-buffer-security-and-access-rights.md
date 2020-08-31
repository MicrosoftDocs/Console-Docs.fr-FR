---
title: Sécurité de la mémoire tampon de la console et droits d’accès
description: Le modèle de sécurité Windows vous permet de contrôler l’accès aux mémoires tampons d’entrée de la console et aux mémoires tampons d’écran de la console. Pour plus d’informations sur la sécurité, consultez modèle de contrôle d’accès.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_console\_buffer\_security\_and\_access\_rights'
- base.console\_buffer\_security\_and\_access\_rights
- consoles.console\_buffer\_security\_and\_access\_rights
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f9a50063-8fc8-4cd1-8f24-9ae3946d3119
ms.openlocfilehash: 63cfdb91f4ab9696ade81c7a15bc62e1c93ab6e3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059349"
---
# <a name="console-buffer-security-and-access-rights"></a>Sécurité de la mémoire tampon de la console et droits d’accès


Le modèle de sécurité Windows vous permet de contrôler l’accès aux mémoires tampons d’entrée de la console et aux mémoires tampons d’écran de la console. Pour plus d’informations sur la sécurité, consultez [modèle de contrôle d’accès](https://msdn.microsoft.com/library/windows/desktop/aa374876).

Vous pouvez spécifier un [descripteur de sécurité](https://msdn.microsoft.com/library/windows/desktop/aa379563) pour l’entrée de la console et des mémoires tampons d’écran de console lorsque vous appelez la fonction [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) ou [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) . Si vous spécifiez **null**, l’objet obtient un descripteur de sécurité par défaut. Les listes de contrôle d’accès dans le descripteur de sécurité par défaut pour une mémoire tampon de la console proviennent du jeton principal ou d’emprunt d’identité du créateur.

Les handles retournés par [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)et [**GetStdHandle**](getstdhandle.md) ont les droits d’accès en ** \_ écriture** **génériques et \_ en lecture** .

Les droits d’accès valides incluent les [droits d’accès](https://msdn.microsoft.com/library/windows/desktop/aa446632)génériques ** \_ en lecture et en** ** \_ écriture** génériques.


| Value                            | Signification                                                                                               |
|----------------------------------|-------------------------------------------------------------------------------------------------------|
| **Générique \_ LECTURE** (0x80000000L)  | Demande l’accès en lecture à la mémoire tampon d’écran de la console, ce qui permet au processus de lire des données à partir de la mémoire tampon. |
| **Générique \_ ÉCRITURE** (0x40000000L) | Demande l’accès en écriture à la mémoire tampon de l’écran de la console, ce qui permet au processus d’écrire des données dans la mémoire tampon. |










