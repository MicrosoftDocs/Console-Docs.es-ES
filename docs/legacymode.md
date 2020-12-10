---
title: 'Modo de consola heredado: escritorio de Windows'
description: El modo de consola heredado es una herramienta de compatibilidad que le permite ejecutar aplicaciones de línea de comandos que no funcionan con el host de la consola de Windows 10.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola, compatibilidad
ms.openlocfilehash: eeddfd00ffa8c3ad9d99583b89e4b3be7959f445
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "93037713"
---
# <a name="legacy-console-mode"></a>Modo de consola heredado

El modo de consola heredado es una herramienta de compatibilidad diseñada para facilitar el trabajo de los usuarios que usan versiones anteriores de las herramientas de línea de comandos en Windows 10. En el caso de cualquier herramienta de línea de comandos que no se muestre o funcione correctamente en la experiencia de la consola de Windows 10 predeterminada, este modo proporciona una solución general para devolver el sistema a una versión anterior de la experiencia de hospedaje de la consola.

## <a name="using-legacy-console-mode"></a>Uso del modo de consola heredado

Para usar el modo de consola heredado, abra primero cualquier ventana de hospedaje de la consola. Normalmente, esto se realiza mediante el inicio de uno de los intérpretes de comandos [CMD](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd) o de [PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-windows-powershell).

Haga clic con el botón derecho en la barra de título de la aplicación y elija la opción `Properties` del menú. Haga clic en la primera pestaña, `Options`. A continuación, active la casilla situada en la parte inferior de la página que describe `Use legacy console`. Presione el botón `OK` para aplicar esta opción.

La configuración se puede revertir volviendo al mismo menú de la hoja de propiedades, desactivando la casilla y presionando `OK`.

> [!NOTE]
>Esta configuración se aplica globalmente a todas las sesiones que se inician después de cambiar la preferencia. Tenga en cuenta que las sesiones que ya están abiertas no se cambiarán.

## <a name="differences-between-modes"></a>Diferencias entre modos

El equipo host de la consola hace todo lo posible para minimizar las diferencias entre los modos heredados y actuales de la consola, para garantizar que tantos clientes como sea posible puedan ejecutar la versión más actualizada. Si tiene algún problema que requiera el uso de la consola heredada y que no se documente aquí, póngase en contacto con el equipo en el repositorio de GitHub [microsoft/terminal](https://github.com/microsoft/terminal/) o a través del [Centro de opiniones](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) para obtener ayuda.

### <a name="16-bit-applications-on-32-bit-windows"></a>Aplicaciones de 16 bits en Windows de 32 bits

Algunas aplicaciones de 16 bits en Windows de 32 bits usan una tecnología de máquina virtual denominada [NTVDM](https://docs.microsoft.com/windows/compatibility/ntvdm-and-16-bit-app-support) para funcionar. A menudo, estas aplicaciones utilizan un modo de almacenamiento en búfer de pantalla gráfica junto con el entorno de hospedaje de la consola para funcionar. Solo la experiencia de la consola heredada admite estos modos de almacenamiento en búfer gráfico y la compatibilidad adicional con la API de consola que es necesaria para poder ejecutar estas aplicaciones. Asimismo, el sistema seleccionará automáticamente el entorno de consola heredado cuando se inicie una de estas aplicaciones.

### <a name="ime-embedding"></a>Incrustación de IME

El host de consola heredado incrustó la parte de sugerencias del IME dentro de la ventana de hospedaje al reservar una línea en la parte inferior de la pantalla para obtener sugerencias. En su lugar, el entorno de host de la consola actual delega esta actividad al subsistema del IME, para que muestre una ventana superpuesta sobre el host de la consola con sugerencias. En un entorno en el que no es posible usar las ventanas de superposición (como ocurre con ciertas herramientas de comunicación remota), es posible que el host de consola heredado sea necesario.

### <a name="api-differences"></a>Diferencias de API

La principal diferencia conocida entre los elementos heredados y actuales es la implementación de UTF-8. El host heredado tiene una compatibilidad muy rudimentaria y a menudo incorrecta de UTF-8 con la [página de códigos 65001](https://docs.microsoft.com/windows/win32/intl/code-pages). En cambio, el host de consola actual contiene mejoras incrementales que se publican en cada versión de Windows 10 para mejorar esta compatibilidad. Por lo tanto, las aplicaciones que intentan confiar en la predicción de interpretaciones "incorrectas conocidas" de UTF-8 de la consola heredada, se encontrarán recibiendo respuestas diferentes debido a la mejora de la compatibilidad.

Puede consultar otras diferencias que se pueden experimentar con las API en el [repositorio de GitHub microsoft/terminal ](https://github.com/microsoft/terminal/) o a través del [Centro de opiniones](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app), para revisar las evaluaciones y sus posibles correcciones.
