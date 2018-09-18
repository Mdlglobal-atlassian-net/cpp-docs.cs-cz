---
title: Upozornění kompilátoru C4484 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4484
dev_langs:
- C++
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6916bac936ad4b8e67888443f397a4c81c0a956
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022978"
---
# <a name="compiler-warning-c4484"></a>Upozornění kompilátoru C4484

'override_function': odpovídá metodě base ref class "base_class_function", ale není označeno 'virtual', 'new' nebo 'override'; předpokládá se 'new' (tzn. ne virtual)

Při kompilaci s **/CLR**, kompilátor nebude implicitně přepsat funkci základní třídy, což znamená, že funkce získá novou patici ve vtable. Pokud chcete vyřešit, explicitně určete, jestli má funkce přepsání.

Další informace naleznete v tématu:

- [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [override](../../windows/override-cpp-component-extensions.md)

- [New (nový slot v tabulce vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)

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