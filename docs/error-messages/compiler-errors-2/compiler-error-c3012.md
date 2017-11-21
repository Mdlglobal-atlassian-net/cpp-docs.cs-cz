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
ms.openlocfilehash: a75b8845fafef81768ae5a2da8c81e8734db4ebf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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