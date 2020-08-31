---
title: Desplazarse por el contenido de un búfer de pantalla
description: La función ScrollConsoleScreenBuffer mueve un bloque de celdas de caracteres de una parte de un búfer de pantalla a otra parte del mismo búfer de pantalla.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
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
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060981"
---
# <a name="scrolling-a-screen-buffers-contents"></a>Desplazarse por el contenido de un búfer de pantalla


La función [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) mueve un bloque de celdas de caracteres de una parte de un búfer de pantalla a otra parte del mismo búfer de pantalla. La función especifica las celdas superior izquierda e inferior derecha del rectángulo de origen que se va a colocar y las coordenadas de destino de la nueva ubicación de la celda superior izquierda. Los datos de color y de carácter de las celdas de origen se mueven a la nueva ubicación y las celdas que quedan vacías por el movimiento se rellenan con el carácter y el color especificados. Si se especifica un rectángulo de recorte, las celdas que se encuentran fuera de ella permanecen sin cambios.

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) se puede usar para eliminar una línea especificando las coordenadas de la primera celda de la línea como las coordenadas de destino y especificando un rectángulo de desplazamiento que incluye todas las filas situadas debajo de la línea.

En el ejemplo siguiente se muestra el uso de un rectángulo de recorte para desplazar solo las 15 filas inferiores del búfer de pantalla de la consola. Las filas del rectángulo especificado se desplazan hacia arriba una línea cada vez y se descarta la fila superior del bloque. El contenido del búfer de pantalla de la consola fuera del rectángulo de recorte permanece inalterado.

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

## <a name="span-idrelated_topicsspanrelated-topics"></a><span id="related_topics"></span>Temas relacionados


[Desplazarse por la ventana de un búfer de pantalla](scrolling-a-screen-buffer-s-window.md)

[Desplazarse por el búfer de pantalla](scrolling-the-screen-buffer.md)

 

 




