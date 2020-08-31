---
title: HandlerRoutine fonction de rappel
description: Fonction définie par l’application utilisée avec la fonction SetConsoleCtrlHandler. Un processus de console utilise cette fonction pour gérer les signaux de contrôle reçus par le processus.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
- Wincon.h
api_type:
- UserDefined
ms.openlocfilehash: 14205baaddd98c8c22881c5f448119412e1f4a1c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059332"
---
# <a name="handlerroutine-callback-function"></a>HandlerRoutine fonction de rappel


Fonction définie par l’application utilisée avec la fonction [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) . Un processus de console utilise cette fonction pour gérer les signaux de contrôle reçus par le processus. Lorsque le signal est reçu, le système crée un nouveau thread dans le processus pour exécuter la fonction.

Le type de ** \_ routine PHANDLER** définit un pointeur vers cette fonction de rappel. **HandlerRoutine** est un espace réservé pour le nom de la fonction définie par l’application.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI HandlerRoutine(
  _In_ DWORD dwCtrlType
);
```

<a name="parameters"></a>Paramètres
----------

*dwCtrlType* \[ dans\]  
Type de signal de contrôle reçu par le gestionnaire. Ce paramètre peut prendre l’une des valeurs suivantes.

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
<td><span id="CTRL_C_EVENT"></span><span id="ctrl_c_event"></span>
<strong>CTRL_C_EVENT</strong> 0</td>
<td><p>Un signal CTRL + C a été reçu, soit à partir d’une entrée au clavier, soit à partir d’un signal généré par la fonction <a href="generateconsolectrlevent.md" data-raw-source="[&lt;strong&gt;GenerateConsoleCtrlEvent&lt;/strong&gt;](generateconsolectrlevent.md)"><strong>GenerateConsoleCtrlEvent</strong></a> .</p></td>
</tr>
<tr class="even">
<td><span id="CTRL_BREAK_EVENT"></span><span id="ctrl_break_event"></span>
<strong>CTRL_BREAK_EVENT</strong> 1</td>
<td><p>Un signal CTRL + ATTN a été reçu, soit à partir d’une entrée au clavier, soit à partir d’un signal généré par <a href="generateconsolectrlevent.md" data-raw-source="[&lt;strong&gt;GenerateConsoleCtrlEvent&lt;/strong&gt;](generateconsolectrlevent.md)"><strong>GenerateConsoleCtrlEvent</strong></a>.</p></td>
</tr>
<tr class="odd">
<td><span id="CTRL_CLOSE_EVENT"></span><span id="ctrl_close_event"></span>
<strong>CTRL_CLOSE_EVENT</strong> 2</td>
<td><p>Signal que le système envoie à tous les processus attachés à une console lorsque l’utilisateur ferme la console (en cliquant sur <strong>Fermer</strong> dans la fenêtre de la console&#39;le menu fenêtre, ou en cliquant sur la commande terminer le bouton <strong>tâche</strong> du gestionnaire des tâches).</p></td>
</tr>
<tr class="even">
<td><span id="CTRL_LOGOFF_EVENT"></span><span id="ctrl_logoff_event"></span>
<strong>CTRL_LOGOFF_EVENT</strong> 5</td>
<td><p>Signal que le système envoie à tous les processus de la console lorsqu’un utilisateur se déconnecte. Ce signal n’indique pas quel utilisateur se déconnecte, donc aucune hypothèse ne peut être faite.</p>
<p>Notez que ce signal est reçu uniquement par les services. Les applications interactives se terminent à la fermeture de session. elles ne sont donc pas présentes lorsque le système envoie ce signal.</p></td>
</tr>
<tr class="odd">
<td><span id="CTRL_SHUTDOWN_EVENT"></span><span id="ctrl_shutdown_event"></span>
<strong>CTRL_SHUTDOWN_EVENT</strong> 6</td>
<td><p>Signal que le système envoie lorsque le système est en cours d’arrêt. Les applications interactives ne sont pas présentes au moment où le système envoie ce signal. par conséquent, il est possible de recevoir uniquement des services dans cette situation. Les services disposent également de leur propre mécanisme de notification pour les événements d’arrêt. Pour plus d’informations, consultez <a href="https://msdn.microsoft.com/library/windows/desktop/ms683240" data-raw-source="[&lt;strong&gt;Handler&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/ms683240)"><strong>handler</strong></a>.</p>
<p>Ce signal peut également être généré par une application à l’aide de <a href="generateconsolectrlevent.md" data-raw-source="[&lt;strong&gt;GenerateConsoleCtrlEvent&lt;/strong&gt;](generateconsolectrlevent.md)"><strong>GenerateConsoleCtrlEvent</strong></a>.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Valeur retournée
------------

Si la fonction gère le signal de contrôle, elle doit retourner **true**. Si elle retourne **false**, la fonction de gestionnaire suivante dans la liste des gestionnaires pour ce processus est utilisée.

<a name="remarks"></a>Remarques
-------

Étant donné que le système crée un nouveau thread dans le processus pour exécuter la fonction de gestionnaire, il est possible que la fonction de gestionnaire se termine par un autre thread dans le processus. Veillez à synchroniser les threads dans le processus avec le thread pour la fonction de gestionnaire.

Chaque processus de console possède sa propre liste de fonctions **HandlerRoutine** . Initialement, cette liste contient uniquement une fonction de gestionnaire par défaut qui appelle [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658). Un processus de console ajoute ou supprime des fonctions gestionnaires supplémentaires en appelant la fonction [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) , qui n’affecte pas la liste des fonctions de gestionnaire pour d’autres processus. Lorsqu’un processus de console reçoit l’un des signaux de contrôle, ses fonctions de gestionnaire sont appelées sur une base de dernier enregistrement, première appel, jusqu’à ce que l’un des gestionnaires retourne la **valeur true**. Si aucun des gestionnaires ne retourne la **valeur true**, le gestionnaire par défaut est appelé.

Les signaux de l’événement **CTRL \_ Close \_ **, de l' ** \_ \_ événement Ctrl Logoff**et de la **touche Ctrl \_ arrêter \_ ** permettent au processus de nettoyer avant l’arrêt. Un **HandlerRoutine** peut effectuer tout nettoyage nécessaire, puis effectuer l’une des actions suivantes :

- Appelez la fonction [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) pour terminer le processus.
- Retourne **false**. Si aucune des fonctions de gestionnaire inscrites ne retourne la **valeur true**, le gestionnaire par défaut arrête le processus.
- Retourne la **valeur true**. Dans ce cas, aucune autre fonction de gestionnaire n’est appelée et le système met fin au processus.

Un processus peut utiliser la fonction [**SetProcessShutdownParameters**](https://msdn.microsoft.com/library/windows/desktop/ms686227) pour empêcher le système d’afficher une boîte de dialogue à l’utilisateur lors de la fermeture ou de l’arrêt. Dans ce cas, le système met fin au processus lorsque **HandlerRoutine** retourne la **valeur true** ou lorsque le délai d’attente est écoulé.

Lorsqu’une application console est exécutée en tant que service, elle reçoit un gestionnaire de contrôle de console par défaut modifié. Ce gestionnaire modifié n’appelle pas [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) lors du traitement des signaux d’événement **CTRL \_ Logoff \_ ** et **CTRL \_ Shutdown \_ ** . Cela permet au service de continuer à s’exécuter après la fermeture de la session de l’utilisateur. Si le service installe son propre gestionnaire de contrôle de console, ce gestionnaire est appelé avant le gestionnaire par défaut. Si le gestionnaire installé appelle **ExitProcess** lors du traitement du signal d' ** \_ \_ événement Ctrl Logoff** , le service se termine lorsque l’utilisateur se déconnecte.

Notez qu’une bibliothèque ou une DLL tierce peut installer un gestionnaire de contrôle de console pour votre application. Si c’est le cas, ce gestionnaire remplace le gestionnaire par défaut et peut provoquer la fermeture de l’application lorsque l’utilisateur se déconnecte.

## <a name="timeouts"></a>Délais d'expiration

| Événement                  | Circonstances                   | Délai d'expiration                                                     |
|------------------------|---------------------------------|-------------------------------------------------------------|
| `CTRL_CLOSE_EVENT`     | _aux_                           | paramètre système `SPI_GETHUNGAPPTIMEOUT` , 5 000 MS            |
| `CTRL_LOGOFF_EVENT`    | _rapide_[1] | clé `CriticalAppShutdownTimeout` de registre ou 500 ms          |
| `CTRL_LOGOFF_EVENT`    | _aucun des éléments ci-dessus_             | paramètre système `SPI_GETWAITTOKILLTIMEOUT` , 5 000 MS         |
| `CTRL_SHUTDOWN_EVENT`  | **processus de service**             | paramètre système `SPI_GETWAITTOKILLSERVICETIMEOUT` , 20000ms |
| `CTRL_SHUTDOWN_EVENT`  | _rapide_[1] | clé `CriticalAppShutdownTimeout` de registre ou 500 ms          |
| `CTRL_SHUTDOWN_EVENT`  | _aucun des éléments ci-dessus_             | paramètre système `SPI_GETWAITTOKILLTIMEOUT` , 5 000 MS         |
| `CTRL_C`, `CTRL_BREAK` | _aux_                           | **aucun délai d’attente**                                              |

_[1] : les événements « rapides » ne sont jamais utilisés, mais il reste du code pour les prendre en charge._

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
<td><p>Windows 2000 professionnel [applications de bureau uniquement]</p></td>
</tr>
<tr class="even">
<td><p>Serveur minimal pris en charge</p></td>
<td><p>Serveur Windows 2000 [applications de bureau uniquement]</p></td>
</tr>
<tr class="odd">
<td><p>En-tête</p></td>
<td>ConsoleApi. h (via wincon. h, incluez Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Voir aussi


[Gestionnaires de contrôle de console](console-control-handlers.md)

[Fonctions de la console](console-functions.md)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetProcessShutdownParameters**](https://msdn.microsoft.com/library/windows/desktop/ms683221)

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md)

[**SetProcessShutdownParameters**](https://msdn.microsoft.com/library/windows/desktop/ms686227)

 

 




