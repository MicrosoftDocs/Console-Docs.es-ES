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
ms.openlocfilehash: 317acd84289e5138e1a947251e745077ba581083
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358515"
---
# <a name="setstdhandle-function"></a><span data-ttu-id="872a7-104">SetStdHandle función)</span><span class="sxs-lookup"><span data-stu-id="872a7-104">SetStdHandle function</span></span>

<span data-ttu-id="872a7-105">Establece el identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).</span><span class="sxs-lookup"><span data-stu-id="872a7-105">Sets the handle for the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="872a7-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="872a7-106">Syntax</span></span>

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

## <a name="parameters"></a><span data-ttu-id="872a7-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="872a7-107">Parameters</span></span>

<span data-ttu-id="872a7-108">*nStdHandle* \[in\]</span><span class="sxs-lookup"><span data-stu-id="872a7-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="872a7-109">El dispositivo estándar para el que se establecerá el identificador.</span><span class="sxs-lookup"><span data-stu-id="872a7-109">The standard device for which the handle is to be set.</span></span> <span data-ttu-id="872a7-110">Este parámetro puede ser uno de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="872a7-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="872a7-111">Valor</span><span class="sxs-lookup"><span data-stu-id="872a7-111">Value</span></span> | <span data-ttu-id="872a7-112">Significado</span><span class="sxs-lookup"><span data-stu-id="872a7-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="872a7-113">**STD_INPUT_HANDLE** (DWORD) -10</span><span class="sxs-lookup"><span data-stu-id="872a7-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="872a7-114">El dispositivo de entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="872a7-114">The standard input device.</span></span> <span data-ttu-id="872a7-115">Inicialmente, es el búfer de entrada de la consola, `CONIN$`.</span><span class="sxs-lookup"><span data-stu-id="872a7-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="872a7-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span><span class="sxs-lookup"><span data-stu-id="872a7-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="872a7-117">El dispositivo de salida estándar.</span><span class="sxs-lookup"><span data-stu-id="872a7-117">The standard output device.</span></span> <span data-ttu-id="872a7-118">Inicialmente, es el búfer de pantalla activo de la consola, `CONOUT$`.</span><span class="sxs-lookup"><span data-stu-id="872a7-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="872a7-119">**STD_ERROR_HANDLE** (DWORD) -12</span><span class="sxs-lookup"><span data-stu-id="872a7-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="872a7-120">El dispositivo de error estándar.</span><span class="sxs-lookup"><span data-stu-id="872a7-120">The standard error device.</span></span> <span data-ttu-id="872a7-121">Inicialmente, es el búfer de pantalla activo de la consola, `CONOUT$`.</span><span class="sxs-lookup"><span data-stu-id="872a7-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

<span data-ttu-id="872a7-122">*hHandle* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="872a7-122">*hHandle* \[in\]</span></span>  
<span data-ttu-id="872a7-123">Identificador del dispositivo estándar.</span><span class="sxs-lookup"><span data-stu-id="872a7-123">The handle for the standard device.</span></span>

## <a name="return-value"></a><span data-ttu-id="872a7-124">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="872a7-124">Return value</span></span>

<span data-ttu-id="872a7-125">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="872a7-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="872a7-126">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="872a7-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="872a7-127">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="872a7-127">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="872a7-128">Comentarios</span><span class="sxs-lookup"><span data-stu-id="872a7-128">Remarks</span></span>

<span data-ttu-id="872a7-129">Es posible que los identificadores estándar de un proceso se hayan Redirigido mediante una llamada a **SetStdHandle**, en cuyo caso [**GetStdHandle**](getstdhandle.md) devolverá el identificador redirigido.</span><span class="sxs-lookup"><span data-stu-id="872a7-129">The standard handles of a process may have been redirected by a call to **SetStdHandle**, in which case [**GetStdHandle**](getstdhandle.md) will return the redirected handle.</span></span> <span data-ttu-id="872a7-130">Si se han redirigido los identificadores estándar, puede especificar el valor de CONIN $ en una llamada a la función [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) para obtener un identificador para el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="872a7-130">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="872a7-131">De forma similar, puede especificar el valor de CONOUT $ para obtener un identificador para el búfer de pantalla activo de la consola.</span><span class="sxs-lookup"><span data-stu-id="872a7-131">Similarly, you can specify the CONOUT$ value to get a handle to the console's active screen buffer.</span></span>

## <a name="examples"></a><span data-ttu-id="872a7-132">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="872a7-132">Examples</span></span>

<span data-ttu-id="872a7-133">Para obtener un ejemplo, consulte [creación de un proceso secundario con entrada y salida redirigidas](/windows/win32/procthread/creating-a-child-process-with-redirected-input-and-output).</span><span class="sxs-lookup"><span data-stu-id="872a7-133">For an example, see [Creating a Child Process with Redirected Input and Output](/windows/win32/procthread/creating-a-child-process-with-redirected-input-and-output).</span></span>

## <a name="requirements"></a><span data-ttu-id="872a7-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="872a7-134">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="872a7-135">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="872a7-135">Minimum supported client</span></span> | <span data-ttu-id="872a7-136">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="872a7-136">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="872a7-137">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="872a7-137">Minimum supported server</span></span> | <span data-ttu-id="872a7-138">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="872a7-138">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="872a7-139">Encabezado</span><span class="sxs-lookup"><span data-stu-id="872a7-139">Header</span></span> | <span data-ttu-id="872a7-140">ProcessEnv.h (via Winbase.h, include Windows.h)</span><span class="sxs-lookup"><span data-stu-id="872a7-140">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="872a7-141">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="872a7-141">Library</span></span> | <span data-ttu-id="872a7-142">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="872a7-142">Kernel32.lib</span></span> |
| <span data-ttu-id="872a7-143">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="872a7-143">DLL</span></span> | <span data-ttu-id="872a7-144">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="872a7-144">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="872a7-145">Vea también</span><span class="sxs-lookup"><span data-stu-id="872a7-145">See also</span></span>

[<span data-ttu-id="872a7-146">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="872a7-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="872a7-147">Identificadores de consola</span><span class="sxs-lookup"><span data-stu-id="872a7-147">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="872a7-148">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="872a7-148">**CreateFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-createfilea)

[<span data-ttu-id="872a7-149">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="872a7-149">**GetStdHandle**</span></span>](getstdhandle.md)