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
ms.openlocfilehash: 0b8f5b33233f49167c67a47f33e5a95b8864f7bd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039140"
---
# <a name="createconsolescreenbuffer-function"></a><span data-ttu-id="27f0c-104">CreateConsoleScreenBuffer función)</span><span class="sxs-lookup"><span data-stu-id="27f0c-104">CreateConsoleScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="27f0c-105">Crea un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="27f0c-105">Creates a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="27f0c-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="27f0c-106">Syntax</span></span>

```C
HANDLE WINAPI CreateConsoleScreenBuffer(
  _In_             DWORD               dwDesiredAccess,
  _In_             DWORD               dwShareMode,
  _In_opt_   const SECURITY_ATTRIBUTES *lpSecurityAttributes,
  _In_             DWORD               dwFlags,
  _Reserved_       LPVOID              lpScreenBufferData
);
```

## <a name="parameters"></a><span data-ttu-id="27f0c-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27f0c-107">Parameters</span></span>

<span data-ttu-id="27f0c-108">*dwDesiredAccess* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="27f0c-108">*dwDesiredAccess* \[in\]</span></span>  
<span data-ttu-id="27f0c-109">El acceso al búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="27f0c-109">The access to the console screen buffer.</span></span> <span data-ttu-id="27f0c-110">Para obtener una lista de derechos de acceso, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="27f0c-110">For a list of access rights, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="27f0c-111">*dwShareMode* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="27f0c-111">*dwShareMode* \[in\]</span></span>  
<span data-ttu-id="27f0c-112">Este parámetro puede ser cero, lo que indica que no se puede compartir el búfer o puede ser uno o varios de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="27f0c-112">This parameter can be zero, indicating that the buffer cannot be shared, or it can be one or more of the following values.</span></span>

| <span data-ttu-id="27f0c-113">Valor</span><span class="sxs-lookup"><span data-stu-id="27f0c-113">Value</span></span> | <span data-ttu-id="27f0c-114">Significado</span><span class="sxs-lookup"><span data-stu-id="27f0c-114">Meaning</span></span> |
|-|-|
| <span data-ttu-id="27f0c-115">**FILE_SHARE_READ** 0x00000001</span><span class="sxs-lookup"><span data-stu-id="27f0c-115">**FILE_SHARE_READ** 0x00000001</span></span> | <span data-ttu-id="27f0c-116">Se pueden realizar otras operaciones de apertura en el búfer de pantalla de la consola para tener acceso de lectura.</span><span class="sxs-lookup"><span data-stu-id="27f0c-116">Other open operations can be performed on the console screen buffer for read access.</span></span> |
| <span data-ttu-id="27f0c-117">**FILE_SHARE_WRITE** 0x00000002</span><span class="sxs-lookup"><span data-stu-id="27f0c-117">**FILE_SHARE_WRITE** 0x00000002</span></span> | <span data-ttu-id="27f0c-118">Se pueden realizar otras operaciones de apertura en el búfer de pantalla de la consola para el acceso de escritura.</span><span class="sxs-lookup"><span data-stu-id="27f0c-118">Other open operations can be performed on the console screen buffer for write access.</span></span> |

<span data-ttu-id="27f0c-119">*lpSecurityAttributes* \[ en, opcional\]</span><span class="sxs-lookup"><span data-stu-id="27f0c-119">*lpSecurityAttributes* \[in, optional\]</span></span>  
<span data-ttu-id="27f0c-120">Puntero a una estructura [**de \_ atributos de seguridad**](https://msdn.microsoft.com/library/windows/desktop/aa379560) que determina si los procesos secundarios pueden heredar el identificador devuelto.</span><span class="sxs-lookup"><span data-stu-id="27f0c-120">A pointer to a [**SECURITY\_ATTRIBUTES**](https://msdn.microsoft.com/library/windows/desktop/aa379560) structure that determines whether the returned handle can be inherited by child processes.</span></span> <span data-ttu-id="27f0c-121">Si *lpSecurityAttributes* es **null** , el identificador no se puede heredar.</span><span class="sxs-lookup"><span data-stu-id="27f0c-121">If *lpSecurityAttributes* is **NULL** , the handle cannot be inherited.</span></span> <span data-ttu-id="27f0c-122">El miembro **lpSecurityDescriptor** de la estructura especifica un descriptor de seguridad para el nuevo búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="27f0c-122">The **lpSecurityDescriptor** member of the structure specifies a security descriptor for the new console screen buffer.</span></span> <span data-ttu-id="27f0c-123">Si *lpSecurityAttributes* es **null** , el búfer de pantalla de la consola obtiene un descriptor de seguridad predeterminado.</span><span class="sxs-lookup"><span data-stu-id="27f0c-123">If *lpSecurityAttributes* is **NULL** , the console screen buffer gets a default security descriptor.</span></span> <span data-ttu-id="27f0c-124">Las ACL del descriptor de seguridad predeterminado para un búfer de pantalla de la consola proceden del token principal o de suplantación del creador.</span><span class="sxs-lookup"><span data-stu-id="27f0c-124">The ACLs in the default security descriptor for a console screen buffer come from the primary or impersonation token of the creator.</span></span>

<span data-ttu-id="27f0c-125">*dwFlags* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="27f0c-125">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="27f0c-126">El tipo de búfer de pantalla de la consola que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="27f0c-126">The type of console screen buffer to create.</span></span> <span data-ttu-id="27f0c-127">El único tipo de búfer de pantalla compatible es el **\_ \_ búfer TEXTMODE** de la consola.</span><span class="sxs-lookup"><span data-stu-id="27f0c-127">The only supported screen buffer type is **CONSOLE\_TEXTMODE\_BUFFER** .</span></span>

<span data-ttu-id="27f0c-128">*lpScreenBufferData*</span><span class="sxs-lookup"><span data-stu-id="27f0c-128">*lpScreenBufferData*</span></span>  
<span data-ttu-id="27f0c-129">Sector debe ser **null** .</span><span class="sxs-lookup"><span data-stu-id="27f0c-129">Reserved; should be **NULL** .</span></span>

## <a name="return-value"></a><span data-ttu-id="27f0c-130">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="27f0c-130">Return value</span></span>

<span data-ttu-id="27f0c-131">Si la función se ejecuta correctamente, el valor devuelto es un identificador del nuevo búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="27f0c-131">If the function succeeds, the return value is a handle to the new console screen buffer.</span></span>

<span data-ttu-id="27f0c-132">Si se produce un error en la función, el valor devuelto es un **\_ \_ valor de identificador no válido** .</span><span class="sxs-lookup"><span data-stu-id="27f0c-132">If the function fails, the return value is **INVALID\_HANDLE\_VALUE** .</span></span> <span data-ttu-id="27f0c-133">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="27f0c-133">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="27f0c-134">Comentarios</span><span class="sxs-lookup"><span data-stu-id="27f0c-134">Remarks</span></span>

<span data-ttu-id="27f0c-135">Una consola de puede tener varios búferes de pantalla, pero solo un búfer de pantalla activo.</span><span class="sxs-lookup"><span data-stu-id="27f0c-135">A console can have multiple screen buffers but only one active screen buffer.</span></span> <span data-ttu-id="27f0c-136">Se puede tener acceso a los búferes de pantalla inactivos para lectura y escritura, pero solo se muestra el búfer de pantalla activo.</span><span class="sxs-lookup"><span data-stu-id="27f0c-136">Inactive screen buffers can be accessed for reading and writing, but only the active screen buffer is displayed.</span></span> <span data-ttu-id="27f0c-137">Para convertir el nuevo búfer de pantalla en el búfer de pantalla activo, utilice la función [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="27f0c-137">To make the new screen buffer the active screen buffer, use the [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) function.</span></span>

<span data-ttu-id="27f0c-138">El búfer de pantalla recién creado copiará algunas propiedades del búfer de pantalla activo en el momento en que se llama a esta función.</span><span class="sxs-lookup"><span data-stu-id="27f0c-138">The newly created screen buffer will copy some properties from the active screen buffer at the time that this function is called.</span></span> <span data-ttu-id="27f0c-139">El comportamiento es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="27f0c-139">The behavior is as follows:</span></span>

- <span data-ttu-id="27f0c-140">`Font` -copiado del búfer de pantalla activo</span><span class="sxs-lookup"><span data-stu-id="27f0c-140">`Font` - copied from active screen buffer</span></span>
- <span data-ttu-id="27f0c-141">`Display Window Size` -copiado del búfer de pantalla activo</span><span class="sxs-lookup"><span data-stu-id="27f0c-141">`Display Window Size` - copied from active screen buffer</span></span>
- <span data-ttu-id="27f0c-142">`Buffer Size` -coincide con `Display Window Size` ( **no** copiado)</span><span class="sxs-lookup"><span data-stu-id="27f0c-142">`Buffer Size` - matched to `Display Window Size` ( **NOT** copied)</span></span>
- <span data-ttu-id="27f0c-143">`Default Attributes` (colores): copiado del búfer de pantalla activo</span><span class="sxs-lookup"><span data-stu-id="27f0c-143">`Default Attributes` (colors) - copied from active screen buffer</span></span>
- <span data-ttu-id="27f0c-144">`Default Popup Attributes` (colores): copiado del búfer de pantalla activo</span><span class="sxs-lookup"><span data-stu-id="27f0c-144">`Default Popup Attributes` (colors) - copied from active screen buffer</span></span>

<span data-ttu-id="27f0c-145">El proceso de llamada puede usar el identificador devuelto en cualquier función que requiera un identificador a un búfer de pantalla de la consola, de acuerdo con las limitaciones de acceso especificadas por el parámetro *dwDesiredAccess* .</span><span class="sxs-lookup"><span data-stu-id="27f0c-145">The calling process can use the returned handle in any function that requires a handle to a console screen buffer, subject to the limitations of access specified by the *dwDesiredAccess* parameter.</span></span>

<span data-ttu-id="27f0c-146">El proceso de llamada puede usar la función [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) para crear un controlador de búfer de pantalla duplicado que tenga un acceso o una herencia diferentes del identificador original.</span><span class="sxs-lookup"><span data-stu-id="27f0c-146">The calling process can use the [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) function to create a duplicate screen buffer handle that has different access or inheritability from the original handle.</span></span> <span data-ttu-id="27f0c-147">Sin embargo, **DuplicateHandle** no se puede usar para crear un duplicado que sea válido para un proceso diferente (excepto a través de la herencia).</span><span class="sxs-lookup"><span data-stu-id="27f0c-147">However, **DuplicateHandle** cannot be used to create a duplicate that is valid for a different process (except through inheritance).</span></span>

<span data-ttu-id="27f0c-148">Para cerrar el identificador de búfer de pantalla de la consola, use la función [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) .</span><span class="sxs-lookup"><span data-stu-id="27f0c-148">To close the console screen buffer handle, use the [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) function.</span></span>

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a><span data-ttu-id="27f0c-149">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="27f0c-149">Examples</span></span>

<span data-ttu-id="27f0c-150">Para obtener un ejemplo, vea [lectura y escritura de bloques de caracteres y atributos](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="27f0c-150">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="27f0c-151">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27f0c-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="27f0c-152">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="27f0c-152">Minimum supported client</span></span> | <span data-ttu-id="27f0c-153">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="27f0c-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="27f0c-154">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="27f0c-154">Minimum supported server</span></span> | <span data-ttu-id="27f0c-155">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="27f0c-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="27f0c-156">Encabezado</span><span class="sxs-lookup"><span data-stu-id="27f0c-156">Header</span></span> | <span data-ttu-id="27f0c-157">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="27f0c-157">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="27f0c-158">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="27f0c-158">Library</span></span> | <span data-ttu-id="27f0c-159">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="27f0c-159">Kernel32.lib</span></span> |
| <span data-ttu-id="27f0c-160">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="27f0c-160">DLL</span></span> | <span data-ttu-id="27f0c-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="27f0c-161">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="27f0c-162">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27f0c-162">See also</span></span>

[<span data-ttu-id="27f0c-163">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="27f0c-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="27f0c-164">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="27f0c-164">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="27f0c-165">**CloseHandle**</span><span class="sxs-lookup"><span data-stu-id="27f0c-165">**CloseHandle**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724211)

[<span data-ttu-id="27f0c-166">**DuplicateHandle**</span><span class="sxs-lookup"><span data-stu-id="27f0c-166">**DuplicateHandle**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724251)

[<span data-ttu-id="27f0c-167">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="27f0c-167">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="27f0c-168">**atributos de seguridad \_**</span><span class="sxs-lookup"><span data-stu-id="27f0c-168">**SECURITY\_ATTRIBUTES**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa379560)

[<span data-ttu-id="27f0c-169">**SetConsoleActiveScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="27f0c-169">**SetConsoleActiveScreenBuffer**</span></span>](setconsoleactivescreenbuffer.md)

[<span data-ttu-id="27f0c-170">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="27f0c-170">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)
