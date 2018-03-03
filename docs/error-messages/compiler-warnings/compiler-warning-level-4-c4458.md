---
title: "Kompilátoru (úroveň 4) upozornění C4458 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4458
dev_langs:
- C++
helpviewer_keywords:
- C4458
ms.assetid: 7bdaa1b1-0caf-4d68-98c4-6bdd441c23fb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5dc5e3e49a8581fda9ecf83df2a96056bec38d7b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4458"></a>C4458 kompilátoru upozornění (úroveň 4)
  
> prohlášení o '*identifikátor*' skryje třídy člena
  
Prohlášení o *identifikátor* v oboru místní skryje deklaraci stejně jako názvem *identifikátor* na rozsah třídy. Toto upozornění informacemi o tom, který odkazuje na *identifikátor* v tomto rozsahu odkazující na lokálně deklarovaný verze není verze člena třídy, která mohou nebo nemusí být vašich představ. Chcete-li tento problém vyřešit, doporučujeme, abyste že poskytnout názvy lokální proměnné, které nejsou v konfliktu s názvy členů třídy.  
    
## <a name="example"></a>Příklad
  
Následující ukázka generuje C4458, protože parametr `x` a místní proměnné `y` v `member_fn` mají stejné názvy jako datových členů v třídě. Chcete-li tento problém vyřešit, použijte odlišné názvy parametrů a místní proměnné.  
  
```cpp  
// C4458_hide.cpp
// compile with: cl /W4 /c C4458_hide.cpp

struct S {
    int x;
    float y;
    void member_fn(long x) {   // C4458
        double y;  // C4458
        y = x;  
        // To fix this issue, change the parameter name x
        // and local name y to something that does not 
        // conflict with the data member names.
    }
} s;
```  
