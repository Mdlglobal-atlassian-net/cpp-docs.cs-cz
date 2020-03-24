---
title: Upozornění kompilátoru C4485
ms.date: 11/04/2016
f1_keywords:
- C4485
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
ms.openlocfilehash: c92f805eb2960336ed34f5da93b6c13f46bf15ac
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165142"
---
# <a name="compiler-warning-c4485"></a>Upozornění kompilátoru C4485

' override_function ': odpovídá metodě Base ref class ' base_class_function ', ale není označeno jako ' New ' nebo ' override '; Předpokládá se klíčové slovo New (a Virtual).

Překrytí přístupového objektu s klíčovým slovem `virtual` nebo bez něj má klíčové slovo základní třídy, ale specifikátor `override` nebo `new` nebyl součástí signatury funkce override. Chcete-li vyřešit toto upozornění, přidejte specifikátor `new` nebo `override`.

Další informace naleznete v tématu [override](../../extensions/override-cpp-component-extensions.md) and [New (New slot v tabulce vtable)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md) .

C4485 se vždy vydá jako chyba. Pro potlačení C4485 Použijte direktivu pragma [Warning](../../preprocessor/warning.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C4485

```cpp
// C4485.cpp
// compile with: /clr
delegate void Del();

ref struct A {
   virtual event Del ^E;
};

ref struct B : A {
   virtual event Del ^E;   // C4485
};

ref struct C : B {
   virtual event Del ^E {
      void raise() override {}
      void add(Del ^) override {}
      void remove(Del^) override {}
   }
};
```
