---
title: Kompilátoru (úroveň 4) upozornění C4211 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4211
dev_langs:
- C++
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8112927940e5e2f17a4e74e2855a035bc7d5e5cc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4211"></a>C4211 kompilátoru upozornění (úroveň 4)
nestandardní rozšíření používané: předefinovat extern statický  
  
 Rozšíření Microsoft výchozí (/Ze), můžete změnit definici `extern` identifikátor jako **statické**.  
  
## <a name="example"></a>Příklad  
  
```  
// C4211.c  
// compile with: /W4  
extern int i;  
static int i;   // C4211  
  
int main()  
{  
}  
```  
  
 Takové předefinování jsou neplatné v části kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).  
  
## <a name="see-also"></a>Viz také  


