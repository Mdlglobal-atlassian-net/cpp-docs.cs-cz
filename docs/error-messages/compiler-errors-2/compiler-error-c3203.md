---
title: Chyba kompilátoru C3203
ms.date: 11/04/2016
f1_keywords:
- C3203
helpviewer_keywords:
- C3203
ms.assetid: 6356770e-22c1-434c-91fe-f60b0aa23b91
ms.openlocfilehash: 1d0ed5ec717efecb9fbea4a9451836c0471522b6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738710"
---
# <a name="compiler-error-c3203"></a>Chyba kompilátoru C3203

' type ': nespecializovaná šablona třídy nebo obecná nejde použít jako šablonu nebo obecný argument pro šablonu nebo obecný parametr ' param ', očekával se skutečný typ.

Předali jste neplatný argument šabloně třídy nebo Obecné. Šablona třídy nebo obecná očekává typ jako parametr.

Tato chyba se může vygenerovat v důsledku práce s shodami s kompilátorem, která se dokončila pro Visual Studio 2005: nespecializovaná šablona třídy se nedá použít jako argument šablony v seznamu základních tříd. Chcete-li vyřešit C3203, explicitně přidejte parametry typu šablony do názvu třídy šablony při použití jako parametru šablony v seznamu základních tříd.

```cpp
// C3203.cpp
template< typename T >
struct X {
   void f(X) {}
};

template< typename T >
struct Y : public X<Y> {   // C3203
// try the following line instead
// struct Y : public X<Y<T> > {
   void f(Y) {}
};

int main() {
   Y<int> y;
}
```

Následující ukázka generuje C3203 a ukazuje, jak ji opravit:

```cpp
// C3203_b.cpp
// compile with: /c
template <class T>
struct S1 {};

template <class T>
class C1 {};

typedef C1<S1> MyC1;   // C3203

// OK
template <template <class> class T>
class C2 {};

typedef C2<S1> MyC1;

template <class T>
class C3 {};

typedef C3<S1<int> > MyC12;
```

C3203 může také nastat při použití generických typů:

```cpp
// C3203_c.cpp
// compile with: /clr /c
generic <class T>
value struct GS1 {};

generic <class T>
value struct GC1 {};

typedef GC1<GS1> MyGC1;   // C3203
typedef GC1<GS1<int> > MyGC2;   // OK
```
