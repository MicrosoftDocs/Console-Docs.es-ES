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
ms.openlocfilehash: f0dd67ecc28907913e10efa8c06a544656d08dc6
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060973"
---
# <a name="scrollconsolescreenbuffer-function"></a><span data-ttu-id="98a0c-104">ScrollConsoleScreenBuffer función)</span><span class="sxs-lookup"><span data-stu-id="98a0c-104">ScrollConsoleScreenBuffer function</span></span>


<span data-ttu-id="98a0c-105">Mueve un bloque de datos en un búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="98a0c-105">Moves a block of data in a screen buffer.</span></span> <span data-ttu-id="98a0c-106">Los efectos del movimiento se pueden limitar especificando un rectángulo de recorte, por lo que el contenido del búfer de pantalla de la consola fuera del rectángulo de recorte no se modifica.</span><span class="sxs-lookup"><span data-stu-id="98a0c-106">The effects of the move can be limited by specifying a clipping rectangle, so the contents of the console screen buffer outside the clipping rectangle are unchanged.</span></span>

<a name="syntax"></a><span data-ttu-id="98a0c-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="98a0c-107">Syntax</span></span>
------

```C
BOOL WINAPI ScrollConsoleScreenBuffer(
  _In_           HANDLE     hConsoleOutput,
  _In_     const SMALL_RECT *lpScrollRectangle,
  _In_opt_ const SMALL_RECT *lpClipRectangle,
  _In_           COORD      dwDestinationOrigin,
  _In_     const CHAR_INFO  *lpFill
);
```

<a name="parameters"></a><span data-ttu-id="98a0c-108">Parámetros</span><span class="sxs-lookup"><span data-stu-id="98a0c-108">Parameters</span></span>
----------

<span data-ttu-id="98a0c-109">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="98a0c-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="98a0c-110">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="98a0c-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="98a0c-111">El identificador debe tener el derecho de acceso de \*\* \_ lectura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="98a0c-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="98a0c-112">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="98a0c-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="98a0c-113">*lpScrollRectangle* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="98a0c-113">*lpScrollRectangle* \[in\]</span></span>  
<span data-ttu-id="98a0c-114">Puntero a una [**pequeña estructura \_ Rect**](small-rect-str.md) cuyos miembros especifican las coordenadas superior izquierda e inferior derecha del rectángulo del búfer de pantalla de la consola que se va a desplace.</span><span class="sxs-lookup"><span data-stu-id="98a0c-114">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure whose members specify the upper-left and lower-right coordinates of the console screen buffer rectangle to be moved.</span></span>

<span data-ttu-id="98a0c-115">*lpClipRectangle* \[ en, opcional\]</span><span class="sxs-lookup"><span data-stu-id="98a0c-115">*lpClipRectangle* \[in, optional\]</span></span>  
<span data-ttu-id="98a0c-116">Puntero a una [**pequeña estructura \_ Rect**](small-rect-str.md) cuyos miembros especifican las coordenadas superior izquierda e inferior derecha del rectángulo del búfer de pantalla de la consola que se ve afectado por el desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="98a0c-116">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure whose members specify the upper-left and lower-right coordinates of the console screen buffer rectangle that is affected by the scrolling.</span></span> <span data-ttu-id="98a0c-117">Este puntero puede ser **null**.</span><span class="sxs-lookup"><span data-stu-id="98a0c-117">This pointer can be **NULL**.</span></span>

<span data-ttu-id="98a0c-118">*dwDestinationOrigin* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="98a0c-118">*dwDestinationOrigin* \[in\]</span></span>  
<span data-ttu-id="98a0c-119">Estructura de [**coordenadas**](coord-str.md) que especifica la esquina superior izquierda de la nueva ubicación del contenido de *lpScrollRectangle* , en caracteres.</span><span class="sxs-lookup"><span data-stu-id="98a0c-119">A [**COORD**](coord-str.md) structure that specifies the upper-left corner of the new location of the *lpScrollRectangle* contents, in characters.</span></span>

<span data-ttu-id="98a0c-120">*lpFill* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="98a0c-120">*lpFill* \[in\]</span></span>  
<span data-ttu-id="98a0c-121">Puntero a una estructura [**de \_ información**](char-info-str.md) de caracteres que especifica los atributos de carácter y color que se van a usar para rellenar las celdas dentro de la intersección de *lpScrollRectangle* y *lpClipRectangle* que se dejaron vacíos como resultado del movimiento.</span><span class="sxs-lookup"><span data-stu-id="98a0c-121">A pointer to a [**CHAR\_INFO**](char-info-str.md) structure that specifies the character and color attributes to be used in filling the cells within the intersection of *lpScrollRectangle* and *lpClipRectangle* that were left empty as a result of the move.</span></span>

<a name="return-value"></a><span data-ttu-id="98a0c-122">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="98a0c-122">Return value</span></span>
------------

<span data-ttu-id="98a0c-123">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="98a0c-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="98a0c-124">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="98a0c-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="98a0c-125">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="98a0c-125">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="98a0c-126">Observaciones</span><span class="sxs-lookup"><span data-stu-id="98a0c-126">Remarks</span></span>
-------

<span data-ttu-id="98a0c-127">**ScrollConsoleScreenBuffer** copia el contenido de una región rectangular de un búfer de pantalla, especificado por el parámetro *lpScrollRectangle* , en otra área del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="98a0c-127">**ScrollConsoleScreenBuffer** copies the contents of a rectangular region of a screen buffer, specified by the *lpScrollRectangle* parameter, to another area of the console screen buffer.</span></span> <span data-ttu-id="98a0c-128">El rectángulo de destino tiene las mismas dimensiones que el rectángulo *lpScrollRectangle* con la esquina superior izquierda en las coordenadas especificadas por el parámetro *dwDestinationOrigin* .</span><span class="sxs-lookup"><span data-stu-id="98a0c-128">The target rectangle has the same dimensions as the *lpScrollRectangle* rectangle with its upper-left corner at the coordinates specified by the *dwDestinationOrigin* parameter.</span></span> <span data-ttu-id="98a0c-129">Las partes de *lpScrollRectangle* que no se superponen con el rectángulo de destino se rellenan con los atributos de carácter y color especificados por el parámetro *lpFill* .</span><span class="sxs-lookup"><span data-stu-id="98a0c-129">Those parts of *lpScrollRectangle* that do not overlap with the target rectangle are filled in with the character and color attributes specified by the *lpFill* parameter.</span></span>

<span data-ttu-id="98a0c-130">El rectángulo de recorte se aplica a los cambios realizados en el rectángulo *lpScrollRectangle* y el rectángulo de destino.</span><span class="sxs-lookup"><span data-stu-id="98a0c-130">The clipping rectangle applies to changes made in both the *lpScrollRectangle* rectangle and the target rectangle.</span></span> <span data-ttu-id="98a0c-131">Por ejemplo, si el rectángulo de recorte no incluye una región que se habría rellenado con el contenido de *lpFill*, el contenido original de la región quedará sin cambios.</span><span class="sxs-lookup"><span data-stu-id="98a0c-131">For example, if the clipping rectangle does not include a region that would have been filled by the contents of *lpFill*, the original contents of the region are left unchanged.</span></span>

<span data-ttu-id="98a0c-132">Si las regiones de desplazamiento o de destino se extienden más allá de las dimensiones del búfer de pantalla de la consola, se recortan.</span><span class="sxs-lookup"><span data-stu-id="98a0c-132">If the scroll or target regions extend beyond the dimensions of the console screen buffer, they are clipped.</span></span> <span data-ttu-id="98a0c-133">Por ejemplo, si *lpScrollRectangle* es la región contenida en (0,0) y (19, 19) y *dwDestinationOrigin* es (10, 15), el rectángulo de destino es la región contenida en (10, 15) y (29, 34).</span><span class="sxs-lookup"><span data-stu-id="98a0c-133">For example, if *lpScrollRectangle* is the region contained by (0,0) and (19,19) and *dwDestinationOrigin* is (10,15), the target rectangle is the region contained by (10,15) and (29,34).</span></span> <span data-ttu-id="98a0c-134">Sin embargo, si el búfer de la pantalla de la consola tiene 50 caracteres de ancho y 30 caracteres de alto, el rectángulo de destino se recorta a (10, 15) y (29, 29).</span><span class="sxs-lookup"><span data-stu-id="98a0c-134">However, if the console screen buffer is 50 characters wide and 30 characters high, the target rectangle is clipped to (10,15) and (29,29).</span></span> <span data-ttu-id="98a0c-135">Los cambios en el búfer de pantalla de la consola también se recortan según *lpClipRectangle*, si el parámetro especifica una estructura [\*\* \_ Rect pequeña\*\*](small-rect-str.md) .</span><span class="sxs-lookup"><span data-stu-id="98a0c-135">Changes to the console screen buffer are also clipped according to *lpClipRectangle*, if the parameter specifies a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="98a0c-136">Si el rectángulo de recorte se especifica como (0,0) y (49, 19), solo se realizan los cambios que se producen en esa región del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="98a0c-136">If the clipping rectangle is specified as (0,0) and (49,19), only the changes that occur in that region of the console screen buffer are made.</span></span>

<span data-ttu-id="98a0c-137">Esta función usa caracteres Unicode o caracteres de 8 bits de la página de códigos actual de la consola.</span><span class="sxs-lookup"><span data-stu-id="98a0c-137">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="98a0c-138">La página de códigos de la consola tiene como valor predeterminado la página de códigos OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="98a0c-138">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="98a0c-139">Para cambiar la página de códigos de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) , o bien use los comandos **chcp** o **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="98a0c-139">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="98a0c-140">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="98a0c-140">Examples</span></span>
--------

<span data-ttu-id="98a0c-141">Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="98a0c-141">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="98a0c-142">Requisitos</span><span class="sxs-lookup"><span data-stu-id="98a0c-142">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="98a0c-143">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="98a0c-143">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="98a0c-144">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="98a0c-144">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="98a0c-145">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="98a0c-145">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="98a0c-146">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="98a0c-146">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="98a0c-147">Encabezado</span><span class="sxs-lookup"><span data-stu-id="98a0c-147">Header</span></span></p></td>
<td><span data-ttu-id="98a0c-148">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="98a0c-148">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="98a0c-149">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="98a0c-149">Library</span></span></p></td>
<td><span data-ttu-id="98a0c-150">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="98a0c-150">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="98a0c-151">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="98a0c-151">DLL</span></span></p></td>
<td><span data-ttu-id="98a0c-152">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="98a0c-152">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="98a0c-153">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="98a0c-153">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="98a0c-154"><strong>ScrollConsoleScreenBufferW</strong> (Unicode) y <strong>ScrollConsoleScreenBufferA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="98a0c-154"><strong>ScrollConsoleScreenBufferW</strong> (Unicode) and <strong>ScrollConsoleScreenBufferA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="98a0c-155"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="98a0c-155"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="98a0c-156">**información de carácter \_**</span><span class="sxs-lookup"><span data-stu-id="98a0c-156">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="98a0c-157">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="98a0c-157">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="98a0c-158">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="98a0c-158">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="98a0c-159">Desplazarse por el búfer de pantalla</span><span class="sxs-lookup"><span data-stu-id="98a0c-159">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

[<span data-ttu-id="98a0c-160">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="98a0c-160">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="98a0c-161">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="98a0c-161">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="98a0c-162">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="98a0c-162">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="98a0c-163">**PEQUEÑO \_ rectángulo**</span><span class="sxs-lookup"><span data-stu-id="98a0c-163">**SMALL\_RECT**</span></span>](small-rect-str.md)

 

 




