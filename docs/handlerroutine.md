---
title: HandlerRoutine fonction de rappel
description: Fonction définie par l’application utilisée avec la fonction SetConsoleCtrlHandler. Un processus de console utilise cette fonction pour gérer les signaux de contrôle reçus par le processus.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
f1_keywords:
- consoleapi/HandlerRoutine
- wincon/HandlerRoutine
- HandlerRoutine
MS-HAID:
- '\_win32\_handlerroutine'
- base.handlerroutine
- consoles.handlerroutine
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2e8732fa-7dfd-415b-b2fc-c27a400496f2
topic_type:
- apiref
api_name:
- HandlerRoutine
api_location:
- WinCon.h
api_type:
- UserDefined
ms.openlocfilehash: d078000b7c0acee73593543058f2195befc6f5e2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037747"
---
# <a name="handlerroutine-callback-function"></a>HandlerRoutine fonction de rappel

Fonction définie par l’application utilisée avec la fonction [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) . Un processus de console utilise cette fonction pour gérer les signaux de contrôle reçus par le processus. Lorsque le signal est reçu, le système crée un nouveau thread dans le processus pour exécuter la fonction.

Le type de **\_ routine PHANDLER** définit un pointeur vers cette fonction de rappel. **HandlerRoutine** est un espace réservé pour le nom de la fonction définie par l’application.

## <a name="syntax"></a>Syntaxe

```C
BOOL WINAPI HandlerRoutine(
  _In_ DWORD dwCtrlType
);
```

## <a name="parameters"></a>Paramètres

*dwCtrlType* \[ dans\]  
Type de signal de contrôle reçu par le gestionnaire. Ce paramètre peut prendre l’une des valeurs suivantes.

| Valeur | Signification |
|-|-|
| **CTRL_C_EVENT** 0 | Un signal <kbd>CTRL</kbd> + <kbd>C</kbd> a été reçu, soit à partir d’une entrée au clavier, soit à partir d’un signal généré par la fonction **[GenerateConsoleCtrlEvent](generateconsolectrlevent.md)** . |
| **CTRL_BREAK_EVENT** 1 | Un <kbd>CTRL</kbd> + signal de <kbd>coupure</kbd> Ctrl a été reçu, soit à partir d’une entrée au clavier, soit à partir d’un signal généré par **[GenerateConsoleCtrlEvent](generateconsolectrlevent.md)** . |
| **CTRL_CLOSE_EVENT** 2 | Signal que le système envoie à tous les processus attachés à une console lorsque l’utilisateur ferme la console (en cliquant sur **Fermer** dans le menu fenêtre de la fenêtre de la console, ou en cliquant sur la commande terminer le bouton **tâche** du gestionnaire des tâches). |
| **CTRL_LOGOFF_EVENT** 5 | Signal que le système envoie à tous les processus de la console lorsqu’un utilisateur se déconnecte. Ce signal n’indique pas quel utilisateur se déconnecte, donc aucune hypothèse ne peut être faite.<br /><br />Notez que ce signal est reçu uniquement par les services. Les applications interactives se terminent à la fermeture de session. elles ne sont donc pas présentes lorsque le système envoie ce signal. |
| **CTRL_SHUTDOWN_EVENT** 6 | Signal que le système envoie lorsque le système est en cours d’arrêt. Les applications interactives ne sont pas présentes au moment où le système envoie ce signal. par conséquent, il est possible de recevoir uniquement des services dans cette situation. Les services disposent également de leur propre mécanisme de notification pour les événements d’arrêt. Pour plus d’informations, consultez **[handler](https://msdn.microsoft.com/library/windows/desktop/ms683240)** .<br /><br />Ce signal peut également être généré par une application à l’aide de **[GenerateConsoleCtrlEvent](generateconsolectrlevent.md)** . |

## <a name="return-value"></a>Valeur retournée

Si la fonction gère le signal de contrôle, elle doit retourner **true** . Si elle retourne **false** , la fonction de gestionnaire suivante dans la liste des gestionnaires pour ce processus est utilisée.

## <a name="remarks"></a>Remarques

Étant donné que le système crée un nouveau thread dans le processus pour exécuter la fonction de gestionnaire, il est possible que la fonction de gestionnaire se termine par un autre thread dans le processus. Veillez à synchroniser les threads dans le processus avec le thread pour la fonction de gestionnaire.

Chaque processus de console possède sa propre liste de fonctions **HandlerRoutine** . Initialement, cette liste contient uniquement une fonction de gestionnaire par défaut qui appelle [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658). Un processus de console ajoute ou supprime des fonctions gestionnaires supplémentaires en appelant la fonction [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) , qui n’affecte pas la liste des fonctions de gestionnaire pour d’autres processus. Lorsqu’un processus de console reçoit l’un des signaux de contrôle, ses fonctions de gestionnaire sont appelées sur une base de dernier enregistrement, première appel, jusqu’à ce que l’un des gestionnaires retourne la **valeur true** . Si aucun des gestionnaires ne retourne la **valeur true** , le gestionnaire par défaut est appelé.

Les signaux de l’événement **CTRL \_ Close \_** , de l' **\_ \_ événement Ctrl Logoff** et de la **touche Ctrl \_ arrêter \_** permettent au processus de nettoyer avant l’arrêt. Un **HandlerRoutine** peut effectuer tout nettoyage nécessaire, puis effectuer l’une des actions suivantes :

- Appelez la fonction [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) pour terminer le processus.
- Retourne **false** . Si aucune des fonctions de gestionnaire inscrites ne retourne la **valeur true** , le gestionnaire par défaut arrête le processus.
- Retourne la **valeur true** . Dans ce cas, aucune autre fonction de gestionnaire n’est appelée et le système met fin au processus.

Un processus peut utiliser la fonction [**SetProcessShutdownParameters**](https://msdn.microsoft.com/library/windows/desktop/ms686227) pour empêcher le système d’afficher une boîte de dialogue à l’utilisateur lors de la fermeture ou de l’arrêt. Dans ce cas, le système met fin au processus lorsque **HandlerRoutine** retourne la **valeur true** ou lorsque le délai d’attente est écoulé.

Lorsqu’une application console est exécutée en tant que service, elle reçoit un gestionnaire de contrôle de console par défaut modifié. Ce gestionnaire modifié n’appelle pas [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) lors du traitement des signaux d’événement **CTRL \_ Logoff \_** et **CTRL \_ Shutdown \_** . Cela permet au service de continuer à s’exécuter après la fermeture de la session de l’utilisateur. Si le service installe son propre gestionnaire de contrôle de console, ce gestionnaire est appelé avant le gestionnaire par défaut. Si le gestionnaire installé appelle **ExitProcess** lors du traitement du signal d' **\_ \_ événement Ctrl Logoff** , le service se termine lorsque l’utilisateur se déconnecte.

Notez qu’une bibliothèque ou une DLL tierce peut installer un gestionnaire de contrôle de console pour votre application. Si c’est le cas, ce gestionnaire remplace le gestionnaire par défaut et peut provoquer la fermeture de l’application lorsque l’utilisateur se déconnecte.

## <a name="timeouts"></a>Délais d’expiration

| Événement                  | Circonstances                   | Délai d'expiration                                                     |
|------------------------|---------------------------------|-------------------------------------------------------------|
| `CTRL_CLOSE_EVENT`     | _aux_                           | paramètre système `SPI_GETHUNGAPPTIMEOUT` , 5 000 MS            |
| `CTRL_LOGOFF_EVENT`    | _rapide_ [1] | clé `CriticalAppShutdownTimeout` de registre ou 500 ms          |
| `CTRL_LOGOFF_EVENT`    | _aucun des éléments ci-dessus_             | paramètre système `SPI_GETWAITTOKILLTIMEOUT` , 5 000 MS         |
| `CTRL_SHUTDOWN_EVENT`  | **processus de service**             | paramètre système `SPI_GETWAITTOKILLSERVICETIMEOUT` , 20000ms |
| `CTRL_SHUTDOWN_EVENT`  | _rapide_ [1] | clé `CriticalAppShutdownTimeout` de registre ou 500 ms          |
| `CTRL_SHUTDOWN_EVENT`  | _aucun des éléments ci-dessus_             | paramètre système `SPI_GETWAITTOKILLTIMEOUT` , 5 000 MS         |
| `CTRL_C`, `CTRL_BREAK` | _aux_                           | **aucun délai d’attente**                                              |

_[1] : les événements « rapides » ne sont jamais utilisés, mais il reste du code pour les prendre en charge._

## <a name="requirements"></a>Spécifications

| &nbsp; | &nbsp; |
|-|-|
| Client minimal pris en charge | Applications de bureau Windows 2000 professionnel \[ uniquement\] |
| Serveur minimal pris en charge | Applications de bureau Windows 2000 Server \[ uniquement\] |
| En-tête | ConsoleApi. h (via WinCon. h, incluez Windows. h) |

## <a name="see-also"></a>Voir aussi

[Gestionnaires de contrôle d’une console](console-control-handlers.md)

[Fonctions de la console](console-functions.md)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetProcessShutdownParameters**](https://msdn.microsoft.com/library/windows/desktop/ms683221)

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md)

[**SetProcessShutdownParameters**](https://msdn.microsoft.com/library/windows/desktop/ms686227)
