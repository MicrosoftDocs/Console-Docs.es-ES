---
title: CreateConsoleScreenBuffer función)
description: La función CreateConsoleScreenBuffer crea un búfer de pantalla para la consola de Windows.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/CreateConsoleScreenBuffer
- wincon/CreateConsoleScreenBuffer
- CreateConsoleScreenBuffer
MS-HAID:
- '\_win32\_createconsolescreenbuffer'
- base.createconsolescreenbuffer
- consoles.createconsolescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98bb74e4-dad2-4615-9263-48ba778a06ff
topic_type:
- apiref
api_name:
- CreateConsoleScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 289908708fb1c89c3ec3d990c9e8bf2649914a1b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060773"
---
# <a name="createconsolescreenbuffer-function"></a><span data-ttu-id="b2692-104">CreateConsoleScreenBuffer función)</span><span class="sxs-lookup"><span data-stu-id="b2692-104">CreateConsoleScreenBuffer function</span></span>


<span data-ttu-id="b2692-105">Crea un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="b2692-105">Creates a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="b2692-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b2692-106">Syntax</span></span>
------

```C
HANDLE WINAPI CreateConsoleScreenBuffer(
  _In_             DWORD               dwDesiredAccess,
  _In_             DWORD               dwShareMode,
  _In_opt_   const SECURITY_ATTRIBUTES *lpSecurityAttributes,
  _In_             DWORD               dwFlags,
  _Reserved_       LPVOID              lpScreenBufferData
);
```

<a name="parameters"></a><span data-ttu-id="b2692-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b2692-107">Parameters</span></span>
----------

<span data-ttu-id="b2692-108">*dwDesiredAccess* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="b2692-108">*dwDesiredAccess* \[in\]</span></span>  
<span data-ttu-id="b2692-109">El acceso al búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="b2692-109">The access to the console screen buffer.</span></span> <span data-ttu-id="b2692-110">Para obtener una lista de derechos de acceso, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="b2692-110">For a list of access rights, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="b2692-111">*dwShareMode* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="b2692-111">*dwShareMode* \[in\]</span></span>  
<span data-ttu-id="b2692-112">Este parámetro puede ser cero, lo que indica que no se puede compartir el búfer o puede ser uno o varios de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="b2692-112">This parameter can be zero, indicating that the buffer cannot be shared, or it can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="b2692-113">Valor</span><span class="sxs-lookup"><span data-stu-id="b2692-113">Value</span></span></th>
<th><span data-ttu-id="b2692-114">Significado</span><span class="sxs-lookup"><span data-stu-id="b2692-114">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="b2692-115"><span id="FILE_SHARE_READ"></span><span id="file_share_read"></span>
<strong>FILE_SHARE_READ</strong> 0x00000001</span><span class="sxs-lookup"><span data-stu-id="b2692-115"><span id="FILE_SHARE_READ"></span><span id="file_share_read"></span>
<strong>FILE_SHARE_READ</strong> 0x00000001</span></span></td>
<td><p><span data-ttu-id="b2692-116">Se pueden realizar otras operaciones de apertura en el búfer de pantalla de la consola para tener acceso de lectura.</span><span class="sxs-lookup"><span data-stu-id="b2692-116">Other open operations can be performed on the console screen buffer for read access.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="b2692-117"><span id="FILE_SHARE_WRITE"></span><span id="file_share_write"></span>
<strong>FILE_SHARE_WRITE</strong> 0x00000002</span><span class="sxs-lookup"><span data-stu-id="b2692-117"><span id="FILE_SHARE_WRITE"></span><span id="file_share_write"></span>
<strong>FILE_SHARE_WRITE</strong> 0x00000002</span></span></td>
<td><p><span data-ttu-id="b2692-118">Se pueden realizar otras operaciones de apertura en el búfer de pantalla de la consola para el acceso de escritura.</span><span class="sxs-lookup"><span data-stu-id="b2692-118">Other open operations can be performed on the console screen buffer for write access.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="b2692-119">*lpSecurityAttributes* \[ en, opcional\]</span><span class="sxs-lookup"><span data-stu-id="b2692-119">*lpSecurityAttributes* \[in, optional\]</span></span>  
<span data-ttu-id="b2692-120">Puntero a una estructura [**de \_ atributos de seguridad**](https://msdn.microsoft.com/library/windows/desktop/aa379560) que determina si los procesos secundarios pueden heredar el identificador devuelto.</span><span class="sxs-lookup"><span data-stu-id="b2692-120">A pointer to a [**SECURITY\_ATTRIBUTES**](https://msdn.microsoft.com/library/windows/desktop/aa379560) structure that determines whether the returned handle can be inherited by child processes.</span></span> <span data-ttu-id="b2692-121">Si *lpSecurityAttributes* es **null**, el identificador no se puede heredar.</span><span class="sxs-lookup"><span data-stu-id="b2692-121">If *lpSecurityAttributes* is **NULL**, the handle cannot be inherited.</span></span> <span data-ttu-id="b2692-122">El miembro **lpSecurityDescriptor** de la estructura especifica un descriptor de seguridad para el nuevo búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="b2692-122">The **lpSecurityDescriptor** member of the structure specifies a security descriptor for the new console screen buffer.</span></span> <span data-ttu-id="b2692-123">Si *lpSecurityAttributes* es **null**, el búfer de pantalla de la consola obtiene un descriptor de seguridad predeterminado.</span><span class="sxs-lookup"><span data-stu-id="b2692-123">If *lpSecurityAttributes* is **NULL**, the console screen buffer gets a default security descriptor.</span></span> <span data-ttu-id="b2692-124">Las ACL del descriptor de seguridad predeterminado para un búfer de pantalla de la consola proceden del token principal o de suplantación del creador.</span><span class="sxs-lookup"><span data-stu-id="b2692-124">The ACLs in the default security descriptor for a console screen buffer come from the primary or impersonation token of the creator.</span></span>

<span data-ttu-id="b2692-125">*dwFlags* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="b2692-125">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="b2692-126">El tipo de búfer de pantalla de la consola que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="b2692-126">The type of console screen buffer to create.</span></span> <span data-ttu-id="b2692-127">El único tipo de búfer de pantalla compatible es el \*\* \_ \_ búfer TEXTMODE\*\*de la consola.</span><span class="sxs-lookup"><span data-stu-id="b2692-127">The only supported screen buffer type is **CONSOLE\_TEXTMODE\_BUFFER**.</span></span>

<span data-ttu-id="b2692-128">*lpScreenBufferData* </span><span class="sxs-lookup"><span data-stu-id="b2692-128">*lpScreenBufferData* </span></span>  
<span data-ttu-id="b2692-129">Sector debe ser **null**.</span><span class="sxs-lookup"><span data-stu-id="b2692-129">Reserved; should be **NULL**.</span></span>

<a name="return-value"></a><span data-ttu-id="b2692-130">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="b2692-130">Return value</span></span>
------------

<span data-ttu-id="b2692-131">Si la función se ejecuta correctamente, el valor devuelto es un identificador del nuevo búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="b2692-131">If the function succeeds, the return value is a handle to the new console screen buffer.</span></span>

<span data-ttu-id="b2692-132">Si se produce un error en la función, el valor devuelto es un \*\* \_ \_ valor de identificador no válido\*\*.</span><span class="sxs-lookup"><span data-stu-id="b2692-132">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="b2692-133">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="b2692-133">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="b2692-134">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b2692-134">Remarks</span></span>
-------

<span data-ttu-id="b2692-135">Una consola de puede tener varios búferes de pantalla, pero solo un búfer de pantalla activo.</span><span class="sxs-lookup"><span data-stu-id="b2692-135">A console can have multiple screen buffers but only one active screen buffer.</span></span> <span data-ttu-id="b2692-136">Se puede tener acceso a los búferes de pantalla inactivos para lectura y escritura, pero solo se muestra el búfer de pantalla activo.</span><span class="sxs-lookup"><span data-stu-id="b2692-136">Inactive screen buffers can be accessed for reading and writing, but only the active screen buffer is displayed.</span></span> <span data-ttu-id="b2692-137">Para convertir el nuevo búfer de pantalla en el búfer de pantalla activo, utilice la función [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="b2692-137">To make the new screen buffer the active screen buffer, use the [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) function.</span></span>

<span data-ttu-id="b2692-138">El búfer de pantalla recién creado copiará algunas propiedades del búfer de pantalla activo en el momento en que se llama a esta función.</span><span class="sxs-lookup"><span data-stu-id="b2692-138">The newly created screen buffer will copy some properties from the active screen buffer at the time that this function is called.</span></span> <span data-ttu-id="b2692-139">El comportamiento es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="b2692-139">The behavior is as follows:</span></span>
- <span data-ttu-id="b2692-140">`Font` -copiado del búfer de pantalla activo</span><span class="sxs-lookup"><span data-stu-id="b2692-140">`Font` - copied from active screen buffer</span></span>
- <span data-ttu-id="b2692-141">`Display Window Size` -copiado del búfer de pantalla activo</span><span class="sxs-lookup"><span data-stu-id="b2692-141">`Display Window Size` - copied from active screen buffer</span></span>
- <span data-ttu-id="b2692-142">`Buffer Size` -coincide con `Display Window Size` (**no** copiado)</span><span class="sxs-lookup"><span data-stu-id="b2692-142">`Buffer Size` - matched to `Display Window Size` (**NOT** copied)</span></span>
- <span data-ttu-id="b2692-143">`Default Attributes` (colores): copiado del búfer de pantalla activo</span><span class="sxs-lookup"><span data-stu-id="b2692-143">`Default Attributes` (colors) - copied from active screen buffer</span></span>
- <span data-ttu-id="b2692-144">`Default Popup Attributes` (colores): copiado del búfer de pantalla activo</span><span class="sxs-lookup"><span data-stu-id="b2692-144">`Default Popup Attributes` (colors) - copied from active screen buffer</span></span>

<span data-ttu-id="b2692-145">El proceso de llamada puede usar el identificador devuelto en cualquier función que requiera un identificador a un búfer de pantalla de la consola, de acuerdo con las limitaciones de acceso especificadas por el parámetro *dwDesiredAccess* .</span><span class="sxs-lookup"><span data-stu-id="b2692-145">The calling process can use the returned handle in any function that requires a handle to a console screen buffer, subject to the limitations of access specified by the *dwDesiredAccess* parameter.</span></span>

<span data-ttu-id="b2692-146">El proceso de llamada puede usar la función [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) para crear un controlador de búfer de pantalla duplicado que tenga un acceso o una herencia diferentes del identificador original.</span><span class="sxs-lookup"><span data-stu-id="b2692-146">The calling process can use the [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) function to create a duplicate screen buffer handle that has different access or inheritability from the original handle.</span></span> <span data-ttu-id="b2692-147">Sin embargo, **DuplicateHandle** no se puede usar para crear un duplicado que sea válido para un proceso diferente (excepto a través de la herencia).</span><span class="sxs-lookup"><span data-stu-id="b2692-147">However, **DuplicateHandle** cannot be used to create a duplicate that is valid for a different process (except through inheritance).</span></span>

<span data-ttu-id="b2692-148">Para cerrar el identificador de búfer de pantalla de la consola, use la función [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) .</span><span class="sxs-lookup"><span data-stu-id="b2692-148">To close the console screen buffer handle, use the [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) function.</span></span>

<a name="examples"></a><span data-ttu-id="b2692-149">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="b2692-149">Examples</span></span>
--------

<span data-ttu-id="b2692-150">Para obtener un ejemplo, vea [lectura y escritura de bloques de caracteres y atributos](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b2692-150">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

<a name="requirements"></a><span data-ttu-id="b2692-151">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2692-151">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b2692-152">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="b2692-152">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="b2692-153">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="b2692-153">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b2692-154">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="b2692-154">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="b2692-155">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="b2692-155">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b2692-156">Encabezado</span><span class="sxs-lookup"><span data-stu-id="b2692-156">Header</span></span></p></td>
<td><span data-ttu-id="b2692-157">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b2692-157">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b2692-158">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="b2692-158">Library</span></span></p></td>
<td><span data-ttu-id="b2692-159">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="b2692-159">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b2692-160">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="b2692-160">DLL</span></span></p></td>
<td><span data-ttu-id="b2692-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b2692-161">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="b2692-162"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="b2692-162"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="b2692-163">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="b2692-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b2692-164">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="b2692-164">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="b2692-165">**CloseHandle**</span><span class="sxs-lookup"><span data-stu-id="b2692-165">**CloseHandle**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724211)

[<span data-ttu-id="b2692-166">**DuplicateHandle**</span><span class="sxs-lookup"><span data-stu-id="b2692-166">**DuplicateHandle**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724251)

[<span data-ttu-id="b2692-167">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="b2692-167">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="b2692-168">**atributos de seguridad \_**</span><span class="sxs-lookup"><span data-stu-id="b2692-168">**SECURITY\_ATTRIBUTES**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa379560)

[<span data-ttu-id="b2692-169">**SetConsoleActiveScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="b2692-169">**SetConsoleActiveScreenBuffer**</span></span>](setconsoleactivescreenbuffer.md)

[<span data-ttu-id="b2692-170">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="b2692-170">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

 

 




