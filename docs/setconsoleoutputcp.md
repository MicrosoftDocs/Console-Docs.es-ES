---
title: SetConsoleOutputCP función)
description: Establece la página de códigos de salida utilizada por la consola asociada al proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleOutputCP
- wincon/SetConsoleOutputCP
- SetConsoleOutputCP
MS-HAID:
- '\_win32\_setconsoleoutputcp'
- base.setconsoleoutputcp
- consoles.setconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0b41e66b-ca19-4d69-9f39-92da158344ef
topic_type:
- apiref
api_name:
- SetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 85b6ba4d829b86b99138efbdaa14284429d2aa81
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039343"
---
# <a name="setconsoleoutputcp-function"></a>SetConsoleOutputCP función)

Establece la página de códigos de salida utilizada por la consola asociada al proceso de llamada. Una consola usa su página de códigos de salida para traducir los valores de caracteres escritos por las distintas funciones de salida en las imágenes que se muestran en la ventana de la consola.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI SetConsoleOutputCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a>Parámetros

*wCodePageID* \[ de\]  
Identificador de la página de códigos que se va a establecer. Para obtener más información, vea la sección Comentarios.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

Una página de códigos asigna códigos de caracteres de 256 a caracteres individuales. Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas.

Si la fuente actual es una fuente Unicode de punto fijo, **SetConsoleOutputCP** cambia la asignación de los valores de caracteres en el conjunto de glifos de la fuente, en lugar de cargar una fuente independiente cada vez que se llama. Esto afecta al modo en que se muestran los caracteres extendidos (valor ASCII superior a 127) en una ventana de consola. Sin embargo, si la fuente actual es una fuente de trama, **SetConsoleOutputCP** no afecta al modo en que se muestran los caracteres extendidos.

Para buscar las páginas de códigos que el sistema operativo instala o admite, utilice la función [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) . Los identificadores de las páginas de códigos disponibles en el equipo local también se almacenan en el registro con la siguiente clave:

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

Sin embargo, es mejor usar [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) para enumerar las páginas de códigos, ya que el registro puede diferir en diferentes versiones de Windows.
Para determinar si una página de códigos determinada es válida, utilice la función [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) . Para recuperar más información sobre una página de códigos, incluido su nombre, utilice la función [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) . Para obtener una lista de los identificadores de página de códigos disponibles, vea [identificadores de páginas de códigos](https://msdn.microsoft.com/library/windows/desktop/dd317756).

Para determinar la página de códigos de salida actual de la consola, use la función [**GetConsoleOutputCP**](getconsoleoutputcp.md) . Para establecer y recuperar una página de códigos de entrada de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) y [**GetConsoleCP**](getconsolecp.md) .

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | ConsoleApi2. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Consulte también

[Páginas de código de la consola](console-code-pages.md)

[Funciones de la consola](console-functions.md)

[**GetConsoleCP**](getconsolecp.md)

[**GetConsoleOutputCP**](getconsoleoutputcp.md)

[**SetConsoleCP**](setconsolecp.md)
