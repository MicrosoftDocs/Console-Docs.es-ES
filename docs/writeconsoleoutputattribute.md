---
title: WriteConsoleOutputAttribute función)
description: Copia un número de atributos de carácter en celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/WriteConsoleOutputAttribute
- wincon/WriteConsoleOutputAttribute
- WriteConsoleOutputAttribute
MS-HAID:
- '\_win32\_writeconsoleoutputattribute'
- base.writeconsoleoutputattribute
- consoles.writeconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 52a9d6e5-072e-4411-9945-10bd3dd61e25
topic_type:
- apiref
api_name:
- WriteConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e7c684b2f450713eaa78730676a0148e9b090c79
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061049"
---
# <a name="writeconsoleoutputattribute-function"></a><span data-ttu-id="654e4-104">WriteConsoleOutputAttribute función)</span><span class="sxs-lookup"><span data-stu-id="654e4-104">WriteConsoleOutputAttribute function</span></span>


<span data-ttu-id="654e4-105">Copia un número de atributos de carácter en celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.</span><span class="sxs-lookup"><span data-stu-id="654e4-105">Copies a number of character attributes to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

<a name="syntax"></a><span data-ttu-id="654e4-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="654e4-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

<a name="parameters"></a><span data-ttu-id="654e4-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="654e4-107">Parameters</span></span>
----------

<span data-ttu-id="654e4-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="654e4-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="654e4-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="654e4-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="654e4-110">El identificador debe tener el derecho de acceso de \*\* \_ escritura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="654e4-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="654e4-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="654e4-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="654e4-112">*lpAttribute* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="654e4-112">*lpAttribute* \[in\]</span></span>  
<span data-ttu-id="654e4-113">Atributos que se van a usar al escribir en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="654e4-113">The attributes to be used when writing to the console screen buffer.</span></span> <span data-ttu-id="654e4-114">Para obtener más información, vea [atributos de caracteres](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="654e4-114">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="654e4-115">*nLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="654e4-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="654e4-116">El número de celdas de caracteres del búfer de pantalla en las que se copiarán los atributos.</span><span class="sxs-lookup"><span data-stu-id="654e4-116">The number of screen buffer character cells to which the attributes will be copied.</span></span>

<span data-ttu-id="654e4-117">*dwWriteCoord* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="654e4-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="654e4-118">Estructura de [**coordenadas**](coord-str.md) que especifica las coordenadas de caracteres de la primera celda en el búfer de pantalla de la consola en la que se escribirán los atributos.</span><span class="sxs-lookup"><span data-stu-id="654e4-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which the attributes will be written.</span></span>

<span data-ttu-id="654e4-119">*lpNumberOfAttrsWritten* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="654e4-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="654e4-120">Puntero a una variable que recibe el número de atributos escritos realmente en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="654e4-120">A pointer to a variable that receives the number of attributes actually written to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="654e4-121">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="654e4-121">Return value</span></span>
------------

<span data-ttu-id="654e4-122">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="654e4-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="654e4-123">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="654e4-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="654e4-124">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="654e4-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="654e4-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="654e4-125">Remarks</span></span>
-------

<span data-ttu-id="654e4-126">Si el número de atributos que se va a escribir se extiende más allá del final de la fila especificada en el búfer de pantalla de la consola, los atributos se escriben en la fila siguiente.</span><span class="sxs-lookup"><span data-stu-id="654e4-126">If the number of attributes to be written to extends beyond the end of the specified row in the console screen buffer, attributes are written to the next row.</span></span> <span data-ttu-id="654e4-127">Si el número de atributos que se va a escribir se extiende más allá del final del búfer de pantalla de la consola, los atributos se escriben hasta el final del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="654e4-127">If the number of attributes to be written to extends beyond the end of the console screen buffer, the attributes are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="654e4-128">Los valores de caracteres en las posiciones escritas en no cambian.</span><span class="sxs-lookup"><span data-stu-id="654e4-128">The character values at the positions written to are not changed.</span></span>

<a name="requirements"></a><span data-ttu-id="654e4-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="654e4-129">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="654e4-130">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="654e4-130">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="654e4-131">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="654e4-131">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="654e4-132">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="654e4-132">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="654e4-133">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="654e4-133">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="654e4-134">Encabezado</span><span class="sxs-lookup"><span data-stu-id="654e4-134">Header</span></span></p></td>
<td><span data-ttu-id="654e4-135">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="654e4-135">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="654e4-136">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="654e4-136">Library</span></span></p></td>
<td><span data-ttu-id="654e4-137">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="654e4-137">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="654e4-138">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="654e4-138">DLL</span></span></p></td>
<td><span data-ttu-id="654e4-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="654e4-139">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="654e4-140"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="654e4-140"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="654e4-141">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="654e4-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="654e4-142">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="654e4-142">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="654e4-143">Funciones de salida de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="654e4-143">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="654e4-144">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="654e4-144">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="654e4-145">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="654e4-145">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="654e4-146">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="654e4-146">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="654e4-147">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="654e4-147">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="654e4-148">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="654e4-148">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




