---
title: "Kompilátoru (úroveň 4) upozornění C4456 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4456
dev_langs: C++
helpviewer_keywords: C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 937475e32ce3c57633f0d0c504ce0ca4b7c627c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4456"></a>C4456 kompilátoru upozornění (úroveň 4)
  
> prohlášení o '*identifikátor*' skryje předchozí místní deklarace
  
Prohlášení o *identifikátor* v oboru místní skryje deklaraci předchozích místní deklarace se stejným názvem. Toto upozornění informacemi o tom, který odkazuje na *identifikátor* v oboru místní odkazující na lokálně deklarovaný verze není předchozí místní, který může nebo nemusí být vašich představ. Chcete-li tento problém vyřešit, doporučujeme, abyste že poskytnout názvy lokální proměnné, které nejsou v konfliktu s další místní názvy.  
    
## <a name="example"></a>Příklad
  
Následující ukázka generuje C4456, protože smyčky řídit proměnná `int x` a místní proměnné `double x` v `member_fn` se stejnými názvy. Chcete-li tento problém vyřešit, použijte odlišné názvy pro místní proměnné.  
  
```cpp  
// C4456_hide.cpp
// compile with: cl /W4 /c C4456_hide.cpp

struct S {
    void member_fn(unsigned u) {
        double x = 0;
        for (int x = 0; x < 10; ++x) {  // C4456
            u += x; // uses local int x
        } 
        x += u; // uses local double x
    }
} s;
```  