---
title: Vararg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e7b71cd426bc89570f9d394f3e38dc7a002f6e8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380505"
---
# <a name="varargs"></a>Vararg
Pokud parametry jsou předány prostřednictvím vararg (například třemi tečkami argumentů), pak v podstatě normální parametr předávání vztahuje, včetně přesahu pátého a následujících argumentů. Je znovu odpovědností volaného k výpisu argumentů, které adresu. Pouze hodnoty s plovoucí desetinnou čárkou celé číslo a s plovoucí desetinnou čárkou registrace obsahovat plovoucí hodnotu v případě, že volaného očekává hodnotu v registrech celé číslo.  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../build/calling-convention.md)