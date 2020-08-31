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
ms.openlocfilehash: 784bed6c1a7b7f7ed9ed204b8483d30371e510a3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061124"
---
# <a name="writeconsoleinput-function"></a><span data-ttu-id="be480-104">WriteConsoleInput función)</span><span class="sxs-lookup"><span data-stu-id="be480-104">WriteConsoleInput function</span></span>


<span data-ttu-id="be480-105">Escribe los datos directamente en el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="be480-105">Writes data directly to the console input buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="be480-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="be480-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

<a name="parameters"></a><span data-ttu-id="be480-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="be480-107">Parameters</span></span>
----------

<span data-ttu-id="be480-108">*hConsoleInput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="be480-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="be480-109">Identificador para el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="be480-109">A handle to the console input buffer.</span></span> <span data-ttu-id="be480-110">El identificador debe tener el derecho de acceso de \*\* \_ escritura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="be480-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="be480-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="be480-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="be480-112">*lpBuffer* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="be480-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="be480-113">Puntero a una matriz de estructuras [**de \_ registros de entrada**](input-record-str.md) que contienen datos que se van a escribir en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="be480-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that contain data to be written to the input buffer.</span></span>

<span data-ttu-id="be480-114">*nLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="be480-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="be480-115">El número de registros de entrada que se van a escribir.</span><span class="sxs-lookup"><span data-stu-id="be480-115">The number of input records to be written.</span></span>

<span data-ttu-id="be480-116">*lpNumberOfEventsWritten* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="be480-116">*lpNumberOfEventsWritten* \[out\]</span></span>  
<span data-ttu-id="be480-117">Puntero a una variable que recibe el número de registros de entrada escritos realmente.</span><span class="sxs-lookup"><span data-stu-id="be480-117">A pointer to a variable that receives the number of input records actually written.</span></span>

<a name="return-value"></a><span data-ttu-id="be480-118">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="be480-118">Return value</span></span>
------------

<span data-ttu-id="be480-119">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="be480-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="be480-120">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="be480-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="be480-121">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="be480-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="be480-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="be480-122">Remarks</span></span>
-------

<span data-ttu-id="be480-123">**WriteConsoleInput** coloca los registros de entrada en el búfer de entrada detrás de los eventos pendientes en el búfer.</span><span class="sxs-lookup"><span data-stu-id="be480-123">**WriteConsoleInput** places input records into the input buffer behind any pending events in the buffer.</span></span> <span data-ttu-id="be480-124">El búfer de entrada crece dinámicamente, si es necesario, para contener tantos eventos como se escriban.</span><span class="sxs-lookup"><span data-stu-id="be480-124">The input buffer grows dynamically, if necessary, to hold as many events as are written.</span></span>

<span data-ttu-id="be480-125">Esta función usa caracteres Unicode o caracteres de 8 bits de la página de códigos actual de la consola.</span><span class="sxs-lookup"><span data-stu-id="be480-125">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="be480-126">La página de códigos de la consola tiene como valor predeterminado la página de códigos OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="be480-126">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="be480-127">Para cambiar la página de códigos de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) , o bien use los comandos **chcp** o **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="be480-127">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="be480-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="be480-128">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="be480-129">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="be480-129">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="be480-130">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="be480-130">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="be480-131">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="be480-131">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="be480-132">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="be480-132">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="be480-133">Encabezado</span><span class="sxs-lookup"><span data-stu-id="be480-133">Header</span></span></p></td>
<td><span data-ttu-id="be480-134">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="be480-134">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="be480-135">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="be480-135">Library</span></span></p></td>
<td><span data-ttu-id="be480-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="be480-136">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="be480-137">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="be480-137">DLL</span></span></p></td>
<td><span data-ttu-id="be480-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="be480-138">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="be480-139">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="be480-139">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="be480-140"><strong>WriteConsoleInputW</strong> (Unicode) y <strong>WriteConsoleInputA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="be480-140"><strong>WriteConsoleInputW</strong> (Unicode) and <strong>WriteConsoleInputA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="be480-141"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="be480-141"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="be480-142">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="be480-142">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="be480-143">**registro de entrada \_**</span><span class="sxs-lookup"><span data-stu-id="be480-143">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="be480-144">Funciones de entrada de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="be480-144">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="be480-145">**MapVirtualKey**</span><span class="sxs-lookup"><span data-stu-id="be480-145">**MapVirtualKey**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646306)

[<span data-ttu-id="be480-146">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="be480-146">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="be480-147">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="be480-147">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="be480-148">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="be480-148">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="be480-149">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="be480-149">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="be480-150">**VkKeyScan**</span><span class="sxs-lookup"><span data-stu-id="be480-150">**VkKeyScan**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646329)

 

 




