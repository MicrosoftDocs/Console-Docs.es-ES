---
title: CreatePseudoConsole función)
description: Vea la información de referencia sobre la función CreatePseudoConsole, que asigna un nuevo pseudoconsole para el proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola, conpty, pseudoconsole
f1_keywords:
- consoleapi/CreatePseudoConsole
- CreatePseudoConsole
topic_type:
- apiref
api_name:
- CreatePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: b015f224684a53a8bb654f04b1797ac1af794fc3
ms.sourcegitcommit: f16996b9c7deead9bcfa44954be93a6ba087abcb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/16/2020
ms.locfileid: "97601482"
---
# <a name="createpseudoconsole-function"></a><span data-ttu-id="54883-104">CreatePseudoConsole función)</span><span class="sxs-lookup"><span data-stu-id="54883-104">CreatePseudoConsole function</span></span>

<span data-ttu-id="54883-105">Crea un nuevo objeto pseudoconsole para el proceso que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="54883-105">Creates a new pseudoconsole object for the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="54883-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="54883-106">Syntax</span></span>

```C
HRESULT WINAPI CreatePseudoConsole(
    _In_ COORD size,
    _In_ HANDLE hInput,
    _In_ HANDLE hOutput,
    _In_ DWORD dwFlags,
    _Out_ HPCON* phPC
);
```

## <a name="parameters"></a><span data-ttu-id="54883-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="54883-107">Parameters</span></span>

<span data-ttu-id="54883-108">*tamaño* \[ de de\]</span><span class="sxs-lookup"><span data-stu-id="54883-108">*size* \[in\]</span></span>  
<span data-ttu-id="54883-109">Dimensiones de la ventana o búfer en el recuento de caracteres que se usarán para la creación inicial de pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="54883-109">The dimensions of the window/buffer in count of characters that will be used on initial creation of the pseudoconsole.</span></span> <span data-ttu-id="54883-110">Se puede ajustar más adelante con [ResizePseudoConsole](resizepseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="54883-110">This can be adjusted later with [ResizePseudoConsole](resizepseudoconsole.md).</span></span>

<span data-ttu-id="54883-111">*hInput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="54883-111">*hInput* \[in\]</span></span>  
<span data-ttu-id="54883-112">Identificador abierto de un flujo de datos que representa la entrada del usuario en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="54883-112">An open handle to a stream of data that represents user input to the device.</span></span> <span data-ttu-id="54883-113">Esto está restringido actualmente a la e/s [sincrónica](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .</span><span class="sxs-lookup"><span data-stu-id="54883-113">This is currently restricted to [synchronous](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.</span></span>

<span data-ttu-id="54883-114">*hOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="54883-114">*hOutput* \[in\]</span></span>  
<span data-ttu-id="54883-115">Identificador abierto de un flujo de datos que representa la salida de la aplicación del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="54883-115">An open handle to a stream of data that represents application output from the device.</span></span> <span data-ttu-id="54883-116">Esto está restringido actualmente a la e/s [sincrónica](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .</span><span class="sxs-lookup"><span data-stu-id="54883-116">This is currently restricted to [synchronous](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.</span></span>

<span data-ttu-id="54883-117">*dwFlags* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="54883-117">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="54883-118">El valor puede ser uno de los siguientes:</span><span class="sxs-lookup"><span data-stu-id="54883-118">The value can be one of the following:</span></span>

| <span data-ttu-id="54883-119">Valor</span><span class="sxs-lookup"><span data-stu-id="54883-119">Value</span></span> | <span data-ttu-id="54883-120">Significado</span><span class="sxs-lookup"><span data-stu-id="54883-120">Meaning</span></span> |
|-|-|
| <span data-ttu-id="54883-121">**0**</span><span class="sxs-lookup"><span data-stu-id="54883-121">**0**</span></span> | <span data-ttu-id="54883-122">Realice una creación de pseudoconsole estándar.</span><span class="sxs-lookup"><span data-stu-id="54883-122">Perform a standard pseudoconsole creation.</span></span> |
| <span data-ttu-id="54883-123">**PSEUDOCONSOLE_INHERIT_CURSOR** (DWORD) 1</span><span class="sxs-lookup"><span data-stu-id="54883-123">**PSEUDOCONSOLE_INHERIT_CURSOR** (DWORD)1</span></span> | <span data-ttu-id="54883-124">La sesión de pseudoconsole creada intentará heredar la posición del cursor de la consola primaria.</span><span class="sxs-lookup"><span data-stu-id="54883-124">The created pseudoconsole session will attempt to inherit the cursor position of the parent console.</span></span> |

<span data-ttu-id="54883-125">*phPC* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="54883-125">*phPC* \[out\]</span></span>  
<span data-ttu-id="54883-126">Puntero a una ubicación que recibirá un identificador para el nuevo dispositivo pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="54883-126">Pointer to a location that will receive a handle to the new pseudoconsole device.</span></span>

## <a name="return-value"></a><span data-ttu-id="54883-127">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="54883-127">Return value</span></span>

<span data-ttu-id="54883-128">Tipo: **HRESULT**</span><span class="sxs-lookup"><span data-stu-id="54883-128">Type: **HRESULT**</span></span>

<span data-ttu-id="54883-129">Si este método se ejecuta correctamente, devuelve **S_OK**.</span><span class="sxs-lookup"><span data-stu-id="54883-129">If this method succeeds, it returns **S_OK**.</span></span> <span data-ttu-id="54883-130">De lo contrario, devuelve un código de error **HRESULT** .</span><span class="sxs-lookup"><span data-stu-id="54883-130">Otherwise, it returns an **HRESULT** error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="54883-131">Comentarios</span><span class="sxs-lookup"><span data-stu-id="54883-131">Remarks</span></span>

<span data-ttu-id="54883-132">Esta función la usan principalmente las aplicaciones que intentan ser una ventana de terminal para una aplicación de la interfaz de usuario de línea de comandos (CUI).</span><span class="sxs-lookup"><span data-stu-id="54883-132">This function is primarily used by applications attempting to be a terminal window for a command-line user interface (CUI) application.</span></span> <span data-ttu-id="54883-133">Los llamadores se convierten en responsables de la presentación de la información en el flujo de salida y de la recopilación de datos proporcionados por el usuario y su serialización en el flujo de entrada.</span><span class="sxs-lookup"><span data-stu-id="54883-133">The callers become responsible for presentation of the information on the output stream and for collecting user input and serializing it into the input stream.</span></span>

<span data-ttu-id="54883-134">Los flujos de entrada y salida codificados como UTF-8 contienen texto sin formato intercalado con [secuencias de terminales virtuales](console-virtual-terminal-sequences.md).</span><span class="sxs-lookup"><span data-stu-id="54883-134">The input and output streams encoded as UTF-8 contain plain text interleaved with [Virtual Terminal Sequences](console-virtual-terminal-sequences.md).</span></span>

<span data-ttu-id="54883-135">En el flujo de salida, la aplicación que realiza la llamada puede descodificar las [secuencias de terminal virtuales](console-virtual-terminal-sequences.md) para diseñar y presentar el texto sin formato en una ventana de presentación.</span><span class="sxs-lookup"><span data-stu-id="54883-135">On the output stream, the [virtual terminal sequences](console-virtual-terminal-sequences.md) can be decoded by the calling application to layout and present the plain text in a display window.</span></span>

<span data-ttu-id="54883-136">En el flujo de entrada, el texto sin formato representa las teclas de teclado estándar que introduce un usuario.</span><span class="sxs-lookup"><span data-stu-id="54883-136">On the input stream, plain text represents standard keyboard keys input by a user.</span></span> <span data-ttu-id="54883-137">Las operaciones más complicadas se representan mediante claves de control de codificación y movimientos del mouse como [secuencias de terminales virtuales](console-virtual-terminal-sequences.md) incrustadas en esta secuencia.</span><span class="sxs-lookup"><span data-stu-id="54883-137">More complicated operations are represented by encoding control keys and mouse movements as [virtual terminal sequences](console-virtual-terminal-sequences.md) embedded in this stream.</span></span>

<span data-ttu-id="54883-138">El identificador creado por esta función debe cerrarse con [ClosePseudoConsole](closepseudoconsole.md) cuando se completen las operaciones.</span><span class="sxs-lookup"><span data-stu-id="54883-138">The handle created by this function must be closed with [ClosePseudoConsole](closepseudoconsole.md) when operations are complete.</span></span>

<span data-ttu-id="54883-139">Si usa `PSEUDOCONSOLE_INHERIT_CURSOR` , la aplicación que realiza la llamada debe estar preparada para responder a la solicitud del estado del cursor de forma asincrónica en un subproceso en segundo plano reenviando o interpretando la solicitud de información de cursor que se recibirá en `hOutput` y responderá `hInput` .</span><span class="sxs-lookup"><span data-stu-id="54883-139">If using `PSEUDOCONSOLE_INHERIT_CURSOR`, the calling application should be prepared to respond to the request for the cursor state in an asynchronous fashion on a background thread by forwarding or interpreting the request for cursor information that will be received on `hOutput` and replying on `hInput`.</span></span> <span data-ttu-id="54883-140">Si no lo hace, es posible que la aplicación que llama se bloquee mientras realiza otra solicitud del sistema pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="54883-140">Failure to do so may cause the calling application to hang while making another request of the pseudoconsole system.</span></span>

## <a name="examples"></a><span data-ttu-id="54883-141">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="54883-141">Examples</span></span>

<span data-ttu-id="54883-142">Para ver un tutorial completo sobre el uso de esta función para establecer una sesión de pseudoconsole, consulte [creación de una sesión de pseudoconsole](creating-a-pseudoconsole-session.md).</span><span class="sxs-lookup"><span data-stu-id="54883-142">For a full walkthrough on using this function to establish a pseudoconsole session, please see [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="54883-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="54883-143">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="54883-144">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="54883-144">Minimum supported client</span></span> | <span data-ttu-id="54883-145">Actualización 2018 de octubre de Windows 10 (versión 1809) \[ solo para aplicaciones de escritorio\]</span><span class="sxs-lookup"><span data-stu-id="54883-145">Windows 10 October 2018 Update (version 1809) \[desktop apps only\]</span></span> |
| <span data-ttu-id="54883-146">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="54883-146">Minimum supported server</span></span> | <span data-ttu-id="54883-147">Solo aplicaciones de escritorio de Windows Server 2019 \[\]</span><span class="sxs-lookup"><span data-stu-id="54883-147">Windows Server 2019 \[desktop apps only\]</span></span> |
| <span data-ttu-id="54883-148">Encabezado</span><span class="sxs-lookup"><span data-stu-id="54883-148">Header</span></span> | <span data-ttu-id="54883-149">ConsoleApi.h (a través de WinCon.h, incluido Windows.h)</span><span class="sxs-lookup"><span data-stu-id="54883-149">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="54883-150">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="54883-150">Library</span></span> | <span data-ttu-id="54883-151">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="54883-151">Kernel32.lib</span></span> |
| <span data-ttu-id="54883-152">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="54883-152">DLL</span></span> | <span data-ttu-id="54883-153">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="54883-153">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="54883-154">Vea también</span><span class="sxs-lookup"><span data-stu-id="54883-154">See also</span></span>

[<span data-ttu-id="54883-155">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="54883-155">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="54883-156">Creación de una sesión de pseudoconsola</span><span class="sxs-lookup"><span data-stu-id="54883-156">Creating a Pseudoconsole Session</span></span>](creating-a-pseudoconsole-session.md)

[<span data-ttu-id="54883-157">**ResizePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="54883-157">**ResizePseudoConsole**</span></span>](resizepseudoconsole.md)

[<span data-ttu-id="54883-158">**ClosePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="54883-158">**ClosePseudoConsole**</span></span>](closepseudoconsole.md)
