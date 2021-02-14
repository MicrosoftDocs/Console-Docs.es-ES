---
title: SetConsoleWindowInfo función)
description: Establece el tamaño y la posición actuales de la ventana de un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleWindowInfo
- wincon/SetConsoleWindowInfo
- SetConsoleWindowInfo
MS-HAID:
- '\_win32\_setconsolewindowinfo'
- base.setconsolewindowinfo
- consoles.setconsolewindowinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad16a8fe-ca91-41d6-93b1-8cce6d54b1da
topic_type:
- apiref
api_name:
- SetConsoleWindowInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: af3f9d63b01697a2ab0735014a4836d9ab11d8cf
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358535"
---
# <a name="setconsolewindowinfo-function"></a>SetConsoleWindowInfo función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Establece el tamaño y la posición actuales de la ventana de un búfer de pantalla de la consola.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI SetConsoleWindowInfo(
  _In_       HANDLE     hConsoleOutput,
  _In_       BOOL       bAbsolute,
  _In_ const SMALL_RECT *lpConsoleWindow
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[in\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener derecho de acceso de **GENERIC\_READ**. Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).

*bAbsolute* \[ de\]  
Si este parámetro es **true**, las coordenadas especifican las nuevas esquinas superior izquierda e inferior derecha de la ventana. Si es **false**, las coordenadas son relativas a las coordenadas de la esquina de la ventana actual.

*lpConsoleWindow* \[ de\]  
Puntero a una [**pequeña estructura \_ Rect**](small-rect-str.md) que especifica las nuevas esquinas superior izquierda e inferior derecha de la ventana.

## <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Comentarios

Se produce un error en la función si el rectángulo de la ventana especificado se extiende más allá de los límites del búfer de pantalla de la consola. Esto significa que los miembros **superior** e **izquierdo** del rectángulo *lpConsoleWindow* (o las coordenadas superior e izquierda calculadas, si *bAbsolute* es false) no pueden ser menores que cero. Del mismo modo, los miembros **inferior** y **derecho** (o las coordenadas inferior y derecha calculadas) no pueden ser mayores que (alto del búfer de pantalla – 1) y (ancho del búfer de pantalla – 1), respectivamente. También se produce un error en la función si el miembro **derecho** (o la coordenada derecha calculada) es menor o igual que el miembro **izquierdo** (o la coordenada izquierda calculada) o si el miembro **inferior** (o la coordenada inferior calculada) es menor o igual que el miembro **superior** (o la coordenada superior calculada).

En el caso de las consolas de más de un búfer de pantalla, el cambio de la ubicación de la ventana para un búfer de pantalla no afecta a las ubicaciones de ventana de los otros búferes de pantalla.

Para determinar el tamaño y la posición actuales de la ventana de un búfer de pantalla, utilice la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) . Esta función también devuelve el tamaño máximo de la ventana, dado el tamaño actual del búfer de pantalla, el tamaño de fuente actual y el tamaño de la pantalla. La función [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) devuelve el tamaño máximo de la ventana a partir de la fuente actual y los tamaños de pantalla, pero no tiene en cuenta el tamaño del búfer de pantalla de la consola.

**SetConsoleWindowInfo** se puede usar para desplazarse por el contenido del búfer de pantalla de la consola desplazando la posición del rectángulo de la ventana sin cambiar su tamaño.

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, vea [desplazarse por la ventana de un búfer de pantalla](scrolling-a-screen-buffer-s-window.md).

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

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[Desplazarse por el búfer de pantalla](scrolling-the-screen-buffer.md)

[**PEQUEÑO \_ rectángulo**](small-rect-str.md)