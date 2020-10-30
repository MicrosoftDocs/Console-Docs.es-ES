---
ms.openlocfilehash: eaaaa3487e8f2aa95915f6f10724bf4c26784622
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038881"
---
Una consola de está formada por un búfer de entrada y uno o más búferes de pantalla. El modo de un búfer de consola determina cómo se comporta la consola durante las operaciones de entrada o salida (e/s). Un conjunto de constantes de marca se usa con los identificadores de entrada y otro conjunto se utiliza con los identificadores de búfer de pantalla (salida). La configuración de los modos de salida de un búfer de pantalla no afecta a los modos de salida de otros búferes de pantalla.

Los modos de entrada **habilitar \_ \_ entrada de línea** y **habilitar \_ eco \_** solo afectan a los procesos que usan [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](../readconsole.md) para leer desde el búfer de entrada de la consola. De forma similar, el modo **habilitar \_ \_ entrada procesada** afecta principalmente a los usuarios **readfile** y **ReadConsole** , salvo que también determina si la entrada Ctrl + C se indica en el búfer de entrada (que será leída por la función [**ReadConsoleInput**](../readconsoleinput.md) ) o se pasa a una función definida por la aplicación.

Los **modos \_ habilitar \_ entrada de ventana** y **habilitar \_ \_ entrada del mouse** determinan si las interacciones del usuario que implican el cambio de tamaño de las ventanas y las acciones del mouse se registran en el búfer de entrada o se descartan. Estos eventos pueden ser leídos por [**ReadConsoleInput**](../readconsoleinput.md), pero siempre se filtran por [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**ReadConsole**](../readconsole.md).

Los modos de salida **habilitar \_ \_ salida procesada** y **habilitar \_ encapsulado \_ en \_ \_ EOL** solo afectan a los procesos que usan [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](../readconsole.md) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](../writeconsole.md).
