---
title: FillConsoleOutputCharacter función)
description: Escribe un carácter en el búfer de la pantalla de la consola un número especificado de veces, comenzando en las coordenadas especificadas.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/FillConsoleOutputCharacter
- wincon/FillConsoleOutputCharacter
- FillConsoleOutputCharacter
- consoleapi2/FillConsoleOutputCharacterA
- wincon/FillConsoleOutputCharacterA
- FillConsoleOutputCharacterA
- consoleapi2/FillConsoleOutputCharacterW
- wincon/FillConsoleOutputCharacterW
- FillConsoleOutputCharacterW
MS-HAID:
- '\_win32\_fillconsoleoutputcharacter'
- base.fillconsoleoutputcharacter
- consoles.fillconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 37579cc9-14b3-4fd9-81ed-abaad5c7bd1a
topic_type:
- apiref
api_name:
- FillConsoleOutputCharacter
- FillConsoleOutputCharacterA
- FillConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d11e0ef196f9923f1478e17faacd41b43a0511eb
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060748"
---
# <a name="fillconsoleoutputcharacter-function"></a><span data-ttu-id="d649b-104">FillConsoleOutputCharacter función)</span><span class="sxs-lookup"><span data-stu-id="d649b-104">FillConsoleOutputCharacter function</span></span>


<span data-ttu-id="d649b-105">Escribe un carácter en el búfer de la pantalla de la consola un número especificado de veces, comenzando en las coordenadas especificadas.</span><span class="sxs-lookup"><span data-stu-id="d649b-105">Writes a character to the console screen buffer a specified number of times, beginning at the specified coordinates.</span></span>

<a name="syntax"></a><span data-ttu-id="d649b-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d649b-106">Syntax</span></span>
------

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

<a name="parameters"></a><span data-ttu-id="d649b-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="d649b-107">Parameters</span></span>
----------

<span data-ttu-id="d649b-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="d649b-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="d649b-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="d649b-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="d649b-110">El identificador debe tener el derecho de acceso de \*\* \_ escritura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="d649b-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="d649b-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="d649b-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="d649b-112">*cCharacter* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="d649b-112">*cCharacter* \[in\]</span></span>  
<span data-ttu-id="d649b-113">Carácter que se va a escribir en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="d649b-113">The character to be written to the console screen buffer.</span></span>

<span data-ttu-id="d649b-114">*nLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="d649b-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="d649b-115">El número de celdas de caracteres en las que se debe escribir el carácter.</span><span class="sxs-lookup"><span data-stu-id="d649b-115">The number of character cells to which the character should be written.</span></span>

<span data-ttu-id="d649b-116">*dwWriteCoord* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="d649b-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="d649b-117">Estructura de [**coordenadas**](coord-str.md) que especifica las coordenadas de caracteres de la primera celda en la que se va a escribir el carácter.</span><span class="sxs-lookup"><span data-stu-id="d649b-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell to which the character is to be written.</span></span>

<span data-ttu-id="d649b-118">*lpNumberOfCharsWritten* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="d649b-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="d649b-119">Puntero a una variable que recibe el número de caracteres escritos realmente en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="d649b-119">A pointer to a variable that receives the number of characters actually written to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="d649b-120">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="d649b-120">Return value</span></span>
------------

<span data-ttu-id="d649b-121">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="d649b-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d649b-122">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="d649b-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d649b-123">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="d649b-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="d649b-124">Observaciones</span><span class="sxs-lookup"><span data-stu-id="d649b-124">Remarks</span></span>
-------

<span data-ttu-id="d649b-125">Si el número de caracteres que se va a escribir se extiende más allá del final de la fila especificada en el búfer de pantalla de la consola, los caracteres se escriben en la fila siguiente.</span><span class="sxs-lookup"><span data-stu-id="d649b-125">If the number of characters to write to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="d649b-126">Si el número de caracteres que se va a escribir se extiende más allá del final del búfer de pantalla de la consola, los caracteres se escriben al final del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="d649b-126">If the number of characters to write to extends beyond the end of the console screen buffer, the characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="d649b-127">Los valores de atributo en las posiciones escritas no cambian.</span><span class="sxs-lookup"><span data-stu-id="d649b-127">The attribute values at the positions written are not changed.</span></span>

<span data-ttu-id="d649b-128">Esta función usa caracteres Unicode o caracteres de 8 bits de la página de códigos actual de la consola.</span><span class="sxs-lookup"><span data-stu-id="d649b-128">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="d649b-129">La página de códigos de la consola tiene como valor predeterminado la página de códigos OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="d649b-129">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="d649b-130">Para cambiar la página de códigos de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) , o bien use los comandos **chcp** o **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="d649b-130">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="d649b-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d649b-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="d649b-132">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="d649b-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="d649b-133">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="d649b-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d649b-134">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="d649b-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="d649b-135">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="d649b-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d649b-136">Encabezado</span><span class="sxs-lookup"><span data-stu-id="d649b-136">Header</span></span></p></td>
<td><span data-ttu-id="d649b-137">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d649b-137">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d649b-138">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="d649b-138">Library</span></span></p></td>
<td><span data-ttu-id="d649b-139">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="d649b-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d649b-140">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="d649b-140">DLL</span></span></p></td>
<td><span data-ttu-id="d649b-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d649b-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d649b-142">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="d649b-142">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="d649b-143"><strong>FillConsoleOutputCharacterW</strong> (Unicode) y <strong>FillConsoleOutputCharacterA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="d649b-143"><strong>FillConsoleOutputCharacterW</strong> (Unicode) and <strong>FillConsoleOutputCharacterA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="d649b-144"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="d649b-144"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="d649b-145">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="d649b-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d649b-146">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="d649b-146">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="d649b-147">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="d649b-147">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="d649b-148">Funciones de salida de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="d649b-148">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="d649b-149">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="d649b-149">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="d649b-150">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="d649b-150">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="d649b-151">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="d649b-151">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




