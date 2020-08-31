---
title: Modos de consola de alto nivel
description: El comportamiento de las funciones de la consola de alto nivel se ve afectado por los modos de entrada y salida de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_high\_level\_console\_modes'
- base.high\_level\_console\_modes
- consoles.high\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3ec915eb-333d-484d-a14d-46377b503ecc
ms.openlocfilehash: b5b24056a1283d46cbfe21737bd930318042c039
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060620"
---
# <a name="high-level-console-modes"></a>Modos de consola de alto nivel


El comportamiento de las funciones de la consola de alto nivel se ve afectado por los modos de entrada y salida de la consola. Todos los siguientes modos de entrada de la consola están habilitados para el búfer de entrada de la consola cuando se crea una consola:

- Modo de entrada de línea
- Modo de entrada procesado
- Modo de entrada de eco

Los dos modos de salida de la consola siguientes están habilitados para un búfer de pantalla de la consola cuando se crea:

- Modo de salida procesado
- Encapsulado en modo de salida EOL

Los tres modos de entrada, junto con el modo de salida procesado, están diseñados para funcionar juntos. Es mejor habilitar o deshabilitar todos estos modos como un grupo. Cuando todos están habilitados, se dice que la aplicación está en modo "cocido", lo que significa que la mayor parte del procesamiento se controla para la aplicación. Cuando se deshabilitan todos, la aplicación está en modo "sin procesar", lo que significa que la entrada no se filtra y se deja cualquier procesamiento en la aplicación.

Una aplicación puede usar la función [**GetConsoleMode**](getconsolemode.md) para determinar el modo actual del búfer de entrada o el búfer de pantalla de una consola. Puede habilitar o deshabilitar cualquiera de estos modos con los siguientes valores en la función [**SetConsoleMode**](setconsolemode.md) . Tenga en cuenta que al establecer el modo de salida de un búfer de pantalla no se ve afectado el modo de salida de otros búferes de pantalla.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Mode</th>
<th>Descripción</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>ENABLE_PROCESSED_INPUT</strong></td>
<td>Se usa con un identificador de entrada de consola para hacer que el sistema procese cualquier entrada de tecla de control o de edición del sistema en lugar de devolverla como entrada en la operación de lectura&#39;búfer s. Si la entrada de línea también está habilitada, los retroceso y los retornos de carro se controlan correctamente. Un retroceso hace que el cursor se desplace un espacio sin que afecte al carácter situado en la posición del cursor. Un retorno de carro se convierte en combinación de caracteres de retorno de carro y avance de línea. Si el modo de entrada de eco está habilitado y la salida debe reflejar la edición del sistema, la salida procesada debe estar habilitada para el búfer de pantalla activo. Si está habilitada la entrada procesada, la combinación de teclas CTRL + C se pasa al controlador adecuado independientemente de si está habilitada la entrada de línea. Para obtener más información sobre los controladores de control, vea <a href="console-control-handlers.md" data-raw-source="[Console Control Handlers](console-control-handlers.md)">controladores de control de consola</a>.</td>
</tr>
<tr class="even">
<td><strong>ENABLE_LINE_INPUT</strong></td>
<td>Se usa con un identificador de entrada de consola para hacer que las funciones <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>readfile</strong></a> y <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> devuelvan cuando se presiona la tecla entrar. Si el modo de entrada de línea está deshabilitado, las funciones devuelven cuando uno o varios caracteres están disponibles en el búfer de entrada.</td>
</tr>
<tr class="odd">
<td><strong>ENABLE_ECHO_INPUT</strong></td>
<td>Se usa con un identificador de entrada de consola para hacer que la entrada de teclado leída por la función <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>readfile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> se repita en el búfer de pantalla activo. Los caracteres se repiten solo si el proceso que llama a <strong>readfile</strong> o <strong>ReadConsole</strong> tiene un identificador abierto para el búfer de pantalla activo. No se puede habilitar el modo de eco a menos que la entrada de línea también esté habilitada. El modo de salida del búfer de pantalla activo afecta a la forma en que se muestra la entrada en eco.</td>
</tr>
<tr class="even">
<td><strong>ENABLE_PROCESSED_OUTPUT</strong></td>
<td>Se usa con un identificador de búfer de pantalla de la consola para hacer que el sistema realice la acción adecuada para los caracteres de control ANSI que se escriben en un búfer de pantalla. Se procesan los caracteres de retroceso, tabulación, campana, retorno de carro y avance de línea. Un carácter de tabulación mueve el cursor a la siguiente tabulación, que se produce cada ocho caracteres. Un carácter de campana emite un tono breve.</td>
</tr>
<tr class="odd">
<td><strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong></td>
<td>Se usa con un identificador de búfer de pantalla de la consola para hacer que la posición de salida actual (posición del cursor) se mueva a la primera columna de la fila siguiente (línea) cuando se alcanza el final de la fila actual. Si se alcanza la parte inferior de la región de la ventana, el origen de la ventana se mueve una fila hacia abajo. Este movimiento tiene el efecto de desplazar el contenido de la ventana hacia arriba una fila. Si se alcanza la parte inferior del búfer de pantalla de la consola, el contenido del búfer de pantalla se desplaza una fila hacia arriba y se descarta la fila superior del búfer de pantalla de la consola.
<p>Si este modo está deshabilitado, el último carácter de la fila se sobrescribe con los caracteres posteriores.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

 

 




