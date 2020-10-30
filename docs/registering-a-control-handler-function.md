---
title: Registro de una función de identificador de control
description: Este es un ejemplo de la función SetConsoleCtrlHandler que se usa para instalar un controlador de control.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_registering\_a\_control\_handler\_function'
- base.registering\_a\_control\_handler\_function
- consoles.registering\_a\_control\_handler\_function
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f1c72277-f06c-4147-a74c-6aaf6feb730e
ms.openlocfilehash: 4142f4f0871bd11a56085324195702ab47301227
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039453"
---
# <a name="registering-a-control-handler-function"></a>Registro de una función de identificador de control

Este es un ejemplo de la función [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) que se usa para instalar un controlador de control.

Cuando se recibe una señal CTRL + C, el controlador de control devuelve **true** , lo que indica que ha controlado la señal. Esto impide que se llame a otros controladores de control.

Cuando se recibe una señal de **\_ \_ evento Ctrl Close** , el controlador de control devuelve **true** y finaliza el proceso.

Cuando se recibe un evento **Ctrl \_ break \_** , un evento **Ctrl \_ Logoff \_** o un evento **Ctrl \_ \_ Shutdown** , el controlador de control devuelve **false** . Esto hace que la señal se pase a la siguiente función de controlador de control. Si no se han registrado otros controladores de control o ninguno de los controladores registrados devuelve **true** , se usará el controlador predeterminado, lo que provocará que se termine el proceso.

```C
// CtrlHandler.cpp : This file contains the 'main' function. Program execution begins and ends there.
//

#include "pch.h"

#include <windows.h>
#include <stdio.h>

BOOL WINAPI CtrlHandler(DWORD fdwCtrlType)
{
    switch (fdwCtrlType)
    {
        // Handle the CTRL-C signal.
    case CTRL_C_EVENT:
        printf("Ctrl-C event\n\n");
        Beep(750, 300);
        return TRUE;

        // CTRL-CLOSE: confirm that the user wants to exit.
    case CTRL_CLOSE_EVENT:
        Beep(600, 200);
        printf("Ctrl-Close event\n\n");
        return TRUE;

        // Pass other signals to the next handler.
    case CTRL_BREAK_EVENT:
        Beep(900, 200);
        printf("Ctrl-Break event\n\n");
        return FALSE;

    case CTRL_LOGOFF_EVENT:
        Beep(1000, 200);
        printf("Ctrl-Logoff event\n\n");
        return FALSE;

    case CTRL_SHUTDOWN_EVENT:
        Beep(750, 500);
        printf("Ctrl-Shutdown event\n\n");
        return FALSE;

    default:
        return FALSE;
    }
}

int main(void)
{
    if (SetConsoleCtrlHandler(CtrlHandler, TRUE))
    {
        printf("\nThe Control Handler is installed.\n");
        printf("\n -- Now try pressing Ctrl+C or Ctrl+Break, or");
        printf("\n    try logging off or closing the console...\n");
        printf("\n(...waiting in a loop for events...)\n\n");

        while (1) {}
    }
    else
    {
        printf("\nERROR: Could not set control handler");
        return 1;
    }
    return 0;
}
```
