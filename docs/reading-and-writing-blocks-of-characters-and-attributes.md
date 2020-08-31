---
title: Lecture et écriture de blocs de caractères et d’attributs
description: La fonction ReadConsoleOutput copie un bloc rectangulaire de données d’attribut de caractère et de couleur à partir d’une mémoire tampon d’écran de console dans une mémoire tampon de destination.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_reading\_and\_writing\_blocks\_of\_characters\_and\_attributes'
- base.reading\_and\_writing\_blocks\_of\_characters\_and\_attributes
- consoles.reading\_and\_writing\_blocks\_of\_characters\_and\_attributes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: eaa57723-f003-4e90-8156-be8c3b42b912
ms.openlocfilehash: f7993979d358c46a6fb6f8411c52e8df50a1eed5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059449"
---
# <a name="reading-and-writing-blocks-of-characters-and-attributes"></a>Lecture et écriture de blocs de caractères et d’attributs


La fonction [**ReadConsoleOutput**](readconsoleoutput.md) copie un bloc rectangulaire de données d’attribut de caractère et de couleur à partir d’une mémoire tampon d’écran de console dans une mémoire tampon de destination. La fonction traite la mémoire tampon de destination comme un tableau à deux dimensions de structures d' [** \_ informations de type char**](char-info-str.md) . De même, la fonction [**WriteConsoleOutput**](writeconsoleoutput.md) copie un bloc rectangulaire de données de l’attribut character et Color d’une mémoire tampon source vers une mémoire tampon d’écran de la console. Pour plus d’informations sur la lecture ou l’écriture dans des blocs rectangulaires de cellules de mémoire tampon d’écran, consultez [méthodes d’entrée et de sortie](input-and-output-methods.md).

L’exemple suivant utilise la fonction [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) pour créer une nouvelle mémoire tampon d’écran. Une fois que la fonction [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) a fait de cela la mémoire tampon d’écran active, un bloc de caractères et des attributs de couleur est copié des deux lignes supérieures de la mémoire tampon d’écran stdout dans une mémoire tampon temporaire. Les données sont ensuite copiées à partir de la mémoire tampon temporaire dans la nouvelle mémoire tampon d’écran active. Lorsque l’application a fini d’utiliser la nouvelle mémoire tampon d’écran, elle appelle **SetConsoleActiveScreenBuffer** pour restaurer la mémoire tampon d’écran stdout d’origine.

```C
#include <windows.h> 
#include <stdio.h>
 
int main(void) 
{ 
    HANDLE hStdout, hNewScreenBuffer; 
    SMALL_RECT srctReadRect; 
    SMALL_RECT srctWriteRect; 
    CHAR_INFO chiBuffer[160]; // [2][80]; 
    COORD coordBufSize; 
    COORD coordBufCoord; 
    BOOL fSuccess; 
 
    // Get a handle to the STDOUT screen buffer to copy from and 
    // create a new screen buffer to copy to. 
 
    hStdout = GetStdHandle(STD_OUTPUT_HANDLE); 
    hNewScreenBuffer = CreateConsoleScreenBuffer( 
       GENERIC_READ |           // read/write access 
       GENERIC_WRITE, 
       FILE_SHARE_READ | 
       FILE_SHARE_WRITE,        // shared 
       NULL,                    // default security attributes 
       CONSOLE_TEXTMODE_BUFFER, // must be TEXTMODE 
       NULL);                   // reserved; must be NULL 
    if (hStdout == INVALID_HANDLE_VALUE || 
            hNewScreenBuffer == INVALID_HANDLE_VALUE) 
    {
        printf("CreateConsoleScreenBuffer failed - (%d)\n", GetLastError()); 
        return 1;
    }
 
    // Make the new screen buffer the active screen buffer. 
 
    if (! SetConsoleActiveScreenBuffer(hNewScreenBuffer) ) 
    {
        printf("SetConsoleActiveScreenBuffer failed - (%d)\n", GetLastError()); 
        return 1;
    }
 
    // Set the source rectangle. 
 
    srctReadRect.Top = 0;    // top left: row 0, col 0 
    srctReadRect.Left = 0; 
    srctReadRect.Bottom = 1; // bot. right: row 1, col 79 
    srctReadRect.Right = 79; 
 
    // The temporary buffer size is 2 rows x 80 columns. 
 
    coordBufSize.Y = 2; 
    coordBufSize.X = 80; 
 
    // The top left destination cell of the temporary buffer is 
    // row 0, col 0. 
 
    coordBufCoord.X = 0; 
    coordBufCoord.Y = 0; 
 
    // Copy the block from the screen buffer to the temp. buffer. 
 
    fSuccess = ReadConsoleOutput( 
       hStdout,        // screen buffer to read from 
       chiBuffer,      // buffer to copy into 
       coordBufSize,   // col-row size of chiBuffer 
       coordBufCoord,  // top left dest. cell in chiBuffer 
       &srctReadRect); // screen buffer source rectangle 
    if (! fSuccess) 
    {
        printf("ReadConsoleOutput failed - (%d)\n", GetLastError()); 
        return 1;
    }
 
    // Set the destination rectangle. 
 
    srctWriteRect.Top = 10;    // top lt: row 10, col 0 
    srctWriteRect.Left = 0; 
    srctWriteRect.Bottom = 11; // bot. rt: row 11, col 79 
    srctWriteRect.Right = 79; 
 
    // Copy from the temporary buffer to the new screen buffer. 
 
    fSuccess = WriteConsoleOutput( 
        hNewScreenBuffer, // screen buffer to write to 
        chiBuffer,        // buffer to copy from 
        coordBufSize,     // col-row size of chiBuffer 
        coordBufCoord,    // top left src cell in chiBuffer 
        &srctWriteRect);  // dest. screen buffer rectangle 
    if (! fSuccess) 
    {
        printf("WriteConsoleOutput failed - (%d)\n", GetLastError()); 
        return 1;
    }
    Sleep(5000); 
 
    // Restore the original active screen buffer. 
 
    if (! SetConsoleActiveScreenBuffer(hStdout)) 
    {
        printf("SetConsoleActiveScreenBuffer failed - (%d)\n", GetLastError()); 
        return 1;
    }

    return 0;
}
```

 

 




