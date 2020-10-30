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
ms.openlocfilehash: bfc71c10a02e9ed8a0bc18fd26cffa855012c692
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037483"
---
# <a name="attachconsole-function"></a><span data-ttu-id="cca77-104">AttachConsole función)</span><span class="sxs-lookup"><span data-stu-id="cca77-104">AttachConsole function</span></span>

<span data-ttu-id="cca77-105">Asocia el proceso de llamada a la consola del proceso especificado como una aplicación cliente.</span><span class="sxs-lookup"><span data-stu-id="cca77-105">Attaches the calling process to the console of the specified process as a client application.</span></span>

## <a name="syntax"></a><span data-ttu-id="cca77-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="cca77-106">Syntax</span></span>

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

## <a name="parameters"></a><span data-ttu-id="cca77-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="cca77-107">Parameters</span></span>

<span data-ttu-id="cca77-108">*dwProcessId* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="cca77-108">*dwProcessId* \[in\]</span></span>  
<span data-ttu-id="cca77-109">Identificador del proceso cuya consola se va a usar.</span><span class="sxs-lookup"><span data-stu-id="cca77-109">The identifier of the process whose console is to be used.</span></span> <span data-ttu-id="cca77-110">Este parámetro puede ser uno de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="cca77-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="cca77-111">Valor</span><span class="sxs-lookup"><span data-stu-id="cca77-111">Value</span></span> | <span data-ttu-id="cca77-112">Significado</span><span class="sxs-lookup"><span data-stu-id="cca77-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="cca77-113">*pid*</span><span class="sxs-lookup"><span data-stu-id="cca77-113">*pid*</span></span> | <span data-ttu-id="cca77-114">Use la consola del proceso especificado.</span><span class="sxs-lookup"><span data-stu-id="cca77-114">Use the console of the specified process.</span></span> |
| <span data-ttu-id="cca77-115">**Asociar \_ \_proceso primario**`(DWORD)-1`</span><span class="sxs-lookup"><span data-stu-id="cca77-115">**ATTACH\_PARENT\_PROCESS** `(DWORD)-1`</span></span> | <span data-ttu-id="cca77-116">Use la consola del elemento primario del proceso actual.</span><span class="sxs-lookup"><span data-stu-id="cca77-116">Use the console of the parent of the current process.</span></span> |

## <a name="return-value"></a><span data-ttu-id="cca77-117">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="cca77-117">Return value</span></span>

<span data-ttu-id="cca77-118">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="cca77-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="cca77-119">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="cca77-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="cca77-120">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="cca77-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="cca77-121">Comentarios</span><span class="sxs-lookup"><span data-stu-id="cca77-121">Remarks</span></span>

<span data-ttu-id="cca77-122">Un proceso se puede adjuntar a como máximo una consola.</span><span class="sxs-lookup"><span data-stu-id="cca77-122">A process can be attached to at most one console.</span></span> <span data-ttu-id="cca77-123">Si el proceso de llamada ya está asociado a una consola de, el código de error devuelto es **error de \_ acceso \_ denegado** ( `5` ).</span><span class="sxs-lookup"><span data-stu-id="cca77-123">If the calling process is already attached to a console, the error code returned is **ERROR\_ACCESS\_DENIED** (`5`).</span></span> <span data-ttu-id="cca77-124">Si el proceso especificado no tiene una consola de, el código de error devuelto es un **error de \_ \_ identificador no válido** ( `6` ).</span><span class="sxs-lookup"><span data-stu-id="cca77-124">If the specified process does not have a console, the error code returned is **ERROR\_INVALID\_HANDLE** (`6`).</span></span> <span data-ttu-id="cca77-125">Si el proceso especificado no existe, el código de error devuelto es un **parámetro de error \_ no válido \_** ( `87` ).</span><span class="sxs-lookup"><span data-stu-id="cca77-125">If the specified process does not exist, the error code returned is **ERROR\_INVALID\_PARAMETER** (`87`).</span></span>

<span data-ttu-id="cca77-126">Un proceso puede usar la función [**FreeConsole**](freeconsole.md) para desasociarse de su consola.</span><span class="sxs-lookup"><span data-stu-id="cca77-126">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console.</span></span> <span data-ttu-id="cca77-127">Si otros procesos comparten la consola, la consola no se destruye, pero el proceso que llamó a **FreeConsole** no puede hacer referencia a ella.</span><span class="sxs-lookup"><span data-stu-id="cca77-127">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="cca77-128">Una consola se cierra cuando el último proceso asociado a ella finaliza o llama a **FreeConsole** .</span><span class="sxs-lookup"><span data-stu-id="cca77-128">A console is closed when the last process attached to it terminates or calls **FreeConsole** .</span></span> <span data-ttu-id="cca77-129">Una vez que un proceso llama a **FreeConsole** , puede llamar a la función [**AllocConsole**](allocconsole.md) para crear una nueva consola o **AttachConsole** para asociar a otra consola.</span><span class="sxs-lookup"><span data-stu-id="cca77-129">After a process calls **FreeConsole** , it can call the [**AllocConsole**](allocconsole.md) function to create a new console or **AttachConsole** to attach to another console.</span></span>

<span data-ttu-id="cca77-130">Esta función es principalmente útil para las aplicaciones que se vincularon con [**/Subsystem: Windows**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem), que implica al sistema operativo que no se necesita una consola antes de entrar en el método Main del programa.</span><span class="sxs-lookup"><span data-stu-id="cca77-130">This function is primarily useful to applications that were linked with [**/SUBSYSTEM:WINDOWS**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem), which implies to the operating system that a console is not needed before entering the program's main method.</span></span> <span data-ttu-id="cca77-131">En esa instancia, es probable que los identificadores estándar recuperados con [**GetStdHandle**](getstdhandle.md) no sean válidos en el inicio hasta que se llame a **AttachConsole** .</span><span class="sxs-lookup"><span data-stu-id="cca77-131">In that instance, the standard handles retrieved with [**GetStdHandle**](getstdhandle.md) will likely be invalid on startup until **AttachConsole** is called.</span></span> <span data-ttu-id="cca77-132">La excepción a esto es si la aplicación se inicia con la herencia de identificadores por su proceso primario.</span><span class="sxs-lookup"><span data-stu-id="cca77-132">The exception to this is if the application is launched with handle inheritance by its parent process.</span></span>

<span data-ttu-id="cca77-133">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como `0x0501` o posterior.</span><span class="sxs-lookup"><span data-stu-id="cca77-133">To compile an application that uses this function, define **\_WIN32\_WINNT** as `0x0501` or later.</span></span> <span data-ttu-id="cca77-134">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="cca77-134">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

## <a name="requirements"></a><span data-ttu-id="cca77-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cca77-135">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="cca77-136">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="cca77-136">Minimum supported client</span></span> | <span data-ttu-id="cca77-137">Solo aplicaciones de escritorio de Windows XP \[\]</span><span class="sxs-lookup"><span data-stu-id="cca77-137">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="cca77-138">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="cca77-138">Minimum supported server</span></span> | <span data-ttu-id="cca77-139">Solo aplicaciones de escritorio de Windows Server 2003 \[\]</span><span class="sxs-lookup"><span data-stu-id="cca77-139">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="cca77-140">Encabezado</span><span class="sxs-lookup"><span data-stu-id="cca77-140">Header</span></span> | <span data-ttu-id="cca77-141">ConsoleApi. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="cca77-141">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="cca77-142">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="cca77-142">Library</span></span> | <span data-ttu-id="cca77-143">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="cca77-143">Kernel32.lib</span></span> |
| <span data-ttu-id="cca77-144">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="cca77-144">DLL</span></span> | <span data-ttu-id="cca77-145">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="cca77-145">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="cca77-146">Consulte también</span><span class="sxs-lookup"><span data-stu-id="cca77-146">See also</span></span>

[<span data-ttu-id="cca77-147">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="cca77-147">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="cca77-148">Consolas</span><span class="sxs-lookup"><span data-stu-id="cca77-148">Consoles</span></span>](consoles.md)

[<span data-ttu-id="cca77-149">**AllocConsole**</span><span class="sxs-lookup"><span data-stu-id="cca77-149">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="cca77-150">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="cca77-150">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="cca77-151">**GetConsoleProcessList**</span><span class="sxs-lookup"><span data-stu-id="cca77-151">**GetConsoleProcessList**</span></span>](getconsoleprocesslist.md)
