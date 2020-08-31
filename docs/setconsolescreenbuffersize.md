---
title: SetConsoleScreenBufferSize función)
description: Vea la información de referencia sobre la función SetConsoleScreenBufferSize, que cambia el tamaño del búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleScreenBufferSize
- wincon/SetConsoleScreenBufferSize
- SetConsoleScreenBufferSize
MS-HAID:
- '\_win32\_setconsolescreenbuffersize'
- base.setconsolescreenbuffersize
- consoles.setconsolescreenbuffersize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 50bf1973-5604-42fe-bbeb-611ddc240bdd
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0e2f3a3ea11f291e88837885c6fc3e555fd39e09
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061082"
---
# <a name="setconsolescreenbuffersize-function"></a><span data-ttu-id="3e42b-104">SetConsoleScreenBufferSize función)</span><span class="sxs-lookup"><span data-stu-id="3e42b-104">SetConsoleScreenBufferSize function</span></span>


<span data-ttu-id="3e42b-105">Cambia el tamaño del búfer de pantalla de la consola especificado.</span><span class="sxs-lookup"><span data-stu-id="3e42b-105">Changes the size of the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="3e42b-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3e42b-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleScreenBufferSize(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwSize
);
```

<a name="parameters"></a><span data-ttu-id="3e42b-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3e42b-107">Parameters</span></span>
----------

<span data-ttu-id="3e42b-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="3e42b-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="3e42b-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="3e42b-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="3e42b-110">El identificador debe tener el derecho de acceso de \*\* \_ lectura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="3e42b-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="3e42b-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="3e42b-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="3e42b-112">*dwSize* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="3e42b-112">*dwSize* \[in\]</span></span>  
<span data-ttu-id="3e42b-113">Estructura de [**coordenadas**](coord-str.md) que especifica el nuevo tamaño del búfer de pantalla de la consola, en filas y columnas de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3e42b-113">A [**COORD**](coord-str.md) structure that specifies the new size of the console screen buffer, in character rows and columns.</span></span> <span data-ttu-id="3e42b-114">El ancho y el alto especificados no pueden ser menores que el ancho y el alto de la ventana del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="3e42b-114">The specified width and height cannot be less than the width and height of the console screen buffer's window.</span></span> <span data-ttu-id="3e42b-115">Las dimensiones especificadas tampoco pueden ser menores que el tamaño mínimo permitido por el sistema.</span><span class="sxs-lookup"><span data-stu-id="3e42b-115">The specified dimensions also cannot be less than the minimum size allowed by the system.</span></span> <span data-ttu-id="3e42b-116">Este mínimo depende del tamaño de la fuente actual para la consola (seleccionada por el usuario) y los valores **SM \_ CXMIN** y **SM \_ CYMIN** devueltos por la función [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) .</span><span class="sxs-lookup"><span data-stu-id="3e42b-116">This minimum depends on the current font size for the console (selected by the user) and the **SM\_CXMIN** and **SM\_CYMIN** values returned by the [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) function.</span></span>

<a name="return-value"></a><span data-ttu-id="3e42b-117">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="3e42b-117">Return value</span></span>
------------

<span data-ttu-id="3e42b-118">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="3e42b-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="3e42b-119">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="3e42b-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="3e42b-120">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="3e42b-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="3e42b-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e42b-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="3e42b-122">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="3e42b-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="3e42b-123">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="3e42b-123">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3e42b-124">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="3e42b-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="3e42b-125">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="3e42b-125">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3e42b-126">Encabezado</span><span class="sxs-lookup"><span data-stu-id="3e42b-126">Header</span></span></p></td>
<td><span data-ttu-id="3e42b-127">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="3e42b-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3e42b-128">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="3e42b-128">Library</span></span></p></td>
<td><span data-ttu-id="3e42b-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="3e42b-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3e42b-130">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="3e42b-130">DLL</span></span></p></td>
<td><span data-ttu-id="3e42b-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3e42b-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="3e42b-132"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="3e42b-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="3e42b-133">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="3e42b-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3e42b-134">Búfer de entrada de la consola</span><span class="sxs-lookup"><span data-stu-id="3e42b-134">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="3e42b-135">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="3e42b-135">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="3e42b-136">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="3e42b-136">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="3e42b-137">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="3e42b-137">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

 

 




