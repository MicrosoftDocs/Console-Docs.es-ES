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
ms.openlocfilehash: b67f741aafcb067e85d339d550646261a46c273a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037263"
---
# <a name="writeconsoleoutput-function"></a><span data-ttu-id="9e586-104">WriteConsoleOutput función)</span><span class="sxs-lookup"><span data-stu-id="9e586-104">WriteConsoleOutput function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="9e586-105">Escribe datos de atributos de caracteres y colores en un bloque rectangular especificado de celdas de caracteres en un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="9e586-105">Writes character and color attribute data to a specified rectangular block of character cells in a console screen buffer.</span></span> <span data-ttu-id="9e586-106">Los datos que se van a escribir se toman de un bloque rectangular de tamaño correspondiente en una ubicación especificada del búfer de origen.</span><span class="sxs-lookup"><span data-stu-id="9e586-106">The data to be written is taken from a correspondingly sized rectangular block at a specified location in the source buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="9e586-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9e586-107">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleOutput(
  _In_          HANDLE      hConsoleOutput,
  _In_    const CHAR_INFO   *lpBuffer,
  _In_          COORD       dwBufferSize,
  _In_          COORD       dwBufferCoord,
  _Inout_       PSMALL_RECT lpWriteRegion
);
```

## <a name="parameters"></a><span data-ttu-id="9e586-108">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9e586-108">Parameters</span></span>

<span data-ttu-id="9e586-109">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="9e586-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="9e586-110">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="9e586-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="9e586-111">El identificador debe tener el derecho de acceso de **\_ escritura genérico** .</span><span class="sxs-lookup"><span data-stu-id="9e586-111">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="9e586-112">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="9e586-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="9e586-113">*lpBuffer* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="9e586-113">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="9e586-114">Los datos que se van a escribir en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="9e586-114">The data to be written to the console screen buffer.</span></span> <span data-ttu-id="9e586-115">Este puntero se trata como el origen de una matriz bidimensional de estructuras [**de \_ información de char**](char-info-str.md) cuyo tamaño se especifica mediante el parámetro *dwBufferSize* .</span><span class="sxs-lookup"><span data-stu-id="9e586-115">This pointer is treated as the origin of a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures whose size is specified by the *dwBufferSize* parameter.</span></span>

<span data-ttu-id="9e586-116">*dwBufferSize* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="9e586-116">*dwBufferSize* \[in\]</span></span>  
<span data-ttu-id="9e586-117">Tamaño del búfer al que apunta el parámetro *lpBuffer* , en celdas de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9e586-117">The size of the buffer pointed to by the *lpBuffer* parameter, in character cells.</span></span> <span data-ttu-id="9e586-118">El miembro **X** de la estructura [**coordenadas**](coord-str.md) es el número de columnas; el miembro **Y** es el número de filas.</span><span class="sxs-lookup"><span data-stu-id="9e586-118">The **X** member of the [**COORD**](coord-str.md) structure is the number of columns; the **Y** member is the number of rows.</span></span>

<span data-ttu-id="9e586-119">*dwBufferCoord* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="9e586-119">*dwBufferCoord* \[in\]</span></span>  
<span data-ttu-id="9e586-120">Coordenadas de la celda superior izquierda del búfer a la que apunta el parámetro *lpBuffer* .</span><span class="sxs-lookup"><span data-stu-id="9e586-120">The coordinates of the upper-left cell in the buffer pointed to by the *lpBuffer* parameter.</span></span> <span data-ttu-id="9e586-121">El miembro **X** de la estructura [**coordenadas**](coord-str.md) es la columna y el miembro **y** es la fila.</span><span class="sxs-lookup"><span data-stu-id="9e586-121">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="9e586-122">*lpWriteRegion* \[ in, out\]</span><span class="sxs-lookup"><span data-stu-id="9e586-122">*lpWriteRegion* \[in, out\]</span></span>  
<span data-ttu-id="9e586-123">Puntero a una estructura [**\_ Rect pequeña**](small-rect-str.md) .</span><span class="sxs-lookup"><span data-stu-id="9e586-123">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="9e586-124">En la entrada, los miembros de la estructura especifican las coordenadas superior izquierda e inferior derecha del rectángulo del búfer de pantalla de la consola en el que se va a escribir.</span><span class="sxs-lookup"><span data-stu-id="9e586-124">On input, the structure members specify the upper-left and lower-right coordinates of the console screen buffer rectangle to write to.</span></span> <span data-ttu-id="9e586-125">En la salida, los miembros de la estructura especifican el rectángulo real que se usó.</span><span class="sxs-lookup"><span data-stu-id="9e586-125">On output, the structure members specify the actual rectangle that was used.</span></span>

## <a name="return-value"></a><span data-ttu-id="9e586-126">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="9e586-126">Return value</span></span>

<span data-ttu-id="9e586-127">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="9e586-127">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="9e586-128">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="9e586-128">If the function fails, the return value is zero.</span></span> <span data-ttu-id="9e586-129">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="9e586-129">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="9e586-130">Comentarios</span><span class="sxs-lookup"><span data-stu-id="9e586-130">Remarks</span></span>

<span data-ttu-id="9e586-131">**WriteConsoleOutput** trata el búfer de origen y el búfer de pantalla de destino como matrices bidimensionales (columnas y filas de celdas de caracteres).</span><span class="sxs-lookup"><span data-stu-id="9e586-131">**WriteConsoleOutput** treats the source buffer and the destination screen buffer as two-dimensional arrays (columns and rows of character cells).</span></span> <span data-ttu-id="9e586-132">El rectángulo al que apunta el parámetro *lpWriteRegion* especifica el tamaño y la ubicación del bloque en el que se va a escribir en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="9e586-132">The rectangle pointed to by the *lpWriteRegion* parameter specifies the size and location of the block to be written to in the console screen buffer.</span></span> <span data-ttu-id="9e586-133">Un rectángulo del mismo tamaño se encuentra con la celda superior izquierda en las coordenadas del parámetro *dwBufferCoord* en la matriz *lpBuffer* .</span><span class="sxs-lookup"><span data-stu-id="9e586-133">A rectangle of the same size is located with its upper-left cell at the coordinates of the *dwBufferCoord* parameter in the *lpBuffer* array.</span></span> <span data-ttu-id="9e586-134">Los datos de las celdas que están en la intersección de este rectángulo y el rectángulo del búfer de origen (cuyas dimensiones se especifican mediante el parámetro *dwBufferSize* ) se escriben en el rectángulo de destino.</span><span class="sxs-lookup"><span data-stu-id="9e586-134">Data from the cells that are in the intersection of this rectangle and the source buffer rectangle (whose dimensions are specified by the *dwBufferSize* parameter) is written to the destination rectangle.</span></span>

<span data-ttu-id="9e586-135">Las celdas del rectángulo de destino cuya ubicación de origen correspondiente están fuera de los límites del rectángulo del búfer de origen dejan de ser afectadas por la operación de escritura.</span><span class="sxs-lookup"><span data-stu-id="9e586-135">Cells in the destination rectangle whose corresponding source location are outside the boundaries of the source buffer rectangle are left unaffected by the write operation.</span></span> <span data-ttu-id="9e586-136">En otras palabras, se trata de las celdas para las que no hay datos disponibles para su escritura.</span><span class="sxs-lookup"><span data-stu-id="9e586-136">In other words, these are the cells for which no data is available to be written.</span></span>

<span data-ttu-id="9e586-137">Antes de que **WriteConsoleOutput** devuelva, establece los miembros de *lpWriteRegion* en el rectángulo del búfer de pantalla real afectado por la operación de escritura.</span><span class="sxs-lookup"><span data-stu-id="9e586-137">Before **WriteConsoleOutput** returns, it sets the members of *lpWriteRegion* to the actual screen buffer rectangle affected by the write operation.</span></span> <span data-ttu-id="9e586-138">Este rectángulo refleja las celdas del rectángulo de destino para las que existe una celda correspondiente en el búfer de origen, porque **WriteConsoleOutput** recorta las dimensiones del rectángulo de destino en los límites del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="9e586-138">This rectangle reflects the cells in the destination rectangle for which there existed a corresponding cell in the source buffer, because **WriteConsoleOutput** clips the dimensions of the destination rectangle to the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="9e586-139">Si el rectángulo especificado por *lpWriteRegion* se encuentra completamente fuera de los límites del búfer de pantalla de la consola, o si el rectángulo correspondiente se coloca completamente fuera de los límites del búfer de origen, no se escribe ningún dato.</span><span class="sxs-lookup"><span data-stu-id="9e586-139">If the rectangle specified by *lpWriteRegion* lies completely outside the boundaries of the console screen buffer, or if the corresponding rectangle is positioned completely outside the boundaries of the source buffer, no data is written.</span></span> <span data-ttu-id="9e586-140">En este caso, la función devuelve con los miembros de la estructura a la que apunta el conjunto de parámetros *lpWriteRegion* , de modo que el miembro de la **derecha** es menor que el **izquierdo** , o el miembro **inferior** es menor que la **parte superior** .</span><span class="sxs-lookup"><span data-stu-id="9e586-140">In this case, the function returns with the members of the structure pointed to by the *lpWriteRegion* parameter set such that the **Right** member is less than the **Left** , or the **Bottom** member is less than the **Top** .</span></span> <span data-ttu-id="9e586-141">Para determinar el tamaño del búfer de pantalla de la consola, use la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="9e586-141">To determine the size of the console screen buffer, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="9e586-142">**WriteConsoleOutput** no tiene ningún efecto en la posición del cursor.</span><span class="sxs-lookup"><span data-stu-id="9e586-142">**WriteConsoleOutput** has no effect on the cursor position.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="9e586-143">Esta API tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente en las secuencias de **[formato de texto](console-virtual-terminal-sequences.md#text-formatting)** y **[posición del cursor](console-virtual-terminal-sequences.md#cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="9e586-143">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sequences.</span></span> <span data-ttu-id="9e586-144">Mueva el cursor a la ubicación que se va a insertar, aplique el formato deseado y escriba el texto.</span><span class="sxs-lookup"><span data-stu-id="9e586-144">Move the cursor to the location to insert, apply the formatting desired, and write out the text.</span></span> <span data-ttu-id="9e586-145">Se recomiendan las _secuencias de terminal virtuales_ para todo el desarrollo nuevo y en curso.</span><span class="sxs-lookup"><span data-stu-id="9e586-145">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="9e586-146">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="9e586-146">Examples</span></span>

<span data-ttu-id="9e586-147">Para obtener un ejemplo, vea [lectura y escritura de bloques de caracteres y atributos](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="9e586-147">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="9e586-148">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e586-148">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="9e586-149">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="9e586-149">Minimum supported client</span></span> | <span data-ttu-id="9e586-150">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="9e586-150">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="9e586-151">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="9e586-151">Minimum supported server</span></span> | <span data-ttu-id="9e586-152">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="9e586-152">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="9e586-153">Encabezado</span><span class="sxs-lookup"><span data-stu-id="9e586-153">Header</span></span> | <span data-ttu-id="9e586-154">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9e586-154">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="9e586-155">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="9e586-155">Library</span></span> | <span data-ttu-id="9e586-156">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="9e586-156">Kernel32.lib</span></span> |
| <span data-ttu-id="9e586-157">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="9e586-157">DLL</span></span> | <span data-ttu-id="9e586-158">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9e586-158">Kernel32.dll</span></span> |
| <span data-ttu-id="9e586-159">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="9e586-159">Unicode and ANSI names</span></span> | <span data-ttu-id="9e586-160">**WriteConsoleOutputW** (Unicode) y **WriteConsoleOutputA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="9e586-160">**WriteConsoleOutputW** (Unicode) and **WriteConsoleOutputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="9e586-161">Consulte también</span><span class="sxs-lookup"><span data-stu-id="9e586-161">See also</span></span>

[<span data-ttu-id="9e586-162">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="9e586-162">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="9e586-163">**información de carácter \_**</span><span class="sxs-lookup"><span data-stu-id="9e586-163">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="9e586-164">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="9e586-164">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="9e586-165">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="9e586-165">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="9e586-166">Funciones de salida de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="9e586-166">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="9e586-167">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="9e586-167">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="9e586-168">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="9e586-168">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="9e586-169">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="9e586-169">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="9e586-170">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="9e586-170">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="9e586-171">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="9e586-171">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="9e586-172">**PEQUEÑO \_ rectángulo**</span><span class="sxs-lookup"><span data-stu-id="9e586-172">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="9e586-173">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="9e586-173">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="9e586-174">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="9e586-174">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
