---
title: Estructura de WINDOW_BUFFER_SIZE_RECORD
description: Vea información de referencia sobre la estructura de WINDOW_BUFFER_SIZE_RECORD, que describe un cambio en el tamaño del búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/WINDOW_BUFFER_SIZE_RECORD
- wincon/WINDOW_BUFFER_SIZE_RECORD
- WINDOW_BUFFER_SIZE_RECORD
- wincontypes/PWINDOW_BUFFER_SIZE_RECORD
- wincon/PWINDOW_BUFFER_SIZE_RECORD
- PWINDOW_BUFFER_SIZE_RECORD
MS-HAID:
- '\_win32\_window\_buffer\_size\_record\_str'
- base.window\_buffer\_size\_record\_str
- consoles.window\_buffer\_size\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f2875e8-aa09-455b-a923-7cc388525b98
topic_type:
- apiref
api_name:
- WINDOW_BUFFER_SIZE_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 0041c4390fe331302df458965faec0ace2d1888f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061109"
---
# <a name="window_buffer_size_record-structure"></a><span data-ttu-id="b97d6-104">\_Estructura de \_ registro del tamaño del búfer de ventana \_</span><span class="sxs-lookup"><span data-stu-id="b97d6-104">WINDOW\_BUFFER\_SIZE\_RECORD structure</span></span>


<span data-ttu-id="b97d6-105">Describe un cambio en el tamaño del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="b97d6-105">Describes a change in the size of the console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="b97d6-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b97d6-106">Syntax</span></span>
------

```C
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

<a name="members"></a><span data-ttu-id="b97d6-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="b97d6-107">Members</span></span>
-------

<span data-ttu-id="b97d6-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="b97d6-108">**dwSize**</span></span>  
<span data-ttu-id="b97d6-109">Una estructura de [**coordenadas**](coord-str.md) que contiene el tamaño del búfer de pantalla de la consola, en columnas y filas de celda de carácter.</span><span class="sxs-lookup"><span data-stu-id="b97d6-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character cell columns and rows.</span></span>

<a name="remarks"></a><span data-ttu-id="b97d6-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b97d6-110">Remarks</span></span>
-------

<span data-ttu-id="b97d6-111">Los eventos de tamaño de búfer se colocan en el búfer de entrada cuando la consola está en modo de ventana (**habilitar \_ \_ entrada de ventana**).</span><span class="sxs-lookup"><span data-stu-id="b97d6-111">Buffer size events are placed in the input buffer when the console is in window-aware mode (**ENABLE\_WINDOW\_INPUT**).</span></span>

<a name="examples"></a><span data-ttu-id="b97d6-112">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="b97d6-112">Examples</span></span>
--------

<span data-ttu-id="b97d6-113">Para obtener un ejemplo, vea [leer eventos de búfer de entrada](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="b97d6-113">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="b97d6-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b97d6-114">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b97d6-115">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="b97d6-115">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="b97d6-116">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="b97d6-116">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b97d6-117">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="b97d6-117">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="b97d6-118">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="b97d6-118">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b97d6-119">Encabezado</span><span class="sxs-lookup"><span data-stu-id="b97d6-119">Header</span></span></p></td>
<td><span data-ttu-id="b97d6-120">WinConTypes. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b97d6-120">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="b97d6-121"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="b97d6-121"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="b97d6-122">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="b97d6-122">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="b97d6-123">**registro de entrada \_**</span><span class="sxs-lookup"><span data-stu-id="b97d6-123">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="b97d6-124">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="b97d6-124">**ReadConsoleInput**</span></span>](readconsoleinput.md)

 

 




