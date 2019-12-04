---
title: Chyba kompilátoru C3651
ms.date: 11/04/2016
f1_keywords:
- C3651
helpviewer_keywords:
- C3651
ms.assetid: a03e692e-c219-4654-9827-8415cfa5a22d
ms.openlocfilehash: 9468b1e9193bfa52ed133f6fdfa398e02e40c4ef
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756315"
---
# <a name="compiler-error-c3651"></a>Chyba kompilátoru C3651

member: nejde použít jako explicitní přepsání; musí se jednat o člen základní (Base) třídy.

Bylo zadáno Explicitní přepsání, ale přepsaná funkce byla v typu, který není základním typem.

Další informace najdete v tématu [Explicitní přepsání](../../extensions/explicit-overrides-cpp-component-extensions.md).

Následující ukázka generuje C3651:

```cpp
// C3651.cpp
// compile with: /clr /c
ref class C {
public:
   virtual void func2();
};

ref class Other {
public:
   virtual void func();
};

ref class D : public C {
public:
   virtual void func() new sealed = Other::func;   // C3651
   virtual void func2() new sealed = C::func2;   // OK
};
```
