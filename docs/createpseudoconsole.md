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
ms.openlocfilehash: 7d707423d7fca7c55d06bff11d6cbc904512e62b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059233"
---
# <a name="createpseudoconsole-function"></a>CreatePseudoConsole fonction)


Crée un nouvel objet pseudoconsole pour le processus appelant.

<a name="syntax"></a>Syntaxe
------

```C
HRESULT WINAPI CreatePseudoConsole(
    _In_ COORD size,
    _In_ HANDLE hInput,
    _In_ HANDLE hOutput,
    _In_ DWORD dwFlags,
    _Out_ HPCON* phPC
);
```

<a name="parameters"></a>Paramètres
----------

*taille* \[ dans\]  
Dimensions de la fenêtre/mémoire tampon en nombre de caractères qui seront utilisés lors de la création initiale du pseudoconsole. Cela peut être ajusté ultérieurement avec [ResizePseudoConsole](resizepseudoconsole.md).

*hInput* \[ dans\]  
Handle ouvert d’un flux de données qui représente l’entrée d’utilisateur sur l’appareil. Cela est actuellement limité à des e/s [synchrones](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .

*hOutput* \[ dans\]  
Handle ouvert d’un flux de données qui représente la sortie de l’application à partir de l’appareil. Cela est actuellement limité à des e/s [synchrones](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .

*dwFlags* \[ dans\]  
Il peut s'agir de l'une des valeurs suivantes :
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Value</th>
<th>Signification</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>0</strong></td>
<td><p>Effectuez une création pseudoconsole standard.</p></td>
</tr>
<tr class="even">
<td><span id="PSEUDOCONSOLE_INHERIT_CURSOR"></span><span id="pseudoconsole_inherit_cursor"></span>
<strong>PSEUDOCONSOLE_INHERIT_CURSOR</strong> (DWORD) 1</td>
<td><p>La session pseudoconsole créée va essayer d’hériter de la position du curseur de la console parente.</p></td>
</tr>
</tbody>
</table>

*phPC* \[ à\]  
Pointeur vers un emplacement qui recevra un handle vers le nouvel appareil pseudoconsole.

<a name="return-value"></a>Valeur retournée
------------

Type : **HRESULT**

Si cette méthode est réussie, elle retourne **S_OK**. Sinon, elle retourne un code d’erreur **HRESULT** .

<a name="remarks"></a>Remarques
-------

Cette fonction est principalement utilisée par les applications qui tentent d’être une fenêtre de terminal pour une application d’interface utilisateur de ligne de commande (CUI). Les appelants sont responsables de la présentation des informations sur le flux de sortie et de la collecte des entrées d’utilisateur et de leur sérialisation dans le flux d’entrée.

Les flux d’entrée et de sortie encodés au format UTF-8 contiennent du texte brut entrelacé avec des [séquences de terminaux virtuels](console-virtual-terminal-sequences.md). 

Dans le flux de sortie, les [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) peuvent être décodées par l’application appelante pour mettre en forme et présenter le texte brut dans une fenêtre d’affichage. 

Dans le flux d’entrée, le texte brut représente les touches de clavier standard entrées par un utilisateur. Des opérations plus compliquées sont représentées par l’encodage des clés de contrôle et des mouvements de la souris en tant que [séquences de terminaux virtuels](console-virtual-terminal-sequences.md) incorporées dans ce flux.

Le descripteur créé par cette fonction doit être fermé avec [ClosePseudoConsole](closepseudoconsole.md) lorsque les opérations sont terminées.

Si `PSEUDOCONSOLE_INHERIT_CURSOR` vous utilisez, l’application appelante doit être préparée à répondre à la demande d’état de curseur de manière asynchrone sur un thread d’arrière-plan en transférant ou en interprétant la demande d’informations de curseur qui seront reçues `hOutput` et répondant à `hInput` . Si vous ne le faites pas, l’application appelante risque de se bloquer lors de l’exécution d’une autre demande du système pseudoconsole.

<a name="examples"></a>Exemples
--------

Pour une procédure pas à pas complète sur l’utilisation de cette fonction pour établir une session psuedoconsole, consultez [création d’une session Pseudoconsole](creating-a-pseudoconsole-session.md).

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
<td><p>Windows 10 1809 [applications de bureau uniquement]</p></td>
</tr>
<tr class="even">
<td><p>Serveur minimal pris en charge</p></td>
<td><p>Windows Server 2019 [applications de bureau uniquement]</p></td>
</tr>
<tr class="odd">
<td><p>En-tête</p></td>
<td>ConsoleApi. h (via wincon. h, incluez Windows. h)</td>
</tr>
<tr class="even">
<td><p>Bibliothèque</p></td>
<td>Kernel32. lib</td>
</tr>
<tr class="odd">
<td><p>DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Voir aussi


[Pseudoconsoles](pseudoconsoles.md)

[Création d’une session Pseudoconsole](creating-a-pseudoconsole-session.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)

[**ClosePseudoConsole**](closepseudoconsole.md)
