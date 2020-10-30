---
title: FillConsoleOutputAttribute función)
description: Establece los atributos de carácter para un número especificado de celdas de caracteres, a partir de las coordenadas especificadas en un búfer de pantalla.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/FillConsoleOutputAttribute
- wincon/FillConsoleOutputAttribute
- FillConsoleOutputAttribute
MS-HAID:
- '\_win32\_fillconsoleoutputattribute'
- base.fillconsoleoutputattribute
- consoles.fillconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 09440263-71c4-4b7a-8fc6-a2b4fcd677ff
topic_type:
- apiref
api_name:
- FillConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 40eb97e43e406d68ff625db110998ebf69eb26f7
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039073"
---
# <a name="fillconsoleoutputattribute-function"></a><span data-ttu-id="88d4a-104">FillConsoleOutputAttribute función)</span><span class="sxs-lookup"><span data-stu-id="88d4a-104">FillConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="88d4a-105">Establece los atributos de carácter para un número especificado de celdas de caracteres, a partir de las coordenadas especificadas en un búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="88d4a-105">Sets the character attributes for a specified number of character cells, beginning at the specified coordinates in a screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="88d4a-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="88d4a-106">Syntax</span></span>

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="88d4a-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="88d4a-107">Parameters</span></span>

<span data-ttu-id="88d4a-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="88d4a-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="88d4a-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="88d4a-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="88d4a-110">El identificador debe tener el derecho de acceso de **\_ escritura genérico** .</span><span class="sxs-lookup"><span data-stu-id="88d4a-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="88d4a-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="88d4a-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="88d4a-112">*wAttribute* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="88d4a-112">*wAttribute* \[in\]</span></span>  
<span data-ttu-id="88d4a-113">Atributos que se van a usar al escribir en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="88d4a-113">The attributes to use when writing to the console screen buffer.</span></span> <span data-ttu-id="88d4a-114">Para obtener más información, vea [atributos de caracteres](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="88d4a-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="88d4a-115">*nLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="88d4a-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="88d4a-116">El número de celdas de caracteres que se van a establecer en los atributos de color especificados.</span><span class="sxs-lookup"><span data-stu-id="88d4a-116">The number of character cells to be set to the specified color attributes.</span></span>

<span data-ttu-id="88d4a-117">*dwWriteCoord* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="88d4a-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="88d4a-118">Estructura de [**coordenadas**](coord-str.md) que especifica las coordenadas de caracteres de la primera celda cuyos atributos se van a establecer.</span><span class="sxs-lookup"><span data-stu-id="88d4a-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell whose attributes are to be set.</span></span>

<span data-ttu-id="88d4a-119">*lpNumberOfAttrsWritten* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="88d4a-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="88d4a-120">Puntero a una variable que recibe el número de celdas de caracteres cuyos atributos se establecieron realmente.</span><span class="sxs-lookup"><span data-stu-id="88d4a-120">A pointer to a variable that receives the number of character cells whose attributes were actually set.</span></span>

## <a name="return-value"></a><span data-ttu-id="88d4a-121">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="88d4a-121">Return value</span></span>

<span data-ttu-id="88d4a-122">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="88d4a-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="88d4a-123">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="88d4a-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="88d4a-124">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="88d4a-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="88d4a-125">Comentarios</span><span class="sxs-lookup"><span data-stu-id="88d4a-125">Remarks</span></span>

<span data-ttu-id="88d4a-126">Si el número de celdas de caracteres cuyos atributos se van a establecer se extiende más allá del final de la fila especificada en el búfer de pantalla de la consola, se establecen las celdas de la fila siguiente.</span><span class="sxs-lookup"><span data-stu-id="88d4a-126">If the number of character cells whose attributes are to be set extends beyond the end of the specified row in the console screen buffer, the cells of the next row are set.</span></span> <span data-ttu-id="88d4a-127">Si el número de celdas que se van a escribir se extiende más allá del final del búfer de pantalla de la consola, las celdas se escriben hasta el final del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="88d4a-127">If the number of cells to write to extends beyond the end of the console screen buffer, the cells are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="88d4a-128">Los valores de caracteres en las posiciones escritas en no cambian.</span><span class="sxs-lookup"><span data-stu-id="88d4a-128">The character values at the positions written to are not changed.</span></span>

> [!TIP]
> <span data-ttu-id="88d4a-129">Esta API no se recomienda y no tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** específico equivalente.</span><span class="sxs-lookup"><span data-stu-id="88d4a-129">This API is not recommended and does not have a specific **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="88d4a-130">No se admite el rellenado de la región fuera de la ventana visible y se reserva para el espacio de historial del terminal.</span><span class="sxs-lookup"><span data-stu-id="88d4a-130">Filling the region outside the viewable window is not supported and is reserved for the terminal's history space.</span></span> <span data-ttu-id="88d4a-131">El rellenado de un área visible con nuevo texto o color se realiza mediante el **[movimiento del cursor](console-virtual-terminal-sequences.md#cursor-positioning)** , **[la configuración de los nuevos atributos](console-virtual-terminal-sequences.md#text-formatting)** y la escritura del texto deseado para esa región, repitiendo los caracteres si es necesario para la longitud de la ejecución de relleno.</span><span class="sxs-lookup"><span data-stu-id="88d4a-131">Filling a visible region with new text or color is performed through **[moving the cursor](console-virtual-terminal-sequences.md#cursor-positioning)** , **[setting the new attributes](console-virtual-terminal-sequences.md#text-formatting)** , then writing the desired text for that region, repeating characters if necessary for the length of the fill run.</span></span> <span data-ttu-id="88d4a-132">Es posible que se requiera un movimiento de cursor adicional seguido de la escritura del texto deseado para rellenar una región rectangular.</span><span class="sxs-lookup"><span data-stu-id="88d4a-132">Additional cursor movement may be required followed by writing the desired text to fill a rectangular region.</span></span> <span data-ttu-id="88d4a-133">Se espera que la aplicación cliente mantenga su propia memoria de lo que se encuentra en la pantalla y que no puede consultar el estado remoto.</span><span class="sxs-lookup"><span data-stu-id="88d4a-133">The client application is expected to keep its own memory of what is on the screen and is not able to query the remote state.</span></span> <span data-ttu-id="88d4a-134">Puede encontrar más información en la **[consola clásica](classic-vs-vt.md)** y en la documentación de terminal virtual.</span><span class="sxs-lookup"><span data-stu-id="88d4a-134">More information can be found in **[classic console versus virtual terminal](classic-vs-vt.md)** documentation.</span></span>

## <a name="requirements"></a><span data-ttu-id="88d4a-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88d4a-135">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="88d4a-136">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="88d4a-136">Minimum supported client</span></span> | <span data-ttu-id="88d4a-137">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="88d4a-137">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="88d4a-138">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="88d4a-138">Minimum supported server</span></span> | <span data-ttu-id="88d4a-139">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="88d4a-139">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="88d4a-140">Encabezado</span><span class="sxs-lookup"><span data-stu-id="88d4a-140">Header</span></span> | <span data-ttu-id="88d4a-141">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="88d4a-141">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="88d4a-142">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="88d4a-142">Library</span></span> | <span data-ttu-id="88d4a-143">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="88d4a-143">Kernel32.lib</span></span> |
| <span data-ttu-id="88d4a-144">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="88d4a-144">DLL</span></span> | <span data-ttu-id="88d4a-145">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="88d4a-145">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="88d4a-146">Consulte también</span><span class="sxs-lookup"><span data-stu-id="88d4a-146">See also</span></span>

[<span data-ttu-id="88d4a-147">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="88d4a-147">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="88d4a-148">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="88d4a-148">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="88d4a-149">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="88d4a-149">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="88d4a-150">Funciones de salida de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="88d4a-150">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="88d4a-151">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="88d4a-151">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

[<span data-ttu-id="88d4a-152">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="88d4a-152">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)
