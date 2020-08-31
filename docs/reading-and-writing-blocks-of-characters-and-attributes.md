---
title: Leer y escribir bloques de caracteres y atributos
description: La función ReadConsoleOutput copia un bloque rectangular de datos de atributos de caracteres y colores desde un búfer de pantalla de la consola en un búfer de destino.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
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
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060985"
---
# <a name="reading-and-writing-blocks-of-characters-and-attributes"></a>Leer y escribir bloques de caracteres y atributos


La función [**ReadConsoleOutput**](readconsoleoutput.md) copia un bloque rectangular de datos de atributos de caracteres y colores desde un búfer de pantalla de la consola en un búfer de destino. La función trata el búfer de destino como una matriz bidimensional de estructuras de [** \_ información de caracteres**](char-info-str.md) . Del mismo modo, la función [**WriteConsoleOutput**](writeconsoleoutput.md) copia un bloque rectangular de datos de atributos de caracteres y colores de un búfer de origen en un búfer de pantalla de la consola. Para obtener más información sobre cómo leer o escribir en bloques rectangulares de celdas de búfer de pantalla, vea [métodos de entrada y salida](input-and-output-methods.md).

En el ejemplo siguiente se usa la función [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) para crear un nuevo búfer de pantalla. Una vez que la función [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) hace que este sea el búfer de pantalla activo, se copia un bloque de caracteres y atributos de color de las dos primeras filas del búfer de pantalla stdout en un búfer temporal. Los datos se copian desde el búfer temporal en el nuevo búfer de pantalla activo. Cuando la aplicación termina de usar el nuevo búfer de pantalla, llama a **SetConsoleActiveScreenBuffer** para restaurar el búfer de pantalla stdout original.

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

 

 




