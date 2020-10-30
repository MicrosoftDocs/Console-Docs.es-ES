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
ms.openlocfilehash: c74fe1a29b9ba2ea721e874eb624ea2f8517094c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038813"
---
# <a name="getconsolewindow-function"></a><span data-ttu-id="27a04-104">GetConsoleWindow función)</span><span class="sxs-lookup"><span data-stu-id="27a04-104">GetConsoleWindow function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="27a04-105">Recupera el identificador de ventana que usa la consola asociada al proceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="27a04-105">Retrieves the window handle used by the console associated with the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="27a04-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="27a04-106">Syntax</span></span>

```C
HWND WINAPI GetConsoleWindow(void);
```

## <a name="parameters"></a><span data-ttu-id="27a04-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27a04-107">Parameters</span></span>

<span data-ttu-id="27a04-108">Esta función no tiene parámetros.</span><span class="sxs-lookup"><span data-stu-id="27a04-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="27a04-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="27a04-109">Return value</span></span>

<span data-ttu-id="27a04-110">El valor devuelto es un identificador de la ventana que usa la consola asociada al proceso de llamada o **null** si no existe tal consola asociada.</span><span class="sxs-lookup"><span data-stu-id="27a04-110">The return value is a handle to the window used by the console associated with the calling process or **NULL** if there is no such associated console.</span></span>

## <a name="remarks"></a><span data-ttu-id="27a04-111">Comentarios</span><span class="sxs-lookup"><span data-stu-id="27a04-111">Remarks</span></span>

<span data-ttu-id="27a04-112">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0500 o posterior.</span><span class="sxs-lookup"><span data-stu-id="27a04-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="27a04-113">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="27a04-113">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>


[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

<span data-ttu-id="27a04-114">En el caso de una aplicación que se hospeda dentro de una sesión de [**pseudoconsole**](pseudoconsoles.md) , esta función devuelve un identificador de ventana solo para propósitos de cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="27a04-114">For an application that is hosted inside a [**pseudoconsole**](pseudoconsoles.md) session, this function returns a window handle for message queue purposes only.</span></span> <span data-ttu-id="27a04-115">La ventana asociada no se muestra localmente, ya que _pseudoconsole_ está serializando todas las acciones en una secuencia para su presentación en otra ventana de terminal en otro lugar.</span><span class="sxs-lookup"><span data-stu-id="27a04-115">The associated window is not displayed locally as the _pseudoconsole_ is serializing all actions to a stream for presentation on another terminal window elsewhere.</span></span>

## <a name="requirements"></a><span data-ttu-id="27a04-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27a04-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="27a04-117">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="27a04-117">Minimum supported client</span></span> | <span data-ttu-id="27a04-118">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="27a04-118">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="27a04-119">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="27a04-119">Minimum supported server</span></span> | <span data-ttu-id="27a04-120">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="27a04-120">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="27a04-121">Encabezado</span><span class="sxs-lookup"><span data-stu-id="27a04-121">Header</span></span> | <span data-ttu-id="27a04-122">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="27a04-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="27a04-123">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="27a04-123">Library</span></span> | <span data-ttu-id="27a04-124">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="27a04-124">Kernel32.lib</span></span> |
| <span data-ttu-id="27a04-125">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="27a04-125">DLL</span></span> | <span data-ttu-id="27a04-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="27a04-126">Kernel32.dll</span></span> |

</table>

## <a name="see-also"></a><span data-ttu-id="27a04-127">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27a04-127">See also</span></span>

[<span data-ttu-id="27a04-128">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="27a04-128">Console Functions</span></span>](console-functions.md)
