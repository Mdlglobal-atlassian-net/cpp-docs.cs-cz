---
title: Chyba kompilátoru C2253
ms.date: 11/04/2016
f1_keywords:
- C2253
helpviewer_keywords:
- C2253
ms.assetid: bd6445ae-b2c1-4669-9657-a8f4acf80b16
ms.openlocfilehash: 89acfd8a03dc0ee2dc25e14e0b3a63ab25151cc6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758850"
---
# <a name="compiler-error-c2253"></a>Chyba kompilátoru C2253

' function ': specifikátor Pure nebo abstract override je povolený jenom pro virtuální funkci.

Nevirtuální funkce je zadána jako Pure `virtual`.

Následující ukázka generuje C2253:

```cpp
// C2253.cpp
// compile with: /c
class A {
public:
   void func1() = 0;   // C2253 not virtual
   virtual void func2() = 0;   // OK
};
```

Následující ukázka generuje C2253:

```cpp
// C2253_2.cpp
// compile with: /clr /c
ref struct A {
   property int Prop_3 {
      int get() abstract;   // C2253
      // try the following line instead
      // virtual int get() abstract;

      void set(int i) abstract;   // C2253
      // try the following line instead
      // virtual void set(int i) abstract;
   }
};
```
