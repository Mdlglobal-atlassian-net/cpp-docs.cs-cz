---
title: Chyba kompilátoru C2910
ms.date: 11/04/2016
f1_keywords:
- C2910
helpviewer_keywords:
- C2910
ms.assetid: 09c50e6a-e099-42f6-8ed6-d80e292a7a36
ms.openlocfilehash: 0061a7171dd08440ec5d8c8b8cadb77303ff8f41
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761112"
---
# <a name="compiler-error-c2910"></a>Chyba kompilátoru C2910

' function ': nelze explicitně specializovat

Kompilátor zjistil pokus o explicitní specializaci funkce dvakrát.

Následující ukázka generuje C2910:

```cpp
// C2910.cpp
// compile with: /c
template <class T>
struct S;

template <> struct S<int> { void f() {} };
template <> void S<int>::f() {}   // C2910 delete this specialization
```

C2910 může být také vygenerována, pokud se pokusíte o explicitní specializaci člena, který není šablonou. To znamená, že je možné pouze explicitně specializovat šablonu funkce.

Následující ukázka generuje C2910:

```cpp
// C2910b.cpp
// compile with: /c
template <class T> struct A {
   A(T* p);
};

template <> struct A<void> {
   A(void* p);
};

template <class T>
inline A<T>::A(T* p) {}

template <> A<void>::A(void* p){}   // C2910
// try the following line instead
// A<void>::A(void* p){}
```

Tato chyba se taky vygeneruje v důsledku práce s vyhovujícími kompilátory, které se udělaly v sadě Visual Studio .NET 2003:.

Pro kód bude platný v jazyce Visual Studio .NET 2003 a Visual Studio .NET verze vizuálu C++, odeberte `template <>`.

Následující ukázka generuje C2910:

```cpp
// C2910c.cpp
// compile with: /c
template <class T> class A {
   void f();
};

template <> class A<int> {
   void f();
};

template <> void A<int>::f() {}   // C2910
// try the following line instead
// void A<int>::f(){}   // OK
```
