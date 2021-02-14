---
title: Fonction SetConsoleCtrlHandler
description: Ajoute ou supprime une fonction HandlerRoutine définie par l’application dans la liste des fonctions de gestionnaire pour le processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/SetConsoleCtrlHandler
- wincon/SetConsoleCtrlHandler
- SetConsoleCtrlHandler
MS-HAID:
- '\_win32\_setconsolectrlhandler'
- base.setconsolectrlhandler
- consoles.setconsolectrlhandler
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6fc64265-1403-45ea-925c-c5eb31d56734
topic_type:
- apiref
api_name:
- SetConsoleCtrlHandler
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 03e7166f84be2f760a4ffea385225390bdb3ffa1
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357709"
---
# <a name="setconsolectrlhandler-function"></a>Fonction SetConsoleCtrlHandler

Ajoute ou supprime une fonction [**HandlerRoutine**](handlerroutine.md) définie par l’application dans la liste des fonctions de gestionnaire pour le processus appelant.

Si aucune fonction de gestionnaire n’est spécifiée, la fonction définit un attribut pouvant être hérité qui détermine si le processus appelant ignore les signaux <kbd>CTRL</kbd>+<kbd>C</kbd>.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

## <a name="parameters"></a>Paramètres

*HandlerRoutine* \[entrée, facultatif\]  
Pointeur vers la fonction [**HandlerRoutine**](handlerroutine.md) définie par l’application à ajouter ou à supprimer. Ce paramètre peut être **NULL**.

*Add* \[entrée\]  
Si ce paramètre est **TRUE**, le gestionnaire est ajouté ; si la valeur est **FALSE**, le gestionnaire est supprimé.

Si le paramètre *HandlerRoutine* est **NULL**, une valeur **TRUE** fait que le processus appelant ignore l’entrée <kbd>CTRL</kbd>+<kbd>C</kbd>, et une valeur **FALSE** restaure le traitement normal de <kbd>CTRL</kbd>+<kbd>C</kbd>. Cet attribut pour ignorer ou traiter <kbd>CTRL</kbd>+<kbd>C</kbd> est hérité par les processus enfants.

## <a name="return-value"></a>Valeur retournée

Si la fonction réussit, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Remarques

Cette fonction fournit une notification similaire pour l’application console et les services fournis par [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) pour les applications graphiques avec une pompe de messages. Vous pouvez également utiliser cette fonction à partir d’une application graphique, mais il n’y a aucune garantie qu’elle arrive avant la notification de **WM\_QUERYENDSESSION**.

Chaque processus de console a sa propre liste de fonctions [**HandlerRoutine**](handlerroutine.md) définies par l’application qui gèrent les signaux <kbd>CTRL</kbd>+<kbd>C</kbd> et <kbd>CTRL</kbd>+<kbd>BREAK</kbd>. Les fonctions du gestionnaire gèrent également les signaux générés par le système quand l’utilisateur ferme la console, se déconnecte ou arrête le système. À la base, la liste de gestionnaires de chaque processus contient seulement une fonction de gestionnaire par défaut qui appelle la fonction [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess). Un processus de console ajoute ou supprime des fonctions de gestionnaire supplémentaires en appelant la fonction **SetConsoleCtrlHandler**, qui n’affecte pas la liste des fonctions de gestionnaire pour d’autres processus. Quand un processus de console reçoit un des signaux de contrôle, ses fonctions de gestionnaire sont appelées selon le principe « dernier enregistré, premier appelé », jusqu’à ce qu’un des gestionnaires retourne `TRUE`. Si aucun des gestionnaires ne retourne `TRUE`, le gestionnaire par défaut est appelé.

Pour les processus de la console, les combinaisons de touches <kbd>Ctrl</kbd>+<kbd>C</kbd> et <kbd>Ctrl</kbd>+<kbd>Pause</kbd> sont généralement traitées comme des signaux (**CTRL\_C\_EVENT** et **CTRL\_BREAK\_EVENT**). Quand une fenêtre de console avec le focus au clavier reçoit <kbd>CTRL</kbd>+<kbd>C</kbd> ou <kbd>CTRL</kbd>+<kbd>BREAK</kbd>, le signal est généralement passé à tous les processus qui partagent cette console.

<kbd>CTRL</kbd>+<kbd>BREAK</kbd> est toujours traitée comme un signal, mais le comportement habituel de <kbd>CTRL</kbd>+<kbd>C</kbd> peut être changé de trois façons qui empêchent l’appel des fonctions du gestionnaire :

- La fonction [**SetConsoleMode**](setconsolemode.md) peut désactiver le mode **ENABLE\_PROCESSED\_INPUT** pour la mémoire tampon d’entrée d’une console : <kbd>CTRL</kbd>+<kbd>C</kbd> est donc signalé comme étant une entrée du clavier au lieu d’un signal.
- L’appel de **SetConsoleCtrlHandler** avec les arguments **NULL** et **TRUE** fait que le processus appelant ignore les signaux <kbd>CTRL</kbd>+<kbd>C</kbd>. Cet attribut est hérité par les processus enfants, mais il peut être activé ou désactivé par n’importe quel processus sans affecter les processus existants.
- Si un processus de console est en cours de débogage et que les signaux <kbd>CTRL</kbd>+<kbd>C</kbd> n’ont pas été désactivés, le système génère une exception **DBG\_CONTROL\_C**. Cette exception est déclenchée seulement à destination du débogueur, et une application ne doit jamais utiliser un gestionnaire d’exceptions pour le gérer. Si le débogueur gère l’exception, une application ne va pas détecter le <kbd>CTRL</kbd>+<kbd>C</kbd>, à une exception près : les attentes susceptibles de déclencher des alertes vont se terminer. Si le débogueur passe l’exception en « non géré », <kbd>CTRL</kbd>+<kbd>C</kbd> est passé au processus de console et est traité en tant que signal, comme indiqué précédemment.

Un processus de console peut utiliser la fonction [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) pour envoyer un signal <kbd>CTRL</kbd>+<kbd>C</kbd> ou <kbd>CTRL</kbd>+<kbd>BREAK</kbd> à un groupe de processus de console.

Le système génère des signaux **CTRL\_CLOSE\_EVENT**, **CTRL\_LOGOFF\_EVENT** et **CTRL\_SHUTDOWN\_EVENT** quand l’utilisateur ferme la console, ferme une session ou arrête le système afin que le processus puisse être nettoyé avant l’arrêt. Les fonctions de console, ou les fonctions du runtime C qui appellent des fonctions de console, risquent de ne pas fonctionner de façon fiable lors du traitement des trois signaux mentionnés précédemment. La raison en est que tout ou partie des routines de nettoyage de la console interne peuvent avoir été appelées avant l’exécution du gestionnaire de signaux du processus.

**Windows 7, Windows 8, Windows 8.1 et Windows 10 :**

Si une application console charge la bibliothèque gdi32.dll ou user32.dll, la fonction [**HandlerRoutine**](handlerroutine.md) que vous spécifiez quand vous appelez **SetConsoleCtrlHandler** n’est pas appelée pour les événements **CTRL\_LOGOFF\_EVENT** et **CTRL\_SHUTDOWN\_EVENT**. Le système d’exploitation reconnaît les processus qui chargent gdi32.dll ou user32.dll en tant qu’applications Windows et non pas en tant qu’applications console. Ce comportement se produit également pour les applications console qui n’appellent pas directement des fonctions dans gdi32.dll ou user32.dll, mais qui appellent des fonctions comme des [fonctions Shell](/previous-versions/windows/desktop/legacy/bb776426(v=vs.85)) qui appellent à leur tour des fonctions dans gdi32.dll ou user32.dll.

Pour recevoir des événements quand un utilisateur se déconnecte ou que l’appareil s’arrête dans ces circonstances, créez une fenêtre masquée dans votre application console, puis gérez les messages de fenêtre [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) et [**WM\_ENDSESSION**](/windows/win32/shutdown/wm-endsession) que la fenêtre masquée reçoit. Vous pouvez créer une fenêtre masquée en appelant la méthode [**CreateWindowEx**](/windows/win32/api/winuser/nf-winuser-createwindowexa) avec le paramètre *dwExStyle* défini sur 0.

## <a name="examples"></a>Exemples

Pour obtenir un exemple, consultez [Inscription d’une fonction de gestionnaire de contrôle](registering-a-control-handler-function.md).

## <a name="requirements"></a>Configuration requise

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Windows 2000 Professionnel - \[Applications de bureau uniquement\] |
| Serveur minimal pris en charge | Windows 2000 Server - \[Applications de bureau uniquement\] |
| En-tête | ConsoleApi.h (via WinCon.h, inclure Windows.h) |
| Bibliothèque | Kernel32.lib |
| DLL | Kernel32.dll |
| Noms Unicode et ANSI | |

## <a name="see-also"></a>Voir aussi

[Gestionnaires de contrôle d’une console](console-control-handlers.md)

[Fonctions de console](console-functions.md)

[**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetConsoleMode**](getconsolemode.md)

[**HandlerRoutine**](handlerroutine.md)

[**SetConsoleMode**](setconsolemode.md)