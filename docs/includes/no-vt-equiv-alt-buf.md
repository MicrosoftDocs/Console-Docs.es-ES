---
ms.openlocfilehash: ef8a068fe6edd2a7d2013c930c238235326b8c1d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039141"
---
> [!TIP]
> <span data-ttu-id="140fb-101">No se recomienda esta API, pero tiene un equivalente de **[terminal virtual](../console-virtual-terminal-sequences.md)** aproximado en la secuencia de **[búfer de pantalla alternativa](../console-virtual-terminal-sequences.md#alternate-screen-buffer)** .</span><span class="sxs-lookup"><span data-stu-id="140fb-101">This API is not recommended but it does have an approximate **[virtual terminal](../console-virtual-terminal-sequences.md)** equivalent in the **[alternate screen buffer](../console-virtual-terminal-sequences.md#alternate-screen-buffer)** sequence.</span></span> <span data-ttu-id="140fb-102">Al establecer el _búfer de pantalla alternativo_ , puede proporcionar una aplicación con un espacio aislado independiente para dibujar en el transcurso del tiempo de ejecución de la sesión, al tiempo que se conserva el contenido mostrado por el invocador de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="140fb-102">Setting the _alternate screen buffer_ can provide an application with a separate, isolated space for drawing over the course of its session runtime while preserving the content that was displayed by the application's invoker.</span></span> <span data-ttu-id="140fb-103">Esto mantiene la información de dibujo para la restauración simple al salir del proceso.</span><span class="sxs-lookup"><span data-stu-id="140fb-103">This maintains that drawing information for simple restoration on process exit.</span></span>
