---
title: GetStdHandle fonction)
description: Récupère un handle vers l’appareil standard spécifié (entrée standard, sortie standard ou erreur standard).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- processenv/GetStdHandle
- winbase/GetStdHandle
- GetStdHandle
MS-HAID:
- '\_win32\_getstdhandle'
- base.getstdhandle
- consoles.getstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 23cd76e9-671a-48d0-9b82-2beda8917348
topic_type:
- apiref
api_name:
- GetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 42857417cedb661014de869536b798d29c9eb884
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420208"
---
# <a name="getstdhandle-function"></a>GetStdHandle fonction)

Récupère un handle vers l’appareil standard spécifié (entrée standard, sortie standard ou erreur standard).

## <a name="syntax"></a>Syntaxe

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a>Paramètres

*nStdHandle* \[ dans\]  
Appareil standard. Ce paramètre peut prendre l’une des valeurs suivantes.

| Valeur | Signification |
|-|-|
| **STD_INPUT_HANDLE** (DWORD)-10 | Périphérique d’entrée standard. Initialement, il s’agit de la mémoire tampon d’entrée de la console, `CONIN$` . |
| **STD_OUTPUT_HANDLE** (DWORD)-11 | Périphérique de sortie standard. Initialement, il s’agit de la mémoire tampon d’écran active de la console, `CONOUT$` . |
| **STD_ERROR_HANDLE** (DWORD)-12 | Périphérique d’erreur standard. Initialement, il s’agit de la mémoire tampon d’écran active de la console, `CONOUT$` . |

## <a name="return-value"></a>Valeur retournée

Si la fonction s’exécute correctement, la valeur de retour est un handle vers l’appareil spécifié, ou un handle Redirigé défini par un appel précédent à [**SetStdHandle**](setstdhandle.md). Le descripteur dispose de droits d’accès en **\_ écriture** génériques **\_ en lecture** et génériques, sauf si l’application a utilisé **SetStdHandle** pour définir un descripteur standard avec un accès plus faible.

Si la fonction échoue, la valeur de retour est une **\_ \_ valeur de handle non valide**. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Si une application n’a pas de descripteurs standard associés, comme un service s’exécutant sur un bureau interactif, et n’a pas été redirigée, la valeur de retour est **null**.

## <a name="remarks"></a>Remarques

Les handles retournés par **GetStdHandle** peuvent être utilisés par les applications qui doivent lire ou écrire dans la console. Quand une console est créée, le descripteur d’entrée standard est un handle de la mémoire tampon d’entrée de la console, et la sortie standard et les descripteurs d’erreur standard sont des handles de la mémoire tampon d’écran active de la console. Ces handles peuvent être utilisés par les fonctions [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) et [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) , ou par n’importe quelle fonction de console qui accède à la mémoire tampon d’entrée de la console ou à une mémoire tampon d’écran (par exemple, les fonctions [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md)ou [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) ).

Les handles standard d’un processus peuvent être redirigés par un appel à [**SetStdHandle**](setstdhandle.md), auquel cas **GetStdHandle** retourne le handle Redirigé. Si les handles standard ont été redirigés, vous pouvez spécifier la `CONIN$` valeur dans un appel à la fonction [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) pour obtenir un handle vers la mémoire tampon d’entrée d’une console. De même, vous pouvez spécifier la `CONOUT$` valeur pour obtenir un descripteur de la mémoire tampon d’écran active d’une console.

Les handles standard d’un processus sur l’entrée de la méthode main sont dictés par la configuration de l’indicateur [**/Subsystem**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem) passé à l’éditeur de liens lors de la génération de l’application. La spécification de **/SUBSYSTEM : console** demande que le système d’exploitation remplisse les descripteurs à l’aide d’une session de console au démarrage, si le parent n’a pas déjà rempli la table de handles standard par héritage. En revanche, **/SUBSYSTEM : Windows** implique que l’application n’a pas besoin d’une console et n’utilisera probablement pas les handles standard. Vous trouverez plus d’informations sur l’héritage des handles dans la documentation de [**STARTF \_ USESTDHANDLES**](https://docs.microsoft.com/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).

Certaines applications fonctionnent en dehors des limites du sous-système déclaré. par exemple, une application **/SUBSYSTEM : Windows** peut vérifier/utiliser des handles standard à des fins de journalisation ou de débogage, mais fonctionne normalement avec une interface utilisateur graphique. Ces applications devront soigneusement sonder l’état des handles standard au démarrage et utiliser [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md)et [**FreeConsole**](freeconsole.md) pour ajouter/supprimer une console si vous le souhaitez.

Certaines applications peuvent également modifier leur comportement sur le type de handle hérité. Disambiguating le type entre console, canal, fichier et d’autres peut être effectué avec [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype).

### <a name="attachdetach-behavior"></a>Comportement d’attachement/détachement

Lors de l’attachement à une nouvelle console, les handles standard sont toujours remplacés par des handles de console, sauf si **STARTF \_ USESTDHANDLES** a été spécifié lors de la création du processus.

Si la valeur existante du handle standard est **null**, ou si la valeur existante du handle standard ressemble à un pseudohandle de console, le handle est remplacé par un handle de console.

Lorsqu’un parent utilise à la fois **Create \_ New \_ console** et **STARTF \_ USESTDHANDLES** pour créer un processus de console, les handles standard ne sont pas remplacés, sauf si la valeur existante du handle standard est **null** ou un pseudohandle de console.

> [!NOTE]
>Les processus de console *doivent* démarrer avec les handles standard remplis ou ils seront remplis automatiquement avec les descripteurs appropriés sur une nouvelle console. Les applications de l’interface utilisateur graphique peuvent être démarrées sans les handles standard et ne pas être automatiquement remplies.

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | ProcessEnv. h (via Winbase. h, incluez Windows. h) |
| Bibliothèque | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de la console](console-functions.md)

[Handles de console](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetStdHandle**](setstdhandle.md)

[**WriteConsole**](writeconsole.md)

[**Appel**](https://msdn.microsoft.com/library/windows/desktop/aa365747)
