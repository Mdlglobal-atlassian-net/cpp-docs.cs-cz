---
title: Chyba kompilátoru C3203 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3203
dev_langs:
- C++
helpviewer_keywords:
- C3203
ms.assetid: 6356770e-22c1-434c-91fe-f60b0aa23b91
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae0707bc56a812af77d30ac9dac8e945ee5e2aa6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082847"
---
# <a name="compiler-error-c3203"></a>Chyba kompilátoru C3203

'type': Třída nespecializovaná šablona nebo obecná nelze použít jako šablony nebo obecný argument šablony nebo obecný parametr 'param', očekával se skutečný typ.

Neplatný argument předaný do šablony třídy nebo obecná. Třída šablona nebo obecná hodnota očekává jako parametr typu.

Tuto chybu mohou být generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual C++ 2005: šablonu nespecializovaná třídy nelze použít jako argument šablony v seznamu základních tříd. C3203 vyřešíte explicitně přidáte parametrů typu šablony pro název třídy šablony při použití jako parametr šablony v seznamu základních tříd.

```
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

Následující ukázka generuje C3203 a ukazuje, jak ho opravit:

```
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

C3203 může dojít také při použití obecných typů:

```
// C3203_c.cpp
// compile with: /clr /c
generic <class T>
value struct GS1 {};

generic <class T>
value struct GC1 {};

typedef GC1<GS1> MyGC1;   // C3203
typedef GC1<GS1<int> > MyGC2;   // OK
```