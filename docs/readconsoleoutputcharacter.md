---
title: ReadConsoleOutputCharacter función)
description: Copia un número de caracteres de las celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/ReadConsoleOutputCharacter
- wincon/ReadConsoleOutputCharacter
- ReadConsoleOutputCharacter
- consoleapi2/ReadConsoleOutputCharacterA
- wincon/ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterA
- consoleapi2/ReadConsoleOutputCharacterW
- wincon/ReadConsoleOutputCharacterW
- ReadConsoleOutputCharacterW
MS-HAID:
- '\_win32\_readconsoleoutputcharacter'
- base.readconsoleoutputcharacter
- consoles.readconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f47464a9-6c59-4f15-abd0-be29ab515698
topic_type:
- apiref
api_name:
- ReadConsoleOutputCharacter
- ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 8f761d10951e6df77a54fd075c29379657204a99
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060988"
---
# <a name="readconsoleoutputcharacter-function"></a><span data-ttu-id="df4ea-104">ReadConsoleOutputCharacter función)</span><span class="sxs-lookup"><span data-stu-id="df4ea-104">ReadConsoleOutputCharacter function</span></span>


<span data-ttu-id="df4ea-105">Copia un número de caracteres de las celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.</span><span class="sxs-lookup"><span data-stu-id="df4ea-105">Copies a number of characters from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

<a name="syntax"></a><span data-ttu-id="df4ea-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="df4ea-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPTSTR  lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfCharsRead
);
```

<a name="parameters"></a><span data-ttu-id="df4ea-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="df4ea-107">Parameters</span></span>
----------

<span data-ttu-id="df4ea-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="df4ea-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="df4ea-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="df4ea-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="df4ea-110">El identificador debe tener el derecho de acceso de \*\* \_ lectura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="df4ea-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="df4ea-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="df4ea-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="df4ea-112">*lpCharacter* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="df4ea-112">*lpCharacter* \[out\]</span></span>  
<span data-ttu-id="df4ea-113">Un puntero a un búfer que recibe los caracteres leídos del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="df4ea-113">A pointer to a buffer that receives the characters read from the console screen buffer.</span></span>

<span data-ttu-id="df4ea-114">*nLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="df4ea-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="df4ea-115">Número de celdas de caracteres del búfer de pantalla desde las que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="df4ea-115">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="df4ea-116">El tamaño del búfer al que apunta el parámetro *lpCharacter* debe ser `nLength * sizeof(TCHAR)` .</span><span class="sxs-lookup"><span data-stu-id="df4ea-116">The size of the buffer pointed to by the *lpCharacter* parameter should be `nLength * sizeof(TCHAR)`.</span></span>

<span data-ttu-id="df4ea-117">*dwReadCoord* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="df4ea-117">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="df4ea-118">Coordenadas de la primera celda en el búfer de pantalla de la consola desde la que se va a leer, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="df4ea-118">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="df4ea-119">El miembro **X** de la estructura [**coordenadas**](coord-str.md) es la columna y el miembro **y** es la fila.</span><span class="sxs-lookup"><span data-stu-id="df4ea-119">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="df4ea-120">*lpNumberOfCharsRead* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="df4ea-120">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="df4ea-121">Puntero a una variable que recibe el número de caracteres leídos realmente.</span><span class="sxs-lookup"><span data-stu-id="df4ea-121">A pointer to a variable that receives the number of characters actually read.</span></span>

<a name="return-value"></a><span data-ttu-id="df4ea-122">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="df4ea-122">Return value</span></span>
------------

<span data-ttu-id="df4ea-123">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="df4ea-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="df4ea-124">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="df4ea-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="df4ea-125">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="df4ea-125">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="df4ea-126">Observaciones</span><span class="sxs-lookup"><span data-stu-id="df4ea-126">Remarks</span></span>
-------

<span data-ttu-id="df4ea-127">Si el número de caracteres que se van a leer de se extiende más allá del final de la fila de búfer de pantalla especificada, se leen los caracteres de la fila siguiente.</span><span class="sxs-lookup"><span data-stu-id="df4ea-127">If the number of characters to be read from extends beyond the end of the specified screen buffer row, characters are read from the next row.</span></span> <span data-ttu-id="df4ea-128">Si el número de caracteres que se van a leer de se extiende más allá del final del búfer de pantalla de la consola, se leen los caracteres hasta el final del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="df4ea-128">If the number of characters to be read from extends beyond the end of the console screen buffer, characters up to the end of the console screen buffer are read.</span></span>

<span data-ttu-id="df4ea-129">Esta función usa caracteres Unicode o caracteres de 8 bits de la página de códigos actual de la consola.</span><span class="sxs-lookup"><span data-stu-id="df4ea-129">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="df4ea-130">La página de códigos de la consola tiene como valor predeterminado la página de códigos OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="df4ea-130">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="df4ea-131">Para cambiar la página de códigos de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) , o bien use los comandos **chcp** o **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="df4ea-131">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="df4ea-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df4ea-132">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="df4ea-133">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="df4ea-133">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="df4ea-134">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="df4ea-134">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="df4ea-135">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="df4ea-135">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="df4ea-136">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="df4ea-136">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="df4ea-137">Encabezado</span><span class="sxs-lookup"><span data-stu-id="df4ea-137">Header</span></span></p></td>
<td><span data-ttu-id="df4ea-138">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="df4ea-138">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="df4ea-139">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="df4ea-139">Library</span></span></p></td>
<td><span data-ttu-id="df4ea-140">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="df4ea-140">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="df4ea-141">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="df4ea-141">DLL</span></span></p></td>
<td><span data-ttu-id="df4ea-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="df4ea-142">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="df4ea-143">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="df4ea-143">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="df4ea-144"><strong>ReadConsoleOutputCharacterW</strong> (Unicode) y <strong>ReadConsoleOutputCharacterA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="df4ea-144"><strong>ReadConsoleOutputCharacterW</strong> (Unicode) and <strong>ReadConsoleOutputCharacterA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="df4ea-145"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="df4ea-145"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="df4ea-146">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="df4ea-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="df4ea-147">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="df4ea-147">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="df4ea-148">Funciones de salida de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="df4ea-148">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="df4ea-149">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="df4ea-149">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="df4ea-150">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="df4ea-150">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="df4ea-151">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="df4ea-151">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="df4ea-152">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="df4ea-152">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="df4ea-153">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="df4ea-153">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="df4ea-154">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="df4ea-154">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="df4ea-155">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="df4ea-155">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




