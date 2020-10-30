---
title: Effacement de l’écran
description: Comment effacer l’écran de la console Windows à l’aide de la fonction système ou par programme à l’aide des fonctions d’API publiques.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: console, applications en mode caractère, applications en ligne de commande, applications de terminal, API console
MS-HAID:
- '\_win32\_clearing\_the\_screen'
- base.clearing\_the\_screen
- consoles.clearing\_the\_screen
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2097cc53-13b9-4f29-9d2c-feea56a27cb8
ms.openlocfilehash: 0207cde67faaa9516bb1e9fc57d55a00e06fa552
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037327"
---
# <a name="clearing-the-screen"></a><span data-ttu-id="feb5f-104">Effacement de l’écran</span><span class="sxs-lookup"><span data-stu-id="feb5f-104">Clearing the Screen</span></span>

<span data-ttu-id="feb5f-105">Il existe quatre façons de supprimer l’écran dans une application console.</span><span class="sxs-lookup"><span data-stu-id="feb5f-105">There are four ways to clear the screen in a console application.</span></span>

## <a name="example-1"></a><span data-ttu-id="feb5f-106">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="feb5f-106">Example 1</span></span>

> [!TIP]
> <span data-ttu-id="feb5f-107">Il s’agit de la méthode recommandée utilisant des **[séquences de terminaux virtuels](console-virtual-terminal-sequences.md)** pour tout nouveau développement.</span><span class="sxs-lookup"><span data-stu-id="feb5f-107">This is the recommended method using **[virtual terminal sequences](console-virtual-terminal-sequences.md)** for all new development.</span></span> <span data-ttu-id="feb5f-108">Pour plus d’informations, consultez la discussion sur les **[API de console classiques par rapport aux séquences de terminaux virtuels](classic-vs-vt.md)** .</span><span class="sxs-lookup"><span data-stu-id="feb5f-108">For more information, see the discussion of **[classic console APIs versus virtual terminal sequences](classic-vs-vt.md)** .</span></span>

<span data-ttu-id="feb5f-109">La première méthode consiste à définir votre application pour les séquences de sortie de terminal virtuel, puis à appeler la commande « Clear Screen ».</span><span class="sxs-lookup"><span data-stu-id="feb5f-109">The first method is to set your application up for virtual terminal output sequences and then call the "clear screen" command.</span></span>

```C
#include <windows.h>

int main( void )
{
    HANDLE hStdout;

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE);

    // Fetch existing console mode so we correctly add a flag and not turn off others
    DWORD mode = 0;
    if (!GetConsoleMode(hStdOut, &mode))
    {
        return ::GetLastError();
    }

    // Hold original mode to restore on exit to be cooperative with other command-line apps.
    const DWORD originalMode = mode;
    mode |= ENABLE_VIRTUAL_TERMINAL_PROCESSING;

    // Try to set the mode.
    if (!SetConsoleMode(hStdOut, mode))
    {
        return ::GetLastError();
    }

    // Write the sequence for clearing the display.
    DWORD written = 0;
    PCWSTR sequence = L"\x1b[2J";
    if (!WriteConsoleW(hStdOut, sequence, ARRAYSIZE(sequence), &written, NULL))
    {
        // If we fail, try to restore the mode on the way out.
        SetConsoleMode(hStdOut, originalMode);
        return ::GetLastError();
    }

    // To also clear the scroll back, emit L"\x1b[3J" as well.
    // 2J only clears the visible window and 3J only clears the scroll back.

    // Restore the mode on the way out to be nice to other command-line applications.
    SetConsoleMode(hStdOut, originalMode);

    return 0;
}
```

<span data-ttu-id="feb5f-110">Vous trouverez des variantes supplémentaires sur cette commande dans la documentation sur les séquences de terminaux virtuels sur **[Effacer dans l’affichage](console-virtual-terminal-sequences.md#text-modification)** .</span><span class="sxs-lookup"><span data-stu-id="feb5f-110">You can find additional variations on this command in the virtual terminal sequences documentation on **[Erase In Display](console-virtual-terminal-sequences.md#text-modification)** .</span></span>

## <a name="example-2"></a><span data-ttu-id="feb5f-111">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="feb5f-111">Example 2</span></span>

<span data-ttu-id="feb5f-112">La deuxième méthode consiste à écrire une fonction pour faire défiler le contenu de l’écran ou de la mémoire tampon et définir un remplissage pour l’espace révélé.</span><span class="sxs-lookup"><span data-stu-id="feb5f-112">The second method is to write a function to scroll the contents of the screen or buffer and set a fill for the revealed space.</span></span>

<span data-ttu-id="feb5f-113">Cela correspond au comportement de l’invite de commandes `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="feb5f-113">This matches the behavior of the command prompt `cmd.exe`.</span></span>

```C
#include <windows.h>

void cls(HANDLE hConsole)
{
    CONSOLE_SCREEN_BUFFER_INFO csbi;
    SMALL_RECT scrollRect;
    COORD scrollTarget;
    CHAR_INFO fill;

    // Get the number of character cells in the current buffer.
    if (!GetConsoleScreenBufferInfo(hConsole, &csbi))
    {
        return;
    }

    // Scroll the rectangle of the entire buffer.
    scrollRect.Left = 0;
    scrollRect.Top = 0;
    scrollRect.Right = csbi.dwSize.X;
    scrollRect.Bottom = csbi.dwSize.Y;

    // Scroll it upwards off the top of the buffer with a magnitude of the entire height.
    scrollTarget.X = 0;
    scrollTarget.Y = (SHORT)(0 - csbi.dwSize.Y);

    // Fill with empty spaces with the buffer's default text attribute.
    fill.Char.UnicodeChar = TEXT(' ');
    fill.Attributes = csbi.wAttributes;

    // Do the scroll
    ScrollConsoleScreenBuffer(hConsole, &scrollRect, NULL, scrollTarget, &fill);

    // Move the cursor to the top left corner too.
    csbi.dwCursorPosition.X = 0;
    csbi.dwCursorPosition.Y = 0;

    SetConsoleCursorPosition(hConsole, csbi.dwCursorPosition);
}

int main(void)
{
    HANDLE hStdout;

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE);

    cls(hStdout);

    return 0;
}

```

## <a name="example-3"></a><span data-ttu-id="feb5f-114">Exemple 3</span><span class="sxs-lookup"><span data-stu-id="feb5f-114">Example 3</span></span>

<span data-ttu-id="feb5f-115">La troisième méthode consiste à écrire une fonction pour effacer par programmation l’écran à l’aide des fonctions [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md) et [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) .</span><span class="sxs-lookup"><span data-stu-id="feb5f-115">The third method is to write a function to programmatically clear the screen using the [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md) and [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) functions.</span></span>

<span data-ttu-id="feb5f-116">L’exemple de code suivant illustre cette technique.</span><span class="sxs-lookup"><span data-stu-id="feb5f-116">The following sample code demonstrates this technique.</span></span>

```C
#include <windows.h>

void cls(HANDLE hConsole)
{
    COORD coordScreen = { 0, 0 };    // home for the cursor
    DWORD cCharsWritten;
    CONSOLE_SCREEN_BUFFER_INFO csbi;
    DWORD dwConSize;

    // Get the number of character cells in the current buffer.
    if (!GetConsoleScreenBufferInfo(hConsole, &csbi))
    {
        return;
    }

    dwConSize = csbi.dwSize.X * csbi.dwSize.Y;

    // Fill the entire screen with blanks.
    if (!FillConsoleOutputCharacter(hConsole,        // Handle to console screen buffer
                                    (TCHAR)' ',      // Character to write to the buffer
                                    dwConSize,       // Number of cells to write
                                    coordScreen,     // Coordinates of first cell
                                    &cCharsWritten)) // Receive number of characters written
    {
        return;
    }

    // Get the current text attribute.
    if (!GetConsoleScreenBufferInfo(hConsole, &csbi))
    {
        return;
    }

    // Set the buffer's attributes accordingly.
    if (!FillConsoleOutputAttribute(hConsole,         // Handle to console screen buffer
                                    csbi.wAttributes, // Character attributes to use
                                    dwConSize,        // Number of cells to set attribute
                                    coordScreen,      // Coordinates of first cell
                                    &cCharsWritten))  // Receive number of characters written
    {
        return;
    }

    // Put the cursor at its home coordinates.
    SetConsoleCursorPosition(hConsole, coordScreen);
}

int main(void)
{
    HANDLE hStdout;

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE);

    cls(hStdout);

    return 0;
}
```
