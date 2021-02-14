---
title: Funciones de entrada y salida de la consola de High-Level
description: Las funciones ReadFile y WriteFile, o las funciones ReadConsole y WriteConsole, permiten que una aplicación Lea la entrada de la consola y escriba la salida de la consola como un flujo de caracteres.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_high\_level\_console\_input\_and\_output\_functions'
- base.high\_level\_console\_input\_and\_output\_functions
- consoles.high\_level\_console\_input\_and\_output\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 086b1bec-85f8-4e31-848d-7cb2d2703a3d
ms.openlocfilehash: 4da8845e4e35170980d306930c182ff6e5fb6cbf
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358305"
---
# <a name="high-level-console-input-and-output-functions"></a>Funciones de entrada y salida de la consola de High-Level

Las funciones [**readfile**](/windows/win32/api/fileapi/nf-fileapi-readfile) y [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) , o las funciones [**ReadConsole**](readconsole.md) y [**WriteConsole**](writeconsole.md) , permiten que una aplicación Lea la entrada de la consola y escriba la salida de la consola como un flujo de caracteres. **ReadConsole** y **WriteConsole** se comportan exactamente igual que **readfile** y **WriteFile** , salvo que se pueden usar como funciones de caracteres anchos (en las que los argumentos de texto deben usar Unicode) o como funciones ANSI (en las que los argumentos de texto deben usar caracteres del juego de caracteres de Windows). Las aplicaciones que necesitan mantener un único conjunto de orígenes para admitir Unicode o el juego de caracteres ANSI deben usar **ReadConsole** y **WriteConsole**.

[**ReadConsole**](readconsole.md) y [**WriteConsole**](writeconsole.md) solo se pueden usar con los identificadores de consola; [**Readfile**](/windows/win32/api/fileapi/nf-fileapi-readfile) y [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) se pueden usar con otros identificadores (como archivos o canalizaciones). **ReadConsole** y **WriteConsole** generan un error si se usan con un identificador estándar que se ha redirigido y ya no es un controlador de consola.

Para obtener la entrada mediante teclado, un proceso puede usar [**readfile**](/windows/win32/api/fileapi/nf-fileapi-readfile) o [**ReadConsole**](readconsole.md) con un identificador para el búfer de entrada de la consola, o puede usar **readfile** para leer la entrada de un archivo o una canalización si se ha `STDIN` redirigido. Estas funciones solo devuelven los eventos de teclado que se pueden traducir en caracteres ANSI o Unicode. La entrada que se puede devolver incluye combinaciones de teclas de control. Las funciones no devuelven eventos de teclado que impliquen las teclas de función o las teclas de dirección. Los eventos de entrada generados por el mouse, la ventana, el foco o la entrada de menú se descartan.

Si está habilitado el modo de entrada de línea (el modo predeterminado), [**readfile**](/windows/win32/api/fileapi/nf-fileapi-readfile) y [**ReadConsole**](readconsole.md) no vuelven a la aplicación que realiza la llamada hasta que se presiona la tecla entrar. Si el modo de entrada de línea está deshabilitado, las funciones no devuelven hasta que al menos un carácter esté disponible. En cualquier modo, se leen todos los caracteres disponibles hasta que no haya más claves disponibles o se haya leído el número especificado de caracteres. Los caracteres no leídos se almacenan en búfer hasta la siguiente operación de lectura. Las funciones informan del número total de caracteres leídos realmente. Si el modo de entrada de eco está habilitado, los caracteres leídos por estas funciones se escriben en el búfer de pantalla activo en la posición actual del cursor.

Un proceso puede usar [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) o **WriteConsole** para escribir en un búfer de pantalla activo o inactivo, o puede usar **WriteFile** para escribir en un archivo o una canalización si se ha redirigido stdout. El modo de salida procesado y el ajuste en el modo de salida EOL controlan la forma en que los caracteres se escriben o se repiten en un búfer de pantalla.

Los caracteres escritos por [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) o [**WriteConsole**](writeconsole.md), o que se han devuelto por [**readfile**](/windows/win32/api/fileapi/nf-fileapi-readfile) o [**ReadConsole**](readconsole.md), se insertan en un búfer de pantalla en la posición actual del cursor. A medida que se escribe cada carácter, la posición del cursor avanza hasta la siguiente celda de carácter; sin embargo, el comportamiento al final de una fila depende del ajuste del búfer de pantalla de la consola en el modo de salida EOL.

Se pueden encontrar más detalles sobre la posición del cursor a través de las **[secuencias de terminales virtuales](console-virtual-terminal-sequences.md)**, específicamente en la categoría estado de la **[consulta](console-virtual-terminal-sequences.md#query-state)** para buscar la posición actual y la categoría posición del **[cursor](console-virtual-terminal-sequences.md#cursor-positioning)** para establecer la posición actual. Como alternativa, una aplicación puede usar la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) para determinar la posición actual del cursor y la función [**SetConsoleCursorPosition**](setconsolecursorposition.md) para establecer la posición del cursor. Sin embargo, se prefiere el mecanismo de **secuencias de terminal virtuales** para todo el desarrollo nuevo y en curso. Puede encontrar más detalles sobre la estrategia que se encuentra detrás de esta decisión en la documentación sobre las **[funciones clásicas frente al terminal virtual](classic-vs-vt.md)** y el **[plan del ecosistema](ecosystem-roadmap.md)** .

Para obtener un ejemplo que usa las funciones de e/s de la consola de alto nivel, consulte [uso de las funciones de entrada y salida de High-Level](using-the-high-level-input-and-output-functions.md).