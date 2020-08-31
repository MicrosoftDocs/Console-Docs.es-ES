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
ms.openlocfilehash: 7d707423d7fca7c55d06bff11d6cbc904512e62b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060769"
---
# <a name="createpseudoconsole-function"></a><span data-ttu-id="14305-104">CreatePseudoConsole función)</span><span class="sxs-lookup"><span data-stu-id="14305-104">CreatePseudoConsole function</span></span>


<span data-ttu-id="14305-105">Crea un nuevo objeto pseudoconsole para el proceso que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="14305-105">Creates a new pseudoconsole object for the calling process.</span></span>

<a name="syntax"></a><span data-ttu-id="14305-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="14305-106">Syntax</span></span>
------

```C
HRESULT WINAPI CreatePseudoConsole(
    _In_ COORD size,
    _In_ HANDLE hInput,
    _In_ HANDLE hOutput,
    _In_ DWORD dwFlags,
    _Out_ HPCON* phPC
);
```

<a name="parameters"></a><span data-ttu-id="14305-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="14305-107">Parameters</span></span>
----------

<span data-ttu-id="14305-108">*tamaño* \[ de de\]</span><span class="sxs-lookup"><span data-stu-id="14305-108">*size* \[in\]</span></span>  
<span data-ttu-id="14305-109">Dimensiones de la ventana o búfer en el recuento de caracteres que se usarán para la creación inicial de pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="14305-109">The dimensions of the window/buffer in count of characters that will be used on initial creation of the pseudoconsole.</span></span> <span data-ttu-id="14305-110">Se puede ajustar más adelante con [ResizePseudoConsole](resizepseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="14305-110">This can be adjusted later with [ResizePseudoConsole](resizepseudoconsole.md).</span></span>

<span data-ttu-id="14305-111">*hInput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="14305-111">*hInput* \[in\]</span></span>  
<span data-ttu-id="14305-112">Identificador abierto de un flujo de datos que representa la entrada del usuario en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="14305-112">An open handle to a stream of data that represents user input to the device.</span></span> <span data-ttu-id="14305-113">Esto está restringido actualmente a la e/s [sincrónica](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .</span><span class="sxs-lookup"><span data-stu-id="14305-113">This is currently restricted to [synchronous](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.</span></span>

<span data-ttu-id="14305-114">*hOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="14305-114">*hOutput* \[in\]</span></span>  
<span data-ttu-id="14305-115">Identificador abierto de un flujo de datos que representa la salida de la aplicación del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="14305-115">An open handle to a stream of data that represents application output from the device.</span></span> <span data-ttu-id="14305-116">Esto está restringido actualmente a la e/s [sincrónica](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .</span><span class="sxs-lookup"><span data-stu-id="14305-116">This is currently restricted to [synchronous](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.</span></span>

<span data-ttu-id="14305-117">*dwFlags* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="14305-117">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="14305-118">El valor puede ser uno de los siguientes:</span><span class="sxs-lookup"><span data-stu-id="14305-118">The value can be one of the following:</span></span>
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="14305-119">Valor</span><span class="sxs-lookup"><span data-stu-id="14305-119">Value</span></span></th>
<th><span data-ttu-id="14305-120">Significado</span><span class="sxs-lookup"><span data-stu-id="14305-120">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="14305-121"><strong>0</strong></span><span class="sxs-lookup"><span data-stu-id="14305-121"><strong>0</strong></span></span></td>
<td><p><span data-ttu-id="14305-122">Realice una creación de pseudoconsole estándar.</span><span class="sxs-lookup"><span data-stu-id="14305-122">Perform a standard pseudoconsole creation.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="14305-123"><span id="PSEUDOCONSOLE_INHERIT_CURSOR"></span><span id="pseudoconsole_inherit_cursor"></span>
<strong>PSEUDOCONSOLE_INHERIT_CURSOR</strong> (DWORD) 1</span><span class="sxs-lookup"><span data-stu-id="14305-123"><span id="PSEUDOCONSOLE_INHERIT_CURSOR"></span><span id="pseudoconsole_inherit_cursor"></span>
<strong>PSEUDOCONSOLE_INHERIT_CURSOR</strong> (DWORD)1</span></span></td>
<td><p><span data-ttu-id="14305-124">La sesión de pseudoconsole creada intentará heredar la posición del cursor de la consola primaria.</span><span class="sxs-lookup"><span data-stu-id="14305-124">The created pseudoconsole session will attempt to inherit the cursor position of the parent console.</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="14305-125">*phPC* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="14305-125">*phPC* \[out\]</span></span>  
<span data-ttu-id="14305-126">Puntero a una ubicación que recibirá un identificador para el nuevo dispositivo pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="14305-126">Pointer to a location that will receive a handle to the new pseudoconsole device.</span></span>

<a name="return-value"></a><span data-ttu-id="14305-127">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="14305-127">Return value</span></span>
------------

<span data-ttu-id="14305-128">Tipo: **HRESULT**</span><span class="sxs-lookup"><span data-stu-id="14305-128">Type: **HRESULT**</span></span>

<span data-ttu-id="14305-129">Si este método se ejecuta correctamente, devuelve **S_OK**.</span><span class="sxs-lookup"><span data-stu-id="14305-129">If this method succeeds, it returns **S_OK**.</span></span> <span data-ttu-id="14305-130">De lo contrario, devuelve un código de error **HRESULT** .</span><span class="sxs-lookup"><span data-stu-id="14305-130">Otherwise, it returns an **HRESULT** error code.</span></span>

<a name="remarks"></a><span data-ttu-id="14305-131">Observaciones</span><span class="sxs-lookup"><span data-stu-id="14305-131">Remarks</span></span>
-------

<span data-ttu-id="14305-132">Esta función la usan principalmente las aplicaciones que intentan ser una ventana de terminal para una aplicación de la interfaz de usuario de línea de comandos (CUI).</span><span class="sxs-lookup"><span data-stu-id="14305-132">This function is primarily used by applications attempting to be a terminal window for a command-line user interface (CUI) application.</span></span> <span data-ttu-id="14305-133">Los llamadores se convierten en responsables de la presentación de la información en el flujo de salida y de la recopilación de datos proporcionados por el usuario y su serialización en el flujo de entrada.</span><span class="sxs-lookup"><span data-stu-id="14305-133">The callers become responsible for presentation of the information on the output stream and for collecting user input and serializing it into the input stream.</span></span>

<span data-ttu-id="14305-134">Los flujos de entrada y salida codificados como UTF-8 contienen texto sin formato intercalado con [secuencias de terminales virtuales](console-virtual-terminal-sequences.md).</span><span class="sxs-lookup"><span data-stu-id="14305-134">The input and output streams encoded as UTF-8 contain plain text interleaved with [Virtual Terminal Sequences](console-virtual-terminal-sequences.md).</span></span> 

<span data-ttu-id="14305-135">En el flujo de salida, la aplicación que realiza la llamada puede descodificar las [secuencias de terminal virtuales](console-virtual-terminal-sequences.md) para diseñar y presentar el texto sin formato en una ventana de presentación.</span><span class="sxs-lookup"><span data-stu-id="14305-135">On the output stream, the [virtual terminal sequences](console-virtual-terminal-sequences.md) can be decoded by the calling application to layout and present the plain text in a display window.</span></span> 

<span data-ttu-id="14305-136">En el flujo de entrada, el texto sin formato representa las teclas de teclado estándar que introduce un usuario.</span><span class="sxs-lookup"><span data-stu-id="14305-136">On the input stream, plain text represents standard keyboard keys input by a user.</span></span> <span data-ttu-id="14305-137">Las operaciones más complicadas se representan mediante claves de control de codificación y movimientos del mouse como [secuencias de terminales virtuales](console-virtual-terminal-sequences.md) incrustadas en esta secuencia.</span><span class="sxs-lookup"><span data-stu-id="14305-137">More complicated operations are represented by encoding control keys and mouse movements as [virtual terminal sequences](console-virtual-terminal-sequences.md) embedded in this stream.</span></span>

<span data-ttu-id="14305-138">El identificador creado por esta función debe cerrarse con [ClosePseudoConsole](closepseudoconsole.md) cuando se completen las operaciones.</span><span class="sxs-lookup"><span data-stu-id="14305-138">The handle created by this function must be closed with [ClosePseudoConsole](closepseudoconsole.md) when operations are complete.</span></span>

<span data-ttu-id="14305-139">Si usa `PSEUDOCONSOLE_INHERIT_CURSOR` , la aplicación que realiza la llamada debe estar preparada para responder a la solicitud del estado del cursor de forma asincrónica en un subproceso en segundo plano reenviando o interpretando la solicitud de información de cursor que se recibirá en `hOutput` y responderá `hInput` .</span><span class="sxs-lookup"><span data-stu-id="14305-139">If using `PSEUDOCONSOLE_INHERIT_CURSOR`, the calling application should be prepared to respond to the request for the cursor state in an asynchronous fashion on a background thread by forwarding or interpreting the request for cursor information that will be received on `hOutput` and replying on `hInput`.</span></span> <span data-ttu-id="14305-140">Si no lo hace, es posible que la aplicación que llama se bloquee mientras realiza otra solicitud del sistema pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="14305-140">Failure to do so may cause the calling application to hang while making another request of the pseudoconsole system.</span></span>

<a name="examples"></a><span data-ttu-id="14305-141">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="14305-141">Examples</span></span>
--------

<span data-ttu-id="14305-142">Para ver un tutorial completo sobre el uso de esta función para establecer una sesión de psuedoconsole, consulte [creación de una sesión de Pseudoconsole](creating-a-pseudoconsole-session.md).</span><span class="sxs-lookup"><span data-stu-id="14305-142">For a full walkthrough on using this function to establish a psuedoconsole session, please see [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).</span></span>

<a name="requirements"></a><span data-ttu-id="14305-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="14305-143">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="14305-144">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="14305-144">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="14305-145">Windows 10 1809 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="14305-145">Windows 10 1809 [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="14305-146">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="14305-146">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="14305-147">Windows Server 2019 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="14305-147">Windows Server 2019 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="14305-148">Encabezado</span><span class="sxs-lookup"><span data-stu-id="14305-148">Header</span></span></p></td>
<td><span data-ttu-id="14305-149">ConsoleApi. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="14305-149">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="14305-150">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="14305-150">Library</span></span></p></td>
<td><span data-ttu-id="14305-151">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="14305-151">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="14305-152">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="14305-152">DLL</span></span></p></td>
<td><span data-ttu-id="14305-153">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="14305-153">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="14305-154"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="14305-154"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="14305-155">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="14305-155">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="14305-156">Creación de una sesión de Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="14305-156">Creating a Pseudoconsole Session</span></span>](creating-a-pseudoconsole-session.md)

[<span data-ttu-id="14305-157">**ResizePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="14305-157">**ResizePseudoConsole**</span></span>](resizepseudoconsole.md)

[<span data-ttu-id="14305-158">**ClosePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="14305-158">**ClosePseudoConsole**</span></span>](closepseudoconsole.md)
