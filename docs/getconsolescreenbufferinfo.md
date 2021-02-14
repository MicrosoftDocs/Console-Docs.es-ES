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
ms.openlocfilehash: 2f80f77b749fc9e9dc0aebf4507b0c41f589e40c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358915"
---
# <a name="getconsolescreenbufferinfo-function"></a><span data-ttu-id="6a6d4-104">GetConsoleScreenBufferInfo función)</span><span class="sxs-lookup"><span data-stu-id="6a6d4-104">GetConsoleScreenBufferInfo function</span></span>

<span data-ttu-id="6a6d4-105">Recupera información sobre el búfer de pantalla de la consola especificado.</span><span class="sxs-lookup"><span data-stu-id="6a6d4-105">Retrieves information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="6a6d4-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="6a6d4-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

## <a name="parameters"></a><span data-ttu-id="6a6d4-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="6a6d4-107">Parameters</span></span>

<span data-ttu-id="6a6d4-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="6a6d4-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="6a6d4-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="6a6d4-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="6a6d4-110">El identificador debe tener derecho de acceso de **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="6a6d4-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="6a6d4-111">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="6a6d4-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="6a6d4-112">*lpConsoleScreenBufferInfo* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="6a6d4-112">*lpConsoleScreenBufferInfo* \[out\]</span></span>  
<span data-ttu-id="6a6d4-113">Puntero a una estructura [**de \_ \_ \_ información del búfer de pantalla**](console-screen-buffer-info-str.md) de la consola que recibe la información del búfer de la pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="6a6d4-113">A pointer to a [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure that receives the console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="6a6d4-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="6a6d4-114">Return value</span></span>

<span data-ttu-id="6a6d4-115">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="6a6d4-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="6a6d4-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="6a6d4-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="6a6d4-117">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="6a6d4-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="6a6d4-118">Comentarios</span><span class="sxs-lookup"><span data-stu-id="6a6d4-118">Remarks</span></span>

<span data-ttu-id="6a6d4-119">El rectángulo devuelto en el miembro **srWindow** de la estructura de información de búfer de pantalla de la consola se puede modificar y, a continuación, pasar a la función [**SetConsoleWindowInfo**](setconsolewindowinfo.md) para desplazarse por el búfer de pantalla de la ventana, para cambiar el tamaño de la ventana o ambos. [**\_ \_ \_**](console-screen-buffer-info-str.md)</span><span class="sxs-lookup"><span data-stu-id="6a6d4-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="6a6d4-120">Todas las coordenadas devueltas en la estructura de [**\_ información de \_ búfer \_ de pantalla**](console-screen-buffer-info-str.md) de la consola se encuentran en coordenadas de celda de carácter, donde el origen (0,0) está en la esquina superior izquierda del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="6a6d4-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

> [!TIP]
> <span data-ttu-id="6a6d4-121">Esta API no tiene un equivalente de **[terminal virtual](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="6a6d4-121">This API does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="6a6d4-122">Es posible que su uso siga siendo necesario para las aplicaciones que intentan dibujar columnas, cuadrículas o rellenar la pantalla para recuperar el tamaño de la ventana.</span><span class="sxs-lookup"><span data-stu-id="6a6d4-122">Its use may still be required for applications that are attempting to draw columns, grids, or fill the display to retrieve the window size.</span></span> <span data-ttu-id="6a6d4-123">El estado de esta ventana se administra mediante los TTY/PTY/Pseudoconsole fuera del flujo de flujo normal y generalmente se considera un privilegio de usuario no ajustable por la aplicación cliente.</span><span class="sxs-lookup"><span data-stu-id="6a6d4-123">This window state is managed by the TTY/PTY/Pseudoconsole outside of the normal stream flow and is generally considered a user privilege not adjustable by the client application.</span></span> <span data-ttu-id="6a6d4-124">Se pueden recibir actualizaciones en [**ReadConsoleInput**](readconsoleinput.md).</span><span class="sxs-lookup"><span data-stu-id="6a6d4-124">Updates can be received on [**ReadConsoleInput**](readconsoleinput.md).</span></span>

## <a name="examples"></a><span data-ttu-id="6a6d4-125">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="6a6d4-125">Examples</span></span>

<span data-ttu-id="6a6d4-126">Para obtener un ejemplo, vea [desplazarse por la ventana de un búfer de pantalla](scrolling-a-screen-buffer-s-window.md).</span><span class="sxs-lookup"><span data-stu-id="6a6d4-126">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="6a6d4-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6a6d4-127">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="6a6d4-128">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="6a6d4-128">Minimum supported client</span></span> | <span data-ttu-id="6a6d4-129">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="6a6d4-129">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="6a6d4-130">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="6a6d4-130">Minimum supported server</span></span> | <span data-ttu-id="6a6d4-131">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="6a6d4-131">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="6a6d4-132">Encabezado</span><span class="sxs-lookup"><span data-stu-id="6a6d4-132">Header</span></span> | <span data-ttu-id="6a6d4-133">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6a6d4-133">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="6a6d4-134">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="6a6d4-134">Library</span></span> | <span data-ttu-id="6a6d4-135">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="6a6d4-135">Kernel32.lib</span></span> |
| <span data-ttu-id="6a6d4-136">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="6a6d4-136">DLL</span></span> | <span data-ttu-id="6a6d4-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6a6d4-137">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="6a6d4-138">Vea también</span><span class="sxs-lookup"><span data-stu-id="6a6d4-138">See also</span></span>

[<span data-ttu-id="6a6d4-139">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="6a6d4-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="6a6d4-140">**\_información del \_ búfer de pantalla de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="6a6d4-140">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="6a6d4-141">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="6a6d4-141">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="6a6d4-142">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="6a6d4-142">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="6a6d4-143">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="6a6d4-143">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="6a6d4-144">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="6a6d4-144">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="6a6d4-145">Tamaño de búfer de ventana y pantalla</span><span class="sxs-lookup"><span data-stu-id="6a6d4-145">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)