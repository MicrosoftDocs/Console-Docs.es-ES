---
title: Guía básica de la consola de Windows y del ecosistema de terminal
description: Proporciona una vista de alto nivel de las interacciones entre y los planes para el host de consola de Windows, las API de consola, el subsistema de consola y el producto de terminal.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, terminal, terminal virtual, host de consola, línea de comandos, subsistema, guía básica, ecosistema
ms.prod: console
ms.openlocfilehash: e47b72a6f66e54b5f2904770f7c1a87e08d927e2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039629"
---
# <a name="windows-console-and-terminal-ecosystem-roadmap"></a>Guía básica de la consola de Windows y del ecosistema de terminal

Este documento es una guía básica de alto nivel de la consola de Windows y productos de Windows terminal. Abarca:


- Cómo encaja la consola de Windows y Windows terminal en el ecosistema de aplicaciones de línea de comandos en Windows y otros sistemas operativos.

- Un historial y un plan de desarrollo futuro de los productos, las características y las estrategias que forman parte de la creación de la plataforma, así como la compilación para esta plataforma.

El foco de la actual época de la consola o el terminal en Microsoft es ofrecer directamente una experiencia de terminal de primera clase a los desarrolladores de la plataforma Windows, así como [salir](classic-vs-vt.md) de las API clásicas de la consola de Windows, reemplazarlas por [secuencias de terminal virtuales](console-virtual-terminal-sequences.md) mediante [pseudoconsole](pseudoconsoles.md). **[Windows terminal](/terminal/get-started)** exhibe esta transición en una experiencia de primera clase, con lo que se invita a la [colaboración de código abierto](https://github.com/microsoft/terminal) de la comunidad de desarrolladores, con lo que se ofrece un amplio abanico de combinaciones y coincidencias de la línea de comandos del cliente y las aplicaciones de hospedaje de terminal, y la unificación del ecosistema de Windows con todas las demás plataformas.

## <a name="definitions"></a>Definiciones

Se recomienda familiarizarse con las [definiciones](definitions.md) de la terminología común que se usa en este espacio antes de continuar. La terminología común incluye [las aplicaciones de línea de comandos (o consola)](definitions.md#command-line-applications), los [identificadores estándar ( `STDIN` , `STDOUT` , `STDERR` )](definitions.md#standard-handles), los [dispositivos TTY y PTY](definitions.md#ttypty), [los clientes y servidores](definitions.md#clients-and-servers), el [subsistema](definitions.md#console-subsystem)de la consola, el [host de consola](definitions.md#console-host), el [pseudoconsole](definitions.md#pseudoconsole)y el [terminal](definitions.md#terminal).

## <a name="architecture"></a>Arquitectura

La arquitectura general del sistema se encuentra en cuatro partes: cliente, dispositivo, servidor y terminal.

![Origen del gráfico de flujo de comunicación de línea de comandos en destino que se ejecuta desde el cliente al dispositivo al servidor Terminal Server](images/command-line-communication.png)

### <a name="client"></a>Cliente

El cliente es una aplicación de línea de comandos que usa una interfaz basada en texto para que el usuario pueda escribir comandos (en lugar de una interfaz de usuario basada en el mouse) y devolver una representación de texto del resultado. En Windows, la API de la consola proporciona una capa de comunicaciones entre el cliente y el dispositivo. (Esto también puede ser un controlador de consola estándar con las API de control de dispositivos).

### <a name="device"></a>Dispositivo

El dispositivo es un nivel intermedio de comunicaciones de control de mensajes entre dos procesos, el cliente y el servidor. En Windows, este es el controlador de consola. En otras plataformas, es el dispositivo TTY o PTY. Se pueden usar otros dispositivos como archivos, canalizaciones y Sockets como este canal de comunicación si toda la transacción está en texto sin formato o contiene [secuencias de terminales virtuales](console-virtual-terminal-sequences.md), pero no con las API de la [consola de Windows](console-functions.md).

### <a name="server"></a>Servidor

El servidor interpreta las llamadas o mensajes de API solicitados del cliente. En Windows en el modo operativo clásico, el servidor también crea una interfaz de usuario para presentar el resultado en la pantalla. Además, el servidor recopila entradas para devolverlos en los mensajes de respuesta al cliente, a través del controlador, como un paquete de terminal incluido en el mismo módulo. Con el modo [pseudoconsole](pseudoconsoles.md) , en su lugar solo es un traductor para presentar esta información en [secuencias de terminal virtuales](console-virtual-terminal-sequences.md) en un terminal conectado.

### <a name="terminal"></a>Terminal

El terminal es el nivel final que proporciona servicios de visualización e interactividad gráficos al usuario. Es responsable de capturar la entrada y codificarla como [secuencias de terminales virtuales](console-virtual-terminal-sequences.md), lo que finalmente llegará a la del cliente `STDIN` . También recibirá y descodificará las *secuencias de terminal virtuales* que recibe de la presentación del cliente `STDOUT` en la pantalla.

#### <a name="further-connections"></a>Conexiones adicionales

Como apéndice, se pueden realizar más conexiones mediante la encadenamiento de aplicaciones que atienden varios roles en uno de los extremos. Por ejemplo, una sesión de SSH tiene dos roles: es un **terminal** para la aplicación de línea de comandos que se ejecuta en un dispositivo, pero reenvía toda la información recibida a un rol de **cliente** en otro dispositivo. Este encadenamiento puede producirse indefinidamente en los dispositivos y contextos que ofrecen una gran flexibilidad al escenario.

En plataformas que no son de Windows, el **servidor** y los roles de **terminal** son una sola unidad, ya que no es necesario disponer de una capa de compatibilidad de traducción entre un conjunto de API y las [secuencias de terminales virtuales](console-virtual-terminal-sequences.md).

## <a name="microsoft-products"></a>Productos de Microsoft

Todos los productos de línea de comandos de Microsoft Windows están ahora disponibles en GitHub en un repositorio de código abierto, [Microsoft/Terminal](https://github.com/microsoft/terminal).

### <a name="windows-console-host"></a>Host de consola de Windows

Esta es la interfaz de usuario tradicional de Windows para las aplicaciones de línea de comandos. Controla todo el servicio de la API de consola llamado desde cualquier aplicación de línea de comandos adjunta. La consola de Windows también controla la representación de la interfaz gráfica de usuario (GUI) en nombre de todas esas aplicaciones. Se encuentra en el directorio del sistema como `conhost.exe` o `openconsole.exe` en su forma de código abierto. Incluye el sistema operativo Windows. También se puede encontrar en otros productos de Microsoft creados desde el repositorio de código abierto para obtener una implementación más actualizada de la infraestructura de [pseudoconsole](pseudoconsoles.md) . Según las definiciones anteriores, funciona en un rol de servidor y terminal combinado tradicionalmente o en un rol de servidor a través de la infraestructura de _pseudoconsole_ preferida.

### <a name="windows-terminal"></a>Terminal Windows

Esta es la nueva interfaz de Windows para las aplicaciones de línea de comandos. Windows terminal sirve como un ejemplo de primera parte del uso de [pseudoconsole](pseudoconsoles.md) para separar las preocupaciones entre el servicio de API y la interconexión de aplicaciones basadas en texto, de forma muy similar a la de todas las plataformas que no son de Windows.


Windows terminal es la interfaz de usuario de modo de texto insignia para Windows. Muestra las capacidades del ecosistema y está impulsando el desarrollo de Windows para unificar con otras plataformas. Windows terminal también es un ejemplo de cómo crear una aplicación moderna sólida y compleja que abarque el historial y la gama de las API y los marcos de trabajo de Windows. Según las definiciones anteriores, este producto funciona en un rol de terminal.

## <a name="major-historical-milestones"></a>Hitos históricos principales

Los hitos históricos principales del subsistema de la consola están divididos en una implementación anterior a la 2014 y, a continuación, pasan a una visión general del trabajo realizado desde 2014, cuando el enfoque renovado en la línea de comandos se formó en la era de Windows 10.

### <a name="initial-implementation"></a>Implementación inicial

**\[ 1989-90]** el sistema de host de la consola inicial se implementó como una emulación del entorno de dos en el sistema operativo Windows. Su código está inenredado y cooperativo con el [símbolo del sistema](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd), `cmd.exe` , que es una representación de ese entorno de dos. El código del sistema host de la consola comparte responsabilidades y privilegios con el intérprete o Shell del símbolo del sistema. También proporciona un nivel básico de servicios para otras utilidades de línea de comandos para realizar servicios de una manera similar a la de CMD.

### <a name="dbcs-for-cjk"></a>DBCS para CJK

**\[ 1997-1999 \]** en torno a esta hora, se introduce la compatibilidad con [DBCS](https://docs.microsoft.com/windows/win32/intl/double-byte-character-sets) ("juego de caracteres de doble byte") para admitir los mercados CJK (Chino, Japonés y Coreano). Este esfuerzo produce una bifurcación de muchos de los métodos de lectura y escritura dentro de la consola de para proporcionar las dos versiones "Western" para tratar los caracteres de un solo byte, así como una representación alternativa de las versiones "orientales", donde se requieren dos bytes para representar la inmensa matriz de caracteres. Esta bifurcación incluía la representación de expansión de una celda en el entorno de la consola para que tenga una longitud de 1 o 2 celdas de ancho, donde una celda es estrecha (es más alta que la ancha) y dos celdas son anchas, de ancho completo, o de otra forma, un cuadrado en el que se pueden inscribir los ideogramas de chino, Japonés y Coreano típicos.

### <a name="securityisolation"></a>Seguridad y aislamiento

**\[ 2005-2009 \]** con la experiencia del subsistema de la consola que se ejecuta dentro del proceso crítico del sistema, `csrss.exe` , la conexión de aplicaciones cliente coordenadas, en distintos niveles de acceso, a un único proceso de gran importancia y con privilegios se observó como especialmente peligrosa. En esta era, el subsistema de la consola se dividió en aplicaciones cliente, de controlador y de servidor. Cada aplicación puede ejecutarse en su propio contexto, lo que reduce las responsabilidades y los privilegios en cada una de ellas. Este aislamiento aumentó la robustez general del sistema, ya que cualquier error en el subsistema de la consola ya no afecta a otras funciones de proceso críticas.

### <a name="user-experience-improvements"></a>Mejoras en la experiencia del usuario

**\[ 2014-2016 \]** después de un período de tiempo prolongado en el que el subsistema de consola ha distribuido por lo general los equipos de la organización, un nuevo equipo centrado en el desarrollador tenía el mismo formato y mejora en la consola. Las mejoras que se han realizado durante este tiempo incluyen: selección de líneas, cambio de tamaño de ventanas suaves, reflujo de texto, copia y pegado, compatibilidad con alta resolución de PPP y un enfoque en Unicode, incluida la convergencia de la división entre el almacenamiento "occidental" y los algoritmos de manipulación de secuencias y de almacenamiento "oriental".

### <a name="virtual-terminal-client"></a>Cliente de terminal virtual

**\[ 2015-2017 \]** con la llegada del [subsistema de Windows para Linux](https://docs.microsoft.com/windows/wsl/), Microsoft esfuerzos por mejorar la experiencia de [Docker en Windows](https://docs.microsoft.com/dotnet/architecture/microservices/container-docker-introduction/docker-defined)y la adopción de [OpenSSH](https://docs.microsoft.com/windows-server/administration/openssh/openssh_overview) como la tecnología de ejecución remota de línea de comandos Premier, las implementaciones iniciales de las [secuencias de terminal virtuales](console-virtual-terminal-sequences.md) se introdujeron en el host de consola. Esto permitía que la consola existente actuara como terminal, conectada directamente a esas aplicaciones nativas de Linux en sus respectivos entornos, lo que representa los atributos gráficos y de texto en la pantalla y devuelve los datos proporcionados por el usuario en el dialecto adecuado.

### <a name="virtual-terminal-server"></a>Servidor de Terminal Server virtual

**\[ 2018 \]** en los últimos veinte años, se crearon alternativas de terceros para el host de la consola de bandeja de entrada para ofrecer una productividad de desarrollador adicional, que se centra en las personalizaciones enriquecidas y las interfaces con fichas. Estas aplicaciones siguen siendo necesarias para ejecutar y ocultar la ventana host de la consola. Se adjuntan como una aplicación "cliente" secundaria para descartar la información del búfer en bucles de sondeo a medida que funciona la aplicación de cliente de la línea de comandos principal. Su objetivo era ser un terminal, como en otras plataformas, pero en el mundo de Windows, donde no se podía reemplazar a los terminales.

En este período, se presentó la infraestructura de [pseudoconsole](pseudoconsoles.md) . Pseudoconsole permite que cualquier aplicación inicie el host de consola en un modo no interactivo y se convierta en la interfaz de terminal final del usuario. La principal limitación de este esfuerzo era la promesa de compatibilidad continua de Windows en el mantenimiento de todas las API de la [consola de Windows](console-functions.md) publicadas para un futuro indefinido, al tiempo que proporciona una interfaz de hospedaje de servidor de reemplazo que coincidía con lo que se espera en todas las demás plataformas: [secuencias de terminales virtuales](console-virtual-terminal-sequences.md). Como tal, este esfuerzo llevó a cabo la imagen reflejada de la fase de cliente: el _pseudoconsole_ proyecta lo que se mostraría en la pantalla como _secuencias de terminal virtuales_ para un host delegado e interpretará las respuestas en secuencias de entrada con formato de Windows para el consumo de la aplicación cliente.

## <a name="roadmap-for-the-future"></a>Guía básica para el futuro

### <a name="terminal-applications"></a>Aplicaciones de terminal

**\[ 2019: ahora \]** es la era de código abierto para el subsistema de la consola, centrándose en el nuevo terminal de Windows. Anunciado durante la Conferencia de Microsoft Build en mayo de 2019, Windows terminal está completamente en GitHub en [Microsoft/Terminal](https://github.com/microsoft/terminal). Compilar la aplicación de Windows terminal sobre la plataforma refinada para [pseudoconsole](pseudoconsoles.md) será el centro de esta era, lo que aportará una experiencia de terminal de primera clase directamente a los desarrolladores de la plataforma Windows.

**[Windows terminal](/terminal/get-started)** no solo tiene que presentar la plataforma, incluida la tecnología de interfaz [WinUI](/apps/winui/) , el modelo de empaquetado de [MSIX](/msix/) y la arquitectura de componentes [/WinRT de C++](/uwp/cpp-and-winrt-apis/) , sino también como una validación de la propia plataforma. Windows terminal está impulsando que la organización de Windows abra y evolucione la plataforma de aplicaciones según sea necesario para seguir elevando la productividad de los desarrolladores. El conjunto único de Windows terminal para los requisitos de usuario avanzado y desarrollador permite impulsar los requisitos modernos de la plataforma Windows para lo que realmente necesitan esos mercados de Windows.

Dentro del sistema operativo Windows, esto incluye [retirar la interfaz de usuario del host de consola clásico](./classic-vs-vt.md) de su posición predeterminada en favor de [Windows terminal](/terminal/get-started), [ConPTY](https://devblogs.microsoft.com/commandline/windows-command-line-introducing-the-windows-pseudo-console-conpty/)y [secuencias de terminales virtuales](console-virtual-terminal-sequences.md).

Por último, esta era tiene la intención de ofrecer una selección completa sobre la experiencia predeterminada, ya sea el producto de Windows terminal o los terminales alternativos.

### <a name="client-support-library"></a>Biblioteca de compatibilidad de cliente

En el **\[ futuro \]** con la compatibilidad y la documentación de las [secuencias de terminal virtuales](console-virtual-terminal-sequences.md) en el lado cliente, recomendamos encarecidamente que los desarrolladores de la utilidad de línea de comandos de Windows usen secuencias de terminal virtuales en primer lugar en las API de Windows clásicas para beneficiarse de un ecosistema unificado con todas las plataformas. Sin embargo, una parte importante que falta es que otras plataformas tienen una amplia gama de bibliotecas auxiliares del lado cliente para administrar entradas como [ReadLine](https://tiswww.case.edu/php/chet/readline/rltop.html) y presentación gráfica como [ncurses](https://invisible-island.net/ncurses/ncurses.html). Este elemento de mapa de carreteras futuro determinado representa la exploración de lo que ofrece el ecosistema y cómo se puede acelerar la adopción de secuencias de terminal virtuales en aplicaciones de línea de comandos de Windows a través de la API de consola clásica.

### <a name="sequence-passthrough"></a>Secuencia de paso a través

En el **\[ futuro \]** , la combinación de implementaciones de servidor y cliente de terminal virtuales permite mezclar y hacer coincidir todas las aplicaciones de la línea de comandos del cliente y el hospedaje de terminal. Esta combinación puede hablar con las API clásicas de la [consola de Windows](console-functions.md) o con las [secuencias de terminal virtuales](console-virtual-terminal-sequences.md). sin embargo, hay un costo de sobrecarga por traducir esto al método clásico de Windows compatible y, a continuación, volver al método de terminal virtual más universal.

Una vez que el mercado adopta las _secuencias de terminales virtuales_ y UTF-8 en Windows, el trabajo de conversión/interpretación del host de consola se puede deshabilitar opcionalmente. A continuación, el host de consola se convertirá en un servicio simple de llamada de API y retransmitirá desde llamadas de dispositivo a la aplicación de hospedaje a través de [pseudoconsole](pseudoconsoles.md). Este cambio aumentará el rendimiento y maximizará el dialecto de las secuencias que se pueden hablar entre la aplicación cliente y el terminal. A través de este cambio, se habilitarán escenarios de interactividad adicionales y *(por último)* el mundo de Windows se alineará con la familia de todas las demás plataformas en el espacio de la aplicación de línea de comandos.
