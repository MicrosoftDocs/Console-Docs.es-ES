---
ms.openlocfilehash: eaaaa3487e8f2aa95915f6f10724bf4c26784622
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "93038881"
---
Una consola de está formada por un búfer de entrada y uno o más búferes de pantalla. El modo de un búfer de consola determina cómo se comporta esta durante las operaciones de entrada o salida (E/S). Un conjunto de constantes de marca se usa con los identificadores de entrada, y el otro conjunto se usa con los identificadores del búfer de pantalla (salida). Tenga en cuenta que la configuración de los modos de salida de un búfer de pantalla no afecta a los modos de salida de otros búferes de pantalla.

Los modos **ENABLE\_LINE\_INPUT** y **ENABLE\_ECHO\_INPUT** solo afectan a los procesos que usan [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](../readconsole.md) para leer contenido desde el búfer de entrada de la consola. De forma similar, el modo **ENABLE\_PROCESSED\_INPUT** afecta principalmente a los usuarios de **ReadFile** y **ReadConsole**; sin embargo, también determina si la entrada de CTRL + C se indica en el búfer de entrada (para que pueda leerla [**ReadConsoleInput**](../readconsoleinput.md)) o si se pasa a una función que haya definido la aplicación.

Los modos **ENABLE\_WINDOW\_INPUT** y **ENABLE\_MOUSE\_INPUT** determinan si las interacciones del usuario que implican el cambio de tamaño de las ventanas y las acciones del mouse se registran en el búfer de entrada o se descartan. Estos eventos puede leerlos [**ReadConsoleInput**](../readconsoleinput.md), pero siempre se filtran mediante [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**ReadConsole**](../readconsole.md).

Los modos **ENABLE\_PROCESSED\_OUTPUT** y **ENABLE\_WRAP\_AT\_EOL\_OUTPUT** solo afectan a los procesos que usan [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](../readconsole.md) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](../writeconsole.md).
