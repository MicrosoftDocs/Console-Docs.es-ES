---
title: SetConsoleTextAttribute función)
description: Establece los atributos de caracteres que se escriben en el búfer de pantalla de la consola mediante la función WriteFile o WriteConsole, o que se han devuelto por la función ReadFile o ReadConsole.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleTextAttribute
- wincon/SetConsoleTextAttribute
- SetConsoleTextAttribute
MS-HAID:
- '\_win32\_setconsoletextattribute'
- base.setconsoletextattribute
- consoles.setconsoletextattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9fba5bb5-b999-4abd-ab39-7a63d58b8074
topic_type:
- apiref
api_name:
- SetConsoleTextAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 03925af2668774a36de33bfe6ea5fcdc1b475d5b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039323"
---
# <a name="setconsoletextattribute-function"></a><span data-ttu-id="81c08-104">SetConsoleTextAttribute función)</span><span class="sxs-lookup"><span data-stu-id="81c08-104">SetConsoleTextAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="81c08-105">Establece los atributos de caracteres que se escriben en el búfer de pantalla de la consola mediante la función [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md) , o que se han devuelto por la función [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="81c08-105">Sets the attributes of characters written to the console screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="81c08-106">Esta función afecta al texto escrito después de la llamada de función.</span><span class="sxs-lookup"><span data-stu-id="81c08-106">This function affects text written after the function call.</span></span>

## <a name="syntax"></a><span data-ttu-id="81c08-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="81c08-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleTextAttribute(
  _In_ HANDLE hConsoleOutput,
  _In_ WORD   wAttributes
);
```

## <a name="parameters"></a><span data-ttu-id="81c08-108">Parámetros</span><span class="sxs-lookup"><span data-stu-id="81c08-108">Parameters</span></span>

<span data-ttu-id="81c08-109">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="81c08-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="81c08-110">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="81c08-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="81c08-111">El identificador debe tener el derecho de acceso de **\_ lectura genérico** .</span><span class="sxs-lookup"><span data-stu-id="81c08-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="81c08-112">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="81c08-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="81c08-113">*wAttributes* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="81c08-113">*wAttributes* \[in\]</span></span>  
<span data-ttu-id="81c08-114">[Atributos de carácter](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="81c08-114">The [character attributes](console-screen-buffers.md#character-attributes).</span></span>

## <a name="return-value"></a><span data-ttu-id="81c08-115">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="81c08-115">Return value</span></span>

<span data-ttu-id="81c08-116">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="81c08-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="81c08-117">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="81c08-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="81c08-118">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="81c08-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="81c08-119">Comentarios</span><span class="sxs-lookup"><span data-stu-id="81c08-119">Remarks</span></span>

<span data-ttu-id="81c08-120">Para determinar los atributos de color actuales de un búfer de pantalla, llame a la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="81c08-120">To determine the current color attributes of a screen buffer, call the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

> [!TIP]
> <span data-ttu-id="81c08-121">Esta API tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente en las secuencias de **[formato de texto](console-virtual-terminal-sequences.md#text-formatting)** .</span><span class="sxs-lookup"><span data-stu-id="81c08-121">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** sequences.</span></span> <span data-ttu-id="81c08-122">Se recomiendan las _secuencias de terminal virtuales_ para todo el desarrollo nuevo y en curso.</span><span class="sxs-lookup"><span data-stu-id="81c08-122">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="81c08-123">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="81c08-123">Examples</span></span>

<span data-ttu-id="81c08-124">Para obtener un ejemplo, consulte [uso de las funciones de entrada y salida de High-Level](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="81c08-124">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="81c08-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81c08-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="81c08-126">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="81c08-126">Minimum supported client</span></span> | <span data-ttu-id="81c08-127">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="81c08-127">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="81c08-128">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="81c08-128">Minimum supported server</span></span> | <span data-ttu-id="81c08-129">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="81c08-129">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="81c08-130">Encabezado</span><span class="sxs-lookup"><span data-stu-id="81c08-130">Header</span></span> | <span data-ttu-id="81c08-131">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="81c08-131">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="81c08-132">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="81c08-132">Library</span></span> | <span data-ttu-id="81c08-133">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="81c08-133">Kernel32.lib</span></span> |
| <span data-ttu-id="81c08-134">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="81c08-134">DLL</span></span> | <span data-ttu-id="81c08-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="81c08-135">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="81c08-136">Consulte también</span><span class="sxs-lookup"><span data-stu-id="81c08-136">See also</span></span>

[<span data-ttu-id="81c08-137">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="81c08-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="81c08-138">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="81c08-138">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="81c08-139">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="81c08-139">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="81c08-140">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="81c08-140">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="81c08-141">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="81c08-141">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="81c08-142">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="81c08-142">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="81c08-143">**Escritura**</span><span class="sxs-lookup"><span data-stu-id="81c08-143">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
