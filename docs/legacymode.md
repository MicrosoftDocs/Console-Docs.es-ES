---
title: 'Modo de consola heredada: escritorio de Windows'
description: El modo de consola heredada es una herramienta de compatibilidad que ayuda a ejecutar aplicaciones de línea de comandos que pueden no funcionar con el host de la consola de Windows 10.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola, compatibilidad
ms.openlocfilehash: a69e192426cc178ae98565db07c49f9ff2ce4961
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060824"
---
# <a name="legacy-console-mode"></a>Modo de consola heredada

El modo de consola heredada es una herramienta de compatibilidad diseñada para ayudar a los usuarios de herramientas de línea de comandos anteriores en Windows 10. En el caso de cualquier herramienta de línea de comandos que no se muestre o funcione correctamente en la experiencia de la consola de Windows 10 predeterminada, este modo proporciona una solución general para devolver el sistema a una versión anterior de la experiencia de hospedaje de la consola.

## <a name="using-legacy-console-mode"></a>Usar el modo de consola heredado

Para usar el modo de consola heredado, abra primero cualquier ventana de hospedaje de la consola. Normalmente, esto se realiza mediante el inicio de uno de los intérpretes de comandos [cmd](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd) o [PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-windows-powershell).

Haga clic con el botón derecho en la barra de título de la aplicación y elija la `Properties` opción de menú. Elija la primera pestaña, `Options` . A continuación, active la casilla que se encuentra en la parte inferior de la página que describe `Use legacy console` . Presione el `OK` botón para aplicar.

La configuración se puede revertir volviendo al mismo menú de la hoja de propiedades y desactivando la casilla y presionando después `OK` .

**Nota:** Esta configuración se aplica globalmente a todas las sesiones que se inician después de cambiar la preferencia. Las sesiones que ya están abiertas no se cambiarán.

## <a name="differences-between-modes"></a>Diferencias entre los modos

El equipo host de la consola se esfuerza por minimizar las diferencias entre los modos heredado y actual de la consola de para garantizar que tantos clientes como sea posible puedan ejecutar la versión más actualizada. Si experimenta un problema que requiere el uso de la consola heredada que no se documenta aquí, póngase en contacto con el equipo en el repositorio de github de [Microsoft/Terminal](https://github.com/microsoft/terminal/) o a través del [centro de comentarios](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) para obtener ayuda.

### <a name="16-bit-applications-on-32-bit-windows"></a>aplicaciones de 16 bits en Windows de 32 bits

Algunas aplicaciones de 16 bits en Windows de 32 bits usan una tecnología de máquina virtual para operar denominada [NTVDM](https://docs.microsoft.com/windows/compatibility/ntvdm-and-16-bit-app-support). A menudo, estas aplicaciones usan un modo de almacenamiento en búfer gráfico junto con el entorno de hospedaje de la consola para funcionar. Solo la experiencia de la consola heredada admite estos modos de almacenamiento en búfer gráfico y la compatibilidad con la API de consola adicional necesaria para poder realizar estas aplicaciones. El sistema seleccionará automáticamente el entorno de consola heredado cuando se inicie una de estas aplicaciones.

### <a name="ime-embedding"></a>Incrustación de IME

El host de consola heredado incrustó la parte de sugerencia del IME dentro de la ventana de hospedaje al reservar una línea en la parte inferior de la pantalla para obtener sugerencias. En su lugar, el entorno de host de la consola actual delega esta actividad en el subsistema del IME para mostrar una ventana superpuesta sobre el host de la consola con sugerencias. En un entorno en el que no son posibles las ventanas de superposición (como con ciertas herramientas de comunicación remota), es posible que se requiera el host de consola heredado.

### <a name="api-differences"></a>Diferencias de API

La principal diferencia conocida entre Legacy y Current es la implementación de UTF-8. El host heredado tiene una compatibilidad muy rudimentaria y a menudo incorrecta de UTF-8 con la [Página de códigos 65001](https://docs.microsoft.com/windows/win32/intl/code-pages). El host de consola actual contiene mejoras incrementales que se publican sobre la versión de Windows 10 para mejorar esta compatibilidad. Las aplicaciones que intentan confiar en la predicción de interpretaciones "incorrectas" de UTF-8 de la consola heredada se verán recibiendo respuestas diferentes, ya que se ha mejorado la compatibilidad. 

Otras diferencias experimentadas con las API deben aparecer en el repositorio de github de [Microsoft/Terminal](https://github.com/microsoft/terminal/) o a través del [centro de comentarios](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) para la evaluación de errores y la posible corrección.