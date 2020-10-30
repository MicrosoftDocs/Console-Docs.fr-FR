---
title: GetConsoleProcessList fonction)
description: Consultez les informations de référence sur la fonction GetConsoleProcessList, qui récupère une liste des processus attachés à la console actuelle.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi3/GetConsoleProcessList
- wincon/GetConsoleProcessList
- GetConsoleProcessList
MS-HAID:
- '\_win32\_getconsoleprocesslist'
- base.getconsoleprocesslist
- consoles.getconsoleprocesslist
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3d21103b-662d-4393-ae3f-773cd9e4a930
topic_type:
- apiref
api_name:
- GetConsoleProcessList
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: bfc16edccb2f1be2b22c81992800d8f62d86cf4f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037980"
---
# <a name="getconsoleprocesslist-function"></a>GetConsoleProcessList fonction)

Récupère une liste des processus attachés à la console actuelle.

## <a name="syntax"></a>Syntaxe

```C
DWORD WINAPI GetConsoleProcessList(
  _Out_ LPDWORD lpdwProcessList,
  _In_  DWORD   dwProcessCount
);
```

## <a name="parameters"></a>Paramètres

*lpdwProcessList* \[ à\]  
Pointeur vers une mémoire tampon qui reçoit un tableau d’identificateurs de processus en cas de réussite. Il doit s’agir d’une mémoire tampon valide qui ne peut pas être `NULL` . La mémoire tampon doit avoir un espace pour recevoir au moins 1 ID de processus retourné.

*dwProcessCount* \[ dans\]  
Nombre maximal d’identificateurs de processus qui peuvent être stockés dans la mémoire tampon *lpdwProcessList* . La valeur doit être supérieure à 0.

## <a name="return-value"></a>Valeur retournée

Si la fonction est réussie, la valeur de retour est inférieure ou égale à *dwProcessCount* et représente le nombre d’identificateurs de processus stockés dans la mémoire tampon *lpdwProcessList* .

Si la mémoire tampon est trop petite pour contenir tous les identificateurs de processus valides, la valeur de retour est le nombre requis d’éléments de tableau. La fonction n’a stocké aucun identificateur dans la mémoire tampon. Dans ce cas, utilisez la valeur de retour pour allouer une mémoire tampon suffisamment grande pour stocker la liste entière et appeler à nouveau la fonction.

Si la valeur de retour est égale à zéro, la fonction a échoué, car chaque console a au moins un processus associé. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Si une `NULL` liste de processus a été fournie ou si le nombre de processus est égal à 0, l’appel retourne 0 et `GetLastError` retourne `ERROR_INVALID_PARAMETER` . Indiquez une mémoire tampon d’au moins un élément pour appeler cette fonction. Allouez une mémoire tampon plus grande et rappelez si le code de retour est plus grand que la longueur de la mémoire tampon fournie.

## <a name="remarks"></a>Remarques

Pour compiler une application qui utilise cette fonction, définissez **\_ Win32 \_ winnt** comme 0x0501 ou version ultérieure. Pour plus d’informations, consultez [utilisation des en-têtes Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de \[ Bureau Windows XP uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows Server 2003 \[ uniquement\] |
| En-tête | ConsoleApi3. h (via WinCon. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[**AttachConsole**](attachconsole.md)

[Fonctions de la console](console-functions.md)
