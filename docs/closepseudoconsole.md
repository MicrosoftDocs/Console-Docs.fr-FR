---
title: ClosePseudoConsole fonction)
description: Consultez les informations de référence sur la fonction ClosePseudoConsole, qui ferme un pseudoconsole à partir du handle donné.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API console, conpty, pseudoconsole
topic_type:
- apiref
api_name:
- ClosePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 067fa732f5badfe46ee6391c892aa037613cb4dd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037287"
---
# <a name="closepseudoconsole-function"></a>ClosePseudoConsole fonction)

Ferme un pseudoconsole à partir du handle donné.

## <a name="syntax"></a>Syntaxe

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC
);
```

## <a name="parameters"></a>Paramètres

*hPC* \[ dans\]  
Handle d’un pseudoconsole actif tel qu’il est ouvert par [CreatePseudoConsole](createpseudoconsole.md).

## <a name="return-value"></a>Valeur retournée

*Aucune*

## <a name="remarks"></a>Remarques

Lors de la fermeture d’un pseudoconsole, les applications clientes attachées à la session sont également arrêtées.

Un frame peint final peut arriver sur le `hOutput` handle initialement fourni à [CreatePsuedoConsole](createpseudoconsole.md) lorsque cette API est appelée. Il est prévu que l’appelant draine ces informations à partir de la mémoire tampon du canal de communication, puis le présente ou l’ignore. L’échec de la vidange de la mémoire tampon peut provoquer l’attente indéfinie de l’appel de fermeture jusqu’à ce qu’il soit vidé ou que les canaux de communication soient rompus d’une autre façon.

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 10 octobre 2018 mise à jour (version 1809) \[ applications de bureau uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2019 \[ uniquement\] |
| En-tête | ConsoleApi. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Pseudoconsoles](pseudoconsoles.md)

[**CreatePseudoConsole**](createpseudoconsole.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)
