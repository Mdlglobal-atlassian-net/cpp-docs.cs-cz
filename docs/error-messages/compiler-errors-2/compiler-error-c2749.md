---
title: Chyba kompilátoru C2749
ms.date: 11/04/2016
f1_keywords:
- C2749
helpviewer_keywords:
- C2749
ms.assetid: a81aef36-cdca-4d78-89d5-b72eff2500b2
ms.openlocfilehash: 71c2f3d3a297d70501c675ac6a9f750cbdf0d421
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759617"
---
# <a name="compiler-error-c2749"></a>Chyba kompilátoru C2749

' type ': lze vyvolat nebo zachytit popisovač do spravované třídy s možností/CLR: Safe

Při použití **/clr: Safe**můžete vyvolat nebo zachytit pouze odkazový typ.

Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2749:

```cpp
// C2749.cpp
// compile with: /clr:safe
ref struct MyStruct {
public:
   int i;
};

int main() {
   MyStruct ^x = gcnew MyStruct;

   // Delete the following 4 lines to resolve.
   try {
      throw (1);   // C2749
   }
   catch(int){}

   // OK
   try {
      throw (x);
   }
   catch(MyStruct ^){}
}
```
