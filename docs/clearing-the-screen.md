---
title: Borrar la pantalla
description: Cómo borrar la pantalla de la consola de Windows mediante la función del sistema o mediante programación con las funciones de la API pública.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
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
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037333"
---
# <a name="clearing-the-screen"></a>Borrar la pantalla

Hay cuatro maneras de borrar la pantalla en una aplicación de consola.

## <a name="example-1"></a>Ejemplo 1

> [!TIP]
> Este es el método recomendado mediante **[secuencias de terminal virtuales](console-virtual-terminal-sequences.md)** para todo el desarrollo nuevo. Para obtener más información, consulte la explicación de las **[API de consola clásica frente a las secuencias de terminales virtuales](classic-vs-vt.md)** .

El primer método consiste en configurar la aplicación para las secuencias de salida de terminal virtuales y, a continuación, llamar al comando "borrar pantalla".

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

Puede encontrar otras variaciones en este comando en la documentación de las secuencias de terminal virtuales en **[borrar en pantalla](console-virtual-terminal-sequences.md#text-modification)** .

## <a name="example-2"></a>Ejemplo 2

El segundo método consiste en escribir una función para desplazar el contenido de la pantalla o el búfer y establecer un relleno para el espacio mostrado.

Esto coincide con el comportamiento del símbolo del sistema `cmd.exe` .

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

## <a name="example-3"></a>Ejemplo 3

El tercer método consiste en escribir una función para borrar la pantalla mediante programación con las funciones [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md) y [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) .

En el código de ejemplo siguiente se muestra esta técnica.

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
