---
title: API de consola clásica frente a secuencias de terminal virtuales
description: Describe el contraste entre la superficie clásica de la API de la consola Win32 y el concepto de secuencias de terminal virtuales, a veces denominados secuencias de escape, para escribir aplicaciones de línea de comandos.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, terminal, terminal virtual, secuencias de escape, VT, VT100, API de consola
ms.prod: console
ms.localizationpriority: high
ms.openlocfilehash: 541300b50521909b22ceaccb595f1945fbfc7e6d
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420184"
---
# <a name="classic-console-apis-versus-virtual-terminal-sequences"></a>API de consola clásica frente a secuencias de terminal virtuales

Nuestra recomendación es reemplazar la API clásica de la **consola de Windows** con **secuencias de terminal virtuales**. En este artículo se describe la diferencia entre los dos y se describen las razones de nuestra recomendación.

## <a name="definitions"></a>Definiciones

La superficie de la API de la consola clásica de **[Windows](console-functions.md)** se define como la serie de interfaces funcionales del lenguaje C en `kernel32.dll` con "Console" en el nombre.

Las **[secuencias de terminal virtuales](console-virtual-terminal-sequences.md)** se definen como un lenguaje de comandos que está incrustado en los flujos de entrada y salida estándar. Las secuencias de terminal virtuales usan caracteres de escape no imprimibles para los comandos de señal intercalados con texto imprimible normal.

## <a name="history"></a>Historial

La **consola de Windows** proporciona una amplia superficie de API para que las aplicaciones de línea de comandos de cliente manipulen el búfer de presentación de salida y el búfer de entrada del usuario. Sin embargo, otras plataformas que no son de Windows nunca han ofrecido este enfoque específico basado en API a sus entornos de línea de comandos, eligiendo en su lugar usar secuencias de terminal virtuales incrustadas en los flujos de entrada y salida estándar. *(Durante un tiempo, Microsoft admite este comportamiento también en las ediciones tempranas de DOS y Windows a través de un controlador denominado ANSI.SYS).*

Por el contrario, las **secuencias de terminal virtuales** (en una variedad de dialectos) controlan las operaciones de entorno de línea de comandos para todas las demás plataformas. Estas secuencias están arraigadas en un [estándar de ECMA](https://www.ecma-international.org/publications/standards/Ecma-048.htm) y una serie de extensiones por parte de muchos proveedores que vuelven a realizar el seguimiento a Digital Equipment Corporation y a los terminales de Tektronix, a través de los terminales de software más moderno y común, como [xterm](https://invisible-island.net/xterm/). Existen muchas extensiones en el dominio de la secuencia de terminales virtuales y algunas secuencias se admiten más ampliamente que otras, pero es seguro decir que el mundo ha estandarizado esto como el lenguaje de comandos para las experiencias de línea de comandos con un subconjunto conocido que es compatible prácticamente con cada terminal y aplicación cliente de línea de comandos.

## <a name="cross-platform-support"></a>Compatibilidad entre plataformas

Las **secuencias de terminal virtuales** se admiten de forma nativa en todas las plataformas, por lo que las aplicaciones de terminal y las utilidades de línea de comandos se pueden portable fácilmente entre las versiones y las variaciones de los sistemas operativos, con la excepción de Windows.

Por el contrario, las API de la **consola de Windows** solo se admiten en Windows. Se debe escribir una amplia biblioteca de adaptadores o de traducción entre Windows y terminal virtual, o viceversa, al intentar migrar las utilidades de línea de comandos de una plataforma o de otra.

### <a name="remote-access"></a>Acceso remoto

Las **secuencias de terminal virtuales** tienen una ventaja importante para el acceso remoto. No requieren ningún trabajo adicional para el transporte, ni realizan llamadas a procedimientos remotos, a través de lo que se necesita para configurar una conexión de línea de comandos remota estándar. Simplemente la conexión de un canal de transporte de entrada y de salida (o un canal bidireccional único) a través de una canalización, un socket, un archivo, un puerto serie o cualquier otro dispositivo es suficiente para llevar por completo toda la información necesaria para que una aplicación hable de estas secuencias a un host remoto.

Por el contrario, las **API** de la consola de Windows solo se han accesible en el equipo local y todos los esfuerzos para conversiones remotas requieren la creación de una capa de interfaz de transporte y de llamadas remotas completa más allá de un canal simple.

### <a name="separation-of-concerns"></a>Separación de intereses

Algunas **API** de la consola de Windows proporcionan acceso de bajo nivel a los búferes de entrada y salida o a las funciones de comodidad para las líneas de comandos interactivas. Esto podría incluir alias y el historial de comandos programados en el subsistema de consola y el entorno de host, en lugar de en la propia aplicación cliente de línea de comandos.

Por el contrario, **otras plataformas** hacen que la memoria del estado actual de la aplicación y la funcionalidad de comodidad sean responsabilidad del propio shell o la utilidad de línea de comandos.

La **consola de Windows** para controlar esta responsabilidad en el host y la API de la consola facilita y facilita la escritura de una aplicación de línea de comandos con estas características, lo que elimina la responsabilidad de recordar el estado del dibujo o de controlar las características prácticas de edición. Sin embargo, esto hace que sea casi imposible conectar las actividades de forma remota entre plataformas, versiones o escenarios debido a las variaciones en las implementaciones y la disponibilidad. Esta manera de controlar la responsabilidad también hace que la experiencia interactiva final de estas aplicaciones de línea de comandos de Windows dependa completamente de la implementación, las prioridades y el ciclo de lanzamiento del host de consola.

Por ejemplo, las características de edición de línea avanzadas, como el resaltado de sintaxis y la selección compleja, solo son posibles cuando una aplicación de línea de comandos controla los problemas de edición. La consola nunca puede tener un contexto suficiente para comprender perfectamente estos escenarios de una manera amplia como la aplicación cliente.

Por el contrario, otras plataformas utilizan **secuencias de terminal virtuales** para controlar estas actividades y la comunicación de terminal virtual a través de bibliotecas de cliente reutilizables, como [ReadLine](https://tiswww.case.edu/php/chet/readline/rltop.html) y [ncurses](https://invisible-island.net/ncurses/ncurses.html). El terminal final solo es responsable de mostrar la información y recibir la entrada a través de ese canal de comunicación bidireccional.

### <a name="wrong-way-verbs"></a>Wrong-Way verbos)

Con la **consola de Windows**, algunas acciones se pueden realizar en la dirección opuesta a la natural en los flujos de entrada y salida. Esto permite a las aplicaciones de línea de comandos de Windows evitar el problema de administrar sus propios búferes. También permite que las aplicaciones de línea de comandos de Windows realicen operaciones avanzadas, como la simulación o inserción de entrada en nombre de un usuario, o la lectura de parte del historial de lo que se ha escrito.

Aunque esto proporciona una capacidad adicional para las aplicaciones de Windows que funcionan en un contexto de usuario específico en un solo equipo, también proporciona un vector para la seguridad cruzada y los niveles de privilegios o dominios cuando se usa en determinados escenarios. Estos escenarios incluyen el funcionamiento entre los contextos en el mismo equipo o entre los contextos y otro equipo o entorno.

Otras plataformas, que usan **secuencias de terminales virtuales**, no permiten esta actividad. La intención de nuestra recomendación de pasar de la consola clásica de Windows a las secuencias de terminal virtuales es converger con esta estrategia por motivos de interoperabilidad y seguridad.

### <a name="direct-window-access"></a>Acceso directo a ventanas

La superficie de la API de la **consola de Windows** proporciona el identificador de ventana exacto para la ventana de hospedaje. Esto permite que una utilidad de línea de comandos realice operaciones de ventana avanzadas al llegar a la amplia gama de API de Win32 permitidas en un identificador de ventana. Estas API de Win32 pueden manipular el estado de la ventana, el marco, el icono u otras propiedades de la ventana.

Por el contrario, en otras plataformas con **secuencias de terminal virtuales**, hay un conjunto estrecho de comandos que se pueden realizar en la ventana. Estos comandos pueden hacer cosas como cambiar el tamaño de la ventana o el título que se muestra, pero deben realizarse en la misma banda y bajo el mismo control que el resto de la secuencia.

A medida que Windows ha evolucionado, los controles de seguridad y las restricciones en los identificadores de ventana han aumentado. Además, la naturaleza y la existencia de un identificador de ventana direccionable por la aplicación en cualquier elemento de interfaz de usuario específico ha evolucionado, especialmente con la mayor compatibilidad de los factores de forma y las plataformas de los dispositivos. Esto hace que el acceso directo a las ventanas en las aplicaciones de línea de comandos sea frágil a medida que la plataforma y las experiencias evolucionen.

### <a name="unicode"></a>Unicode

UTF-8 es la codificación aceptada para los datos Unicode en casi todas las plataformas modernas, ya que consigue un equilibrio adecuado entre la portabilidad, el tamaño de almacenamiento y el tiempo de procesamiento. Sin embargo, Windows históricamente eligió UTF-16 como la codificación principal para los datos Unicode. La compatibilidad con UTF-8 está aumentando en Windows y el uso de estos formatos Unicode no impide el uso de otras codificaciones.

La plataforma de la **consola de Windows** admite y seguirá admitiendo todas las páginas de códigos y codificaciones existentes. Use UTF-16 para obtener la máxima compatibilidad entre las versiones de Windows y realizar la traducción algorítmica con UTF-8 si es necesario. La mayor compatibilidad con UTF-8 está en curso para el sistema de consola.

La compatibilidad con UTF-16 en la consola de se puede utilizar sin ninguna configuración adicional a través de la variante _W_ de todas las API de consola y es una opción más probable para las aplicaciones que ya se han usado en UTF-16 a través de la comunicación con la `wchar_t` variante y _W_ de otras funciones y productos de la plataforma de Microsoft y Windows.

La compatibilidad con UTF-8 en la consola de se puede utilizar a través de _una_ variante de las API de consola en los identificadores de consola después de establecer la página de códigos en `65001` o `CP_UTF8` con los métodos [**SetConsoleOutputCP**](setconsoleoutputcp.md) y [**SetConsoleCP**](setconsolecp.md) , según corresponda. Establecer las páginas de códigos de antemano solo es necesario si la máquina no ha elegido "usar UTF-8 de Unicode para la compatibilidad con idiomas en todo el mundo" en la sección configuración de aplicaciones no Unicode en la región del panel de control.

>[!NOTE]
> A partir de ahora, UTF-8 se admite totalmente en el flujo de salida estándar con los métodos [**WriteConsole**](writeconsole.md) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) . La compatibilidad en el flujo de entrada varía en función del modo de entrada y continuará mejorando con el tiempo. En concreto, los modos **["cocidos"](high-level-console-modes.md)** predeterminados en la entrada no son totalmente compatibles con UTF-8. El estado actual de este trabajo se puede encontrar en [**Microsoft/Terminal # South Cone**](https://github.com/microsoft/terminal/issues/7777) en github. La solución consiste en usar UTF-16 con algoritmo traducible para leer la entrada a través de [**ReadConsoleW**](readconsole.md) o [**ReadConsoleInputW**](readconsoleinput.md) hasta que se resuelvan los problemas pendientes.

## <a name="recommendations"></a>Recomendaciones

Para el desarrollo nuevo y continuo en Windows, **se recomiendan las secuencias de terminal virtuales** como la manera de interactuar con el terminal. Esto hará que las aplicaciones cliente de línea de comandos de Windows se converjan con el estilo de programación de aplicaciones en todas las demás plataformas.

### <a name="exceptions-for-using-windows-console-apis"></a>Excepciones para usar las API de la consola de Windows

**Todavía es necesario un subconjunto limitado de las API de la consola de Windows** para establecer el entorno inicial. La plataforma de Windows todavía difiere de la de otros modos de procesamiento, señalización, dispositivo y codificación:

- Los identificadores estándar de un proceso se seguirán controlando con **[GetStdHandle](getstdhandle.md)** y **[SetStdHandle](setstdhandle.md)**.

- La configuración de los modos de consola en un identificador para participar en la compatibilidad con la secuencia de terminal virtual se administrará con **[GetConsoleMode](getconsolemode.md)** y **[SetConsoleMode](setconsolemode.md)**.

- La declaración de la compatibilidad con UTF-8 o la página de códigos se realiza con los métodos [**SetConsoleOutputCP**](setconsoleoutputcp.md) y [**SetConsoleCP**](setconsolecp.md) .

- Es posible que se necesite cierto nivel de administración de procesos general con [**AllocConsole**](allocconsole.md), [**AttachConsole**](attachconsole.md) y [**FreeConsole**](freeconsole.md) para unirse a una sesión de dispositivo de consola o salir de ella.

- Las señales y el control de señales se seguirán llevando a cabo con [**SetConsoleCtrlHandler**](setconsolectrlhandler.md), [**HandlerRoutine**](handlerroutine.md)y [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md).

- La comunicación con los identificadores de dispositivo de la consola se puede llevar a cabo con [**WriteConsole**](writeconsole.md) y [**ReadConsole**](readconsole.md). También se pueden aprovechar a través de los tiempos de ejecución del lenguaje de programación en los formatos:-C Runtime (CRT): [e/s de secuencia](https://docs.microsoft.com/cpp/c-runtime-library/stream-i-o) como **printf**, **scanf**, **putc**, **GETC** u [otros niveles de funciones de e/s](https://docs.microsoft.com/cpp/c-runtime-library/input-and-output).
        -Biblioteca estándar de C++ (STL): [iostream](https://docs.microsoft.com/cpp/standard-library/iostream) como **cout** y **CIN**.
        -.NET Runtime: [System. Console](https://docs.microsoft.com/dotnet/api/system.console) como **Console. WriteLine**.

- Las aplicaciones que deben tener en cuenta los cambios de tamaño de la ventana deben seguir usando [**ReadConsoleInput**](readconsoleinput.md) para recibirlos intercalados con eventos clave, ya que **ReadConsole** solo los descartará.

- La búsqueda del tamaño de la ventana todavía debe realizarse con [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) para las aplicaciones que intentan dibujar columnas, cuadrículas o rellenar la pantalla. La ventana y el tamaño de búfer coincidirán en una sesión de [pseudoconsole](pseudoconsoles.md) .

## <a name="future-planning-and-pseudoconsole"></a>Planeación y pseudoconsole futuros

No hay planes para quitar las API de la consola de Windows de la plataforma.

Por el contrario, el host de la consola de Windows ha proporcionado la tecnología **[pseudoconsole](pseudoconsoles.md)** para traducir las llamadas existentes de la aplicación de línea de comandos de Windows en secuencias de terminal virtuales y reenviarlas a otro entorno de hospedaje de forma remota o entre plataformas.

Esta traducción no es perfecta. Requiere la ventana host de la consola para mantener un entorno simulado de lo que las ventanas habrían mostrado al usuario. A continuación, proyecta una réplica de este entorno simulado en el host **pseudoconsole** . Todas las llamadas a la API de la consola de Windows funcionan en el entorno simulado para satisfacer las necesidades de la aplicación cliente de línea de comandos heredada. Solo los efectos se propagan en el host final.

Por lo tanto, se recomienda que una aplicación de línea de comandos que requiera compatibilidad completa entre plataformas y soporte técnico completo de todas las características y escenarios nuevos en Windows y en otro lugar se mueva a las secuencias de terminal virtuales y ajuste la arquitectura de las aplicaciones de línea de comandos para que se alineen con todas las plataformas.

Puede encontrar más información sobre esta transición de Windows para las aplicaciones de línea de comandos en nuestro [mapa de ruta del ecosistema](ecosystem-roadmap.md).
