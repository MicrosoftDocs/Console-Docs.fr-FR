---
title: Sécurité de la mémoire tampon et droits d’accès d’une console
description: Le modèle de sécurité Windows vous permet de contrôler l’accès aux mémoires tampons d’entrée de la console et aux mémoires tampons d’écran de la console. Pour plus d’informations sur la sécurité, consultez Access-Control modèle.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_console\_buffer\_security\_and\_access\_rights'
- base.console\_buffer\_security\_and\_access\_rights
- consoles.console\_buffer\_security\_and\_access\_rights
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f9a50063-8fc8-4cd1-8f24-9ae3946d3119
ms.openlocfilehash: dfafdbd59c2b06929c35612d7dcf03b24439eba2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93036977"
---
# <a name="console-buffer-security-and-access-rights"></a>Sécurité de la mémoire tampon et droits d’accès d’une console

Le modèle de sécurité Windows vous permet de contrôler l’accès aux mémoires tampons d’entrée de la console et aux mémoires tampons d’écran de la console. Pour plus d’informations sur la sécurité, consultez [modèle de contrôle d’accès](https://msdn.microsoft.com/library/windows/desktop/aa374876).

## <a name="console-object-security-descriptors"></a>Descripteurs de sécurité de l’objet console

Vous pouvez spécifier un [descripteur de sécurité](https://msdn.microsoft.com/library/windows/desktop/aa379563) pour l’entrée de la console et des mémoires tampons d’écran de console lorsque vous appelez la fonction [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) ou [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) . Si vous spécifiez **null** , l’objet obtient un descripteur de sécurité par défaut. Les listes de contrôle d’accès dans le descripteur de sécurité par défaut pour une mémoire tampon de la console proviennent du jeton principal ou d’emprunt d’identité du créateur.

Les handles retournés par [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)et [**GetStdHandle**](getstdhandle.md) ont les droits d’accès en **\_ écriture** **génériques et \_ en lecture** .

Les droits d’accès valides incluent les [droits d’accès](https://msdn.microsoft.com/library/windows/desktop/aa446632)génériques **\_ en lecture et en** **\_ écriture** génériques.

| Valeur | Signification |
|-|-|
| **Générique \_ LECTURE** (0x80000000L)  | Demande l’accès en lecture à la mémoire tampon d’écran de la console, ce qui permet au processus de lire des données à partir de la mémoire tampon. |
| **Générique \_ ÉCRITURE** (0x40000000L) | Demande l’accès en écriture à la mémoire tampon de l’écran de la console, ce qui permet au processus d’écrire des données dans la mémoire tampon. |

> [!NOTE]
> **[Plateforme Windows universelle applications console](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp)** et celles avec un **[niveau d’intégrité](https://docs.microsoft.com/windows/win32/secauthz/mandatory-integrity-control)** inférieur à celui de la console attachée ne sont pas autorisées à lire la mémoire tampon de sortie et à écrire dans la mémoire tampon d’entrée, même si les descripteurs de sécurité ci-dessus l’autorisent normalement. Pour plus d’informations, consultez la discussion sur les **[verbes de façon incorrecte](#wrong-way-verbs)** ci-dessous.

## <a name="wrong-way-verbs"></a>Verbes de Wrong-Way

Certaines opérations sur les objets de la console sont refusées même si l’objet a un descripteur de sécurité qui est indiqué pour autoriser spécifiquement la lecture ou l’écriture. Cela concerne spécifiquement les applications de ligne de commande qui s’exécutent dans un contexte à privilèges réduits qui partagent une session de console créée par une application en ligne de commande dans un contexte plus permissif.

Le terme « verbes incorrects » est destiné à s’appliquer à l’opération qui est l’inverse du passage normal de l’un des objets de la console. Plus précisément, le sens normal pour la mémoire tampon de sortie est l’écriture et le workflow normal pour la mémoire tampon d’entrée est en lecture. Le « mauvais sens » est donc la lecture de la mémoire tampon de sortie ou l’écriture de la mémoire tampon d’entrée. Il s’agit des fonctions décrites dans la documentation sur les **[fonctions d’e/s de la console de bas niveau](low-level-console-i-o.md)** .

Voici les deux scénarios où il est possible de trouver :

1. **[Applications console plateforme Windows universelle](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp)** . Étant donné qu’il s’agit de cousins d’autres plateforme Windows universelle applications, ils sont assurés qu’ils sont isolés des autres applications et fournissent aux utilisateurs des garanties quant aux effets de leur fonctionnement.
1. Toute application console lancée intentionnellement avec un **[niveau d’intégrité](https://docs.microsoft.com/windows/win32/secauthz/mandatory-integrity-control)** inférieur à la session existante, qui peut être obtenue avec l' **[étiquetage ou la manipulation de jetons pendant CreateProcess](https://docs.microsoft.com/previous-versions/dotnet/articles/bb625960(v=msdn.10))** .

Si l’un de ces scénarios est détecté, la console applique l’indicateur « verbes incorrects » à la connexion d’application de ligne de commande et rejette les appels aux API suivantes pour réduire la surface de communication entre les niveaux :

:::row:::
    :::column:::
        [ReadConsoleOutput](readconsoleoutput.md)  
        [ReadConsoleOutputCharacter](readconsoleoutputcharacter.md)  
        [ReadConsoleOutputAttribute](readconsoleoutputattribute.md)  
    :::column-end:::
    :::column:::
        [WriteConsoleInput](writeconsoleinput.md)  
    :::column-end:::
:::row-end:::

Les appels rejetés recevront un code d’erreur d' **accès refusé** , le même que si l’autorisation de lecture ou d’écriture était refusée par les descripteurs de sécurité sur l’objet.
