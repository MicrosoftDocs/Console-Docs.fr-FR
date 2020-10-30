---
title: ResizePseudoConsole fonction)
description: Consultez les informations de référence sur la fonction ResizePseudoConsole, qui redimensionne les mémoires tampons internes pour un pseudoconsole à la taille donnée.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API console, conpty, pseudoconsole
f1_keywords:
- consoleapi/ResizePseudoConsole
- ResizePseudoConsole
topic_type:
- apiref
api_name:
- ResizePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 0d5a4ff954c8ebea688573f23d3981ee9c5d7d2a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037537"
---
# <a name="resizepseudoconsole-function"></a>ResizePseudoConsole fonction)

Redimensionne les mémoires tampons internes pour un pseudoconsole à la taille donnée.

## <a name="syntax"></a>Syntaxe

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

## <a name="parameters"></a>Paramètres

*hPC* \[ dans\]  
Handle d’un pseudoconsole actif tel qu’il est ouvert par [CreatePseudoConsole](createpseudoconsole.md).

*taille* \[ dans\]  
Dimensions de la fenêtre/mémoire tampon en nombre de caractères qui seront utilisés pour la mémoire tampon interne de ce pseudoconsole.

## <a name="return-value"></a>Valeur retournée

Type : **HRESULT**

Si cette méthode est réussie, elle retourne **S_OK** . Sinon, elle retourne un code d’erreur **HRESULT** .

## <a name="remarks"></a>Remarques

Cette fonction peut redimensionner les mémoires tampons internes de la session pseudoconsole pour qu’elles correspondent à la taille de la fenêtre/de la mémoire tampon utilisée pour l’affichage sur l’extrémité terminal. Cela garantit que les applications CUI (attached Command-Line interface) utilisant les fonctions de la [console](console-functions.md) pour communiquer auront les dimensions correctes retournées dans leurs appels.

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

[**ClosePseudoConsole**](closepseudoconsole.md)
