---
title: Effacement de l’écran
description: Comment effacer l’écran de la console Windows à l’aide de la fonction système ou par programme à l’aide des fonctions d’API publiques.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_clearing\_the\_screen'
- base.clearing\_the\_screen
- consoles.clearing\_the\_screen
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2097cc53-13b9-4f29-9d2c-feea56a27cb8
ms.openlocfilehash: fd2a407e56d6b0fe00db59c5f783cb13546119f6
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059369"
---
# <a name="clearing-the-screen"></a><span data-ttu-id="ddb0a-104">Effacement de l’écran</span><span class="sxs-lookup"><span data-stu-id="ddb0a-104">Clearing the Screen</span></span>


<span data-ttu-id="ddb0a-105">Il existe deux façons de supprimer l’écran dans une application console.</span><span class="sxs-lookup"><span data-stu-id="ddb0a-105">There are two ways to clear the screen in a console application.</span></span>

## <a name="span-idexample_1spanspan-idexample_1spanspan-idexample_1spanexample-1"></a><span data-ttu-id="ddb0a-106"><span id="Example_1"></span><span id="example_1"></span><span id="EXAMPLE_1"></span>Exemple 1</span><span class="sxs-lookup"><span data-stu-id="ddb0a-106"><span id="Example_1"></span><span id="example_1"></span><span id="EXAMPLE_1"></span>Example 1</span></span>


<span data-ttu-id="ddb0a-107">La première méthode consiste à utiliser la fonction **système** Runtime C.</span><span class="sxs-lookup"><span data-stu-id="ddb0a-107">The first method is to use the C run-time **system** function.</span></span> <span data-ttu-id="ddb0a-108">La fonction **système** appelle la commande **CLS** fournie par l’interpréteur de commandes pour effacer l’écran.</span><span class="sxs-lookup"><span data-stu-id="ddb0a-108">The **system** function invokes the **cls** command provided by the command interpreter to clear the screen.</span></span>

```C
#include <stdlib.h>

int main( void )
{
    system("cls");
    return 0;
}
```

## <a name="span-idexample_2spanspan-idexample_2spanspan-idexample_2spanexample-2"></a><span data-ttu-id="ddb0a-109"><span id="Example_2"></span><span id="example_2"></span><span id="EXAMPLE_2"></span>Exemple 2</span><span class="sxs-lookup"><span data-stu-id="ddb0a-109"><span id="Example_2"></span><span id="example_2"></span><span id="EXAMPLE_2"></span>Example 2</span></span>


<span data-ttu-id="ddb0a-110">La deuxième méthode consiste à écrire une fonction pour effacer par programmation l’écran à l’aide des fonctions [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md) et [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) .</span><span class="sxs-lookup"><span data-stu-id="ddb0a-110">The second method is to write a function to programmatically clear the screen using the [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md) and [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) functions.</span></span> <span data-ttu-id="ddb0a-111">L’exemple de code suivant illustre cette technique.</span><span class="sxs-lookup"><span data-stu-id="ddb0a-111">The following sample code demonstrates this technique.</span></span>

```C
#include <windows.h>

void cls( HANDLE hConsole )
{
   COORD coordScreen = { 0, 0 };    // home for the cursor 
   DWORD cCharsWritten;
   CONSOLE_SCREEN_BUFFER_INFO csbi; 
   DWORD dwConSize;

// Get the number of character cells in the current buffer. 

   if( !GetConsoleScreenBufferInfo( hConsole, &csbi ))
   {
      return;
   }

   dwConSize = csbi.dwSize.X * csbi.dwSize.Y;

   // Fill the entire screen with blanks.

   if( !FillConsoleOutputCharacter( hConsole,        // Handle to console screen buffer 
                                    (TCHAR) ' ',     // Character to write to the buffer
                                    dwConSize,       // Number of cells to write 
                                    coordScreen,     // Coordinates of first cell 
                                    &cCharsWritten ))// Receive number of characters written
   {
      return;
   }

   // Get the current text attribute.

   if( !GetConsoleScreenBufferInfo( hConsole, &csbi ))
   {
      return;
   }

   // Set the buffer's attributes accordingly.

   if( !FillConsoleOutputAttribute( hConsole,         // Handle to console screen buffer 
                                    csbi.wAttributes, // Character attributes to use
                                    dwConSize,        // Number of cells to set attribute 
                                    coordScreen,      // Coordinates of first cell 
                                    &cCharsWritten )) // Receive number of characters written
   {
      return;
   }

   // Put the cursor at its home coordinates.

   SetConsoleCursorPosition( hConsole, coordScreen );
}

int main( void )
{
    HANDLE hStdout;

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE);

    cls(hStdout);
    
    return 0;
}
```

 

 




