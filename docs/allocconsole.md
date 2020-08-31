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
ms.openlocfilehash: 2e06cdc82c4e58dd09b99fa08bf4917ad37b552f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060928"
---
# <a name="allocconsole-function"></a><span data-ttu-id="7dd26-104">AllocConsole función)</span><span class="sxs-lookup"><span data-stu-id="7dd26-104">AllocConsole function</span></span>


<span data-ttu-id="7dd26-105">Asigna una nueva consola para el proceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="7dd26-105">Allocates a new console for the calling process.</span></span>

<a name="syntax"></a><span data-ttu-id="7dd26-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7dd26-106">Syntax</span></span>
------

```C
BOOL WINAPI AllocConsole(void);
```

<a name="parameters"></a><span data-ttu-id="7dd26-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7dd26-107">Parameters</span></span>
----------

<span data-ttu-id="7dd26-108">Esta función no tiene parámetros.</span><span class="sxs-lookup"><span data-stu-id="7dd26-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="7dd26-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="7dd26-109">Return value</span></span>
------------

<span data-ttu-id="7dd26-110">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="7dd26-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="7dd26-111">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="7dd26-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="7dd26-112">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="7dd26-112">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="7dd26-113">Observaciones</span><span class="sxs-lookup"><span data-stu-id="7dd26-113">Remarks</span></span>
-------

<span data-ttu-id="7dd26-114">Un proceso solo se puede asociar a una consola, por lo que se produce un error en la función **AllocConsole** si el proceso de llamada ya tiene una consola.</span><span class="sxs-lookup"><span data-stu-id="7dd26-114">A process can be associated with only one console, so the **AllocConsole** function fails if the calling process already has a console.</span></span> <span data-ttu-id="7dd26-115">Un proceso puede usar la función [**FreeConsole**](freeconsole.md) para desasociarse de su consola actual y, después, puede llamar a **AllocConsole** para crear una nueva consola o [**AttachConsole**](attachconsole.md) para adjuntar a otra consola.</span><span class="sxs-lookup"><span data-stu-id="7dd26-115">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its current console, then it can call **AllocConsole** to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<span data-ttu-id="7dd26-116">Si el proceso de llamada crea un proceso secundario, el elemento secundario hereda la nueva consola.</span><span class="sxs-lookup"><span data-stu-id="7dd26-116">If the calling process creates a child process, the child inherits the new console.</span></span>

<span data-ttu-id="7dd26-117">**AllocConsole** inicializa la entrada estándar, la salida estándar y los identificadores de error estándar para la nueva consola.</span><span class="sxs-lookup"><span data-stu-id="7dd26-117">**AllocConsole** initializes standard input, standard output, and standard error handles for the new console.</span></span> <span data-ttu-id="7dd26-118">El identificador de entrada estándar es un identificador del búfer de entrada de la consola, y los identificadores de salida estándar y de error estándar son identificadores del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="7dd26-118">The standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles to the console's screen buffer.</span></span> <span data-ttu-id="7dd26-119">Para recuperar estos identificadores, use la función [**GetStdHandle**](getstdhandle.md) .</span><span class="sxs-lookup"><span data-stu-id="7dd26-119">To retrieve these handles, use the [**GetStdHandle**](getstdhandle.md) function.</span></span>

<span data-ttu-id="7dd26-120">Esta función se usa principalmente en una aplicación de interfaz gráfica de usuario (GUI) para crear una ventana de consola.</span><span class="sxs-lookup"><span data-stu-id="7dd26-120">This function is primarily used by a graphical user interface (GUI) application to create a console window.</span></span> <span data-ttu-id="7dd26-121">Las aplicaciones de GUI se inicializan sin una consola de.</span><span class="sxs-lookup"><span data-stu-id="7dd26-121">GUI applications are initialized without a console.</span></span> <span data-ttu-id="7dd26-122">Las aplicaciones de consola se inicializan con una consola de, a menos que se creen como procesos desasociados (llamando a la función [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) con la marca de \*\* \_ proceso separado\*\* ).</span><span class="sxs-lookup"><span data-stu-id="7dd26-122">Console applications are initialized with a console, unless they are created as detached processes (by calling the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function with the **DETACHED\_PROCESS** flag).</span></span>

<a name="requirements"></a><span data-ttu-id="7dd26-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7dd26-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="7dd26-124">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="7dd26-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="7dd26-125">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="7dd26-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7dd26-126">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="7dd26-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="7dd26-127">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="7dd26-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7dd26-128">Encabezado</span><span class="sxs-lookup"><span data-stu-id="7dd26-128">Header</span></span></p></td>
<td><span data-ttu-id="7dd26-129">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="7dd26-129">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7dd26-130">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="7dd26-130">Library</span></span></p></td>
<td><span data-ttu-id="7dd26-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="7dd26-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7dd26-132">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="7dd26-132">DLL</span></span></p></td>
<td><span data-ttu-id="7dd26-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7dd26-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="7dd26-134"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="7dd26-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="7dd26-135">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="7dd26-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="7dd26-136">Consolas</span><span class="sxs-lookup"><span data-stu-id="7dd26-136">Consoles</span></span>](consoles.md)

[<span data-ttu-id="7dd26-137">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="7dd26-137">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="7dd26-138">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="7dd26-138">**CreateProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[<span data-ttu-id="7dd26-139">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="7dd26-139">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="7dd26-140">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="7dd26-140">**GetStdHandle**</span></span>](getstdhandle.md)

 

 




