---
title: Secuencias de terminal virtuales de la consola
description: Las secuencias de terminal virtuales son secuencias de caracteres de control que pueden controlar el movimiento del cursor, el modo de color/fuente y otras operaciones cuando se escriben en el flujo de salida.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: A5C553A5-FD84-4D16-A814-EDB3B8699B91
ms.openlocfilehash: 45ee5518ec8ea2da840d2a4442efd9e0d4346526
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039153"
---
# <a name="console-virtual-terminal-sequences"></a>Secuencias de terminal virtuales de la consola


Las secuencias de terminal virtuales son secuencias de caracteres de control que pueden controlar el movimiento del cursor, el modo de color/fuente y otras operaciones cuando se escriben en el flujo de salida. También se pueden recibir secuencias en el flujo de entrada en respuesta a una secuencia de información de consulta de flujo de salida o como codificación de datos proporcionados por el usuario cuando se establece el modo adecuado.

Puede usar las funciones [**GetConsoleMode**](getconsolemode.md) y [**SetConsoleMode**](setconsolemode.md) para configurar este comportamiento. Al final de este documento, se incluye un ejemplo de la forma sugerida de habilitar los comportamientos de terminal virtual.

El comportamiento de las secuencias siguientes se basa en las tecnologías de VT100 y de emulador de terminal derivado, especialmente en el emulador de terminal de xterm. Puede encontrar más información sobre las secuencias de terminal en <http://vt100.net> y en <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html> .

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Secuencias de salida


El host de consola intercepta las siguientes secuencias de terminal cuando se escriben en el flujo de salida, si la marca habilitar el \_ \_ \_ procesamiento de terminal virtual está establecida en el identificador de búfer de pantalla mediante la función [**SetConsoleMode**](setconsolemode.md) . Tenga en cuenta que la marca deshabilitar \_ \_ devolución automática de nueva línea \_ también puede ser útil para emular la posición del cursor y el comportamiento de desplazamiento de otros emuladores de terminal en relación con los caracteres escritos en la columna final de cualquier fila.

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Posición de cursor simple


En todas las descripciones siguientes, ESC siempre es el valor hexadecimal 0x1B. No se incluirán espacios en las secuencias de terminal. Para obtener un ejemplo de cómo se usan estas secuencias en la práctica, vea el [ejemplo](#example) al final de este tema.

En la tabla siguiente se describen las secuencias de escape simples con un solo comando de acción directamente después del carácter ESC. Estas secuencias no tienen ningún parámetro y surten efecto inmediatamente.

Todos los comandos de esta tabla suelen ser equivalentes a llamar a la API de la consola de [**SetConsoleCursorPosition**](setconsolecursorposition.md) para colocar el cursor.

El movimiento del cursor estará limitado por la ventanilla actual en el búfer. No se producirá el desplazamiento (si está disponible).


| Secuencia | Abreviada | Comportamiento |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| ESC A | CUU | Cursor hacia arriba en 1 |
| ESC B | CUD | Cursor hacia abajo en 1 |
| ESC C | CUF | Cursor hacia delante (derecha) en 1 |
| ESC D | CUB | Cursor hacia atrás (izquierda) en 1 |
| ESC M | Instancia reservada | Reverse index: realiza la operación inversa de \\ n, mueve el cursor una línea hacia arriba, mantiene la posición horizontal y desplaza el búfer si es necesario.\* |
| ESC 7 | DECSC | Guardar la posición del cursor en la memoria\*\* |
| ESC 8 | DECSR | Restaurar la posición del cursor desde la memoria\*\* |



> [!NOTE]
>\* Si hay márgenes de desplazamiento establecidos, RI dentro de los márgenes solo se desplazará por el contenido de los márgenes y dejará la ventanilla sin cambios. (Consulte márgenes de desplazamiento)
>
>\*\*No habrá ningún valor guardado en la memoria hasta el primer uso del comando Guardar. La única manera de tener acceso al valor guardado es con el comando restore.

## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Posición del cursor


Las tablas siguientes abarcan las secuencias de tipo de presentador de secuencia de control (CSI). Todas las secuencias CSI comienzan con ESC (0x1B) seguidos de \[ (corchete de apertura, 0x5B) y pueden contener parámetros de longitud variable para especificar más información para cada operación. Esto se representará con la forma abreviada &lt; n &gt; . Cada tabla siguiente está agrupada por funcionalidad con notas debajo de cada tabla en la que se explica cómo funciona el grupo.

En todos los parámetros, se aplican las reglas siguientes, a menos que se indique lo contrario:

- &lt;n &gt; representa la distancia que se va a trasladar y es un parámetro opcional
- Si &lt; n &gt; se omite o es igual a 0, se tratará como 1
- &lt;n &gt; no puede ser mayor que 32.767 (valor corto máximo)
- &lt;n &gt; no puede ser negativo

Todos los comandos de esta sección suelen ser equivalentes a llamar a la API de la consola de [**SetConsoleCursorPosition**](setconsolecursorposition.md) .

El movimiento del cursor estará limitado por la ventanilla actual en el búfer. No se producirá el desplazamiento (si está disponible).


| Secuencia | Código | Descripción | Comportamiento |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt; n &gt; A | CUU | Cursor hacia arriba | Cursor hacia arriba por &lt; n&gt; |
| ESC \[ &lt; n &gt; B | CUD | Cursor hacia abajo | Cursor hacia abajo por &lt; n&gt; |
| ESC \[ &lt; n &gt; C | CUF | Cursor hacia delante | Cursor hacia delante (derecha) por &lt; n&gt; |
| ESC \[ &lt; n &gt; D | CUB | Cursor hacia atrás | Cursor hacia atrás (izquierda) por &lt; n&gt; |
| ESC \[ &lt; n &gt; E | CNL | Cursor siguiente línea | Cursor hacia abajo &lt; n &gt; líneas desde la posición actual |
| ESC \[ &lt; n &gt; F | CPL | Línea de cursor anterior | Cursor hacia arriba &lt; n &gt; líneas desde la posición actual |
| ESC \[ &lt; n &gt; G | CHA | Cursor horizontal absoluto | El cursor se mueve a &lt; &gt; la posición n horizontalmente en la línea actual |
| ESC \[ &lt; n &gt; d | VPA | Posición de línea vertical absoluta | El cursor se mueve a la &lt; &gt; posición n verticalmente en la columna actual |
| ESC \[ &lt; y &gt; ; &lt; x &gt; H | CUP | Posición del cursor | \*El cursor se mueve a &lt; x &gt; ; &lt; coordenada y &gt; dentro de la ventanilla, donde &lt; x &gt; es la columna de la &lt; &gt; línea y |
| ESC \[ &lt; y &gt; ; &lt; x &gt; f | HVP | Posición vertical horizontal | \*El cursor se mueve a &lt; x &gt; ; &lt; coordenada y &gt; dentro de la ventanilla, donde &lt; x &gt; es la columna de la &lt; &gt; línea y |
| ESC \[ s | ANSISYSSC | Guardar cursor: emulación de Ansi.sys | \*\*Sin parámetros, realiza una operación de guardar el cursor como DECSC |
| ESC \[ u | ANSISYSSC | Cursor de restauración: emulación de Ansi.sys | \*\*Sin parámetros, realiza una operación de restauración de cursor como DECRC |



> [!NOTE]
>\*&lt;los &gt; parámetros x e y &lt; &gt; tienen las mismas limitaciones que &lt; n &gt; anteriores. Si &lt; &gt; &lt; se omiten x e y, se &gt; establecerán en 1; 1.
>
>\*\*ANSI.sys documentación histórica puede encontrarse en <https://msdn.microsoft.com/library/cc722862.aspx> y se implementa por comodidad y compatibilidad.



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Visibilidad del cursor


Los siguientes comandos controlan la visibilidad del cursor y su estado de parpadeo. Las secuencias DECTCEM suelen ser equivalentes a llamar a la API de la consola de [**SetConsoleCursorInfo**](setconsolecursorinfo.md) para alternar la visibilidad del cursor.


| Secuencia | Código | Descripción | Comportamiento |
|---------------|---------|------------------------------|---------------------------|
| \[¿ESC? 12 h | ATT160 | Cursor de texto habilitar parpadeo | Iniciar el parpadeo del cursor |
| \[¿ESC? 12 l | ATT160 | Deshabilitar parpadeo de cursor de texto | Detener el parpadeo del cursor |
| \[¿ESC? 25 h | DECTCEM | Modo de activación de cursor de texto, Mostrar | Mostrar el cursor |
| \[¿ESC? 25 l | DECTCEM | Ocultar modo de cursor de texto | Ocultar el cursor |

> [!TIP]
> El final de las secuencias de la habilitación termina con un carácter H en minúscula ( `h` ) y el extremo de las secuencias deshabilitadas en un carácter L en minúscula ( `l` ).

## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Posición de la ventanilla


Todos los comandos de esta sección suelen ser equivalentes a llamar a la API de la consola de [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) para trasladar el contenido del búfer de la consola.

**PRECAUCIÓN** Los nombres de comando son engañosos. Desplazar hace referencia a la dirección en la que se mueve el texto durante la operación, no a la manera en que la ventanilla parecería moverse.




| Secuencia | Código | Descripción | Comportamiento |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| ESC \[ &lt; n &gt; S | SU | Desplazar hacia arriba | Desplazar texto hacia arriba por &lt; n &gt; . También conocido como panorámica hacia abajo, las nuevas líneas se rellenan desde la parte inferior de la pantalla |
| ESC \[ &lt; n &gt; T | SD | Desplazar hacia abajo | Desplácese hacia abajo por &lt; n &gt; . También conocido como pan up, nuevas líneas que se rellenan desde la parte superior de la pantalla |



El texto se mueve a partir de la línea en la que se encuentra el cursor. Si el cursor está en la fila central de la ventanilla, al desplazarse hacia arriba se moverá la mitad inferior de la ventanilla y se insertarán líneas en blanco en la parte inferior. Desplazarse hacia abajo moverá la mitad superior de las filas de la ventanilla e insertará nuevas líneas en la parte superior.

También es importante tener en cuenta que los márgenes de desplazamiento también afectan hacia arriba y hacia abajo. Desplazarse hacia arriba y hacia abajo no afectará a las líneas fuera de los márgenes desplazados.

El valor predeterminado de &lt; n &gt; es 1 y el valor se puede omitir opcionalmente.

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Modificación de texto


Todos los comandos de esta sección suelen ser equivalentes a llamar a las API de consola [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)y [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) para modificar el contenido del búfer de texto.


| Secuencia | Código | Descripción | Comportamiento |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt; n&gt; @ | ICH | Insertar carácter | Insertar &lt; n &gt; espacios en la posición actual del cursor, desplazando todo el texto existente a la derecha. Se quita el texto que sale de la pantalla hacia la derecha. |
| ESC \[ &lt; n &gt; P | DCH | Eliminar carácter | Elimine &lt; n &gt; caracteres en la posición actual del cursor, desplazando los caracteres de espacio desde el borde derecho de la pantalla. |
| ESC \[ &lt; n &gt; X | ECH | Borrar carácter | Borrar &lt; n &gt; caracteres de la posición actual del cursor si se sobrescriben con un carácter de espacio. |
| ESC \[ &lt; n &gt; L | IL | Insertar línea | Inserta &lt; n &gt; líneas en el búfer en la posición del cursor. La línea en la que se encuentra el cursor y las líneas que hay debajo se desplazará hacia abajo. |
| ESC \[ &lt; n &gt; M | DL | Eliminar línea | Elimina &lt; n &gt; líneas del búfer, comenzando por la fila en la que se encuentra el cursor. |



> [!NOTE]
>En el caso de IL y DL, solo se ven afectadas las líneas de los márgenes de desplazamiento (vea los márgenes de desplazamiento). Si no se establece ningún margen, los bordes de margen predeterminados son la ventanilla actual. Si se desplazan las líneas por debajo de los márgenes, se descartan. Cuando se eliminan líneas, se insertan líneas en blanco en la parte inferior de los márgenes, mientras que las líneas desde fuera de la ventanilla nunca se ven afectadas.

Para cada una de las secuencias, el valor predeterminado de &lt; n &gt; si se omite es 0.



En el caso de los siguientes comandos, el parámetro &lt; n &gt; tiene 3 valores válidos:

- 0 borra desde la posición actual del cursor (inclusivo) hasta el final de la línea o pantalla.
- 1 borra desde el principio de la línea/muestra hasta la posición actual del cursor, inclusive
- 2 borra la línea o pantalla completa


| Secuencia | Código | Descripción | Comportamiento |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| ESC \[ &lt; n &gt; J | ED | Borrar en pantalla | Reemplazar todo el texto de la ventanilla o pantalla actual especificada por &lt; n por &gt; caracteres de espacio |
| ESC \[ &lt; n &gt; K | Torito | Borrar en línea | Reemplazar todo el texto de la línea con el cursor especificado por &lt; n por &gt; caracteres de espacio |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Formato de texto


Todos los comandos de esta sección suelen ser equivalentes a llamar a las API de la consola de [**SetConsoleTextAttribute**](setconsoletextattribute.md) para ajustar el formato de todas las escrituras futuras en el búfer de texto de salida de la consola.

Este comando es especial, ya que &lt; la &gt; posición n siguiente puede aceptar entre 0 y 16 parámetros separados por punto y coma.

Cuando no se especifican parámetros, se trata igual que un solo parámetro 0.


| Secuencia | Código | Descripción | Comportamiento |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| ESC \[ &lt; n &gt; m | SGR | Establecer copias de gráficos | Establezca el formato de la pantalla y el texto tal y como se especifica en &lt; n&gt; |



La siguiente tabla de valores se puede usar en &lt; n &gt; para representar diferentes modos de formato.

Los modos de formato se aplican de izquierda a derecha. La aplicación de las opciones de formato de la competencia dará lugar a que la opción más a la derecha tenga prioridad.

En el caso de las opciones que especifican colores, se usarán los colores tal y como se definen en la tabla de colores de la consola, que se pueden modificar mediante la API de [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) . Si se modifica la tabla para que la posición "azul" en la tabla muestre un tono RGB de rojo, todas las llamadas al **azul de primer plano** mostrarán el color rojo hasta que cambien.


| Valor | Descripción | Comportamiento |
|-------|---------------------------|--------------------------------------------------------------------|
| 0 | Valor predeterminado | Devuelve todos los atributos al estado predeterminado antes de la modificación. |
| 1 | Negrita/brillante | Aplica la marca de brillo/intensidad al color de primer plano |
| 4 | Subrayado | Agrega el subrayado |
| 24 | Sin subrayado | Quita el subrayado |
| 7 | Negativo | Intercambia los colores de primer plano y de fondo |
| 27 | Positivo (sin negativo) | Devuelve Foreground/Background a normal |
| 30 | Negro de primer plano | Se aplica a primer plano el negro brillante y no en negrita |
| 31 | Rojo de primer plano | Se aplica rojo a primer plano que no sea de negrita o brillante |
| 32 | Verde de primer plano | Se aplica de verde a primer plano que no sea de negrita o brillante |
| 33 | Amarillo de primer plano | Se aplica al primer plano un amarillo brillante o no en negrita |
| 34 | Azul de primer plano | Se aplica a primer plano el azul brillante o no negrita |
| 35 | Magenta de primer plano | Se aplica a primer plano el magenta brillante o no en negrita |
| 36 | Aguamarina de primer plano | Se aplica al primer plano un cian brillante o no en negrita. |
| 37 | Blanco de primer plano | Se aplica a primer plano el blanco brillante o no negrita |
| 38 | Primer plano extendido | Aplica el valor de color extendido al primer plano (vea los detalles a continuación). |
| 39 | Valor predeterminado de primer plano | Aplica solo la parte de primer plano de los valores predeterminados (vea 0) |
| 40 | Fondo negro | Se aplica a fondo que no es de negrita o brillante |
| 41 | Rojo de fondo | Aplica rojo a fondo que no es de negrita o brillante |
| 42 | Verde de fondo | Se aplica a fondo que no es de negrita o brillante |
| 43 | Amarillo de fondo | Se aplica a fondo que no es de negrita o brillante |
| 44 | Azul de fondo | Se aplica al fondo de color azul brillante o no negrita |
| 45 | Magenta de fondo | Se aplica al fondo un magenta que no sea de negrita o brillante |
| 46 | Aguamarina de fondo | Se aplica el color aguamarina, no en negrita o brillante al fondo |
| 47 | Fondo blanco | Se aplica a fondo que no está en negrita o brillante |
| 48 | En segundo plano | Aplica el valor de color extendido al fondo (vea los detalles a continuación). |
| 49 | Valor predeterminado de fondo | Aplica solo la parte de fondo de los valores predeterminados (vea 0) |
| 90 | Negro de primer plano brillante | Aplica el negro de negrita o brillante al primer plano. |
| 91 | Rojo de primer plano brillante | Aplica el color rojo de negrita o brillante al primer plano. |
| 92 | Verde en primer plano brillante | Aplica el color verde de negrita o brillante al primer plano. |
| 93 | Amarillo de primer plano brillante | Aplica el color amarillo de negrita o brillante al primer plano |
| 94 | Azul de primer plano brillante | Aplica el color azul oscuro o brillante al primer plano |
| 95 | Magenta de primer plano brillante | Aplica el magenta de negrita o brillante al primer plano. |
| 96 | Aguamarina de primer plano brillante | Aplica el color aguamarina/aguamarina brillante al primer plano. |
| 97 | Blanco de primer plano brillante | Aplica negrita/blanco brillante al primer plano |
| 100 | Negro de fondo brillante | Aplica el negro de negrita o brillante al fondo |
| 101 | Rojo de fondo brillante | Aplica el color rojo de negrita o brillante al fondo |
| 102 | Verde de fondo brillante | Aplica el color verde de negrita o brillante al fondo |
| 103 | Amarillo de fondo brillante | Aplica el color amarillo de negrita o brillante al fondo |
| 104 | Azul de fondo brillante | Se aplica el color azul oscuro al fondo |
| 105 | Magenta de fondo brillante | Aplica el color magenta de negrita o brillante al fondo |
| 106 | Aguamarina de fondo brillante | Aplica el color aguamarina/aguamarina brillante al fondo |
| 107 | Blanco de fondo brillante | Aplica negrita/blanco brillante al fondo |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Colores extendidos

Algunos emuladores de terminal virtuales admiten una paleta de colores mayores que los 16 colores proporcionados por la consola de Windows. Para estos colores extendidos, la consola de Windows elegirá el color más cercano adecuado en la tabla de 16 colores existente para su presentación. A diferencia de los valores de SGR típicos anteriores, los valores extendidos consumirán parámetros adicionales después del indicador inicial según la tabla siguiente.


| Subsecuencia SGR | Description |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| 38; dos &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt; | Establecer el color de primer plano en el valor RGB especificado en &lt; &gt; &lt; los parámetros r, g &gt; , &lt; b &gt;\* |
| 48; dos &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt; | Establecer el color de fondo en el valor RGB especificado en &lt; &gt; &lt; los parámetros r, g &gt; , &lt; b &gt;\* |
| 38; 5 &lt;s&gt; | Establecer el color de primer plano &lt; &gt; en el índice de s en la tabla de colores 88 o 256\* |
| 48; 5 &lt;s&gt; | Establecer el color de fondo en el &lt; &gt; índice en la tabla de colores 88 o 256\* |



\*Las paletas de colores 88 y 256 que se mantienen internamente para la comparación se basan en el emulador de terminal de xterm. Las tablas de comparación o redondeo no se pueden modificar en este momento.


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Colores de pantalla


El siguiente comando permite que la aplicación establezca los valores de la paleta de colores de pantalla en cualquier valor RGB.

Los valores RGB deben ser valores hexadecimales entre `0` y y `ff` separados por el carácter de barra diagonal (por ejemplo, `rgb:1/24/86` ).

Tenga en cuenta que esta secuencia es una secuencia del "comando del sistema operativo" OSC y no un CSI como muchas de las otras secuencias enumeradas, y como tal comienza con " \\ X1b \] ", no con " \\ X1b \[ ".


| Secuencia | Descripción | Comportamiento |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| ESC \] 4; &lt; i &gt; ; RGB: &lt; r &gt;  /  &lt; g &gt;  /  &lt; b &gt; ESC | Modificar los colores de la pantalla | Establece el índice de paleta de &lt; colores &gt; de pantalla i en los valores RGB especificados en &lt; r &gt; , &lt; g &gt; , &lt; b&gt; |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Cambios de modo


Se trata de secuencias que controlan los modos de entrada. Hay dos conjuntos diferentes de modos de entrada, el modo de teclas de cursor y el modo de teclas del teclado. El modo de teclas de cursor controla las secuencias emitidas por las teclas de dirección, así como el inicio y el final, mientras que el modo de teclas del teclado controla las secuencias emitidas por las teclas en el teclado numérico principalmente, así como las teclas de función.

Cada uno de estos modos es una configuración booleana simple: el modo de teclas de cursor es normal (predeterminado) o aplicación, y el modo de teclas del teclado es numérico (predeterminado) o aplicación.

Vea las secciones teclas de cursor y teclado numérico & las de las secuencias emitidas en estos modos.


| Secuencia | Código | Descripción | Comportamiento |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| ESC = | DECKPAM | Habilitar el modo de aplicación de teclado | Las teclas del teclado emitirán sus secuencias en modo de aplicación. |
| ESC &gt; | DECKPNM | Habilitar el modo numérico del teclado | Las teclas del teclado emitirán sus secuencias en modo numérico. |
| \[¿ESC? 1 h | DECCKM | Habilitar el modo de aplicación de teclas de cursor | Las teclas del teclado emitirán sus secuencias en modo de aplicación. |
| \[¿ESC? 1 l | DECCKM | Deshabilitar el modo de aplicación de teclas de cursor (usar el modo normal) | Las teclas del teclado emitirán sus secuencias en modo numérico. |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Estado de la consulta


Todos los comandos de esta sección suelen ser equivalentes a llamar a get \* Console API para recuperar información de estado sobre el estado actual del búfer de la consola.

> [!NOTE]
>Estas consultas emitirán sus respuestas en el flujo de entrada de la consola inmediatamente después de que se reconozcan en el flujo de salida mientras \_ \_ se establece habilitar el procesamiento de terminal virtual \_ . El \_ indicador habilitar \_ entrada de terminal virtual \_ no se aplica a los comandos de consulta, ya que se supone que una aplicación que realiza la consulta siempre querrá recibir la respuesta.




| Secuencia | Código | Descripción | Comportamiento |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| ESC \[ 6 n | DECXCPR | Posición del cursor de informe | Emita la posición del cursor como: ESC \[ &lt; r &gt; ; &lt; c &gt; r donde &lt; R &gt; = cursor Row y &lt; c &gt; = columna cursor |
| ESC \[ 0 c | & | Atributos de dispositivo | Notificar la identidad del terminal. Emitirá " \\ X1b \[ ? 1; 0C", que indica "VT101 sin opciones". |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Columnas


Aunque la consola de Windows normalmente espera que las pestañas tengan exclusivamente ocho caracteres de ancho, \* las aplicaciones de Nix que usan ciertas secuencias pueden manipular dónde se detienen las tabulaciones en las ventanas de la consola para optimizar el movimiento del cursor por parte de la aplicación.

Las secuencias siguientes permiten a una aplicación establecer las ubicaciones de tabulación dentro de la ventana de la consola, quitarlas y desplazarse entre ellas.


| Secuencia | Código | Descripción | Comportamiento |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC H | HTS | Conjunto de pestañas horizontal | Establece un punto de tabulación en la columna actual en la que se encuentra el cursor. |
| ESC \[ &lt; n &gt; I | CHT | Cursor horizontal (hacia delante) | Avanzar el cursor hasta la columna siguiente (en la misma fila) con una tabulación. Si no hay más tabulaciones, desplácese a la última columna de la fila. Si el cursor está en la última columna, desplácese a la primera columna de la fila siguiente. |
| ESC \[ &lt; n &gt; Z | ORDENADOR | Tabulador hacia atrás de cursor | Mueve el cursor a la columna anterior (en la misma fila) con una tabulación. Si no hay más tabulaciones, mueve el cursor a la primera columna. Si el cursor está en la primera columna, no mueve el cursor. |
| ESC \[ 0 g | TBC | Borrado de tabulación (columna actual) | Borra la tabulación de la columna actual, si hay alguna. En caso contrario, no hace nada. |
| ESC \[ 3 g | TBC | Borrado de tabulación (todas las columnas) | Borra todas las tabulaciones establecidas actualmente. |



- En el caso de CHT y CBT, &lt; n &gt; es un parámetro opcional que (valor predeterminado = 1) que indica el número de veces que se debe avanzar el cursor en la dirección especificada.
- Si no se establece ninguna detención de tabulación a través de HTS, CHT y CBT tratarán la primera y la última columna de la ventana como las dos primeras tabulaciones.
- El uso de HTS para establecer una detención de tabulación también hará que la consola navegue hasta la siguiente detención de tabulación en el resultado de un carácter de TABULAción (0x09, ' \\ t '), de la misma manera que CHT.

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designación del juego de caracteres


Las secuencias siguientes permiten que un programa cambie la asignación del juego de caracteres activo. Esto permite que un programa emita caracteres ASCII de 7 bits, pero que se muestren como otros glifos en la pantalla del terminal. Actualmente, los únicos dos juegos de caracteres admitidos son ASCII (valor predeterminado) y el juego de caracteres de gráficos especiales DEC. Vea <http://vt100.net/docs/vt220-rm/table2-4.html> para obtener una lista de todos los caracteres representados por el juego de caracteres de gráficos especiales Dec.


| Secuencia | Descripción | Comportamiento |
|----------|--------------------------------------------|-------------------------------|
| ESC (0 | Designar juego de caracteres: DEC line Drawing | Habilita el modo de dibujo de línea DEC |
| ESC (B | Designar juego de caracteres: ASCII de EE. UU. | Habilita el modo ASCII (valor predeterminado) |



En particular, el modo de dibujo de línea DEC se usa para dibujar los bordes en las aplicaciones de consola. En la tabla siguiente se muestra qué caracteres ASCII se asignan al carácter de dibujo de línea.


| Hex | ASCII | Dibujo de línea DEC |
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


Las secuencias siguientes permiten a un programa configurar la "región de desplazamiento" de la pantalla que se ve afectada por las operaciones de desplazamiento. Este es un subconjunto de las filas que se ajustan cuando la pantalla se desplazaría de otro modo, por ejemplo, en una ' \\ n ' o RI. Estos márgenes también afectan a las filas modificadas por la inserción de línea (IL) y la línea de eliminación (DL), se desplazan hacia arriba (SU) y se desplazan hacia abajo (SD).

Los márgenes de desplazamiento pueden ser especialmente útiles para tener una parte de la pantalla que no se desplaza cuando se rellena el resto de la pantalla, como tener una barra de título en la parte superior o una barra de estado en la parte inferior de la aplicación.

En el caso de DECSTBM, hay dos parámetros opcionales, &lt; t &gt; y &lt; b &gt; , que se usan para especificar las filas que representan las líneas superior e inferior de la región de desplazamiento, ambos incluidos. Si se omiten los parámetros, el &lt; &gt; valor predeterminado de t es 1 y &lt; b se toma de &gt; forma predeterminada en el alto de la ventanilla actual.

Los márgenes de desplazamiento son por búfer, por lo que, lo que es importante, el búfer alternativo y el búfer principal mantienen configuraciones de márgenes de desplazamiento independientes (por lo que una aplicación de pantalla completa en el búfer alternativo no conseguirá los márgenes del búfer principal).


| Secuencia | Código | Descripción | Comportamiento |
|--------------------------------|---------|----------------------|------------------------------------------------|
| ESC \[ &lt; t &gt; ; &lt; b &gt; r | DECSTBM | Establecer región de desplazamiento | Establece los márgenes de desplazamiento de VT de la ventanilla. |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Título de ventana


Los siguientes comandos permiten que la aplicación establezca el título de la ventana de la consola en el &lt; parámetro de cadena especificado &gt; . La cadena debe tener menos de 255 caracteres para aceptar. Esto es equivalente a llamar a SetConsoleTitle con la cadena especificada.

Tenga en cuenta que estas secuencias son secuencias del OSC "comando del sistema operativo" y no un CSI como muchas de las otras secuencias enumeradas, y como tal comienza por " \\ X1b \] ", no por " \\ X1b \[ ".


| Secuencia | Descripción | Comportamiento |
|-------------------------------|---------------------------|----------------------------------------------------|
| ESC \] 0; &lt; cadena &gt; Bel | Establecer el título de la ventana y el icono | Establece el título de la ventana de la consola en &lt; cadena &gt; . |
| ESC \] 2; &lt; cadena &gt; Bel | Establecer el título de la ventana | Establece el título de la ventana de la consola en &lt; cadena &gt; . |



El carácter de terminación aquí es el carácter "campana", " \\ x07".

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Búfer de pantalla alternativo


\*Las aplicaciones de estilo Nix suelen utilizar un búfer de pantalla alternativo para que puedan modificar todo el contenido del búfer, sin que ello afecte a la aplicación que los inició. El búfer alternativo es exactamente las dimensiones de la ventana, sin ninguna región desplazamiento.

Para obtener un ejemplo de este comportamiento, tenga en cuenta Cuándo se inicia VIM desde bash. VIM usa el completo de la pantalla para editar el archivo y, a continuación, si se vuelve a bash, el búfer original no se modifica.


| Secuencia | Descripción | Comportamiento |
|--------------------|-----------------------------|--------------------------------------------|
| \[¿ESC? 1 0 4 9 h | Usar búfer de pantalla alternativo | Cambia a un nuevo búfer de pantalla alternativo. |
| \[¿ESC? 1 0 4 9 l | Usar búfer de pantalla principal | Cambia al búfer principal. |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Ancho de la ventana


Las secuencias siguientes se pueden usar para controlar el ancho de la ventana de la consola. Son aproximadamente equivalentes a la llamada a la API de la consola de SetConsoleScreenBufferInfoEx para establecer el ancho de la ventana.


| Secuencia | Código | Descripción | Comportamiento |
|--------------|---------|------------------------------|---------------------------------------------|
| \[¿ESC? 3 h | DECCOLM | Establecer el número de columnas en 132 | Establece el ancho de la consola en 132 columnas de ancho. |
| \[¿ESC? 3 l | DECCOLM | Establecer el número de columnas en 80 | Establece el ancho de la consola en 80 columnas de ancho. |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Restablecimiento parcial


La siguiente secuencia se puede usar para restablecer los valores predeterminados de algunas propiedades. Las siguientes propiedades se restablecen a los siguientes valores predeterminados (también se muestran las secuencias que controlan esas propiedades):

- Visibilidad del cursor: visible (DECTEM)
- Teclado numérico: modo numérico (DECNKM)
- Modo de teclas de cursor: modo normal (DECCKM)
- Márgenes superior e inferior: superior = 1, inferior = alto de la consola (DECSTBM)
- Juego de caracteres: ASCII de EE. UU.
- Representación de gráficos: predeterminada/desactivada (SGR)
- Guardar estado del cursor: posición inicial (0,0) (DECSC)


| Secuencia | Código | Descripción | Comportamiento |
|------------|--------|-------------|----------------------------------------------------|
| ESC \[ ! p | DECSTR | Restablecimiento parcial | Restablezca los valores predeterminados de ciertas opciones de terminal. |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Secuencias de entrada


El host de consola emite las siguientes secuencias de terminal en el flujo de entrada si el \_ \_ indicador de entrada habilitar terminal virtual \_ está establecido en el identificador de búfer de entrada mediante la marca SetConsoleMode.

Hay dos modos internos que controlan qué secuencias se emiten para las teclas de entrada dadas, el modo de teclas de cursor y el modo de teclas del teclado. Estos se describen en la sección cambios en el modo.

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Teclas de cursor


| Clave | Modo normal | Modo de aplicación |
|-------------|-------------|------------------|
| Flecha arriba | ESC \[ A | ESC O A |
| Flecha abajo | ESC \[ B | ESC O B |
| Flecha derecha | ESC \[ C | ESC O C |
| Flecha izquierda | ESC \[ D | ESC O D |
| Página principal | ESC \[ H | ESC O H |
| End | ESC \[ F | ESC O F |



Además, si se presiona Ctrl con cualquiera de estas teclas, se emiten las secuencias siguientes en su lugar, independientemente del modo de teclas de cursor:


| Clave | Cualquier modo |
|--------------------|----------------|
| Ctrl + flecha arriba | ESC \[ 1; 5 A |
| Ctrl + flecha abajo | ESC \[ 1; 5 B |
| Ctrl + flecha derecha | ESC \[ 1; 5 C |
| Ctrl + flecha izquierda | ESC \[ 1; 5 D |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Teclas de función de & de teclado


| Clave | Secuencia |
|-----------|--------------|
| Retroceso | 0x7F (DEL) |
| Pausar | 0x1A (SUB) |
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

Alt se trata al prefijar la secuencia con un escape: ESC &lt; c, &gt; donde &lt; c &gt; es el carácter que pasa el sistema operativo. Alt + Ctrl se administra de la misma manera, salvo que el sistema operativo habrá desplazado la &lt; &gt; tecla c al carácter de control adecuado, que se retransmitirá a la aplicación.

Ctrl suele pasar exactamente como se recibe del sistema. Suele ser un carácter único desplazado hacia abajo en el espacio reservado de carácter de control (0X0-0x1F). Por ejemplo, Ctrl + @ (0x40) se convierte en NUL (0x00), Ctrl + \[ (0x5b) se convierte en ESC (0x1b), etc. Algunas combinaciones de teclas Ctrl se tratan de forma especial según la tabla siguiente:


| Clave | Secuencia |
|--------------------|----------------|
| Ctrl + Espacio | 0x00 (NUL) |
| Ctrl + flecha arriba | ESC \[ 1; 5 A |
| Ctrl + flecha abajo | ESC \[ 1; 5 B |
| Ctrl + flecha derecha | ESC \[ 1; 5 C |
| Ctrl + flecha izquierda | ESC \[ 1; 5 D |



> [!NOTE]
>Left <kbd>Ctrl</kbd> + derecha <kbd>Alt</kbd> se trata como altgr. Cuando ambos se ven juntos, se eliminarán y el valor Unicode del carácter presentado por el sistema se pasará al destino. El sistema traducirá previamente los valores de AltGr según la configuración de entrada del sistema actual.



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Assembl


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span id="example"></span><span id="EXAMPLE"></span>Ejemplo de secuencias terminales de SGR

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
>En el ejemplo anterior, la cadena ' `\x1b[31m` ' es la implementación de **Esc \[ &lt; n &gt; m** con &lt; n &gt; siendo 31.



En el gráfico siguiente se muestra la salida del ejemplo de código anterior.

![salida de la consola con el comando SGR](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Ejemplo de cómo habilitar el procesamiento de terminal virtual

El código siguiente proporciona un ejemplo de la manera recomendada de habilitar el procesamiento de terminal virtual para una aplicación. El propósito del ejemplo es mostrar:

1. El modo existente siempre debe recuperarse a través de GetConsoleMode y analizarse antes de establecerse con SetConsoleMode.

2. Comprobando si SetConsoleMode devuelve `0` y GetLastError devuelve \_ \_ el estado el parámetro no válido es el mecanismo actual para determinar cuándo se ejecuta en un sistema de nivel inferior. Un \_ parámetro no válido de estado de recepción de \_ la aplicación con una de las marcas de modo de consola más recientes del campo de bits debe degradar el comportamiento correctamente e intentarlo de nuevo.

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

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Ejemplo de características de selección de actualización de aniversario

El ejemplo siguiente pretende ser un ejemplo más sólido de código que usa una variedad de secuencias de escape para manipular el búfer, con énfasis en las características agregadas en la actualización de aniversario para Windows 10.

En este ejemplo se usa el búfer de pantalla alternativo, se manipulan las tabulaciones, se establecen los márgenes de desplazamiento y se cambia el juego de caracteres.

```C
//
// Copyright (C) Microsoft. All rights reserved.
//
#define DEFINE_CONSOLEV2_PROPERTIES

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
 printf(fIsTop? "l" : "m"); // print left corner 

 for (int i = 1; i < Size.X - 1; i++) 
 printf("q"); // in line drawing mode, \x71 -> \u2500 "HORIZONTAL SCAN LINE-5"

 printf(fIsTop? "k" : "j"); // print right corner
 printf(CSI "0m");
 printf(ESC "(B"); // exit line drawing mode
}

void PrintStatusLine(char* const pszMessage, COORD const Size)
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
 printf(CSI "3;%dr", Size.Y-2);
 int iNumLines = Size.Y - 4;

 printf(CSI "1;1H");
 printf(CSI "102;30m");
 printf("Windows 10 Anniversary Update - VT Example"); 
 printf(CSI "0m");

 // Print a top border - Yellow
 printf(CSI "2;1H");
 PrintHorizontalBorder(Size, true);

 // // Print a bottom border
 printf(CSI "%d;1H", Size.Y-1);
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
 for (tab = 0; tab < iNumTabStops-1; tab++)
 {
 PrintVerticalBorder();
 printf("line=%d", line);
 printf("\t"); // advance to next tab stop
 }
 PrintVerticalBorder();// print border at right side
 if (line+1 != iNumLines)
 printf("\t"); // advance to next tab stop, (on the next line)
 }

 PrintStatusLine("Press any key to demonstrate scroll margins", Size);
 wch = _getwch();

 printf(CSI "3;1H"); 
 for (line = 0; line < iNumLines * 2; line++)
 {
 printf(CSI "K"); // clear the line
 int tab = 0;
 for (tab = 0; tab < iNumTabStops-1; tab++)
 {
 PrintVerticalBorder();
 printf("line=%d", line);
 printf("\t"); // advance to next tab stop
 }
 PrintVerticalBorder(); // print border at right side
 if (line+1 != iNumLines * 2)
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








