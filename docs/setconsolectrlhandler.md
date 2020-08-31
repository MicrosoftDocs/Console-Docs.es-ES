---
title: SetConsoleCtrlHandler función)
description: Agrega o quita una función HandlerRoutine definida por la aplicación de la lista de funciones de controlador para el proceso que realiza la llamada.
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
ms.openlocfilehash: cd7b491c1a395483d4aef052d4147d3edf2514e5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060952"
---
# <a name="setconsolectrlhandler-function"></a>SetConsoleCtrlHandler función)


Agrega o quita una función [**HandlerRoutine**](handlerroutine.md) definida por la aplicación de la lista de funciones de controlador para el proceso que realiza la llamada.

Si no se especifica ninguna función de controlador, la función establece un atributo heredable que determina si el proceso de llamada omite las señales CTRL + C.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

<a name="parameters"></a>Parámetros
----------

*HandlerRoutine* \[ en, opcional\]  
Puntero a la función [**HandlerRoutine**](handlerroutine.md) definida por la aplicación que se va a agregar o quitar. Este parámetro puede ser **null**.

*Agregar* \[ de\]  
Si este parámetro es **true**, se agrega el controlador; Si es **false**, se quita el controlador.

Si el parámetro *HandlerRoutine* es **null**, un valor **true** hace que el proceso de llamada ignore la entrada Ctrl + c y un valor **false** restaura el procesamiento normal de la entrada Ctrl + c. Los procesos secundarios heredan este atributo de omitir o procesar CTRL + C.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

Esta función proporciona una notificación similar a la aplicación de consola y los servicios que [**WM \_ QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) proporciona para aplicaciones gráficas con un bombeo de mensajes. También puede usar esta función desde una aplicación gráfica, pero no hay ninguna garantía de que llegue antes de la notificación de **WM \_ QUERYENDSESSION**.

Cada proceso de consola tiene su propia lista de funciones [**HandlerRoutine**](handlerroutine.md) definidas por la aplicación que controlan las señales Ctrl + C y Ctrl + Inter. Las funciones de controlador también controlan las señales generadas por el sistema cuando el usuario cierra la consola, cierra la sesión o apaga el sistema. Inicialmente, la lista de controladores para cada proceso contiene solo una función de controlador predeterminada que llama a la función [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) . Un proceso de consola agrega o quita funciones de controlador adicionales mediante una llamada a la función **SetConsoleCtrlHandler** , que no afecta a la lista de funciones de controlador para otros procesos. Cuando un proceso de consola recibe cualquiera de las señales de control, se llama a sus funciones de controlador en la última base de registro, que se llama primero, hasta que uno de los controladores devuelve TRUE. Si ninguno de los controladores devuelve TRUE, se llama al controlador predeterminado.

En los procesos de la consola, las combinaciones de teclas CTRL + C y CTRL + INTER se tratan normalmente como señales (**Ctrl \_ C \_ Event** y **Ctrl \_ break \_ Event**). Cuando una ventana de consola con el foco de teclado recibe CTRL + C o CTRL + INTER, la señal normalmente se pasa a todos los procesos que comparten esa consola.

CTRL + INTER siempre se trata como una señal, pero el comportamiento típico de CTRL + C se puede cambiar de tres maneras que impiden que se llame a las funciones del controlador:

- La función [**SetConsoleMode**](setconsolemode.md) puede deshabilitar el modo de ** \_ \_ entrada procesada** para el búfer de entrada de una consola, por lo que Ctrl + C se indica como entrada de teclado en lugar de como señal.
- La llamada a **SetConsoleCtrlHandler** con los argumentos **null** y **true** hace que el proceso de llamada ignore las señales Ctrl + C. Este atributo lo heredan los procesos secundarios, pero se puede habilitar o deshabilitar en cualquier proceso sin que ello afecte a los procesos existentes.
- Si se está depurando un proceso de consola y no se han deshabilitado las señales de CTRL + C, el sistema genera una excepción del **control dbg de \_ \_ C** . Esta excepción solo se produce para los beneficios del depurador, y una aplicación nunca debe utilizar un controlador de excepciones para tratar con ella. Si el depurador controla la excepción, una aplicación no observará el CTRL + C, con una excepción: se terminarán las esperas de alerta. Si el depurador pasa la excepción en un control no controlado, se pasa CTRL + C al proceso de la consola y se trata como una señal, como se explicó anteriormente.

Un proceso de consola puede usar la función [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) para enviar una señal CTRL + C o Ctrl + Inter a un grupo de procesos de la consola.

El sistema genera señales de evento **Ctrl \_ Close \_ **, evento **Ctrl \_ Logoff \_ **y **Ctrl \_ Shutdown \_ ** cuando el usuario cierra la consola, cierra la sesión o apaga el sistema para que el proceso tenga la oportunidad de limpiar antes de la terminación. Es posible que las funciones de consola o cualquier función en tiempo de ejecución de C que llame a funciones de consola no funcionen de forma confiable durante el procesamiento de cualquiera de las tres señales mencionadas anteriormente. La razón es que es posible que se haya llamado a algunas o todas las rutinas de limpieza de la consola internas antes de ejecutar el controlador de la señal de proceso.

**Windows 7, Windows 8, Windows 8.1 y Windows 10:**

Si una aplicación de consola carga el gdi32.dll o user32.dll biblioteca, no se llama a la función [**HandlerRoutine**](handlerroutine.md) que se especifica cuando se llama a **SetConsoleCtrlHandler** para los eventos de ** \_ \_ evento** **Ctrl \_ Logoff \_ ** y Ctrl shutdown. El sistema operativo reconoce los procesos que cargan gdi32.dll o user32.dll como aplicaciones Windows en lugar de aplicaciones de consola. Este comportamiento también se produce en las aplicaciones de consola que no llaman a funciones en gdi32.dll o user32.dll directamente, pero llaman a funciones como [funciones de Shell](https://msdn.microsoft.com/library/windows/desktop/bb776426) que, a su vez, llaman a funciones en gdi32.dll o user32.dll.

Para recibir eventos cuando un usuario cierra la sesión o el dispositivo se apaga en estas circunstancias, cree una ventana oculta en la aplicación de consola y, a continuación, controle los mensajes de la ventana de [**WM \_ QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) y [**WM \_ ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) que recibe la ventana oculta. Puede crear una ventana oculta llamando al método [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) con el parámetro *dwExStyle* establecido en 0.

<a name="examples"></a>Ejemplos
--------

Para obtener un ejemplo, vea [registrar una función de controlador de control](registering-a-control-handler-function.md).

<a name="requirements"></a>Requisitos
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Cliente mínimo compatible</p></td>
<td><p>Windows 2000 Professional [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="even">
<td><p>Servidor mínimo compatible</p></td>
<td><p>Windows 2000 Server [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="odd">
<td><p>Encabezado</p></td>
<td>ConsoleApi. h (a través de winCon. h, include Windows. h)</td>
</tr>
<tr class="even">
<td><p>Biblioteca</p></td>
<td>Kernel32. lib</td>
</tr>
<tr class="odd">
<td><p>Archivo DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vea también


[Controladores de control de consola](console-control-handlers.md)

[Funciones de la consola](console-functions.md)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetConsoleMode**](getconsolemode.md)

[**HandlerRoutine**](handlerroutine.md)

[**SetConsoleMode**](setconsolemode.md)

 

 




