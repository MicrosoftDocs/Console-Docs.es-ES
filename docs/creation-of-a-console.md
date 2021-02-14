---
title: Creación de una consola
description: El sistema crea una nueva consola cuando inicia un proceso de consola, un proceso en modo de carácter cuyo punto de entrada es la función principal.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_creation\_of\_a\_console'
- base.creation\_of\_a\_console
- consoles.creation\_of\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ec2559-cade-447e-8594-5b824d3d3e81
ms.localizationpriority: high
ms.openlocfilehash: bf7993874c4f7c7031dbbcc9ce53a0610157eb75
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357925"
---
# <a name="creation-of-a-console"></a>Creación de una consola

El sistema crea una nueva consola cuando inicia un *proceso de consola*, un proceso en modo de carácter cuyo punto de entrada es la función **principal**. Por ejemplo, el sistema crea una nueva consola cuando inicia el procesador de comandos `cmd.exe`. Cuando el procesador de comandos inicia un nuevo proceso de consola, el usuario puede especificar si el sistema crea una nueva consola para el nuevo proceso o si hereda la consola del procesador de comandos.

Un proceso puede crear una consola mediante uno de los siguientes métodos:

- Una interfaz gráfica de usuario (GUI) o un proceso de consola puede usar la función [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) con **CREATE\_NEW\_CONSOLE** para crear un proceso de consola con una nueva consola. (De manera predeterminada, un proceso de consola hereda la consola de su elemento primario y no hay ninguna garantía de que el proceso para el que se ha diseñado reciba la entrada).
- Un proceso de consola o de GUI que no está asociado actualmente a una consola puede usar la función [**AllocConsole**](allocconsole.md) para crear una nueva consola. (Los procesos de GUI no se asocian a una consola cuando se crean. Los procesos de consola no se asocian a una consola de si se crean mediante [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) con **DETACHED\_PROCESS**).

Normalmente, un proceso usa [**AllocConsole**](allocconsole.md) para crear una consola cuando se produce un error que requiere interacción con el usuario. Por ejemplo, un proceso de GUI puede crear una consola cuando se produce un error que impide que use su interfaz gráfica normal, o un proceso de consola que no interactúa normalmente con el usuario puede crear una consola para mostrar un error.

Un proceso también puede crear una consola mediante la especificación de la marca **CREATE\_NEW\_CONSOLE** en una llamada a [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa). Este método crea una nueva consola que es accesible para el proceso secundario, pero no para el primario. Las consolas independientes permiten que los procesos primarios y secundarios interactúen con el usuario sin conflictos. Si esta marca no se especifica cuando se crea un proceso de consola, ambos procesos se asocian a la misma consola y no hay ninguna garantía de que el proceso correcto reciba la entrada prevista. Las aplicaciones pueden evitar confusiones mediante la creación de procesos secundarios que no heredan los identificadores del búfer de entrada o mediante la habilitación de un solo proceso secundario cada vez para heredar un identificador del búfer de entrada, a la vez que se impide que el proceso primario lea la entrada de la consola hasta que el secundario haya finalizado.

La creación de una nueva consola da como resultado una nueva ventana de consola, así como búferes de pantalla de E/S independientes. El proceso asociado a la nueva consola usa la función [**GetStdHandle**](getstdhandle.md) para obtener los identificadores de los búferes de entrada y de pantalla de la nueva consola. Estos identificadores permiten que el proceso tenga acceso a la consola.

Cuando un proceso utiliza [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa), puede especificar una estructura [**STARTUPINFO**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa), cuyos miembros controlan las características de la primera consola nueva (si existe) creada para el proceso secundario. La estructura **STARTUPINFO** especificada en la llamada a **CreateProcess** afecta a una consola creada si se especifica la marca **CREATE\_NEW\_CONSOLE**. También afecta a una consola creada si el proceso secundario usa posteriormente [**AllocConsole**](allocconsole.md). Se pueden especificar las siguientes características de la consola:

- Tamaño de la ventana de la nueva consola, en celdas de caracteres.
- Ubicación de la ventana de la nueva consola, en coordenadas de píxeles de pantalla.
- Tamaño del búfer de pantalla de la nueva consola, en celdas de caracteres.
- Atributos de color de fondo y de texto del búfer de pantalla de la nueva consola.
- Nombre para mostrar de la barra de título de la ventana de la nueva consola.

El sistema utiliza los valores predeterminados si no se especifican los valores de [**STARTUPINFO**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa). Un proceso secundario puede usar la función [**GetStartupInfo**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getstartupinfow) para determinar los valores de su estructura **STARTUPINFO**.

Un proceso no puede cambiar la ubicación de la ventana de consola en la pantalla, pero las siguientes funciones de la consola están disponibles para establecer o recuperar las demás propiedades especificadas en la estructura [**STARTUPINFO**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).

| Función | Descripción |
|-|-|
| [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) | Recupera el tamaño de la ventana, el tamaño de búfer de pantalla y los atributos de color. |
| [**SetConsoleWindowInfo**](setconsolewindowinfo.md)  | Cambia el tamaño de la ventana de consola.  |
| [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) | Cambia el tamaño del búfer de tamaño de la consola. |
| [**SetConsoleTextAttribute**](setconsoletextattribute.md) | Establece los atributos de color.  |
| [**SetConsoleTitle**](setconsoletitle.md)  | Establece el título de la ventana de consola. |
| [**GetConsoleTitle**](getconsoletitle.md)  | Recupera el título de la ventana de consola.  |

Un proceso puede usar la función [**FreeConsole**](freeconsole.md) para desasociarse de una consola heredada o de una consola creada por [**AllocConsole**](allocconsole.md).

Un proceso puede usar la función [**AttachConsole**](attachconsole.md) para asociarse a otra sesión de consola existente después de usar [**FreeConsole**](freeconsole.md) para desasociarse de su propia sesión (o si, de lo contrario, no hay ninguna sesión asociada).