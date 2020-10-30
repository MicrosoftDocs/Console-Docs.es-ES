---
title: ScrollConsoleScreenBuffer función)
description: Vea la información de referencia sobre la función ScrollConsoleScreenBuffer, que mueve un bloque de datos en un búfer de pantalla.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/ScrollConsoleScreenBuffer
- wincon/ScrollConsoleScreenBuffer
- ScrollConsoleScreenBuffer
- consoleapi2/ScrollConsoleScreenBufferA
- wincon/ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferA
- consoleapi2/ScrollConsoleScreenBufferW
- wincon/ScrollConsoleScreenBufferW
- ScrollConsoleScreenBufferW
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d78bf4c9-2314-466c-b617-619259c824b5
topic_type:
- apiref
api_name:
- ScrollConsoleScreenBuffer
- ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4ebe6efa246d627add041a5ef188fbb81294fb61
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039463"
---
# <a name="scrollconsolescreenbuffer-function"></a><span data-ttu-id="e16da-104">ScrollConsoleScreenBuffer función)</span><span class="sxs-lookup"><span data-stu-id="e16da-104">ScrollConsoleScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="e16da-105">Mueve un bloque de datos en un búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="e16da-105">Moves a block of data in a screen buffer.</span></span> <span data-ttu-id="e16da-106">Los efectos del movimiento se pueden limitar especificando un rectángulo de recorte, por lo que el contenido del búfer de pantalla de la consola fuera del rectángulo de recorte no se modifica.</span><span class="sxs-lookup"><span data-stu-id="e16da-106">The effects of the move can be limited by specifying a clipping rectangle, so the contents of the console screen buffer outside the clipping rectangle are unchanged.</span></span>

## <a name="syntax"></a><span data-ttu-id="e16da-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e16da-107">Syntax</span></span>

```C
BOOL WINAPI ScrollConsoleScreenBuffer(
  _In_           HANDLE     hConsoleOutput,
  _In_     const SMALL_RECT *lpScrollRectangle,
  _In_opt_ const SMALL_RECT *lpClipRectangle,
  _In_           COORD      dwDestinationOrigin,
  _In_     const CHAR_INFO  *lpFill
);
```

## <a name="parameters"></a><span data-ttu-id="e16da-108">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e16da-108">Parameters</span></span>

<span data-ttu-id="e16da-109">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="e16da-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="e16da-110">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="e16da-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="e16da-111">El identificador debe tener el derecho de acceso de **\_ lectura genérico** .</span><span class="sxs-lookup"><span data-stu-id="e16da-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="e16da-112">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="e16da-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="e16da-113">*lpScrollRectangle* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="e16da-113">*lpScrollRectangle* \[in\]</span></span>  
<span data-ttu-id="e16da-114">Puntero a una [**pequeña estructura \_ Rect**](small-rect-str.md) cuyos miembros especifican las coordenadas superior izquierda e inferior derecha del rectángulo del búfer de pantalla de la consola que se va a desplace.</span><span class="sxs-lookup"><span data-stu-id="e16da-114">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure whose members specify the upper-left and lower-right coordinates of the console screen buffer rectangle to be moved.</span></span>

<span data-ttu-id="e16da-115">*lpClipRectangle* \[ en, opcional\]</span><span class="sxs-lookup"><span data-stu-id="e16da-115">*lpClipRectangle* \[in, optional\]</span></span>  
<span data-ttu-id="e16da-116">Puntero a una [**pequeña estructura \_ Rect**](small-rect-str.md) cuyos miembros especifican las coordenadas superior izquierda e inferior derecha del rectángulo del búfer de pantalla de la consola que se ve afectado por el desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="e16da-116">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure whose members specify the upper-left and lower-right coordinates of the console screen buffer rectangle that is affected by the scrolling.</span></span> <span data-ttu-id="e16da-117">Este puntero puede ser **null** .</span><span class="sxs-lookup"><span data-stu-id="e16da-117">This pointer can be **NULL** .</span></span>

<span data-ttu-id="e16da-118">*dwDestinationOrigin* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="e16da-118">*dwDestinationOrigin* \[in\]</span></span>  
<span data-ttu-id="e16da-119">Estructura de [**coordenadas**](coord-str.md) que especifica la esquina superior izquierda de la nueva ubicación del contenido de *lpScrollRectangle* , en caracteres.</span><span class="sxs-lookup"><span data-stu-id="e16da-119">A [**COORD**](coord-str.md) structure that specifies the upper-left corner of the new location of the *lpScrollRectangle* contents, in characters.</span></span>

<span data-ttu-id="e16da-120">*lpFill* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="e16da-120">*lpFill* \[in\]</span></span>  
<span data-ttu-id="e16da-121">Puntero a una estructura [**de \_ información**](char-info-str.md) de caracteres que especifica los atributos de carácter y color que se van a usar para rellenar las celdas dentro de la intersección de *lpScrollRectangle* y *lpClipRectangle* que se dejaron vacíos como resultado del movimiento.</span><span class="sxs-lookup"><span data-stu-id="e16da-121">A pointer to a [**CHAR\_INFO**](char-info-str.md) structure that specifies the character and color attributes to be used in filling the cells within the intersection of *lpScrollRectangle* and *lpClipRectangle* that were left empty as a result of the move.</span></span>

## <a name="return-value"></a><span data-ttu-id="e16da-122">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="e16da-122">Return value</span></span>

<span data-ttu-id="e16da-123">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="e16da-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e16da-124">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="e16da-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e16da-125">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="e16da-125">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="e16da-126">Comentarios</span><span class="sxs-lookup"><span data-stu-id="e16da-126">Remarks</span></span>

<span data-ttu-id="e16da-127">**ScrollConsoleScreenBuffer** copia el contenido de una región rectangular de un búfer de pantalla, especificado por el parámetro *lpScrollRectangle* , en otra área del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="e16da-127">**ScrollConsoleScreenBuffer** copies the contents of a rectangular region of a screen buffer, specified by the *lpScrollRectangle* parameter, to another area of the console screen buffer.</span></span> <span data-ttu-id="e16da-128">El rectángulo de destino tiene las mismas dimensiones que el rectángulo *lpScrollRectangle* con la esquina superior izquierda en las coordenadas especificadas por el parámetro *dwDestinationOrigin* .</span><span class="sxs-lookup"><span data-stu-id="e16da-128">The target rectangle has the same dimensions as the *lpScrollRectangle* rectangle with its upper-left corner at the coordinates specified by the *dwDestinationOrigin* parameter.</span></span> <span data-ttu-id="e16da-129">Las partes de *lpScrollRectangle* que no se superponen con el rectángulo de destino se rellenan con los atributos de carácter y color especificados por el parámetro *lpFill* .</span><span class="sxs-lookup"><span data-stu-id="e16da-129">Those parts of *lpScrollRectangle* that do not overlap with the target rectangle are filled in with the character and color attributes specified by the *lpFill* parameter.</span></span>

<span data-ttu-id="e16da-130">El rectángulo de recorte se aplica a los cambios realizados en el rectángulo *lpScrollRectangle* y el rectángulo de destino.</span><span class="sxs-lookup"><span data-stu-id="e16da-130">The clipping rectangle applies to changes made in both the *lpScrollRectangle* rectangle and the target rectangle.</span></span> <span data-ttu-id="e16da-131">Por ejemplo, si el rectángulo de recorte no incluye una región que se habría rellenado con el contenido de *lpFill* , el contenido original de la región quedará sin cambios.</span><span class="sxs-lookup"><span data-stu-id="e16da-131">For example, if the clipping rectangle does not include a region that would have been filled by the contents of *lpFill* , the original contents of the region are left unchanged.</span></span>

<span data-ttu-id="e16da-132">Si las regiones de desplazamiento o de destino se extienden más allá de las dimensiones del búfer de pantalla de la consola, se recortan.</span><span class="sxs-lookup"><span data-stu-id="e16da-132">If the scroll or target regions extend beyond the dimensions of the console screen buffer, they are clipped.</span></span> <span data-ttu-id="e16da-133">Por ejemplo, si *lpScrollRectangle* es la región contenida en (0,0) y (19, 19) y *dwDestinationOrigin* es (10, 15), el rectángulo de destino es la región contenida en (10, 15) y (29, 34).</span><span class="sxs-lookup"><span data-stu-id="e16da-133">For example, if *lpScrollRectangle* is the region contained by (0,0) and (19,19) and *dwDestinationOrigin* is (10,15), the target rectangle is the region contained by (10,15) and (29,34).</span></span> <span data-ttu-id="e16da-134">Sin embargo, si el búfer de la pantalla de la consola tiene 50 caracteres de ancho y 30 caracteres de alto, el rectángulo de destino se recorta a (10, 15) y (29, 29).</span><span class="sxs-lookup"><span data-stu-id="e16da-134">However, if the console screen buffer is 50 characters wide and 30 characters high, the target rectangle is clipped to (10,15) and (29,29).</span></span> <span data-ttu-id="e16da-135">Los cambios en el búfer de pantalla de la consola también se recortan según *lpClipRectangle* , si el parámetro especifica una estructura [**\_ Rect pequeña**](small-rect-str.md) .</span><span class="sxs-lookup"><span data-stu-id="e16da-135">Changes to the console screen buffer are also clipped according to *lpClipRectangle* , if the parameter specifies a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="e16da-136">Si el rectángulo de recorte se especifica como (0,0) y (49, 19), solo se realizan los cambios que se producen en esa región del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="e16da-136">If the clipping rectangle is specified as (0,0) and (49,19), only the changes that occur in that region of the console screen buffer are made.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="e16da-137">No se recomienda esta API y no tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente.</span><span class="sxs-lookup"><span data-stu-id="e16da-137">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="e16da-138">El uso se puede aproximar con **[márgenes de desplazamiento](console-virtual-terminal-sequences.md#scrolling-margins)** para corregir un área de la pantalla, **[colocar el cursor](console-virtual-terminal-sequences.md#cursor-positioning)** para establecer la posición activa fuera de la región y nuevas líneas para forzar el movimiento del texto.</span><span class="sxs-lookup"><span data-stu-id="e16da-138">Use can be approximated with **[scroll margins](console-virtual-terminal-sequences.md#scrolling-margins)** to fix an area of the screen, **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** to set the active position outside the region, and newlines to force text to move.</span></span> <span data-ttu-id="e16da-139">El espacio restante se puede rellenar moviendo el cursor, **[estableciendo los atributos gráficos](console-virtual-terminal-sequences.md#text-formatting)** y escribiendo texto normal.</span><span class="sxs-lookup"><span data-stu-id="e16da-139">The remaining space can be filled by moving the cursor, **[setting graphical attributes](console-virtual-terminal-sequences.md#text-formatting)** , and writing normal text.</span></span>

## <a name="examples"></a><span data-ttu-id="e16da-140">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="e16da-140">Examples</span></span>

<span data-ttu-id="e16da-141">Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="e16da-141">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="e16da-142">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e16da-142">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e16da-143">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="e16da-143">Minimum supported client</span></span> | <span data-ttu-id="e16da-144">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="e16da-144">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="e16da-145">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="e16da-145">Minimum supported server</span></span> | <span data-ttu-id="e16da-146">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="e16da-146">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="e16da-147">Encabezado</span><span class="sxs-lookup"><span data-stu-id="e16da-147">Header</span></span> | <span data-ttu-id="e16da-148">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e16da-148">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="e16da-149">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="e16da-149">Library</span></span> | <span data-ttu-id="e16da-150">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="e16da-150">Kernel32.lib</span></span> |
| <span data-ttu-id="e16da-151">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="e16da-151">DLL</span></span> | <span data-ttu-id="e16da-152">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e16da-152">Kernel32.dll</span></span> |
| <span data-ttu-id="e16da-153">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="e16da-153">Unicode and ANSI names</span></span> | <span data-ttu-id="e16da-154">**ScrollConsoleScreenBufferW** (Unicode) y **ScrollConsoleScreenBufferA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="e16da-154">**ScrollConsoleScreenBufferW** (Unicode) and **ScrollConsoleScreenBufferA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="e16da-155">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e16da-155">See also</span></span>

[<span data-ttu-id="e16da-156">**información de carácter \_**</span><span class="sxs-lookup"><span data-stu-id="e16da-156">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="e16da-157">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="e16da-157">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e16da-158">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="e16da-158">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="e16da-159">Desplazarse por el búfer de pantalla</span><span class="sxs-lookup"><span data-stu-id="e16da-159">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

[<span data-ttu-id="e16da-160">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="e16da-160">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="e16da-161">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="e16da-161">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="e16da-162">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="e16da-162">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="e16da-163">**PEQUEÑO \_ rectángulo**</span><span class="sxs-lookup"><span data-stu-id="e16da-163">**SMALL\_RECT**</span></span>](small-rect-str.md)
