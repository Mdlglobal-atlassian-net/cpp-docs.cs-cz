---
title: "Kompilátoru (úroveň 4) upozornění C4457 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4457
dev_langs: C++
helpviewer_keywords: C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 77965ba08b311768b54788692d3f5b7fa724f5b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4457"></a>C4457 kompilátoru upozornění (úroveň 4)
  
> prohlášení o '*identifikátor*' skryje funkce parametr
  
Prohlášení o *identifikátor* v oboru místní skryje deklaraci parametr stejně jako název funkce. Toto upozornění informacemi o tom, který odkazuje na *identifikátor* v oboru místní odkazující na lokálně deklarovaný verze, není parametr, který může nebo nemusí být vašich představ. Chcete-li tento problém vyřešit, doporučujeme, abyste že poskytnout místní proměnné názvy, které nejsou v konfliktu s názvy parametrů.  
    
## <a name="example"></a>Příklad
  
Následující ukázka generuje C4457, protože parametr `x` a místní proměnné `x` v `member_fn` se stejnými názvy. Chcete-li tento problém vyřešit, použijte odlišné názvy parametrů a místní proměnné.  
  
```cpp  
// C4457_hide.cpp
// compile with: cl /W4 /c C4457_hide.cpp

struct S {
    void member_fn(unsigned x) {
        double a = 0;
        for (int x = 0; x < 10; ++x) {  // C4457
            a += x; // uses local x
        } 
        a += x; // uses parameter x
    }
} s;
```  
