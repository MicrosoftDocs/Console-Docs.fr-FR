---
title: Lecture des événements de mémoire tampon d’entrée
description: La fonction ReadConsoleInput peut être utilisée pour accéder directement à la mémoire tampon d’entrée d’une console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_reading\_input\_buffer\_events'
- base.reading\_input\_buffer\_events
- consoles.reading\_input\_buffer\_events
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 57570f3b-4a37-4789-bf6c-474fae60171d
ms.openlocfilehash: 2604add28fa89fa5650d2802069e3e0559272e11
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059448"
---
# <a name="reading-input-buffer-events"></a>Lecture des événements de mémoire tampon d’entrée


La fonction [**ReadConsoleInput**](readconsoleinput.md) peut être utilisée pour accéder directement à la mémoire tampon d’entrée d’une console. Quand une console est créée, l’entrée de la souris est activée et l’entrée de fenêtre est désactivée. Pour vous assurer que le processus reçoit tous les types d’événements, cet exemple utilise la fonction [**SetConsoleMode**](setconsolemode.md) pour activer l’entrée de la souris et de la fenêtre. Il passe ensuite dans une boucle qui lit et gère les événements d’entrée de la console 100. Par exemple, le message « événement de clavier » s’affiche lorsque l’utilisateur appuie sur une touche et que le message « événement de souris » s’affiche lorsque l’utilisateur interagit avec la souris.

```C
#include <windows.h>
#include <stdio.h>

HANDLE hStdin; 
DWORD fdwSaveOldMode;

VOID ErrorExit(LPSTR);
VOID KeyEventProc(KEY_EVENT_RECORD); 
VOID MouseEventProc(MOUSE_EVENT_RECORD); 
VOID ResizeEventProc(WINDOW_BUFFER_SIZE_RECORD); 
 
int main(VOID) 
{ 
    DWORD cNumRead, fdwMode, i; 
    INPUT_RECORD irInBuf[128]; 
    int counter=0;
 
    // Get the standard input handle. 
 
    hStdin = GetStdHandle(STD_INPUT_HANDLE); 
    if (hStdin == INVALID_HANDLE_VALUE) 
        ErrorExit("GetStdHandle"); 
 
    // Save the current input mode, to be restored on exit. 
 
    if (! GetConsoleMode(hStdin, &fdwSaveOldMode) ) 
        ErrorExit("GetConsoleMode"); 

    // Enable the window and mouse input events. 
 
    fdwMode = ENABLE_WINDOW_INPUT | ENABLE_MOUSE_INPUT; 
    if (! SetConsoleMode(hStdin, fdwMode) ) 
        ErrorExit("SetConsoleMode"); 
 
    // Loop to read and handle the next 100 input events. 
 
    while (counter++ <= 100) 
    { 
        // Wait for the events. 
 
        if (! ReadConsoleInput( 
                hStdin,      // input buffer handle 
                irInBuf,     // buffer to read into 
                128,         // size of read buffer 
                &cNumRead) ) // number of records read 
            ErrorExit("ReadConsoleInput"); 
 
        // Dispatch the events to the appropriate handler. 
 
        for (i = 0; i < cNumRead; i++) 
        {
            switch(irInBuf[i].EventType) 
            { 
                case KEY_EVENT: // keyboard input 
                    KeyEventProc(irInBuf[i].Event.KeyEvent); 
                    break; 
 
                case MOUSE_EVENT: // mouse input 
                    MouseEventProc(irInBuf[i].Event.MouseEvent); 
                    break; 
 
                case WINDOW_BUFFER_SIZE_EVENT: // scrn buf. resizing 
                    ResizeEventProc( irInBuf[i].Event.WindowBufferSizeEvent ); 
                    break; 
 
                case FOCUS_EVENT:  // disregard focus events 
 
                case MENU_EVENT:   // disregard menu events 
                    break; 
 
                default: 
                    ErrorExit("Unknown event type"); 
                    break; 
            } 
        }
    } 

    // Restore input mode on exit.

    SetConsoleMode(hStdin, fdwSaveOldMode);
 
    return 0; 
}

VOID ErrorExit (LPSTR lpszMessage) 
{ 
    fprintf(stderr, "%s\n", lpszMessage); 

    // Restore input mode on exit.

    SetConsoleMode(hStdin, fdwSaveOldMode);

    ExitProcess(0); 
}

VOID KeyEventProc(KEY_EVENT_RECORD ker)
{
    printf("Key event: ");

    if(ker.bKeyDown)
        printf("key pressed\n");
    else printf("key released\n");
}

VOID MouseEventProc(MOUSE_EVENT_RECORD mer)
{
#ifndef MOUSE_HWHEELED
#define MOUSE_HWHEELED 0x0008
#endif
    printf("Mouse event: ");
    
    switch(mer.dwEventFlags)
    {
        case 0:

            if(mer.dwButtonState == FROM_LEFT_1ST_BUTTON_PRESSED)
            {
                printf("left button press \n");
            }
            else if(mer.dwButtonState == RIGHTMOST_BUTTON_PRESSED)
            {
                printf("right button press \n");
            }
            else
            {
                printf("button press\n");
            }
            break;
        case DOUBLE_CLICK:
            printf("double click\n");
            break;
        case MOUSE_HWHEELED:
            printf("horizontal mouse wheel\n");
            break;
        case MOUSE_MOVED:
            printf("mouse moved\n");
            break;
        case MOUSE_WHEELED:
            printf("vertical mouse wheel\n");
            break;
        default:
            printf("unknown\n");
            break;
    }
}

VOID ResizeEventProc(WINDOW_BUFFER_SIZE_RECORD wbsr)
{
    printf("Resize event\n");
    printf("Console screen buffer is %d columns by %d rows.\n", wbsr.dwSize.X, wbsr.dwSize.Y);
}
```

 

 




