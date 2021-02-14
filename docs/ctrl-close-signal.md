---
title: CTRL + cerrar señal
description: El sistema genera una señal CTRL + cerrar cuando el usuario cierra una consola.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_ctrl\_close\_signal'
- base.ctrl\_close\_signal
- consoles.ctrl\_close\_signal
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a327dd55-3250-40ee-b1c4-6ba3b80984a8
ms.openlocfilehash: be237eac7649ad76615aea341a555a8a7af6445c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357895"
---
# <a name="ctrlclose-signal"></a><span data-ttu-id="3146c-104">CTRL + cerrar señal</span><span class="sxs-lookup"><span data-stu-id="3146c-104">CTRL+CLOSE Signal</span></span>

<span data-ttu-id="3146c-105">El sistema genera una señal CTRL + cerrar cuando el usuario cierra una consola.</span><span class="sxs-lookup"><span data-stu-id="3146c-105">The system generates a CTRL+CLOSE signal when the user closes a console.</span></span> <span data-ttu-id="3146c-106">Todos los procesos conectados a la consola reciben la señal, con lo que cada proceso tiene la oportunidad de limpiar antes de la terminación.</span><span class="sxs-lookup"><span data-stu-id="3146c-106">All processes attached to the console receive the signal, giving each process an opportunity to clean up before termination.</span></span> <span data-ttu-id="3146c-107">Cuando un proceso recibe esta señal, la función controladora puede realizar una de las siguientes acciones después de realizar las operaciones de limpieza:</span><span class="sxs-lookup"><span data-stu-id="3146c-107">When a process receives this signal, the handler function can take one of the following actions after performing any cleanup operations:</span></span>

- <span data-ttu-id="3146c-108">Llame a [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) para finalizar el proceso.</span><span class="sxs-lookup"><span data-stu-id="3146c-108">Call [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) to terminate the process.</span></span>
- <span data-ttu-id="3146c-109">Devuelve **false**.</span><span class="sxs-lookup"><span data-stu-id="3146c-109">Return **FALSE**.</span></span> <span data-ttu-id="3146c-110">Si ninguna de las funciones de controlador registradas devuelve **true**, el controlador predeterminado finaliza el proceso.</span><span class="sxs-lookup"><span data-stu-id="3146c-110">If none of the registered handler functions returns **TRUE**, the default handler terminates the process.</span></span>
- <span data-ttu-id="3146c-111">Devuelve **true**.</span><span class="sxs-lookup"><span data-stu-id="3146c-111">Return **TRUE**.</span></span> <span data-ttu-id="3146c-112">En este caso, no se llama a ninguna otra función de controlador y finaliza el proceso.</span><span class="sxs-lookup"><span data-stu-id="3146c-112">In this case, no other handler functions are called and the process terminates.</span></span>