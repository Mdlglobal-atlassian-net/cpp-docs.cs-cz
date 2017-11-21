---
title: "C2955 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2955
dev_langs: C++
helpviewer_keywords: C2955
ms.assetid: 77709fb6-d69b-46fd-a62f-e8564563d01b
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: af3f53545aa70e738f14c902a7a75afc48275b57
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2955"></a>C2955 chyby kompilátoru
"identifikátor": použití třídy šablony nebo alias obecného vyžaduje šablony nebo seznam argumentů obecné  
  
 Šablona třídy nebo obecné třídy nelze použít jako identifikátor bez šablony nebo seznam obecné argumentů.  
  
 Další informace najdete v tématu [šablony třídy](../../cpp/class-templates.md).  
  
 Následující ukázka generuje C2955 a ukazuje, jak to opravit:  
  
```  
// C2955.cpp  
// compile with: /c  
template<class T>   
class X {};  
  
X x1;   // C2955  
X<int> x2;   // OK - this is how to fix it.  
```  
  
 C2955 může dojít také při pokusu o definici z přesahujících pro funkce deklarované v šabloně třídy:  
  
```  
// C2955_b.cpp  
// compile with: /c  
template <class T>  
class CT {  
public:  
   void CTFunc();  
   void CTFunc2();  
};  
  
void CT::CTFunc() {}   // C2955  
  
// OK - this is how to fix it  
template <class T>  
void CT<T>::CTFunc2() {}  
  
```  
  
 C2955 může dojít také při použití obecných typů:  
  
```  
// C2955_c.cpp  
// compile with: /clr  
generic <class T>   
ref struct GC {   
   T t;  
};  
  
int main() {  
   GC^ g;   // C2955  
   GC <int>^ g;  
}  
```

## <a name="example"></a>Příklad
**Visual Studio 2017 a novější:** kompilátor správně diagnostikuje chybějící seznamy argumentů šablony, když šablonu se zobrazí v seznamu parametrů šablony (například jako součást výchozí šablonu argumentu nebo parametru šablony bez typu). Následující kód zkompiluje v sadě Visual Studio 2015, ale vytváří chyby ve Visual Studio 2017.

```
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias 
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```
