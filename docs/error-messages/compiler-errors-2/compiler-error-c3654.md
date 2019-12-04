---
title: Chyba kompilátoru C3654
ms.date: 11/04/2016
f1_keywords:
- C3654
helpviewer_keywords:
- C3654
ms.assetid: 57d96e3f-6bbb-4eaa-934b-26c23b4ceb2e
ms.openlocfilehash: 960dbe9f18403c12919db713cc41451dd7b93aac
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756289"
---
# <a name="compiler-error-c3654"></a>Chyba kompilátoru C3654

' text ': Chyba syntaxe v explicitním přepsání

Neočekávaný řetězec byl v explicitním přepsání. Další informace najdete v tématu [Explicitní přepsání](../../extensions/explicit-overrides-cpp-component-extensions.md).

Následující ukázka generuje C3654:

```cpp
// C3654.cpp
// compile with: /clr /c
public ref struct B {
   virtual void f() = 0;
   virtual void g() = 0;
   virtual void h() = 0;
};

public ref struct Q : B {
   virtual void f() = B::f, 3 {}   // C3654
   // try the following line instead
   // virtual void g() = B::g, B::h {}
};
```
