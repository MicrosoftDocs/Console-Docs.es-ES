---
title: FillConsoleOutputCharacter función)
description: Escribe un carácter en el búfer de la pantalla de la consola un número especificado de veces, comenzando en las coordenadas especificadas.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/FillConsoleOutputCharacter
- wincon/FillConsoleOutputCharacter
- FillConsoleOutputCharacter
- consoleapi2/FillConsoleOutputCharacterA
- wincon/FillConsoleOutputCharacterA
- FillConsoleOutputCharacterA
- consoleapi2/FillConsoleOutputCharacterW
- wincon/FillConsoleOutputCharacterW
- FillConsoleOutputCharacterW
MS-HAID:
- '\_win32\_fillconsoleoutputcharacter'
- base.fillconsoleoutputcharacter
- consoles.fillconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 37579cc9-14b3-4fd9-81ed-abaad5c7bd1a
topic_type:
- apiref
api_name:
- FillConsoleOutputCharacter
- FillConsoleOutputCharacterA
- FillConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 95efbcc261943a2986fe6fbb1f3d54aaae1b2d2b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357515"
---
# <a name="fillconsoleoutputcharacter-function"></a><span data-ttu-id="4397d-104">FillConsoleOutputCharacter función)</span><span class="sxs-lookup"><span data-stu-id="4397d-104">FillConsoleOutputCharacter function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="4397d-105">Escribe un carácter en el búfer de la pantalla de la consola un número especificado de veces, comenzando en las coordenadas especificadas.</span><span class="sxs-lookup"><span data-stu-id="4397d-105">Writes a character to the console screen buffer a specified number of times, beginning at the specified coordinates.</span></span>

## <a name="syntax"></a><span data-ttu-id="4397d-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4397d-106">Syntax</span></span>

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="4397d-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4397d-107">Parameters</span></span>

<span data-ttu-id="4397d-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4397d-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="4397d-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="4397d-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="4397d-110">El identificador debe tener derecho de acceso de **GENERIC\_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="4397d-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="4397d-111">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="4397d-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="4397d-112">*cCharacter* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="4397d-112">*cCharacter* \[in\]</span></span>  
<span data-ttu-id="4397d-113">Carácter que se va a escribir en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="4397d-113">The character to be written to the console screen buffer.</span></span>

<span data-ttu-id="4397d-114">*nLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="4397d-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="4397d-115">El número de celdas de caracteres en las que se debe escribir el carácter.</span><span class="sxs-lookup"><span data-stu-id="4397d-115">The number of character cells to which the character should be written.</span></span>

<span data-ttu-id="4397d-116">*dwWriteCoord* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="4397d-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="4397d-117">Estructura de [**coordenadas**](coord-str.md) que especifica las coordenadas de caracteres de la primera celda en la que se va a escribir el carácter.</span><span class="sxs-lookup"><span data-stu-id="4397d-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell to which the character is to be written.</span></span>

<span data-ttu-id="4397d-118">*lpNumberOfCharsWritten* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="4397d-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="4397d-119">Puntero a una variable que recibe el número de caracteres escritos realmente en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="4397d-119">A pointer to a variable that receives the number of characters actually written to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="4397d-120">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4397d-120">Return value</span></span>

<span data-ttu-id="4397d-121">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="4397d-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4397d-122">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="4397d-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4397d-123">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="4397d-123">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="4397d-124">Comentarios</span><span class="sxs-lookup"><span data-stu-id="4397d-124">Remarks</span></span>

<span data-ttu-id="4397d-125">Si el número de caracteres que se va a escribir se extiende más allá del final de la fila especificada en el búfer de pantalla de la consola, los caracteres se escriben en la fila siguiente.</span><span class="sxs-lookup"><span data-stu-id="4397d-125">If the number of characters to write to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="4397d-126">Si el número de caracteres que se va a escribir se extiende más allá del final del búfer de pantalla de la consola, los caracteres se escriben al final del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="4397d-126">If the number of characters to write to extends beyond the end of the console screen buffer, the characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="4397d-127">Los valores de atributo en las posiciones escritas no cambian.</span><span class="sxs-lookup"><span data-stu-id="4397d-127">The attribute values at the positions written are not changed.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="4397d-128">Esta API no se recomienda y no tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** específico equivalente.</span><span class="sxs-lookup"><span data-stu-id="4397d-128">This API is not recommended and does not have a specific **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="4397d-129">No se admite el rellenado de la región fuera de la ventana visible y se reserva para el espacio de historial del terminal.</span><span class="sxs-lookup"><span data-stu-id="4397d-129">Filling the region outside the viewable window is not supported and is reserved for the terminal's history space.</span></span> <span data-ttu-id="4397d-130">El rellenado de un área visible con nuevo texto o color se realiza mediante el **[movimiento del cursor](console-virtual-terminal-sequences.md#cursor-positioning)**, **[la configuración de los nuevos atributos](console-virtual-terminal-sequences.md#text-formatting)** y la escritura del texto deseado para esa región, repitiendo los caracteres si es necesario para la longitud de la ejecución de relleno.</span><span class="sxs-lookup"><span data-stu-id="4397d-130">Filling a visible region with new text or color is performed through **[moving the cursor](console-virtual-terminal-sequences.md#cursor-positioning)**, **[setting the new attributes](console-virtual-terminal-sequences.md#text-formatting)**, then writing the desired text for that region, repeating characters if necessary for the length of the fill run.</span></span> <span data-ttu-id="4397d-131">Es posible que se requiera un movimiento de cursor adicional seguido de la escritura del texto deseado para rellenar una región rectangular.</span><span class="sxs-lookup"><span data-stu-id="4397d-131">Additional cursor movement may be required followed by writing the desired text to fill a rectangular region.</span></span> <span data-ttu-id="4397d-132">Se espera que la aplicación cliente mantenga su propia memoria de lo que se encuentra en la pantalla y que no puede consultar el estado remoto.</span><span class="sxs-lookup"><span data-stu-id="4397d-132">The client application is expected to keep its own memory of what is on the screen and is not able to query the remote state.</span></span> <span data-ttu-id="4397d-133">Puede encontrar más información en la **[consola clásica](classic-vs-vt.md)** y en la documentación de terminal virtual.</span><span class="sxs-lookup"><span data-stu-id="4397d-133">More information can be found in **[classic console versus virtual terminal](classic-vs-vt.md)** documentation.</span></span>

## <a name="requirements"></a><span data-ttu-id="4397d-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4397d-134">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4397d-135">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="4397d-135">Minimum supported client</span></span> | <span data-ttu-id="4397d-136">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="4397d-136">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="4397d-137">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="4397d-137">Minimum supported server</span></span> | <span data-ttu-id="4397d-138">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="4397d-138">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="4397d-139">Encabezado</span><span class="sxs-lookup"><span data-stu-id="4397d-139">Header</span></span> | <span data-ttu-id="4397d-140">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4397d-140">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="4397d-141">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="4397d-141">Library</span></span> | <span data-ttu-id="4397d-142">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="4397d-142">Kernel32.lib</span></span> |
| <span data-ttu-id="4397d-143">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="4397d-143">DLL</span></span> | <span data-ttu-id="4397d-144">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4397d-144">Kernel32.dll</span></span> |
| <span data-ttu-id="4397d-145">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="4397d-145">Unicode and ANSI names</span></span> | <span data-ttu-id="4397d-146">**FillConsoleOutputCharacterW** (Unicode) y **FillConsoleOutputCharacterA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="4397d-146">**FillConsoleOutputCharacterW** (Unicode) and **FillConsoleOutputCharacterA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="4397d-147">Vea también</span><span class="sxs-lookup"><span data-stu-id="4397d-147">See also</span></span>

[<span data-ttu-id="4397d-148">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="4397d-148">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4397d-149">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="4397d-149">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="4397d-150">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="4397d-150">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="4397d-151">Funciones de salida de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="4397d-151">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="4397d-152">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="4397d-152">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="4397d-153">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="4397d-153">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="4397d-154">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="4397d-154">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)