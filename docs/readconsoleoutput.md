---
title: ReadConsoleOutput función)
description: Lee datos de atributos de caracteres y colores de un bloque rectangular de celdas de caracteres en un búfer de pantalla de la consola y escribe datos en el búfer de destino.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/ReadConsoleOutput
- wincon/ReadConsoleOutput
- ReadConsoleOutput
- consoleapi2/ReadConsoleOutputA
- wincon/ReadConsoleOutputA
- ReadConsoleOutputA
- consoleapi2/ReadConsoleOutputW
- wincon/ReadConsoleOutputW
- ReadConsoleOutputW
MS-HAID:
- '\_win32\_readconsoleoutput'
- base.readconsoleoutput
- consoles.readconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d1391684-6a8f-4b5e-9706-11970a957710
topic_type:
- apiref
api_name:
- ReadConsoleOutput
- ReadConsoleOutputA
- ReadConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 382ed9cd06586ab86097c6efd2f6b8ea92f03eaf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061009"
---
# <a name="readconsoleoutput-function"></a><span data-ttu-id="ecafd-104">ReadConsoleOutput función)</span><span class="sxs-lookup"><span data-stu-id="ecafd-104">ReadConsoleOutput function</span></span>


<span data-ttu-id="ecafd-105">Lee los datos de atributos de caracteres y colores de un bloque rectangular de celdas de caracteres en un búfer de pantalla de la consola, y la función escribe los datos en un bloque rectangular en una ubicación especificada del búfer de destino.</span><span class="sxs-lookup"><span data-stu-id="ecafd-105">Reads character and color attribute data from a rectangular block of character cells in a console screen buffer, and the function writes the data to a rectangular block at a specified location in the destination buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="ecafd-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ecafd-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsoleOutput(
  _In_    HANDLE      hConsoleOutput,
  _Out_   PCHAR_INFO  lpBuffer,
  _In_    COORD       dwBufferSize,
  _In_    COORD       dwBufferCoord,
  _Inout_ PSMALL_RECT lpReadRegion
);
```

<a name="parameters"></a><span data-ttu-id="ecafd-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ecafd-107">Parameters</span></span>
----------

<span data-ttu-id="ecafd-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="ecafd-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="ecafd-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="ecafd-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="ecafd-110">El identificador debe tener el derecho de acceso de \*\* \_ lectura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="ecafd-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="ecafd-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="ecafd-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="ecafd-112">*lpBuffer* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="ecafd-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="ecafd-113">Un puntero a un búfer de destino que recibe los datos leídos del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="ecafd-113">A pointer to a destination buffer that receives the data read from the console screen buffer.</span></span> <span data-ttu-id="ecafd-114">Este puntero se trata como el origen de una matriz bidimensional de estructuras [**de \_ información de char**](char-info-str.md) cuyo tamaño se especifica mediante el parámetro *dwBufferSize* .</span><span class="sxs-lookup"><span data-stu-id="ecafd-114">This pointer is treated as the origin of a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures whose size is specified by the *dwBufferSize* parameter.</span></span>

<span data-ttu-id="ecafd-115">*dwBufferSize* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="ecafd-115">*dwBufferSize* \[in\]</span></span>  
<span data-ttu-id="ecafd-116">Tamaño del parámetro *lpBuffer* , en celdas de carácter.</span><span class="sxs-lookup"><span data-stu-id="ecafd-116">The size of the *lpBuffer* parameter, in character cells.</span></span> <span data-ttu-id="ecafd-117">El miembro **X** de la estructura [**coordenadas**](coord-str.md) es el número de columnas; el miembro **Y** es el número de filas.</span><span class="sxs-lookup"><span data-stu-id="ecafd-117">The **X** member of the [**COORD**](coord-str.md) structure is the number of columns; the **Y** member is the number of rows.</span></span>

<span data-ttu-id="ecafd-118">*dwBufferCoord* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="ecafd-118">*dwBufferCoord* \[in\]</span></span>  
<span data-ttu-id="ecafd-119">Coordenadas de la celda superior izquierda del parámetro *lpBuffer* que recibe los datos leídos del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="ecafd-119">The coordinates of the upper-left cell in the *lpBuffer* parameter that receives the data read from the console screen buffer.</span></span> <span data-ttu-id="ecafd-120">El miembro **X** de la estructura [**coordenadas**](coord-str.md) es la columna y el miembro **y** es la fila.</span><span class="sxs-lookup"><span data-stu-id="ecafd-120">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="ecafd-121">*lpReadRegion* \[ in, out\]</span><span class="sxs-lookup"><span data-stu-id="ecafd-121">*lpReadRegion* \[in, out\]</span></span>  
<span data-ttu-id="ecafd-122">Puntero a una estructura [\*\* \_ Rect pequeña\*\*](small-rect-str.md) .</span><span class="sxs-lookup"><span data-stu-id="ecafd-122">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="ecafd-123">En la entrada, los miembros de la estructura especifican las coordenadas superior izquierda e inferior derecha del rectángulo del búfer de pantalla de la consola desde el que se va a leer la función.</span><span class="sxs-lookup"><span data-stu-id="ecafd-123">On input, the structure members specify the upper-left and lower-right coordinates of the console screen buffer rectangle from which the function is to read.</span></span> <span data-ttu-id="ecafd-124">En la salida, los miembros de la estructura especifican el rectángulo real que se usó.</span><span class="sxs-lookup"><span data-stu-id="ecafd-124">On output, the structure members specify the actual rectangle that was used.</span></span>

<a name="return-value"></a><span data-ttu-id="ecafd-125">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="ecafd-125">Return value</span></span>
------------

<span data-ttu-id="ecafd-126">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="ecafd-126">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ecafd-127">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="ecafd-127">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ecafd-128">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="ecafd-128">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="ecafd-129">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ecafd-129">Remarks</span></span>
-------

<span data-ttu-id="ecafd-130">**ReadConsoleOutput** trata el búfer de pantalla de la consola y el búfer de destino como matrices bidimensionales (columnas y filas de celdas de caracteres).</span><span class="sxs-lookup"><span data-stu-id="ecafd-130">**ReadConsoleOutput** treats the console screen buffer and the destination buffer as two-dimensional arrays (columns and rows of character cells).</span></span> <span data-ttu-id="ecafd-131">El rectángulo al que apunta el parámetro *lpReadRegion* especifica el tamaño y la ubicación del bloque que se va a leer desde el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="ecafd-131">The rectangle pointed to by the *lpReadRegion* parameter specifies the size and location of the block to be read from the console screen buffer.</span></span> <span data-ttu-id="ecafd-132">Un rectángulo de destino del mismo tamaño se encuentra con la celda superior izquierda en las coordenadas del parámetro *dwBufferCoord* en la matriz *lpBuffer* .</span><span class="sxs-lookup"><span data-stu-id="ecafd-132">A destination rectangle of the same size is located with its upper-left cell at the coordinates of the *dwBufferCoord* parameter in the *lpBuffer* array.</span></span> <span data-ttu-id="ecafd-133">Los datos leídos de las celdas del rectángulo de origen del búfer de pantalla de la consola se copian en las celdas correspondientes del búfer de destino.</span><span class="sxs-lookup"><span data-stu-id="ecafd-133">Data read from the cells in the console screen buffer source rectangle is copied to the corresponding cells in the destination buffer.</span></span> <span data-ttu-id="ecafd-134">Si la celda correspondiente está fuera de los límites del rectángulo del búfer de destino (cuyas dimensiones se especifican mediante el parámetro *dwBufferSize* ), los datos no se copian.</span><span class="sxs-lookup"><span data-stu-id="ecafd-134">If the corresponding cell is outside the boundaries of the destination buffer rectangle (whose dimensions are specified by the *dwBufferSize* parameter), the data is not copied.</span></span>

<span data-ttu-id="ecafd-135">Las celdas del búfer de destino que se corresponden con las coordenadas que no están dentro de los límites del búfer de pantalla de la consola permanecen sin cambios.</span><span class="sxs-lookup"><span data-stu-id="ecafd-135">Cells in the destination buffer corresponding to coordinates that are not within the boundaries of the console screen buffer are left unchanged.</span></span> <span data-ttu-id="ecafd-136">En otras palabras, se trata de las celdas para las que no hay datos de búfer de pantalla disponibles para leer.</span><span class="sxs-lookup"><span data-stu-id="ecafd-136">In other words, these are the cells for which no screen buffer data is available to be read.</span></span>

<span data-ttu-id="ecafd-137">Antes de que **ReadConsoleOutput** devuelva, establece los miembros de la estructura a la que apunta el parámetro *lpReadRegion* en el rectángulo del búfer de pantalla real cuyas celdas se copiaron en el búfer de destino.</span><span class="sxs-lookup"><span data-stu-id="ecafd-137">Before **ReadConsoleOutput** returns, it sets the members of the structure pointed to by the *lpReadRegion* parameter to the actual screen buffer rectangle whose cells were copied into the destination buffer.</span></span> <span data-ttu-id="ecafd-138">Este rectángulo refleja las celdas del rectángulo de origen para las que existía una celda correspondiente en el búfer de destino, porque **ReadConsoleOutput** recorta las dimensiones del rectángulo de origen para ajustarse a los límites del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="ecafd-138">This rectangle reflects the cells in the source rectangle for which there existed a corresponding cell in the destination buffer, because **ReadConsoleOutput** clips the dimensions of the source rectangle to fit the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="ecafd-139">Si el rectángulo especificado por *lpReadRegion* se encuentra completamente fuera de los límites del búfer de pantalla de la consola, o si el rectángulo correspondiente se coloca completamente fuera de los límites del búfer de destino, no se copia ningún dato.</span><span class="sxs-lookup"><span data-stu-id="ecafd-139">If the rectangle specified by *lpReadRegion* lies completely outside the boundaries of the console screen buffer, or if the corresponding rectangle is positioned completely outside the boundaries of the destination buffer, no data is copied.</span></span> <span data-ttu-id="ecafd-140">En este caso, la función devuelve con los miembros de la estructura a la que apunta el conjunto de parámetros *lpReadRegion* , de modo que el miembro de la **derecha** es menor que el **izquierdo**, o el miembro **inferior** es menor que la **parte superior**.</span><span class="sxs-lookup"><span data-stu-id="ecafd-140">In this case, the function returns with the members of the structure pointed to by the *lpReadRegion* parameter set such that the **Right** member is less than the **Left**, or the **Bottom** member is less than the **Top**.</span></span> <span data-ttu-id="ecafd-141">Para determinar el tamaño del búfer de pantalla de la consola, use la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="ecafd-141">To determine the size of the console screen buffer, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="ecafd-142">La función **ReadConsoleOutput** no tiene ningún efecto en la posición del cursor del búfer de la pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="ecafd-142">The **ReadConsoleOutput** function has no effect on the console screen buffer's cursor position.</span></span> <span data-ttu-id="ecafd-143">La función no cambia el contenido del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="ecafd-143">The contents of the console screen buffer are not changed by the function.</span></span>

<span data-ttu-id="ecafd-144">Esta función usa caracteres Unicode o caracteres de 8 bits de la página de códigos actual de la consola.</span><span class="sxs-lookup"><span data-stu-id="ecafd-144">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="ecafd-145">La página de códigos de la consola tiene como valor predeterminado la página de códigos OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="ecafd-145">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="ecafd-146">Para cambiar la página de códigos de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) , o bien use los comandos **chcp** o **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="ecafd-146">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="ecafd-147">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="ecafd-147">Examples</span></span>
--------

<span data-ttu-id="ecafd-148">Para obtener un ejemplo, vea [lectura y escritura de bloques de caracteres y atributos](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="ecafd-148">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

<a name="requirements"></a><span data-ttu-id="ecafd-149">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ecafd-149">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="ecafd-150">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="ecafd-150">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="ecafd-151">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="ecafd-151">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ecafd-152">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="ecafd-152">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="ecafd-153">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="ecafd-153">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ecafd-154">Encabezado</span><span class="sxs-lookup"><span data-stu-id="ecafd-154">Header</span></span></p></td>
<td><span data-ttu-id="ecafd-155">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ecafd-155">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ecafd-156">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="ecafd-156">Library</span></span></p></td>
<td><span data-ttu-id="ecafd-157">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ecafd-157">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ecafd-158">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="ecafd-158">DLL</span></span></p></td>
<td><span data-ttu-id="ecafd-159">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ecafd-159">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ecafd-160">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="ecafd-160">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="ecafd-161"><strong>ReadConsoleOutputW</strong> (Unicode) y <strong>ReadConsoleOutputA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="ecafd-161"><strong>ReadConsoleOutputW</strong> (Unicode) and <strong>ReadConsoleOutputA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="ecafd-162"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="ecafd-162"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="ecafd-163">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="ecafd-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ecafd-164">Funciones de salida de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="ecafd-164">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="ecafd-165">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="ecafd-165">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="ecafd-166">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="ecafd-166">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="ecafd-167">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="ecafd-167">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="ecafd-168">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="ecafd-168">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="ecafd-169">**PEQUEÑO \_ rectángulo**</span><span class="sxs-lookup"><span data-stu-id="ecafd-169">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="ecafd-170">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="ecafd-170">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="ecafd-171">**información de carácter \_**</span><span class="sxs-lookup"><span data-stu-id="ecafd-171">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="ecafd-172">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="ecafd-172">**COORD**</span></span>](coord-str.md)

 

 




