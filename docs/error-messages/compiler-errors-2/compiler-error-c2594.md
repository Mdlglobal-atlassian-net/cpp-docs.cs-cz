---
title: Chyba kompilátoru C2594
ms.date: 11/04/2016
f1_keywords:
- C2594
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
ms.openlocfilehash: ade657f9ada2a2249d2f96b7caada7b9719195d1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759331"
---
# <a name="compiler-error-c2594"></a>Chyba kompilátoru C2594

' operator ': dvojznačné převody z ' typ1 ' na ' typ2 '

Žádný převod z *typ1* na *typ2* byl více přímý než jiný. Doporučujeme dvě možná řešení pro převod z *typ1* na *typ2*. První možností je definovat přímý převod z *typ1* na *typ2*a druhou možností je určit sekvenci převodů z *typ1* na *typ2*.

Následující ukázka generuje C2594. Navrhované řešení chyby je posloupnost převodů:

```cpp
// C2594.cpp
// compile with: /c
struct A{};
struct I1 : A {};
struct I2 : A {};
struct D : I1, I2 {};

A *f (D *p) {
   return (A*) (p);    // C2594

// try the following line instead
// return static_cast<A *>(static_cast<I1 *>(p));
}
```
