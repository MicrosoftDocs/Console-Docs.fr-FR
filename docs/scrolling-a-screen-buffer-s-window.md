---
title: Défilement de la fenêtre d’une mémoire tampon d’écran
description: La fonction SetConsoleWindowInfo peut être utilisée pour faire défiler le contenu d’une mémoire tampon d’écran dans la fenêtre de console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_scrolling\_a\_screen\_buffer\_s\_window'
- base.scrolling\_a\_screen\_buffer\_s\_window
- consoles.scrolling\_a\_screen\_buffer\_s\_window
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bc300349-9bfa-4417-92ad-57a05a658ce5
ms.openlocfilehash: 02d39574e38c277bc7637816cd8e3866278a87e6
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059460"
---
# <a name="scrolling-a-screen-buffers-window"></a><span data-ttu-id="6ca71-104">Défilement de la fenêtre d’une mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="6ca71-104">Scrolling a Screen Buffer's Window</span></span>


<span data-ttu-id="6ca71-105">La fonction [**SetConsoleWindowInfo**](setconsolewindowinfo.md) peut être utilisée pour faire défiler le contenu d’une mémoire tampon d’écran dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="6ca71-105">The [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function can be used to scroll the contents of a screen buffer in the console window.</span></span> <span data-ttu-id="6ca71-106">Cette fonction peut également modifier la taille de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="6ca71-106">This function can also change the window size.</span></span> <span data-ttu-id="6ca71-107">La fonction peut spécifier les nouveaux angles supérieur gauche et inférieur droit de la fenêtre de la mémoire tampon de l’écran de la console en tant que coordonnées de mémoire tampon de l’écran absolu ou spécifier les modifications des coordonnées de la fenêtre active.</span><span class="sxs-lookup"><span data-stu-id="6ca71-107">The function can either specify the new upper left and lower right corners of the console screen buffer's window as absolute screen buffer coordinates or specify the changes from the current window coordinates.</span></span> <span data-ttu-id="6ca71-108">La fonction échoue si les coordonnées de fenêtre spécifiées sont en dehors des limites de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="6ca71-108">The function fails if the specified window coordinates are outside the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="6ca71-109">L’exemple suivant fait défiler la vue de la mémoire tampon de l’écran de la console vers le haut en modifiant les coordonnées de la fenêtre retournées par la fonction [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="6ca71-109">The following example scrolls the view of the console screen buffer up by modifying the window coordinates returned by the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span> <span data-ttu-id="6ca71-110">La `ScrollByAbsoluteCoord` fonction montre comment spécifier des coordonnées absolues, tandis que la `ScrollByRelativeCoord` fonction montre comment spécifier des coordonnées relatives.</span><span class="sxs-lookup"><span data-stu-id="6ca71-110">The `ScrollByAbsoluteCoord` function demonstrates how to specify absolute coordinates, while the `ScrollByRelativeCoord` function demonstrates how to specify relative coordinates.</span></span>

```C
#include <windows.h>
#include <stdio.h>
#include <conio.h>

HANDLE hStdout; 

int ScrollByAbsoluteCoord(int iRows)
{
    CONSOLE_SCREEN_BUFFER_INFO csbiInfo; 
    SMALL_RECT srctWindow; 
 
    // Get the current screen buffer size and window position. 
 
    if (! GetConsoleScreenBufferInfo(hStdout, &csbiInfo)) 
    {
        printf("GetConsoleScreenBufferInfo (%d)\n", GetLastError()); 
        return 0;
    }
 
    // Set srctWindow to the current window size and location. 
 
    srctWindow = csbiInfo.srWindow; 
 
    // Check whether the window is too close to the screen buffer top
 
    if ( srctWindow.Top >= iRows ) 
    { 
        srctWindow.Top -= (SHORT)iRows;     // move top up
        srctWindow.Bottom -= (SHORT)iRows;  // move bottom up

        if (! SetConsoleWindowInfo( 
                   hStdout,          // screen buffer handle 
                   TRUE,             // absolute coordinates 
                   &srctWindow))     // specifies new location 
        {
            printf("SetConsoleWindowInfo (%d)\n", GetLastError()); 
            return 0;
        }
        return iRows;
    }
    else
    {
        printf("\nCannot scroll; the window is too close to the top.\n");
        return 0;
    }
}

int ScrollByRelativeCoord(int iRows)
{
    CONSOLE_SCREEN_BUFFER_INFO csbiInfo; 
    SMALL_RECT srctWindow; 

    // Get the current screen buffer window position. 
 
    if (! GetConsoleScreenBufferInfo(hStdout, &csbiInfo)) 
    {
        printf("GetConsoleScreenBufferInfo (%d)\n", GetLastError()); 
        return 0;
    }
 
    // Check whether the window is too close to the screen buffer top
 
    if (csbiInfo.srWindow.Top >= iRows) 
    { 
        srctWindow.Top =- (SHORT)iRows;     // move top up
        srctWindow.Bottom =- (SHORT)iRows;  // move bottom up 
        srctWindow.Left = 0;         // no change 
        srctWindow.Right = 0;        // no change 
 
        if (! SetConsoleWindowInfo( 
                   hStdout,          // screen buffer handle 
                   FALSE,            // relative coordinates
                   &srctWindow))     // specifies new location 
        {
            printf("SetConsoleWindowInfo (%d)\n", GetLastError()); 
            return 0;
        }
        return iRows;
    }
    else
    {
        printf("\nCannot scroll; the window is too close to the top.\n");
        return 0;
    }
}

int main( void )
{
    int i;

    printf("\nPrinting twenty lines, then scrolling up five lines.\n");
    printf("Press any key to scroll up ten lines; ");
    printf("then press another key to stop the demo.\n");
    for(i=0; i<=20; i++)
        printf("%d\n", i);

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE); 

    if(ScrollByAbsoluteCoord(5))
        _getch();
    else return 0;

    if(ScrollByRelativeCoord(10))
        _getch();
    else return 0;
}
```

## <a name="span-idrelated_topicsspanrelated-topics"></a><span data-ttu-id="6ca71-111"><span id="related_topics"></span>Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="6ca71-111"><span id="related_topics"></span>Related topics</span></span>


[<span data-ttu-id="6ca71-112">Faire défiler le contenu d’une mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="6ca71-112">Scrolling a Screen Buffer's Contents</span></span>](scrolling-a-screen-buffer-s-contents.md)

[<span data-ttu-id="6ca71-113">Défilement de la mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="6ca71-113">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

 

 




