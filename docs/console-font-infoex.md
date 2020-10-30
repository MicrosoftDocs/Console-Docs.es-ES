---
title: Estructura de CONSOLE_FONT_INFOEX
description: Vea la información de referencia sobre la estructura de CONSOLE_FONT_INFOEX, que contiene información extendida para una fuente de consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/CONSOLE_FONT_INFOEX
- wincon/CONSOLE_FONT_INFOEX
- CONSOLE_FONT_INFOEX
- consoleapi3/PCONSOLE_FONT_INFOEX
- wincon/PCONSOLE_FONT_INFOEX
- PCONSOLE_FONT_INFOEX
MS-HAID:
- base.console\_font\_infoex
- consoles.console\_font\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e9a087e1-264d-4d48-8adb-771a0e35b511
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFOEX
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: ef89d1bf47a4153d44140d3f9f4845bb7496680e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039263"
---
# <a name="console_font_infoex-structure"></a><span data-ttu-id="05e55-104">\_ \_ Estructura INFOEX de la consola</span><span class="sxs-lookup"><span data-stu-id="05e55-104">CONSOLE\_FONT\_INFOEX structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="05e55-105">Contiene información extendida para una fuente de consola.</span><span class="sxs-lookup"><span data-stu-id="05e55-105">Contains extended information for a console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="05e55-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="05e55-106">Syntax</span></span>

```C
typedef struct _CONSOLE_FONT_INFOEX {
  ULONG cbSize;
  DWORD nFont;
  COORD dwFontSize;
  UINT  FontFamily;
  UINT  FontWeight;
  WCHAR FaceName[LF_FACESIZE];
} CONSOLE_FONT_INFOEX, *PCONSOLE_FONT_INFOEX;
```

## <a name="members"></a><span data-ttu-id="05e55-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="05e55-107">Members</span></span>

<span data-ttu-id="05e55-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="05e55-108">**cbSize**</span></span>  
<span data-ttu-id="05e55-109">Tamaño de esta estructura, en bytes.</span><span class="sxs-lookup"><span data-stu-id="05e55-109">The size of this structure, in bytes.</span></span> <span data-ttu-id="05e55-110">Este miembro debe establecerse en `sizeof(CONSOLE_FONT_INFOEX)` antes de llamar a [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) o se producirá un error.</span><span class="sxs-lookup"><span data-stu-id="05e55-110">This member must be set to `sizeof(CONSOLE_FONT_INFOEX)` before calling [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) or it will fail.</span></span>

<span data-ttu-id="05e55-111">**nFont**</span><span class="sxs-lookup"><span data-stu-id="05e55-111">**nFont**</span></span>  
<span data-ttu-id="05e55-112">Índice de la fuente en la tabla de fuentes de la consola del sistema.</span><span class="sxs-lookup"><span data-stu-id="05e55-112">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="05e55-113">**dwFontSize**</span><span class="sxs-lookup"><span data-stu-id="05e55-113">**dwFontSize**</span></span>  
<span data-ttu-id="05e55-114">Una estructura de [**coordenadas**](coord-str.md) que contiene el ancho y el alto de cada carácter de la fuente, en unidades lógicas.</span><span class="sxs-lookup"><span data-stu-id="05e55-114">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="05e55-115">El miembro **X** contiene el ancho, mientras que el miembro **Y** contiene el alto.</span><span class="sxs-lookup"><span data-stu-id="05e55-115">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="05e55-116">**FontFamily**</span><span class="sxs-lookup"><span data-stu-id="05e55-116">**FontFamily**</span></span>  
<span data-ttu-id="05e55-117">El paso y la familia de la fuente.</span><span class="sxs-lookup"><span data-stu-id="05e55-117">The font pitch and family.</span></span> <span data-ttu-id="05e55-118">Para obtener información sobre los valores posibles para este miembro, vea la descripción del miembro **tmPitchAndFamily** de la estructura [**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132) .</span><span class="sxs-lookup"><span data-stu-id="05e55-118">For information about the possible values for this member, see the description of the **tmPitchAndFamily** member of the [**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132) structure.</span></span>

<span data-ttu-id="05e55-119">**FontWeight**</span><span class="sxs-lookup"><span data-stu-id="05e55-119">**FontWeight**</span></span>  
<span data-ttu-id="05e55-120">Espesor de la fuente.</span><span class="sxs-lookup"><span data-stu-id="05e55-120">The font weight.</span></span> <span data-ttu-id="05e55-121">El peso puede oscilar entre 100 y 1000, en múltiplos de 100.</span><span class="sxs-lookup"><span data-stu-id="05e55-121">The weight can range from 100 to 1000, in multiples of 100.</span></span> <span data-ttu-id="05e55-122">Por ejemplo, el peso normal es 400, mientras que 700 está en negrita.</span><span class="sxs-lookup"><span data-stu-id="05e55-122">For example, the normal weight is 400, while 700 is bold.</span></span>

<span data-ttu-id="05e55-123">**FaceName**</span><span class="sxs-lookup"><span data-stu-id="05e55-123">**FaceName**</span></span>  
<span data-ttu-id="05e55-124">Nombre del tipo de letra (por ejemplo, Courier o Arial).</span><span class="sxs-lookup"><span data-stu-id="05e55-124">The name of the typeface (such as Courier or Arial).</span></span>

## <a name="remarks"></a><span data-ttu-id="05e55-125">Comentarios</span><span class="sxs-lookup"><span data-stu-id="05e55-125">Remarks</span></span>

<span data-ttu-id="05e55-126">Para obtener el tamaño de la fuente, pase el índice de fuente a la función [**GetConsoleFontSize**](getconsolefontsize.md) .</span><span class="sxs-lookup"><span data-stu-id="05e55-126">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="05e55-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="05e55-127">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="05e55-128">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="05e55-128">Minimum supported client</span></span> | <span data-ttu-id="05e55-129">Solo aplicaciones de escritorio de Windows Vista \[\]</span><span class="sxs-lookup"><span data-stu-id="05e55-129">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="05e55-130">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="05e55-130">Minimum supported server</span></span> | <span data-ttu-id="05e55-131">Solo aplicaciones de escritorio de Windows Server 2008 \[\]</span><span class="sxs-lookup"><span data-stu-id="05e55-131">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="05e55-132">Encabezado</span><span class="sxs-lookup"><span data-stu-id="05e55-132">Header</span></span> | <span data-ttu-id="05e55-133">WinCon. h (incluir Windows. h)</span><span class="sxs-lookup"><span data-stu-id="05e55-133">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="05e55-134">Consulte también</span><span class="sxs-lookup"><span data-stu-id="05e55-134">See also</span></span>

[<span data-ttu-id="05e55-135">**GetCurrentConsoleFontEx**</span><span class="sxs-lookup"><span data-stu-id="05e55-135">**GetCurrentConsoleFontEx**</span></span>](getcurrentconsolefontex.md)
