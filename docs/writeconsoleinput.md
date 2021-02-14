---
title: WriteConsoleInput función)
description: Consulte la información de referencia sobre la función WriteConsoleInput, que escribe datos directamente en el búfer de entrada de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/WriteConsoleInput
- wincon/WriteConsoleInput
- WriteConsoleInput
- consoleapi2/WriteConsoleInputA
- wincon/WriteConsoleInputA
- WriteConsoleInputA
- consoleapi2/WriteConsoleInputW
- wincon/WriteConsoleInputW
- WriteConsoleInputW
MS-HAID:
- '\_win32\_writeconsoleinput'
- base.writeconsoleinput
- consoles.writeconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad06231f-5063-4aff-b14d-8df5e6e42430
topic_type:
- apiref
api_name:
- WriteConsoleInput
- WriteConsoleInputA
- WriteConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e4b9cdae52da2e23ff93e1904c4cb24ebac62831
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357785"
---
# <a name="writeconsoleinput-function"></a><span data-ttu-id="92d55-104">WriteConsoleInput función)</span><span class="sxs-lookup"><span data-stu-id="92d55-104">WriteConsoleInput function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="92d55-105">Escribe los datos directamente en el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="92d55-105">Writes data directly to the console input buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="92d55-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="92d55-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="92d55-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="92d55-107">Parameters</span></span>

<span data-ttu-id="92d55-108">*hConsoleInput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="92d55-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="92d55-109">Identificador para el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="92d55-109">A handle to the console input buffer.</span></span> <span data-ttu-id="92d55-110">El identificador debe tener derecho de acceso de **GENERIC\_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="92d55-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="92d55-111">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="92d55-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="92d55-112">*lpBuffer* \[in\]</span><span class="sxs-lookup"><span data-stu-id="92d55-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="92d55-113">Puntero a una matriz de estructuras [**de \_ registros de entrada**](input-record-str.md) que contienen datos que se van a escribir en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="92d55-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that contain data to be written to the input buffer.</span></span>

<span data-ttu-id="92d55-114">*nLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="92d55-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="92d55-115">El número de registros de entrada que se van a escribir.</span><span class="sxs-lookup"><span data-stu-id="92d55-115">The number of input records to be written.</span></span>

<span data-ttu-id="92d55-116">*lpNumberOfEventsWritten* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="92d55-116">*lpNumberOfEventsWritten* \[out\]</span></span>  
<span data-ttu-id="92d55-117">Puntero a una variable que recibe el número de registros de entrada escritos realmente.</span><span class="sxs-lookup"><span data-stu-id="92d55-117">A pointer to a variable that receives the number of input records actually written.</span></span>

## <a name="return-value"></a><span data-ttu-id="92d55-118">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="92d55-118">Return value</span></span>

<span data-ttu-id="92d55-119">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="92d55-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="92d55-120">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="92d55-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="92d55-121">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="92d55-121">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="92d55-122">Comentarios</span><span class="sxs-lookup"><span data-stu-id="92d55-122">Remarks</span></span>

<span data-ttu-id="92d55-123">**WriteConsoleInput** coloca los registros de entrada en el búfer de entrada detrás de los eventos pendientes en el búfer.</span><span class="sxs-lookup"><span data-stu-id="92d55-123">**WriteConsoleInput** places input records into the input buffer behind any pending events in the buffer.</span></span> <span data-ttu-id="92d55-124">El búfer de entrada crece dinámicamente, si es necesario, para contener tantos eventos como se escriban.</span><span class="sxs-lookup"><span data-stu-id="92d55-124">The input buffer grows dynamically, if necessary, to hold as many events as are written.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="92d55-125">No se recomienda esta API y no tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente.</span><span class="sxs-lookup"><span data-stu-id="92d55-125">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="92d55-126">Esta decisión alinea intencionadamente la plataforma de Windows con otros sistemas operativos.</span><span class="sxs-lookup"><span data-stu-id="92d55-126">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="92d55-127">Esta operación se considera el **[verbo equivocado](console-buffer-security-and-access-rights.md#wrong-way-verbs)** para este búfer.</span><span class="sxs-lookup"><span data-stu-id="92d55-127">This operation is considered the **[wrong-way verb](console-buffer-security-and-access-rights.md#wrong-way-verbs)** for this buffer.</span></span> <span data-ttu-id="92d55-128">Es posible que las aplicaciones remotas mediante utilidades y transportes multiplataforma como SSH no funcionen según lo esperado si se usa esta API.</span><span class="sxs-lookup"><span data-stu-id="92d55-128">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="92d55-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92d55-129">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="92d55-130">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="92d55-130">Minimum supported client</span></span> | <span data-ttu-id="92d55-131">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="92d55-131">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="92d55-132">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="92d55-132">Minimum supported server</span></span> | <span data-ttu-id="92d55-133">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="92d55-133">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="92d55-134">Encabezado</span><span class="sxs-lookup"><span data-stu-id="92d55-134">Header</span></span> | <span data-ttu-id="92d55-135">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="92d55-135">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="92d55-136">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="92d55-136">Library</span></span> | <span data-ttu-id="92d55-137">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="92d55-137">Kernel32.lib</span></span> |
| <span data-ttu-id="92d55-138">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="92d55-138">DLL</span></span> | <span data-ttu-id="92d55-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="92d55-139">Kernel32.dll</span></span> |
| <span data-ttu-id="92d55-140">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="92d55-140">Unicode and ANSI names</span></span> | <span data-ttu-id="92d55-141">**WriteConsoleInputW** (Unicode) y **WriteConsoleInputA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="92d55-141">**WriteConsoleInputW** (Unicode) and **WriteConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="92d55-142">Vea también</span><span class="sxs-lookup"><span data-stu-id="92d55-142">See also</span></span>

[<span data-ttu-id="92d55-143">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="92d55-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="92d55-144">**registro de entrada \_**</span><span class="sxs-lookup"><span data-stu-id="92d55-144">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="92d55-145">Funciones de entrada de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="92d55-145">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="92d55-146">**MapVirtualKey**</span><span class="sxs-lookup"><span data-stu-id="92d55-146">**MapVirtualKey**</span></span>](/windows/win32/api/winuser/nf-winuser-mapvirtualkeya)

[<span data-ttu-id="92d55-147">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="92d55-147">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="92d55-148">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="92d55-148">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="92d55-149">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="92d55-149">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="92d55-150">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="92d55-150">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="92d55-151">**VkKeyScan**</span><span class="sxs-lookup"><span data-stu-id="92d55-151">**VkKeyScan**</span></span>](/windows/win32/api/winuser/nf-winuser-vkkeyscana)