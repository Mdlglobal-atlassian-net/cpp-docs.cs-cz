---
title: Chyba kompilátoru C2140
ms.date: 11/04/2016
f1_keywords:
- C2140
helpviewer_keywords:
- C2140
ms.assetid: d44a0500-002c-4632-9e5e-c71c3a473ec4
ms.openlocfilehash: e04a44007161fcfae5bab948584809590edbc095
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668699"
---
# <a name="compiler-error-c2140"></a>Chyba kompilátoru C2140

'type': typ, který je závislý na parametru obecného typu není povolený jako argument vlastnosti kompilátoru vnitřního typu 'vlastnosti'

Vlastnost typu byl předán neplatná specifikace typu.

Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](../../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2140.

```
// C2140.cpp
// compile with: /clr /c
template <class T>

struct is_polymorphic {
   static const bool value = __is_polymorphic(T);
};

class x {};

generic <class T>
ref class C {
   void f() {
      System::Console::WriteLine(__is_polymorphic(T));   // C2140
      System::Console::WriteLine(is_polymorphic<T>::value);   // C2140

      System::Console::WriteLine(__is_polymorphic(x));   // OK
      System::Console::WriteLine(is_polymorphic<x>::value);   // OK
   }
};
```