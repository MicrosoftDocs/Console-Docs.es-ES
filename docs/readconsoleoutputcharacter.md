---
title: ReadConsoleOutputCharacter función)
description: Copia un número de caracteres de las celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/ReadConsoleOutputCharacter
- wincon/ReadConsoleOutputCharacter
- ReadConsoleOutputCharacter
- consoleapi2/ReadConsoleOutputCharacterA
- wincon/ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterA
- consoleapi2/ReadConsoleOutputCharacterW
- wincon/ReadConsoleOutputCharacterW
- ReadConsoleOutputCharacterW
MS-HAID:
- '\_win32\_readconsoleoutputcharacter'
- base.readconsoleoutputcharacter
- consoles.readconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f47464a9-6c59-4f15-abd0-be29ab515698
topic_type:
- apiref
api_name:
- ReadConsoleOutputCharacter
- ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: fa70841d5dccf3289807d29c67fab86e3b445279
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037731"
---
# <a name="readconsoleoutputcharacter-function"></a><span data-ttu-id="726e6-104">ReadConsoleOutputCharacter función)</span><span class="sxs-lookup"><span data-stu-id="726e6-104">ReadConsoleOutputCharacter function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="726e6-105">Copia un número de caracteres de las celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.</span><span class="sxs-lookup"><span data-stu-id="726e6-105">Copies a number of characters from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="726e6-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="726e6-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPTSTR  lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfCharsRead
);
```

## <a name="parameters"></a><span data-ttu-id="726e6-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="726e6-107">Parameters</span></span>

<span data-ttu-id="726e6-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="726e6-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="726e6-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="726e6-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="726e6-110">El identificador debe tener el derecho de acceso de **\_ lectura genérico** .</span><span class="sxs-lookup"><span data-stu-id="726e6-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="726e6-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="726e6-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="726e6-112">*lpCharacter* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="726e6-112">*lpCharacter* \[out\]</span></span>  
<span data-ttu-id="726e6-113">Un puntero a un búfer que recibe los caracteres leídos del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="726e6-113">A pointer to a buffer that receives the characters read from the console screen buffer.</span></span>

<span data-ttu-id="726e6-114">*nLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="726e6-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="726e6-115">Número de celdas de caracteres del búfer de pantalla desde las que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="726e6-115">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="726e6-116">El tamaño del búfer al que apunta el parámetro *lpCharacter* debe ser `nLength * sizeof(TCHAR)` .</span><span class="sxs-lookup"><span data-stu-id="726e6-116">The size of the buffer pointed to by the *lpCharacter* parameter should be `nLength * sizeof(TCHAR)`.</span></span>

<span data-ttu-id="726e6-117">*dwReadCoord* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="726e6-117">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="726e6-118">Coordenadas de la primera celda en el búfer de pantalla de la consola desde la que se va a leer, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="726e6-118">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="726e6-119">El miembro **X** de la estructura [**coordenadas**](coord-str.md) es la columna y el miembro **y** es la fila.</span><span class="sxs-lookup"><span data-stu-id="726e6-119">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="726e6-120">*lpNumberOfCharsRead* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="726e6-120">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="726e6-121">Puntero a una variable que recibe el número de caracteres leídos realmente.</span><span class="sxs-lookup"><span data-stu-id="726e6-121">A pointer to a variable that receives the number of characters actually read.</span></span>

## <a name="return-value"></a><span data-ttu-id="726e6-122">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="726e6-122">Return value</span></span>

<span data-ttu-id="726e6-123">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="726e6-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="726e6-124">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="726e6-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="726e6-125">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="726e6-125">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="726e6-126">Comentarios</span><span class="sxs-lookup"><span data-stu-id="726e6-126">Remarks</span></span>

<span data-ttu-id="726e6-127">Si el número de caracteres que se van a leer de se extiende más allá del final de la fila de búfer de pantalla especificada, se leen los caracteres de la fila siguiente.</span><span class="sxs-lookup"><span data-stu-id="726e6-127">If the number of characters to be read from extends beyond the end of the specified screen buffer row, characters are read from the next row.</span></span> <span data-ttu-id="726e6-128">Si el número de caracteres que se van a leer de se extiende más allá del final del búfer de pantalla de la consola, se leen los caracteres hasta el final del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="726e6-128">If the number of characters to be read from extends beyond the end of the console screen buffer, characters up to the end of the console screen buffer are read.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="requirements"></a><span data-ttu-id="726e6-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="726e6-129">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="726e6-130">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="726e6-130">Minimum supported client</span></span> | <span data-ttu-id="726e6-131">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="726e6-131">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="726e6-132">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="726e6-132">Minimum supported server</span></span> | <span data-ttu-id="726e6-133">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="726e6-133">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="726e6-134">Encabezado</span><span class="sxs-lookup"><span data-stu-id="726e6-134">Header</span></span> | <span data-ttu-id="726e6-135">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="726e6-135">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="726e6-136">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="726e6-136">Library</span></span> | <span data-ttu-id="726e6-137">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="726e6-137">Kernel32.lib</span></span> |
| <span data-ttu-id="726e6-138">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="726e6-138">DLL</span></span> | <span data-ttu-id="726e6-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="726e6-139">Kernel32.dll</span></span> |
| <span data-ttu-id="726e6-140">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="726e6-140">Unicode and ANSI names</span></span> | <span data-ttu-id="726e6-141">**ReadConsoleOutputCharacterW** (Unicode) y **ReadConsoleOutputCharacterA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="726e6-141">**ReadConsoleOutputCharacterW** (Unicode) and **ReadConsoleOutputCharacterA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="726e6-142">Consulte también</span><span class="sxs-lookup"><span data-stu-id="726e6-142">See also</span></span>

[<span data-ttu-id="726e6-143">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="726e6-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="726e6-144">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="726e6-144">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="726e6-145">Funciones de salida de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="726e6-145">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="726e6-146">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="726e6-146">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="726e6-147">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="726e6-147">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="726e6-148">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="726e6-148">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="726e6-149">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="726e6-149">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="726e6-150">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="726e6-150">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="726e6-151">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="726e6-151">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="726e6-152">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="726e6-152">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
