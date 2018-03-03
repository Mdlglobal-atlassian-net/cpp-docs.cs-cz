---
title: Vararg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f3d22a5c3f20480d1e904ec8e087114385ba7ee9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="varargs"></a>Vararg
Pokud parametry jsou předány prostřednictvím vararg (například třemi tečkami argumentů), pak v podstatě normální parametr předávání vztahuje, včetně přesahu pátého a následujících argumentů. Je znovu odpovědností volaného k výpisu argumentů, které adresu. Pouze hodnoty s plovoucí desetinnou čárkou celé číslo a s plovoucí desetinnou čárkou registrace obsahovat plovoucí hodnotu v případě, že volaného očekává hodnotu v registrech celé číslo.  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../build/calling-convention.md)