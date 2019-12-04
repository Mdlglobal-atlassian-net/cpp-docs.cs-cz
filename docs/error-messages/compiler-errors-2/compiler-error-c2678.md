---
title: Chyba kompilátoru C2678
ms.date: 11/04/2016
f1_keywords:
- C2678
helpviewer_keywords:
- C2678
ms.assetid: 1f0a4e26-b429-44f5-9f94-cb66441220c8
ms.openlocfilehash: 390752d5d34685afc8b5fc5401fd75585bb48dd0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760332"
---
# <a name="compiler-error-c2678"></a>Chyba kompilátoru C2678

binární operátor: není definovaný žádný operátor, který by přebírají levý operand typu Type (nebo neexistuje žádný přijatelný převod).

Chcete-li operátor použít, je třeba jej přetížit pro daný typ nebo definovat převod na typ, pro který je operátor definován.

## <a name="example"></a>Příklad

K C2678 může dojít, když je levý operand kvalifikován jako const, ale operátor je definován pro převzetí argumentu, který není const.

Následující ukázka generuje C2678 a ukazuje, jak ji opravit:

```cpp
// C2678a.cpp
// Compile by using: cl /EHsc /W4 C2678a.cpp
struct Combo {
   int number;
   char letter;
};

inline Combo& operator+=(Combo& lhs, int rhs) {
   lhs.number += rhs;
   return lhs;
}

int main() {
   Combo const combo1{ 42, 'X' };
   Combo combo2{ 13, 'Z' };

   combo1 += 6; // C2678
   combo2 += 9; // OK - operator+= matches non-const Combo
}
```

## <a name="example"></a>Příklad

K C2678 může dojít také v případě, že před voláním členské funkce připnout nativní člen.

Následující ukázka generuje C2678 a ukazuje, jak ji opravit.

```cpp
// C2678.cpp
// compile with: /clr /c
struct S { int _a; };

ref class C {
public:
   void M( S param ) {
      test = param;   // C2678

      // OK
      pin_ptr<S> ptest = &test;
      *ptest = param;
   }
   S test;
};
```
