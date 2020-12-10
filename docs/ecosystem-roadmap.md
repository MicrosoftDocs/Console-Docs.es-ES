---
title: Hoja de ruta de la consola de Windows y del ecosistema de terminal
description: Proporciona una vista de alto nivel de las interacciones y los planes para el host de consola de Windows, las API de consola, el subsistema de consola y el producto de terminal.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, terminal, terminal virtual, host de consola, línea de comandos, subsistema, hoja de ruta, ecosistema
ms.prod: console
ms.localizationpriority: high
ms.openlocfilehash: e5d28a06789f230943d70a49e7c89642b17fdb5c
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420264"
---
# <a name="windows-console-and-terminal-ecosystem-roadmap"></a>Hoja de ruta de la consola de Windows y del ecosistema de terminal

Este documento es una hoja de ruta básica de alto nivel de la consola de Windows y los productos de Terminal Windows. Incluye los temas siguientes:


- Cómo se ajusta la consola de Windows y Terminal Windows en el ecosistema de aplicaciones de línea de comandos en Windows y otros sistemas operativos.

- Un historial y una hoja de ruta futura de los productos, las características y las estrategias que forman parte de la compilación de la plataforma, así como la propia compilación de esta plataforma.

El enfoque de la era actual de la consola o el terminal en Microsoft es ofrecer directamente una experiencia de terminal excepcional a los desarrolladores de la plataforma de Windows, [retirar gradualmente](classic-vs-vt.md) las API clásicas de la consola Windows y reemplazarlas por [secuencias de terminal virtuales](console-virtual-terminal-sequences.md) mediante una [pseudoconsola](pseudoconsoles.md). **[Terminal Windows](/terminal/get-started)** presenta esta transición en una experiencia de primera clase, en la que se invita a la [colaboración mediante código abierto](https://github.com/microsoft/terminal) por parte de la comunidad de desarrolladores, se admite un amplio abanico de combinaciones y coincidencias de las aplicaciones de hospedaje de terminal y de línea de comandos del cliente y se unifica el ecosistema de Windows con las demás plataformas.

## <a name="definitions"></a>Definiciones

Le recomendamos que se familiarice con las [definiciones](definitions.md) de la terminología común que se usa en este espacio antes de continuar. Entre la terminología común se incluye la siguiente: [Aplicaciones de línea de comandos (o consola)](definitions.md#command-line-applications), [identificadores estándar (`STDIN`, `STDOUT`, `STDERR`)](definitions.md#standard-handles), [dispositivos TTY y PTY](definitions.md#ttypty), [clientes y servidores](definitions.md#clients-and-servers), [subsistema de consola](definitions.md#console-subsystem), [host de consola](definitions.md#console-host), [pseudoconsola](definitions.md#pseudoconsole) y [terminal](definitions.md#terminal).

## <a name="architecture"></a>Architecture

La arquitectura general del sistema se divide en cuatro partes: cliente, dispositivo, servidor y terminal.

![Diagrama de flujo de comunicación de línea de comandos de origen a destino que se ejecuta desde el cliente al dispositivo, al servidor y al terminal](images/command-line-communication.png)

### <a name="client"></a>Cliente

El cliente es una aplicación de línea de comandos que usa una interfaz basada en texto para que el usuario pueda escribir comandos (en lugar de una interfaz de usuario basada en el mouse) y devolver una representación de texto del resultado. En Windows, la API de la consola proporciona una capa de comunicaciones entre el cliente y el dispositivo. (También puede ser un identificador de consola estándar con las API de control de dispositivos).

### <a name="device"></a>Dispositivo

El dispositivo es una capa intermedia de comunicaciones de administración de mensajes entre dos procesos, el cliente y el servidor. En Windows, este es el controlador de consola. En otras plataformas, es el dispositivo TTY o PTY. Se pueden usar otros dispositivos, como archivos, canalizaciones y sockets, para este canal de comunicación si toda la transacción está en texto sin formato o contiene [secuencias de terminal virtuales](console-virtual-terminal-sequences.md), pero no con la [API de la consola de Windows](console-functions.md).

### <a name="server"></a>Servidor

El servidor interpreta las llamadas o mensajes de la API solicitados del cliente. En Windows en el modo operativo clásico, el servidor también crea una interfaz de usuario para presentar el resultado en la pantalla. Además, el servidor recopila entradas para devolverlas en los mensajes de respuesta al cliente, a través del controlador, como un terminal incluido en el mismo módulo. En cambio, si se usa el modo de [pseudoconsola ](pseudoconsoles.md), solo es un traductor que presenta esta información en [ secuencias de terminales virtuales ](console-virtual-terminal-sequences.md) a un terminal adjunto.

### <a name="terminal"></a>Terminal

El terminal es la capa final que proporciona servicios gráficos de visualización e interactividad al usuario. Es responsable de capturar la entrada y de codificarla como [secuencias de terminal virtuales](console-virtual-terminal-sequences.md), que finalmente llegan a la entrada `STDIN` del cliente. También recibirá y descodificará las *secuencias de terminal virtuales* que recibe de la entrada `STDOUT` del cliente para presentarlas en pantalla.

#### <a name="further-connections"></a>Conexiones adicionales

Como anexo, se pueden realizar más conexiones mediante el encadenamiento de aplicaciones que atienden varios roles en uno de los puntos de conexión. Por ejemplo, una sesión de SSH tiene dos roles: es un **terminal** para la aplicación de línea de comandos que se ejecuta en un dispositivo, pero reenvía toda la información recibida a un rol de **cliente** de otro dispositivo. Este encadenamiento puede producirse de forma indefinida en todos los dispositivos y contextos, lo que ofrece una amplia flexibilidad de escenarios.

En las plataformas que no son de Windows, los roles de **servidor** y de **terminal** son una sola unidad, ya que no es necesario disponer de ninguna capa de compatibilidad de traducción entre un conjunto de API y las [secuencias de terminal virtuales](console-virtual-terminal-sequences.md).

## <a name="microsoft-products"></a>Productos de Microsoft

Todos los productos de la línea de comandos de Microsoft Windows ahora están disponibles en GitHub en un repositorio de código abierto, [microsoft/terminal](https://github.com/microsoft/terminal).

### <a name="windows-console-host"></a>Host de consola de Windows

Esta es la interfaz de usuario tradicional de Windows para las aplicaciones de línea de comandos. Controla todo el mantenimiento de la API de consola que se llama desde cualquier aplicación de línea de comandos adjunta. La consola de Windows también controla la representación de la interfaz gráfica de usuario (GUI) en nombre de todas esas aplicaciones. Se encuentra en el directorio del sistema como `conhost.exe` o `openconsole.exe` en su forma de código abierto. Se incluye con el sistema operativo Windows. También puede encontrarse en otros productos de Microsoft compilados desde el repositorio de código abierto a fin de obtener una implementación más actualizada de la infraestructura de la [pseudoconsola](pseudoconsoles.md). Según las definiciones anteriores, funciona en un rol de servidor y terminal combinado tradicionalmente o en un rol solo de servidor a través de la infraestructura de _pseudoconsola_ preferida.

### <a name="windows-terminal"></a>Terminal Windows

Esta es la nueva interfaz de Windows para las aplicaciones de la línea de comandos. Terminal Windows sirve como ejemplo propio del uso de la [pseudoconsola](pseudoconsoles.md) para separar las preocupaciones entre el mantenimiento de la API y la interconexión de aplicaciones basadas en texto, de forma muy parecida a las plataformas que no son de Windows.


Terminal Windows es la interfaz de usuario principal de modo de texto para Windows. Muestra las funcionalidades del ecosistema e impulsa el desarrollo de Windows para la unificación con otras plataformas. Terminal Windows también es un ejemplo de cómo crear una aplicación moderna, sólida y compleja que abarque el historial y la gama de API y marcos de trabajo de Windows. Según las definiciones anteriores, este producto funciona en un rol de terminal.

## <a name="major-historical-milestones"></a>Hitos históricos principales

Los hitos históricos principales del subsistema de la consola tuvieron lugar en varias implementaciones anteriores a la 2014. Luego, pasaron a ser una introducción del trabajo realizado desde 2014, cuando el enfoque renovado en la línea de comandos se formó en la era de Windows 10.

### <a name="initial-implementation"></a>Implementación inicial

**\[1989-década de 1990]** El sistema de host de consola inicial se implementó como una emulación del entorno de DOS en el sistema operativo Windows. Su código está entrelazado y coopera con el [símbolo del sistema](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd), `cmd.exe`, que es una representación de ese entorno de DOS. El código del sistema host de la consola comparte responsabilidades y privilegios con el intérprete o shell del símbolo del sistema. También proporciona un nivel básico de servicios para otras utilidades de línea de comandos a fin de realizar servicios de una manera similar a la de CMD.

### <a name="dbcs-for-cjk"></a>DBCS para CJK

**\[1997-1999\]** En este momento, se introdujo la compatibilidad con [DBCS ](https://docs.microsoft.com/windows/win32/intl/double-byte-character-sets) ("conjunto de caracteres de doble byte") para admitir los mercados CJK (chino, japonés y coreano). Este trabajo dio como resultado una bifurcación de muchos de los métodos de escritura y lectura de la consola a fin de proporcionar versiones "occidentales" para tratar con caracteres de un solo byte, así como una representación alternativa para las versiones "orientales" en las que se requieren dos bytes para representar la gran variedad de caracteres. Esta bifurcación incluía la representación expandida de una celda en el entorno de la consola con una o dos celdas de ancho. La opción de una celda era estrecha (más alta que ancha) y, la de dos, era ancha, de ancho completo o bien un cuadrado en el que se podían inscribir ideogramas chinos, japoneses y coreanos comunes.

### <a name="securityisolation"></a>Seguridad y aislamiento

**\[2005-2009\]** Con la experiencia del subsistema de la consola en ejecución en el proceso crítico del sistema, `csrss.exe`, se observó que la conexión de distintas aplicaciones cliente, en distintos niveles de acceso, a un único proceso crítico y con privilegios era especialmente peligrosa. En esta era, el subsistema de la consola se dividió en aplicaciones cliente, de controlador y de servidor. Cada aplicación podía ejecutarse en su propio contexto, lo que reducía las responsabilidades y los privilegios en cada una. Este aislamiento aumentó la solidez general del sistema, ya que cualquier error en el subsistema de la consola ya no afectaba a otras funcionalidades críticas del proceso.

### <a name="user-experience-improvements"></a>Mejoras en la experiencia del usuario

**\[2014-2016\]** Después de un largo tiempo de mantenimiento poco constante en general del subsistema de la consola por parte de varios equipos de toda la organización, se formó un nuevo equipo centrado en el desarrollo para que realizara e impulsara mejoras en la consola. Entre las mejoras que se realizaron durante este tiempo se incluyen: selección de líneas, cambio de tamaño fluido de las ventanas, reflujo del texto, función de copiar y pegar, compatibilidad con valores altos de PPP y un enfoque en Unicode, incluida la convergencia de la división entre el almacenamiento "occidental" y "oriental" y los algoritmos de manipulación de secuencias.

### <a name="virtual-terminal-client"></a>Cliente de terminal virtual

**\[2015-2017\]** Con la llegada del [Subsistema de Windows para Linux](https://docs.microsoft.com/windows/wsl/), los esfuerzos de Microsoft por mejorar la experiencia de [Docker en Windows](https://docs.microsoft.com/dotnet/architecture/microservices/container-docker-introduction/docker-defined) y la adopción de [OpenSSH](https://docs.microsoft.com/windows-server/administration/openssh/openssh_overview) como la tecnología líder de ejecución remota de línea de comandos, se introdujeron las implementaciones iniciales de las [secuencias de terminal virtuales](console-virtual-terminal-sequences.md) en el host de consola. Ello permitió que la consola existente actuara como terminal, conectado directamente a esas aplicaciones nativas de Linux en sus respectivos entornos, que se representaran los atributos gráficos y de texto en la pantalla y que se devolviera la entrada del usuario en el dialecto adecuado.

### <a name="virtual-terminal-server"></a>Servidor de terminal virtual

**\[2018\]** En los últimos veinte años, se crearon alternativas de terceros para el host de consola de bandeja de entrada a fin de ofrecer una productividad adicional al desarrollador, que se centraba claramente en personalizaciones avanzadas e interfaces con pestañas. Estas aplicaciones aún debían ejecutar y ocultar la ventana del host de la consola. Se conectaban como una aplicación "cliente" secundaria para extraer información del búfer en bucles de sondeo, tal y como hacía la aplicación cliente de línea de comandos principal. Su objetivo era ser un terminal, igual que en otras plataformas, pero en el mundo de Windows, en que no se podían reemplazar los terminales.

En este período, se presentó la infraestructura de [pseudoconsola](pseudoconsoles.md). La pseudoconsola permite que cualquier aplicación inicie el host de consola en un modo no interactivo y se convierta en la interfaz de terminal final del usuario. La principal limitación de este trabajo era la promesa de compatibilidad continua de Windows en el mantenimiento de todas las [API de la consola de Windows](console-functions.md) publicadas para un futuro indefinido, así como el hecho de proporcionar una interfaz de hospedaje de servidor de reemplazo que coincidiera con lo que se espera en todas las demás plataformas: [secuencias de terminal virtuales](console-virtual-terminal-sequences.md). Como tal, este trabajo fue un reflejo de la fase del cliente: la _pseudoconsola_ proyectaba lo que se mostraría en la pantalla como _secuencias de terminal virtuales_ para un host delegado e interpretaba las respuestas en secuencias de entrada de formato de Windows para el consumo de la aplicación cliente.

## <a name="roadmap-for-the-future"></a>Hoja de ruta para el futuro

### <a name="terminal-applications"></a>Aplicaciones de terminal

**\[2019-presente\]** Es la era de código abierto del subsistema de la consola, que se centra en el nuevo terminal de Windows. Según se anunció durante la conferencia de Microsoft Build en mayo de 2019, Terminal Windows se encuentra disponible en su totalidad en GitHub en [microsoft/terminal](https://github.com/microsoft/terminal). La compilación de la aplicación de Terminal Windows a partir de la plataforma refinada para la [pseudoconsola](pseudoconsoles.md) será el enfoque de esta era, lo que aportará una excelente experiencia de terminal directamente a los desarrolladores de la plataforma de Windows.

El objetivo de **[Terminal Windows](/terminal/get-started)** no solo es presentar la plataforma, lo que incluye la tecnología de interfaz [WinUI](/apps/winui/), el modelo de empaquetado [MSIX](/msix/) y la arquitectura de componentes [C ++/WinRT](/uwp/cpp-and-winrt-apis/), sino que también ser una validación de la propia plataforma. Terminal Windows promueve que la organización de Windows abra y desarrolle la plataforma de aplicaciones según sea necesario a fin de seguir aumentando la productividad de los desarrolladores. El conjunto único de requisitos de desarrolladores y usuarios avanzados de Terminal Windows fomenta los requisitos de la plataforma de Windows moderna para lo que esos mercados realmente necesitan de Windows.

En el sistema operativo Windows, esto incluye [la retirada de la interfaz de usuario de host de consola clásica](./classic-vs-vt.md) de su posición predeterminada en favor de [Terminal Windows](/terminal/get-started), [ConPTY](https://devblogs.microsoft.com/commandline/windows-command-line-introducing-the-windows-pseudo-console-conpty/) y [secuencias de terminal virtuales](console-virtual-terminal-sequences.md).

Por último, el objetivo de esta era es permitir la elección completa de la experiencia predeterminada, ya sea del producto Terminal Windows o de terminales alternativos.

### <a name="client-support-library"></a>Biblioteca de compatibilidad de cliente

**\[En el futuro\]** Con la compatibilidad y la documentación de [secuencias de terminal virtuales](console-virtual-terminal-sequences.md) en el lado cliente, recomendamos encarecidamente que los desarrolladores de la utilidad de línea de comandos de Windows usen preferentemente secuencias de terminal virtuales en lugar de las API de Windows clásicas a fin de beneficiarse de un ecosistema unificado con todas las plataformas. Sin embargo, hay una parte importante que falta: las demás plataformas tienen una amplia gama de bibliotecas auxiliares de cliente para controlar la entrada, como [readline](https://tiswww.case.edu/php/chet/readline/rltop.html), y la presentación gráfica, como [ncurses](https://invisible-island.net/ncurses/ncurses.html). Este elemento concreto de la hoja de ruta representa la exploración de lo que ofrece el ecosistema y cómo podemos acelerar la adopción de secuencias de terminal virtuales en aplicaciones de línea de comandos de Windows a través de la API de consola clásica.

### <a name="sequence-passthrough"></a>Tránsito de la secuencia

**\[En el futuro\]** La combinación de implementaciones de servidor y de cliente de terminal virtual permitirá mezclar y hacer coincidir todas las aplicaciones de línea de comandos del cliente y de hospedaje de terminal. Esta combinación podrá establecer comunicación con las [API de consola de Windows ](console-functions.md)clásicas o las [secuencias de terminal virtuales](console-virtual-terminal-sequences.md), sin embargo, realizar la conversión al método clásico de Windows compatible y, luego, de nuevo al método de terminal virtual más universal tendrá un costo muy elevado.

Una vez que el mercado realice una suficiente adopción de las _secuencias de terminal virtuales_ y UTF-8 en Windows, el trabajo de conversión e interpretación del host de consola se podrá deshabilitar opcionalmente. A continuación, el host de consola se convertirá en un servicio simple de llamadas a la API y una retransmisión de llamadas de dispositivo a la aplicación de hospedaje a través de la [pseudoconsola](pseudoconsoles.md). Este cambio aumentará el rendimiento y maximizará el dialecto de las secuencias que se podrán usar entre la aplicación cliente y el terminal. Mediante este cambio, los escenarios de interactividad adicionales se habilitarán y *(finalmente)* el mundo de Windows se alineará con la familia de todas las demás plataformas en el espacio de la aplicación de línea de comandos.
