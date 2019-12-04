---
title: Chyba kompilátoru C3830
ms.date: 11/04/2016
f1_keywords:
- C3830
helpviewer_keywords:
- C3830
ms.assetid: c9798f88-5001-4067-9fb1-09957ddc6fa8
ms.openlocfilehash: 14272d2c0b0f8de63f55d2ba3d1c01cf04e0dfbd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741635"
---
# <a name="compiler-error-c3830"></a>Chyba kompilátoru C3830

' typ1 ': nelze dědit z ' typ2 ', typy hodnot můžou dědit pouze z tříd rozhraní

Typ hodnoty nemůže dědit základní třídu.  Další informace naleznete v tématu [třídy a struktury](../../extensions/classes-and-structs-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3830:

```cpp
// C3830a.cpp
// compile with: /clr /c
public value struct MyStruct4 {
   int i;
};

public value class MyClass : public MyStruct4 {};   // C3830

// OK
public interface struct MyInterface4 {
   void i();
};

public value class MyClass2 : public MyInterface4 {
public:
   virtual void i(){}
};
```
