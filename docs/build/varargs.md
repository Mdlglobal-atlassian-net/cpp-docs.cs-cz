---
title: Vararg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8492610721846e8252cbe71b358e428a2aaf024f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="varargs"></a>Vararg
Pokud parametry jsou předány prostřednictvím vararg (například třemi tečkami argumentů), pak v podstatě normální parametr předávání vztahuje, včetně přesahu pátého a následujících argumentů. Je znovu odpovědností volaného k výpisu argumentů, které adresu. Pouze hodnoty s plovoucí desetinnou čárkou celé číslo a s plovoucí desetinnou čárkou registrace obsahovat plovoucí hodnotu v případě, že volaného očekává hodnotu v registrech celé číslo.  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../build/calling-convention.md)