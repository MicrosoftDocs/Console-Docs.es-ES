---
title: WriteConsoleOutput función)
description: Escribe datos de atributos de caracteres y colores en un bloque rectangular especificado de celdas de caracteres en un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/WriteConsoleOutput
- wincon/WriteConsoleOutput
- WriteConsoleOutput
- consoleapi2/WriteConsoleOutputA
- wincon/WriteConsoleOutputA
- WriteConsoleOutputA
- consoleapi2/WriteConsoleOutputW
- wincon/WriteConsoleOutputW
- WriteConsoleOutputW
MS-HAID:
- '\_win32\_writeconsoleoutput'
- base.writeconsoleoutput
- consoles.writeconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a98b8118-97ce-4dd4-a337-122d4a76f232
topic_type:
- apiref
api_name:
- WriteConsoleOutput
- WriteConsoleOutputA
- WriteConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e2f84f5c072a8404b129e27bec3464363b9dd3d0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060588"
---
# <a name="writeconsoleoutput-function"></a><span data-ttu-id="6bfc7-104">WriteConsoleOutput función)</span><span class="sxs-lookup"><span data-stu-id="6bfc7-104">WriteConsoleOutput function</span></span>


<span data-ttu-id="6bfc7-105">Escribe datos de atributos de caracteres y colores en un bloque rectangular especificado de celdas de caracteres en un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-105">Writes character and color attribute data to a specified rectangular block of character cells in a console screen buffer.</span></span> <span data-ttu-id="6bfc7-106">Los datos que se van a escribir se toman de un bloque rectangular de tamaño correspondiente en una ubicación especificada del búfer de origen.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-106">The data to be written is taken from a correspondingly sized rectangular block at a specified location in the source buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="6bfc7-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="6bfc7-107">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleOutput(
  _In_          HANDLE      hConsoleOutput,
  _In_    const CHAR_INFO   *lpBuffer,
  _In_          COORD       dwBufferSize,
  _In_          COORD       dwBufferCoord,
  _Inout_       PSMALL_RECT lpWriteRegion
);
```

<a name="parameters"></a><span data-ttu-id="6bfc7-108">Parámetros</span><span class="sxs-lookup"><span data-stu-id="6bfc7-108">Parameters</span></span>
----------

<span data-ttu-id="6bfc7-109">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="6bfc7-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="6bfc7-110">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="6bfc7-111">El identificador debe tener el derecho de acceso de \*\* \_ escritura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="6bfc7-111">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="6bfc7-112">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="6bfc7-113">*lpBuffer* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="6bfc7-113">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="6bfc7-114">Los datos que se van a escribir en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-114">The data to be written to the console screen buffer.</span></span> <span data-ttu-id="6bfc7-115">Este puntero se trata como el origen de una matriz bidimensional de estructuras [**de \_ información de char**](char-info-str.md) cuyo tamaño se especifica mediante el parámetro *dwBufferSize* .</span><span class="sxs-lookup"><span data-stu-id="6bfc7-115">This pointer is treated as the origin of a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures whose size is specified by the *dwBufferSize* parameter.</span></span>

<span data-ttu-id="6bfc7-116">*dwBufferSize* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="6bfc7-116">*dwBufferSize* \[in\]</span></span>  
<span data-ttu-id="6bfc7-117">Tamaño del búfer al que apunta el parámetro *lpBuffer* , en celdas de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-117">The size of the buffer pointed to by the *lpBuffer* parameter, in character cells.</span></span> <span data-ttu-id="6bfc7-118">El miembro **X** de la estructura [**coordenadas**](coord-str.md) es el número de columnas; el miembro **Y** es el número de filas.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-118">The **X** member of the [**COORD**](coord-str.md) structure is the number of columns; the **Y** member is the number of rows.</span></span>

<span data-ttu-id="6bfc7-119">*dwBufferCoord* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="6bfc7-119">*dwBufferCoord* \[in\]</span></span>  
<span data-ttu-id="6bfc7-120">Coordenadas de la celda superior izquierda del búfer a la que apunta el parámetro *lpBuffer* .</span><span class="sxs-lookup"><span data-stu-id="6bfc7-120">The coordinates of the upper-left cell in the buffer pointed to by the *lpBuffer* parameter.</span></span> <span data-ttu-id="6bfc7-121">El miembro **X** de la estructura [**coordenadas**](coord-str.md) es la columna y el miembro **y** es la fila.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-121">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="6bfc7-122">*lpWriteRegion* \[ in, out\]</span><span class="sxs-lookup"><span data-stu-id="6bfc7-122">*lpWriteRegion* \[in, out\]</span></span>  
<span data-ttu-id="6bfc7-123">Puntero a una estructura [\*\* \_ Rect pequeña\*\*](small-rect-str.md) .</span><span class="sxs-lookup"><span data-stu-id="6bfc7-123">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="6bfc7-124">En la entrada, los miembros de la estructura especifican las coordenadas superior izquierda e inferior derecha del rectángulo del búfer de pantalla de la consola en el que se va a escribir.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-124">On input, the structure members specify the upper-left and lower-right coordinates of the console screen buffer rectangle to write to.</span></span> <span data-ttu-id="6bfc7-125">En la salida, los miembros de la estructura especifican el rectángulo real que se usó.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-125">On output, the structure members specify the actual rectangle that was used.</span></span>

<a name="return-value"></a><span data-ttu-id="6bfc7-126">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="6bfc7-126">Return value</span></span>
------------

<span data-ttu-id="6bfc7-127">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-127">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="6bfc7-128">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-128">If the function fails, the return value is zero.</span></span> <span data-ttu-id="6bfc7-129">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="6bfc7-129">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="6bfc7-130">Observaciones</span><span class="sxs-lookup"><span data-stu-id="6bfc7-130">Remarks</span></span>
-------

<span data-ttu-id="6bfc7-131">**WriteConsoleOutput** trata el búfer de origen y el búfer de pantalla de destino como matrices bidimensionales (columnas y filas de celdas de caracteres).</span><span class="sxs-lookup"><span data-stu-id="6bfc7-131">**WriteConsoleOutput** treats the source buffer and the destination screen buffer as two-dimensional arrays (columns and rows of character cells).</span></span> <span data-ttu-id="6bfc7-132">El rectángulo al que apunta el parámetro *lpWriteRegion* especifica el tamaño y la ubicación del bloque en el que se va a escribir en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-132">The rectangle pointed to by the *lpWriteRegion* parameter specifies the size and location of the block to be written to in the console screen buffer.</span></span> <span data-ttu-id="6bfc7-133">Un rectángulo del mismo tamaño se encuentra con la celda superior izquierda en las coordenadas del parámetro *dwBufferCoord* en la matriz *lpBuffer* .</span><span class="sxs-lookup"><span data-stu-id="6bfc7-133">A rectangle of the same size is located with its upper-left cell at the coordinates of the *dwBufferCoord* parameter in the *lpBuffer* array.</span></span> <span data-ttu-id="6bfc7-134">Los datos de las celdas que están en la intersección de este rectángulo y el rectángulo del búfer de origen (cuyas dimensiones se especifican mediante el parámetro *dwBufferSize* ) se escriben en el rectángulo de destino.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-134">Data from the cells that are in the intersection of this rectangle and the source buffer rectangle (whose dimensions are specified by the *dwBufferSize* parameter) is written to the destination rectangle.</span></span>

<span data-ttu-id="6bfc7-135">Las celdas del rectángulo de destino cuya ubicación de origen correspondiente están fuera de los límites del rectángulo del búfer de origen dejan de ser afectadas por la operación de escritura.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-135">Cells in the destination rectangle whose corresponding source location are outside the boundaries of the source buffer rectangle are left unaffected by the write operation.</span></span> <span data-ttu-id="6bfc7-136">En otras palabras, se trata de las celdas para las que no hay datos disponibles para su escritura.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-136">In other words, these are the cells for which no data is available to be written.</span></span>

<span data-ttu-id="6bfc7-137">Antes de que **WriteConsoleOutput** devuelva, establece los miembros de *lpWriteRegion* en el rectángulo del búfer de pantalla real afectado por la operación de escritura.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-137">Before **WriteConsoleOutput** returns, it sets the members of *lpWriteRegion* to the actual screen buffer rectangle affected by the write operation.</span></span> <span data-ttu-id="6bfc7-138">Este rectángulo refleja las celdas del rectángulo de destino para las que existe una celda correspondiente en el búfer de origen, porque **WriteConsoleOutput** recorta las dimensiones del rectángulo de destino en los límites del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-138">This rectangle reflects the cells in the destination rectangle for which there existed a corresponding cell in the source buffer, because **WriteConsoleOutput** clips the dimensions of the destination rectangle to the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="6bfc7-139">Si el rectángulo especificado por *lpWriteRegion* se encuentra completamente fuera de los límites del búfer de pantalla de la consola, o si el rectángulo correspondiente se coloca completamente fuera de los límites del búfer de origen, no se escribe ningún dato.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-139">If the rectangle specified by *lpWriteRegion* lies completely outside the boundaries of the console screen buffer, or if the corresponding rectangle is positioned completely outside the boundaries of the source buffer, no data is written.</span></span> <span data-ttu-id="6bfc7-140">En este caso, la función devuelve con los miembros de la estructura a la que apunta el conjunto de parámetros *lpWriteRegion* , de modo que el miembro de la **derecha** es menor que el **izquierdo**, o el miembro **inferior** es menor que la **parte superior**.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-140">In this case, the function returns with the members of the structure pointed to by the *lpWriteRegion* parameter set such that the **Right** member is less than the **Left**, or the **Bottom** member is less than the **Top**.</span></span> <span data-ttu-id="6bfc7-141">Para determinar el tamaño del búfer de pantalla de la consola, use la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="6bfc7-141">To determine the size of the console screen buffer, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="6bfc7-142">**WriteConsoleOutput** no tiene ningún efecto en la posición del cursor.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-142">**WriteConsoleOutput** has no effect on the cursor position.</span></span>

<span data-ttu-id="6bfc7-143">Esta función usa caracteres Unicode o caracteres de 8 bits de la página de códigos actual de la consola.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-143">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="6bfc7-144">La página de códigos de la consola tiene como valor predeterminado la página de códigos OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="6bfc7-144">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="6bfc7-145">Para cambiar la página de códigos de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) , o bien use los comandos **chcp** o **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="6bfc7-145">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="6bfc7-146">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="6bfc7-146">Examples</span></span>
--------

<span data-ttu-id="6bfc7-147">Para obtener un ejemplo, vea [lectura y escritura de bloques de caracteres y atributos](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="6bfc7-147">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

<a name="requirements"></a><span data-ttu-id="6bfc7-148">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6bfc7-148">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="6bfc7-149">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="6bfc7-149">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="6bfc7-150">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="6bfc7-150">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6bfc7-151">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="6bfc7-151">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="6bfc7-152">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="6bfc7-152">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6bfc7-153">Encabezado</span><span class="sxs-lookup"><span data-stu-id="6bfc7-153">Header</span></span></p></td>
<td><span data-ttu-id="6bfc7-154">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6bfc7-154">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6bfc7-155">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="6bfc7-155">Library</span></span></p></td>
<td><span data-ttu-id="6bfc7-156">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="6bfc7-156">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6bfc7-157">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="6bfc7-157">DLL</span></span></p></td>
<td><span data-ttu-id="6bfc7-158">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6bfc7-158">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6bfc7-159">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="6bfc7-159">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="6bfc7-160"><strong>WriteConsoleOutputW</strong> (Unicode) y <strong>WriteConsoleOutputA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="6bfc7-160"><strong>WriteConsoleOutputW</strong> (Unicode) and <strong>WriteConsoleOutputA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="6bfc7-161"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="6bfc7-161"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="6bfc7-162">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="6bfc7-162">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="6bfc7-163">**información de carácter \_**</span><span class="sxs-lookup"><span data-stu-id="6bfc7-163">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="6bfc7-164">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="6bfc7-164">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="6bfc7-165">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="6bfc7-165">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="6bfc7-166">Funciones de salida de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="6bfc7-166">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="6bfc7-167">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="6bfc7-167">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="6bfc7-168">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="6bfc7-168">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="6bfc7-169">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="6bfc7-169">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="6bfc7-170">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="6bfc7-170">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="6bfc7-171">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="6bfc7-171">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="6bfc7-172">**PEQUEÑO \_ rectángulo**</span><span class="sxs-lookup"><span data-stu-id="6bfc7-172">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="6bfc7-173">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="6bfc7-173">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="6bfc7-174">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="6bfc7-174">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




