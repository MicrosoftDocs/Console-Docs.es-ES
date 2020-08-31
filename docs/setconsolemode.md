---
title: SetConsoleMode función)
description: Establece el modo de entrada del búfer de entrada de una consola o el modo de salida de un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/SetConsoleMode
- wincon/SetConsoleMode
- SetConsoleMode
MS-HAID:
- '\_win32\_setconsolemode'
- base.setconsolemode
- consoles.setconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 77508d58-8a7a-4c47-9ec5-dc61e5c4beac
topic_type:
- apiref
api_name:
- SetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a524a9f730d53efd331a70693aadfeddeaad4cc0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061088"
---
# <a name="setconsolemode-function"></a>SetConsoleMode función)


Establece el modo de entrada del búfer de entrada de una consola o el modo de salida de un búfer de pantalla de la consola.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

<a name="parameters"></a>Parámetros
----------

*hConsoleHandle* \[ de\]  
Identificador para el búfer de entrada de la consola o un búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de ** \_ lectura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*dwMode* \[ de\]  
Modo de entrada o de salida que se va a establecer. Si el parámetro *hConsoleHandle* es un identificador de entrada, el modo puede ser uno o varios de los valores siguientes. Cuando se crea una consola, todos los modos de entrada excepto **habilitar \_ \_ entrada de ventana** están habilitados de forma predeterminada.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Valor</th>
<th>Significado</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="ENABLE_ECHO_INPUT"></span><span id="enable_echo_input"></span>
<strong>ENABLE_ECHO_INPUT</strong> 0x0004</td>
<td><p>Los caracteres leídos por la función <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>readfile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> se escriben en el búfer de pantalla activo mientras se leen. Este modo solo se puede usar si el modo de <strong>ENABLE_LINE_INPUT</strong> también está habilitado.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_EXTENDED_FLAGS"></span><span id="enable_extended_flags"></span>
<strong>ENABLE_EXTENDED_FLAGS</strong> 0x0080</td>
<td><p>Necesario para habilitar o deshabilitar las marcas extendidas. Consulte <strong>ENABLE_INSERT_MODE</strong> y <strong>ENABLE_QUICK_EDIT_MODE</strong>.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_INSERT_MODE"></span><span id="enable_insert_mode"></span>
<strong>ENABLE_INSERT_MODE</strong> 0x0020</td>
<td><p>Cuando está habilitado, el texto especificado en una ventana de la consola se insertará en la ubicación actual del cursor y no se sobrescribirá todo el texto que sigue a esa ubicación. Cuando está deshabilitada, se sobrescribirá todo el texto siguiente.</p>
<p>Para habilitar este modo, use <code>ENABLE_INSERT_MODE | ENABLE_EXTENDED_FLAGS</code> . Para deshabilitar este modo, utilice <strong>ENABLE_EXTENDED_FLAGS</strong> sin esta marca.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_LINE_INPUT"></span><span id="enable_line_input"></span>
<strong>ENABLE_LINE_INPUT</strong> 0x0002</td>
<td><p>La función <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>readfile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> solo devuelve cuando se lee un carácter de retorno de carro. Si este modo está deshabilitado, las funciones devuelven cuando uno o varios caracteres están disponibles.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_MOUSE_INPUT"></span><span id="enable_mouse_input"></span>
<strong>ENABLE_MOUSE_INPUT</strong> 0x0010</td>
<td><p>Si el puntero del mouse está dentro de los bordes de la ventana de la consola y la ventana tiene el foco de teclado, los eventos del mouse generados por el movimiento del mouse y las pulsaciones de botón se colocan en el búfer de entrada. <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>Readfile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>descartan estos eventos, incluso cuando este modo está habilitado.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_PROCESSED_INPUT"></span><span id="enable_processed_input"></span>
<strong>ENABLE_PROCESSED_INPUT</strong> 0x0001</td>
<td><p>El sistema procesa CTRL + C y no se coloca en el búfer de entrada. Si <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>readfile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>leen el búfer de entrada, el sistema procesa otras claves de control y no se devuelven en el búfer <strong>readfile</strong> o <strong>ReadConsole</strong> . Si el modo de <strong>ENABLE_LINE_INPUT</strong> también está habilitado, el sistema controla el retroceso, el retorno de carro y los caracteres de avance de línea.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_QUICK_EDIT_MODE"></span><span id="enable_quick_edit_mode"></span>
<strong>ENABLE_QUICK_EDIT_MODE</strong> 0x0040</td>
<td><p>Esta marca permite al usuario utilizar el mouse para seleccionar y editar texto.</p>
<p>Para habilitar este modo, use <code>ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS</code> . Para deshabilitar este modo, utilice <strong>ENABLE_EXTENDED_FLAGS</strong> sin esta marca.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_WINDOW_INPUT"></span><span id="enable_window_input"></span>
<strong>ENABLE_WINDOW_INPUT</strong> 0x0008</td>
<td><p>Las interacciones de usuario que cambian el tamaño del búfer de pantalla de la consola se muestran en el búfer de entrada de la consola de&#39;s. La información sobre estos eventos se puede leer desde el búfer de entrada mediante aplicaciones que usan la función <a href="readconsoleinput.md" data-raw-source="[&lt;strong&gt;ReadConsoleInput&lt;/strong&gt;](readconsoleinput.md)"><strong>ReadConsoleInput</strong></a> , pero no para los que usan <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>readfile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_VIRTUAL_TERMINAL_INPUT"></span><span id="enable_virtual_terminal_input"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_INPUT</strong> 0x0200</td>
<td><p>Al establecer esta marca, se indica al motor de procesamiento de terminal virtuales que convierta las entradas de usuario recibidas por la ventana de la consola en secuencias de terminal virtuales de la consola que se pueden recuperar mediante una aplicación auxiliar a través de las funciones ReadFile o ReadConsole.</p>
<p>El uso típico de esta marca está pensado junto con ENABLE_VIRTUAL_TERMINAL_PROCESSING en el identificador de salida para conectarse a una aplicación que se comunica exclusivamente a través de secuencias de terminales virtuales.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

Si el parámetro *hConsoleHandle* es un controlador de búfer de pantalla, el modo puede ser uno o varios de los valores siguientes. Cuando se crea un búfer de pantalla, ambos modos de salida están habilitados de forma predeterminada.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Valor</th>
<th>Significado</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="ENABLE_PROCESSED_OUTPUT"></span><span id="enable_processed_output"></span>
<strong>ENABLE_PROCESSED_OUTPUT</strong> 0x0001</td>
<td><p>Los caracteres escritos por la función <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> o que se han devuelto por la función <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>readfile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> se examinan para las secuencias de control ASCII y se realiza la acción correcta. Se procesan los caracteres de retroceso, tabulación, campana, retorno de carro y avance de línea.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_WRAP_AT_EOL_OUTPUT"></span><span id="enable_wrap_at_eol_output"></span>
<strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong> 0x0002</td>
<td><p>Al escribir con <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> o al repetir con <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>readfile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, el cursor se desplaza al principio de la fila siguiente cuando llega al final de la fila actual. Esto hace que las filas mostradas en la ventana de la consola se desplacen automáticamente cuando el cursor avance más allá de la última fila de la ventana. También hace que el contenido del búfer de pantalla de la consola se desplace hacia arriba (descartando la fila superior del búfer de pantalla de la consola) cuando el cursor avanza más allá de la última fila del búfer de pantalla de la consola. Si este modo está deshabilitado, el último carácter de la fila se sobrescribe con los caracteres posteriores.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_VIRTUAL_TERMINAL_PROCESSING"></span><span id="enable_virtual_terminal_processing"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_PROCESSING</strong> 0x0004</td>
<td><p>Al escribir con <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, se analizan los caracteres de las secuencias de caracteres de control de VT100 y similares que controlan el movimiento del cursor, el modo de color/fuente y otras operaciones que también se pueden realizar a través de las API de consola existentes. Para obtener más información, vea <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">secuencias de terminal virtuales de consola</a>.</p></td>
</tr>
<tr class="even">
<td><span id="DISABLE_NEWLINE_AUTO_RETURN"></span><span id="disable_newline_auto_return"></span>
<strong>DISABLE_NEWLINE_AUTO_RETURN</strong> 0x0008</td>
<td><p>Al escribir con <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, se agrega un estado adicional al ajuste de final de línea que puede retrasar las operaciones de movimiento de cursor y desplazamiento de búfer.</p>
<p>Normalmente, cuando se establece ENABLE_WRAP_AT_EOL_OUTPUT y el texto alcanza el final de la línea, el cursor se mueve inmediatamente a la línea siguiente y el contenido del búfer se desplaza hacia arriba una línea. A diferencia de este conjunto de marcadores, la operación de desplazamiento y el movimiento del cursor se retrasan hasta que llega el siguiente carácter. El carácter escrito se imprimirá en la posición final de la línea y el cursor permanecerá por encima de este carácter como si ENABLE_WRAP_AT_EOL_OUTPUT fuera OFF, pero el siguiente carácter imprimible se imprimirá como si ENABLE_WRAP_AT_EOL_OUTPUT estuviera activada. No se producirá ninguna sobrescritura. En concreto, el cursor avanza rápidamente hasta la línea siguiente, se realiza un desplazamiento si es necesario, se imprime el carácter y el cursor se desplaza una posición más.</p>
<p>El uso típico de esta marca está pensado junto con la configuración ENABLE_VIRTUAL_TERMINAL_PROCESSING para emular mejor un emulador de terminal en el que escribir el carácter final en la pantalla (en la esquina inferior derecha) sin desencadenar un desplazamiento inmediato es el comportamiento deseado.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_LVB_GRID_WORLDWIDE"></span><span id="enable_lvb_grid_worldwide"></span>
<strong>ENABLE_LVB_GRID_WORLDWIDE</strong> 0x0010</td>
<td><p>Las API para escribir atributos de caracteres, incluidos <a href="writeconsoleoutput.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutput&lt;/strong&gt;](writeconsoleoutput.md)"><strong>WriteConsoleOutput</strong></a> y <a href="writeconsoleoutputattribute.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutputAttribute&lt;/strong&gt;](writeconsoleoutputattribute.md)"><strong>WriteConsoleOutputAttribute</strong></a> , permiten el uso de marcas de <a href="https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes" data-raw-source="[character attributes](https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes)">atributos de caracteres</a> para ajustar el color de primer plano y de fondo del texto. Además, se especificó un intervalo de marcas DBCS con el prefijo COMMON_LVB. Históricamente, estas marcas solo funcionaban en páginas de códigos DBCS para idiomas chinos, japoneses y coreanos.</p>
<p>Con la excepción de las marcas de bytes iniciales y finales, los marcadores restantes que describen el dibujo de líneas y el vídeo inverso (cambiar los colores de primer plano y de fondo) pueden ser útiles para que otros lenguajes resalten partes de la salida.</p>
<p>Al establecer esta marca de modo de consola, se permitirá utilizar estos atributos en todas las páginas de códigos de todos los lenguajes.</p>
<p>Está desactivada de forma predeterminada para mantener la compatibilidad con las aplicaciones conocidas que han aprovechado históricamente la consola y omitir estas marcas en máquinas no CJK para almacenar bits en estos campos por su propio propósito o por accidente.</p>
<p>Tenga en cuenta que el uso del modo ENABLE_VIRTUAL_TERMINAL_PROCESSING puede dar lugar a la cuadrícula de LVB y a que se establezcan marcas de vídeo inverso, mientras que la aplicación conectada solicita el subrayado o el vídeo inverso a través de las <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">secuencias de terminal virtuales</a>de la consola.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

Una consola de está formada por un búfer de entrada y uno o más búferes de pantalla. El modo de un búfer de consola determina cómo se comporta la consola durante las operaciones de entrada y salida (e/s). Un conjunto de constantes de marca se usa con los identificadores de entrada y otro conjunto se utiliza con los identificadores de búfer de pantalla (salida). La configuración de los modos de salida de un búfer de pantalla no afecta a los modos de salida de otros búferes de pantalla.

Los modos de entrada **habilitar \_ \_ entrada de línea** y **habilitar \_ eco \_ ** solo afectan a los procesos que usan [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) para leer desde el búfer de entrada de la consola. Del mismo modo, la habilitación del modo de ** \_ \_ entrada procesada** afecta principalmente a los usuarios **readfile** y **ReadConsole** , con la salvedad de que también determina si la entrada de Ctrl + C se indica en el búfer de entrada (que será leída por la función [**ReadConsoleInput**](readconsoleinput.md) ) o se pasa a una función [**HandlerRoutine**](handlerroutine.md) definida por la aplicación.

Los **modos \_ habilitar \_ entrada de ventana** y **habilitar \_ \_ entrada del mouse** determinan si las interacciones del usuario que implican el cambio de tamaño de las ventanas y las acciones del mouse se registran en el búfer de entrada o se descartan. Estos eventos pueden ser leídos por [**ReadConsoleInput**](readconsoleinput.md), pero siempre se filtran por [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**ReadConsole**](readconsole.md).

Los modos de salida **habilitar \_ \_ salida procesada** y **habilitar \_ encapsulado \_ en \_ \_ EOL** solo afectan a los procesos que usan [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md).

Para determinar el modo actual de un búfer de entrada de la consola o un búfer de pantalla, utilice la función [**GetConsoleMode**](getconsolemode.md) .

<a name="examples"></a>Ejemplos
--------

Para obtener un ejemplo, vea [leer eventos de búfer de entrada](reading-input-buffer-events.md).

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


[Funciones de la consola](console-functions.md)

[Modos de consola](console-modes.md)

[**GetConsoleMode**](getconsolemode.md)

[**HandlerRoutine**](handlerroutine.md)

[**ReadConsole**](readconsole.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**WriteConsole**](writeconsole.md)

[**Escritura**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




