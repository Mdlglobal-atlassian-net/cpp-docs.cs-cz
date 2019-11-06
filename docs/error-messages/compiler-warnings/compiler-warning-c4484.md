---
title: Upozornění kompilátoru C4484
ms.date: 11/04/2016
f1_keywords:
- C4484
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
ms.openlocfilehash: 4d3f72ddf7675ea7ad73022dc55a60fdc74d4390
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623634"
---
# <a name="compiler-warning-c4484"></a>Upozornění kompilátoru C4484

' override_function ': odpovídá metodě Base ref class ' base_class_function ', ale není označeno jako ' Virtual ', ' New ' nebo ' override '; Předpokládá se klíčové slovo New (a ne Virtual).

Při kompilaci s možností **/CLR**kompilátor implicitně nepřepisuje funkci základní třídy, což znamená, že funkce získá novou pozici v tabulce vtable. Pro vyřešení explicitně určete, zda je funkce přepsání.

Další informace naleznete v tématu:

- [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [override](../../extensions/override-cpp-component-extensions.md)

- [new (nový slot v tabulce vtable)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

C4484 se vždy vydá jako chyba. Pro potlačení C4484 Použijte direktivu pragma [Warning](../../preprocessor/warning.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C4484.

```cpp
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