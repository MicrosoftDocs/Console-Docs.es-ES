---
title: GenerateConsoleCtrlEvent función)
description: Envía una señal especificada a un grupo de procesos de consola que comparte la consola asociada al proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/GenerateConsoleCtrlEvent
- wincon/GenerateConsoleCtrlEvent
- GenerateConsoleCtrlEvent
MS-HAID:
- '\_win32\_generateconsolectrlevent'
- base.generateconsolectrlevent
- consoles.generateconsolectrlevent
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ed392d97-6fd0-4256-a783-bc7d27d01a10
topic_type:
- apiref
api_name:
- GenerateConsoleCtrlEvent
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4002ec67000edda38c7b14476528a0167e521bbf
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357535"
---
# <a name="generateconsolectrlevent-function"></a><span data-ttu-id="78467-104">GenerateConsoleCtrlEvent función)</span><span class="sxs-lookup"><span data-stu-id="78467-104">GenerateConsoleCtrlEvent function</span></span>

<span data-ttu-id="78467-105">Envía una señal especificada a un grupo de procesos de consola que comparte la consola asociada al proceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="78467-105">Sends a specified signal to a console process group that shares the console associated with the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="78467-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="78467-106">Syntax</span></span>

```C
BOOL WINAPI GenerateConsoleCtrlEvent(
  _In_ DWORD dwCtrlEvent,
  _In_ DWORD dwProcessGroupId
);
```

## <a name="parameters"></a><span data-ttu-id="78467-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="78467-107">Parameters</span></span>

<span data-ttu-id="78467-108">*dwCtrlEvent* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="78467-108">*dwCtrlEvent* \[in\]</span></span>  
<span data-ttu-id="78467-109">Tipo de señal que se va a generar.</span><span class="sxs-lookup"><span data-stu-id="78467-109">The type of signal to be generated.</span></span> <span data-ttu-id="78467-110">Este parámetro puede ser uno de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="78467-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="78467-111">Valor</span><span class="sxs-lookup"><span data-stu-id="78467-111">Value</span></span> | <span data-ttu-id="78467-112">Significado</span><span class="sxs-lookup"><span data-stu-id="78467-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="78467-113">**CTRL_C_EVENT** 0</span><span class="sxs-lookup"><span data-stu-id="78467-113">**CTRL_C_EVENT** 0</span></span> | <span data-ttu-id="78467-114">Genera una señal CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="78467-114">Generates a CTRL+C signal.</span></span> <span data-ttu-id="78467-115">Esta señal no se puede generar para grupos de procesos.</span><span class="sxs-lookup"><span data-stu-id="78467-115">This signal cannot be generated for process groups.</span></span> <span data-ttu-id="78467-116">Si *dwProcessGroupId* es distinto de cero, esta función se realizará correctamente, pero los procesos del grupo de procesos especificado no recibirán la señal CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="78467-116">If *dwProcessGroupId* is nonzero, this function will succeed, but the CTRL+C signal will not be received by processes within the specified process group.</span></span> |
| <span data-ttu-id="78467-117">**CTRL_BREAK_EVENT** 1</span><span class="sxs-lookup"><span data-stu-id="78467-117">**CTRL_BREAK_EVENT** 1</span></span> | <span data-ttu-id="78467-118">Genera una señal CTRL + INTER.</span><span class="sxs-lookup"><span data-stu-id="78467-118">Generates a CTRL+BREAK signal.</span></span> |

<span data-ttu-id="78467-119">*dwProcessGroupId* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="78467-119">*dwProcessGroupId* \[in\]</span></span>  
<span data-ttu-id="78467-120">Identificador del grupo de procesos que va a recibir la señal.</span><span class="sxs-lookup"><span data-stu-id="78467-120">The identifier of the process group to receive the signal.</span></span> <span data-ttu-id="78467-121">Un grupo de procesos se crea cuando se especifica la marca **crear \_ nuevo \_ \_ grupo de procesos** en una llamada a la función [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) .</span><span class="sxs-lookup"><span data-stu-id="78467-121">A process group is created when the **CREATE\_NEW\_PROCESS\_GROUP** flag is specified in a call to the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) function.</span></span> <span data-ttu-id="78467-122">El identificador de proceso del nuevo proceso también es el identificador del grupo de procesos de un nuevo grupo de procesos.</span><span class="sxs-lookup"><span data-stu-id="78467-122">The process identifier of the new process is also the process group identifier of a new process group.</span></span> <span data-ttu-id="78467-123">El grupo de procesos incluye todos los procesos que son descendientes del proceso raíz.</span><span class="sxs-lookup"><span data-stu-id="78467-123">The process group includes all processes that are descendants of the root process.</span></span> <span data-ttu-id="78467-124">Solo los procesos del grupo que comparten la misma consola que el proceso de llamada reciben la señal.</span><span class="sxs-lookup"><span data-stu-id="78467-124">Only those processes in the group that share the same console as the calling process receive the signal.</span></span> <span data-ttu-id="78467-125">En otras palabras, si un proceso del grupo crea una nueva consola, ese proceso no recibe la señal ni sus descendientes.</span><span class="sxs-lookup"><span data-stu-id="78467-125">In other words, if a process in the group creates a new console, that process does not receive the signal, nor do its descendants.</span></span>

<span data-ttu-id="78467-126">Si este parámetro es cero, la señal se genera en todos los procesos que comparten la consola del proceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="78467-126">If this parameter is zero, the signal is generated in all processes that share the console of the calling process.</span></span>

## <a name="return-value"></a><span data-ttu-id="78467-127">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="78467-127">Return value</span></span>

<span data-ttu-id="78467-128">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="78467-128">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="78467-129">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="78467-129">If the function fails, the return value is zero.</span></span> <span data-ttu-id="78467-130">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="78467-130">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="78467-131">Comentarios</span><span class="sxs-lookup"><span data-stu-id="78467-131">Remarks</span></span>

<span data-ttu-id="78467-132">**GenerateConsoleCtrlEvent** hace que se llame a las funciones de controlador de control de los procesos del grupo de destino.</span><span class="sxs-lookup"><span data-stu-id="78467-132">**GenerateConsoleCtrlEvent** causes the control handler functions of processes in the target group to be called.</span></span> <span data-ttu-id="78467-133">Todos los procesos de la consola tienen una función de controlador predeterminada que llama a la función [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) .</span><span class="sxs-lookup"><span data-stu-id="78467-133">All console processes have a default handler function that calls the [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) function.</span></span> <span data-ttu-id="78467-134">Un proceso de consola puede usar la función [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) para instalar o quitar otras funciones de controlador.</span><span class="sxs-lookup"><span data-stu-id="78467-134">A console process can use the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function to install or remove other handler functions.</span></span>

<span data-ttu-id="78467-135">[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) también puede habilitar un atributo heredable que hace que el proceso de llamada ignore las señales Ctrl + C.</span><span class="sxs-lookup"><span data-stu-id="78467-135">[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) can also enable an inheritable attribute that causes the calling process to ignore CTRL+C signals.</span></span> <span data-ttu-id="78467-136">Si **GenerateConsoleCtrlEvent** envía una señal CTRL + C a un proceso para el que este atributo está habilitado, no se llama a las funciones de controlador para ese proceso.</span><span class="sxs-lookup"><span data-stu-id="78467-136">If **GenerateConsoleCtrlEvent** sends a CTRL+C signal to a process for which this attribute is enabled, the handler functions for that process are not called.</span></span> <span data-ttu-id="78467-137">CTRL + INTERRUMPIr señales siempre hace que se llame a las funciones de controlador.</span><span class="sxs-lookup"><span data-stu-id="78467-137">CTRL+BREAK signals always cause the handler functions to be called.</span></span>

## <a name="requirements"></a><span data-ttu-id="78467-138">Requisitos</span><span class="sxs-lookup"><span data-stu-id="78467-138">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="78467-139">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="78467-139">Minimum supported client</span></span> | <span data-ttu-id="78467-140">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="78467-140">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="78467-141">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="78467-141">Minimum supported server</span></span> | <span data-ttu-id="78467-142">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="78467-142">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="78467-143">Encabezado</span><span class="sxs-lookup"><span data-stu-id="78467-143">Header</span></span> | <span data-ttu-id="78467-144">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="78467-144">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="78467-145">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="78467-145">Library</span></span> | <span data-ttu-id="78467-146">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="78467-146">Kernel32.lib</span></span> |
| <span data-ttu-id="78467-147">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="78467-147">DLL</span></span> | <span data-ttu-id="78467-148">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="78467-148">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="78467-149">Vea también</span><span class="sxs-lookup"><span data-stu-id="78467-149">See also</span></span>

[<span data-ttu-id="78467-150">Identificadores de control de la consola</span><span class="sxs-lookup"><span data-stu-id="78467-150">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="78467-151">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="78467-151">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="78467-152">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="78467-152">**CreateProcess**</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)

[<span data-ttu-id="78467-153">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="78467-153">**ExitProcess**</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess)

[<span data-ttu-id="78467-154">**SetConsoleCtrlHandler**</span><span class="sxs-lookup"><span data-stu-id="78467-154">**SetConsoleCtrlHandler**</span></span>](setconsolectrlhandler.md)