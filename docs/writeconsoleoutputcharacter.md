---
title: WriteConsoleOutputCharacter función)
description: Copia un número de caracteres en celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/WriteConsoleOutputCharacter
- wincon/WriteConsoleOutputCharacter
- WriteConsoleOutputCharacter
- consoleapi2/WriteConsoleOutputCharacterA
- wincon/WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterA
- consoleapi2/WriteConsoleOutputCharacterW
- wincon/WriteConsoleOutputCharacterW
- WriteConsoleOutputCharacterW
MS-HAID:
- '\_win32\_writeconsoleoutputcharacter'
- base.writeconsoleoutputcharacter
- consoles.writeconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 7cc935ea-6b19-4494-b746-259aa7aaa9cc
topic_type:
- apiref
api_name:
- WriteConsoleOutputCharacter
- WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 462ebfaed09a5c18fa9a075227a5568a789685bd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037213"
---
# <a name="writeconsoleoutputcharacter-function"></a><span data-ttu-id="959e8-104">WriteConsoleOutputCharacter función)</span><span class="sxs-lookup"><span data-stu-id="959e8-104">WriteConsoleOutputCharacter function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="959e8-105">Copia un número de caracteres en celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.</span><span class="sxs-lookup"><span data-stu-id="959e8-105">Copies a number of characters to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="959e8-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="959e8-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  LPCTSTR lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="959e8-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="959e8-107">Parameters</span></span>

<span data-ttu-id="959e8-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="959e8-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="959e8-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="959e8-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="959e8-110">El identificador debe tener el derecho de acceso de **\_ escritura genérico** .</span><span class="sxs-lookup"><span data-stu-id="959e8-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="959e8-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="959e8-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="959e8-112">*lpCharacter* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="959e8-112">*lpCharacter* \[in\]</span></span>  
<span data-ttu-id="959e8-113">Caracteres que se van a escribir en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="959e8-113">The characters to be written to the console screen buffer.</span></span>

<span data-ttu-id="959e8-114">*nLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="959e8-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="959e8-115">El número de caracteres que se va a escribir.</span><span class="sxs-lookup"><span data-stu-id="959e8-115">The number of characters to be written.</span></span>

<span data-ttu-id="959e8-116">*dwWriteCoord* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="959e8-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="959e8-117">Estructura de [**coordenadas**](coord-str.md) que especifica las coordenadas de caracteres de la primera celda en el búfer de pantalla de la consola en la que se escribirán los caracteres.</span><span class="sxs-lookup"><span data-stu-id="959e8-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which characters will be written.</span></span>

<span data-ttu-id="959e8-118">*lpNumberOfCharsWritten* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="959e8-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="959e8-119">Puntero a una variable que recibe el número de caracteres escritos realmente.</span><span class="sxs-lookup"><span data-stu-id="959e8-119">A pointer to a variable that receives the number of characters actually written.</span></span>

## <a name="return-value"></a><span data-ttu-id="959e8-120">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="959e8-120">Return value</span></span>

<span data-ttu-id="959e8-121">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="959e8-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="959e8-122">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="959e8-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="959e8-123">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="959e8-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="959e8-124">Comentarios</span><span class="sxs-lookup"><span data-stu-id="959e8-124">Remarks</span></span>

<span data-ttu-id="959e8-125">Si el número de caracteres que se va a escribir se extiende más allá del final de la fila especificada en el búfer de pantalla de la consola, los caracteres se escriben en la fila siguiente.</span><span class="sxs-lookup"><span data-stu-id="959e8-125">If the number of characters to be written to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="959e8-126">Si el número de caracteres que se va a escribir se extiende más allá del final del búfer de pantalla de la consola, los caracteres se escriben al final del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="959e8-126">If the number of characters to be written to extends beyond the end of the console screen buffer, characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="959e8-127">Los valores de atributo en las posiciones escritas en no cambian.</span><span class="sxs-lookup"><span data-stu-id="959e8-127">The attribute values at the positions written to are not changed.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="959e8-128">Esta API tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente en las secuencias de **[formato de texto](console-virtual-terminal-sequences.md#text-formatting)** y **[posición del cursor](console-virtual-terminal-sequences.md#cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="959e8-128">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sequences.</span></span> <span data-ttu-id="959e8-129">Mueva el cursor a la ubicación que se va a insertar, aplique el formato deseado y escriba el texto para rellenar.</span><span class="sxs-lookup"><span data-stu-id="959e8-129">Move the cursor to the location to insert, apply the formatting desired, and write out text to fill.</span></span> <span data-ttu-id="959e8-130">No hay ningún equivalente para emitir texto en un área sin aplicar también el formato de color activo.</span><span class="sxs-lookup"><span data-stu-id="959e8-130">There is no equivalent to emit text to an area without also applying the active color formatting.</span></span> <span data-ttu-id="959e8-131">Esta decisión alinea intencionadamente la plataforma de Windows con otros sistemas operativos en los que se espera que la aplicación cliente individual Recuerde su propio estado dibujado para su posterior manipulación.</span><span class="sxs-lookup"><span data-stu-id="959e8-131">This decision intentionally aligns the Windows platform with other operating systems where the individual client application is expected to remember its own drawn state for further manipulation.</span></span>

## <a name="requirements"></a><span data-ttu-id="959e8-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="959e8-132">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="959e8-133">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="959e8-133">Minimum supported client</span></span> | <span data-ttu-id="959e8-134">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="959e8-134">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="959e8-135">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="959e8-135">Minimum supported server</span></span> | <span data-ttu-id="959e8-136">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="959e8-136">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="959e8-137">Encabezado</span><span class="sxs-lookup"><span data-stu-id="959e8-137">Header</span></span> | <span data-ttu-id="959e8-138">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="959e8-138">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="959e8-139">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="959e8-139">Library</span></span> | <span data-ttu-id="959e8-140">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="959e8-140">Kernel32.lib</span></span> |
| <span data-ttu-id="959e8-141">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="959e8-141">DLL</span></span> | <span data-ttu-id="959e8-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="959e8-142">Kernel32.dll</span></span> |
| <span data-ttu-id="959e8-143">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="959e8-143">Unicode and ANSI names</span></span> | <span data-ttu-id="959e8-144">**WriteConsoleOutputCharacterW** (Unicode) y **WriteConsoleOutputCharacterA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="959e8-144">**WriteConsoleOutputCharacterW** (Unicode) and **WriteConsoleOutputCharacterA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="959e8-145">Consulte también</span><span class="sxs-lookup"><span data-stu-id="959e8-145">See also</span></span>

[<span data-ttu-id="959e8-146">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="959e8-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="959e8-147">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="959e8-147">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="959e8-148">Funciones de salida de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="959e8-148">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="959e8-149">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="959e8-149">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="959e8-150">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="959e8-150">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="959e8-151">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="959e8-151">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="959e8-152">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="959e8-152">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="959e8-153">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="959e8-153">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="959e8-154">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="959e8-154">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="959e8-155">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="959e8-155">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)
