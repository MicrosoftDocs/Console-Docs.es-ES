---
title: SetConsoleHistoryInfo función)
description: Establece la configuración del historial para la consola de Windows del proceso que realiza la llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/SetConsoleHistoryInfo
- wincon/SetConsoleHistoryInfo
- SetConsoleHistoryInfo
MS-HAID:
- base.setconsolehistoryinfo
- consoles.setconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: db180f53-aa3c-4a91-bc3e-9f3f0bb7ab01
topic_type:
- apiref
api_name:
- SetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: bf194e154a06efc32510fe811ab89877e283e142
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060636"
---
# <a name="setconsolehistoryinfo-function"></a><span data-ttu-id="330c3-104">SetConsoleHistoryInfo función)</span><span class="sxs-lookup"><span data-stu-id="330c3-104">SetConsoleHistoryInfo function</span></span>


<span data-ttu-id="330c3-105">Establece la configuración del historial de la consola del proceso que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="330c3-105">Sets the history settings for the calling process's console.</span></span>

<a name="syntax"></a><span data-ttu-id="330c3-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="330c3-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleHistoryInfo(
  _In_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

<a name="parameters"></a><span data-ttu-id="330c3-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="330c3-107">Parameters</span></span>
----------

<span data-ttu-id="330c3-108">*lpConsoleHistoryInfo* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="330c3-108">*lpConsoleHistoryInfo* \[in\]</span></span>  
<span data-ttu-id="330c3-109">Un puntero a una estructura de [\*\* \_ \_ información del historial\*\*](console-history-info.md) de la consola que contiene la configuración del historial de la consola del proceso.</span><span class="sxs-lookup"><span data-stu-id="330c3-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that contains the history settings for the process's console.</span></span>

<a name="return-value"></a><span data-ttu-id="330c3-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="330c3-110">Return value</span></span>
------------

<span data-ttu-id="330c3-111">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="330c3-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="330c3-112">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="330c3-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="330c3-113">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="330c3-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="330c3-114">Observaciones</span><span class="sxs-lookup"><span data-stu-id="330c3-114">Remarks</span></span>
-------

<span data-ttu-id="330c3-115">Si el proceso de llamada no es un proceso de consola, se produce un error en la función y se establece el último código de error en \*\* \_ acceso \_ denegado\*\*.</span><span class="sxs-lookup"><span data-stu-id="330c3-115">If the calling process is not a console process, the function fails and sets the last error code to **ERROR\_ACCESS\_DENIED**.</span></span>

<a name="requirements"></a><span data-ttu-id="330c3-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="330c3-116">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="330c3-117">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="330c3-117">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="330c3-118">Windows Vista [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="330c3-118">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="330c3-119">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="330c3-119">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="330c3-120">Windows Server 2008 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="330c3-120">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="330c3-121">Encabezado</span><span class="sxs-lookup"><span data-stu-id="330c3-121">Header</span></span></p></td>
<td><span data-ttu-id="330c3-122">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="330c3-122">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="330c3-123">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="330c3-123">Library</span></span></p></td>
<td><span data-ttu-id="330c3-124">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="330c3-124">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="330c3-125">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="330c3-125">DLL</span></span></p></td>
<td><span data-ttu-id="330c3-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="330c3-126">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="330c3-127"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="330c3-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="330c3-128">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="330c3-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="330c3-129">**\_información del historial de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="330c3-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="330c3-130">**GetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="330c3-130">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)

 

 




