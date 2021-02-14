---
title: Fonction GetStdHandle
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
ms.openlocfilehash: 0804e12ff7510cd41bec66e1a45f8a31add7c17a
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358749"
---
# <a name="getstdhandle-function"></a>Fonction GetStdHandle

Récupère un handle vers l’appareil standard spécifié (entrée standard, sortie standard ou erreur standard).

## <a name="syntax"></a>Syntaxe

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a>Paramètres

*nStdHandle* \[entrée\]  
Périphérique standard. Ce paramètre peut prendre les valeurs suivantes.

| Valeur | Signification |
|-|-|
| **STD_INPUT_HANDLE** (DWORD) -10 | Périphérique d’entrée standard. À la base, il s’agit de la mémoire tampon d’entrée de la console, `CONIN$`. |
| **STD_OUTPUT_HANDLE** (DWORD) -11 | Périphérique de sortie standard. À la base, il s’agit de la mémoire tampon d’écran de la console active, `CONOUT$`. |
| **STD_ERROR_HANDLE** (DWORD) -12 | Périphérique d’erreur standard. À la base, il s’agit de la mémoire tampon d’écran de la console active, `CONOUT$`. |

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, la valeur de retour est un handle vers le périphérique spécifié, ou un handle redirigé défini par un appel précédent à [**SetStdHandle**](setstdhandle.md). Le handle a les droits d’accès **GENERIC\_READ** et **GENERIC\_WRITE**, sauf si l’application a utilisé **SetStdHandle** pour définir un handle standard avec un accès plus restreint.

Si la fonction échoue, la valeur de retour est **INVALID\_HANDLE\_VALUE**. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

Si une application n’a pas de handles standard associés, comme un service s’exécutant sur un bureau interactif, et qu’elle ne les a pas redirigés, la valeur de retour est **NULL**.

## <a name="remarks"></a>Remarques

Les handles retournés par **GetStdHandle** peuvent être utilisés par les applications qui doivent lire ou écrire dans la console. Quand une console est créée, le handle d’entrée standard est un handle vers la mémoire tampon d’entrée de la console, et les handles de sortie standard et d’erreur standard sont des handles vers la mémoire tampon d’écran active de la console. Ces handles peuvent être utilisés par les fonctions [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) et [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile), ou par une des fonctions de console qui accèdent à la mémoire tampon d’entrée de la console ou à une mémoire tampon d’écran (par exemple, les fonctions [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md) ou [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)).

Les handles standard d’un processus peuvent être redirigés par un appel à [**SetStdHandle**](setstdhandle.md), auquel cas **GetStdHandle** retourne le handle redirigé. Si les handles standard ont été redirigés, vous pouvez spécifier la valeur `CONIN$` dans un appel à la fonction [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) pour obtenir un handle vers la mémoire tampon d’entrée d’une console. De même, vous pouvez spécifier la valeur `CONOUT$` pour obtenir un handle vers la mémoire tampon d’écran active d’une console.

Les handles standard d’un processus sur l’entrée de la méthode main sont dictés par la configuration de l’indicateur [ **/SUBSYSTEM**](/cpp/build/reference/subsystem-specify-subsystem) passé à l’éditeur de liens lors de la génération de l’application. La spécification de **/SUBSYSTEM : CONSOLE** demande que le système d’exploitation remplisse les handles avec une session de console au démarrage si le parent n’a pas déjà rempli la table de handles standard par héritage. En revanche, **/SUBSYSTEM:WINDOWS** implique que l’application n’a pas besoin d’une console et qu’elle ne va probablement pas utiliser les handles standard. Vous trouverez plus d’informations sur l’héritage des handles dans la documentation pour [**STARTF\_USESTDHANDLES**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).

Certaines applications fonctionnent en dehors des limites de leur sous-système déclaré. Par exemple, une application **/SUBSYSTEM:WINDOWS** peut vérifier/utiliser des handles standard à des fins de journalisation ou de débogage, mais elle fonctionne normalement avec une interface graphique utilisateur. Ces applications doivent soigneusement interroger l’état des handles standard au démarrage et utiliser [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md) et [**FreeConsole**](freeconsole.md) pour ajouter/supprimer une console si nécessaire.

Certaines applications peuvent également modifier leur comportement selon le type de handle hérité. La levée des ambiguïtés de type entre console, canal, fichier et d’autres éléments peut être effectué avec [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype).

### <a name="attachdetach-behavior"></a>Comportement d’attachement/détachement

Lors de l’attachement à une nouvelle console, les handles standard sont toujours remplacés par des handles de console, sauf si **STARTF\_USESTDHANDLES** a été spécifié lors de la création du processus.

Si la valeur existante du handle standard est **NULL** ou si la valeur existante du handle standard ressemble à un pseudohandle de console, le handle est remplacé par un handle de console.

Quand un parent utilise à la fois **CREATE\_NEW\_CONSOLE** et **STARTF\_USESTDHANDLES** pour créer un processus de console, les handles standard ne sont pas remplacés, sauf si la valeur existante du handle standard est **NULL** ou un pseudohandle de console.

> [!NOTE]
>Les processus de console *doivent* démarrer avec les handles standard remplis ; sinon, ils seront renseignés automatiquement avec les handles appropriés pour une nouvelle console. Les applications avec interface graphique utilisateur peuvent être démarrées sans les handles standard ; ils ne seront pas renseignés automatiquement.

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [Lecture des événements de mémoire tampon d’entrée](reading-input-buffer-events.md).

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 2000 Professionnel - \[Applications de bureau uniquement\] |
| Serveur minimal pris en charge | Windows 2000 Server - \[Applications de bureau uniquement\] |
| En-tête | ProcessEnv.h (via Winbase.h, inclure Windows.h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Voir aussi

[Fonctions de console](console-functions.md)

[Handles de console](console-handles.md)

[**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**SetStdHandle**](setstdhandle.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)