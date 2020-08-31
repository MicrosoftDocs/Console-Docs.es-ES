---
title: WriteConsole función)
description: Escribe una cadena de caracteres en un búfer de pantalla de la consola a partir de la ubicación actual del cursor.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/WriteConsole
- wincon/WriteConsole
- WriteConsole
- consoleapi/WriteConsoleA
- wincon/WriteConsoleA
- WriteConsoleA
- consoleapi/WriteConsoleW
- wincon/WriteConsoleW
- WriteConsoleW
MS-HAID:
- '\_win32\_writeconsole'
- base.writeconsole
- consoles.writeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1a13d9ef-75a9-49fd-9717-207f18612b59
topic_type:
- apiref
api_name:
- WriteConsole
- WriteConsoleA
- WriteConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: de5138326c0800016cf5ca6e3232f032abcd01de
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061052"
---
# <a name="writeconsole-function"></a>WriteConsole función)


Escribe una cadena de caracteres en un búfer de pantalla de la consola a partir de la ubicación actual del cursor.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

<a name="parameters"></a>Parámetros
----------

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de ** \_ escritura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*lpBuffer* \[ de\]  
Un puntero a un búfer que contiene los caracteres que se van a escribir en el búfer de pantalla de la consola.

*nNumberOfCharsToWrite* \[ de\]  
El número de caracteres que se va a escribir. Si el tamaño total del número de caracteres especificado supera el montón disponible, se produce un error en la función y ** \_ no \_ hay suficiente \_ memoria**.

*lpNumberOfCharsWritten* \[ out, opcional\]  
Puntero a una variable que recibe el número de caracteres escritos realmente.

*lpReserved*   
Sector debe ser **null**.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

La función **WriteConsole** escribe caracteres en el búfer de pantalla de la consola en la posición actual del cursor. La posición del cursor avanza a medida que se escriben caracteres. La función [**SetConsoleCursorPosition**](setconsolecursorposition.md) establece la posición actual del cursor.

Los caracteres se escriben con los atributos de color de primer plano y de fondo asociados al búfer de pantalla de la consola. La función [**SetConsoleTextAttribute**](setconsoletextattribute.md) cambia estos colores. Para determinar los atributos de color actuales y la posición actual del cursor, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).

Todos los modos de entrada que afectan al comportamiento de la función [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) tienen el mismo efecto en **WriteConsole**. Para recuperar y establecer los modos de salida de un búfer de pantalla de la consola, use las funciones [**GetConsoleMode**](getconsolemode.md) y [**SetConsoleMode**](setconsolemode.md) .

La función **WriteConsole** usa caracteres Unicode o caracteres ANSI de la página de códigos actual de la consola. La página de códigos de la consola tiene como valor predeterminado la página de códigos OEM del sistema. Para cambiar la página de códigos de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) , o bien use los comandos **chcp** o **mode con CP Select =** .

**WriteConsole** produce un error si se usa con un identificador estándar que se redirige a un archivo. Si una aplicación procesa una salida multilingüe que se puede redirigir, determine si el identificador de salida es un identificador de consola (un método es llamar a la función [**GetConsoleMode**](getconsolemode.md) y comprobar si se realiza correctamente). Si el identificador es un identificador de consola, llame a **WriteConsole**. Si el identificador no es un identificador de consola, se redirige el resultado y se debe llamar a [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) para realizar la e/s. Asegúrese de prefijar un archivo de texto sin formato Unicode con una marca de orden de bytes. Para obtener más información, vea [usar marcas de orden de bytes](https://msdn.microsoft.com/library/windows/desktop/dd374101).

Aunque una aplicación puede usar **WriteConsole** en modo ANSI para escribir caracteres ANSI, las consolas no admiten secuencias de escape ANSI. Sin embargo, algunas funciones proporcionan una funcionalidad equivalente. Para obtener más información, vea [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md)y [**GetConsoleCursorInfo**](getconsolecursorinfo.md).

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
<tr class="even">
<td><p>Biblioteca</p></td>
<td>Kernel32. lib</td>
</tr>
<tr class="odd">
<td><p>Archivo DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
<td><p>Nombres Unicode y ANSI</p></td>
<td><p><strong>WriteConsoleW</strong> (Unicode) y <strong>WriteConsoleA</strong> (ANSI)</p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vea también


[Funciones de la consola](console-functions.md)

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**GetConsoleMode**](getconsolemode.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[Métodos de entrada y salida](input-and-output-methods.md)

[**ReadConsole**](readconsole.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleMode**](setconsolemode.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleTextAttribute**](setconsoletextattribute.md)

[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)

[**Escritura**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




