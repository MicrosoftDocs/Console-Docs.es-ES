---
title: Función AllocConsole
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
ms.localizationpriority: high
ms.openlocfilehash: c63c9a176c0d8ca2ef4342f7bee1b427eae00014
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420174"
---
# <a name="allocconsole-function"></a><span data-ttu-id="fb68f-104">Función AllocConsole</span><span class="sxs-lookup"><span data-stu-id="fb68f-104">AllocConsole function</span></span>

<span data-ttu-id="fb68f-105">Asigna una nueva consola para el proceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="fb68f-105">Allocates a new console for the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="fb68f-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fb68f-106">Syntax</span></span>

```C
BOOL WINAPI AllocConsole(void);
```

## <a name="parameters"></a><span data-ttu-id="fb68f-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="fb68f-107">Parameters</span></span>

<span data-ttu-id="fb68f-108">Esta función no tiene parámetros.</span><span class="sxs-lookup"><span data-stu-id="fb68f-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="fb68f-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="fb68f-109">Return value</span></span>

<span data-ttu-id="fb68f-110">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="fb68f-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="fb68f-111">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="fb68f-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="fb68f-112">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="fb68f-112">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="fb68f-113">Comentarios</span><span class="sxs-lookup"><span data-stu-id="fb68f-113">Remarks</span></span>

<span data-ttu-id="fb68f-114">Un proceso se puede asociar solo a una consola, por lo que se produce un error en la función **AllocConsole** si el proceso de llamada ya tiene una consola.</span><span class="sxs-lookup"><span data-stu-id="fb68f-114">A process can be associated with only one console, so the **AllocConsole** function fails if the calling process already has a console.</span></span> <span data-ttu-id="fb68f-115">Un proceso puede usar la función [**FreeConsole**](freeconsole.md) para desasociarse de su consola actual y, después, puede llamar a **AllocConsole** para crear una nueva consola o [**AttachConsole**](attachconsole.md) para asociarse a otra consola.</span><span class="sxs-lookup"><span data-stu-id="fb68f-115">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its current console, then it can call **AllocConsole** to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<span data-ttu-id="fb68f-116">Si el proceso de llamada crea un proceso secundario, el elemento secundario hereda la nueva consola.</span><span class="sxs-lookup"><span data-stu-id="fb68f-116">If the calling process creates a child process, the child inherits the new console.</span></span>

<span data-ttu-id="fb68f-117">**AllocConsole** inicializa la entrada estándar, la salida estándar y los identificadores de error estándar para la nueva consola.</span><span class="sxs-lookup"><span data-stu-id="fb68f-117">**AllocConsole** initializes standard input, standard output, and standard error handles for the new console.</span></span> <span data-ttu-id="fb68f-118">El identificador de entrada estándar es un identificador del búfer de entrada de la consola, y los identificadores de salida estándar y de error estándar son identificadores del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="fb68f-118">The standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles to the console's screen buffer.</span></span> <span data-ttu-id="fb68f-119">Para recuperar estos identificadores, use la función [**GetStdHandle**](getstdhandle.md).</span><span class="sxs-lookup"><span data-stu-id="fb68f-119">To retrieve these handles, use the [**GetStdHandle**](getstdhandle.md) function.</span></span>

<span data-ttu-id="fb68f-120">Esta función se usa principalmente en una aplicación de interfaz gráfica de usuario (GUI) para crear una ventana de consola.</span><span class="sxs-lookup"><span data-stu-id="fb68f-120">This function is primarily used by a graphical user interface (GUI) application to create a console window.</span></span> <span data-ttu-id="fb68f-121">Las aplicaciones de GUI se inicializan sin una consola.</span><span class="sxs-lookup"><span data-stu-id="fb68f-121">GUI applications are initialized without a console.</span></span> <span data-ttu-id="fb68f-122">Las aplicaciones de consola se inicializan con una consola, a menos que se creen como procesos desasociados (llamando a la función [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) con la marca **DETACHED\_PROCESS**).</span><span class="sxs-lookup"><span data-stu-id="fb68f-122">Console applications are initialized with a console, unless they are created as detached processes (by calling the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function with the **DETACHED\_PROCESS** flag).</span></span>

## <a name="requirements"></a><span data-ttu-id="fb68f-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb68f-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="fb68f-124">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="fb68f-124">Minimum supported client</span></span> | <span data-ttu-id="fb68f-125">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="fb68f-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="fb68f-126">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="fb68f-126">Minimum supported server</span></span> | <span data-ttu-id="fb68f-127">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="fb68f-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="fb68f-128">Encabezado</span><span class="sxs-lookup"><span data-stu-id="fb68f-128">Header</span></span> | <span data-ttu-id="fb68f-129">ConsoleApi.h (via WinCon.h, include Windows.h)</span><span class="sxs-lookup"><span data-stu-id="fb68f-129">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="fb68f-130">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="fb68f-130">Library</span></span> | <span data-ttu-id="fb68f-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="fb68f-131">Kernel32.lib</span></span> |
| <span data-ttu-id="fb68f-132">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="fb68f-132">DLL</span></span> | <span data-ttu-id="fb68f-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="fb68f-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="fb68f-134">Vea también</span><span class="sxs-lookup"><span data-stu-id="fb68f-134">See also</span></span>

[<span data-ttu-id="fb68f-135">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="fb68f-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="fb68f-136">Consolas</span><span class="sxs-lookup"><span data-stu-id="fb68f-136">Consoles</span></span>](consoles.md)

[<span data-ttu-id="fb68f-137">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="fb68f-137">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="fb68f-138">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="fb68f-138">**CreateProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[<span data-ttu-id="fb68f-139">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="fb68f-139">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="fb68f-140">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="fb68f-140">**GetStdHandle**</span></span>](getstdhandle.md)
