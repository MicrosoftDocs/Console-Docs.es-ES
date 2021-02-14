---
title: GetConsoleMode función)
description: Recupera el modo de entrada actual del búfer de entrada de una consola o el modo de salida actual de un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/GetConsoleMode
- wincon/GetConsoleMode
- GetConsoleMode
MS-HAID:
- '\_win32\_getconsolemode'
- base.getconsolemode
- consoles.getconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 49adf618-196d-4490-93ca-cd177807f58e
topic_type:
- apiref
api_name:
- GetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 3f98797b0662dadcf696f76ffda5f42e759bf930
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357294"
---
# <a name="getconsolemode-function"></a><span data-ttu-id="d77e7-104">GetConsoleMode función)</span><span class="sxs-lookup"><span data-stu-id="d77e7-104">GetConsoleMode function</span></span>

<span data-ttu-id="d77e7-105">Recupera el modo de entrada actual del búfer de entrada de una consola o el modo de salida actual de un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="d77e7-105">Retrieves the current input mode of a console's input buffer or the current output mode of a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="d77e7-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d77e7-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleMode(
  _In_  HANDLE  hConsoleHandle,
  _Out_ LPDWORD lpMode
);
```

## <a name="parameters"></a><span data-ttu-id="d77e7-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="d77e7-107">Parameters</span></span>

<span data-ttu-id="d77e7-108">*hConsoleHandle* \[in\]</span><span class="sxs-lookup"><span data-stu-id="d77e7-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="d77e7-109">Identificador para el búfer de entrada de la consola o el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="d77e7-109">A handle to the console input buffer or the console screen buffer.</span></span> <span data-ttu-id="d77e7-110">El identificador debe tener derecho de acceso de **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="d77e7-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="d77e7-111">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="d77e7-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="d77e7-112">*lpMode* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="d77e7-112">*lpMode* \[out\]</span></span>  
<span data-ttu-id="d77e7-113">Puntero a una variable que recibe el modo actual del búfer especificado.</span><span class="sxs-lookup"><span data-stu-id="d77e7-113">A pointer to a variable that receives the current mode of the specified buffer.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a><span data-ttu-id="d77e7-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="d77e7-114">Return value</span></span>

<span data-ttu-id="d77e7-115">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="d77e7-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d77e7-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="d77e7-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d77e7-117">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="d77e7-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="d77e7-118">Comentarios</span><span class="sxs-lookup"><span data-stu-id="d77e7-118">Remarks</span></span>

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

<span data-ttu-id="d77e7-119">Para cambiar los modos de e/s de una consola, llame a la función [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="d77e7-119">To change a console's I/O modes, call [**SetConsoleMode**](setconsolemode.md) function.</span></span>

## <a name="examples"></a><span data-ttu-id="d77e7-120">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="d77e7-120">Examples</span></span>

<span data-ttu-id="d77e7-121">Para un ejemplo, vea [Lectura de eventos de búfer de entrada](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="d77e7-121">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="d77e7-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d77e7-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="d77e7-123">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="d77e7-123">Minimum supported client</span></span> | <span data-ttu-id="d77e7-124">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="d77e7-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="d77e7-125">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="d77e7-125">Minimum supported server</span></span> | <span data-ttu-id="d77e7-126">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="d77e7-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="d77e7-127">Encabezado</span><span class="sxs-lookup"><span data-stu-id="d77e7-127">Header</span></span> | <span data-ttu-id="d77e7-128">ConsoleApi.h (a través de WinCon.h, incluido Windows.h)</span><span class="sxs-lookup"><span data-stu-id="d77e7-128">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="d77e7-129">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="d77e7-129">Library</span></span> | <span data-ttu-id="d77e7-130">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="d77e7-130">Kernel32.lib</span></span> |
| <span data-ttu-id="d77e7-131">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="d77e7-131">DLL</span></span> | <span data-ttu-id="d77e7-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d77e7-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="d77e7-133">Vea también</span><span class="sxs-lookup"><span data-stu-id="d77e7-133">See also</span></span>

[<span data-ttu-id="d77e7-134">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="d77e7-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d77e7-135">Modos de consola</span><span class="sxs-lookup"><span data-stu-id="d77e7-135">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="d77e7-136">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="d77e7-136">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="d77e7-137">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="d77e7-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="d77e7-138">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="d77e7-138">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="d77e7-139">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="d77e7-139">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="d77e7-140">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="d77e7-140">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="d77e7-141">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="d77e7-141">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)