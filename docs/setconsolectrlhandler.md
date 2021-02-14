---
title: Función SetConsoleCtrlHandler
description: Agrega o quita una función HandlerRoutine definida por la aplicación de la lista de funciones de controlador para el proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/SetConsoleCtrlHandler
- wincon/SetConsoleCtrlHandler
- SetConsoleCtrlHandler
MS-HAID:
- '\_win32\_setconsolectrlhandler'
- base.setconsolectrlhandler
- consoles.setconsolectrlhandler
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6fc64265-1403-45ea-925c-c5eb31d56734
topic_type:
- apiref
api_name:
- SetConsoleCtrlHandler
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 03e7166f84be2f760a4ffea385225390bdb3ffa1
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357715"
---
# <a name="setconsolectrlhandler-function"></a>Función SetConsoleCtrlHandler

Agrega o quita una función [**HandlerRoutine**](handlerroutine.md) definida por la aplicación de la lista de funciones de controlador para el proceso de llamada.

Si no se especifica ninguna función de controlador, la función establece un atributo heredable que determina si el proceso de llamada ignora las señales de <kbd>CTRL</kbd>+<kbd>C</kbd>.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

## <a name="parameters"></a>Parámetros

*HandlerRoutine* \[in, opcional\]  
Puntero a la función [**HandlerRoutine**](handlerroutine.md) definida por la aplicación que se va a agregar o quitar. Este parámetro puede ser **NULL**.

*Add* \[in\]  
Si este parámetro es **TRUE**, se agrega el controlador; si es **FALSE**, se quita el controlador.

Si el parámetro *HandlerRoutine* es **NULL**, un valor **TRUE** provoca que el proceso de llamada ignore la entrada <kbd>CTRL</kbd>+<kbd>C</kbd>. Un valor **FALSE** restaura el procesamiento normal de la entrada <kbd>CTRL</kbd>+<kbd>C</kbd>. Los procesos secundarios heredan este atributo de ignorar o procesar <kbd>CTRL</kbd>+<kbd>C</kbd>.

## <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Comentarios

Esta función proporciona una notificación similar a la aplicación de consola y los servicios que [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) proporciona para aplicaciones gráficas con un bombeo de mensajes. También puede usar esta función desde una aplicación gráfica, pero no hay ninguna garantía de que llegue antes de la notificación de **WM\_QUERYENDSESSION**.

Cada proceso de consola tiene su propia lista de funciones [**HandlerRoutine**](handlerroutine.md) definidas por la aplicación que controlan las señales de <kbd>CTRL</kbd>+<kbd>C</kbd> y <kbd>CTRL</kbd>+<kbd>BREAK</kbd>. Las funciones de controlador también controlan las señales generadas por el sistema cuando el usuario cierra la consola, cierra sesión o apaga el sistema. Inicialmente, la lista de controladores para cada proceso solo contiene una función de controlador predeterminada que llama a la función [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess). Un proceso de consola agrega o quita funciones de controlador adicionales mediante una llamada a la función **SetConsoleCtrlHandler**, que no afecta a la lista de funciones de controlador para otros procesos. Cuando un proceso de consola recibe alguna de las señales de control, se llama a sus funciones de controlador en función del último registro y la primera llamada, hasta que uno de los controladores devuelve `TRUE`. Si ninguno de los controladores devuelve `TRUE`, se llama al controlador predeterminado.

En el caso de los procesos de consola, normalmente las combinaciones de teclas <kbd>CTRL</kbd>+<kbd>C</kbd> y <kbd>CTRL</kbd>+<kbd>BREAK</kbd> se tratan como señales (**CTRL\_C\_EVENT** y **CTRL\_BREAK\_EVENT**). Cuando una ventana de consola con el foco de teclado recibe <kbd>CTRL</kbd>+<kbd>C</kbd> o <kbd>CTRL</kbd>+<kbd>BREAK</kbd>, normalmente la señal se pasa a todos los procesos que comparten esa consola.

<kbd>CTRL</kbd>+<kbd>BREAK</kbd> se trata siempre como una señal, pero un comportamiento típico de <kbd>CTRL</kbd>+<kbd>C</kbd> se puede cambiar de tres maneras que impidan que se llame a las funciones del controlador:

- La función [**SetConsoleMode**](setconsolemode.md) puede deshabilitar el modo **ENABLE\_PROCESSED\_INPUT** para el búfer de entrada de una consola, por lo que <kbd>CTRL</kbd>+<kbd>C</kbd> se indica como entrada del teclado en lugar de como una señal.
- La llamada a **SetConsoleCtrlHandler** con los argumentos **NULL** y **TRUE** hace que el proceso de llamada ignore las señales de <kbd>CTRL</kbd>+<kbd>C</kbd>. Los procesos secundarios heredan este atributo, pero puede habilitarse o deshabilitarse en cualquier proceso sin que ello afecte a los procesos existentes.
- Si se está depurando un proceso de consola y no se han deshabilitado las señales de <kbd>CTRL</kbd>+<kbd>C</kbd>, el sistema genera una excepción **DBG\_CONTROL\_C**. Esta excepción solo se produce en beneficio del depurador y una aplicación nunca debe utilizar un controlador de excepciones para tratarla. Si el depurador controla la excepción, una aplicación no tendrá en cuenta <kbd>CTRL</kbd>+<kbd>C</kbd>, con una excepción: se terminarán las esperas que generan alertas. Si el depurador pasa la excepción como no controlada, <kbd>CTRL</kbd>+<kbd>C</kbd> se pasa al proceso de consola y se trata como una señal, como se explicó anteriormente.

Un proceso de consola puede usar la función [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) para enviar una señal de <kbd>CTRL</kbd>+<kbd>C</kbd> o <kbd>CTRL</kbd>+<kbd>BREAK</kbd> a un grupo de procesos de consola.

El sistema genera señales de **CTRL\_CLOSE\_EVENT**, **CTRL\_LOGOFF\_EVENT** y **CTRL\_SHUTDOWN\_EVENT** cuando el usuario cierra la consola, cierra sesión o apaga el sistema para que el proceso tenga una oportunidad de limpiarse antes de que finalice. Es posible que las funciones de consola o cualquier función en tiempo de ejecución de C que llame a funciones de consola no funcionen de forma confiable durante el procesamiento de cualquiera de las tres señales mencionadas anteriormente. El motivo es que es posible que se haya llamado a algunas o todas las rutinas de limpieza internas de la consola antes de ejecutar el controlador de la señal de proceso.

**Windows 7, Windows 8, Windows 8.1 y Windows 10:**

Si una aplicación de consola carga la biblioteca gdi32.dll o user32.dll, no se llama a la función [**HandlerRoutine**](handlerroutine.md) que se especifica cuando se llama a **SetConsoleCtrlHandler** para los eventos **CTRL\_LOGOFF\_EVENT** y **CTRL\_SHUTDOWN\_EVENT**. El sistema operativo reconoce los procesos que cargan gdi32.dll o user32.dll como aplicaciones Windows en lugar de aplicaciones de consola. Este comportamiento también se produce en las aplicaciones de consola que no llaman directamente a las funciones de gdi32.dll o user32.dll, sino que llaman a funciones como [funciones de Shell](/previous-versions/windows/desktop/legacy/bb776426(v=vs.85)) que, a su vez, llaman a funciones de gdi32.dll o user32.dll.

Para recibir eventos cuando un usuario cierra sesión o el dispositivo se apaga en estas circunstancias, cree una ventana oculta en la aplicación de consola y, a continuación, controle los mensajes de la ventana [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) y [**WM\_ENDSESSION**](/windows/win32/shutdown/wm-endsession) que recibe la ventana oculta. Para crear una ventana oculta, llame al método [**CreateWindowEx**](/windows/win32/api/winuser/nf-winuser-createwindowexa) con el parámetro *dwExStyle* establecido en 0.

## <a name="examples"></a>Ejemplos

Por ejemplo, consulte [Registro de una función de identificador de control](registering-a-control-handler-function.md).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Professional |
| Servidor mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Server |
| Encabezado | ConsoleApi.h (a través de WinCon.h, incluido Windows.h) |
| Biblioteca | Kernel32.lib |
| Archivo DLL | Kernel32.dll |
| Nombres Unicode y ANSI | |

## <a name="see-also"></a>Vea también

[Identificadores de control de la consola](console-control-handlers.md)

[Funciones de la consola](console-functions.md)

[**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetConsoleMode**](getconsolemode.md)

[**HandlerRoutine**](handlerroutine.md)

[**SetConsoleMode**](setconsolemode.md)