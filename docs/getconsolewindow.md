---
title: GetConsoleWindow función)
description: Recupera el identificador de ventana que usa la consola asociada al proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleWindow
- wincon/GetConsoleWindow
- GetConsoleWindow
MS-HAID:
- '\_win32\_getconsolewindow'
- base.getconsolewindow
- consoles.getconsolewindow
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a5ab0b37-45ac-4413-b6ff-73876556ad38
topic_type:
- apiref
api_name:
- GetConsoleWindow
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: ead8c4216fd0d1beb2a5fa6a6acfe3f4ce20df6f
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358895"
---
# <a name="getconsolewindow-function"></a><span data-ttu-id="d80d9-104">GetConsoleWindow función)</span><span class="sxs-lookup"><span data-stu-id="d80d9-104">GetConsoleWindow function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="d80d9-105">Recupera el identificador de ventana que usa la consola asociada al proceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="d80d9-105">Retrieves the window handle used by the console associated with the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="d80d9-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d80d9-106">Syntax</span></span>

```C
HWND WINAPI GetConsoleWindow(void);
```

## <a name="parameters"></a><span data-ttu-id="d80d9-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="d80d9-107">Parameters</span></span>

<span data-ttu-id="d80d9-108">Esta función no tiene parámetros.</span><span class="sxs-lookup"><span data-stu-id="d80d9-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="d80d9-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="d80d9-109">Return value</span></span>

<span data-ttu-id="d80d9-110">El valor devuelto es un identificador de la ventana que usa la consola asociada al proceso de llamada o **null** si no existe tal consola asociada.</span><span class="sxs-lookup"><span data-stu-id="d80d9-110">The return value is a handle to the window used by the console associated with the calling process or **NULL** if there is no such associated console.</span></span>

## <a name="remarks"></a><span data-ttu-id="d80d9-111">Comentarios</span><span class="sxs-lookup"><span data-stu-id="d80d9-111">Remarks</span></span>

<span data-ttu-id="d80d9-112">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0500 o posterior.</span><span class="sxs-lookup"><span data-stu-id="d80d9-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="d80d9-113">Para obtener más información, consulte [uso de los encabezados de Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="d80d9-113">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>


[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

<span data-ttu-id="d80d9-114">En el caso de una aplicación que se hospeda dentro de una sesión de [**pseudoconsole**](pseudoconsoles.md) , esta función devuelve un identificador de ventana solo para propósitos de cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="d80d9-114">For an application that is hosted inside a [**pseudoconsole**](pseudoconsoles.md) session, this function returns a window handle for message queue purposes only.</span></span> <span data-ttu-id="d80d9-115">La ventana asociada no se muestra localmente, ya que _pseudoconsole_ está serializando todas las acciones en una secuencia para su presentación en otra ventana de terminal en otro lugar.</span><span class="sxs-lookup"><span data-stu-id="d80d9-115">The associated window is not displayed locally as the _pseudoconsole_ is serializing all actions to a stream for presentation on another terminal window elsewhere.</span></span>

## <a name="requirements"></a><span data-ttu-id="d80d9-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d80d9-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="d80d9-117">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="d80d9-117">Minimum supported client</span></span> | <span data-ttu-id="d80d9-118">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="d80d9-118">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="d80d9-119">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="d80d9-119">Minimum supported server</span></span> | <span data-ttu-id="d80d9-120">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="d80d9-120">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="d80d9-121">Encabezado</span><span class="sxs-lookup"><span data-stu-id="d80d9-121">Header</span></span> | <span data-ttu-id="d80d9-122">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d80d9-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="d80d9-123">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="d80d9-123">Library</span></span> | <span data-ttu-id="d80d9-124">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="d80d9-124">Kernel32.lib</span></span> |
| <span data-ttu-id="d80d9-125">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="d80d9-125">DLL</span></span> | <span data-ttu-id="d80d9-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d80d9-126">Kernel32.dll</span></span> |

</table>

## <a name="see-also"></a><span data-ttu-id="d80d9-127">Vea también</span><span class="sxs-lookup"><span data-stu-id="d80d9-127">See also</span></span>

[<span data-ttu-id="d80d9-128">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="d80d9-128">Console Functions</span></span>](console-functions.md)