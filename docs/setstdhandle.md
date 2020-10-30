---
title: SetStdHandle función)
description: Establece el identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 36531872df90239e2b909c80fb75ad3011280c78
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039303"
---
# <a name="setstdhandle-function"></a><span data-ttu-id="93720-104">SetStdHandle función)</span><span class="sxs-lookup"><span data-stu-id="93720-104">SetStdHandle function</span></span>

<span data-ttu-id="93720-105">Establece el identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).</span><span class="sxs-lookup"><span data-stu-id="93720-105">Sets the handle for the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="93720-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="93720-106">Syntax</span></span>

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

## <a name="parameters"></a><span data-ttu-id="93720-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="93720-107">Parameters</span></span>

<span data-ttu-id="93720-108">*nStdHandle* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="93720-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="93720-109">El dispositivo estándar para el que se establecerá el identificador.</span><span class="sxs-lookup"><span data-stu-id="93720-109">The standard device for which the handle is to be set.</span></span> <span data-ttu-id="93720-110">Este parámetro puede ser uno de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="93720-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="93720-111">Valor</span><span class="sxs-lookup"><span data-stu-id="93720-111">Value</span></span> | <span data-ttu-id="93720-112">Significado</span><span class="sxs-lookup"><span data-stu-id="93720-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="93720-113">**STD_INPUT_HANDLE** (DWORD)-10</span><span class="sxs-lookup"><span data-stu-id="93720-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="93720-114">El dispositivo de entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="93720-114">The standard input device.</span></span> <span data-ttu-id="93720-115">Inicialmente, es el búfer de entrada de la consola, `CONIN$` .</span><span class="sxs-lookup"><span data-stu-id="93720-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="93720-116">**STD_OUTPUT_HANDLE** (DWORD)-11</span><span class="sxs-lookup"><span data-stu-id="93720-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="93720-117">El dispositivo de salida estándar.</span><span class="sxs-lookup"><span data-stu-id="93720-117">The standard output device.</span></span> <span data-ttu-id="93720-118">Inicialmente, es el búfer de pantalla de la consola activo, `CONOUT$` .</span><span class="sxs-lookup"><span data-stu-id="93720-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="93720-119">**STD_ERROR_HANDLE** (DWORD)-12</span><span class="sxs-lookup"><span data-stu-id="93720-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="93720-120">El dispositivo de error estándar.</span><span class="sxs-lookup"><span data-stu-id="93720-120">The standard error device.</span></span> <span data-ttu-id="93720-121">Inicialmente, es el búfer de pantalla de la consola activo, `CONOUT$` .</span><span class="sxs-lookup"><span data-stu-id="93720-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

<span data-ttu-id="93720-122">*hHandle* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="93720-122">*hHandle* \[in\]</span></span>  
<span data-ttu-id="93720-123">Identificador del dispositivo estándar.</span><span class="sxs-lookup"><span data-stu-id="93720-123">The handle for the standard device.</span></span>

## <a name="return-value"></a><span data-ttu-id="93720-124">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="93720-124">Return value</span></span>

<span data-ttu-id="93720-125">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="93720-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="93720-126">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="93720-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="93720-127">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="93720-127">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="93720-128">Comentarios</span><span class="sxs-lookup"><span data-stu-id="93720-128">Remarks</span></span>

<span data-ttu-id="93720-129">Es posible que los identificadores estándar de un proceso se hayan Redirigido mediante una llamada a **SetStdHandle** , en cuyo caso [**GetStdHandle**](getstdhandle.md) devolverá el identificador redirigido.</span><span class="sxs-lookup"><span data-stu-id="93720-129">The standard handles of a process may have been redirected by a call to **SetStdHandle** , in which case [**GetStdHandle**](getstdhandle.md) will return the redirected handle.</span></span> <span data-ttu-id="93720-130">Si se han redirigido los identificadores estándar, puede especificar el valor de CONIN $ en una llamada a la función [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) para obtener un identificador para el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="93720-130">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="93720-131">De forma similar, puede especificar el valor de CONOUT $ para obtener un identificador para el búfer de pantalla activo de la consola.</span><span class="sxs-lookup"><span data-stu-id="93720-131">Similarly, you can specify the CONOUT$ value to get a handle to the console's active screen buffer.</span></span>

## <a name="examples"></a><span data-ttu-id="93720-132">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="93720-132">Examples</span></span>

<span data-ttu-id="93720-133">Para obtener un ejemplo, consulte [creación de un proceso secundario con entrada y salida redirigidas](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span><span class="sxs-lookup"><span data-stu-id="93720-133">For an example, see [Creating a Child Process with Redirected Input and Output](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span></span>

## <a name="requirements"></a><span data-ttu-id="93720-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93720-134">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="93720-135">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="93720-135">Minimum supported client</span></span> | <span data-ttu-id="93720-136">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="93720-136">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="93720-137">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="93720-137">Minimum supported server</span></span> | <span data-ttu-id="93720-138">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="93720-138">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="93720-139">Encabezado</span><span class="sxs-lookup"><span data-stu-id="93720-139">Header</span></span> | <span data-ttu-id="93720-140">ProcessEnv. h (a través de Winbase. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="93720-140">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="93720-141">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="93720-141">Library</span></span> | <span data-ttu-id="93720-142">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="93720-142">Kernel32.lib</span></span> |
| <span data-ttu-id="93720-143">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="93720-143">DLL</span></span> | <span data-ttu-id="93720-144">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="93720-144">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="93720-145">Consulte también</span><span class="sxs-lookup"><span data-stu-id="93720-145">See also</span></span>

[<span data-ttu-id="93720-146">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="93720-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="93720-147">Identificadores de consola</span><span class="sxs-lookup"><span data-stu-id="93720-147">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="93720-148">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="93720-148">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="93720-149">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="93720-149">**GetStdHandle**</span></span>](getstdhandle.md)
