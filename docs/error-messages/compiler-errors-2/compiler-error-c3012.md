---
title: C3012 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3012
dev_langs:
- C++
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d30a7fbb50a984c8cec6b45a0ab4759a0578de7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3012"></a>C3012 chyby kompilátoru
  
> '*vnitřní*': není povoleno přímo v rámci paralelní oblasti – vnitřní funkce  
  
 A [vnitřní funkce kompilátoru](../../intrinsics/compiler-intrinsics.md) funkce není povolena v `omp parallel` oblast. Chcete-li tento problém vyřešit, přesunout vnitřní funkce mimo oblast nebo nahradíte je ekvivalenty – vnitřní funkce.   
  
## <a name="example"></a>Příklad  
  
 Následující ukázka generuje C3012 a ukazuje jeden ze způsobů a opravte ji:  
  
```cpp  
// C3012.cpp  
// compile with: /openmp  
#ifdef __cplusplus  
extern "C" {  
#endif  
void* _ReturnAddress();  
#ifdef __cplusplus  
}  
#endif  
  
int main()  
{  
   #pragma omp parallel  
   {  
      _ReturnAddress();   // C3012  
   }  
   _ReturnAddress();      // OK  
}  
```