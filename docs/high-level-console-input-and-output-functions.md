---
title: Funciones de entrada y salida de la consola de alto nivel
description: Las funciones ReadFile y WriteFile, o las funciones ReadConsole y WriteConsole, permiten que una aplicación Lea la entrada de la consola y escriba la salida de la consola como un flujo de caracteres.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_high\_level\_console\_input\_and\_output\_functions'
- base.high\_level\_console\_input\_and\_output\_functions
- consoles.high\_level\_console\_input\_and\_output\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 086b1bec-85f8-4e31-848d-7cb2d2703a3d
ms.openlocfilehash: d6e13edf9350fcff812ad02b2d9116c3fe132154
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060625"
---
# <a name="high-level-console-input-and-output-functions"></a>Funciones de entrada y salida de la consola de alto nivel


Las funciones [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) , o las funciones [**ReadConsole**](readconsole.md) y [**WriteConsole**](writeconsole.md) , permiten que una aplicación Lea la entrada de la consola y escriba la salida de la consola como un flujo de caracteres. **ReadConsole** y **WriteConsole** se comportan exactamente igual que **readfile** y **WriteFile** , salvo que se pueden usar como funciones de caracteres anchos (en las que los argumentos de texto deben usar Unicode) o como funciones ANSI (en las que los argumentos de texto deben usar caracteres del juego de caracteres de Windows). Las aplicaciones que necesitan mantener un único conjunto de orígenes para admitir Unicode o el juego de caracteres ANSI deben usar **ReadConsole** y **WriteConsole**.

[**ReadConsole**](readconsole.md) y [**WriteConsole**](writeconsole.md) solo se pueden usar con los identificadores de consola; [**Readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) se pueden usar con otros identificadores (como archivos o canalizaciones). **ReadConsole** y **WriteConsole** generan un error si se usan con un identificador estándar que se ha redirigido y ya no es un controlador de consola.

Para obtener la entrada mediante teclado, un proceso puede usar [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) con un identificador para el búfer de entrada de la consola, o puede usar **readfile** para leer la entrada de un archivo o una canalización si se ha redirigido stdin. Estas funciones solo devuelven eventos de teclado que se pueden traducir en caracteres ANSI (o caracteres Unicode en el caso de **ReadConsole**). La entrada que se puede devolver incluye combinaciones de teclas de control. Las funciones no devuelven eventos de teclado que impliquen las teclas de función o las teclas de dirección. Los eventos de entrada generados por el mouse, la ventana, el foco o la entrada de menú se descartan.

Si está habilitado el modo de entrada de línea (el modo predeterminado), [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**ReadConsole**](readconsole.md) no vuelven a la aplicación que realiza la llamada hasta que se presiona la tecla entrar. Si el modo de entrada de línea está deshabilitado, las funciones no devuelven hasta que al menos un carácter esté disponible. En cualquier modo, se leen todos los caracteres disponibles hasta que no haya más claves disponibles o se haya leído el número especificado de caracteres. Los caracteres no leídos se almacenan en búfer hasta la siguiente operación de lectura. Las funciones informan del número total de caracteres leídos realmente. Si el modo de entrada de eco está habilitado, los caracteres leídos por estas funciones se escriben en el búfer de pantalla activo en la posición actual del cursor.

Un proceso puede usar [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o **WriteConsole** para escribir en un búfer de pantalla activo o inactivo, o puede usar **WriteFile** para escribir en un archivo o una canalización si se ha redirigido stdout. El modo de salida procesado y el ajuste en el modo de salida EOL controlan la forma en que los caracteres se escriben o se repiten en un búfer de pantalla.

Los caracteres escritos por [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md), o que se han devuelto por [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md), se insertan en un búfer de pantalla en la posición actual del cursor. A medida que se escribe cada carácter, la posición del cursor avanza hasta la siguiente celda de carácter; sin embargo, el comportamiento al final de una fila depende del ajuste del búfer de pantalla de la consola en el modo de salida EOL. Una aplicación puede usar la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) para determinar la posición actual del cursor y la función [**SetConsoleCursorPosition**](setconsolecursorposition.md) para establecer la posición del cursor.

Para obtener un ejemplo en el que se usan las funciones de e/s de la consola de alto nivel, consulte [uso de las funciones de entrada y salida de alto nivel](using-the-high-level-input-and-output-functions.md).

 

 




