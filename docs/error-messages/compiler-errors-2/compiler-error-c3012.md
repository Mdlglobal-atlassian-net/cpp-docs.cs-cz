---
title: "C3012 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3012
dev_langs: C++
helpviewer_keywords: C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 32c12397339f861b71fe41566f29fd1a8929b66e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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