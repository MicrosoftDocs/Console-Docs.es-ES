---
title: WriteConsoleOutputAttribute función)
description: Copia un número de atributos de carácter en celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/WriteConsoleOutputAttribute
- wincon/WriteConsoleOutputAttribute
- WriteConsoleOutputAttribute
MS-HAID:
- '\_win32\_writeconsoleoutputattribute'
- base.writeconsoleoutputattribute
- consoles.writeconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 52a9d6e5-072e-4411-9945-10bd3dd61e25
topic_type:
- apiref
api_name:
- WriteConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 04c7799cd98479d3b776b1933994b60f5ed9fc9f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039283"
---
# <a name="writeconsoleoutputattribute-function"></a><span data-ttu-id="ed4cd-104">WriteConsoleOutputAttribute función)</span><span class="sxs-lookup"><span data-stu-id="ed4cd-104">WriteConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="ed4cd-105">Copia un número de atributos de carácter en celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.</span><span class="sxs-lookup"><span data-stu-id="ed4cd-105">Copies a number of character attributes to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="ed4cd-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ed4cd-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="ed4cd-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ed4cd-107">Parameters</span></span>

<span data-ttu-id="ed4cd-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="ed4cd-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="ed4cd-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="ed4cd-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="ed4cd-110">El identificador debe tener el derecho de acceso de **\_ escritura genérico** .</span><span class="sxs-lookup"><span data-stu-id="ed4cd-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="ed4cd-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="ed4cd-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="ed4cd-112">*lpAttribute* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="ed4cd-112">*lpAttribute* \[in\]</span></span>  
<span data-ttu-id="ed4cd-113">Atributos que se van a usar al escribir en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="ed4cd-113">The attributes to be used when writing to the console screen buffer.</span></span> <span data-ttu-id="ed4cd-114">Para obtener más información, vea [atributos de caracteres](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="ed4cd-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="ed4cd-115">*nLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="ed4cd-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="ed4cd-116">El número de celdas de caracteres del búfer de pantalla en las que se copiarán los atributos.</span><span class="sxs-lookup"><span data-stu-id="ed4cd-116">The number of screen buffer character cells to which the attributes will be copied.</span></span>

<span data-ttu-id="ed4cd-117">*dwWriteCoord* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="ed4cd-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="ed4cd-118">Estructura de [**coordenadas**](coord-str.md) que especifica las coordenadas de caracteres de la primera celda en el búfer de pantalla de la consola en la que se escribirán los atributos.</span><span class="sxs-lookup"><span data-stu-id="ed4cd-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which the attributes will be written.</span></span>

<span data-ttu-id="ed4cd-119">*lpNumberOfAttrsWritten* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="ed4cd-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="ed4cd-120">Puntero a una variable que recibe el número de atributos escritos realmente en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="ed4cd-120">A pointer to a variable that receives the number of attributes actually written to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="ed4cd-121">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="ed4cd-121">Return value</span></span>

<span data-ttu-id="ed4cd-122">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="ed4cd-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ed4cd-123">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="ed4cd-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ed4cd-124">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="ed4cd-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="ed4cd-125">Comentarios</span><span class="sxs-lookup"><span data-stu-id="ed4cd-125">Remarks</span></span>

<span data-ttu-id="ed4cd-126">Si el número de atributos que se va a escribir se extiende más allá del final de la fila especificada en el búfer de pantalla de la consola, los atributos se escriben en la fila siguiente.</span><span class="sxs-lookup"><span data-stu-id="ed4cd-126">If the number of attributes to be written to extends beyond the end of the specified row in the console screen buffer, attributes are written to the next row.</span></span> <span data-ttu-id="ed4cd-127">Si el número de atributos que se va a escribir se extiende más allá del final del búfer de pantalla de la consola, los atributos se escriben hasta el final del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="ed4cd-127">If the number of attributes to be written to extends beyond the end of the console screen buffer, the attributes are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="ed4cd-128">Los valores de caracteres en las posiciones escritas en no cambian.</span><span class="sxs-lookup"><span data-stu-id="ed4cd-128">The character values at the positions written to are not changed.</span></span>

> [!TIP]
> <span data-ttu-id="ed4cd-129">Esta API tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente en las secuencias de **[formato de texto](console-virtual-terminal-sequences.md#text-formatting)** y **[posición del cursor](console-virtual-terminal-sequences.md#cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="ed4cd-129">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sequences.</span></span> <span data-ttu-id="ed4cd-130">Mueva el cursor a la ubicación que se va a insertar, aplique el formato deseado y escriba el texto para rellenar.</span><span class="sxs-lookup"><span data-stu-id="ed4cd-130">Move the cursor to the location to insert, apply the formatting desired, and write out text to fill.</span></span> <span data-ttu-id="ed4cd-131">No hay ningún equivalente para aplicar color a un área sin emitir también texto.</span><span class="sxs-lookup"><span data-stu-id="ed4cd-131">There is no equivalent to apply color to an area without also emitting text.</span></span> <span data-ttu-id="ed4cd-132">Esta decisión alinea intencionadamente la plataforma de Windows con otros sistemas operativos en los que se espera que la aplicación cliente individual Recuerde su propio estado dibujado para su posterior manipulación.</span><span class="sxs-lookup"><span data-stu-id="ed4cd-132">This decision intentionally aligns the Windows platform with other operating systems where the individual client application is expected to remember its own drawn state for further manipulation.</span></span>

## <a name="requirements"></a><span data-ttu-id="ed4cd-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ed4cd-133">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ed4cd-134">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="ed4cd-134">Minimum supported client</span></span> | <span data-ttu-id="ed4cd-135">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="ed4cd-135">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="ed4cd-136">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="ed4cd-136">Minimum supported server</span></span> | <span data-ttu-id="ed4cd-137">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="ed4cd-137">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="ed4cd-138">Encabezado</span><span class="sxs-lookup"><span data-stu-id="ed4cd-138">Header</span></span> | <span data-ttu-id="ed4cd-139">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ed4cd-139">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ed4cd-140">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="ed4cd-140">Library</span></span> | <span data-ttu-id="ed4cd-141">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ed4cd-141">Kernel32.lib</span></span> |
| <span data-ttu-id="ed4cd-142">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="ed4cd-142">DLL</span></span> | <span data-ttu-id="ed4cd-143">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ed4cd-143">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="ed4cd-144">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ed4cd-144">See also</span></span>

[<span data-ttu-id="ed4cd-145">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="ed4cd-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ed4cd-146">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="ed4cd-146">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="ed4cd-147">Funciones de salida de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="ed4cd-147">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="ed4cd-148">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="ed4cd-148">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="ed4cd-149">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="ed4cd-149">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="ed4cd-150">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="ed4cd-150">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="ed4cd-151">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="ed4cd-151">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="ed4cd-152">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="ed4cd-152">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
