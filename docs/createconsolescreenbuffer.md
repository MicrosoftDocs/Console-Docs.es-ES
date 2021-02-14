---
title: CreateConsoleScreenBuffer función)
description: La función CreateConsoleScreenBuffer crea un búfer de pantalla para la consola de Windows.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/CreateConsoleScreenBuffer
- wincon/CreateConsoleScreenBuffer
- CreateConsoleScreenBuffer
MS-HAID:
- '\_win32\_createconsolescreenbuffer'
- base.createconsolescreenbuffer
- consoles.createconsolescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98bb74e4-dad2-4615-9263-48ba778a06ff
topic_type:
- apiref
api_name:
- CreateConsoleScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0e7e4606e561454a2037650cc8d1f3b685ff2d5d
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357965"
---
# <a name="createconsolescreenbuffer-function"></a>CreateConsoleScreenBuffer función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Crea un búfer de pantalla de la consola.

## <a name="syntax"></a>Sintaxis

```C
HANDLE WINAPI CreateConsoleScreenBuffer(
  _In_             DWORD               dwDesiredAccess,
  _In_             DWORD               dwShareMode,
  _In_opt_   const SECURITY_ATTRIBUTES *lpSecurityAttributes,
  _In_             DWORD               dwFlags,
  _Reserved_       LPVOID              lpScreenBufferData
);
```

## <a name="parameters"></a>Parámetros

*dwDesiredAccess* \[ de\]  
El acceso al búfer de pantalla de la consola. Para obtener una lista de derechos de acceso, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*dwShareMode* \[ de\]  
Este parámetro puede ser cero, lo que indica que no se puede compartir el búfer o puede ser uno o varios de los valores siguientes.

| Valor | Significado |
|-|-|
| **FILE_SHARE_READ** 0x00000001 | Se pueden realizar otras operaciones de apertura en el búfer de pantalla de la consola para tener acceso de lectura. |
| **FILE_SHARE_WRITE** 0x00000002 | Se pueden realizar otras operaciones de apertura en el búfer de pantalla de la consola para el acceso de escritura. |

*lpSecurityAttributes* \[ en, opcional\]  
Puntero a una estructura [**de \_ atributos de seguridad**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85)) que determina si los procesos secundarios pueden heredar el identificador devuelto. Si *lpSecurityAttributes* es **null**, el identificador no se puede heredar. El miembro **lpSecurityDescriptor** de la estructura especifica un descriptor de seguridad para el nuevo búfer de pantalla de la consola. Si *lpSecurityAttributes* es **null**, el búfer de pantalla de la consola obtiene un descriptor de seguridad predeterminado. Las ACL del descriptor de seguridad predeterminado para un búfer de pantalla de la consola proceden del token principal o de suplantación del creador.

*dwFlags* \[ de\]  
El tipo de búfer de pantalla de la consola que se va a crear. El único tipo de búfer de pantalla compatible es el **\_ \_ búfer TEXTMODE** de la consola.

*lpScreenBufferData*  
Sector debe ser **null**.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es un identificador del nuevo búfer de pantalla de la consola.

Si la función no se ejecuta correctamente, el valor devuelto es **INVALID\_HANDLE\_VALUE**. Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Comentarios

Una consola de puede tener varios búferes de pantalla, pero solo un búfer de pantalla activo. Se puede tener acceso a los búferes de pantalla inactivos para lectura y escritura, pero solo se muestra el búfer de pantalla activo. Para convertir el nuevo búfer de pantalla en el búfer de pantalla activo, utilice la función [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) .

El búfer de pantalla recién creado copiará algunas propiedades del búfer de pantalla activo en el momento en que se llama a esta función. El comportamiento es el siguiente:

- `Font` -copiado del búfer de pantalla activo
- `Display Window Size` -copiado del búfer de pantalla activo
- `Buffer Size` -coincide con `Display Window Size` (**no** copiado)
- `Default Attributes` (colores): copiado del búfer de pantalla activo
- `Default Popup Attributes` (colores): copiado del búfer de pantalla activo

El proceso de llamada puede usar el identificador devuelto en cualquier función que requiera un identificador a un búfer de pantalla de la consola, de acuerdo con las limitaciones de acceso especificadas por el parámetro *dwDesiredAccess* .

El proceso de llamada puede usar la función [**DuplicateHandle**](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle) para crear un controlador de búfer de pantalla duplicado que tenga un acceso o una herencia diferentes del identificador original. Sin embargo, **DuplicateHandle** no se puede usar para crear un duplicado que sea válido para un proceso diferente (excepto a través de la herencia).

Para cerrar el identificador de búfer de pantalla de la consola, use la función [**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle) .

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, vea [lectura y escritura de bloques de caracteres y atributos](reading-and-writing-blocks-of-characters-and-attributes.md).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Professional |
| Servidor mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Server |
| Encabezado | ConsoleApi2. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32.lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Vea también

[Funciones de la consola](console-functions.md)

[Búferes de pantalla de la consola](console-screen-buffers.md)

[**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle)

[**DuplicateHandle**](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**atributos de seguridad \_**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85))

[**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)