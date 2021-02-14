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
ms.openlocfilehash: b08f4b0b628f4d20029b81873b4fc25077a11029
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358565"
---
# <a name="setconsoletextattribute-function"></a><span data-ttu-id="61896-104">SetConsoleTextAttribute función)</span><span class="sxs-lookup"><span data-stu-id="61896-104">SetConsoleTextAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="61896-105">Establece los atributos de caracteres que se escriben en el búfer de pantalla de la consola mediante la función [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) o [**WriteConsole**](writeconsole.md) , o que se han devuelto por la función [**readfile**](/windows/win32/api/fileapi/nf-fileapi-readfile) o [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="61896-105">Sets the attributes of characters written to the console screen buffer by the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) or [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="61896-106">Esta función afecta al texto escrito después de la llamada de función.</span><span class="sxs-lookup"><span data-stu-id="61896-106">This function affects text written after the function call.</span></span>

## <a name="syntax"></a><span data-ttu-id="61896-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="61896-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleTextAttribute(
  _In_ HANDLE hConsoleOutput,
  _In_ WORD   wAttributes
);
```

## <a name="parameters"></a><span data-ttu-id="61896-108">Parámetros</span><span class="sxs-lookup"><span data-stu-id="61896-108">Parameters</span></span>

<span data-ttu-id="61896-109">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="61896-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="61896-110">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="61896-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="61896-111">El identificador debe tener derecho de acceso de **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="61896-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="61896-112">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="61896-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="61896-113">*wAttributes* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="61896-113">*wAttributes* \[in\]</span></span>  
<span data-ttu-id="61896-114">[Atributos de carácter](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="61896-114">The [character attributes](console-screen-buffers.md#character-attributes).</span></span>

## <a name="return-value"></a><span data-ttu-id="61896-115">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="61896-115">Return value</span></span>

<span data-ttu-id="61896-116">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="61896-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="61896-117">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="61896-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="61896-118">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="61896-118">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="61896-119">Comentarios</span><span class="sxs-lookup"><span data-stu-id="61896-119">Remarks</span></span>

<span data-ttu-id="61896-120">Para determinar los atributos de color actuales de un búfer de pantalla, llame a la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="61896-120">To determine the current color attributes of a screen buffer, call the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

> [!TIP]
> <span data-ttu-id="61896-121">Esta API tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente en las secuencias de **[formato de texto](console-virtual-terminal-sequences.md#text-formatting)** .</span><span class="sxs-lookup"><span data-stu-id="61896-121">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** sequences.</span></span> <span data-ttu-id="61896-122">Se recomiendan las _secuencias de terminal virtuales_ para todo el desarrollo nuevo y en curso.</span><span class="sxs-lookup"><span data-stu-id="61896-122">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="61896-123">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="61896-123">Examples</span></span>

<span data-ttu-id="61896-124">Para obtener un ejemplo, consulte [uso de las funciones de entrada y salida de High-Level](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="61896-124">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="61896-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61896-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="61896-126">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="61896-126">Minimum supported client</span></span> | <span data-ttu-id="61896-127">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="61896-127">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="61896-128">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="61896-128">Minimum supported server</span></span> | <span data-ttu-id="61896-129">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="61896-129">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="61896-130">Encabezado</span><span class="sxs-lookup"><span data-stu-id="61896-130">Header</span></span> | <span data-ttu-id="61896-131">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="61896-131">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="61896-132">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="61896-132">Library</span></span> | <span data-ttu-id="61896-133">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="61896-133">Kernel32.lib</span></span> |
| <span data-ttu-id="61896-134">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="61896-134">DLL</span></span> | <span data-ttu-id="61896-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="61896-135">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="61896-136">Vea también</span><span class="sxs-lookup"><span data-stu-id="61896-136">See also</span></span>

[<span data-ttu-id="61896-137">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="61896-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="61896-138">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="61896-138">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="61896-139">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="61896-139">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="61896-140">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="61896-140">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="61896-141">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="61896-141">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="61896-142">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="61896-142">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="61896-143">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="61896-143">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)