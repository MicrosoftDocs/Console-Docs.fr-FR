---
title: CreatePseudoConsole fonction)
description: Consultez les informations de référence sur la fonction CreatePseudoConsole, qui alloue un nouveau pseudoconsole pour le processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API console, conpty, pseudoconsole
f1_keywords:
- consoleapi/CreatePseudoConsole
- CreatePseudoConsole
topic_type:
- apiref
api_name:
- CreatePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 91958b23348895f7454c9228e3c730d231dc4f0b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357939"
---
# <a name="createpseudoconsole-function"></a>CreatePseudoConsole fonction)

Crée un nouvel objet pseudoconsole pour le processus appelant.

## <a name="syntax"></a>Syntaxe

```C
HRESULT WINAPI CreatePseudoConsole(
    _In_ COORD size,
    _In_ HANDLE hInput,
    _In_ HANDLE hOutput,
    _In_ DWORD dwFlags,
    _Out_ HPCON* phPC
);
```

## <a name="parameters"></a>Paramètres

*taille* \[ dans\]  
Dimensions de la fenêtre/mémoire tampon en nombre de caractères qui seront utilisés lors de la création initiale du pseudoconsole. Cela peut être ajusté ultérieurement avec [ResizePseudoConsole](resizepseudoconsole.md).

*hInput* \[ dans\]  
Handle ouvert d’un flux de données qui représente l’entrée d’utilisateur sur l’appareil. Cela est actuellement limité à des e/s [synchrones](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .

*hOutput* \[ dans\]  
Handle ouvert d’un flux de données qui représente la sortie de l’application à partir de l’appareil. Cela est actuellement limité à des e/s [synchrones](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .

*dwFlags* \[ dans\]  
Il peut s'agir de l'une des valeurs suivantes :

| Valeur | Signification |
|-|-|
| **0** | Effectuez une création pseudoconsole standard. |
| **PSEUDOCONSOLE_INHERIT_CURSOR** (DWORD) 1 | La session pseudoconsole créée va essayer d’hériter de la position du curseur de la console parente. |

*phPC* \[ à\]  
Pointeur vers un emplacement qui recevra un handle vers le nouvel appareil pseudoconsole.

## <a name="return-value"></a>Valeur de retour

Type : **HRESULT**

Si cette méthode est réussie, elle retourne **S_OK**. Sinon, elle retourne un code d’erreur **HRESULT** .

## <a name="remarks"></a>Notes

Cette fonction est principalement utilisée par les applications qui tentent d’être une fenêtre de terminal pour une application d’interface utilisateur de ligne de commande (CUI). Les appelants sont responsables de la présentation des informations sur le flux de sortie et de la collecte des entrées d’utilisateur et de leur sérialisation dans le flux d’entrée.

Les flux d’entrée et de sortie encodés au format UTF-8 contiennent du texte brut entrelacé avec des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md).

Dans le flux de sortie, les [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) peuvent être décodées par l’application appelante pour mettre en forme et présenter le texte brut dans une fenêtre d’affichage.

Dans le flux d’entrée, le texte brut représente les touches de clavier standard entrées par un utilisateur. Des opérations plus compliquées sont représentées par l’encodage des clés de contrôle et des mouvements de la souris en tant que [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) incorporées dans ce flux.

Le descripteur créé par cette fonction doit être fermé avec [ClosePseudoConsole](closepseudoconsole.md) lorsque les opérations sont terminées.

Si `PSEUDOCONSOLE_INHERIT_CURSOR` vous utilisez, l’application appelante doit être préparée à répondre à la demande d’état de curseur de manière asynchrone sur un thread d’arrière-plan en transférant ou en interprétant la demande d’informations de curseur qui seront reçues `hOutput` et répondant à `hInput` . Si vous ne le faites pas, l’application appelante risque de se bloquer lors de l’exécution d’une autre demande du système pseudoconsole.

## <a name="examples"></a>Exemples

Pour une procédure pas à pas complète sur l’utilisation de cette fonction pour établir une session pseudoconsole, consultez [création d’une session pseudoconsole](creating-a-pseudoconsole-session.md).

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 10 octobre 2018 mise à jour (version 1809) \[ applications de bureau uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2019 \[ uniquement\] |
| En-tête | ConsoleApi.h (via WinCon.h, inclure Windows.h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Pseudoconsoles](pseudoconsoles.md)

[Création d’une session pseudo-console](creating-a-pseudoconsole-session.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)

[**ClosePseudoConsole**](closepseudoconsole.md)