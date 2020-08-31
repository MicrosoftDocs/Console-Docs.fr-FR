---
title: Faire défiler le contenu d’une mémoire tampon d’écran
description: La fonction ScrollConsoleScreenBuffer déplace un bloc de cellules de caractères d’une partie d’une mémoire tampon d’écran vers une autre partie de la même mémoire tampon d’écran.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applications en mode caractère, applications en ligne de commande, applications Terminal Server, API de console
MS-HAID:
- '\_win32\_scrolling\_a\_screen\_buffer\_s\_contents'
- base.scrolling\_a\_screen\_buffer\_s\_contents
- consoles.scrolling\_a\_screen\_buffer\_s\_contents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 288c6a0f-fbaa-4eee-895e-a25884b7b70a
ms.openlocfilehash: a25e9ad7a27977e6dbfcf58de2cf7a250ffd6c4d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059445"
---
# <a name="scrolling-a-screen-buffers-contents"></a><span data-ttu-id="7b008-104">Faire défiler le contenu d’une mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="7b008-104">Scrolling a Screen Buffer's Contents</span></span>


<span data-ttu-id="7b008-105">La fonction [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) déplace un bloc de cellules de caractères d’une partie d’une mémoire tampon d’écran vers une autre partie de la même mémoire tampon d’écran.</span><span class="sxs-lookup"><span data-stu-id="7b008-105">The [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) function moves a block of character cells from one part of a screen buffer to another part of the same screen buffer.</span></span> <span data-ttu-id="7b008-106">La fonction spécifie les cellules supérieure gauche et inférieure droite du rectangle source à déplacer et les coordonnées de destination du nouvel emplacement pour la cellule supérieure gauche.</span><span class="sxs-lookup"><span data-stu-id="7b008-106">The function specifies the upper left and lower right cells of the source rectangle to be moved and the destination coordinates of the new location for the upper left cell.</span></span> <span data-ttu-id="7b008-107">Les données de caractère et de couleur des cellules sources sont déplacées vers le nouvel emplacement, et toutes les cellules laissées vides par le déplacement sont remplies avec un caractère et une couleur spécifiés.</span><span class="sxs-lookup"><span data-stu-id="7b008-107">The character and color data in the source cells is moved to the new location, and any cells left empty by the move are filled in with a specified character and color.</span></span> <span data-ttu-id="7b008-108">Si un rectangle de découpage est spécifié, les cellules en dehors de celui-ci restent inchangées.</span><span class="sxs-lookup"><span data-stu-id="7b008-108">If a clipping rectangle is specified, the cells outside of it are left unchanged.</span></span>

<span data-ttu-id="7b008-109">[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) peut être utilisé pour supprimer une ligne en spécifiant des coordonnées de la première cellule de la ligne comme coordonnées de destination et en spécifiant un rectangle de défilement qui comprend toutes les lignes sous la ligne.</span><span class="sxs-lookup"><span data-stu-id="7b008-109">[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) can be used to delete a line by specifying coordinates of the first cell in the line as the destination coordinates and specifying a scrolling rectangle that includes all the rows below the line.</span></span>

<span data-ttu-id="7b008-110">L’exemple suivant illustre l’utilisation d’un rectangle de découpage pour faire défiler uniquement les 15 lignes inférieures de la mémoire tampon d’écran de la console.</span><span class="sxs-lookup"><span data-stu-id="7b008-110">The following example shows the use of a clipping rectangle to scroll only the bottom 15 rows of the console screen buffer.</span></span> <span data-ttu-id="7b008-111">Les lignes du rectangle spécifié défilent d’une ligne à la fois, et la ligne supérieure du bloc est ignorée.</span><span class="sxs-lookup"><span data-stu-id="7b008-111">The rows in the specified rectangle are scrolled up one line at a time, and the top row of the block is discarded.</span></span> <span data-ttu-id="7b008-112">Le contenu de la mémoire tampon d’écran de la console en dehors du rectangle de découpage reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="7b008-112">The contents of the console screen buffer outside the clipping rectangle are left unchanged.</span></span>

```C
#include <windows.h>
#include <stdio.h>

int main( void )
{
    HANDLE hStdout; 
    CONSOLE_SCREEN_BUFFER_INFO csbiInfo; 
    SMALL_RECT srctScrollRect, srctClipRect; 
    CHAR_INFO chiFill; 
    COORD coordDest; 
    int i;

    printf("\nPrinting 20 lines for reference. ");
    printf("Notice that line 6 is discarded during scrolling.\n");
    for(i=0; i<=20; i++)
        printf("%d\n", i);
 
    hStdout = GetStdHandle(STD_OUTPUT_HANDLE); 

    if (hStdout == INVALID_HANDLE_VALUE) 
    {
        printf("GetStdHandle failed with %d\n", GetLastError()); 
        return 1;
    }
 
    // Get the screen buffer size. 
 
    if (!GetConsoleScreenBufferInfo(hStdout, &csbiInfo)) 
    {
        printf("GetConsoleScreenBufferInfo failed %d\n", GetLastError()); 
        return 1;
    }
 
    // The scrolling rectangle is the bottom 15 rows of the 
    // screen buffer. 
 
    srctScrollRect.Top = csbiInfo.dwSize.Y - 16; 
    srctScrollRect.Bottom = csbiInfo.dwSize.Y - 1; 
    srctScrollRect.Left = 0; 
    srctScrollRect.Right = csbiInfo.dwSize.X - 1; 
 
    // The destination for the scroll rectangle is one row up. 
 
    coordDest.X = 0; 
    coordDest.Y = csbiInfo.dwSize.Y - 17; 
 
    // The clipping rectangle is the same as the scrolling rectangle. 
    // The destination row is left unchanged. 
 
    srctClipRect = srctScrollRect; 
 
    // Fill the bottom row with green blanks. 
 
    chiFill.Attributes = BACKGROUND_GREEN | FOREGROUND_RED; 
    chiFill.Char.AsciiChar = (char)' '; 
 
    // Scroll up one line. 
 
    if(!ScrollConsoleScreenBuffer(  
        hStdout,         // screen buffer handle 
        &srctScrollRect, // scrolling rectangle 
        &srctClipRect,   // clipping rectangle 
        coordDest,       // top left destination cell 
        &chiFill))       // fill character and color
    {
        printf("ScrollConsoleScreenBuffer failed %d\n", GetLastError()); 
        return 1;
    }
return 0;
}
```

## <a name="span-idrelated_topicsspanrelated-topics"></a><span data-ttu-id="7b008-113"><span id="related_topics"></span>Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="7b008-113"><span id="related_topics"></span>Related topics</span></span>


[<span data-ttu-id="7b008-114">Défilement de la fenêtre d’une mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="7b008-114">Scrolling a Screen Buffer's Window</span></span>](scrolling-a-screen-buffer-s-window.md)

[<span data-ttu-id="7b008-115">Défilement de la mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="7b008-115">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

 

 




