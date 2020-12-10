---
title: API de consola clásica frente a secuencias de terminal virtuales
description: Describe el contraste entre la superficie de API de consola Win32 clásica y el concepto de secuencias de terminal virtual, a veces denominadas secuencias de escape, para escribir aplicaciones de línea de comandos.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, terminal, terminal virtual, secuencias de escape, VT, VT100, API de consola
ms.prod: console
ms.localizationpriority: high
ms.openlocfilehash: 541300b50521909b22ceaccb595f1945fbfc7e6d
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420184"
---
# <a name="classic-console-apis-versus-virtual-terminal-sequences"></a>API de consola clásica frente a secuencias de terminal virtuales

Nuestra recomendación es reemplazar la **API de consola de Windows** por **secuencias de terminal virtual**. En este artículo se indica la diferencia entre los dos conceptos y se describen los motivos de nuestra recomendación.

## <a name="definitions"></a>Definiciones

La superficie de **[API de consola de Windows](console-functions.md)** clásica se define como la serie de interfaces funcionales de lenguaje C de `kernel32.dll` que incluyen "Console" en el nombre.

Las **[secuencias de terminal virtual](console-virtual-terminal-sequences.md)** se definen como un lenguaje de comandos que está incrustado en los flujos de entrada y salida estándar. Las secuencias de terminal virtual usan caracteres de escape no imprimibles para los comandos de señal intercalados con texto imprimible normal.

## <a name="history"></a>Historial

La **consola de Windows** proporciona una superficie de API amplia para que las aplicaciones cliente de línea de comandos manipulen el búfer de visualización de la salida y el búfer de entrada del usuario. Sin embargo, otras plataformas que no son de Windows nunca han ofrecido este enfoque específico controlado por API a sus entornos de línea de comandos, eligiendo en su lugar usar secuencias de terminal virtual incrustadas en los flujos de entrada y salida estándar. *(Durante un tiempo, Microsoft también admitió este comportamiento en las primeras ediciones de DOS y Windows a través de un controlador denominado ANSI.SYS).*

Por el contrario, las **secuencias de terminal virtual** (en una variedad de dialectos) controlan las operaciones del entorno de línea de comandos para todas las demás plataformas. Estas secuencias se basan en un [estándar de ECMA](https://www.ecma-international.org/publications/standards/Ecma-048.htm) y una serie de extensiones de muchos proveedores que se pueden rastrear hasta terminales de Digital Equipment Corporation y Tektronix y hasta terminales de software más modernos y comunes, como [xterm](https://invisible-island.net/xterm/). Existen muchas extensiones en el dominio de la secuencia de terminales virtual, y algunas secuencias se admiten más ampliamente que otras, pero se puede afirmar con seguridad que se ha estandarizado mundialmente como el lenguaje de comandos para las experiencias de línea de comandos con un subconjunto conocido que es compatible prácticamente con todos los terminales y aplicaciones cliente de línea de comandos.

## <a name="cross-platform-support"></a>Compatibilidad entre plataformas

Las **secuencias de terminal virtual** se admiten de forma nativa entre plataformas, por lo que las aplicaciones de terminal y las utilidades de línea de comandos se pueden transferir fácilmente entre versiones y variaciones de los sistemas operativos, a excepción de Windows.

Por el contrario, las **API de consola de Windows** solo se admiten en Windows. Se debe escribir una amplia biblioteca de adaptadores o de traducción entre Windows y el terminal virtual, o viceversa, al intentar transferir las utilidades de línea de comandos de una plataforma a otra.

### <a name="remote-access"></a>Acceso remoto

Las **secuencias de terminal virtual** tienen una ventaja importante para el acceso remoto. No requieren ningún trabajo adicional para el transporte, ni se deben realizar llamadas a procedimientos remotos, aparte de lo que es necesario para configurar una conexión de línea de comandos remota estándar. La simple conexión de un canal de transporte de entrada y de salida (o un canal bidireccional único) a través de una canalización, un socket, un archivo, un puerto serie o cualquier otro dispositivo es suficiente para transferir por completo toda la información necesaria para que una aplicación transfiera estas secuencias a un host remoto.

Por el contrario, las **API de consola de Windows** solo son accesibles en el equipo local y todos los intentos de usarlas de forma remota requerirán la creación de una capa de interfaz completa de llamada remota y transporte, más allá de un simple canal.

### <a name="separation-of-concerns"></a>Separación de intereses

Algunas **API de consola de Windows** proporcionan acceso de bajo nivel a los búferes de entrada y salida o a las funciones adecuadas para las líneas de comandos interactivas. Esto puede incluir los alias y el historial de comandos programados en el subsistema de consola y el entorno de host, en lugar de en la propia aplicación cliente de línea de comandos.

Por el contrario, **otras plataformas** hacen que la memoria del estado actual de la aplicación y la funcionalidad adecuada sean responsabilidad de la utilidad de línea de comandos o el propio shell.

La manera en que la **consola de Windows** controla esta responsabilidad en el host de la consola y la API hace que sea más fácil y rápido escribir una aplicación de línea de comandos con estas características, ya que elimina la responsabilidad de recordar el estado del dibujo o de controlar las características adecuadas para la edición. Sin embargo, esto hace que sea casi imposible conectar estas actividades de forma remota entre plataformas, versiones o escenarios debido a las variaciones en las implementaciones y la disponibilidad. Esta manera de controlar la responsabilidad también hace que la experiencia interactiva final de estas aplicaciones de línea de comandos de Windows dependa completamente de la implementación, las prioridades y el ciclo de lanzamiento del host de consola.

Por ejemplo, las características avanzadas de edición de líneas, como el resaltado de la sintaxis y la selección compleja, solo son posibles cuando una aplicación de línea de comandos controla por sí misma los problemas de edición. La consola nunca puede tener suficiente contexto como para comprender por completo estos escenarios de una manera amplia, a diferencia de la aplicación cliente.

Por el contrario, otras plataformas usan **secuencias de terminal virtual** para controlar estas actividades y la comunicación de terminal virtual a través de bibliotecas de cliente reutilizables, como [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) y [ncurses](https://invisible-island.net/ncurses/ncurses.html). El terminal final solo es responsable de mostrar la información y recibir la entrada a través de ese canal de comunicación bidireccional.

### <a name="wrong-way-verbs"></a>Verbos con dirección incorrecta

Con la **consola de Windows**, algunas acciones se pueden realizar en la dirección opuesta a la natural en los flujos de entrada y salida. Esto permite a las aplicaciones de línea de comandos de Windows evitar el problema de administrar sus propios búferes. También permite que las aplicaciones de línea de comandos de Windows realicen operaciones avanzadas, como la simulación o inserción de entrada en nombre de un usuario, o la lectura de parte del historial de lo que se ha escrito.

Aunque esto proporciona una capacidad adicional para las aplicaciones de Windows que funcionan en un contexto de usuario específico en una sola máquina, también proporciona un vector para la seguridad cruzada y los niveles de privilegios o dominios cuando se usa en determinados escenarios. Estos escenarios incluyen el funcionamiento entre contextos de la misma máquina o entre contextos de otra máquina o entorno.

Otras plataformas, que usan **secuencias de terminal virtual**, no permiten esta actividad. La intención de nuestra recomendación de pasar de la consola de Windows clásica a las secuencias de terminal virtual es converger con esta estrategia por motivos de interoperabilidad y seguridad.

### <a name="direct-window-access"></a>Acceso directo a ventanas

La **superficie de API de consola de Windows** proporciona el identificador de ventana exacto para la ventana de hospedaje. Esto permite que una utilidad de línea de comandos realice operaciones avanzadas de ventana ya que llega a la amplia gama de API de Win32 permitidas en un identificador de ventana. Estas API de Win32 pueden manipular el estado de la ventana, el marco, el icono u otras propiedades de la ventana.

Por el contrario, en otras plataformas con **secuencias de terminal virtual**, existe un conjunto reducido de comandos que se pueden ejecutar en la ventana. Estos comandos pueden realizar acciones como cambiar el tamaño de la ventana o el título que se muestra, pero deben realizarse en la misma banda y bajo el mismo control que el resto del flujo.

A medida que Windows ha ido evolucionando, los controles de seguridad y las restricciones sobre los identificadores de ventana han aumentado. Además, la naturaleza y la existencia de un identificador de ventana direccionable por la aplicación en cualquier elemento específico de la interfaz de usuario ha evolucionado, especialmente con la mayor compatibilidad de los factores de forma y las plataformas de los dispositivos. Esto hace que el acceso directo a las ventanas en las aplicaciones de línea de comandos sea frágil a medida que la plataforma y las experiencias evolucionan.

### <a name="unicode"></a>Unicode

UTF-8 es la codificación aceptada para los datos Unicode en casi todas las plataformas modernas, ya que consigue el equilibrio adecuado entre la portabilidad, el tamaño de almacenamiento y el tiempo de procesamiento. Sin embargo, Windows ha elegido históricamente UTF-16 como la codificación principal para los datos Unicode. La compatibilidad con UTF-8 está aumentando en Windows y el uso de estos formatos Unicode no impide el uso de otras codificaciones.

La plataforma de la **consola de Windows** es compatible y seguirá siéndolo con todas las páginas de códigos y codificaciones existentes. Use UTF-16 para obtener la máxima compatibilidad entre versiones de Windows y realice la traducción algorítmica con UTF-8 si es necesario. Se está incluyendo una mayor compatibilidad con UTF-8 para el sistema de consola.

La compatibilidad con UTF-16 en la consola se puede utilizar sin ninguna configuración adicional a través de la variante _W_ de todas las API de consola y es una opción más probable para las aplicaciones que ya se han incorporado en UTF-16 a través de la comunicación con `wchar_t` y la variante _W_ de otras funciones y productos de la plataforma de Microsoft y Windows.

La compatibilidad con UTF-8 en la consola se puede utilizar a través de la variante _A_ de las API de consola en los identificadores de consola después de establecer la página de códigos en `65001` o `CP_UTF8` con los métodos [**SetConsoleOutputCP**](setconsoleoutputcp.md) y [**SetConsoleCP**](setconsolecp.md), según corresponda. Solo es necesario establecer las páginas de códigos de antemano si la máquina no ha elegido "Use Unicode UTF-8 for worldwide language support" (Usar Unicode UTF-8 para compatibilidad con idiomas en todo el mundo) en la configuración de aplicaciones no Unicode de la sección Región del Panel de control.

>[!NOTE]
> A partir de ahora, UTF-8 se admite totalmente en el flujo de salida estándar con los métodos [**WriteConsole**](writeconsole.md) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747). La compatibilidad con el flujo de entrada varía en función del modo de entrada y continuará mejorando con el tiempo. En particular, los modos **["cocinados"](high-level-console-modes.md)** en la entrada no son totalmente compatibles con UTF-8. El estado actual de este trabajo se puede encontrar en [**microsoft/terminal#7777**](https://github.com/microsoft/terminal/issues/7777) en GitHub. La solución consiste en usar UTF-16 traducible mediante algoritmo para leer la entrada a través de [**ReadConsoleW**](readconsole.md) o [**ReadConsoleInputW**](readconsoleinput.md) hasta que se resuelvan los problemas pendientes.

## <a name="recommendations"></a>Recomendaciones

Para todo el desarrollo nuevo y en curso en Windows, **se recomiendan las secuencias de terminal virtual** como la manera de interactuar con el terminal. Esto hará que las aplicaciones cliente de línea de comandos de Windows converjan con el estilo de programación de aplicaciones en todas las demás plataformas.

### <a name="exceptions-for-using-windows-console-apis"></a>Excepciones para usar las API de consola de Windows

**Sigue siendo necesario un subconjunto limitado de API de consola de Windows** para establecer el entorno inicial. La plataforma de Windows todavía difiere de otras en el control del proceso, la señal, el dispositivo y la codificación:

- Los identificadores estándar de un proceso se seguirán controlando con **[GetStdHandle](getstdhandle.md)** y **[SetStdHandle](setstdhandle.md)** .

- La configuración de los modos de la consola en un identificador para lograr la compatibilidad con la secuencia de terminal virtual se administrará con **[GetConsoleMode](getconsolemode.md)** y **[SetConsoleMode](setconsolemode.md)** .

- La declaración de compatibilidad con la página de códigos o UTF-8 se lleva a cabo con [**SetConsoleOutputCP**](setconsoleoutputcp.md) y [**SetConsoleCP**](setconsolecp.md).

- Es posible que se necesite cierto nivel de administración general del proceso con [**AllocConsole**](allocconsole.md), [**AttachConsole**](attachconsole.md) y [**FreeConsole**](freeconsole.md) para unirse a una sesión de dispositivo de consola o salir de ella.

- Las señales y el control de señales se seguirán llevando a cabo con [**SetConsoleCtrlHandler**](setconsolectrlhandler.md), [**HandlerRoutine**](handlerroutine.md) y [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md).

- La comunicación con los identificadores del dispositivo de consola se puede llevar a cabo con [**WriteConsole**](writeconsole.md) y [**ReadConsole**](readconsole.md). También se pueden aprovechar a través de los tiempos de ejecución del lenguaje de programación en los formatos: -C Runtime (CRT): [E/S de flujo](https://docs.microsoft.com/cpp/c-runtime-library/stream-i-o) como **printf**, **scanf**, **putc**, **getc** u [otros niveles de funciones de E/S](https://docs.microsoft.com/cpp/c-runtime-library/input-and-output).
        - Biblioteca estándar de C++ (STL): [iostream](https://docs.microsoft.com/cpp/standard-library/iostream) como **cout** y **cin**.
        - Entorno de ejecución .NET: [System.Console](https://docs.microsoft.com/dotnet/api/system.console) como **Console.WriteLine**.

- Las aplicaciones que deben tener en cuenta los cambios de tamaño de ventana deberán seguir usando [**ReadConsoleInput**](readconsoleinput.md) para recibirlos intercalados con los eventos clave, ya que **ReadConsole** solo los descartará.

- La búsqueda del tamaño de la ventana se debe seguir realizando con [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) para las aplicaciones que intentan dibujar columnas, cuadrículas o rellenar la pantalla. El tamaño de ventana y búfer coincidirán en una sesión de [pseudoconsola](pseudoconsoles.md).

## <a name="future-planning-and-pseudoconsole"></a>Planeación futura y pseudoconsola

No hay planes para quitar las API de consola de Windows de la plataforma.

Por el contrario, el host de la consola de Windows ha proporcionado la tecnología de **[pseudoconsola](pseudoconsoles.md)** para traducir las llamadas existentes de la aplicación de línea de comandos de Windows en secuencias de terminal virtual y reenviarlas a otro entorno de hospedaje de forma remota o entre plataformas.

Esta traducción no es perfecta. Requiere que la ventana del host de la consola mantenga un entorno simulado de lo que Windows habría mostrado al usuario. A continuación, proyecta una réplica de este entorno simulado en el host de **pseudoconsola**. Todas las llamadas a la API de consola de Windows funcionan en el entorno simulado para satisfacer las necesidades de la aplicación cliente de línea de comandos heredada. Solo los efectos se propagan al host final.

Por lo tanto, se recomienda que una aplicación de línea de comandos que desee compatibilidad completa entre plataformas y el soporte técnico completo de todas las características y escenarios nuevos en Windows y en otros sitios, se migre a las secuencias de terminal virtual y ajuste la arquitectura de las aplicaciones de línea de comandos para que se alineen con todas las plataformas.

Puede encontrar más información sobre esta transición de Windows para las aplicaciones de línea de comandos en nuestro [mapa de ruta del ecosistema](ecosystem-roadmap.md).
