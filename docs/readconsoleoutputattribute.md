---
title: ReadConsoleOutputAttribute función)
description: Copia un número especificado de atributos de carácter de las celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/ReadConsoleOutputAttribute
- wincon/ReadConsoleOutputAttribute
- ReadConsoleOutputAttribute
MS-HAID:
- '\_win32\_readconsoleoutputattribute'
- base.readconsoleoutputattribute
- consoles.readconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c3e35779-a487-47f1-8d07-0d5fae99d54a
topic_type:
- apiref
api_name:
- ReadConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: f64e39b7b68e24e6c2aa7e9704c285bbbbc234f0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039513"
---
# <a name="readconsoleoutputattribute-function"></a><span data-ttu-id="c0162-104">ReadConsoleOutputAttribute función)</span><span class="sxs-lookup"><span data-stu-id="c0162-104">ReadConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="c0162-105">Copia un número especificado de atributos de carácter de las celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.</span><span class="sxs-lookup"><span data-stu-id="c0162-105">Copies a specified number of character attributes from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="c0162-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c0162-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPWORD  lpAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfAttrsRead
);
```

## <a name="parameters"></a><span data-ttu-id="c0162-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="c0162-107">Parameters</span></span>

<span data-ttu-id="c0162-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="c0162-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="c0162-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="c0162-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="c0162-110">El identificador debe tener el derecho de acceso de **\_ lectura genérico** .</span><span class="sxs-lookup"><span data-stu-id="c0162-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="c0162-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="c0162-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="c0162-112">*lpAttribute* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="c0162-112">*lpAttribute* \[out\]</span></span>  
<span data-ttu-id="c0162-113">Un puntero a un búfer que recibe los atributos utilizados por el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="c0162-113">A pointer to a buffer that receives the attributes being used by the console screen buffer.</span></span>

<span data-ttu-id="c0162-114">Para obtener más información, vea [atributos de caracteres](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="c0162-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="c0162-115">*nLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="c0162-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="c0162-116">Número de celdas de caracteres del búfer de pantalla desde las que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="c0162-116">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="c0162-117">El tamaño del búfer al que apunta el parámetro *lpAttribute* debe ser `nLength * sizeof(WORD)` .</span><span class="sxs-lookup"><span data-stu-id="c0162-117">The size of the buffer pointed to by the *lpAttribute* parameter should be `nLength * sizeof(WORD)`.</span></span>

<span data-ttu-id="c0162-118">*dwReadCoord* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="c0162-118">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="c0162-119">Coordenadas de la primera celda en el búfer de pantalla de la consola desde la que se va a leer, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="c0162-119">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="c0162-120">El miembro **X** de la estructura [**coordenadas**](coord-str.md) es la columna y el miembro **y** es la fila.</span><span class="sxs-lookup"><span data-stu-id="c0162-120">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="c0162-121">*lpNumberOfAttrsRead* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="c0162-121">*lpNumberOfAttrsRead* \[out\]</span></span>  
<span data-ttu-id="c0162-122">Puntero a una variable que recibe el número de atributos leídos realmente.</span><span class="sxs-lookup"><span data-stu-id="c0162-122">A pointer to a variable that receives the number of attributes actually read.</span></span>

## <a name="return-value"></a><span data-ttu-id="c0162-123">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="c0162-123">Return value</span></span>

<span data-ttu-id="c0162-124">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="c0162-124">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c0162-125">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="c0162-125">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c0162-126">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="c0162-126">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="c0162-127">Comentarios</span><span class="sxs-lookup"><span data-stu-id="c0162-127">Remarks</span></span>

<span data-ttu-id="c0162-128">Si el número de atributos que se van a leer de se extiende más allá del final de la fila de búfer de pantalla especificada, los atributos se leen de la fila siguiente.</span><span class="sxs-lookup"><span data-stu-id="c0162-128">If the number of attributes to be read from extends beyond the end of the specified screen buffer row, attributes are read from the next row.</span></span> <span data-ttu-id="c0162-129">Si el número de atributos que se van a leer se extiende más allá del final del búfer de pantalla de la consola, se leen los atributos hasta el final del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="c0162-129">If the number of attributes to be read from extends beyond the end of the console screen buffer, attributes up to the end of the console screen buffer are read.</span></span>

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="requirements"></a><span data-ttu-id="c0162-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c0162-130">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c0162-131">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="c0162-131">Minimum supported client</span></span> | <span data-ttu-id="c0162-132">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="c0162-132">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="c0162-133">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="c0162-133">Minimum supported server</span></span> | <span data-ttu-id="c0162-134">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="c0162-134">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="c0162-135">Encabezado</span><span class="sxs-lookup"><span data-stu-id="c0162-135">Header</span></span> | <span data-ttu-id="c0162-136">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c0162-136">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c0162-137">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="c0162-137">Library</span></span> | <span data-ttu-id="c0162-138">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="c0162-138">Kernel32.lib</span></span> |
| <span data-ttu-id="c0162-139">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="c0162-139">DLL</span></span> | <span data-ttu-id="c0162-140">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c0162-140">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="c0162-141">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c0162-141">See also</span></span>

[<span data-ttu-id="c0162-142">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="c0162-142">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c0162-143">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="c0162-143">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="c0162-144">Funciones de salida de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="c0162-144">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="c0162-145">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="c0162-145">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="c0162-146">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="c0162-146">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="c0162-147">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="c0162-147">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="c0162-148">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="c0162-148">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="c0162-149">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="c0162-149">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
