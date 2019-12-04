---
title: Chyba kompilátoru C2108
ms.date: 11/04/2016
f1_keywords:
- C2108
helpviewer_keywords:
- C2108
ms.assetid: c84f0b47-5e2c-47d2-8edb-427a40e17c36
ms.openlocfilehash: 069f369627f42314cc14688a9e0c0a55808db507
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752025"
---
# <a name="compiler-error-c2108"></a>Chyba kompilátoru C2108

dolní index není celočíselný typ

Dolní index pole není celočíselný výraz.

## <a name="example"></a>Příklad

Upozornění C2108 se může vygenerovat, pokud nesprávně používáte ukazatel `this` typu hodnoty pro přístup k výchozímu indexeru typu. Další informace naleznete v tématu [Sémantika ukazatele this](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer).

Následující ukázka generuje C2108.

```cpp
// C2108.cpp
// compile with: /clr
using namespace System;

value struct B {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
   void Test() {
      Console::WriteLine("{0}", this[3.3]);   // C2108
      Console::WriteLine("{0}", this->default[3.3]);   // OK
   }
};

int main() {
   B ^ myb = gcnew B();
   myb->Test();
}
```
