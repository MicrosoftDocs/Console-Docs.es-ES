---
title: Identificadores de consola
description: Un proceso de consola utiliza identificadores para tener acceso a los búferes de entrada y de pantalla de su consola, incluidas las funciones GetStdHandle, CreateFile o CreateConsoleScreenBuffer.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_handles'
- base.console\_handles
- consoles.console\_handles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: dc723046-b3e9-418a-b386-79be411e5ac8
ms.localizationpriority: high
ms.openlocfilehash: acc7d65e15451fc2804dc1782644c1ccbaa30e28
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420244"
---
# <a name="console-handles"></a>Identificadores de consola

Un proceso de consola utiliza identificadores para tener acceso a los búferes de entrada y de pantalla de su consola. Un proceso puede utilizar la función [**GetStdHandle**](getstdhandle.md), [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)o [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) para abrir uno de estos identificadores.

La función [**GetStdHandle**](getstdhandle.md) proporciona un mecanismo para recuperar los identificadores de entrada estándar ( `STDIN` ), salida estándar ( `STDOUT` ) y error estándar ( `STDERR` ) asociados a un proceso. Durante la creación de la consola, el sistema crea estos identificadores. Inicialmente, `STDIN` es un identificador para el búfer de entrada de la consola y `STDOUT` y `STDERR` son los identificadores del búfer de pantalla activo de la consola. Sin embargo, la función [**SetStdHandle**](setstdhandle.md) puede redirigir los identificadores estándar cambiando el identificador asociado a `STDIN` , `STDOUT` o `STDERR` . Dado que todos los procesos secundarios heredan los identificadores estándar del elemento primario, las llamadas subsiguientes a **GetStdHandle** devuelven el identificador redirigido. Un identificador devuelto por **GetStdHandle** puede, por tanto, hacer referencia a un elemento distinto de e/s de la consola. Por ejemplo, antes de crear un proceso secundario, un proceso primario puede usar **SetStdHandle** para establecer un identificador de canalización que sea el `STDIN` identificador heredado por el proceso secundario. Cuando el proceso secundario llama a **GetStdHandle**, obtiene el identificador de canalización. Esto significa que el proceso primario puede controlar los identificadores estándar del proceso secundario. Los identificadores devueltos por **GetStdHandle** tienen `GENERIC_READ | GENERIC_WRITE` acceso a menos que se haya usado **SetStdHandle** para establecer el identificador estándar para tener un acceso inferior.

El valor de los identificadores devueltos por [**GetStdHandle**](getstdhandle.md) no es 0, 1 y 2, por lo que las constantes de secuencia predefinidas estándar en stdio. h ( `STDIN` , `STDOUT` y `STDERR` ) no se pueden usar en funciones que requieren un identificador de consola.

La función [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) permite a un proceso obtener un identificador para el búfer de entrada de la consola y el búfer de pantalla activo, incluso si `STDIN` y se han `STDOUT` redirigido. Para abrir un identificador de un búfer de entrada de la consola, especifique el `CONIN$` valor en una llamada a **CreateFile**. Especifique el `CONOUT$` valor de una llamada a **CreateFile** para abrir un identificador en el búfer de pantalla activo de la consola. **CreateFile** le permite especificar el acceso de lectura y escritura del identificador que devuelve.

La función [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) crea un nuevo búfer de pantalla y devuelve un identificador. Este identificador se puede utilizar en cualquier función que acepte un identificador para la salida de la consola. El nuevo búfer de pantalla no está activo (se muestra) hasta que su identificador se especifica en una llamada a la función [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) . Tenga en cuenta que el cambio del búfer de pantalla activo no afecta al identificador devuelto por [**GetStdHandle**](getstdhandle.md). Del mismo modo, el uso de [**SetStdHandle**](setstdhandle.md) para cambiar el `STDOUT` identificador no afecta al búfer de pantalla activo.

Los identificadores de consola devueltos por [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) y [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) se pueden usar en cualquiera de las funciones de consola que requieren un identificador para el búfer de entrada de una consola o un búfer de pantalla de la consola. Las funciones de la consola pueden usar los identificadores devueltos por [**GetStdHandle**](getstdhandle.md) si no se han redirigido para hacer referencia a un elemento distinto de e/s de la consola. Sin embargo, si se redirigió un identificador estándar para hacer referencia a un archivo o una canalización, el identificador solo lo pueden usar las funciones [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) . [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype) puede ayudar a determinar a qué tipo de dispositivo hace referencia el identificador. Un identificador de consola presenta como `FILE_TYPE_CHAR` .

Un proceso puede usar la función [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) para crear un controlador de consola duplicado que tenga un acceso o una herencia diferentes del identificador original. Sin embargo, tenga en cuenta que un proceso puede crear un identificador de consola duplicado solo para su propio uso. Esto difiere de otros tipos de identificadores (como objetos de archivo, canalización o exclusión mutua), para los que **DuplicateHandle** puede crear un duplicado que sea válido para un proceso diferente.
El acceso a una consola debe compartirse durante la [creación](creation-of-a-console.md) del otro proceso o puede ser solicitada por el otro proceso a través del mecanismo [**AttachConsole**](attachconsole.md) .

Para cerrar un identificador de consola, un proceso puede utilizar la función [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) .
