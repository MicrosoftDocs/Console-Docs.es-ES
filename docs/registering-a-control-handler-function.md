---
title: Registrar una función de controlador de control
description: Este es un ejemplo de la función SetConsoleCtrlHandler que se usa para instalar un controlador de control.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_registering\_a\_control\_handler\_function'
- base.registering\_a\_control\_handler\_function
- consoles.registering\_a\_control\_handler\_function
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f1c72277-f06c-4147-a74c-6aaf6feb730e
ms.openlocfilehash: cda72574b13c8c8fa1644e78310c66598c7b9dcf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060977"
---
# <a name="registering-a-control-handler-function"></a><span data-ttu-id="b9bfc-104">Registrar una función de controlador de control</span><span class="sxs-lookup"><span data-stu-id="b9bfc-104">Registering a Control Handler Function</span></span>


<span data-ttu-id="b9bfc-105">Este es un ejemplo de la función [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) que se usa para instalar un controlador de control.</span><span class="sxs-lookup"><span data-stu-id="b9bfc-105">This is an example of the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function that is used to install a control handler.</span></span>

<span data-ttu-id="b9bfc-106">Cuando se recibe una señal CTRL + C, el controlador de control devuelve **true**, lo que indica que ha controlado la señal.</span><span class="sxs-lookup"><span data-stu-id="b9bfc-106">When a CTRL+C signal is received, the control handler returns **TRUE**, indicating that it has handled the signal.</span></span> <span data-ttu-id="b9bfc-107">Esto impide que se llame a otros controladores de control.</span><span class="sxs-lookup"><span data-stu-id="b9bfc-107">Doing this prevents other control handlers from being called.</span></span>

<span data-ttu-id="b9bfc-108">Cuando se recibe una señal de \*\* \_ \_ evento Ctrl Close\*\* , el controlador de control devuelve **true** y finaliza el proceso.</span><span class="sxs-lookup"><span data-stu-id="b9bfc-108">When a **CTRL\_CLOSE\_EVENT** signal is received, the control handler returns **TRUE** and the process terminates.</span></span>

<span data-ttu-id="b9bfc-109">Cuando se recibe un evento \*\*Ctrl \_ break \_ \*\*, un evento \*\*Ctrl \_ Logoff \_ \*\*o un evento **Ctrl \_ \_ Shutdown** , el controlador de control devuelve **false**.</span><span class="sxs-lookup"><span data-stu-id="b9bfc-109">When a **CTRL\_BREAK\_EVENT**, **CTRL\_LOGOFF\_EVENT**, or **CTRL\_SHUTDOWN\_EVENT** signal is received, the control handler returns **FALSE**.</span></span> <span data-ttu-id="b9bfc-110">Esto hace que la señal se pase a la siguiente función de controlador de control.</span><span class="sxs-lookup"><span data-stu-id="b9bfc-110">Doing this causes the signal to be passed to the next control handler function.</span></span> <span data-ttu-id="b9bfc-111">Si no se han registrado otros controladores de control o ninguno de los controladores registrados devuelve **true**, se usará el controlador predeterminado, lo que provocará que se termine el proceso.</span><span class="sxs-lookup"><span data-stu-id="b9bfc-111">If no other control handlers have been registered or none of the registered handlers returns **TRUE**, the default handler will be used, resulting in the process being terminated.</span></span>

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

 

 




