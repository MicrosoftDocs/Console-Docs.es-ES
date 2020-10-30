---
title: Estructura de CONSOLE_HISTORY_INFO
description: Vea la información de referencia sobre la estructura de CONSOLE_HISTORY_INFO, que contiene información sobre el historial de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/CONSOLE_HISTORY_INFO
- wincon/CONSOLE_HISTORY_INFO
- CONSOLE_HISTORY_INFO
- consoleapi3/PCONSOLE_HISTORY_INFO
- wincon/PCONSOLE_HISTORY_INFO
- PCONSOLE_HISTORY_INFO
MS-HAID:
- base.console\_history\_info
- consoles.console\_history\_info
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: df7d2f12-5299-47ed-b1f6-2db903dba81b
topic_type:
- apiref
api_name:
- CONSOLE_HISTORY_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 24d41dca61146cc3e835f405889400ae0d168e7f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039223"
---
# <a name="console_history_info-structure"></a>Estructura de información del \_ historial de la consola \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contiene información sobre el historial de la consola.

## <a name="syntax"></a>Sintaxis

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

## <a name="members"></a>Miembros

**cbSize**  
Tamaño de la estructura, en bytes. Establezca este miembro en `sizeof(CONSOLE_HISTORY_INFO)` .

**HistoryBufferSize**  
El número de comandos que se mantienen en cada búfer del historial.

**NumberOfHistoryBuffers**  
El número de búferes de historial conservados para este proceso de consola.

**dwFlags**  
Este parámetro puede ser cero o el valor siguiente.

| Valor | Significado |
|-|-|
| **HISTORY_NO_DUP_FLAG** 0x1 | Las entradas duplicadas no se almacenarán en el búfer del historial.

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows Vista \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows Server 2008 \[\] |
| Encabezado | ConsoleApi3. h (a través de WinCon. h, include Windows. h) |

## <a name="see-also"></a>Consulte también

[**GetConsoleHistoryInfo**](getconsolehistoryinfo.md)

[**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)
