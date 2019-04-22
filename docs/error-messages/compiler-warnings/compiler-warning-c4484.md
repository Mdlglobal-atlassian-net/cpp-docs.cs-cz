---
title: Upozornění kompilátoru C4484
ms.date: 11/04/2016
f1_keywords:
- C4484
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
ms.openlocfilehash: 29e99da02aa0144699d3c20e523b5e5e4b6b8f72
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58766792"
---
# <a name="compiler-warning-c4484"></a>Upozornění kompilátoru C4484

'override_function': odpovídá metodě base ref class "base_class_function", ale není označeno 'virtual', 'new' nebo 'override'; předpokládá se 'new' (tzn. ne virtual)

Při kompilaci s **/CLR**, kompilátor nebude implicitně přepsat funkci základní třídy, což znamená, že funkce získá novou patici ve vtable. Pokud chcete vyřešit, explicitně určete, jestli má funkce přepsání.

Další informace naleznete v tématu:

- [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [override](../../extensions/override-cpp-component-extensions.md)

- [new (nový slot v tabulce vtable)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

C4484 je vždy vyvoláno jako chyba. Použití [upozornění](../../preprocessor/warning.md) potlačit C4484 direktivy pragma.

## <a name="example"></a>Příklad

Následující ukázka generuje C4484.

```
// C4484.cpp
// compile with: /clr
ref struct A {
   virtual void Test() {}
};

ref struct B : A {
   void Test() {}   // C4484
};

// OK
ref struct C {
   virtual void Test() {}
   virtual void Test2() {}
};

ref struct D : C {
   virtual void Test() new {}
   virtual void Test2() override {}
};
```