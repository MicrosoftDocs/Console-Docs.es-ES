---
title: AllocConsole función)
description: Consulte la información de referencia sobre la función AllocConsole, que asigna una nueva consola para el proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/AllocConsole
- wincon/AllocConsole
- AllocConsole
MS-HAID:
- '\_win32\_allocconsole'
- base.allocconsole
- consoles.allocconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bdf3bf2f-8eb8-4ba6-bf3a-a67b29dffda2
topic_type:
- apiref
api_name:
- AllocConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: db010f60f1661d67e77de841fc243c24f32e2d1f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037513"
---
# <a name="allocconsole-function"></a><span data-ttu-id="dbc01-104">AllocConsole función)</span><span class="sxs-lookup"><span data-stu-id="dbc01-104">AllocConsole function</span></span>

<span data-ttu-id="dbc01-105">Asigna una nueva consola para el proceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="dbc01-105">Allocates a new console for the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="dbc01-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="dbc01-106">Syntax</span></span>

```C
BOOL WINAPI AllocConsole(void);
```

## <a name="parameters"></a><span data-ttu-id="dbc01-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="dbc01-107">Parameters</span></span>

<span data-ttu-id="dbc01-108">Esta función no tiene parámetros.</span><span class="sxs-lookup"><span data-stu-id="dbc01-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="dbc01-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="dbc01-109">Return value</span></span>

<span data-ttu-id="dbc01-110">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="dbc01-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="dbc01-111">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="dbc01-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="dbc01-112">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="dbc01-112">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="dbc01-113">Comentarios</span><span class="sxs-lookup"><span data-stu-id="dbc01-113">Remarks</span></span>

<span data-ttu-id="dbc01-114">Un proceso solo se puede asociar a una consola, por lo que se produce un error en la función **AllocConsole** si el proceso de llamada ya tiene una consola.</span><span class="sxs-lookup"><span data-stu-id="dbc01-114">A process can be associated with only one console, so the **AllocConsole** function fails if the calling process already has a console.</span></span> <span data-ttu-id="dbc01-115">Un proceso puede usar la función [**FreeConsole**](freeconsole.md) para desasociarse de su consola actual y, después, puede llamar a **AllocConsole** para crear una nueva consola o [**AttachConsole**](attachconsole.md) para adjuntar a otra consola.</span><span class="sxs-lookup"><span data-stu-id="dbc01-115">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its current console, then it can call **AllocConsole** to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<span data-ttu-id="dbc01-116">Si el proceso de llamada crea un proceso secundario, el elemento secundario hereda la nueva consola.</span><span class="sxs-lookup"><span data-stu-id="dbc01-116">If the calling process creates a child process, the child inherits the new console.</span></span>

<span data-ttu-id="dbc01-117">**AllocConsole** inicializa la entrada estándar, la salida estándar y los identificadores de error estándar para la nueva consola.</span><span class="sxs-lookup"><span data-stu-id="dbc01-117">**AllocConsole** initializes standard input, standard output, and standard error handles for the new console.</span></span> <span data-ttu-id="dbc01-118">El identificador de entrada estándar es un identificador del búfer de entrada de la consola, y los identificadores de salida estándar y de error estándar son identificadores del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="dbc01-118">The standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles to the console's screen buffer.</span></span> <span data-ttu-id="dbc01-119">Para recuperar estos identificadores, use la función [**GetStdHandle**](getstdhandle.md) .</span><span class="sxs-lookup"><span data-stu-id="dbc01-119">To retrieve these handles, use the [**GetStdHandle**](getstdhandle.md) function.</span></span>

<span data-ttu-id="dbc01-120">Esta función se usa principalmente en una aplicación de interfaz gráfica de usuario (GUI) para crear una ventana de consola.</span><span class="sxs-lookup"><span data-stu-id="dbc01-120">This function is primarily used by a graphical user interface (GUI) application to create a console window.</span></span> <span data-ttu-id="dbc01-121">Las aplicaciones de GUI se inicializan sin una consola de.</span><span class="sxs-lookup"><span data-stu-id="dbc01-121">GUI applications are initialized without a console.</span></span> <span data-ttu-id="dbc01-122">Las aplicaciones de consola se inicializan con una consola de, a menos que se creen como procesos desasociados (llamando a la función [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) con la marca de **\_ proceso separado** ).</span><span class="sxs-lookup"><span data-stu-id="dbc01-122">Console applications are initialized with a console, unless they are created as detached processes (by calling the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function with the **DETACHED\_PROCESS** flag).</span></span>

## <a name="requirements"></a><span data-ttu-id="dbc01-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dbc01-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="dbc01-124">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="dbc01-124">Minimum supported client</span></span> | <span data-ttu-id="dbc01-125">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="dbc01-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="dbc01-126">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="dbc01-126">Minimum supported server</span></span> | <span data-ttu-id="dbc01-127">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="dbc01-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="dbc01-128">Encabezado</span><span class="sxs-lookup"><span data-stu-id="dbc01-128">Header</span></span> | <span data-ttu-id="dbc01-129">ConsoleApi. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="dbc01-129">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="dbc01-130">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="dbc01-130">Library</span></span> | <span data-ttu-id="dbc01-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="dbc01-131">Kernel32.lib</span></span> |
| <span data-ttu-id="dbc01-132">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="dbc01-132">DLL</span></span> | <span data-ttu-id="dbc01-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="dbc01-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="dbc01-134">Consulte también</span><span class="sxs-lookup"><span data-stu-id="dbc01-134">See also</span></span>

[<span data-ttu-id="dbc01-135">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="dbc01-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="dbc01-136">Consolas</span><span class="sxs-lookup"><span data-stu-id="dbc01-136">Consoles</span></span>](consoles.md)

[<span data-ttu-id="dbc01-137">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="dbc01-137">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="dbc01-138">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="dbc01-138">**CreateProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[<span data-ttu-id="dbc01-139">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="dbc01-139">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="dbc01-140">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="dbc01-140">**GetStdHandle**</span></span>](getstdhandle.md)
