---
title: Estructura de CONSOLE_FONT_INFO
description: Vea la información de referencia sobre la estructura de CONSOLE_FONT_INFO, que contiene el índice y el tamaño de una fuente de consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/CONSOLE_FONT_INFO
- wincon/CONSOLE_FONT_INFO
- CONSOLE_FONT_INFO
- wincontypes/PCONSOLE_FONT_INFO
- wincon/PCONSOLE_FONT_INFO
- PCONSOLE_FONT_INFO
MS-HAID:
- '\_win32\_console\_font\_info\_str'
- base.console\_font\_info\_str
- consoles.console\_font\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 380b8183-1964-46f2-a511-01f39f21f5c5
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: c4218c53eacd95d67f3dc9056f5a1024ac1a8ab0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060869"
---
# <a name="console_font_info-structure"></a><span data-ttu-id="e2743-104">Estructura de información de \_ fuente de consola \_</span><span class="sxs-lookup"><span data-stu-id="e2743-104">CONSOLE\_FONT\_INFO structure</span></span>


<span data-ttu-id="e2743-105">Contiene información de una fuente de consola.</span><span class="sxs-lookup"><span data-stu-id="e2743-105">Contains information for a console font.</span></span>

<a name="syntax"></a><span data-ttu-id="e2743-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e2743-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

<a name="members"></a><span data-ttu-id="e2743-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="e2743-107">Members</span></span>
-------

<span data-ttu-id="e2743-108">**nFont**</span><span class="sxs-lookup"><span data-stu-id="e2743-108">**nFont**</span></span>  
<span data-ttu-id="e2743-109">Índice de la fuente en la tabla de fuentes de la consola del sistema.</span><span class="sxs-lookup"><span data-stu-id="e2743-109">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="e2743-110">**dwFontSize**</span><span class="sxs-lookup"><span data-stu-id="e2743-110">**dwFontSize**</span></span>  
<span data-ttu-id="e2743-111">Una estructura de [**coordenadas**](coord-str.md) que contiene el ancho y el alto de cada carácter de la fuente, en unidades lógicas.</span><span class="sxs-lookup"><span data-stu-id="e2743-111">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="e2743-112">El miembro **X** contiene el ancho, mientras que el miembro **Y** contiene el alto.</span><span class="sxs-lookup"><span data-stu-id="e2743-112">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<a name="remarks"></a><span data-ttu-id="e2743-113">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e2743-113">Remarks</span></span>
-------

<span data-ttu-id="e2743-114">Para obtener el tamaño de la fuente, pase el índice de fuente a la función [**GetConsoleFontSize**](getconsolefontsize.md) .</span><span class="sxs-lookup"><span data-stu-id="e2743-114">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

<a name="requirements"></a><span data-ttu-id="e2743-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e2743-115">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e2743-116">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="e2743-116">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="e2743-117">Windows XP [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="e2743-117">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e2743-118">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="e2743-118">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="e2743-119">Windows Server 2003 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="e2743-119">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e2743-120">Encabezado</span><span class="sxs-lookup"><span data-stu-id="e2743-120">Header</span></span></p></td>
<td><span data-ttu-id="e2743-121">WINCON. h (incluir Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e2743-121">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="e2743-122"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="e2743-122"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="e2743-123">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="e2743-123">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="e2743-124">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="e2743-124">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)

 

 




