---
title: Secuencias de terminal virtuales de la consola
description: Las secuencias de terminal virtuales son secuencias de caracteres de control que pueden controlar el movimiento del cursor, el modo del color y la fuente y otras operaciones cuando se escriben en el flujo de salida.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: A5C553A5-FD84-4D16-A814-EDB3B8699B91
ms.openlocfilehash: 29c1cc65db5e20c35ca0aaf6dc58c6e485d0edc6
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358135"
---
# <a name="console-virtual-terminal-sequences"></a>Secuencias de terminal virtuales de la consola


Las secuencias de terminal virtuales son secuencias de caracteres de control que pueden controlar el movimiento del cursor, el modo del color y la fuente y otras operaciones cuando se escriben en el flujo de salida. Asimismo, también se pueden recibir secuencias en el flujo de entrada en respuesta a una secuencia de información de consulta del flujo de salida o como codificación de aquellos datos proporcionados por el usuario cuando se establece el modo adecuado.

Puede usar las funciones [**GetConsoleMode**](getconsolemode.md) y [**SetConsoleMode**](setconsolemode.md) para configurar este comportamiento. Al final de este documento, se incluye un ejemplo con el método sugerido para habilitar los comportamientos de terminal virtual.

El comportamiento de las siguientes secuencias se basa en las tecnologías de VT100 y de emulador de terminal derivado, especialmente en tecnologías del emulador de terminal xterm. Puede encontrar más información sobre las secuencias de terminal en <http://vt100.net> y en <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Secuencias de salida


El host de consola intercepta las siguientes secuencias de terminal cuando se escriben en el flujo de salida, si se establece la marca ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING en el identificador del búfer de pantalla mediante la función [**SetConsoleMode**](setconsolemode.md). Tenga en cuenta que la marca DISABLE\_NEWLINE\_AUTO\_RETURN también puede serle útil para emular la posición del cursor y el comportamiento de desplazamiento de otros emuladores de terminal, en relación con los caracteres que se hayan escrito en la columna final de cualquier fila.

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Posición de cursor simple


En todas las descripciones que se proporcionan a continuación, ESC siempre es el valor hexadecimal 0x1B. No se incluirán espacios en las secuencias de terminal. Para obtener un ejemplo de cómo se usan estas secuencias en la práctica, consulte el [ejemplo](#example) que se encuentra al final de este tema.

En la siguiente tabla se describen las secuencias de escape simples que cuentan con un solo comando de acción directamente después del carácter ESC. Estas secuencias no tienen ningún parámetro y surten efecto inmediatamente.

En general, todos los comandos de esta tabla son equivalentes a la llamada que se realiza a la API de consola [**SetConsoleCursorPosition**](setconsolecursorposition.md) para colocar el cursor.

La ventanilla actual del búfer se encargará de limitar el movimiento del cursor. No se producirá el desplazamiento (si está disponible).


| Secuencia | Abreviatura | Comportamiento |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| ESC A | CUU | Cursor hacia arriba en 1. |
| ESC B | CUD | Cursor hacia abajo en 1. |
| ESC C | CUF | Cursor hacia delante (derecha) en 1. |
| ESC D | CUB | Cursor hacia atrás (izquierda) en 1. |
| ESC M | Instancia reservada | Índice inverso: realiza la operación inversa de \\n, mueve el cursor una línea hacia arriba, mantiene la posición horizontal y desplaza el búfer si es necesario\*. |
| ESC 7 | DECSC | Permite guardar la posición del cursor en la memoria\*\*. |
| ESC 8 | DECSR | Permite restaurar la posición del cursor de la memoria\*\*. |



> [!NOTE]
>\* Si hay márgenes de desplazamiento establecidos, la secuencia RI dentro de los márgenes solo desplazará el contenido de los márgenes y dejará la ventanilla sin cambios. (Consulte los márgenes de desplazamiento)
>
>\*\*No habrá ningún valor guardado en la memoria hasta que no se use por primera vez el comando save. La única manera de obtener acceso al valor guardado es con el comando restore.

## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Posición del cursor


En las tablas siguientes se indican las secuencias de tipo Control Sequence Introducer (CSI). Todas las secuencias CSI comienzan con el valor ESC (0x1B), seguido de \[ (corchete de apertura, 0x5B), y pueden contener parámetros de longitud variable para especificar más información de cada operación. Esto se representará con la abreviatura &lt;n&gt;. Cada una de las tablas siguientes está agrupada según la funcionalidad, y debajo de cada tabla encontrará una serie de notas en las que se explica cómo funciona el grupo.

En todos los parámetros se aplican las reglas siguientes, a menos que se indique lo contrario:

- &lt;n&gt; representa la distancia de traslado y es un parámetro opcional.
- Si &lt;n&gt; se omite o es igual a 0, se tratará como 1.
- &lt;n&gt; no puede ser mayor que 32.767 (valor corto máximo).
- &lt;n&gt; no puede ser negativo.

En general, todos los comandos de esta sección son equivalentes a la llamada que se realiza a la API de consola [**SetConsoleCursorPosition**](setconsolecursorposition.md).

La ventanilla actual del búfer se encargará de limitar el movimiento del cursor. No se producirá el desplazamiento (si está disponible).


| Secuencia | Código | Descripción | Comportamiento |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; A | CUU | Cursor hacia arriba | Cursor hacia arriba en &lt;n&gt;. |
| ESC \[ &lt;n&gt; B | CUD | Cursor hacia abajo | Cursor hacia abajo en &lt;n&gt;. |
| ESC \[ &lt;n&gt; C | CUF | Cursor hacia delante | Cursor hacia delante (derecha) en &lt;n&gt;. |
| ESC \[ &lt;n&gt; D | CUB | Cursor hacia atrás | Cursor hacia atrás (izquierda) en &lt;n&gt;. |
| ESC \[ &lt;n&gt; E | CNL | Siguiente línea del cursor | El cursor se desplaza hacia abajo &lt;n&gt; líneas desde la posición actual. |
| ESC \[ &lt;n&gt; F | CPL | Línea anterior al cursor | El cursor se desplaza hacia arriba &lt;n&gt; líneas desde la posición actual. |
| ESC \[ &lt;n&gt; G | CHA | Horizontal absoluto del cursor | El cursor se mueve a la &lt;n&gt;ª posición horizontal en la línea actual. |
| ESC \[ &lt;n&gt; d | VPA | Posición de línea vertical absoluta | El cursor se desplaza a la &lt;n&gt;ª posición vertical en la columna actual. |
| ESC \[ &lt;y&gt; ; &lt;x&gt; H | CUP | Posición del cursor | \*El cursor se mueve a la coordenada &lt;x&gt;; &lt;y&gt; dentro de la ventanilla, donde &lt;x&gt; es la columna de la línea &lt;y&gt;. |
| ESC \[ &lt;y&gt; ; &lt;x&gt; f | HVP | Posición vertical horizontal | \*El cursor se mueve a la coordenada &lt;x&gt;; &lt;y&gt; dentro de la ventanilla, donde &lt;x&gt; es la columna de la línea &lt;y&gt;. |
| ESC \[ s | ANSISYSSC | Permite guardar el cursor: emulación Ansi.sys | \*\*Sin parámetros; realiza una operación para guardar el cursor como DECSC. |
| ESC \[ u | ANSISYSSC | Permite restaurar el cursor: emulación Ansi.sys | \*\*Sin parámetros; realiza una operación para restaurar el cursor como DECRC. |



> [!NOTE]
>\*Los parámetros &lt;x&gt; e &lt;y&gt; tienen las mismas limitaciones que el valor &lt;n&gt; anterior. Si &lt;x&gt; e &lt;y&gt; se omiten, los valores se establecerán en 1;1.
>
>\*\*La documentación histórica de ANSI.sys se puede encontrar en <https://msdn.microsoft.com/library/cc722862.aspx> y se implementa en función de la comodidad y la compatibilidad.



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Visibilidad del cursor


Los siguientes comandos controlan la visibilidad del cursor y su estado de parpadeo. Las secuencias DECTCEM suelen ser equivalentes a llamar a la API de consola [**SetConsoleCursorInfo**](setconsolecursorinfo.md) para alternar la visibilidad del cursor.


| Secuencia | Código | Descripción | Comportamiento |
|---------------|---------|------------------------------|---------------------------|
| ESC \[ ? 12 h | ATT160 | Cursor de texto para habilitar el parpadeo. | Permite iniciar el parpadeo del cursor. |
| ESC \[ ? 12 l | ATT160 | Cursor de texto para deshabilitar el parpadeo. | Permite detener el parpadeo del cursor. |
| ESC \[ ? 25 h | DECTCEM | Cursor de texto para habilitar el modo para mostrarlo. | Permite mostrar el cursor. |
| ESC \[ ? 25 l | DECTCEM | Cursor de texto para habilitar el modo para ocultarlo. | Permite ocultar el cursor. |

> [!TIP]
> Las secuencias de habilitación terminan en un carácter H en minúscula (`h`) y las secuencias de deshabilitación terminan en un carácter L en minúscula (`l`).

## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Posición de la ventanilla


En general, todos los comandos de esta sección son equivalentes a llamar a la API de consola [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) para trasladar el contenido del búfer de la consola.

**Precaución**: los nombres de comando son engañosos. "Desplazar" hace referencia a la dirección en la que se mueve el texto durante la operación, no a la manera en que la ventanilla se debería mover.




| Secuencia | Código | Descripción | Comportamiento |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; S | SU | Desplazar hacia arriba | Desplazar el texto hacia arriba en &lt;n&gt;. Opción también conocida como "Movimiento panorámico hacia abajo", las nuevas líneas se rellenan desde la parte inferior de la pantalla. |
| ESC \[ &lt;n&gt; T | SD | Desplazar hacia abajo | Desplazarse hacia abajo en &lt;n&gt;. Opción también conocida como "Movimiento panorámico hacia arriba", las nuevas líneas se rellenan desde la parte superior de la pantalla. |



El texto se mueve a partir de la línea en la que se encuentra el cursor. Si el cursor está en la fila central de la ventanilla, al desplazarse hacia arriba se moverá la mitad inferior de la ventanilla y se insertarán líneas en blanco en la parte inferior. En cambio, si se desplaza hacia abajo, se moverá la mitad superior de las filas de la ventanilla y se insertarán nuevas líneas en la parte superior.

También es importante tener en cuenta que los márgenes de desplazamiento también afectan a las opciones para desplazarse hacia arriba y hacia abajo. En cambio, desplazarse hacia arriba y hacia abajo no afectará a las líneas que estén fuera de los márgenes desplazados.

El valor predeterminado de &lt;n&gt; es 1, aunque este valor se puede omitir opcionalmente.

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Modificación de texto


Todos los comandos de esta sección suelen ser equivalentes a llamar a las API de consola [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) y [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) para modificar el contenido del búfer de texto.


| Secuencia | Código | Descripción | Comportamiento |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; @ | ICH | Insertar carácter | Inserte &lt;n&gt; espacios en la posición actual del cursor, desplazando todo el texto existente a la derecha. Asimismo, se quita el texto que sale de la pantalla hacia la derecha. |
| ESC \[ &lt;n&gt; P | DCH | Eliminar carácter | Elimine &lt;n&gt; caracteres en la posición actual del cursor, desplazando los caracteres de espacio desde el borde derecho de la pantalla. |
| ESC \[ &lt;n&gt; X | ECH | Borrar carácter | Borre &lt;n&gt; caracteres de la posición actual del cursor sobrescribiéndolos con un carácter de espacio. |
| ESC \[ &lt;n&gt; L | IL | Insertar línea | Inserta &lt;n&gt; líneas en el búfer en la posición del cursor. La línea en la que se encuentra el cursor y las líneas que tiene debajo se desplazarán hacia abajo. |
| ESC \[ &lt;n&gt; M | DL | Eliminar línea | Elimina &lt;n&gt; líneas del búfer, comenzando por la fila en la que se encuentra el cursor. |



> [!NOTE]
>En el caso de IL y DL, solo se ven afectadas las líneas de los márgenes de desplazamiento (consulte los márgenes de desplazamiento). Si no se establece ningún margen, los bordes de margen predeterminados formarán la ventanilla actual. Si se desplazan las líneas por debajo de los márgenes, estas se descartan. Cuando se eliminan líneas, se insertan líneas en blanco en la parte inferior de los márgenes, pero las líneas de fuera de la ventanilla nunca se ven afectadas.

Para cada una de las secuencias, el valor predeterminado de &lt;n&gt; es 0 si se omite.



En el caso de los siguientes comandos, el parámetro &lt;n&gt; tiene 3 valores válidos:

- 0: borra contenido desde la posición actual del cursor (inclusive) hasta el final de la línea o pantalla.
- 1: borra contenido desde el principio de la línea o la pantalla hasta la posición actual del cursor (inclusive).
- 2: borra la línea o pantalla completa.


| Secuencia | Código | Descripción | Comportamiento |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; J | ED | Borrar en pantalla | Se reemplaza todo el texto de la ventanilla o pantalla actual especificada según &lt;n&gt;, con caracteres de espacio. |
| ESC \[ &lt;n&gt; K | EL | Borrar en línea | Se reemplaza todo el texto de la línea con el cursor especificado según &lt;n&gt;, con caracteres de espacio. |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Formato de texto


Todos los comandos de esta sección suelen ser equivalentes a llamar a la API de consola [**SetConsoleTextAttribute**](setconsoletextattribute.md) para ajustar el formato de todas las escrituras futuras que se realicen en el búfer de texto de la salida de consola.

Este comando es especial, ya que la posición &lt;n&gt; siguiente puede aceptar entre 0 y 16 parámetros separados por puntos y comas.

Cuando no se especifican parámetros, este valor se administra igual que un solo parámetro 0.


| Secuencia | Código | Descripción | Comportamiento |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| ESC \[ &lt;n&gt; m | SGR | Establecer representaciones de gráficos | Se establece el formato de la pantalla y el texto tal como se especifica en &lt;n&gt;. |



La siguiente tabla de valores se puede usar en &lt;n&gt; para representar diferentes modos de formato.

Recuerde que los modos de formato se aplican de izquierda a derecha. Si aplica opciones de formato paralelas, la opción que esté más a la derecha tendrá prioridad.

En el caso de las opciones que especifican colores, se usarán los colores tal y como se define en la tabla de colores de la consola; estos que se pueden modificar con la API [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md). Si se modifica la tabla para que la posición "azul" de la tabla muestre un tono RGB rojo, todas las llamadas de tipo **Primer plano azul** mostrarán el color rojo hasta que las cambie.


| Valor | Descripción | Comportamiento |
|-------|---------------------------|--------------------------------------------------------------------|
| 0 | Predeterminado | Devuelve todos los atributos al estado predeterminado antes de la modificación. |
| 1 | Negrita/Brillo | Aplica la marca de brillo o intensidad al color del primer plano. |
| 22 | Sin negrita/Brillo | Quita la marca de brillo o intensidad del color del primer plano. |
| 4 | Subrayado | Agrega un subrayado. |
| 24 | Sin subrayado | Quita el subrayado. |
| 7 | Negativo | Intercambia los colores de primer plano y de fondo. |
| 27 | Positivo (sin negativo) | Devuelve el primer plano y el fondo a su estado normal. |
| 30 | Primer plano negro | Aplica un color negro brillante y sin negrita al primer plano. |
| 31 | Primer plano rojo | Aplica un color rojo brillante y sin negrita al primer plano. |
| 32 | Primer plano verde | Aplica un color verde brillante y sin negrita al primer plano. |
| 33 | Primer plano amarillo | Aplica un color amarillo brillante y sin negrita al primer plano. |
| 34 | Primer plano azul | Aplica un color azul brillante y sin negrita al primer plano. |
| 35 | Primer plano magenta | Aplica un color magenta brillante y sin negrita al primer plano. |
| 36 | Primer plano cian | Aplica un color cian brillante y sin negrita al primer plano. |
| 37 | Primer plano blanco | Aplica un color blanco brillante y sin negrita al primer plano. |
| 38 | Primer plano extendido | Aplica el valor del color extendido al primer plano (consulte los detalles a continuación). |
| 39 | Valor predeterminado del primer plano | Aplica solo la parte del primer plano que corresponde a los valores predeterminados (consulte 0). |
| 40 | Fondo negro | Aplica un color negro brillante y sin negrita al fondo. |
| 41 | Fondo rojo | Aplica un color rojo brillante y sin negrita al fondo. |
| 42 | Fondo verde | Aplica un color verde brillante y sin negrita al fondo. |
| 43 | Fondo amarillo | Aplica un color amarillo brillante y sin negrita al fondo. |
| 44 | Fondo azul | Aplica un color azul brillante y sin negrita al fondo. |
| 45 | Fondo magenta | Aplica un color magenta brillante y sin negrita al fondo. |
| 46 | Fondo cian | Aplica un color cian brillante y sin negrita al fondo. |
| 47 | Fondo blanco | Aplica un color blanco brillante y sin negrita al fondo. |
| 48 | Fondo extendido | Aplica el valor del color extendido al fondo (consulte los detalles a continuación). |
| 49 | Fondo predeterminado | Aplica solo la parte del fondo que corresponde a los valores predeterminados (consulte 0). |
| 90 | Primer plano negro brillante | Aplica un color negro brillante y con negrita al primer plano. |
| 91 | Primer plano rojo brillante | Aplica un color rojo brillante y con negrita al primer plano. |
| 92 | Primer plano verde brillante | Aplica un color verde brillante y con negrita al primer plano. |
| 93 | Primer plano amarillo brillante | Aplica un color amarillo brillante y con negrita al primer plano. |
| 94 | Primer plano azul brillante | Aplica un color azul brillante y con negrita al primer plano. |
| 95 | Primer plano magenta brillante | Aplica un color magenta brillante y con negrita al primer plano. |
| 96 | Primer plano cian brillante | Aplica un color cian brillante y con negrita al primer plano. |
| 97 | Primer plano blanco brillante | Aplica un color blanco brillante y con negrita al primer plano. |
| 100 | Fondo negro brillante | Aplica un color negro brillante y con negrita al fondo. |
| 101 | Fondo rojo brillante | Aplica un color rojo brillante y con negrita al fondo. |
| 102 | Fondo verde brillante | Aplica un color verde brillante y con negrita al fondo. |
| 103 | Fondo amarillo brillante | Aplica un color amarillo brillante y con negrita al fondo. |
| 104 | Fondo azul brillante | Aplica un color azul brillante y con negrita al fondo. |
| 105 | Fondo magenta brillante | Aplica un color magenta brillante y con negrita al fondo. |
| 106 | Fondo cian brillante | Aplica un color cian brillante y con negrita al fondo. |
| 107 | Fondo blanco brillante | Aplica un color blanco brillante y con negrita al fondo. |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Colores extendidos

Algunos emuladores de terminal virtuales admiten una paleta que cuenta con más colores que los 16 colores que proporciona la consola de Windows. Al usar estos colores extendidos, la consola de Windows elegirá en la tabla de 16 colores existente el color que más se acerque a su elección y lo mostrará. A diferencia de los valores de SGR típicos anteriores, los valores extendidos consumirán parámetros adicionales después del indicador inicial, según la tabla siguiente.


| Subsecuencia SGR | Descripción |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| 38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt; | Permite establecer el color del primer plano a un valor RGB especificado en los parámetros &lt;r&gt;, &lt;g&gt;, &lt;b&gt;\*. |
| 48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt; | Permite establecer el color del fondo a un valor RGB especificado en los parámetros &lt;r&gt;, &lt;g&gt;, &lt;b&gt;\*. |
| 38 ; 5 ; &lt;s&gt; | Permite establecer el color del primer plano en el índice &lt;s&gt; en la tabla de 88 o 256 colores\*. |
| 48 ; 5 ; &lt;s&gt; | Permite establecer el color del fondo en el índice &lt;s&gt; en la tabla de 88 o 256 colores\*. |



\*Las paletas de 88 y 256 colores que se mantienen de forma interna para la comparación se basan en el emulador de terminal xterm. Las tablas de comparación o redondeo no se pueden modificar en este momento.


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Colores de pantalla


El siguiente comando permite que la aplicación establezca los valores de la paleta de colores de la pantalla en cualquier valor RGB.

Los valores RGB deben ser valores hexadecimales entre `0` y `ff`, y están separados por el carácter de barra diagonal (por ejemplo, `rgb:1/24/86`).

Tenga en cuenta que esta secuencia es una secuencia OSC de tipo "comando del sistema operativo" y no un elemento CSI como muchas de las otras secuencias enumeradas; asimismo, esta secuencia comienza por "\\x1b\]" y no por "\\x1b\[".


| Secuencia | Descripción | Comportamiento |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC | Modificar los colores de la pantalla | Establece el índice &lt;i&gt; de la paleta de colores de la pantalla a los valores RGB especificados en &lt;r&gt;, &lt;g&gt;, &lt;b&gt;. |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Cambios de modo


Estas secuencias controlan los modos de entrada. Existen dos conjuntos diferentes de modos de entrada: el modo de teclas del cursor y el modo de teclas del teclado. El modo de teclas del cursor controla las secuencias que emiten las teclas de dirección, así como el inicio y el final, mientras que el modo de teclas del teclado controla principalmente las secuencias que emiten las teclas en el teclado numérico, así como las teclas de función.

Cada uno de estos modos es una configuración booleana simple; esto es, el modo de teclas del cursor puede ser de tipo "normal" (predeterminado) o de tipo "aplicación", y el modo de teclas del teclado puede ser de tipo "numérico" (predeterminado) o de tipo "aplicación".

Consulte las secciones acerca de las teclas del cursor y las teclas numéricas y de función, para conocer las secuencias emitidas en estos modos.


| Secuencia | Código | Descripción | Comportamiento |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| ESC = | DECKPAM | Permite habilitar el modo de aplicación del teclado. | Las teclas del teclado emitirán sus secuencias en el modo de aplicación. |
| ESC &gt; | DECKPNM | Permite habilitar el modo numérico del teclado | Las teclas del teclado emitirán sus secuencias en el modo numérico. |
| ESC \[ ? 1 h | DECCKM | Permite habilitar el modo de aplicación de las teclas del cursor. | Las teclas del teclado emitirán sus secuencias en el modo de aplicación. |
| ESC \[ ? 1 l | DECCKM | Permite deshabilitar el modo de aplicación de las teclas del cursor (esto es, permite usar el modo normal). | Las teclas del teclado emitirán sus secuencias en el modo numérico. |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Estado de la consulta


Todos los comandos de esta sección suelen ser equivalentes a llamar a la API de la consola Get\* para recuperar información sobre el estado actual del búfer de la consola.

> [!NOTE]
>Estas consultas emitirán sus respuestas en el flujo de entrada de la consola inmediatamente después de que se reconozcan en el flujo de salida mientras se establece la marca ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING. La marca ENABLE\_VIRTUAL\_TERMINAL\_INPUT no se aplica a los comandos de la consulta, ya que se supone que una aplicación que realiza la consulta siempre querrá recibir la respuesta.




| Secuencia | Código | Descripción | Comportamiento |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| ESC \[ 6 n | DECXCPR | Indicar la posición del cursor | Emite la posición del cursor como: ESC \[ &lt;r&gt; ; &lt;c&gt; R, donde &lt;r&gt; = fila del cursor y &lt;c&gt; = columna del cursor. |
| ESC \[ 0 c | DA | Atributos de dispositivo | Permite notificar la identidad del terminal. Emitirá "\\x1b\[?1;0c", lo que indica "VT101 sin opciones". |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Pestañas


Aunque la consola de Windows normalmente espera a que las pestañas tengan exclusivamente ocho caracteres de ancho, las \*aplicaciones de Nix que utilicen ciertas secuencias pueden saber dónde están las tabulaciones en las ventanas de la consola para optimizar el movimiento del cursor por parte de la aplicación.

Las secuencias siguientes permiten que una aplicación establezca las ubicaciones de las tabulaciones dentro de la ventana de la consola, así como quitarlas y desplazarse entre ellas.


| Secuencia | Código | Descripción | Comportamiento |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC H | HTS | Conjunto de tabulación horizontal | Establece una tabulación en la columna actual en la que se encuentra el cursor. |
| ESC \[ &lt;n&gt; I | CHT | Tabulación horizontal del cursor (hacia delante) | Permite avanzar el cursor hasta la columna siguiente (en la misma fila) con una tabulación. Si no hay más tabulaciones, puede desplazarse a la última columna de la fila. En cambio, si el cursor está en la última columna, puede desplazarse a la primera columna de la fila siguiente. |
| ESC \[ &lt;n&gt; Z | CBT | Tabulación hacia atrás del cursor | Permite mover el cursor hasta la columna anterior (en la misma fila) con una tabulación. Si no hay más tabulaciones, mueve el cursor a la primera columna. En cambio, si el cursor está en la primera columna, no mueve el cursor. |
| ESC \[ 0 g | TBC | Borrado de la tabulación (columna actual) | Borra la tabulación de la columna actual, si hay alguna. En caso contrario, no hace nada. |
| ESC \[ 3 g | TBC | Borrado de la tabulación (todas las columnas) | Borra todas las tabulaciones establecidas. |



- En el caso de CHT y CBT, &lt;n&gt; es un parámetro opcional (valor predeterminado=1) que indica el número de veces que se debe avanzar el cursor en la dirección especificada.
- Si no se establece ninguna tabulación a través de HTS, CHT y CBT, la primera y la última columna de la ventana serán las dos únicas tabulaciones.
- De la misma manera que sucede con CHT, al usar HTS para establecer una tabulación, la consola también navegará hasta la siguiente tabulación en el resultado de un carácter TAB (0x09, ‘\\t’).

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designación del juego de caracteres


Las secuencias siguientes permiten que un programa cambie la asignación del juego de caracteres activo. Esto permite que un programa emita caracteres ASCII de 7 bits, pero que se muestren como otros glifos en la pantalla del terminal. Actualmente, los únicos dos juegos de caracteres admitidos son ASCII (valor predeterminado) y el juego de caracteres de gráficos especiales DEC. Consulte <http://vt100.net/docs/vt220-rm/table2-4.html> para obtener una lista de todos los caracteres que representa el juego de caracteres de gráficos especiales DEC.


| Secuencia | Descripción | Comportamiento |
|----------|--------------------------------------------|-------------------------------|
| ESC ( 0 | Permite designar el juego de caracteres: trazado de líneas DEC. | Habilita el modo de trazado de líneas DEC. |
| ESC ( B | Permite designar el juego de caracteres ASCII de EE. UU. | Habilita el modo ASCII (valor predeterminado). |



En particular, el modo de trazado de líneas DEC se usa para trazar los bordes en las aplicaciones de consola. En la tabla siguiente se muestra qué caracteres ASCII se asignan a los caracteres de trazado de líneas.


| Hex | ASCII | Trazado de líneas DEC |
|------|-------|------------------|
| 0x6a | j | ┘ |
| 0x6b | k | ┐ |
| 0x6c | l | ┌ |
| 0x6d | m | └ |
| 0x6e | n | ┼ |
| 0x71 | q | ─ |
| 0x74 | t | ├ |
| 0x75 | u | ┤ |
| 0x76 | v | ┴ |
| 0x77 | w | ┬ |
| 0x78 | x | │ |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Márgenes de desplazamiento


Las siguientes secuencias permiten que un programa configure la "región de desplazamiento" de la pantalla que se ve afectada por las operaciones de desplazamiento. Este es un subconjunto de las filas que se ajustan cuando la pantalla se desplaza; por ejemplo, en "\\n" o RI. Asimismo, estos márgenes también afectan a las filas que hayan modificado las opciones Inserción de línea (IL) y Eliminación de línea (DL), Desplazamiento hacia arriba (SU) y Desplazamiento hacia abajo (SD).

Los márgenes de desplazamiento pueden ser especialmente útiles si quiere tener una parte de la pantalla que no se desplace cuando quiera rellenar el resto; por ejemplo, tener una barra de título en la parte superior o una barra de estado en la parte inferior de la aplicación.

En el caso de DECSTBM, existen dos parámetros opcionales, &lt;t&gt; y &lt;b&gt;, que se usan para especificar las filas que representan las líneas superior e inferior de la región de desplazamiento, ambas inclusive. Si se omiten los parámetros, &lt;t&gt; convierte el valor predeterminado en 1 y &lt;b&gt; se establece en el alto de la ventanilla actual.

Los márgenes de desplazamiento son por búfer, por lo que debe tener en cuenta que el búfer alternativo y el búfer principal mantienen configuraciones de márgenes de desplazamiento independientes; por ello, una aplicación de pantalla completa en el búfer alternativo no afectará a los márgenes del búfer principal.


| Secuencia | Código | Descripción | Comportamiento |
|--------------------------------|---------|----------------------|------------------------------------------------|
| ESC \[ &lt;t&gt; ; &lt;b&gt; r | DECSTBM | Permite establecer la región de desplazamiento. | Establece los márgenes de desplazamiento de VT de la ventanilla. |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Título de ventana


Los siguientes comandos permiten que la aplicación establezca el título de la ventana de la consola en el parámetro &lt;string&gt; especificado. La cadena debe tener menos de 255 caracteres para que pueda aceptarse. Esto equivale a llamar al elemento SetConsoleTitle con la cadena especificada.

Tenga en cuenta que esta secuencia es una secuencia OSC de tipo "Comando del sistema operativo" y no un elemento CSI como muchas de las otras secuencias enumeradas; asimismo, esta secuencia comienza por "\\x1b\]" y no por "\\x1b\[".


| Secuencia | Descripción | Comportamiento |
|-------------------------------|---------------------------|----------------------------------------------------|
| ESC \] 0 ; &lt;string&gt; BEL | Permite establecer el título de la ventana y el icono. | Establece el título de la ventana de la consola en &lt;string&gt;. |
| ESC \] 2 ; &lt;string&gt; BEL | Permite establecer el título de la ventana. | Establece el título de la ventana de la consola en &lt;string&gt;. |



El carácter final que se indica aquí es el carácter "Bell", "\\x07".

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Búfer de pantalla alternativo


\*Las aplicaciones de estilo Nix suelen usar un búfer de pantalla alternativo para que puedan modificar todo el contenido del búfer, sin que ello afecte a la aplicación que inició ese contenido. El búfer alternativo tiene exactamente las dimensiones de la ventana, sin ninguna región desplazamiento.

Para obtener un ejemplo de este comportamiento, tenga en cuenta cuándo se inicia VIM desde Bash. VIM usa toda la pantalla para editar el archivo, por lo que si vuelve a Bash, el búfer original no se modifica.


| Secuencia | Descripción | Comportamiento |
|--------------------|-----------------------------|--------------------------------------------|
| ESC \[ ? 1 0 4 9 h | Permite usar el búfer de pantalla alternativo. | Cambia a un nuevo búfer de pantalla alternativo. |
| ESC \[ ? 1 0 4 9 l | Permite usar el búfer de pantalla principal. | Cambia al búfer principal. |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Ancho de la ventana


Las secuencias siguientes se pueden usar para controlar el ancho de la ventana de la consola. Son aproximadamente equivalentes a la llamada a la API de la consola SetConsoleScreenBufferInfoEx, que se realiza para establecer el ancho de la ventana.


| Secuencia | Código | Descripción | Comportamiento |
|--------------|---------|------------------------------|---------------------------------------------|
| ESC \[ ? 3 h | DECCOLM | Permite establecer el número de columnas en 132. | Establece el ancho de la consola en 132 columnas de ancho. |
| ESC \[ ? 3 l | DECCOLM | Permite establecer el número de columnas en 80. | Establece el ancho de la consola en 80 columnas de ancho. |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Restablecimiento parcial


Puede usar la siguiente secuencia para restablecer los valores predeterminados de algunas propiedades. Las siguientes propiedades se restablecen a los siguientes valores predeterminados (también se muestran las secuencias que controlan esas propiedades):

- Visibilidad del cursor: visible (DECTEM)
- Teclado numérico: Modo numérico (DECNKM)
- Modo de teclas del cursor: Modo normal (DECCKM)
- Márgenes superior e inferior: Superior=1, Inferior=alto de la consola (DECSTBM)
- Juego de caracteres: ASCII (EE. UU.)
- Representación de gráficos: Predeterminado/Desactivado (SGR)
- Guardar el estado del cursor: Posición de inicio (0,0) (DECSC)


| Secuencia | Código | Descripción | Comportamiento |
|------------|--------|-------------|----------------------------------------------------|
| ESC \[ ! p | DECSTR | Restablecimiento parcial | Permite restablecer los valores predeterminados de ciertas opciones de terminal. |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Secuencias de entrada


El host de consola emite las siguientes secuencias de terminal en el flujo de entrada si se establece la marca ENABLE\_VIRTUAL\_TERMINAL\_INPUT en el identificador del búfer de entrada mediante la marca SetConsoleMode.

Existen dos modos internos que controlan qué secuencias se emiten para las teclas de entrada dadas: el modo de teclas del cursor y el modo de teclas del teclado. Ambos modos se describen en la sección de Cambios en el modo.

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Teclas del cursor


| Clave | Modo normal | Modo de la aplicación |
|-------------|-------------|------------------|
| Flecha arriba | ESC \[ A | ESC O A |
| Flecha abajo | ESC \[ B | ESC O B |
| Flecha derecha | ESC \[ C | ESC O C |
| Flecha izquierda | ESC \[ D | ESC O D |
| Inicio | ESC \[ H | ESC O H |
| End | ESC \[ F | ESC O F |



Asimismo, si se presiona Ctrl con cualquiera de estas teclas, se emiten las secuencias siguientes en su lugar, independientemente del modo de teclas del cursor:


| Clave | Cualquier modo |
|--------------------|----------------|
| Ctrl + Flecha arriba | ESC \[ 1 ; 5 A |
| Ctrl + Flecha abajo | ESC \[ 1 ; 5 B |
| Ctrl + Flecha derecha | ESC \[ 1 ; 5 C |
| Ctrl + Flecha izquierda | ESC \[ 1 ; 5 D |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Teclas de función y teclado


| Clave | Secuencia |
|-----------|--------------|
| Retroceso | 0x7f (DEL) |
| Pausar | 0x1a (SUB) |
| Escape | 0x1b (ESC) |
| Insertar | ESC \[ 2 ~ |
| Eliminar | ESC \[ 3 ~ |
| Re Pág | ESC \[ 5 ~ |
| Av Pág | ESC \[ 6 ~ |
| F1 | ESC O P |
| F2 | ESC O Q |
| F3 | ESC O R |
| F4 | ESC O S |
| F5 | ESC \[ 1 5 ~ |
| F6 | ESC \[ 1 7 ~ |
| F7 | ESC \[ 1 8 ~ |
| F8 | ESC \[ 1 9 ~ |
| F9 | ESC \[ 2 0 ~ |
| F10 | ESC \[ 2 1 ~ |
| F11 | ESC \[ 2 3 ~ |
| F12 | ESC \[ 2 4 ~ |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modificadores

Alt se trata al prefijar la secuencia con un escape: ESC &lt;c&gt;, donde &lt;c&gt; es el carácter que pasa el sistema operativo. Alt+Ctrl se usa de la misma manera, salvo que el sistema operativo habrá desplazado la tecla &lt;c&gt; al carácter de control adecuado que se retransmitirá a la aplicación.

Ctrl suele pasar tal como se recibe del sistema. Este suele ser un carácter único que se ha desplazado hacia abajo en el espacio reservado del carácter de control (0x0-0x1f). Por ejemplo, Ctrl+@ (0x40) se convierte en NUL (0x00), Ctrl+\[ (0x5b) se convierte en ESC (0x1b), etc. Algunas combinaciones de teclas Ctrl se tratan de forma especial según la tabla siguiente:


| Clave | Secuencia |
|--------------------|----------------|
| Ctrl + Espacio | 0x00 (NUL) |
| Ctrl + Flecha arriba | ESC \[ 1 ; 5 A |
| Ctrl + Flecha abajo | ESC \[ 1 ; 5 B |
| Ctrl + Flecha derecha | ESC \[ 1 ; 5 C |
| Ctrl + Flecha izquierda | ESC \[ 1 ; 5 D |



> [!NOTE]
><kbd>Ctrl</kbd> izquierdo + <kbd>Alt</kbd> derecho se trata como AltGr. Cuando ambos se usan juntos, se eliminarán y el valor Unicode del carácter que haya presentado el sistema se pasará al destino. El sistema traducirá previamente los valores de AltGr según la configuración de entrada del sistema actual.



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Ejemplos


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span id="example"></span><span id="EXAMPLE"></span>Ejemplo de secuencias de terminales de SGR

En el código siguiente se proporcionan varios ejemplos de formato de texto.

```C
#include <stdio.h>
#include <wchar.h>
#include <windows.h>

int main()
{
    // Set output mode to handle virtual terminal sequences
    HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
    if (hOut == INVALID_HANDLE_VALUE)
    {
        return GetLastError();
    }

    DWORD dwMode = 0;
    if (!GetConsoleMode(hOut, &dwMode))
    {
        return GetLastError();
    }

    dwMode |= ENABLE_VIRTUAL_TERMINAL_PROCESSING;
    if (!SetConsoleMode(hOut, dwMode))
    {
        return GetLastError();
    }

    // Try some Set Graphics Rendition (SGR) terminal escape sequences
    wprintf(L"\x1b[31mThis text has a red foreground using SGR.31.\r\n");
    wprintf(L"\x1b[1mThis text has a bright (bold) red foreground using SGR.1 to affect the previous color setting.\r\n");
    wprintf(L"\x1b[mThis text has returned to default colors using SGR.0 implicitly.\r\n");
    wprintf(L"\x1b[34;46mThis text shows the foreground and background change at the same time.\r\n");
    wprintf(L"\x1b[0mThis text has returned to default colors using SGR.0 explicitly.\r\n");
    wprintf(L"\x1b[31;32;33;34;35;36;101;102;103;104;105;106;107mThis text attempts to apply many colors in the same command. Note the colors are applied from left to right so only the right-most option of foreground cyan (SGR.36) and background bright white (SGR.107) is effective.\r\n");
    wprintf(L"\x1b[39mThis text has restored the foreground color only.\r\n");
    wprintf(L"\x1b[49mThis text has restored the background color only.\r\n");

    return 0;
}
```

> [!NOTE]
>En el ejemplo anterior, la cadena "`\x1b[31m`" es la implementación de **ESC \[ &lt;n&gt; m**, donde &lt;n&gt; es 31.



En el gráfico siguiente se muestra la salida del ejemplo de código anterior.

![salida de la consola mediante el comando SGR](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Ejemplo para habilitar el procesamiento del terminal virtual

El código siguiente proporciona un ejemplo de la manera recomendada para habilitar el procesamiento del terminal virtual de una aplicación. El propósito de este ejemplo es mostrar lo siguiente:

1. Que el modo existente siempre debe recuperarse a través de GetConsoleMode y analizarse antes de establecerlo con SetConsoleMode.

2. Que comprobar si SetConsoleMode devuelve `0` y si GetLastError devuelve STATUS\_INVALID\_PARAMETER resulta ser el mecanismo actual para determinar cuándo se ejecuta en un sistema de nivel inferior. Una aplicación que recibe la marca STATUS\_INVALID\_PARAMETER con una de las marcas de modo de consola más recientes en el campo de bits, debe degradar correctamente el comportamiento e intentarlo de nuevo.

```C
#include <stdio.h>
#include <wchar.h>
#include <windows.h>

int main()
{
    // Set output mode to handle virtual terminal sequences
    HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
    if (hOut == INVALID_HANDLE_VALUE)
    {
        return false;
    }
    HANDLE hIn = GetStdHandle(STD_INPUT_HANDLE);
    if (hIn == INVALID_HANDLE_VALUE)
    {
        return false;
    }

    DWORD dwOriginalOutMode = 0;
    DWORD dwOriginalInMode = 0;
    if (!GetConsoleMode(hOut, &dwOriginalOutMode))
    {
        return false;
    }
    if (!GetConsoleMode(hIn, &dwOriginalInMode))
    {
        return false;
    }

    DWORD dwRequestedOutModes = ENABLE_VIRTUAL_TERMINAL_PROCESSING | DISABLE_NEWLINE_AUTO_RETURN;
    DWORD dwRequestedInModes = ENABLE_VIRTUAL_TERMINAL_INPUT;

    DWORD dwOutMode = dwOriginalOutMode | dwRequestedOutModes;
    if (!SetConsoleMode(hOut, dwOutMode))
    {
        // we failed to set both modes, try to step down mode gracefully.
        dwRequestedOutModes = ENABLE_VIRTUAL_TERMINAL_PROCESSING;
        dwOutMode = dwOriginalOutMode | dwRequestedOutModes;
        if (!SetConsoleMode(hOut, dwOutMode))
        {
            // Failed to set any VT mode, can't do anything here.
            return -1;
        }
    }

    DWORD dwInMode = dwOriginalInMode | ENABLE_VIRTUAL_TERMINAL_INPUT;
    if (!SetConsoleMode(hIn, dwInMode))
    {
        // Failed to set VT input mode, can't do anything here.
        return -1;
    }

    return 0;
}
```

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Ejemplo para seleccionar las características de actualización de aniversario

En el ejemplo siguiente se pretende proporcionar un ejemplo más sólido de código, usando para ello una variedad de secuencias de escape para manipular el búfer, poniendo énfasis en las características agregadas en la Actualización de aniversario de Windows 10.

En este ejemplo se usa el búfer de pantalla alternativo, se manipulan las tabulaciones, se establecen los márgenes de desplazamiento y se cambia el juego de caracteres.

```C
// System headers
#include <windows.h>

// Standard library C-style
#include <wchar.h>
#include <stdlib.h>
#include <stdio.h>

#define ESC "\x1b"
#define CSI "\x1b["

bool EnableVTMode()
{
    // Set output mode to handle virtual terminal sequences
    HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
    if (hOut == INVALID_HANDLE_VALUE)
    {
        return false;
    }

    DWORD dwMode = 0;
    if (!GetConsoleMode(hOut, &dwMode))
    {
        return false;
    }

    dwMode |= ENABLE_VIRTUAL_TERMINAL_PROCESSING;
    if (!SetConsoleMode(hOut, dwMode))
    {
        return false;
    }
    return true;
}

void PrintVerticalBorder()
{
    printf(ESC "(0"); // Enter Line drawing mode
    printf(CSI "104;93m"); // bright yellow on bright blue
    printf("x"); // in line drawing mode, \x78 -> \u2502 "Vertical Bar"
    printf(CSI "0m"); // restore color
    printf(ESC "(B"); // exit line drawing mode
}

void PrintHorizontalBorder(COORD const Size, bool fIsTop)
{
    printf(ESC "(0"); // Enter Line drawing mode
    printf(CSI "104;93m"); // Make the border bright yellow on bright blue
    printf(fIsTop ? "l" : "m"); // print left corner 

    for (int i = 1; i < Size.X - 1; i++)
        printf("q"); // in line drawing mode, \x71 -> \u2500 "HORIZONTAL SCAN LINE-5"

    printf(fIsTop ? "k" : "j"); // print right corner
    printf(CSI "0m");
    printf(ESC "(B"); // exit line drawing mode
}

void PrintStatusLine(const char* const pszMessage, COORD const Size)
{
    printf(CSI "%d;1H", Size.Y);
    printf(CSI "K"); // clear the line
    printf(pszMessage);
}

int __cdecl wmain(int argc, WCHAR* argv[])
{
    argc; // unused
    argv; // unused
    //First, enable VT mode
    bool fSuccess = EnableVTMode();
    if (!fSuccess)
    {
        printf("Unable to enter VT processing mode. Quitting.\n");
        return -1;
    }
    HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
    if (hOut == INVALID_HANDLE_VALUE)
    {
        printf("Couldn't get the console handle. Quitting.\n");
        return -1;
    }

    CONSOLE_SCREEN_BUFFER_INFO ScreenBufferInfo;
    GetConsoleScreenBufferInfo(hOut, &ScreenBufferInfo);
    COORD Size;
    Size.X = ScreenBufferInfo.srWindow.Right - ScreenBufferInfo.srWindow.Left + 1;
    Size.Y = ScreenBufferInfo.srWindow.Bottom - ScreenBufferInfo.srWindow.Top + 1;

    // Enter the alternate buffer
    printf(CSI "?1049h");

    // Clear screen, tab stops, set, stop at columns 16, 32
    printf(CSI "1;1H");
    printf(CSI "2J"); // Clear screen

    int iNumTabStops = 4; // (0, 20, 40, width)
    printf(CSI "3g"); // clear all tab stops
    printf(CSI "1;20H"); // Move to column 20
    printf(ESC "H"); // set a tab stop

    printf(CSI "1;40H"); // Move to column 40
    printf(ESC "H"); // set a tab stop

    // Set scrolling margins to 3, h-2
    printf(CSI "3;%dr", Size.Y - 2);
    int iNumLines = Size.Y - 4;

    printf(CSI "1;1H");
    printf(CSI "102;30m");
    printf("Windows 10 Anniversary Update - VT Example");
    printf(CSI "0m");

    // Print a top border - Yellow
    printf(CSI "2;1H");
    PrintHorizontalBorder(Size, true);

    // // Print a bottom border
    printf(CSI "%d;1H", Size.Y - 1);
    PrintHorizontalBorder(Size, false);

    wchar_t wch;

    // draw columns
    printf(CSI "3;1H");
    int line = 0;
    for (line = 0; line < iNumLines * iNumTabStops; line++)
    {
        PrintVerticalBorder();
        if (line + 1 != iNumLines * iNumTabStops) // don't advance to next line if this is the last line
            printf("\t"); // advance to next tab stop

    }

    PrintStatusLine("Press any key to see text printed between tab stops.", Size);
    wch = _getwch();

    // Fill columns with output
    printf(CSI "3;1H");
    for (line = 0; line < iNumLines; line++)
    {
        int tab = 0;
        for (tab = 0; tab < iNumTabStops - 1; tab++)
        {
            PrintVerticalBorder();
            printf("line=%d", line);
            printf("\t"); // advance to next tab stop
        }
        PrintVerticalBorder();// print border at right side
        if (line + 1 != iNumLines)
            printf("\t"); // advance to next tab stop, (on the next line)
    }

    PrintStatusLine("Press any key to demonstrate scroll margins", Size);
    wch = _getwch();

    printf(CSI "3;1H");
    for (line = 0; line < iNumLines * 2; line++)
    {
        printf(CSI "K"); // clear the line
        int tab = 0;
        for (tab = 0; tab < iNumTabStops - 1; tab++)
        {
            PrintVerticalBorder();
            printf("line=%d", line);
            printf("\t"); // advance to next tab stop
        }
        PrintVerticalBorder(); // print border at right side
        if (line + 1 != iNumLines * 2)
        {
            printf("\n"); //Advance to next line. If we're at the bottom of the margins, the text will scroll.
            printf("\r"); //return to first col in buffer
        }
    }

    PrintStatusLine("Press any key to exit", Size);
    wch = _getwch();

    // Exit the alternate buffer
    printf(CSI "?1049l");

}
```
