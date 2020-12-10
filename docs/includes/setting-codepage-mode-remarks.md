---
ms.openlocfilehash: 2e5222bba5878d98c6f703b8aa25dfd1a22197db
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "93037040"
---
Esta función usa caracteres Unicode o caracteres de 8 bits de la página de códigos actual de la consola. La página de códigos de la consola tiene como valor predeterminado la página de códigos OEM del sistema. Para cambiar la página de códigos de la consola, use las funciones [**SetConsoleCP**](../setconsolecp.md) o [**SetConsoleOutputCP**](../setconsoleoutputcp.md). Los consumidores heredados también pueden usar los comandos **chcp** o **mode con cp select=** , pero no se recomienda si va a desarrollar algo nuevo.