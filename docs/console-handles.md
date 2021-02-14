---
title: Identificadores de consola
description: Un proceso de consola utiliza identificadores para acceder a los búferes de entrada y de pantalla de su consola, incluidas las funciones GetStdHandle, CreateFile o CreateConsoleScreenBuffer.
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
ms.openlocfilehash: 817c902426ac09fdd246f8d1281528ee5dfcab06
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358075"
---
# <a name="console-handles"></a>Identificadores de consola

Un proceso de consola utiliza identificadores para acceder a los búferes de entrada y de pantalla de su consola. Un proceso puede usar la función [**GetStdHandle**](getstdhandle.md), [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) o [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) para abrir uno de estos identificadores.

La función [**GetStdHandle**](getstdhandle.md) proporciona un mecanismo para recuperar los identificadores de entrada estándar (`STDIN`), salida estándar (`STDOUT`) y error estándar (`STDERR`) asociados a un proceso. Durante la creación de la consola, el sistema crea estos identificadores. Inicialmente, `STDIN` es un identificador del búfer de entrada de la consola, y `STDOUT` y `STDERR` son controladores del búfer de pantalla activo de la consola. Sin embargo, la función [**SetStdHandle**](setstdhandle.md) puede redirigir los identificadores estándar cambiando el identificador asociado por `STDIN`, `STDOUT` o `STDERR`. Dado que todos los procesos secundarios heredan los identificadores estándar del elemento primario, las llamadas subsiguientes a **GetStdHandle** devuelven el identificador redirigido. Por tanto, un identificador que devuelva **GetStdHandle** puede hacer referencia a algo distinto de la E/S de la consola. Por ejemplo, antes de crear un proceso secundario, un proceso primario puede usar **SetStdHandle** para establecer que un identificador de canalización sea el identificador `STDIN` que hereda el proceso secundario. Cuando el proceso secundario llama a **GetStdHandle**, obtiene el identificador de canalización. Esto significa que el proceso primario puede controlar los identificadores estándar del proceso secundario. Los identificadores que devuelve **GetStdHandle** tienen el acceso `GENERIC_READ | GENERIC_WRITE` a menos que se haya utilizado **SetStdHandle** para reducir el acceso del identificador estándar.

El valor de los identificadores que devuelve [**GetStdHandle**](getstdhandle.md) no es 0, 1 ni 2, por lo que las constantes de secuencia predefinidas estándar en Stdio.h (`STDIN`, `STDOUT` y `STDERR`) no se pueden usar en funciones que requieren un identificador de consola.

La función [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) permite que un proceso obtenga un identificador para el búfer de entrada de la consola y el búfer de pantalla activo, aunque `STDIN` y `STDOUT` se hayan redirigido. Para abrir un identificador de un búfer de entrada de la consola, especifique el valor `CONIN$` en una llamada a **CreateFile**. Para abrir un identificador en el búfer de pantalla activo de la consola, especifique el valor `CONOUT$` en una llamada a **CreateFile**. **CreateFile** le permite especificar el acceso de lectura y escritura del identificador que devuelve.

La función [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) crea un nuevo búfer de pantalla y devuelve un identificador. Este identificador se puede utilizar en cualquier función que acepte un identificador para la salida de la consola. Un búfer de pantalla nuevo no está activo (no se muestra) hasta que su identificador se especifica en una llamada a la función [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md). Tenga en cuenta que el cambio del búfer de pantalla activo no afecta al identificador que devuelve [**GetStdHandle**](getstdhandle.md). Del mismo modo, el uso de [**SetStdHandle**](setstdhandle.md) para cambiar el identificador `STDOUT` no afecta al búfer de pantalla activo.

Los identificadores de consola que devuelve [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) y [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) se pueden usar en cualquiera de las funciones de la consola que requieran un identificador para un búfer de entrada de la consola o de un búfer de pantalla de la consola. Las funciones de la consola pueden usar los identificadores que devuelve [**GetStdHandle**](getstdhandle.md) si no se han redirigido para hacer referencia a algo distinto de la E/S de la consola. Sin embargo, si se redirigió un identificador estándar para que hiciera referencia a un archivo o a una canalización, el identificador solo podrá usarse en las funciones [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) y [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile). [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype) puede ayudar a determinar a qué tipo de dispositivo hace referencia el identificador. Un identificador de consola se presenta como `FILE_TYPE_CHAR`.

Un proceso puede usar la función [**DuplicateHandle**](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle) para crear un identificador de consola duplicado que tenga un acceso o una herencia distintos del identificador original. Sin embargo, tenga en cuenta que un proceso solo puede crear un identificador de consola duplicado para su propio uso. Esto difiere de otros tipos de identificadores (como objetos de archivo, canalización o exclusión mutua), para los que **DuplicateHandle** puede crear un duplicado que sea válido para otro proceso.
El acceso a una consola debe compartirse durante la [creación](creation-of-a-console.md) del otro proceso o puede solicitarlo el otro proceso a través del mecanismo [**AttachConsole**](attachconsole.md).

Para cerrar un identificador de consola, un proceso puede usar la función [**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle).