---
title: ReadConsoleOutputAttribute función)
description: Copia un número especificado de atributos de carácter de las celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/ReadConsoleOutputAttribute
- wincon/ReadConsoleOutputAttribute
- ReadConsoleOutputAttribute
MS-HAID:
- '\_win32\_readconsoleoutputattribute'
- base.readconsoleoutputattribute
- consoles.readconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c3e35779-a487-47f1-8d07-0d5fae99d54a
topic_type:
- apiref
api_name:
- ReadConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d4cf3ac9b85c3eab73c3530c1fd9991a7fbbf5a5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061001"
---
# <a name="readconsoleoutputattribute-function"></a><span data-ttu-id="74063-104">ReadConsoleOutputAttribute función)</span><span class="sxs-lookup"><span data-stu-id="74063-104">ReadConsoleOutputAttribute function</span></span>


<span data-ttu-id="74063-105">Copia un número especificado de atributos de carácter de las celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.</span><span class="sxs-lookup"><span data-stu-id="74063-105">Copies a specified number of character attributes from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

<a name="syntax"></a><span data-ttu-id="74063-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="74063-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPWORD  lpAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfAttrsRead
);
```

<a name="parameters"></a><span data-ttu-id="74063-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="74063-107">Parameters</span></span>
----------

<span data-ttu-id="74063-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="74063-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="74063-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="74063-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="74063-110">El identificador debe tener el derecho de acceso de \*\* \_ lectura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="74063-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="74063-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="74063-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="74063-112">*lpAttribute* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="74063-112">*lpAttribute* \[out\]</span></span>  
<span data-ttu-id="74063-113">Un puntero a un búfer que recibe los atributos utilizados por el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="74063-113">A pointer to a buffer that receives the attributes being used by the console screen buffer.</span></span>

<span data-ttu-id="74063-114">Para obtener más información, vea [atributos de caracteres](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="74063-114">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="74063-115">*nLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="74063-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="74063-116">Número de celdas de caracteres del búfer de pantalla desde las que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="74063-116">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="74063-117">El tamaño del búfer al que apunta el parámetro *lpAttribute* debe ser `nLength * sizeof(WORD)` .</span><span class="sxs-lookup"><span data-stu-id="74063-117">The size of the buffer pointed to by the *lpAttribute* parameter should be `nLength * sizeof(WORD)`.</span></span>

<span data-ttu-id="74063-118">*dwReadCoord* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="74063-118">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="74063-119">Coordenadas de la primera celda en el búfer de pantalla de la consola desde la que se va a leer, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="74063-119">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="74063-120">El miembro **X** de la estructura [**coordenadas**](coord-str.md) es la columna y el miembro **y** es la fila.</span><span class="sxs-lookup"><span data-stu-id="74063-120">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="74063-121">*lpNumberOfAttrsRead* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="74063-121">*lpNumberOfAttrsRead* \[out\]</span></span>  
<span data-ttu-id="74063-122">Puntero a una variable que recibe el número de atributos leídos realmente.</span><span class="sxs-lookup"><span data-stu-id="74063-122">A pointer to a variable that receives the number of attributes actually read.</span></span>

<a name="return-value"></a><span data-ttu-id="74063-123">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="74063-123">Return value</span></span>
------------

<span data-ttu-id="74063-124">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="74063-124">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="74063-125">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="74063-125">If the function fails, the return value is zero.</span></span> <span data-ttu-id="74063-126">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="74063-126">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="74063-127">Observaciones</span><span class="sxs-lookup"><span data-stu-id="74063-127">Remarks</span></span>
-------

<span data-ttu-id="74063-128">Si el número de atributos que se van a leer de se extiende más allá del final de la fila de búfer de pantalla especificada, los atributos se leen de la fila siguiente.</span><span class="sxs-lookup"><span data-stu-id="74063-128">If the number of attributes to be read from extends beyond the end of the specified screen buffer row, attributes are read from the next row.</span></span> <span data-ttu-id="74063-129">Si el número de atributos que se van a leer se extiende más allá del final del búfer de pantalla de la consola, se leen los atributos hasta el final del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="74063-129">If the number of attributes to be read from extends beyond the end of the console screen buffer, attributes up to the end of the console screen buffer are read.</span></span>

<a name="requirements"></a><span data-ttu-id="74063-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="74063-130">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="74063-131">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="74063-131">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="74063-132">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="74063-132">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="74063-133">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="74063-133">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="74063-134">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="74063-134">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="74063-135">Encabezado</span><span class="sxs-lookup"><span data-stu-id="74063-135">Header</span></span></p></td>
<td><span data-ttu-id="74063-136">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="74063-136">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="74063-137">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="74063-137">Library</span></span></p></td>
<td><span data-ttu-id="74063-138">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="74063-138">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="74063-139">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="74063-139">DLL</span></span></p></td>
<td><span data-ttu-id="74063-140">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="74063-140">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="74063-141"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="74063-141"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="74063-142">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="74063-142">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="74063-143">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="74063-143">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="74063-144">Funciones de salida de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="74063-144">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="74063-145">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="74063-145">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="74063-146">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="74063-146">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="74063-147">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="74063-147">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="74063-148">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="74063-148">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="74063-149">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="74063-149">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




