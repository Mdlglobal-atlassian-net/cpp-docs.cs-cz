---
title: Upozornění kompilátoru C4485
ms.date: 11/04/2016
f1_keywords:
- C4485
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
ms.openlocfilehash: 896fca6c6b257c90ccdf813a9c6cb6bc27ad9e96
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623613"
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