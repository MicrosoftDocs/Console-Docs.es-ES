---
title: GetConsoleHistoryInfo función)
description: Consulte la información de referencia sobre la función GetConsoleHistoryInfo, que recupera la configuración del historial de la consola del proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleHistoryInfo
- wincon/GetConsoleHistoryInfo
- GetConsoleHistoryInfo
MS-HAID:
- base.getconsolehistoryinfo
- consoles.getconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 145008b3-8a4a-4e6a-9144-ee787ce90ef4
topic_type:
- apiref
api_name:
- GetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 176cf5517f18f022f00824de02872adcb916f231
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060677"
---
# <a name="getconsolehistoryinfo-function"></a><span data-ttu-id="325e2-104">GetConsoleHistoryInfo función)</span><span class="sxs-lookup"><span data-stu-id="325e2-104">GetConsoleHistoryInfo function</span></span>


<span data-ttu-id="325e2-105">Recupera la configuración del historial de la consola del proceso que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="325e2-105">Retrieves the history settings for the calling process's console.</span></span>

<a name="syntax"></a><span data-ttu-id="325e2-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="325e2-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

<a name="parameters"></a><span data-ttu-id="325e2-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="325e2-107">Parameters</span></span>
----------

<span data-ttu-id="325e2-108">*lpConsoleHistoryInfo* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="325e2-108">*lpConsoleHistoryInfo* \[out\]</span></span>  
<span data-ttu-id="325e2-109">Puntero a una estructura [**de \_ \_ información del historial**](console-history-info.md) de la consola que recibe la configuración del historial de la consola del proceso que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="325e2-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that receives the history settings for the calling process's console.</span></span>

<a name="return-value"></a><span data-ttu-id="325e2-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="325e2-110">Return value</span></span>
------------

<span data-ttu-id="325e2-111">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="325e2-111">If the function succeeds the return value is nonzero.</span></span>

<span data-ttu-id="325e2-112">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="325e2-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="325e2-113">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="325e2-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="325e2-114">Observaciones</span><span class="sxs-lookup"><span data-stu-id="325e2-114">Remarks</span></span>
-------

<span data-ttu-id="325e2-115">Si el proceso de llamada no es un proceso de consola, se produce un error en la función y se establece el último error en \*\* \_ acceso \_ denegado\*\*.</span><span class="sxs-lookup"><span data-stu-id="325e2-115">If the calling process is not a console process, the function fails and sets the last error to **ERROR\_ACCESS\_DENIED**.</span></span>

<a name="requirements"></a><span data-ttu-id="325e2-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="325e2-116">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="325e2-117">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="325e2-117">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="325e2-118">Windows Vista [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="325e2-118">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="325e2-119">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="325e2-119">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="325e2-120">Windows Server 2008 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="325e2-120">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="325e2-121">Encabezado</span><span class="sxs-lookup"><span data-stu-id="325e2-121">Header</span></span></p></td>
<td><span data-ttu-id="325e2-122">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="325e2-122">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="325e2-123">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="325e2-123">Library</span></span></p></td>
<td><span data-ttu-id="325e2-124">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="325e2-124">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="325e2-125">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="325e2-125">DLL</span></span></p></td>
<td><span data-ttu-id="325e2-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="325e2-126">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="325e2-127"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="325e2-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="325e2-128">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="325e2-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="325e2-129">**\_información del historial de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="325e2-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="325e2-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="325e2-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)

 

 




