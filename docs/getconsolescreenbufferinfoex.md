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
ms.openlocfilehash: 482aaefbeed22475f6f9301d13f480ba5a416fa9
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358905"
---
# <a name="getconsolescreenbufferinfoex-function"></a><span data-ttu-id="c3ddb-104">GetConsoleScreenBufferInfoEx función)</span><span class="sxs-lookup"><span data-stu-id="c3ddb-104">GetConsoleScreenBufferInfoEx function</span></span>

<span data-ttu-id="c3ddb-105">Recupera información extendida sobre el búfer de pantalla de la consola especificado.</span><span class="sxs-lookup"><span data-stu-id="c3ddb-105">Retrieves extended information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="c3ddb-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c3ddb-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleScreenBufferInfoEx(
  _In_  HANDLE                        hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a><span data-ttu-id="c3ddb-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="c3ddb-107">Parameters</span></span>

<span data-ttu-id="c3ddb-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c3ddb-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="c3ddb-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="c3ddb-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="c3ddb-110">El identificador debe tener derecho de acceso de **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="c3ddb-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="c3ddb-111">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="c3ddb-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="c3ddb-112">*lpConsoleScreenBufferInfoEx* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="c3ddb-112">*lpConsoleScreenBufferInfoEx* \[out\]</span></span>  
<span data-ttu-id="c3ddb-113">Una [**estructura \_ \_ \_ INFOEX de búfer de pantalla**](console-screen-buffer-infoex.md) de la consola que recibe la información de búfer de pantalla solicitada.</span><span class="sxs-lookup"><span data-stu-id="c3ddb-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that receives the requested console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="c3ddb-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="c3ddb-114">Return value</span></span>

<span data-ttu-id="c3ddb-115">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="c3ddb-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c3ddb-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="c3ddb-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c3ddb-117">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="c3ddb-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="c3ddb-118">Comentarios</span><span class="sxs-lookup"><span data-stu-id="c3ddb-118">Remarks</span></span>

<span data-ttu-id="c3ddb-119">El rectángulo devuelto en el miembro **srWindow** de la estructura de [**búfer de \_ pantalla \_ \_ INFOEX**](console-screen-buffer-infoex.md) se puede modificar y, a continuación, pasar a la función [**SetConsoleWindowInfo**](setconsolewindowinfo.md) para desplazarse por el búfer de pantalla de la ventana, para cambiar el tamaño de la ventana o ambos.</span><span class="sxs-lookup"><span data-stu-id="c3ddb-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="c3ddb-120">Todas las coordenadas devueltas en la estructura [**\_ INFOEX del \_ búfer \_ de pantalla**](console-screen-buffer-infoex.md) de la consola se encuentran en coordenadas de celda de caracteres, donde el origen (0,0) está en la esquina superior izquierda del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="c3ddb-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

> [!TIP]
> <span data-ttu-id="c3ddb-121">Esta API no tiene un equivalente de **[terminal virtual](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="c3ddb-121">This API does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="c3ddb-122">Es posible que su uso siga siendo necesario para las aplicaciones que intentan dibujar columnas, cuadrículas o rellenar la pantalla para recuperar el tamaño de la ventana.</span><span class="sxs-lookup"><span data-stu-id="c3ddb-122">Its use may still be required for applications that are attempting to draw columns, grids, or fill the display to retrieve the window size.</span></span> <span data-ttu-id="c3ddb-123">El estado de esta ventana se administra mediante los TTY/PTY/Pseudoconsole fuera del flujo de flujo normal y generalmente se considera un privilegio de usuario no ajustable por la aplicación cliente.</span><span class="sxs-lookup"><span data-stu-id="c3ddb-123">This window state is managed by the TTY/PTY/Pseudoconsole outside of the normal stream flow and is generally considered a user privilege not adjustable by the client application.</span></span> <span data-ttu-id="c3ddb-124">Se pueden recibir actualizaciones en [**ReadConsoleInput**](readconsoleinput.md).</span><span class="sxs-lookup"><span data-stu-id="c3ddb-124">Updates can be received on [**ReadConsoleInput**](readconsoleinput.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="c3ddb-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3ddb-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c3ddb-126">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="c3ddb-126">Minimum supported client</span></span> | <span data-ttu-id="c3ddb-127">Solo aplicaciones de escritorio de Windows Vista \[\]</span><span class="sxs-lookup"><span data-stu-id="c3ddb-127">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="c3ddb-128">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="c3ddb-128">Minimum supported server</span></span> | <span data-ttu-id="c3ddb-129">Solo aplicaciones de escritorio de Windows Server 2008 \[\]</span><span class="sxs-lookup"><span data-stu-id="c3ddb-129">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="c3ddb-130">Encabezado</span><span class="sxs-lookup"><span data-stu-id="c3ddb-130">Header</span></span> | <span data-ttu-id="c3ddb-131">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c3ddb-131">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c3ddb-132">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="c3ddb-132">Library</span></span> | <span data-ttu-id="c3ddb-133">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="c3ddb-133">Kernel32.lib</span></span> |
| <span data-ttu-id="c3ddb-134">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="c3ddb-134">DLL</span></span> | <span data-ttu-id="c3ddb-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c3ddb-135">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="c3ddb-136">Vea también</span><span class="sxs-lookup"><span data-stu-id="c3ddb-136">See also</span></span>

[<span data-ttu-id="c3ddb-137">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="c3ddb-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c3ddb-138">**búfer de pantalla de la consola \_ \_ \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="c3ddb-138">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="c3ddb-139">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="c3ddb-139">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)