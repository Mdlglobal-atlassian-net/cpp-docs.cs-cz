---
title: Kompilátoru (úroveň 1) upozornění C4313 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4313
dev_langs:
- C++
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e42bd8f19ac9a70f93a26265af6e310fb51e7229
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4313"></a>C4313 kompilátoru upozornění (úroveň 1)
'function': 'formátovací řetězec, ve formátu řetězce je v konfliktu s počtem argument typu "typ"  
  
 Je v konfliktu s formátem zadaným a hodnotu, která jsou předávání. Například byl předán parametr 64-bit formátu specifikátor nekvalifikované %d, která očekává parametr 32bitové celé číslo. Toto upozornění je platná pouze při kompilaci kódu pro 64bitové cíle.  
  
## <a name="example"></a>Příklad  
 Následující ukázka kódu generuje C4313 při kompilaci pro 64bitové cílové.  
  
```  
// C4313.cpp  
// Compile by using: cl /W1 C4313.cpp  
#include <stdio.h>  
int main() {  
   int * pI = 0;  
   printf("%d", pI);   // C4313 on 64-bit platform code  
   // Try one of the following lines instead:  
   // printf("%p\n", pI);  
   // printf("%Id\n", pI);   // %I64d expects 64-bits of information  
}  
```