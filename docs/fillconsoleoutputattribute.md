---
title: FillConsoleOutputAttribute función)
description: Establece los atributos de carácter para un número especificado de celdas de caracteres, a partir de las coordenadas especificadas en un búfer de pantalla.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/FillConsoleOutputAttribute
- wincon/FillConsoleOutputAttribute
- FillConsoleOutputAttribute
MS-HAID:
- '\_win32\_fillconsoleoutputattribute'
- base.fillconsoleoutputattribute
- consoles.fillconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 09440263-71c4-4b7a-8fc6-a2b4fcd677ff
topic_type:
- apiref
api_name:
- FillConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4b3df3a9922655835979136a33628e2be0663f4e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060745"
---
# <a name="fillconsoleoutputattribute-function"></a><span data-ttu-id="690c3-104">FillConsoleOutputAttribute función)</span><span class="sxs-lookup"><span data-stu-id="690c3-104">FillConsoleOutputAttribute function</span></span>


<span data-ttu-id="690c3-105">Establece los atributos de carácter para un número especificado de celdas de caracteres, a partir de las coordenadas especificadas en un búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="690c3-105">Sets the character attributes for a specified number of character cells, beginning at the specified coordinates in a screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="690c3-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="690c3-106">Syntax</span></span>
------

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

<a name="parameters"></a><span data-ttu-id="690c3-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="690c3-107">Parameters</span></span>
----------

<span data-ttu-id="690c3-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="690c3-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="690c3-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="690c3-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="690c3-110">El identificador debe tener el derecho de acceso de \*\* \_ escritura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="690c3-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="690c3-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="690c3-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="690c3-112">*wAttribute* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="690c3-112">*wAttribute* \[in\]</span></span>  
<span data-ttu-id="690c3-113">Atributos que se van a usar al escribir en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="690c3-113">The attributes to use when writing to the console screen buffer.</span></span> <span data-ttu-id="690c3-114">Para obtener más información, vea [atributos de caracteres](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="690c3-114">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="690c3-115">*nLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="690c3-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="690c3-116">El número de celdas de caracteres que se van a establecer en los atributos de color especificados.</span><span class="sxs-lookup"><span data-stu-id="690c3-116">The number of character cells to be set to the specified color attributes.</span></span>

<span data-ttu-id="690c3-117">*dwWriteCoord* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="690c3-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="690c3-118">Estructura de [**coordenadas**](coord-str.md) que especifica las coordenadas de caracteres de la primera celda cuyos atributos se van a establecer.</span><span class="sxs-lookup"><span data-stu-id="690c3-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell whose attributes are to be set.</span></span>

<span data-ttu-id="690c3-119">*lpNumberOfAttrsWritten* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="690c3-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="690c3-120">Puntero a una variable que recibe el número de celdas de caracteres cuyos atributos se establecieron realmente.</span><span class="sxs-lookup"><span data-stu-id="690c3-120">A pointer to a variable that receives the number of character cells whose attributes were actually set.</span></span>

<a name="return-value"></a><span data-ttu-id="690c3-121">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="690c3-121">Return value</span></span>
------------

<span data-ttu-id="690c3-122">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="690c3-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="690c3-123">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="690c3-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="690c3-124">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="690c3-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="690c3-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="690c3-125">Remarks</span></span>
-------

<span data-ttu-id="690c3-126">Si el número de celdas de caracteres cuyos atributos se van a establecer se extiende más allá del final de la fila especificada en el búfer de pantalla de la consola, se establecen las celdas de la fila siguiente.</span><span class="sxs-lookup"><span data-stu-id="690c3-126">If the number of character cells whose attributes are to be set extends beyond the end of the specified row in the console screen buffer, the cells of the next row are set.</span></span> <span data-ttu-id="690c3-127">Si el número de celdas que se van a escribir se extiende más allá del final del búfer de pantalla de la consola, las celdas se escriben hasta el final del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="690c3-127">If the number of cells to write to extends beyond the end of the console screen buffer, the cells are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="690c3-128">Los valores de caracteres en las posiciones escritas en no cambian.</span><span class="sxs-lookup"><span data-stu-id="690c3-128">The character values at the positions written to are not changed.</span></span>

<a name="requirements"></a><span data-ttu-id="690c3-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="690c3-129">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="690c3-130">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="690c3-130">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="690c3-131">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="690c3-131">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="690c3-132">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="690c3-132">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="690c3-133">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="690c3-133">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="690c3-134">Encabezado</span><span class="sxs-lookup"><span data-stu-id="690c3-134">Header</span></span></p></td>
<td><span data-ttu-id="690c3-135">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="690c3-135">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="690c3-136">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="690c3-136">Library</span></span></p></td>
<td><span data-ttu-id="690c3-137">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="690c3-137">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="690c3-138">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="690c3-138">DLL</span></span></p></td>
<td><span data-ttu-id="690c3-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="690c3-139">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="690c3-140"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="690c3-140"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="690c3-141">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="690c3-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="690c3-142">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="690c3-142">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="690c3-143">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="690c3-143">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="690c3-144">Funciones de salida de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="690c3-144">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="690c3-145">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="690c3-145">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

[<span data-ttu-id="690c3-146">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="690c3-146">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

 

 




