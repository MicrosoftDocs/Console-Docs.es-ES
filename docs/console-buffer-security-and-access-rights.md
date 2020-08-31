---
title: Seguridad y derechos de acceso de búfer de la consola
description: El modelo de seguridad de Windows permite controlar el acceso a los búferes de entrada y de pantalla de la consola. Para obtener más información sobre la seguridad, vea modelo de control de acceso.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_buffer\_security\_and\_access\_rights'
- base.console\_buffer\_security\_and\_access\_rights
- consoles.console\_buffer\_security\_and\_access\_rights
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f9a50063-8fc8-4cd1-8f24-9ae3946d3119
ms.openlocfilehash: 63cfdb91f4ab9696ade81c7a15bc62e1c93ab6e3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060885"
---
# <a name="console-buffer-security-and-access-rights"></a><span data-ttu-id="bf2c3-105">Seguridad y derechos de acceso de búfer de la consola</span><span class="sxs-lookup"><span data-stu-id="bf2c3-105">Console Buffer Security and Access Rights</span></span>


<span data-ttu-id="bf2c3-106">El modelo de seguridad de Windows permite controlar el acceso a los búferes de entrada y de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-106">The Windows security model enables you to control access to console input buffers and console screen buffers.</span></span> <span data-ttu-id="bf2c3-107">Para obtener más información sobre la seguridad, vea [modelo de control de acceso](https://msdn.microsoft.com/library/windows/desktop/aa374876).</span><span class="sxs-lookup"><span data-stu-id="bf2c3-107">For more information about security, see [Access-Control Model](https://msdn.microsoft.com/library/windows/desktop/aa374876).</span></span>

<span data-ttu-id="bf2c3-108">Puede especificar un [descriptor de seguridad](https://msdn.microsoft.com/library/windows/desktop/aa379563) para los búferes de entrada y de pantalla de la consola cuando se llama a la función [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) o [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="bf2c3-108">You can specify a [security descriptor](https://msdn.microsoft.com/library/windows/desktop/aa379563) for the console input and console screen buffers when you call the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) or [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) function.</span></span> <span data-ttu-id="bf2c3-109">Si especifica **null**, el objeto obtiene un descriptor de seguridad predeterminado.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-109">If you specify **NULL**, the object gets a default security descriptor.</span></span> <span data-ttu-id="bf2c3-110">Las ACL del descriptor de seguridad predeterminado de un búfer de la consola proceden del token principal o de suplantación del creador.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-110">The ACLs in the default security descriptor for a console buffer come from the primary or impersonation token of the creator.</span></span>

<span data-ttu-id="bf2c3-111">Los identificadores devueltos por [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)y [**GetStdHandle**](getstdhandle.md) tienen derechos de acceso **genéricos de \_ lectura** y \*\* \_ escritura\*\* .</span><span class="sxs-lookup"><span data-stu-id="bf2c3-111">The handles returned by [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md), and [**GetStdHandle**](getstdhandle.md) have the **GENERIC\_READ** and **GENERIC\_WRITE** access rights.</span></span>

<span data-ttu-id="bf2c3-112">Entre los derechos de acceso válidos se incluyen los [derechos de acceso](https://msdn.microsoft.com/library/windows/desktop/aa446632)genéricos de \*\* \_ lectura\*\* y \*\* \_ escritura\*\* genéricos.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-112">The valid access rights include the **GENERIC\_READ** and **GENERIC\_WRITE** [generic access rights](https://msdn.microsoft.com/library/windows/desktop/aa446632).</span></span>


| <span data-ttu-id="bf2c3-113">Valor</span><span class="sxs-lookup"><span data-stu-id="bf2c3-113">Value</span></span>                            | <span data-ttu-id="bf2c3-114">Significado</span><span class="sxs-lookup"><span data-stu-id="bf2c3-114">Meaning</span></span>                                                                                               |
|----------------------------------|-------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="bf2c3-115">**Genérico \_ LECTURA** (0x80000000L)</span><span class="sxs-lookup"><span data-stu-id="bf2c3-115">**GENERIC\_READ** (0x80000000L)</span></span>  | <span data-ttu-id="bf2c3-116">Solicita acceso de lectura al búfer de pantalla de la consola, lo que permite al proceso leer datos del búfer.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-116">Requests read access to the console screen buffer, enabling the process to read data from the buffer.</span></span> |
| <span data-ttu-id="bf2c3-117">**Genérico \_ ESCRITURA** (0x40000000L)</span><span class="sxs-lookup"><span data-stu-id="bf2c3-117">**GENERIC\_WRITE** (0x40000000L)</span></span> | <span data-ttu-id="bf2c3-118">Solicita acceso de escritura al búfer de pantalla de la consola, lo que permite que el proceso escriba datos en el búfer.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-118">Requests write access to the console screen buffer, enabling the process to write data to the buffer.</span></span> |










