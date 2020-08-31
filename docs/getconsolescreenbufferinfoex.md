---
title: GetConsoleScreenBufferInfoEx función)
description: Recupera información extendida sobre el búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfoEx
- wincon/GetConsoleScreenBufferInfoEx
- GetConsoleScreenBufferInfoEx
MS-HAID:
- base.getconsolescreenbufferinfoex
- consoles.getconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 60534226-d26f-44e2-a4cc-64811882e308
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 69cb3c59af1a93cf6af664bbecaf05ef00b64ce8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060680"
---
# <a name="getconsolescreenbufferinfoex-function"></a><span data-ttu-id="71204-104">GetConsoleScreenBufferInfoEx función)</span><span class="sxs-lookup"><span data-stu-id="71204-104">GetConsoleScreenBufferInfoEx function</span></span>


<span data-ttu-id="71204-105">Recupera información extendida sobre el búfer de pantalla de la consola especificado.</span><span class="sxs-lookup"><span data-stu-id="71204-105">Retrieves extended information about the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="71204-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="71204-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleScreenBufferInfoEx(
  _In_  HANDLE                        hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

<a name="parameters"></a><span data-ttu-id="71204-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="71204-107">Parameters</span></span>
----------

<span data-ttu-id="71204-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="71204-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="71204-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="71204-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="71204-110">El identificador debe tener el derecho de acceso de \*\* \_ lectura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="71204-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="71204-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="71204-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="71204-112">*lpConsoleScreenBufferInfoEx* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="71204-112">*lpConsoleScreenBufferInfoEx* \[out\]</span></span>  
<span data-ttu-id="71204-113">Una [**estructura \_ \_ \_ INFOEX de búfer de pantalla**](console-screen-buffer-infoex.md) de la consola que recibe la información de búfer de pantalla solicitada.</span><span class="sxs-lookup"><span data-stu-id="71204-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that receives the requested console screen buffer information.</span></span>

<a name="return-value"></a><span data-ttu-id="71204-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="71204-114">Return value</span></span>
------------

<span data-ttu-id="71204-115">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="71204-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="71204-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="71204-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="71204-117">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="71204-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="71204-118">Observaciones</span><span class="sxs-lookup"><span data-stu-id="71204-118">Remarks</span></span>
-------

<span data-ttu-id="71204-119">El rectángulo devuelto en el miembro **srWindow** de la estructura de [**búfer de \_ pantalla \_ \_ INFOEX**](console-screen-buffer-infoex.md) se puede modificar y, a continuación, pasar a la función [**SetConsoleWindowInfo**](setconsolewindowinfo.md) para desplazarse por el búfer de pantalla de la ventana, para cambiar el tamaño de la ventana o ambos.</span><span class="sxs-lookup"><span data-stu-id="71204-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="71204-120">Todas las coordenadas devueltas en la estructura [\*\* \_ INFOEX del \_ búfer \_ de pantalla\*\*](console-screen-buffer-infoex.md) de la consola se encuentran en coordenadas de celda de caracteres, donde el origen (0,0) está en la esquina superior izquierda del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="71204-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

<a name="requirements"></a><span data-ttu-id="71204-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="71204-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="71204-122">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="71204-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="71204-123">Windows Vista [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="71204-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="71204-124">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="71204-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="71204-125">Windows Server 2008 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="71204-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="71204-126">Encabezado</span><span class="sxs-lookup"><span data-stu-id="71204-126">Header</span></span></p></td>
<td><span data-ttu-id="71204-127">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="71204-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="71204-128">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="71204-128">Library</span></span></p></td>
<td><span data-ttu-id="71204-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="71204-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="71204-130">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="71204-130">DLL</span></span></p></td>
<td><span data-ttu-id="71204-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="71204-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="71204-132"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="71204-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="71204-133">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="71204-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="71204-134">**búfer de pantalla de la consola \_ \_ \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="71204-134">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="71204-135">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="71204-135">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)

 

 




