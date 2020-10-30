---
title: Creación de una consola
description: El sistema crea una nueva consola cuando inicia un proceso de la consola, un proceso en modo de carácter cuyo punto de entrada es la función principal.
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
ms.openlocfilehash: 78a77044452fe2287a7cea0bfe5a6542eceef337
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038243"
---
# <a name="creation-of-a-console"></a>Creación de una consola

El sistema crea una nueva consola cuando inicia un proceso de la *consola* , un proceso en modo de carácter cuyo punto de entrada es la función **principal** . Por ejemplo, el sistema crea una nueva consola cuando inicia el procesador de comandos `cmd.exe` . Cuando el procesador de comandos inicia un nuevo proceso de consola, el usuario puede especificar si el sistema crea una nueva consola para el nuevo proceso o si hereda la consola del procesador de comandos.

Un proceso puede crear una consola de mediante uno de los métodos siguientes:

- Una interfaz gráfica de usuario (GUI) o un proceso de consola puede usar la función [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) con **crear \_ nueva \_ consola** para crear un proceso de consola con una nueva consola. (De forma predeterminada, un proceso de consola hereda la consola de su elemento primario y no hay ninguna garantía de que la entrada la reciba el proceso para el que se ha diseñado).
- Una GUI o un proceso de consola que no está asociado actualmente a una consola puede usar la función [**AllocConsole**](allocconsole.md) para crear una nueva consola. (Los procesos de la GUI no se adjuntan a una consola cuando se crean. Los procesos de la consola no se adjuntan a una consola si se crean mediante [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) con el **\_ proceso separado** .)

Normalmente, un proceso usa [**AllocConsole**](allocconsole.md) para crear una consola cuando se produce un error que requiere interacción con el usuario. Por ejemplo, un proceso de GUI puede crear una consola cuando se produce un error que impide que use su interfaz gráfica normal, o un proceso de consola que no interactúe normalmente con el usuario puede crear una consola para mostrar un error.

Un proceso también puede crear una consola mediante la especificación de la marca **crear \_ nueva \_ consola** en una llamada a [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425). Este método crea una nueva consola que es accesible para el proceso secundario, pero no para el proceso primario. Las consolas independientes permiten a los procesos primarios y secundarios interactuar con el usuario sin conflictos. Si esta marca no se especifica cuando se crea un proceso de consola, ambos procesos se adjuntan a la misma consola y no hay ninguna garantía de que el proceso correcto recibirá la entrada prevista. Las aplicaciones pueden evitar confusiones creando procesos secundarios que no heredan los identificadores del búfer de entrada, o habilitando un solo proceso secundario a la vez para heredar un identificador de búfer de entrada, a la vez que se impide que el proceso primario Lea la entrada de la consola hasta que el elemento secundario haya finalizado.

La creación de una nueva consola da como resultado una nueva ventana de consola, así como búferes de pantalla de e/s independientes. El proceso asociado a la nueva consola de usa la función [**GetStdHandle**](getstdhandle.md) para obtener los identificadores de los búferes de entrada y de pantalla de la nueva consola. Estos identificadores permiten al proceso tener acceso a la consola.

Cuando un proceso usa [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425), puede especificar una estructura [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) , cuyos miembros controlan las características de la primera consola nueva (si existe) creada para el proceso secundario. La estructura **STARTUPINFO** especificada en la llamada a **CreateProcess** afecta a una consola creada si se especifica la marca **crear \_ nueva \_ consola** . También afecta a una consola creada si el proceso secundario usa posteriormente [**AllocConsole**](allocconsole.md). Se pueden especificar las siguientes características de la consola:

- Tamaño de la nueva ventana de la consola, en celdas de caracteres
- Ubicación de la nueva ventana de la consola, en coordenadas de píxeles de pantalla
- Tamaño del búfer de pantalla de la nueva consola, en celdas de caracteres
- Atributos de color de fondo y de texto del búfer de pantalla de la nueva consola
- Nombre para mostrar de la barra de título de la ventana de la nueva consola

El sistema utiliza los valores predeterminados si no se especifican los valores de [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) . Un proceso secundario puede usar la función [**GetStartupInfo**](https://msdn.microsoft.com/library/windows/desktop/ms683230) para determinar los valores de su estructura **STARTUPINFO** .

Un proceso no puede cambiar la ubicación de la ventana de la consola en la pantalla, pero las siguientes funciones de la consola están disponibles para establecer o recuperar las demás propiedades especificadas en la estructura [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) .

| Función | Descripción |
|-|-|
| [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) | Recupera el tamaño de la ventana, el tamaño del búfer de pantalla y los atributos de color. |
| [**SetConsoleWindowInfo**](setconsolewindowinfo.md)  | Cambia el tamaño de la ventana de la consola.  |
| [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) | Cambia el tamaño del búfer de pantalla de la consola. |
| [**SetConsoleTextAttribute**](setconsoletextattribute.md) | Establece los atributos de color.  |
| [**SetConsoleTitle**](setconsoletitle.md)  | Establece el título de la ventana de la consola. |
| [**GetConsoleTitle**](getconsoletitle.md)  | Recupera el título de la ventana de la consola.  |

Un proceso puede usar la función [**FreeConsole**](freeconsole.md) para desasociarse de una consola heredada o de una consola creada por [**AllocConsole**](allocconsole.md).

Un proceso puede usar la función [**AttachConsole**](attachconsole.md) para adjuntarse a otra sesión de consola existente después de usar [**FreeConsole**](freeconsole.md) para desasociar de su propia sesión (o si, de lo contrario, no hay ninguna sesión asociada).
