---
title: GetConsoleScreenBufferInfo función)
description: Vea la información de referencia sobre la función GetConsoleScreenBufferInfo, que recupera información sobre el búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfo
- wincon/GetConsoleScreenBufferInfo
- GetConsoleScreenBufferInfo
ms.assetid: eafe819e-a99a-4ce1-8898-8860444a31af
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 8ced380982705647b7944cee0f72c723c38776c3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060664"
---
# <a name="getconsolescreenbufferinfo-function"></a><span data-ttu-id="6b91e-104">GetConsoleScreenBufferInfo función)</span><span class="sxs-lookup"><span data-stu-id="6b91e-104">GetConsoleScreenBufferInfo function</span></span>


<span data-ttu-id="6b91e-105">Recupera información sobre el búfer de pantalla de la consola especificado.</span><span class="sxs-lookup"><span data-stu-id="6b91e-105">Retrieves information about the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="6b91e-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="6b91e-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

<a name="parameters"></a><span data-ttu-id="6b91e-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="6b91e-107">Parameters</span></span>
----------

<span data-ttu-id="6b91e-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="6b91e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="6b91e-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="6b91e-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="6b91e-110">El identificador debe tener el derecho de acceso de \*\* \_ lectura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="6b91e-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="6b91e-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="6b91e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="6b91e-112">*lpConsoleScreenBufferInfo* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="6b91e-112">*lpConsoleScreenBufferInfo* \[out\]</span></span>  
<span data-ttu-id="6b91e-113">Puntero a una estructura [**de \_ \_ \_ información del búfer de pantalla**](console-screen-buffer-info-str.md) de la consola que recibe la información del búfer de la pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="6b91e-113">A pointer to a [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure that receives the console screen buffer information.</span></span>

<a name="return-value"></a><span data-ttu-id="6b91e-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="6b91e-114">Return value</span></span>
------------

<span data-ttu-id="6b91e-115">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="6b91e-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="6b91e-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="6b91e-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="6b91e-117">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="6b91e-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="6b91e-118">Observaciones</span><span class="sxs-lookup"><span data-stu-id="6b91e-118">Remarks</span></span>
-------

<span data-ttu-id="6b91e-119">El rectángulo devuelto en el miembro **srWindow** de la estructura de información de búfer de pantalla de la consola se puede modificar y, a continuación, pasar a la función [**SetConsoleWindowInfo**](setconsolewindowinfo.md) para desplazarse por el búfer de pantalla de la ventana, para cambiar el tamaño de la ventana o ambos. [\*\* \_ \_ \_ \*\*](console-screen-buffer-info-str.md)</span><span class="sxs-lookup"><span data-stu-id="6b91e-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="6b91e-120">Todas las coordenadas devueltas en la estructura de [\*\* \_ información de \_ búfer \_ de pantalla\*\*](console-screen-buffer-info-str.md) de la consola se encuentran en coordenadas de celda de carácter, donde el origen (0,0) está en la esquina superior izquierda del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="6b91e-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

<a name="examples"></a><span data-ttu-id="6b91e-121">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="6b91e-121">Examples</span></span>
--------

<span data-ttu-id="6b91e-122">Para obtener un ejemplo, vea [desplazarse por la ventana de un búfer de pantalla](scrolling-a-screen-buffer-s-window.md).</span><span class="sxs-lookup"><span data-stu-id="6b91e-122">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

<a name="requirements"></a><span data-ttu-id="6b91e-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6b91e-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="6b91e-124">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="6b91e-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="6b91e-125">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="6b91e-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6b91e-126">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="6b91e-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="6b91e-127">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="6b91e-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6b91e-128">Encabezado</span><span class="sxs-lookup"><span data-stu-id="6b91e-128">Header</span></span></p></td>
<td><span data-ttu-id="6b91e-129">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6b91e-129">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6b91e-130">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="6b91e-130">Library</span></span></p></td>
<td><span data-ttu-id="6b91e-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="6b91e-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6b91e-132">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="6b91e-132">DLL</span></span></p></td>
<td><span data-ttu-id="6b91e-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6b91e-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="6b91e-134"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="6b91e-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="6b91e-135">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="6b91e-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="6b91e-136">**\_información del \_ búfer de pantalla de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="6b91e-136">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="6b91e-137">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="6b91e-137">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="6b91e-138">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="6b91e-138">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="6b91e-139">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="6b91e-139">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="6b91e-140">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="6b91e-140">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="6b91e-141">Tamaño de búfer de ventana y pantalla</span><span class="sxs-lookup"><span data-stu-id="6b91e-141">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)

 

 




