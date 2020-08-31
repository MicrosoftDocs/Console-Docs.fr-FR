---
title: SetConsoleCtrlHandler fonction)
description: Ajoute ou supprime une fonction HandlerRoutine définie par l’application dans la liste des fonctions de gestionnaire pour le processus appelant.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
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
ms.openlocfilehash: cd7b491c1a395483d4aef052d4147d3edf2514e5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059416"
---
# <a name="setconsolectrlhandler-function"></a>SetConsoleCtrlHandler fonction)


Ajoute ou supprime une fonction [**HandlerRoutine**](handlerroutine.md) définie par l’application dans la liste des fonctions de gestionnaire pour le processus appelant.

Si aucune fonction de gestionnaire n’est spécifiée, la fonction définit un attribut pouvant être hérité qui détermine si le processus appelant ignore les signaux CTRL + C.

<a name="syntax"></a>Syntaxe
------

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

<a name="parameters"></a>Paramètres
----------

*HandlerRoutine* \[ dans, facultatif\]  
Pointeur vers la fonction [**HandlerRoutine**](handlerroutine.md) définie par l’application à ajouter ou à supprimer. Ce paramètre peut avoir la **valeur null**.

*Ajouter* \[ dans\]  
Si ce paramètre a la **valeur true**, le gestionnaire est ajouté ; Si la **valeur est false**, le gestionnaire est supprimé.

Si le paramètre *HandlerRoutine* est **null**, une valeur **true** fait que le processus appelant ignore l’entrée Ctrl + c, et une valeur **false** restaure le traitement normal de l’entrée Ctrl + c. Cet attribut qui ignore ou traite les touches CTRL + C est hérité par les processus enfants.

<a name="return-value"></a>Valeur retournée
------------

Si la fonction est réussie, la valeur de retour est différente de zéro.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, appelez [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Remarques
-------

Cette fonction fournit une notification similaire pour l’application console et les services que [**WM \_ QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) fournit pour les applications graphiques avec une pompe de messages. Vous pouvez également utiliser cette fonction à partir d’une application graphique, mais il n’y a aucune garantie qu’elle arriverait avant la notification de **WM \_ QUERYENDSESSION**.

Chaque processus de console possède sa propre liste de fonctions [**HandlerRoutine**](handlerroutine.md) définies par l’application qui gèrent les signaux Ctrl + C et CTRL + ATTN. Les fonctions de gestionnaire gèrent également les signaux générés par le système lorsque l’utilisateur ferme la console, se déconnecte ou arrête le système. Initialement, la liste de gestionnaires de chaque processus contient uniquement une fonction de gestionnaire par défaut qui appelle la fonction [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) . Un processus de console ajoute ou supprime des fonctions gestionnaires supplémentaires en appelant la fonction **SetConsoleCtrlHandler** , qui n’affecte pas la liste des fonctions de gestionnaire pour d’autres processus. Lorsqu’un processus de console reçoit l’un des signaux de contrôle, ses fonctions de gestionnaire sont appelées sur une base de dernier enregistrement, première appel, jusqu’à ce que l’un des gestionnaires retourne la valeur TRUE. Si aucun des gestionnaires ne retourne la valeur TRUE, le gestionnaire par défaut est appelé.

Pour les processus de console, les combinaisons de touches CTRL + C et CTRL + ATTN sont généralement traitées comme des signaux (événement**CTRL + \_ c \_ ** et **CTRL + \_ \_ événement**). Quand une fenêtre de console avec le focus clavier reçoit CTRL + C ou CTRL + ATTN, le signal est généralement passé à tous les processus qui partagent cette console.

CTRL + ATTN est toujours traité comme un signal, mais le comportement par défaut de CTRL + C peut être modifié de trois manières qui empêchent l’appel des fonctions du gestionnaire :

- La fonction [**SetConsoleMode**](setconsolemode.md) peut désactiver l' **activation du mode \_ \_ d’entrée traité** pour la mémoire tampon d’entrée d’une console. par conséquent, Ctrl + C est signalé comme entrée au clavier plutôt que comme signal.
- L’appel de **SetConsoleCtrlHandler** avec les arguments **null** et **true** fait que le processus appelant ignore les signaux Ctrl + C. Cet attribut est hérité par les processus enfants, mais il peut être activé ou désactivé par n’importe quel processus sans affecter les processus existants.
- Si un processus de console est en cours de débogage et que les signaux CTRL + C n’ont pas été désactivés, le système génère une exception ** \_ \_ C de contrôle dbg** . Cette exception est déclenchée uniquement pour l’avantage du débogueur, et une application ne doit jamais utiliser un gestionnaire d’exceptions pour le gérer. Si le débogueur gère l’exception, une application ne remarquera pas CTRL + C, à une exception près : les attentes alertables se terminent. Si le débogueur passe l’exception sur non géré, CTRL + C est passé au processus de console et traité comme un signal, comme indiqué précédemment.

Un processus de console peut utiliser la fonction [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) pour envoyer un signal Ctrl + C ou CTRL + ATTN à un groupe de processus de console.

Le système génère des signaux d’événement **CTRL \_ Close \_ **, **CTRL de fermeture de \_ session \_ **et **CTRL \_ Shutdown \_ ** quand l’utilisateur ferme la console, ferme une session ou arrête le système afin que le processus puisse effectuer un nettoyage avant son arrêt. Les fonctions de console, ou toutes les fonctions runtime C qui appellent des fonctions de console, peuvent ne pas fonctionner de manière fiable pendant le traitement de l’un des trois signaux mentionnés précédemment. En effet, une partie ou la totalité des routines de nettoyage de la console interne peut avoir été appelée avant l’exécution du gestionnaire de signal de processus.

**Windows 7, Windows 8, Windows 8.1 et Windows 10 :**

Si une application console charge la gdi32.dll ou la bibliothèque de user32.dll, la fonction [**HandlerRoutine**](handlerroutine.md) que vous spécifiez lorsque vous appelez **SetConsoleCtrlHandler** n’est pas appelée pour les événements **CTRL \_ Logoff \_ ** et **CTRL \_ Shutdown \_ Event** . Le système d’exploitation reconnaît les processus qui chargent gdi32.dll ou user32.dll en tant qu’applications Windows plutôt qu’en tant qu’applications console. Ce comportement se produit également pour les applications de console qui n’appellent pas directement des fonctions dans gdi32.dll ou user32.dll, mais qui appellent des fonctions telles que des [fonctions Shell](https://msdn.microsoft.com/library/windows/desktop/bb776426) qui appellent à leur tour des fonctions dans gdi32.dll ou user32.dll.

Pour recevoir des événements lorsqu’un utilisateur se déconnecte ou que l’appareil s’arrête dans ces circonstances, créez une fenêtre masquée dans votre application console, puis gérez les messages de fenêtre [**WM \_ QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) et [**WM \_ ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) que la fenêtre masquée reçoit. Vous pouvez créer une fenêtre masquée en appelant la méthode [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) avec le paramètre *dwExStyle* défini sur 0.

<a name="examples"></a>Exemples
--------

Pour obtenir un exemple, consultez [inscription d’une fonction de gestionnaire de contrôle](registering-a-control-handler-function.md).

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


[Gestionnaires de contrôle de console](console-control-handlers.md)

[Fonctions de la console](console-functions.md)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetConsoleMode**](getconsolemode.md)

[**HandlerRoutine**](handlerroutine.md)

[**SetConsoleMode**](setconsolemode.md)

 

 




