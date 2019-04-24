---
title: Upozornění kompilátoru C4485
ms.date: 11/04/2016
f1_keywords:
- C4485
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
ms.openlocfilehash: b5afb829485e0e9533a14e818e6d6785f268a83b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311311"
---
# <a name="compiler-warning-c4485"></a>Upozornění kompilátoru C4485

'override_function': odpovídá metodě base ref class "base_class_function", ale není označené jako "nové" nebo "override"; předpokládá se 'new. (a 'virtual')

Přístupový objekt přepíše, s nebo bez něj `virtual` – klíčové slovo, funkce přístupového objektu základní třídy, ale `override` nebo `new` specifikátor nebyla součástí přepsání signatura funkce. Přidat `new` nebo `override` specifikátor, chcete-li vyřešit tato upozornění.

Zobrazit [přepsat](../../extensions/override-cpp-component-extensions.md) a [new (nový slot v tabulce vtable)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md) Další informace.

C4485 je vždy vyvoláno jako chyba. Použití [upozornění](../../preprocessor/warning.md) potlačit C4485 direktivy pragma.

## <a name="example"></a>Příklad

Následující ukázka generuje C4485

```
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