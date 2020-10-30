---
title: SetConsoleCP función)
description: Establece la página de códigos de entrada utilizada por la consola asociada al proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleCP
- wincon/SetConsoleCP
- SetConsoleCP
MS-HAID:
- '\_win32\_setconsolecp'
- base.setconsolecp
- consoles.setconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a1a9ba5-c792-491d-ae51-979f462dcb53
topic_type:
- apiref
api_name:
- SetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 644f4d925b31da94f42a465d4bce21bb2dc2ecf9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039413"
---
# <a name="setconsolecp-function"></a>SetConsoleCP función)

Establece la página de códigos de entrada utilizada por la consola asociada al proceso de llamada. Una consola usa su página de códigos de entrada para traducir la entrada del teclado en el valor de carácter correspondiente.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI SetConsoleCP(
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

Para buscar las páginas de códigos que el sistema operativo instala o admite, utilice la función [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) . Los identificadores de las páginas de códigos disponibles en el equipo local también se almacenan en el registro con la siguiente clave:

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

Sin embargo, es mejor usar [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) para enumerar las páginas de códigos, ya que el registro puede diferir en diferentes versiones de Windows.

Para determinar si una página de códigos determinada es válida, utilice la función [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) . Para recuperar más información sobre una página de códigos, incluido su nombre, utilice la función [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) . Para obtener una lista de los identificadores de página de códigos disponibles, vea [identificadores de páginas de códigos](https://msdn.microsoft.com/library/windows/desktop/dd317756).

Para determinar la página de códigos de entrada actual de la consola, use la función [**GetConsoleCP**](getconsolecp.md) . Para establecer y recuperar la página de códigos de salida de una consola, use las funciones [**SetConsoleOutputCP**](setconsoleoutputcp.md) y [**GetConsoleOutputCP**](getconsoleoutputcp.md) .

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

[**SetConsoleOutputCP**](setconsoleoutputcp.md)
