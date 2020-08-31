---
title: GetNumberOfConsoleMouseButtons función)
description: Recupera el número de botones del mouse que usa la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetNumberOfConsoleMouseButtons
- wincon/GetNumberOfConsoleMouseButtons
- GetNumberOfConsoleMouseButtons
MS-HAID:
- '\_win32\_getnumberofconsolemousebuttons'
- base.getnumberofconsolemousebuttons
- consoles.getnumberofconsolemousebuttons
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2
topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 67089bd301ac2632f9a99ca24cc2042789f6a3e8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061028"
---
# <a name="getnumberofconsolemousebuttons-function"></a><span data-ttu-id="0a1e4-104">GetNumberOfConsoleMouseButtons función)</span><span class="sxs-lookup"><span data-stu-id="0a1e4-104">GetNumberOfConsoleMouseButtons function</span></span>


<span data-ttu-id="0a1e4-105">Recupera el número de botones del mouse que usa la consola actual.</span><span class="sxs-lookup"><span data-stu-id="0a1e4-105">Retrieves the number of buttons on the mouse used by the current console.</span></span>

<a name="syntax"></a><span data-ttu-id="0a1e4-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0a1e4-106">Syntax</span></span>
------

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

<a name="parameters"></a><span data-ttu-id="0a1e4-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0a1e4-107">Parameters</span></span>
----------

<span data-ttu-id="0a1e4-108">*lpNumberOfMouseButtons* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="0a1e4-108">*lpNumberOfMouseButtons* \[out\]</span></span>  
<span data-ttu-id="0a1e4-109">Puntero a una variable que recibe el número de botones del mouse.</span><span class="sxs-lookup"><span data-stu-id="0a1e4-109">A pointer to a variable that receives the number of mouse buttons.</span></span>

<a name="return-value"></a><span data-ttu-id="0a1e4-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0a1e4-110">Return value</span></span>
------------

<span data-ttu-id="0a1e4-111">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="0a1e4-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="0a1e4-112">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="0a1e4-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0a1e4-113">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="0a1e4-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="0a1e4-114">Observaciones</span><span class="sxs-lookup"><span data-stu-id="0a1e4-114">Remarks</span></span>
-------

<span data-ttu-id="0a1e4-115">Cuando una consola recibe la entrada del mouse, una estructura de [\*\* \_ registro de entrada\*\*](input-record-str.md) que contiene una estructura de [\*\* \_ \_ registro de eventos del mouse\*\*](mouse-event-record-str.md) se coloca en el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="0a1e4-115">When a console receives mouse input, an [**INPUT\_RECORD**](input-record-str.md) structure containing a [**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md) structure is placed in the console's input buffer.</span></span> <span data-ttu-id="0a1e4-116">El miembro **dwButtonState** del \*\* \_ \_ registro de eventos del mouse\*\* tiene un bit que indica el estado de cada botón del mouse.</span><span class="sxs-lookup"><span data-stu-id="0a1e4-116">The **dwButtonState** member of **MOUSE\_EVENT\_RECORD** has a bit indicating the state of each mouse button.</span></span> <span data-ttu-id="0a1e4-117">El bit es 1 si el botón está presionado y 0 si el botón está activo.</span><span class="sxs-lookup"><span data-stu-id="0a1e4-117">The bit is 1 if the button is down and 0 if the button is up.</span></span> <span data-ttu-id="0a1e4-118">Para determinar el número de bits que son significativos, use **GetNumberOfConsoleMouseButtons**.</span><span class="sxs-lookup"><span data-stu-id="0a1e4-118">To determine the number of bits that are significant, use **GetNumberOfConsoleMouseButtons**.</span></span>

<a name="requirements"></a><span data-ttu-id="0a1e4-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0a1e4-119">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="0a1e4-120">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="0a1e4-120">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="0a1e4-121">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="0a1e4-121">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0a1e4-122">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="0a1e4-122">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="0a1e4-123">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="0a1e4-123">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0a1e4-124">Encabezado</span><span class="sxs-lookup"><span data-stu-id="0a1e4-124">Header</span></span></p></td>
<td><span data-ttu-id="0a1e4-125">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0a1e4-125">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0a1e4-126">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="0a1e4-126">Library</span></span></p></td>
<td><span data-ttu-id="0a1e4-127">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="0a1e4-127">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0a1e4-128">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="0a1e4-128">DLL</span></span></p></td>
<td><span data-ttu-id="0a1e4-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0a1e4-129">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="0a1e4-130"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="0a1e4-130"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="0a1e4-131">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="0a1e4-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0a1e4-132">Búfer de entrada de la consola</span><span class="sxs-lookup"><span data-stu-id="0a1e4-132">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="0a1e4-133">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="0a1e4-133">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="0a1e4-134">**registro de entrada \_**</span><span class="sxs-lookup"><span data-stu-id="0a1e4-134">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="0a1e4-135">**\_registro de eventos del mouse \_**</span><span class="sxs-lookup"><span data-stu-id="0a1e4-135">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

 

 




