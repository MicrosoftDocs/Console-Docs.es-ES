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
# <a name="scrolling-a-screen-buffers-contents"></a><span data-ttu-id="a628b-104">Desplazarse por el contenido de un búfer de pantalla</span><span class="sxs-lookup"><span data-stu-id="a628b-104">Scrolling a Screen Buffer's Contents</span></span>


<span data-ttu-id="a628b-105">La función [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) mueve un bloque de celdas de caracteres de una parte de un búfer de pantalla a otra parte del mismo búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="a628b-105">The [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) function moves a block of character cells from one part of a screen buffer to another part of the same screen buffer.</span></span> <span data-ttu-id="a628b-106">La función especifica las celdas superior izquierda e inferior derecha del rectángulo de origen que se va a colocar y las coordenadas de destino de la nueva ubicación de la celda superior izquierda.</span><span class="sxs-lookup"><span data-stu-id="a628b-106">The function specifies the upper left and lower right cells of the source rectangle to be moved and the destination coordinates of the new location for the upper left cell.</span></span> <span data-ttu-id="a628b-107">Los datos de color y de carácter de las celdas de origen se mueven a la nueva ubicación y las celdas que quedan vacías por el movimiento se rellenan con el carácter y el color especificados.</span><span class="sxs-lookup"><span data-stu-id="a628b-107">The character and color data in the source cells is moved to the new location, and any cells left empty by the move are filled in with a specified character and color.</span></span> <span data-ttu-id="a628b-108">Si se especifica un rectángulo de recorte, las celdas que se encuentran fuera de ella permanecen sin cambios.</span><span class="sxs-lookup"><span data-stu-id="a628b-108">If a clipping rectangle is specified, the cells outside of it are left unchanged.</span></span>

<span data-ttu-id="a628b-109">[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) se puede usar para eliminar una línea especificando las coordenadas de la primera celda de la línea como las coordenadas de destino y especificando un rectángulo de desplazamiento que incluye todas las filas situadas debajo de la línea.</span><span class="sxs-lookup"><span data-stu-id="a628b-109">[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) can be used to delete a line by specifying coordinates of the first cell in the line as the destination coordinates and specifying a scrolling rectangle that includes all the rows below the line.</span></span>

<span data-ttu-id="a628b-110">En el ejemplo siguiente se muestra el uso de un rectángulo de recorte para desplazar solo las 15 filas inferiores del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="a628b-110">The following example shows the use of a clipping rectangle to scroll only the bottom 15 rows of the console screen buffer.</span></span> <span data-ttu-id="a628b-111">Las filas del rectángulo especificado se desplazan hacia arriba una línea cada vez y se descarta la fila superior del bloque.</span><span class="sxs-lookup"><span data-stu-id="a628b-111">The rows in the specified rectangle are scrolled up one line at a time, and the top row of the block is discarded.</span></span> <span data-ttu-id="a628b-112">El contenido del búfer de pantalla de la consola fuera del rectángulo de recorte permanece inalterado.</span><span class="sxs-lookup"><span data-stu-id="a628b-112">The contents of the console screen buffer outside the clipping rectangle are left unchanged.</span></span>

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

## <a name="span-idrelated_topicsspanrelated-topics"></a><span data-ttu-id="a628b-113"><span id="related_topics"></span>Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="a628b-113"><span id="related_topics"></span>Related topics</span></span>


[<span data-ttu-id="a628b-114">Desplazarse por la ventana de un búfer de pantalla</span><span class="sxs-lookup"><span data-stu-id="a628b-114">Scrolling a Screen Buffer's Window</span></span>](scrolling-a-screen-buffer-s-window.md)

[<span data-ttu-id="a628b-115">Desplazarse por el búfer de pantalla</span><span class="sxs-lookup"><span data-stu-id="a628b-115">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

 

 




