---
ms.openlocfilehash: 2e5222bba5878d98c6f703b8aa25dfd1a22197db
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037040"
---
Esta función usa caracteres Unicode o caracteres de 8 bits de la página de códigos actual de la consola. La página de códigos de la consola tiene como valor predeterminado la página de códigos OEM del sistema. Para cambiar la página de códigos de la consola, use las funciones [**SetConsoleCP**](../setconsolecp.md) o [**SetConsoleOutputCP**](../setconsoleoutputcp.md) . Los consumidores heredados también pueden usar los comandos **chcp** o **mode con CP Select =** , pero no se recomienda para el desarrollo nuevo.