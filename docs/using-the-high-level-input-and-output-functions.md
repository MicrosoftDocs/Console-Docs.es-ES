---
title: Usar las funciones de entrada y salida de High-Level
description: En el ejemplo siguiente se usan las funciones de e/s de la consola de alto nivel para la e/s de la consola. Para obtener más información sobre las funciones de e/s de la consola de alto nivel, vea High-Level e/s de la consola.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_using\_the\_high\_level\_input\_and\_output\_functions'
- base.using\_the\_high\_level\_input\_and\_output\_functions
- consoles.using\_the\_high\_level\_input\_and\_output\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0226cd94-86d0-452b-80e6-e0fed8af0a62
ms.openlocfilehash: 13ad97a30459ba3abd0ed197352e69e6e8b45d47
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037073"
---
# <a name="using-the-high-level-input-and-output-functions"></a><span data-ttu-id="5a4a0-105">Usar las funciones de entrada y salida de High-Level</span><span class="sxs-lookup"><span data-stu-id="5a4a0-105">Using the High-Level Input and Output Functions</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="5a4a0-106">En el ejemplo siguiente se usan las funciones de e/s de la consola de alto nivel para la e/s de la consola.</span><span class="sxs-lookup"><span data-stu-id="5a4a0-106">The following example uses the high-level console I/O functions for console I/O.</span></span> <span data-ttu-id="5a4a0-107">Para obtener más información sobre las funciones de e/s de la consola de alto nivel, consulte [e/s de la consola de alto nivel](high-level-console-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="5a4a0-107">For more information about the high-level console I/O functions, see [High-Level Console I/O](high-level-console-i-o.md).</span></span>

<span data-ttu-id="5a4a0-108">En el ejemplo se da por supuesto que los modos de e/s predeterminados están en vigor inicialmente para las primeras llamadas a las funciones [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) .</span><span class="sxs-lookup"><span data-stu-id="5a4a0-108">The example assumes that the default I/O modes are in effect initially for the first calls to the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) functions.</span></span> <span data-ttu-id="5a4a0-109">A continuación, se cambia el modo de entrada para activar el modo de entrada sin conexión y el modo de entrada de Eco para la segunda llamada a **readfile** y **WriteFile** .</span><span class="sxs-lookup"><span data-stu-id="5a4a0-109">Then the input mode is changed to turn offline input mode and echo input mode for the second calls to **ReadFile** and **WriteFile** .</span></span> <span data-ttu-id="5a4a0-110">La función [**SetConsoleTextAttribute**](setconsoletextattribute.md) se usa para establecer los colores en los que se mostrará el texto escrito posteriormente.</span><span class="sxs-lookup"><span data-stu-id="5a4a0-110">The [**SetConsoleTextAttribute**](setconsoletextattribute.md) function is used to set the colors in which subsequently written text will be displayed.</span></span> <span data-ttu-id="5a4a0-111">Antes de salir, el programa restaura el modo de entrada de la consola original y los atributos de color.</span><span class="sxs-lookup"><span data-stu-id="5a4a0-111">Before exiting, the program restores the original console input mode and color attributes.</span></span>

<span data-ttu-id="5a4a0-112">La función del ejemplo `NewLine` se usa cuando se deshabilita el modo de entrada de línea.</span><span class="sxs-lookup"><span data-stu-id="5a4a0-112">The example's `NewLine` function is used when line input mode is disabled.</span></span> <span data-ttu-id="5a4a0-113">Controla los retornos de carro moviendo la posición del cursor a la primera celda de la fila siguiente.</span><span class="sxs-lookup"><span data-stu-id="5a4a0-113">It handles carriage returns by moving the cursor position to the first cell of the next row.</span></span> <span data-ttu-id="5a4a0-114">Si el cursor ya está en la última fila del búfer de pantalla de la consola, el contenido del búfer de pantalla de la consola se desplaza una línea hacia arriba.</span><span class="sxs-lookup"><span data-stu-id="5a4a0-114">If the cursor is already in the last row of the console screen buffer, the contents of the console screen buffer are scrolled up one line.</span></span>

```C
#include <windows.h>

void NewLine(void);
void ScrollScreenBuffer(HANDLE, INT);

HANDLE hStdout, hStdin;
CONSOLE_SCREEN_BUFFER_INFO csbiInfo;

int main(void)
{
    LPSTR lpszPrompt1 = "Type a line and press Enter, or q to quit: ";
    LPSTR lpszPrompt2 = "Type any key, or q to quit: ";
    CHAR chBuffer[256];
    DWORD cRead, cWritten, fdwMode, fdwOldMode;
    WORD wOldColorAttrs;

    // Get handles to STDIN and STDOUT.

    hStdin = GetStdHandle(STD_INPUT_HANDLE);
    hStdout = GetStdHandle(STD_OUTPUT_HANDLE);
    if (hStdin == INVALID_HANDLE_VALUE ||
        hStdout == INVALID_HANDLE_VALUE)
    {
        MessageBox(NULL, TEXT("GetStdHandle"), TEXT("Console Error"),
            MB_OK);
        return 1;
    }

    // Save the current text colors.

    if (! GetConsoleScreenBufferInfo(hStdout, &csbiInfo))
    {
        MessageBox(NULL, TEXT("GetConsoleScreenBufferInfo"),
            TEXT("Console Error"), MB_OK);
        return 1;
    }

    wOldColorAttrs = csbiInfo.wAttributes;

    // Set the text attributes to draw red text on black background.

    if (! SetConsoleTextAttribute(hStdout, FOREGROUND_RED |
            FOREGROUND_INTENSITY))
    {
        MessageBox(NULL, TEXT("SetConsoleTextAttribute"),
            TEXT("Console Error"), MB_OK);
        return 1;
    }

    // Write to STDOUT and read from STDIN by using the default
    // modes. Input is echoed automatically, and ReadFile
    // does not return until a carriage return is typed.
    //
    // The default input modes are line, processed, and echo.
    // The default output modes are processed and wrap at EOL.

    while (1)
    {
        if (! WriteFile(
            hStdout,               // output handle
            lpszPrompt1,           // prompt string
            lstrlenA(lpszPrompt1), // string length
            &cWritten,             // bytes written
            NULL) )                // not overlapped
        {
            MessageBox(NULL, TEXT("WriteFile"), TEXT("Console Error"),
                MB_OK);
            return 1;
        }

        if (! ReadFile(
            hStdin,    // input handle
            chBuffer,  // buffer to read into
            255,       // size of buffer
            &cRead,    // actual bytes read
            NULL) )    // not overlapped
        break;
        if (chBuffer[0] == 'q') break;
    }

    // Turn off the line input and echo input modes

    if (! GetConsoleMode(hStdin, &fdwOldMode))
    {
       MessageBox(NULL, TEXT("GetConsoleMode"), TEXT("Console Error"),
           MB_OK);
       return 1;
    }

    fdwMode = fdwOldMode &
        ~(ENABLE_LINE_INPUT | ENABLE_ECHO_INPUT);
    if (! SetConsoleMode(hStdin, fdwMode))
    {
       MessageBox(NULL, TEXT("SetConsoleMode"), TEXT("Console Error"),
           MB_OK);
       return 1;
    }

    // ReadFile returns when any input is available.  
    // WriteFile is used to echo input.

    NewLine();

    while (1)
    {
        if (! WriteFile(
            hStdout,               // output handle
            lpszPrompt2,           // prompt string
            lstrlenA(lpszPrompt2), // string length
            &cWritten,             // bytes written
            NULL) )                // not overlapped
        {
            MessageBox(NULL, TEXT("WriteFile"), TEXT("Console Error"),
                MB_OK);
            return 1;
        }

        if (! ReadFile(hStdin, chBuffer, 1, &cRead, NULL))
            break;
        if (chBuffer[0] == '\r')
            NewLine();
        else if (! WriteFile(hStdout, chBuffer, cRead,
            &cWritten, NULL)) break;
        else
            NewLine();
        if (chBuffer[0] == 'q') break;
    }

    // Restore the original console mode.

    SetConsoleMode(hStdin, fdwOldMode);

    // Restore the original text colors.

    SetConsoleTextAttribute(hStdout, wOldColorAttrs);

    return 0;
}

// The NewLine function handles carriage returns when the processed
// input mode is disabled. It gets the current cursor position
// and resets it to the first cell of the next row.

void NewLine(void)
{
    if (! GetConsoleScreenBufferInfo(hStdout, &csbiInfo))
    {
        MessageBox(NULL, TEXT("GetConsoleScreenBufferInfo"),
            TEXT("Console Error"), MB_OK);
        return;
    }

    csbiInfo.dwCursorPosition.X = 0;

    // If it is the last line in the screen buffer, scroll
    // the buffer up.

    if ((csbiInfo.dwSize.Y-1) == csbiInfo.dwCursorPosition.Y)
    {
        ScrollScreenBuffer(hStdout, 1);
    }

    // Otherwise, advance the cursor to the next line.

    else csbiInfo.dwCursorPosition.Y += 1;

    if (! SetConsoleCursorPosition(hStdout,
        csbiInfo.dwCursorPosition))
    {
        MessageBox(NULL, TEXT("SetConsoleCursorPosition"),
            TEXT("Console Error"), MB_OK);
        return;
    }
}

void ScrollScreenBuffer(HANDLE h, INT x)
{
    SMALL_RECT srctScrollRect, srctClipRect;
    CHAR_INFO chiFill;
    COORD coordDest;

    srctScrollRect.Left = 0;
    srctScrollRect.Top = 1;
    srctScrollRect.Right = csbiInfo.dwSize.X - (SHORT)x;
    srctScrollRect.Bottom = csbiInfo.dwSize.Y - (SHORT)x;

    // The destination for the scroll rectangle is one row up.

    coordDest.X = 0;
    coordDest.Y = 0;

    // The clipping rectangle is the same as the scrolling rectangle.
    // The destination row is left unchanged.

    srctClipRect = srctScrollRect;

    // Set the fill character and attributes.

    chiFill.Attributes = FOREGROUND_RED|FOREGROUND_INTENSITY;
    chiFill.Char.AsciiChar = (char)' ';

    // Scroll up one line.

    ScrollConsoleScreenBuffer(
        h,               // screen buffer handle
        &srctScrollRect, // scrolling rectangle
        &srctClipRect,   // clipping rectangle
        coordDest,       // top left destination cell
        &chiFill);       // fill character and color
}
```
