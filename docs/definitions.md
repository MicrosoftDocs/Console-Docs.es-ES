---
title: Consola de Windows y definiciones de terminal
description: Proporciona definiciones de palabras y frases que se usan normalmente en este espacio y conjunto de documentos relacionados con la consola y el sistema de terminal.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, terminal, terminal virtual, host de consola, línea de comandos, subsistema, definiciones
ms.prod: console
ms.openlocfilehash: 763421a25d5ecaa2291b68b0370644af152622a9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039631"
---
# <a name="definitions"></a>Definiciones

En este documento se proporcionan las definiciones de palabras y frases específicas en este espacio y se usan como referencia en este conjunto de documentos.

## <a name="command-line-applications"></a>Aplicaciones de línea de comandos

Las aplicaciones de línea de comandos, o a veces denominadas "aplicaciones de consola" o denominadas "clientes" del subsistema de la consola, son programas que operan principalmente en una secuencia de texto o información de caracteres. Por lo general, no contienen elementos de interfaz de usuario propios y delegan los roles de salida/visualización y de entrada/interacción en una aplicación de hospedaje. Las aplicaciones de línea de comandos reciben un flujo de texto en su controlador de entrada estándar `STDIN` que representa la entrada del teclado de un usuario, procesa esa información y, a continuación, responde con un flujo de texto en la salida estándar `STDOUT` para que se muestre de nuevo en el monitor del usuario. Por supuesto, esto ha evolucionado con el tiempo para dispositivos de entrada y escenarios remotos adicionales, pero la misma filosofía básica sigue siendo la misma: los clientes de línea de comandos operan en texto y otro usuario administra la visualización o la entrada.

## <a name="standard-handles"></a>Identificadores estándar

Los identificadores estándar son una serie,, `STDIN` `STDOUT` y `STDERR` , introducida como parte de un espacio de proceso en el inicio. Representan un lugar para que la información se acepte en la forma en que se envía y se devuelve de forma alternativa (incluido un lugar especial para informar sobre los errores). En el caso de las aplicaciones de línea de comandos, siempre deben existir cuando se inicia la aplicación. Se heredan del elemento primario automáticamente, se establecen explícitamente mediante el elemento primario o se crean automáticamente mediante el sistema operativo Si no se especifican ni se permiten. En el caso de las aplicaciones Windows clásicas, pueden estar en blanco al inicio. Sin embargo, se pueden heredar implícita o explícitamente de los elementos primarios o asignados, adjuntados y liberados durante el tiempo de ejecución de la propia aplicación.

Los identificadores estándar no implican un tipo específico de dispositivo conectado. Sin embargo, en el caso de las aplicaciones de línea de comandos, el dispositivo suele ser un dispositivo de consola, un archivo (desde el redireccionamiento en un shell) o una canalización (desde un shell que conecta la salida de una utilidad a la entrada de la siguiente). También puede ser un socket o cualquier otro tipo de dispositivo.

## <a name="ttypty"></a>TTY/PTY

En plataformas que no son de Windows, los dispositivos TTY y PTY representan, respectivamente, un verdadero dispositivo físico o un pseudo-dispositivo creado por software que son el mismo concepto que una sesión de consola de Windows: un canal en el que la comunicación entre una aplicación cliente de línea de comandos y una aplicación de interactividad del host de servidor o un dispositivo físico de pantalla o teclado puede intercambiar información.

## <a name="clients-and-servers"></a>Clientes y servidores

Dentro de este espacio, hacemos referencia a "clientes" como aplicaciones que realizan el trabajo de procesar información y ejecutar comandos. Las aplicaciones "servidor" son las responsables de la interfaz de usuario y son los trabajadores que traducen la entrada y la salida en formularios estándar en nombre de los clientes.

## <a name="console-subsystem"></a>Subsistema de consola

Se trata de un término comodín que representa todos los módulos que afectan a las operaciones de consola y de línea de comandos. Hace referencia específicamente a una marca que forma parte del encabezado ejecutable portable y que especifica si la aplicación de inicio es una aplicación de línea de comandos o de consola (y debe tener identificadores estándar para iniciarse) o una aplicación de Windows (y no la necesita).

Se considera que pertenecen a este grupo el host de consola, las aplicaciones cliente de línea de comandos, el controlador de consola, la superficie de la API de consola, la infraestructura de pseudoconsole, los terminales, las hojas de propiedades de configuración, los mecanismos y los códigos auxiliares del cargador de procesos.

## <a name="console-host"></a>Host de consola

El host de la consola de Windows, o `conhost.exe` , es la aplicación de servidor para todas las API de la consola de Windows, así como la interfaz de usuario clásica de Windows para trabajar con aplicaciones de línea de comandos. El contenido completo de este archivo binario, tanto el servidor de API como la interfaz de usuario, que históricamente pertenecía a Windows `csrss.exe` , un proceso crítico del sistema y fue divergedo por motivos de seguridad y aislamiento. En el futuro, seguirá `conhost.exe` siendo responsable de la traducción y el mantenimiento de llamadas API, pero los componentes de la interfaz de usuario están diseñados para ser delegados a través de un pseudoconsole a un terminal.

## <a name="pseudoconsole"></a>Pseudoconsole

Esta es la simulación de Windows de un pseudoterminal o "PTY" desde otras plataformas. Intenta hacer coincidir la filosofía de la interfaz general de PTYs, proporcionando un canal bidireccional simple de la comunicación basada en texto, pero lo complementa en Windows con una capa de compatibilidad grande para traducir el alcance de las aplicaciones Windows escritas antes de este cambio de filosofía de diseño desde la superficie de API de la consola clásica al formulario de comunicación de canal de texto simple. Los terminales pueden usar pseudoconsole para tomar posesión de los elementos de la interfaz de usuario del host de la consola, y `conhost.exe` dejarlos a cargo de los esfuerzos de servicio, traducción y compatibilidad de la API.

## <a name="terminal"></a>Terminal

Un terminal es la interfaz de usuario y el módulo de interacción para una aplicación de línea de comandos. En la actualidad, se trata de una representación de software de lo que solía ser un dispositivo físico con un monitor, un teclado y un canal de comunicación de serie bidireccional. Es responsable de recopilar la entrada del usuario en una gran variedad de formas, traducirla y codificarla y cualquier información de comando especial en una única secuencia de texto y enviarla al PTY para su transmisión en el `STDIN` canal de la aplicación cliente de la línea de comandos. También es responsable de recibir información, a través de la PTY, que procedía del canal de una aplicación cliente `STDOUT` , la descodificación de cualquier información especial en la carga, el diseño de todo el texto y comandos adicionales, y la presentación gráfica del usuario final.
