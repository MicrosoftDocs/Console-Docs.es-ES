---
title: AttachConsole función)
description: Vea la información de referencia sobre la función AttachConsole, que asocia el proceso de llamada a la consola del proceso especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- base.attachconsole
- consoles.attachconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: a1be050dccc0c77b6ad448cc45e87906a115d82c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357845"
---
# <a name="attachconsole-function"></a><span data-ttu-id="355a4-104">AttachConsole función)</span><span class="sxs-lookup"><span data-stu-id="355a4-104">AttachConsole function</span></span>

<span data-ttu-id="355a4-105">Asocia el proceso de llamada a la consola del proceso especificado como una aplicación cliente.</span><span class="sxs-lookup"><span data-stu-id="355a4-105">Attaches the calling process to the console of the specified process as a client application.</span></span>

## <a name="syntax"></a><span data-ttu-id="355a4-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="355a4-106">Syntax</span></span>

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

## <a name="parameters"></a><span data-ttu-id="355a4-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="355a4-107">Parameters</span></span>

<span data-ttu-id="355a4-108">*dwProcessId* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="355a4-108">*dwProcessId* \[in\]</span></span>  
<span data-ttu-id="355a4-109">Identificador del proceso cuya consola se va a usar.</span><span class="sxs-lookup"><span data-stu-id="355a4-109">The identifier of the process whose console is to be used.</span></span> <span data-ttu-id="355a4-110">Este parámetro puede ser uno de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="355a4-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="355a4-111">Valor</span><span class="sxs-lookup"><span data-stu-id="355a4-111">Value</span></span> | <span data-ttu-id="355a4-112">Significado</span><span class="sxs-lookup"><span data-stu-id="355a4-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="355a4-113">*pid*</span><span class="sxs-lookup"><span data-stu-id="355a4-113">*pid*</span></span> | <span data-ttu-id="355a4-114">Use la consola del proceso especificado.</span><span class="sxs-lookup"><span data-stu-id="355a4-114">Use the console of the specified process.</span></span> |
| <span data-ttu-id="355a4-115">**Asociar \_ \_proceso primario**`(DWORD)-1`</span><span class="sxs-lookup"><span data-stu-id="355a4-115">**ATTACH\_PARENT\_PROCESS** `(DWORD)-1`</span></span> | <span data-ttu-id="355a4-116">Use la consola del elemento primario del proceso actual.</span><span class="sxs-lookup"><span data-stu-id="355a4-116">Use the console of the parent of the current process.</span></span> |

## <a name="return-value"></a><span data-ttu-id="355a4-117">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="355a4-117">Return value</span></span>

<span data-ttu-id="355a4-118">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="355a4-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="355a4-119">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="355a4-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="355a4-120">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="355a4-120">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="355a4-121">Comentarios</span><span class="sxs-lookup"><span data-stu-id="355a4-121">Remarks</span></span>

<span data-ttu-id="355a4-122">Un proceso se puede adjuntar a como máximo una consola.</span><span class="sxs-lookup"><span data-stu-id="355a4-122">A process can be attached to at most one console.</span></span> <span data-ttu-id="355a4-123">Si el proceso de llamada ya está asociado a una consola de, el código de error devuelto es **error de \_ acceso \_ denegado** ( `5` ).</span><span class="sxs-lookup"><span data-stu-id="355a4-123">If the calling process is already attached to a console, the error code returned is **ERROR\_ACCESS\_DENIED** (`5`).</span></span> <span data-ttu-id="355a4-124">Si el proceso especificado no tiene una consola de, el código de error devuelto es un **error de \_ \_ identificador no válido** ( `6` ).</span><span class="sxs-lookup"><span data-stu-id="355a4-124">If the specified process does not have a console, the error code returned is **ERROR\_INVALID\_HANDLE** (`6`).</span></span> <span data-ttu-id="355a4-125">Si el proceso especificado no existe, el código de error devuelto es un **parámetro de error \_ no válido \_** ( `87` ).</span><span class="sxs-lookup"><span data-stu-id="355a4-125">If the specified process does not exist, the error code returned is **ERROR\_INVALID\_PARAMETER** (`87`).</span></span>

<span data-ttu-id="355a4-126">Un proceso puede usar la función [**FreeConsole**](freeconsole.md) para desasociarse de su consola.</span><span class="sxs-lookup"><span data-stu-id="355a4-126">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console.</span></span> <span data-ttu-id="355a4-127">Si otros procesos comparten la consola, la consola no se destruye, pero el proceso que llamó a **FreeConsole** no puede hacer referencia a ella.</span><span class="sxs-lookup"><span data-stu-id="355a4-127">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="355a4-128">Una consola se cierra cuando el último proceso asociado a ella finaliza o llama a **FreeConsole**.</span><span class="sxs-lookup"><span data-stu-id="355a4-128">A console is closed when the last process attached to it terminates or calls **FreeConsole**.</span></span> <span data-ttu-id="355a4-129">Una vez que un proceso llama a **FreeConsole**, puede llamar a la función [**AllocConsole**](allocconsole.md) para crear una nueva consola o **AttachConsole** para asociar a otra consola.</span><span class="sxs-lookup"><span data-stu-id="355a4-129">After a process calls **FreeConsole**, it can call the [**AllocConsole**](allocconsole.md) function to create a new console or **AttachConsole** to attach to another console.</span></span>

<span data-ttu-id="355a4-130">Esta función es principalmente útil para las aplicaciones que se vincularon con [**/Subsystem: Windows**](/cpp/build/reference/subsystem-specify-subsystem), que implica al sistema operativo que no se necesita una consola antes de entrar en el método Main del programa.</span><span class="sxs-lookup"><span data-stu-id="355a4-130">This function is primarily useful to applications that were linked with [**/SUBSYSTEM:WINDOWS**](/cpp/build/reference/subsystem-specify-subsystem), which implies to the operating system that a console is not needed before entering the program's main method.</span></span> <span data-ttu-id="355a4-131">En esa instancia, es probable que los identificadores estándar recuperados con [**GetStdHandle**](getstdhandle.md) no sean válidos en el inicio hasta que se llame a **AttachConsole** .</span><span class="sxs-lookup"><span data-stu-id="355a4-131">In that instance, the standard handles retrieved with [**GetStdHandle**](getstdhandle.md) will likely be invalid on startup until **AttachConsole** is called.</span></span> <span data-ttu-id="355a4-132">La excepción a esto es si la aplicación se inicia con la herencia de identificadores por su proceso primario.</span><span class="sxs-lookup"><span data-stu-id="355a4-132">The exception to this is if the application is launched with handle inheritance by its parent process.</span></span>

<span data-ttu-id="355a4-133">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como `0x0501` o posterior.</span><span class="sxs-lookup"><span data-stu-id="355a4-133">To compile an application that uses this function, define **\_WIN32\_WINNT** as `0x0501` or later.</span></span> <span data-ttu-id="355a4-134">Para obtener más información, consulte [uso de los encabezados de Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="355a4-134">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

## <a name="requirements"></a><span data-ttu-id="355a4-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="355a4-135">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="355a4-136">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="355a4-136">Minimum supported client</span></span> | <span data-ttu-id="355a4-137">Solo aplicaciones de escritorio de Windows XP \[\]</span><span class="sxs-lookup"><span data-stu-id="355a4-137">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="355a4-138">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="355a4-138">Minimum supported server</span></span> | <span data-ttu-id="355a4-139">Solo aplicaciones de escritorio de Windows Server 2003 \[\]</span><span class="sxs-lookup"><span data-stu-id="355a4-139">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="355a4-140">Encabezado</span><span class="sxs-lookup"><span data-stu-id="355a4-140">Header</span></span> | <span data-ttu-id="355a4-141">ConsoleApi.h (a través de WinCon.h, incluido Windows.h)</span><span class="sxs-lookup"><span data-stu-id="355a4-141">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="355a4-142">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="355a4-142">Library</span></span> | <span data-ttu-id="355a4-143">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="355a4-143">Kernel32.lib</span></span> |
| <span data-ttu-id="355a4-144">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="355a4-144">DLL</span></span> | <span data-ttu-id="355a4-145">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="355a4-145">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="355a4-146">Vea también</span><span class="sxs-lookup"><span data-stu-id="355a4-146">See also</span></span>

[<span data-ttu-id="355a4-147">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="355a4-147">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="355a4-148">Consolas</span><span class="sxs-lookup"><span data-stu-id="355a4-148">Consoles</span></span>](consoles.md)

[<span data-ttu-id="355a4-149">**AllocConsole**</span><span class="sxs-lookup"><span data-stu-id="355a4-149">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="355a4-150">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="355a4-150">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="355a4-151">**GetConsoleProcessList**</span><span class="sxs-lookup"><span data-stu-id="355a4-151">**GetConsoleProcessList**</span></span>](getconsoleprocesslist.md)