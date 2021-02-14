---
title: ReadConsoleInput función)
description: Lee datos de un búfer de entrada de la consola y lo quita del búfer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/ReadConsoleInput
- wincon/ReadConsoleInput
- ReadConsoleInput
- consoleapi/ReadConsoleInputA
- wincon/ReadConsoleInputA
- ReadConsoleInputA
- consoleapi/ReadConsoleInputW
- wincon/ReadConsoleInputW
- ReadConsoleInputW
MS-HAID:
- '\_win32\_readconsoleinput'
- base.readconsoleinput
- consoles.readconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5a9f7b18-cdea-4041-a377-5532d30e0105
topic_type:
- apiref
api_name:
- ReadConsoleInput
- ReadConsoleInputA
- ReadConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 06e784ebaebde2ed68ed17f75f4e54932aa463f5
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358725"
---
# <a name="readconsoleinput-function"></a><span data-ttu-id="0b54c-104">ReadConsoleInput función)</span><span class="sxs-lookup"><span data-stu-id="0b54c-104">ReadConsoleInput function</span></span>

<span data-ttu-id="0b54c-105">Lee datos de un búfer de entrada de la consola y lo quita del búfer.</span><span class="sxs-lookup"><span data-stu-id="0b54c-105">Reads data from a console input buffer and removes it from the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="0b54c-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0b54c-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

## <a name="parameters"></a><span data-ttu-id="0b54c-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0b54c-107">Parameters</span></span>

<span data-ttu-id="0b54c-108">*hConsoleInput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="0b54c-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="0b54c-109">Identificador para el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="0b54c-109">A handle to the console input buffer.</span></span> <span data-ttu-id="0b54c-110">El identificador debe tener derecho de acceso de **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="0b54c-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="0b54c-111">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="0b54c-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="0b54c-112">*lpBuffer* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="0b54c-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="0b54c-113">Puntero a una matriz de estructuras [**de \_ registros de entrada**](input-record-str.md) que recibe los datos del búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="0b54c-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="0b54c-114">*nLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="0b54c-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="0b54c-115">Tamaño de la matriz a la que apunta el parámetro *lpBuffer* , en elementos de matriz.</span><span class="sxs-lookup"><span data-stu-id="0b54c-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="0b54c-116">*lpNumberOfEventsRead* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="0b54c-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="0b54c-117">Puntero a una variable que recibe el número de registros de entrada leídos.</span><span class="sxs-lookup"><span data-stu-id="0b54c-117">A pointer to a variable that receives the number of input records read.</span></span>

## <a name="return-value"></a><span data-ttu-id="0b54c-118">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0b54c-118">Return value</span></span>

<span data-ttu-id="0b54c-119">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="0b54c-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="0b54c-120">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="0b54c-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0b54c-121">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="0b54c-121">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="0b54c-122">Comentarios</span><span class="sxs-lookup"><span data-stu-id="0b54c-122">Remarks</span></span>

<span data-ttu-id="0b54c-123">Si el número de registros solicitados en el parámetro *nLength* supera el número de registros disponibles en el búfer, se lee el número disponible.</span><span class="sxs-lookup"><span data-stu-id="0b54c-123">If the number of records requested in the *nLength* parameter exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="0b54c-124">La función no devuelve ningún resultado hasta que se ha leído al menos un registro de entrada.</span><span class="sxs-lookup"><span data-stu-id="0b54c-124">The function does not return until at least one input record has been read.</span></span>

<span data-ttu-id="0b54c-125">Un proceso puede especificar un identificador de búfer de entrada de la consola en una de las [funciones de espera](/windows/win32/sync/wait-functions) para determinar si hay una entrada de consola sin leer.</span><span class="sxs-lookup"><span data-stu-id="0b54c-125">A process can specify a console input buffer handle in one of the [wait functions](/windows/win32/sync/wait-functions) to determine when there is unread console input.</span></span> <span data-ttu-id="0b54c-126">Cuando el búfer de entrada no está vacío, se señala el estado de un controlador de búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="0b54c-126">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="0b54c-127">Para determinar el número de registros de entrada no leídos en el búfer de entrada de la consola, use la función [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) .</span><span class="sxs-lookup"><span data-stu-id="0b54c-127">To determine the number of unread input records in a console's input buffer, use the [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) function.</span></span> <span data-ttu-id="0b54c-128">Para leer los registros de entrada desde un búfer de entrada de la consola sin afectar al número de registros no leídos, utilice la función [**PeekConsoleInput**](peekconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="0b54c-128">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="0b54c-129">Para descartar todos los registros no leídos en el búfer de entrada de la consola, use la función [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="0b54c-129">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## <a name="examples"></a><span data-ttu-id="0b54c-130">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="0b54c-130">Examples</span></span>

<span data-ttu-id="0b54c-131">Para un ejemplo, vea [Lectura de eventos de búfer de entrada](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="0b54c-131">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="0b54c-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0b54c-132">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="0b54c-133">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="0b54c-133">Minimum supported client</span></span> | <span data-ttu-id="0b54c-134">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="0b54c-134">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="0b54c-135">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="0b54c-135">Minimum supported server</span></span> | <span data-ttu-id="0b54c-136">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="0b54c-136">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="0b54c-137">Encabezado</span><span class="sxs-lookup"><span data-stu-id="0b54c-137">Header</span></span> | <span data-ttu-id="0b54c-138">ConsoleApi.h (a través de WinCon.h, incluido Windows.h)</span><span class="sxs-lookup"><span data-stu-id="0b54c-138">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="0b54c-139">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="0b54c-139">Library</span></span> | <span data-ttu-id="0b54c-140">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="0b54c-140">Kernel32.lib</span></span> |
| <span data-ttu-id="0b54c-141">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="0b54c-141">DLL</span></span> | <span data-ttu-id="0b54c-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0b54c-142">Kernel32.dll</span></span> |
| <span data-ttu-id="0b54c-143">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="0b54c-143">Unicode and ANSI names</span></span> | <span data-ttu-id="0b54c-144">**ReadConsoleInputW** (Unicode) y **ReadConsoleInputA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="0b54c-144">**ReadConsoleInputW** (Unicode) and **ReadConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="0b54c-145">Vea también</span><span class="sxs-lookup"><span data-stu-id="0b54c-145">See also</span></span>

[<span data-ttu-id="0b54c-146">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="0b54c-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0b54c-147">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="0b54c-147">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="0b54c-148">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="0b54c-148">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="0b54c-149">**registro de entrada \_**</span><span class="sxs-lookup"><span data-stu-id="0b54c-149">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="0b54c-150">Funciones de entrada de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="0b54c-150">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="0b54c-151">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="0b54c-151">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="0b54c-152">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="0b54c-152">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="0b54c-153">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="0b54c-153">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="0b54c-154">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="0b54c-154">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="0b54c-155">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="0b54c-155">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="0b54c-156">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="0b54c-156">**WriteConsoleInput**</span></span>](writeconsoleinput.md)