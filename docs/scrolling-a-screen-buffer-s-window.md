---
title: Desplazamiento por la ventana de un búfer de pantalla
description: La función SetConsoleWindowInfo se puede usar para desplazar el contenido de un búfer de pantalla en la ventana de la consola.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_scrolling\_a\_screen\_buffer\_s\_window'
- base.scrolling\_a\_screen\_buffer\_s\_window
- consoles.scrolling\_a\_screen\_buffer\_s\_window
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bc300349-9bfa-4417-92ad-57a05a658ce5
ms.openlocfilehash: 332edf04a2f6f4ebaa9b482d2dc3f15381190855
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039433"
---
# <a name="scrolling-a-screen-buffers-window"></a>Desplazamiento por la ventana de un búfer de pantalla

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

La función [**SetConsoleWindowInfo**](setconsolewindowinfo.md) se puede usar para desplazar el contenido de un búfer de pantalla en la ventana de la consola. Esta función también puede cambiar el tamaño de la ventana. La función puede especificar las esquinas superior izquierda e inferior derecha de la ventana del búfer de pantalla de la consola como coordenadas de búfer de pantalla absolutas o especificar los cambios de las coordenadas de la ventana actual. Se produce un error en la función si las coordenadas de la ventana especificadas están fuera de los límites del búfer de pantalla de la consola.

En el ejemplo siguiente se desplaza la vista del búfer de la pantalla de la consola mediante la modificación de las coordenadas de la ventana devueltas por la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) . La `ScrollByAbsoluteCoord` función muestra cómo especificar coordenadas absolutas, mientras que la `ScrollByRelativeCoord` función muestra cómo especificar coordenadas relativas.

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

## <a name="related-topics"></a>Temas relacionados

[Desplazamiento por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md)

[Desplazarse por el búfer de pantalla](scrolling-the-screen-buffer.md)
