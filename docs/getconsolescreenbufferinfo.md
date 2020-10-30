---
title: GetConsoleScreenBufferInfo función)
description: Vea la información de referencia sobre la función GetConsoleScreenBufferInfo, que recupera información sobre el búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfo
- wincon/GetConsoleScreenBufferInfo
- GetConsoleScreenBufferInfo
ms.assetid: eafe819e-a99a-4ce1-8898-8860444a31af
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 251fc71ef58840a962e5c1e09e88474959de27ae
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038773"
---
# <a name="getconsolescreenbufferinfo-function"></a>GetConsoleScreenBufferInfo función)

Recupera información sobre el búfer de pantalla de la consola especificado.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de **\_ lectura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*lpConsoleScreenBufferInfo* \[ enuncia\]  
Puntero a una estructura [**de \_ \_ \_ información del búfer de pantalla**](console-screen-buffer-info-str.md) de la consola que recibe la información del búfer de la pantalla de la consola.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

El rectángulo devuelto en el miembro **srWindow** de la estructura de información de búfer de pantalla de la consola se puede modificar y, a continuación, pasar a la función [**SetConsoleWindowInfo**](setconsolewindowinfo.md) para desplazarse por el búfer de pantalla de la ventana, para cambiar el tamaño de la ventana o ambos. [**\_ \_ \_**](console-screen-buffer-info-str.md)

Todas las coordenadas devueltas en la estructura de [**\_ información de \_ búfer \_ de pantalla**](console-screen-buffer-info-str.md) de la consola se encuentran en coordenadas de celda de carácter, donde el origen (0,0) está en la esquina superior izquierda del búfer de pantalla de la consola.

> [!TIP]
> Esta API no tiene un equivalente de **[terminal virtual](console-virtual-terminal-sequences.md)** . Es posible que su uso siga siendo necesario para las aplicaciones que intentan dibujar columnas, cuadrículas o rellenar la pantalla para recuperar el tamaño de la ventana. El estado de esta ventana se administra mediante los TTY/PTY/Pseudoconsole fuera del flujo de flujo normal y generalmente se considera un privilegio de usuario no ajustable por la aplicación cliente. Se pueden recibir actualizaciones en [**ReadConsoleInput**](readconsoleinput.md).

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, vea [desplazarse por la ventana de un búfer de pantalla](scrolling-a-screen-buffer-s-window.md).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | ConsoleApi2. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Consulte también

[Funciones de la consola](console-functions.md)

[**\_información del \_ búfer de pantalla de la consola \_**](console-screen-buffer-info-str.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[Tamaño de búfer de ventana y pantalla](window-and-screen-buffer-size.md)
