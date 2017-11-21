---
title: "C2676 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2676
dev_langs: C++
helpviewer_keywords: C2676
ms.assetid: 838a5e34-c92f-4f65-a597-e150bf8cf737
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ed21b76da0834ff4a2aaa8af647d791fdaac075a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2676"></a>C2676 chyby kompilátoru
binární 'operátor': 'typ' nedefinuje tento operátor ani převod na typ přijatelný pro předdefinovaný operátor  
  
 Chcete-li operátor použít, je třeba jej přetížit pro daný typ nebo definovat převod na typ, pro který je operátor definován.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2676.  
  
```  
// C2676.cpp  
// C2676 expected  
struct C {  
   C();  
} c;  
  
struct D {  
   D();  
   D operator >>( C& ){return * new D;}  
   D operator <<( C& ){return * new D;}  
} d;  
  
struct E {  
   // operator int();  
};  
  
int main() {  
   d >> c;  
   d << c;  
   E e1, e2;  
   e1 == e2;   // uncomment operator int in class E, then  
               // it is OK even though neither E::operator==(E) nor   
               // operator==(E, E) defined. Uses the conversion to int   
               // and then the builtin-operator==(int, int)  
}  
```  
  
## <a name="example"></a>Příklad  
 K chybě C2676 může dojít také při pokusu o provedení aritmetické operace ukazatele pro ukazatel `this` typu odkazu.  
  
 Ukazatel `this` má v typu odkazu typ popisovače. Další informace najdete v tématu [tímto sémantika ukazatele](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer).  
  
 Následující ukázka generuje C2676.  
  
```  
// C2676_a.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct A {  
   property Double default[Double] {  
      Double get(Double data) {  
         return data*data;  
      }  
   }  
  
   A() {  
      Console::WriteLine("{0}", this + 3.3);   // C2676  
      Console::WriteLine("{0}", this[3.3]);   // OK  
   }  
};  
  
int main() {  
   A ^ mya = gcnew A();  
}  
```