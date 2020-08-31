---
title: Función de devolución de llamada HandlerRoutine
description: Una función definida por la aplicación que se usa con la función SetConsoleCtrlHandler. Un proceso de consola usa esta función para controlar las señales de control recibidas por el proceso.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/HandlerRoutine
- wincon/HandlerRoutine
- HandlerRoutine
MS-HAID:
- '\_win32\_handlerroutine'
- base.handlerroutine
- consoles.handlerroutine
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2e8732fa-7dfd-415b-b2fc-c27a400496f2
topic_type:
- apiref
api_name:
- HandlerRoutine
api_location:
- Wincon.h
api_type:
- UserDefined
ms.openlocfilehash: 14205baaddd98c8c22881c5f448119412e1f4a1c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060868"
---
# <a name="handlerroutine-callback-function"></a>Función de devolución de llamada HandlerRoutine


Una función definida por la aplicación que se usa con la función [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) . Un proceso de consola usa esta función para controlar las señales de control recibidas por el proceso. Cuando se recibe la señal, el sistema crea un nuevo subproceso en el proceso para ejecutar la función.

El tipo de ** \_ rutina PHANDLER** define un puntero a esta función de devolución de llamada. **HandlerRoutine** es un marcador de posición para el nombre de la función definida por la aplicación.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI HandlerRoutine(
  _In_ DWORD dwCtrlType
);
```

<a name="parameters"></a>Parámetros
----------

*dwCtrlType* \[ de\]  
Tipo de señal de control recibida por el controlador. Este parámetro puede ser uno de los valores siguientes.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Valor</th>
<th>Significado</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="CTRL_C_EVENT"></span><span id="ctrl_c_event"></span>
<strong>CTRL_C_EVENT</strong> 0</td>
<td><p>Se recibió una señal CTRL + C, ya sea desde la entrada del teclado o desde una señal generada por la función <a href="generateconsolectrlevent.md" data-raw-source="[&lt;strong&gt;GenerateConsoleCtrlEvent&lt;/strong&gt;](generateconsolectrlevent.md)"><strong>GenerateConsoleCtrlEvent</strong></a> .</p></td>
</tr>
<tr class="even">
<td><span id="CTRL_BREAK_EVENT"></span><span id="ctrl_break_event"></span>
<strong>CTRL_BREAK_EVENT</strong> 1</td>
<td><p>Se recibió una señal CTRL + INTER, ya sea desde la entrada del teclado o desde una señal generada por <a href="generateconsolectrlevent.md" data-raw-source="[&lt;strong&gt;GenerateConsoleCtrlEvent&lt;/strong&gt;](generateconsolectrlevent.md)"><strong>GenerateConsoleCtrlEvent</strong></a>.</p></td>
</tr>
<tr class="odd">
<td><span id="CTRL_CLOSE_EVENT"></span><span id="ctrl_close_event"></span>
<strong>CTRL_CLOSE_EVENT</strong> 2</td>
<td><p>Señal que el sistema envía a todos los procesos conectados a una consola cuando el usuario cierra la consola (haciendo clic en <strong>cerrar</strong> en el menú de la ventana de la consola&#39;s o haciendo clic en el comando <strong>Finalizar tarea</strong> del administrador de tareas).</p></td>
</tr>
<tr class="even">
<td><span id="CTRL_LOGOFF_EVENT"></span><span id="ctrl_logoff_event"></span>
<strong>CTRL_LOGOFF_EVENT</strong> 5</td>
<td><p>Señal que el sistema envía a todos los procesos de la consola cuando un usuario cierra la sesión. Esta señal no indica qué usuario está cerrando la sesión, por lo que no se puede realizar ninguna suposición.</p>
<p>Tenga en cuenta que esta señal solo la reciben los servicios. Las aplicaciones interactivas se terminan al cerrar la sesión, por lo que no están presentes cuando el sistema envía esta señal.</p></td>
</tr>
<tr class="odd">
<td><span id="CTRL_SHUTDOWN_EVENT"></span><span id="ctrl_shutdown_event"></span>
<strong>CTRL_SHUTDOWN_EVENT</strong> 6</td>
<td><p>Señal que el sistema envía cuando el sistema se está cerrando. Las aplicaciones interactivas no están presentes en el momento en que el sistema envía esta señal, por lo que solo se pueden recibir servicios en esta situación. Los servicios también tienen su propio mecanismo de notificación para los eventos de cierre. Para obtener más información, consulte <a href="https://msdn.microsoft.com/library/windows/desktop/ms683240" data-raw-source="[&lt;strong&gt;Handler&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/ms683240)"><strong>controlador</strong></a>.</p>
<p>Esta señal también puede ser generada por una aplicación mediante <a href="generateconsolectrlevent.md" data-raw-source="[&lt;strong&gt;GenerateConsoleCtrlEvent&lt;/strong&gt;](generateconsolectrlevent.md)"><strong>GenerateConsoleCtrlEvent</strong></a>.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Valor devuelto
------------

Si la función controla la señal de control, debe devolver **true**. Si devuelve **false**, se usa la función de controlador siguiente en la lista de controladores para este proceso.

<a name="remarks"></a>Observaciones
-------

Dado que el sistema crea un nuevo subproceso en el proceso para ejecutar la función de controlador, es posible que otro subproceso termine la función de controlador en el proceso. Asegúrese de sincronizar los subprocesos del proceso con el subproceso de la función de controlador.

Cada proceso de consola tiene su propia lista de funciones de **HandlerRoutine** . Inicialmente, esta lista contiene solo una función de controlador predeterminada que llama a [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658). Un proceso de consola agrega o quita funciones de controlador adicionales mediante una llamada a la función [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) , que no afecta a la lista de funciones de controlador para otros procesos. Cuando un proceso de consola recibe cualquiera de las señales de control, se llama a sus funciones de controlador en la última base de registro, que se llama primero, hasta que uno de los controladores devuelve **true**. Si ninguno de los controladores devuelve **true**, se llama al controlador predeterminado.

Las señales de evento **Ctrl \_ Close \_ **, evento **Ctrl \_ Logoff \_ **y **Ctrl \_ Shutdown \_ ** proporcionan al proceso una oportunidad de limpieza antes de la finalización. Un **HandlerRoutine** puede realizar cualquier limpieza necesaria y, a continuación, realizar una de las siguientes acciones:

- Llame a la función [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) para finalizar el proceso.
- Devuelve **false**. Si ninguna de las funciones de controlador registradas devuelve **true**, el controlador predeterminado finaliza el proceso.
- Devuelve **true**. En este caso, no se llama a ninguna otra función de controlador y el sistema finaliza el proceso.

Un proceso puede usar la función [**SetProcessShutdownParameters**](https://msdn.microsoft.com/library/windows/desktop/ms686227) para evitar que el sistema muestre un cuadro de diálogo al usuario durante el cierre de sesión o apagado. En este caso, el sistema finaliza el proceso cuando **HandlerRoutine** devuelve **true** o cuando transcurre el período de tiempo de espera.

Cuando una aplicación de consola se ejecuta como un servicio, recibe un controlador de control de consola predeterminado modificado. Este controlador modificado no llama a [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) al procesar las señales de evento **Ctrl \_ Logoff \_ ** y **Ctrl \_ Shutdown \_ ** . Esto permite que el servicio siga ejecutándose después de que el usuario cierre la sesión. Si el servicio instala su propio controlador de control de consola, se llama a este controlador antes del controlador predeterminado. Si el controlador instalado llama a **ExitProcess** al procesar la señal del ** \_ \_ evento Ctrl Logoff** , el servicio se cierra cuando el usuario cierra la sesión.

Tenga en cuenta que una biblioteca de terceros o DLL puede instalar un controlador de control de consola para la aplicación. Si lo hace, este controlador invalida el controlador predeterminado y puede hacer que la aplicación se cierre cuando el usuario cierra la sesión.

## <a name="timeouts"></a>Tiempos de espera

| Evento                  | Circunstancias                   | Tiempo de espera                                                     |
|------------------------|---------------------------------|-------------------------------------------------------------|
| `CTRL_CLOSE_EVENT`     | _cualquier_                           | parámetro del sistema `SPI_GETHUNGAPPTIMEOUT` , 5.000 MS            |
| `CTRL_LOGOFF_EVENT`    | _rápido_[1] | clave del registro `CriticalAppShutdownTimeout` o 500 ms          |
| `CTRL_LOGOFF_EVENT`    | _ninguno de los anteriores_             | parámetro del sistema `SPI_GETWAITTOKILLTIMEOUT` , 5.000 MS         |
| `CTRL_SHUTDOWN_EVENT`  | **proceso de servicio**             | parámetro del sistema `SPI_GETWAITTOKILLSERVICETIMEOUT` , 20000ms |
| `CTRL_SHUTDOWN_EVENT`  | _rápido_[1] | clave del registro `CriticalAppShutdownTimeout` o 500 ms          |
| `CTRL_SHUTDOWN_EVENT`  | _ninguno de los anteriores_             | parámetro del sistema `SPI_GETWAITTOKILLTIMEOUT` , 5.000 MS         |
| `CTRL_C`, `CTRL_BREAK` | _cualquier_                           | **sin tiempo de espera**                                              |

_[1]: los eventos "rápidos" nunca se usan, pero todavía hay código para admitirlos._

<a name="requirements"></a>Requisitos
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Cliente mínimo compatible</p></td>
<td><p>Windows 2000 Professional [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="even">
<td><p>Servidor mínimo compatible</p></td>
<td><p>Windows 2000 Server [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="odd">
<td><p>Encabezado</p></td>
<td>ConsoleApi. h (a través de winCon. h, include Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vea también


[Controladores de control de consola](console-control-handlers.md)

[Funciones de la consola](console-functions.md)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetProcessShutdownParameters**](https://msdn.microsoft.com/library/windows/desktop/ms683221)

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md)

[**SetProcessShutdownParameters**](https://msdn.microsoft.com/library/windows/desktop/ms686227)

 

 




